<div align="center">
  <img src="../assets/docker.svg">
</div>

## Índice
- [Introducción](#introducción)
  - [Conceptos Clave](#conceptos-clave)
  - [Docker y DevOps](#docker-y-devops)
  - [Docker y CI/CD](#docker-y-cicd)
- [Instalación de Docker](#instalación-de-docker)
  - [Instalación en Windows](#instalación-en-windows)
  - [Instalación en macOS](#instalación-en-macos)
  - [Instalación en Linux (Ubuntu/Debian)](#instalación-en-linux-ubuntudebian)
- [Arquitectura de docker](#arquitectura-de-docker)
  - [Docker Client](#docker-client)
  - [Docker Daemon (dockerd)](#docker-daemon-dockerd)
  - [Docker Objects (Objetos)](#docker-objects-objetos)
  - [Docker Registry](#docker-registry)
  - [Arquitectura interna (Linux)](#arquitectura-interna-linux)
  - [Docker vs Máquinas Virtuales](#docker-vs-máquinas-virtuales)
- [Imagen](#imagen)
  - [Características](#características)
  - [Imagen vs. Contenedor](#imagen-vs-contenedor)
  - [Comandos](#comandos)
  - [Cómo se crea una imagen](#cómo-se-crea-una-imagen)
    - [Desde un Dockerfile](#desde-un-dockerfile)
      - [Para que sirve](#para-que-sirve)
      - [Funcionamiento interno](#funcionamiento-interno)
      - [Estructura básica de un Dockerfile](#estructura-básica-de-un-dockerfile)
      - [CMD VS ENTRYPOINT](#cmd-vs-entrypoint)
    - [A partir de un contenedor existente](#a-partir-de-un-contenedor-existente)
- [Containers/Contenedores](#containerscontenedores)
  - [Características](#características-1)
  - [Ciclo de vida de un contenedor](#ciclo-de-vida-de-un-contenedor)
  - [Comandos](#comandos-1)
  - [Variables de docker run](#variables-de-docker-run)
- [Volumen](#volumen)
  - [Contenedor vs Volumen](#contenedor-vs-volumen)
  - [Tipos de almacenamiento](#tipos-de-almacenamiento)
  - [Comandos](#comandos-2)
- [Network](#network)
  - [Tipos de redes](#tipos-de-redes)
  - [Comandos](#comandos-3)
- [Registry](#registry)
  - [Tipo](#tipo)
  - [Comandos](#comandos-4)
- [Docker compose](#docker-compose)
  - [Diferencias entre Docker CLI y Docker Compose](#diferencias-entre-docker-cli-y-docker-compose)
  - [Estructura de un docker-compose.yml](#estructura-de-un-docker-composeyml)
  - [Comandos](#comandos-5)

# Introducción

Docker es una plataforma de **virtualización ligera basada en contenedores** que permite desarrollar, empaquetar y ejecutar aplicaciones de forma consistente en cualquier entorno.

Un **contenedor** incluye:
- Código de la aplicación
- Dependencias
- Librerías
- Variables de entorno
- Runtime necesario

> A diferencia de una máquina virtual, Docker **comparte el kernel del sistema**, lo que lo hace más rápido y eficiente.

## Conceptos Clave

| Concepto | Descripción |
|--------|------------|
| Imagen | Plantilla inmutable para crear contenedores |
| Contenedor | Instancia en ejecución de una imagen |
| Dockerfile | Archivo con instrucciones para crear una imagen |
| Volumen | Persistencia de datos |
| Red | Comunicación entre contenedores |
| Registry | Repositorio de imágenes (Docker Hub, GitHub, ECR…) |

## Docker y DevOps

Docker es una pieza clave dentro de **DevOps**, ya que permite:
- Entornos reproducibles
- Automatización de despliegues
- Escalabilidad
- Reducción de errores por diferencias entre entornos

## Docker y CI/CD

Docker se integra perfectamente en pipelines de CI/CD para:
- Construir imágenes
- Ejecutar tests
- Versionar releases
- Desplegar automáticamente

Ejemplo de flujo:
```text
Commit → Build imagen → Test → Push registry → Deploy
```

# Instalación de Docker

## Instalación en Windows

Requisitos
- Windows 10/11 Pro, Enterprise o Education
- Virtualización habilitada en BIOS
- WSL2 habilitado (recomendado)

Pasos
- Descargar Docker Desktop: https://www.docker.com/products/docker-desktop
- Ejecutar el instalador y habilitar: Use WSL 2 instead of Hyper-V
- Reiniciar el sistema si es necesario
- Verificar instalación

```bash
docker -v
docker info
```
> Nota: En Windows Home es obligatorio usar WSL2.

## Instalación en macOS

Requisitos
- macOS 11 o superior
- Procesador Intel o Apple Silicon (M1/M2)

Pasos
- Descargar Docker Desktop: https://www.docker.com/products/docker-desktop
- Instalar el .dmg y mover Docker a Applications
- Iniciar Docker Desktop
- Verificar instalación:

```bash
docker -v
docker info
```

## Instalación en Linux (Ubuntu/Debian)

Pasos
- Actualizar el sistema:
```bash
sudo apt update
sudo apt upgrade -y
```
- Instalar dependencias
```bash
sudo apt install -y ca-certificates curl gnupg lsb-release
```
- Agregar la clave oficial de Docker
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
- Agregar repositorio
```bash
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```
- Instalar Docker
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
- Habilitar Docker al inicio
```bash
sudo systemctl enable docker
sudo systemctl start docker
```
- Ejecutar Docker sin sudo (opcional pero recomendado)
```bash
sudo usermod -aG docker $USER
newgrp docker
```
- Verificar instalación
```bash
docker -v
docker run hello-world
```

# Arquitectura de docker

La arquitectura de Docker describe cómo están organizados y cómo interactúan los componentes que permiten crear, distribuir y ejecutar contenedores. A alto nivel, Docker sigue un modelo cliente–servidor.

Docker se compone principalmente de:
- Docker Client
- Docker Daemon (dockerd)
- Docker Objects (images, containers, networks, volumes)
- Docker Registry

+-------------------+
|   Docker Client   |
+-------------------+
          |
          | REST API
          v
+-------------------+
|  Docker Daemon    |
+-------------------+
   |      |      |
 Images Containers Networks
          |
          v
   Docker Registry


## Docker Client

Es la herramienta de línea de comandos (CLI) con la que los usuarios interactúan.
Cuando escribes un comando como docker run, el cliente envía esa instrucción al Docker Daemon a través de una API REST. Un cliente puede conectarse a un daemon local o a uno remoto.

```bash
docker build
docker pull
docker run
docker ps
```

## Docker Daemon (dockerd)

Es el corazón de Docker. Es un proceso que se ejecuta en segundo plano en el sistema operativo host.
- Función: Escucha las peticiones de la API de Docker y gestiona objetos como imágenes, contenedores, redes y volúmenes.
- Comunicación: Se comunica con otros daemons para gestionar servicios de Docker de forma remota.

## Docker Objects (Objetos)

Son los elementos que creas y utilizas en Docker:
- Imágenes: Plantillas de solo lectura con las instrucciones para crear un contenedor. A menudo, una imagen se basa en otra (por ejemplo, una imagen de Python basada en Ubuntu).Se crean a partir de un Dockerfile y están construidas por capas (layers).

Base OS
 └── Runtime (Java, Python, Node)
      └── Dependencias
           └── Aplicación

- Contenedores: Son las instancias ejecutables de una imagen. Puedes pensarlo como un proceso aislado que corre sobre el kernel del host. Comparten el kernel del sistema operativo
- Volúmenes: Permiten que los datos persistan aunque el contenedor se elimine. Usados para Bases de datos y Archivos compartidos
- Redes (Networks): Permiten la comunicación entre contenedores.
  - bridge (por defecto)
  - host
  - none
  - overlay (Swarm)

## Docker Registry

Es el lugar donde se almacenan y distribuyen las imágenes.
- Docker Hub: Es el registro público por defecto donde cualquiera puede alojar imágenes.
- Comandos clave: Cuando haces un docker pull, el daemon descarga la imagen del registro. Con docker push, subes tu propia imagen al registro.

## Arquitectura interna (Linux)

Docker se apoya en funcionalidades del kernel:
- Namespaces → aislamiento
    - PID, NET, MNT, IPC, UTS, USER
- cgroups → control de recursos (CPU, RAM)
- Union File Systems → capas (OverlayFS)

## Docker vs Máquinas Virtuales

| Docker                    | Máquinas Virtuales      |
| ------------------------- | ----------------------- |
| Comparte kernel           | Kernel propio           |
| Más ligero                | Más pesado              |
| Arranque rápido           | Arranque lento          |
| Ideal para microservicios | Ideal para SO completos |

# Imagen

Una imagen Docker es una plantilla inmutable que contiene todo lo necesario para ejecutar una aplicación dentro de un contenedor.

Incluye:

- Un sistema de archivos (base OS ligero, por ejemplo Alpine o Ubuntu)
- El runtime (Java, Python, Node, etc.)
- Librerías y dependencias
- El código de la aplicación
- Instrucciones de cómo ejecutar la app (CMD / ENTRYPOINT)

> Una imagen NO se ejecuta, sirve para crear contenedores.
> Un contenedor es una instancia en ejecución de una imagen.

## Características

- Inmutable
  - Una vez creada, no se modifica.
  - Si necesitas cambios, creas una nueva imagen.
- Basada en capas (layers)

Docker reutiliza capas para ahorrar espacio y acelerar descargas y builds.
  - Capa 1: Sistema base (Ubuntu)
  - Capa 2: Runtime (Python)
  - Capa 3: Dependencias
  - Capa 4: Aplicación

## Imagen vs. Contenedor

Es común confundirlos, pero la diferencia es sencilla

| Característica   | Imagen                      | Contenedor                       |
| -----------------| -----------------------     | -----------------------          |
| Estado           | Estática (archivo en disco) | Viva (proceso en ejecución)      |
| Mutabilidad      | Inmutable (no cambia)       | Mutable (puedes crear archivos)  |
| Analogía         | La receta de cocina         | El plato ya cocinado             |

## Comandos

- ver imagenes (Muestra el repository, el tag, image id y el size)
```bash
docker images
docker image ls
```
- descargar una imagen
```bash
docker pull nginx
docker pull nginx:1.25
```
- construir una imagen
```bash
docker build -t miapp:1.0 .
docker build --no-cache -t miapp:1.0 .
```
- Etiquetar una imagen (tag)
```bash
docker tag miapp:1.0 miusuario/miapp:1.0
```
- Eliminar una imagen
```bash
docker rmi miapp:1.0
docker rmi 3f2c1a
docker rmi -f miapp:1.0
docker image prune
```
> docker image prune Elimina imágenes no utilizadas.
> Útil para limpieza local, pero cuidado en entornos compartidos.
- Inspeccionar una imagen: Muestra las capas, variables de entorno, CMD/ENTRYPOINT y arquitectura
```bash
docker inspect nginx
```
- Historial de capas: Muestra las capas, tamaño y las instrucciones del Dockerfile
```bash
docker history nginx
```
- Ejecutar una imagen: Busca la imagen, si no existe la descarga, crear el contenedor y ejecuta el proceso principal
```bash
docker run nginx
```

## Cómo se crea una imagen

### Desde un Dockerfile

Un Dockerfile es un archivo de texto (sin extensión) que contiene una serie de instrucciones que Docker sigue paso a paso para construir una imagen Docker.

- El contexto de construcción (Build Context)
Cuando ejecutas el build, Docker envía todos los archivos de la carpeta actual al "Daemon". Si tienes archivos pesados que no necesitas (como la carpeta node_modules o archivos .git), debes usar un archivo llamado .dockerignore para que el proceso sea más rápido y la imagen más ligera.

- El orden importa (Caché de capas)
Docker es inteligente: si no has cambiado tu archivo package.json, Docker se saltará el paso de RUN npm install y usará una versión guardada en caché. Por eso, siempre se recomienda copiar los archivos de dependencias antes que el código fuente.

- Inmutabilidad
Recuerda que una vez que el Dockerfile termina de ejecutarse y la imagen se crea, nada cambia. Si modificas una línea de código en tu aplicación, debes volver a ejecutar el comando build para generar una nueva versión de la imagen.

#### Para que sirve

Con un Dockerfile puedes:
- Crear imágenes reproducibles
- Automatizar instalaciones
- Versionar infraestructura
- Evitar configuraciones manuales
- Garantizar que funcione igual en cualquier entorno

#### Funcionamiento interno

- Lee el Dockerfile línea por línea
- Ejecuta cada instrucción en orden
- Cada instrucción crea una capa (layer) nueva
- Si una capa no cambia → se reutiliza de la caché
- Al final, se genera una imagen Docker

> Si una instrucción cambia, todas las capas siguientes se reconstruyen.

#### Estructura básica de un Dockerfile

```dockerfile
# 1. Imagen base oficial de Node.js versión 18
FROM node:18

# 2. Crear y usar este directorio para la app
WORKDIR /usr/src/app

# 3. Copiar los archivos de dependencias primero (para aprovechar el caché)
COPY package*.json ./

# 4. Instalar las dependencias
RUN npm install

# 5. Copiar el resto del código de la aplicación
COPY . .

# 6. Abrir el puerto 3000
EXPOSE 3000

# 7. Comando para arrancar la app
CMD ["node", "app.js"]
```
> Cada instrucción crea una capa nueva.

- FROM
  - Define la imagen base
  - Es obligatoria (salvo FROM scratch)
  - Puede haber varios FROM (multi-stage build)
- WORKDIR
  - Establece el directorio de trabajo
  - Evita usar cd
  - Se crea automáticamente si no existe
- COPY
  - Copia archivos del host a la imagen
  - Solo copia desde el contexto de build
- ADD (menos recomendado)
  - Similar a COPY
  - Puede:
    - Descomprimir archivos
    - Descargar URLs

> Se recomienda COPY por claridad.
- RUN
  - Ejecuta comandos durante el build
  - Crea una nueva capa
  - Ideal para instalar dependencias
- CMD
  - Define el comando por defecto
  - Se ejecuta al iniciar el contenedor
  - Puede ser sobrescrito en docker run
- ENTRYPOINT
  - Comando fijo
  - No se sobrescribe fácilmente
  - Ideal para imágenes tipo “ejecutable”
- EXPOSE
  - Documenta el puerto usado
  - No abre el puerto automáticamente
  - Se usa junto con -p
- ENV
  - Define variables de entorno
  - Disponibles en build y runtime
- ARG
  - Variables solo para el build
  - No existen en el contenedor final
- VOLUME
  - Define puntos de montaje
  - No crea el volumen en el host
- USER
  - Evita usar root
  - Mejora seguridad
- HEALTHCHECK
  - Verifica estado del contenedor
  - Docker marca el contenedor como healthy/unhealthy
- Multi-stage build (avanzado)
  - Imágenes más pequeñas
  - Solo queda el resultado final

#### CMD VS ENTRYPOINT

| CMD            | ENTRYPOINT        |
| -------------- | ----------------- |
| Por defecto    | Obligatorio       |
| Sobrescribible | Más rígido        |
| Parámetros     | Comando principal |

### A partir de un contenedor existente

```bash
docker commit contenedor imagen_nueva
```
> No recomendado en producción (poco reproducible).

# Containers/Contenedores

Un contenedor Docker es una instancia en ejecución de una imagen.
Es un proceso aislado en tu sistema operativo que se comporta como una máquina independiente, pero compartiendo el núcleo (kernel) del host.

Sus 3 pilares:
- Aislamiento: Lo que pasa dentro del contenedor no afecta al host ni a otros contenedores.
- Eficiencia: Se inicia en segundos porque no arranca un sistema operativo completo (como las máquinas virtuales).
- Volatilidad: Por defecto, si borras el contenedor, los datos creados dentro desaparecen (a menos que uses volúmenes).

> Imagen = plantilla (estática, no se ejecuta)
> Contenedor = imagen + ejecución + estado

Un contenedor:
- Ejecuta uno o más procesos
- Está aislado del sistema host
- Comparte el kernel del sistema operativo
- Es ligero y rápido
- Puede crearse, iniciarse, detenerse y eliminarse

## Características

- Aislamiento
  - Usa namespaces:
    - PID (procesos)
    - NET (red)
    - MNT (filesystem)
    - IPC, UTS, USER
- Control de recursos
  - Usa cgroups:
    - CPU
    - Memoria
    - I/O
- Sistema de archivos
  - Capas de solo lectura (imagen)
  - Capa writable (del contenedor)

> Los cambios se pierden al eliminar el contenedor (salvo volúmenes).

## Ciclo de vida de un contenedor

docker create → docker start → running → docker stop → docker rm

## Comandos

- crear y ejecutar
```bash
docker run ubuntu
docker run -it ubuntu bash
```
- Ejecutar en segundo plano
```bash
docker run -d nginx
```
- Asignar nombre al contenedor
```bash
docker run --name mi_nginx nginx
```
- Listar contenedores
```bash
docker ps
docker ps -a
```  
- Detener y arrancar contenedores
```bash
docker stop mi_nginx
docker start mi_nginx
docker restart mi_nginx
```
- Logs
```bash
docker logs mi_nginx
docker logs -f mi_nginx
```
- Ejecutar comandos dentro de un contenedor
```bash
docker exec -it mi_nginx bash
docker exec mi_nginx ls /usr/share/nginx/html
```
- Inspeccionar contenedores: Muestra IP, Volúmenes, Variables de entorno y estado
```bash
docker inspect mi_nginx
```
- Eliminar contenedores
```bash
docker rm mi_nginx
docker rm -f mi_nginx
docker container prune
```

> docker container prune: elimina todos los contenedores detenidos, cuidado en entornos compartidos

- Ver consumo de recursos: Muestra CPU, RAM, Red, I/O
```bash
docker stats
```
- Copiar archivos
```bash
docker cp archivo.txt mi_nginx:/tmp/
docker cp mi_nginx:/tmp/archivo.txt .
```
- Pausar y reanudar
```bash
docker pause mi_nginx
docker unpause mi_nginx
```
- Contenedores efimeros
```bash
docker run --rm alpine echo "Hola Docker"
```

## Variables de docker run

| Opción   | Descripción          |
| -------- | -------------------- |
| `-d`     | Segundo plano        |
| `-it`    | Interactivo          |
| `--name` | Nombre               |
| `-p`     | Puertos              |
| `-v`     | Volúmenes            |
| `-e`     | Variables de entorno |
| `--rm`   | Elimina al detenerse |

> `--rm` elimina automáticamente el contenedor al detenerse. Ideal para pruebas o tareas temporales.

# Volumen

Un Volumen en Docker es el mecanismo diseñado para persistir datos generados o utilizados por contenedores.

Por defecto, los contenedores son "efímeros": si borras un contenedor, todos los archivos que se crearon dentro de él desaparecen. Los volúmenes permiten que los datos sobrevivan incluso si el contenedor se detiene o se elimina.

Permite que los datos persistan, se compartan y se mantengan independientes del contenedor
- Los datos persisten aunque el contenedor se elimine.
- Pueden ser compartidos entre contenedores.
- Son independientes del sistema de archivos del contenedor, evitando que se pierdan los cambios.
- En otras palabras: si quieres que los datos sobrevivan a reinicios, destrucción o actualización de contenedores, usa volúmenes.

## Contenedor vs Volumen

| Datos dentro del contenedor       | Volumen Docker                           |
| --------------------------------- | ---------------------------------------- |
| Se pierden al eliminar contenedor | Persisten después de eliminar contenedor |
| Parte de la capa writable         | Independiente de la capa del contenedor  |
| No se puede compartir fácilmente  | Fácil de compartir entre contenedores    |

## Tipos de almacenamiento

- Volúmenes (Volumes) → gestionados por Docker, persistentes y portables.
- Bind mounts → carpeta específica del host, más riesgo de permisos y dependencias del host.
- tmpfs → memoria temporal, no persiste.

## Comandos
- Crear un volumen
```bash
docker volume create mi_volumen
docker volume create --driver local mi_volumen
```
- Listar volúmenes
```bash
docker volume ls
```
- Inspeccionar un volumen
```bash
docker volume inspect mi_volumen
```
- Eliminar un volumen
```bash
docker volume rm mi_volumen
docker volume prune
```

> Esto elimina datos de forma irreversible.

- Asociar un volumen al contenedor
```bash
docker run -d \
  --name mi_db \
  -v mi_volumen:/var/lib/mysql \
  mysql:8
```
- Crear volumen al vuelo
```bash
docker run -d \
  --name web \
  -v /app/data \
  nginx
```

> Docker creará un volumen anónimo en /var/lib/docker/volumes si no existe un nombre

- Bind mount (host → contenedor)
```bash
docker run -d \
  --name web \
  -v /home/usuario/html:/usr/share/nginx/html \
  nginx
```
- Compartir volúmenes entre contenedores
```bash
docker run -d --name app1 -v mi_volumen:/data alpine
docker run -d --name app2 -v mi_volumen:/data alpine
```

# Network

Una network (red) de Docker es un entorno de comunicación aislado donde los contenedores pueden enviarse y recibir datos.

Características:
- Permite comunicación entre contenedores.
- Aísla los contenedores de otras redes o del host si se desea.
- Docker crea una red por defecto (bridge) si no se especifica.
- Cada contenedor puede estar conectado a una o más redes.
- Las redes pueden ser user-defined (creadas por el usuario) o built-in (por defecto).

## Tipos de redes

| Tipo        | Descripción                                                | Uso típico                                 |
| ----------- | ---------------------------------------------------------- | ------------------------------------------ |
| **bridge**  | Red privada por defecto para contenedores en el mismo host | Comunicación local entre contenedores      |
| **host**    | Contenedor comparte la red del host                        | Rendimiento alto, sin aislamiento de red   |
| **none**    | Sin red, aislado totalmente                                | Contenedores que no necesitan comunicación |
| **overlay** | Conecta contenedores en múltiples hosts (Swarm)            | Clúster de contenedores distribuidos       |
| **macvlan** | Asigna dirección MAC y IP propia al contenedor             | Integración con red física existente       |

## Comandos
- Listar redes: NETWORK ID, NAME, DRIVER (bridge, host, overlay), SCOPE
```bash
docker network ls
```
- Inspeccionar una red: Contenedores conectados, subredes e ip, gateway driver usado
```bash
docker network inspect nombre_red
```
- Crear una red
```bash
docker network create --driver bridge mi_red
```
- Conectar un contenedor a una red
```bash
docker network connect mi_red mi_contenedor
docker run -d --name web nginx
docker network connect mi_red web
```

> Ahora web puede comunicarse con otros contenedores en mi_red.

- Desconectar un contenedor de una red
```bash
docker network disconnect mi_red mi_contenedor
```
- Eliminar una red
```bash
docker network rm mi_red
```

> Solo se puede eliminar si no hay contenedores conectados.

- Exposición de puertos al host
```bash
docker run -d -p 8080:80 --name web nginx
```

# Registry

Un Docker Registry (Registro) es, de forma muy sencilla, un "almacén" o biblioteca centralizada donde se guardan y distribuyen las imágenes de Docker.

Si Docker es el sistema de mensajería, el Registry es el centro logístico. Sin él, no podrías compartir tus imágenes con otros desarrolladores ni desplegarlas en servidores de producción fácilmente.

El flujo de trabajo se basa en tres acciones principales:
- Login: Te identificas ante el registro.
- Push: Subes una imagen local desde tu computadora al registro.
- Pull: Descargas una imagen del registro a tu computadora.

El concepto de "Tagging" (Etiquetado)
Para subir una imagen a un registro, el nombre de la imagen debe seguir un formato específico para que Docker sepa a dónde enviarla: [usuario_o_url_servidor]/[nombre_imagen]:[etiqueta]


## Tipo

| Tipo        | Descripción                          | Ejemplo                                           |
| ----------- | ------------------------------------ | ------------------------------------------------- |
| **Público** | Accesible para todos                 | Docker Hub                                        |
| **Privado** | Solo accesible a tu organización     | Harbor, AWS ECR, GCP Artifact Registry, Azure ACR |
| **Local**   | Registry en tu máquina o red interna | `docker run -d -p 5000:5000 registry`             |

## Comandos

- Iniciar sesión
```bash
docker login
docker login registry.example.com
```
- Cerrar sesión
```bash
docker logout
```
- Buscar imágenes en Docker Hub: Name, Descripcion stars, official
```bash
docker search mysql
```
- Descargar imágenes (pull)
```bash
docker pull nginx
docker pull usuario/miapp:1.0
```
- Subir imágenes (push)
```bash
docker tag miapp:1.0 usuario/miapp:1.0
docker push usuario/miapp:1.0
```
- Etiquetar imágenes (tag)
```bash
docker tag miapp:1.0 registry.example.com/usuario/miapp:1.0
```
- Listar imágenes locales
```bash
docker images
```
- Eliminar imágenes locales
```bash
docker rmi miapp:1.0
```
- Ejecutar un Registry local
```bash
docker run -d -p 5000:5000 --name registry registry:2
docker tag miapp:1.0 localhost:5000/miapp:1.0
docker push localhost:5000/miapp:1.0
docker pull localhost:5000/miapp:1.0
```

# Docker compose

Docker Compose es una herramienta que permite definir y ejecutar aplicaciones Docker que tienen múltiples contenedores mediante un archivo de configuración llamado docker-compose.yml.

Ventajas:
- Definir varios contenedores en un solo archivo.
- Configurar volúmenes, redes y dependencias de contenedores.
- Levantar la aplicación con un solo comando.
- Ideal para desarrollo, pruebas y entornos locales.

Se crea un archivo docker-compose.yml donde se describe:

- Servicios (contenedores)
- Imágenes a usar o Dockerfiles
- Volúmenes
- Redes
- Puertos
- Docker Compose lee el archivo y crea la infraestructura completa.
- Comandos típicos:
```bash
docker-compose up
docker-compose down
```

## Diferencias entre Docker CLI y Docker Compose

| Docker CLI                          | Docker Compose                                 |
| ----------------------------------- | ---------------------------------------------- |
| Maneja contenedor individual        | Maneja múltiples contenedores como un conjunto |
| Configuración manual (`docker run`) | Configuración en archivo `docker-compose.yml`  |
| Difícil de reproducir               | Facilita reproducibilidad y versionamiento     |
| Más comandos dispersos              | Un solo comando levanta toda la app            |

## Estructura de un docker-compose.yml

- version: versión del formato de Compose.
- services: define los contenedores que se van a crear.
- build: ruta de Dockerfile para construir imagen.
- image: imagen preexistente.
- ports: puertos host:contenedor.
- volumes: persistencia de datos.
- networks: red a la que pertenece el contenedor.
- volumes: y networks: fuera de services crean recursos compartidos.

```yaml
version: "3.9"

services:
  web:
    build: ./web
    ports:
      - "8080:80"
    volumes:
      - ./web:/usr/share/nginx/html
    networks:
      - app_net

  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: ejemplo123
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - app_net

volumes:
  db_data:

networks:
  app_net:
```

## Comandos

- Levantar la aplicación
```bash
docker-compose up
docker-compose up -d
```
- Detener y eliminar contenedores, redes y volúmenes creados
```bash
docker-compose down
docker-compose down -v
```
- Construir imágenes
```bash
docker-compose build
```
- Reiniciar servicios
```bash
docker-compose restart
```
- Parar servicios
```bash
docker-compose stop
```
- Listar contenedores de Compose
```bash
docker-compose ps
```
- Ejecutar comandos dentro de un contenedor
```bash
docker-compose exec web bash
```
- Ver logs
```bash
docker-compose logs
docker-compose logs -f   # logs en tiempo real
```
- Escalar servicios
```bash
docker-compose up -d --scale web=3
```