<div align="center">
  <img src="../assets/linux.svg" width="200" alt="Logo de Linux">
</div>

## Índice
- [Introducción](#introducción)
  - [Distribuciones populares](#distribuciones-populares)
  - [Estructura del sistema de archivos](#estructura-del-sistema-de-archivos)
- [Permisos de usuario](#permisos-de-usuario)
  - [Archivos críticos de usuarios y grupos](#archivos-críticos-de-usuarios-y-grupos)
  - [El Sistema de Permisos (rwx)](#el-sistema-de-permisos-rwx)
    - [Representación y Notación](#representación-y-notación)
    - [Conversión a Notación Octal (Numérica)](#conversión-a-notación-octal-numérica)
    - [Máscaras de permisos (umask)](#máscaras-de-permisos-umask)
  - [Comandos de Gestión](#comandos-de-gestión)
    - [Modificar Propietarios (chown)](#modificar-propietarios-chown)
    - [Modificar Permisos (chmod)](#modificar-permisos-chmod)
  - [Elevación de Privilegios: sudo y su](#elevación-de-privilegios-sudo-y-su)
  - [Permisos especiales](#permisos-especiales)
  - [Gestión de usuarios y grupos](#gestión-de-usuarios-y-grupos)
  - [El Usuario Root](#el-usuario-root)
  - [Cambio de usuario](#cambio-de-usuario)
  - [sudo vs su](#sudo-vs-su)
  - [Gestión de Sesiones (Comandos)](#gestión-de-sesiones-comandos)
- [Gestion de paquetes y librerias](#gestion-de-paquetes-y-librerias)
  - [Formatos de paquetes más comunes](#formatos-de-paquetes-más-comunes)
  - [Uso de APT (Debian/Ubuntu)](#uso-de-apt-debianubuntu)
  - [Instalacion manual de paquetes](#instalacion-manual-de-paquetes)
    - [Instalación de paquetes .deb](#instalación-de-paquetes-deb)
    - [Instalación desde código fuente](#instalación-desde-código-fuente)
    - [Paquetes Universales (Agnósticos)](#paquetes-universales-agnósticos)
  - [Repositorios Externos y Seguridad](#repositorios-externos-y-seguridad)
    - [Agregar Repositorios PPA](#agregar-repositorios-ppa)
    - [Gestión de Claves GPG](#gestión-de-claves-gpg)
- [Manejos de ficheros](#manejos-de-ficheros)
  - [Sistema de ficheros](#sistema-de-ficheros)
  - [Navegacion Rutas relativas y absolutas](#navegacion-rutas-relativas-y-absolutas)
  - [Ficheros](#ficheros)
  - [Creación y Visualización de Ficheros](#creación-y-visualización-de-ficheros)
    - [Creación rápida](#creación-rápida)
    - [Visualización de contenido](#visualización-de-contenido)
  - [Editores de Texto](#editores-de-texto)
  - [Manipulación de Ficheros y Directorios](#manipulación-de-ficheros-y-directorios)
  - [Busqueda de ficheros y directorios](#busqueda-de-ficheros-y-directorios)
- [Archivado y compresion de ficheros](#archivado-y-compresion-de-ficheros)
  - [Compresión y descompresión básica](#compresión-y-descompresión-básica)
  - [Archivando con tar (Tape Archiver)](#archivando-con-tar-tape-archiver)
  - [Comprimiendo Ficheros: Gzip, Bzip2 y XZ](#comprimiendo-ficheros-gzip-bzip2-y-xz)
  - [Tar con Compresión](#tar-con-compresión)
  - [Archivar y Comprimir con zip](#archivar-y-comprimir-con-zip)
  - [Técnicas Avanzadas de Archivado](#técnicas-avanzadas-de-archivado)
- [Expresiones regulares y busquedas avanzadas](#expresiones-regulares-y-busquedas-avanzadas)
  - [Metacaracteres Básicos](#metacaracteres-básicos)
  - [Corchetes y Rangos \[\]](#corchetes-y-rangos-)
  - [Cuantificadores](#cuantificadores)
  - [POSIX Básico (BRE) vs Extendido (ERE)](#posix-básico-bre-vs-extendido-ere)
  - [Clases de Caracteres POSIX](#clases-de-caracteres-posix)
  - [Alternancia y Paréntesis](#alternancia-y-paréntesis)
  - [Comandos de Búsqueda Avanzada](#comandos-de-búsqueda-avanzada)
- [Shell](#shell)
- [Redirecciones y pipelines](#redirecciones-y-pipelines)
- [Procesos](#procesos)
- [Networking](#networking)
- [Dispositivos de almacenamiento externo](#dispositivos-de-almacenamiento-externo)
  - [Identificar el nombre del dispositivo](#identificar-el-nombre-del-dispositivo)
  - [Montar y Desmontar dispositivos](#montar-y-desmontar-dispositivos)
    - [Crear el punto de montaje](#crear-el-punto-de-montaje)
    - [Montar (mount)](#montar-mount)
    - [Desmontar (umount)](#desmontar-umount)
  - [Dispositivos extraíbles y Automontaje](#dispositivos-extraíbles-y-automontaje)
  - [Formatear y preparar el dispositivo (Bonus)](#formatear-y-preparar-el-dispositivo-bonus)


# Introducción

Linux es un sistema operativo **libre y de código abierto**, basado en Unix.

## Distribuciones populares

- Ubuntu / Debian
- Fedora
- Arch Linux
- CentOS / Rocky Linux

## Estructura del sistema de archivos

| Directorio | Descripción |
|-----------|-------------|
| `/` | Raíz del sistema |
| `/home` | Directorios de usuarios |
| `/etc` | Configuración del sistema |
| `/var` | Logs y datos variables |
| `/bin` | Comandos esenciales |
| `/usr` | Programas del usuario |
| `/tmp` | Archivos temporales |

# Permisos de usuario

Linux es un sistema multiusuario, lo que significa que la seguridad se basa en controlar estrictamente qué puede hacer cada usuario sobre cada recurso.

## Archivos críticos de usuarios y grupos

El sistema gestiona la identidad mediante tres archivos de texto en /etc/:
- /etc/passwd: Contiene información de los usuarios (UID, shell, directorio home). Visible por todos, pero sin contraseñas.
- /etc/shadow: Almacena las contraseñas cifradas y políticas de expiración. Accesible solo por root.
- /etc/group: Define los grupos y sus miembros.

## El Sistema de Permisos (rwx)

Cada archivo/directorio tiene tres permisos básicos:
- Lectura (r): Permite ver el contenido del archivo.
- Escritura (w): Permite modificar o eliminar el archivo.
- Ejecución (x): Permite ejecutar un archivo como programa o script.

Estos permisos se aplican a tres categorías de usuarios:
- Usuario propietario (u)
- Grupo (g)
- Otros (o)

### Representación y Notación

Podemos ver los permisos con ls -l. La cadena resultante (ej: drwxr-xr--) se interpreta así:
- Primer carácter: - (fichero), d (directorio), l (enlace).
- Tres siguientes: Permisos del propietario.
- Tres siguientes: Permisos del grupo.
- Tres últimos: Permisos de otros.

### Conversión a Notación Octal (Numérica)

Es la forma más rápida de asignar permisos masivos:
- 4: Lectura (r)
- 2: Escritura (w)
- 1: Ejecución (x)
  
> Ejemplo: chmod 755 → Propietario (4+2+1=7), Grupo (4+1=5), Otros (4+1=5).

```bash
ls -l archivo # ver permisos
```

### Máscaras de permisos (umask)

Define los permisos por defecto de archivos y directorios nuevos. Ejemplo:

```bash
umask 022 # Archivos nuevos 644, directorios 755
```

## Comandos de Gestión

### Modificar Propietarios (chown)

```bash
sudo chown usuario archivo          # Cambia solo el dueño
sudo chown usuario:grupo archivo    # Cambia dueño y grupo simultáneamente
sudo chown -R usuario:grupo carpeta # Cambia todo el contenido de forma recursiva
```

### Modificar Permisos (chmod)

```bash
chmod 644 archivo       # r-w para dueño, r para el resto
chmod +x script.sh      # Añade ejecución a todos
chmod u+s /bin/comando  # Activa el bit SUID
```

## Elevación de Privilegios: sudo y su

- su (Substitute User): Cambia la sesión a otro usuario. su - inicia una shell limpia como root (requiere clave de root).
- sudo (SuperUser Do): Ejecuta un comando puntual con privilegios. Es preferible porque usa tu propia contraseña y deja registro en los logs.
- visudo: Comando obligatorio para editar /etc/sudoers. Valida la sintaxis antes de guardar para evitar que el sistema quede bloqueado..

## Permisos especiales

- Setuid (s): Permite que un ejecutable se ejecute con los privilegios del propietario del archivo, normalmente root.
- Setgid (s): Ejecutable corre con privilegios del grupo propietario; en directorios, los archivos creados heredan el grupo.
- Sticky bit (t): En directorios como /tmp, solo el propietario puede borrar sus archivos, aunque otros tengan permisos de escritura.

```bash
chmod u+s programa # Setuid
chmod g+s directorio # Setgid
chmod +t directorio # Sticky bit
```

## Gestión de usuarios y grupos

- Crear y modificar usuarios
```bash
sudo useradd -m -s /bin/bash usuario # Crear usuario con home y shell
sudo usermod -aG grupo usuario # Añadir usuario a grupo el flag -a es vital para no borrar los grupos anteriores
sudo userdel -r usuario #Elimina al usuario y su carpeta personal
sudo deluser usuario # Eliminar usuario
```
- Crear y modificar grupos
```bash
sudo groupadd nombre_grupo # Crear grupo
sudo groupdel nombre_grupo # Eliminar grupo
```
- Cambiar propietario y grupo de archivos/directorios
```bash
sudo chown usuario archivo # Cambiar propietario
sudo chown usuario:grupo archivo # Cambiar propietario y grupo
sudo chgrp grupo archivo # Cambiar solo el grupo
```

## El Usuario Root

El usuario root (UID 0) es la cuenta con privilegios ilimitados en el sistema.
- Poder absoluto: Puede leer, escribir o borrar cualquier archivo, independientemente de los permisos definidos.
- Riesgo: Un error cometido como root (ej: rm -rf /) puede destruir el sistema operativo instantáneamente.
- Uso: En sistemas modernos (como Ubuntu), la cuenta de root suele estar "bloqueada" (sin contraseña definida) para obligar al uso de sudo.

## Cambio de usuario

El comando su (Substitute User) permite convertirte en otro usuario durante la sesión actual.
- su usuario: Cambias al usuario indicado, pero mantienes las variables de entorno de tu usuario original.
- su - usuario: (Recomendado) El guion simula un inicio de sesión completo, cargando el PATH y el entorno del usuario destino.
- su -: Si no se especifica usuario, el sistema asume que quieres entrar como root. Requiere conocer la contraseña de root.

```bash
su - root
su usuario
```

## sudo vs su

Es fundamental entender la diferencia para la seguridad del manual:
|Caracteristicas| su | sudo|
|---------------|----|-----|
|Contraseña requerida|	La del usuario destino (root)|	La del usuario actual|
|Auditoría|	Difícil de rastrear quién hizo qué|	Los comandos se registran en /var/log/auth.log|
|Control|	Acceso total o nada|	Permite restringir comandos específicos en sudoers|

## Gestión de Sesiones (Comandos)

Para verificar quién eres en cada momento y gestionar la sesión:
```bash
whoami      # Muestra el nombre de usuario actual
id          # Muestra el UID, GID y los grupos del usuario actual
groups      # Lista los grupos a los que perteneces
exit        # Cierra la sesión del usuario actual y vuelve al anterior (o cierra la terminal)
```

# Gestion de paquetes y librerias

La gestión de paquetes es el corazón de la administración de software en Linux. Permite instalar, actualizar, configurar y eliminar aplicaciones de forma centralizada, segura y eficiente. 

Un paquete es un contenedor (archivo comprimido) que incluye:
- Binarios y librerías: El código ejecutable.
- Metadatos: Información sobre el autor, versión y arquitectura (x64, ARM).
- Dependencias: Lista de otros paquetes necesarios para que este funcione.
- Scripts: Instrucciones para configurar el software automáticamente tras la instalación.

Las librerías son componentes reutilizables que otros programas necesitan para funcionar. Una buena gestión de paquetes garantiza:
- Compatibilidad entre aplicaciones
- Resolución automática de dependencias
- Actualizaciones de seguridad
- Facilidad de mantenimiento del sistema

Cada distribución Linux utiliza su propio sistema de paquetes, aunque los conceptos generales son comunes.

## Formatos de paquetes más comunes

Los sistemas se dividen principalmente por su formato de archivo y la herramienta que los maneja.

|Familia|Formato|Gestor (CLI)|Distribuciones Populares|
|-------|-------|------------|------------------------|
|Debian|.deb|apt| dpkg|Ubuntu, Mint, Kali, Debian|
|Red Hat|.rpm|dnf|yum|Fedora, RHEL, Rocky Linux|
|Arch|pkg.tar|.zst|pacman|Arch Linux, Manjaro|
|SUSE|.rpm|zypper|openSUSE|

## Uso de APT (Debian/Ubuntu)

Es el estándar más extendido. Estos son los comandos esenciales que todo administrador debe conocer

- Sincronizar repositorios: Actualiza la base de datos local con las últimas versiones disponibles.
```bash
sudo apt update
```
- Actualizar el sistema: Instala las nuevas versiones de todos los paquetes actuales.
```bash
sudo apt upgrade
```
- Gestión de aplicaciones
```bash
sudo search <nombre> # Buscar software
sudo apt install <nombre> # Instalar
sudo apt remove <nombre> # Eliminar (mantiene la configuracion)
sudo apt purge <nombre> # Eliminar (borra todo)
```
- Limpieza de residuos: Elimina paquetes que se instalaron como dependencias y ya no son necesario
```bash
sudo apt autoremove
```
> Consejo: Revisar paquetes actualizables con ```apt list --upgradable``` antes de actualizar.

- Resolución de dependencias rotas
```bash
sudo apt -f install
```

## Instalacion manual de paquetes

A veces, el software no está en los repositorios oficiales y descargamos un archivo directamente:

### Instalación de paquetes .deb

Si descargas un paquete de una web oficial (ej. Google Chrome), se instala mediante dpkg:

```bash
sudo dpkg -i nombre_paquete.deb
sudo apt install -f  # Corrige posibles errores de dependencias faltantes
```

### Instalación desde código fuente

Cuando el software no está empaquetado, usamos el flujo tradicional:
- Descomprimir: ```tar -xzvf fuente.tar.gz```
- Configurar: ```./configure``` (comprueba que tienes las librerías necesarias).
- Compilar: ```make``` (convierte el código en binario).
- Instalar: ```sudo make install``` (lo mueve a las carpetas del sistema).

> Nota: No gestiona dependencias automáticamente y no queda registrado en el gestor de paquetes.

### Paquetes Universales (Agnósticos)

Para evitar problemas de dependencias, existen formatos que funcionan en cualquier distribución:

- ```Flatpak```: Enfocado en aplicaciones de escritorio con aislamiento (sandboxing).
- ```Snap```: Muy común en servidores y Ubuntu.
- ```AppImage```: No requiere instalación; es un solo archivo ejecutable.

## Repositorios Externos y Seguridad

### Agregar Repositorios PPA

Los Personal Package Archives permiten obtener software más actualizado que el de los repositorios oficiales.

```bash
sudo add-apt-repository ppa:usuario/repositorio
sudo apt update
```

También se puede editar directamente:

- ```/etc/apt/sources.list```
- ```/etc/apt/sources.list.d/```

### Gestión de Claves GPG

Para garantizar que el software de un repositorio externo no ha sido manipulado, Linux utiliza claves criptográficas GPG.

```bash
sudo apt install gnupg
curl -fsSL URL_CLAVE | sudo gpg --dearmor -o /usr/share/keyrings/repositorio.gpg
```

> Nota: Al añadir repositorios modernos, suele ser necesario importar la clave pública del autor mediante ```gpg --import``` o añadiéndola a ```/usr/share/keyrings/```

# Manejos de ficheros

El sistema de archivos de Linux está organizado en una estructura de árbol invertido, donde todo cuelga de la raíz (/).

## Sistema de ficheros

A diferencia de Windows, Linux no utiliza letras de unidad (C:, D:). Los dispositivos físicos se "montan" en carpetas del sistema.

- Case sensitive: Linux distingue entre mayúsculas y minúsculas (Archivo.txt y archivo.txt son distintos).
- Ficheros ocultos: Son aquellos cuyo nombre empieza por un punto (ej: .bashrc).

## Navegacion Rutas relativas y absolutas

- Ruta Absoluta: Indica la posición desde la raíz /. Siempre empieza por /.
```Ejemplo: /home/usuario/documentos/notas.txt```

- Ruta Relativa: Indica la posición desde el directorio donde te encuentras actualmente.
  - ```.``` : Directorio actual.
  - ```..``` : Directorio padre (un nivel arriba).
  - ```~``` : Directorio personal (home) del usuario.
  - ```-``` : Directorio anterior (como el botón "atrás" del navegador).

```bash
pwd              # ¿Dónde estoy?
cd /etc/network  # Ruta absoluta
cd ../Descargas  # Ruta relativa
cd -             # Vuelve al último directorio donde estuviste
```

## Ficheros

Tipos de ficheros en Linux:
- Regulares: Documentos, scripts, binarios.
- Directorios: Contenedores de ficheros.
- Enlaces simbólicos y duros: Punteros a otros ficheros.
  - Simbólicos (ln -s): Como un acceso directo. Si borras el original, el enlace se rompe
  - Duros (ln): Una copia física del puntero al archivo. Si borras el original, el dato sigue existiendo.
- Dispositivos y sockets: Para interacción con hardware y procesos.

## Creación y Visualización de Ficheros

### Creación rápida

- ```touch archivo```: Crea un fichero vacío o actualiza la fecha de modificación si ya existe
- ```mkdir carpeta```: Crea un nuevo directorio (usa -p para crear rutas completas: mkdir -p a/b/c).

### Visualización de contenido

- ```cat```: Muestra todo el contenido de golpe (útil para archivos cortos).
- ```more``` / less: Permiten paginar el contenido. less es más potente y permite buscar con /.
- ```head / tail```: Muestran las primeras o últimas 10 líneas.
- ```tail -f archivo.log```: Vital para ver actualizaciones de un log en tiempo real.

## Editores de Texto

Existen dos mundos principales en la terminal:

- Nano: Sencillo, intuitivo y con los comandos visibles en la parte inferior (ej: Ctrl+O guardar, Ctrl+X salir).
- Vi / Vim: El estándar profesional. Es un editor modal (Modo comando vs Modo inserción).
  - :i para escribir.
  - Esc para salir al modo comando.
  - :wq para guardar y salir, :q! para salir sin guardar.
  - :q! : Salir sin guardar.
- gedit: (GUI en entornos gráficos)

## Manipulación de Ficheros y Directorios

|Comando|Acción|Ejemplo|
|-------|-------|-------|
|cp|Copiar|cp origen destino (usa -r para carpetas)|
|mv|Mover o Renombrar|mv viejo_nombre nuevo_nombre|
|rm|Eliminar|rm archivo (usa -rf para borrar carpetas a la fuerza)|
|ln|Crear Enlace|ln -s origen enlace (enlace simbólico o acceso directo)|

```bash
cp origen destino
cp -r carpeta_origen carpeta_destino # Copiar directorio recursivamente

mv archivo_nuevo.txt /ruta/destino/
mv antiguo.txt nuevo.txt

rm archivo.txt
rm -r carpeta/ # Eliminar directorio y su contenido

mkdir nuevo_directorio
mkdir -p ruta/directorio # Crear directorio y padres si no existen
```

## Busqueda de ficheros y directorios

- El comando find (Búsqueda en disco): Es el más potente. Busca en tiempo real basándose en atributos (nombre, tamaño, fecha).
```bash
find /home -name "*.pdf"            # Buscar todos los PDF en /home
find . -type d -name "proyectos"    # Buscar solo directorios con ese nombre
find /var/log -mtime -7             # Archivos modificados en los últimos 7 días
```
- El comando locate (Búsqueda indexada): Busca en una base de datos local. Es instantáneo pero puede no estar actualizado.
```bash
sudo updatedb    # Actualiza la base de datos de búsqueda
locate archivo.txt
```
- El comando which: Sirve para saber qué binario se está ejecutando cuando lanzas un comando.
```bash
which python     # Devuelve algo como /usr/bin/python
```
- * : Representa cualquier número de caracteres (ej: ls *.log).
- ? : Representa un solo carácter (ej: cat nota?.txt).
- Listar archivos y filtrado
```bash
ls -l # Listado detallado
ls -lh # Listado con tamaño legible
ls -a # Mostrar archivos ocultos
```

> Consejos:
> - Combinar find y grep permite buscar contenido dentro de ficheros específicos.
> - Siempre verificar rutas al usar rm -r para evitar eliminar datos importantes.

# Archivado y compresion de ficheros

En Linux, los conceptos de archivar y comprimir son distintos. Archivar es agrupar varios archivos en uno solo (usando tar), mientras que comprimir es reducir el peso de esos archivos usando algoritmos matemáticos.

## Compresión y descompresión básica

- gzip: Comprime archivos individuales.
- gunzip: Descomprime archivos .gz
- zcat: Visualiza el contenido de un archivo comprimido sin descomprimirlo
- Bzip2: Comprime con mejor ratio que gzip pero más lento.
- bunzip2: Descomprime archivos
- bzcat: Visualiza

```bash
gzip archivo.txt # Genera archivo.txt.gz y elimina el original
gzip -k archivo.txt # Comprime pero mantiene el original

gunzip archivo.txt.gz
zcat archivo.txt.gz

bzip2 archivo.txt # Genera archivo.txt.bz2
bunzip2 archivo.txt.bz2 # Descomprime
bzcat archivo.txt.bz2 # Visualizar sin descomprimir
```

## Archivando con tar (Tape Archiver)

tar no comprime por sí solo; simplemente empaqueta. Es el estándar para copias de seguridad.
Sintaxis básica: tar [opciones] nombre_archivo.tar origen
- -c: Crear un archivo (Create).
- -x: Extraer contenido.
- -v: Ver el progreso (Verbose).
- -f: Especificar el nombre del archivo (File) - Siempre debe ir al final de las opciones.
- -z: gzip
- -j: bzip2
- -t: Listar contenido sin extraer.

```bash
tar -cvf backup.tar /home/usuario/documentos  # Crear archivo
tar -xvf backup.tar                            # Extraer archivo
```

## Comprimiendo Ficheros: Gzip, Bzip2 y XZ

Cada herramienta utiliza un algoritmo diferente, equilibrando velocidad vs. tasa de compresión.

|Herramienta|Extensión|Ventaja|Desventaja|
|-----------|---------|-------|----------|
|Gzip|.gz|"Muy rápido, estándar."|Compresión media.|
|Bzip2|.bz2|Mejor compresión que Gzip.|Más lento y consume más CPU.|
|XZ|.xz|Máxima compresión.|El más lento de todos.|

```bash
gzip archivo.txt      # Crea archivo.txt.gz y ELIMINA el original
bzip2 archivo.txt     # Crea archivo.txt.bz2
xz archivo.txt        # Crea archivo.txt.xz

# Para descomprimir:
gunzip archivo.gz
bunzip2 archivo.bz2
unxz archivo.xz
```

## Tar con Compresión

Lo más común es realizar ambas tareas en un solo comando. tar detecta el algoritmo mediante un flag específico:

- -z (Gzip): tar -czvf archivo.tar.gz /ruta
- -j (Bzip2): tar -cjvf archivo.tar.bz2 /ruta
- -J (XZ): tar -cJvf archivo.tar.xz /ruta

```bash
# Ejemplo avanzado: Extraer cualquier tar comprimido sin especificar el tipo
tar -xvf archivo.tar.gz   # tar moderno detecta el formato automáticamente
```

## Archivar y Comprimir con zip

zip es muy popular para compatibilidad con Windows, ya que archiva y comprime en un solo paso.
- Instalación (si no está): sudo apt install zip unzip
- Comprimir: zip -r backup.zip carpeta/ (el -r es vital para incluir subcarpetas).
- Proteger con contraseña: zip -re secure.zip carpeta/
- Descomprimir: unzip archivo.zip
- Ver contenido: unzip -l archivo.zip

## Técnicas Avanzadas de Archivado

- Excluir ficheros al comprimir: Útil para no incluir carpetas como node_modules o archivos .git.
```bash
tar --exclude='node_modules' -czvf proyecto.tar.gz ./mi_proyecto
```
- Comprimir por bloques o volúmenes (Split): Si necesitas mover un archivo muy grande en partes pequeñas
```bash
# Dividir un archivo en partes de 100MB
zip -s 100m -r backup_grande.zip /data

# Con tar y split
tar -cvf - /data | split -b 100m - backup.tar.
```
- Comprimir a través de la red (SSH): Puedes crear un archivo en un servidor remoto sin guardarlo localmente primero
```bash
tar -czf - /home/usuario | ssh usuario@servidor "cat > backup.tar.gz"
```
- Verificar integridad de archivos
```bash
tar -tvf backup.tar.gz # Listar contenido y comprobar
unzip -t backup.zip # Test de integridad zip
```
- Cifrado de archivos comprimidos con GPG:
```bash
tar -czvf backup.tar.gz /home/usuario
gpg -c backup.tar.gz # Protege con contraseña
# Extraer y descifrar
gpg -d backup.tar.gz.gpg | tar -xzvf -
```
- Backups incrementales
```bash
tar --listed-incremental=snapshot.file -czvf backup_incremental.tar.gz /home/usuario
```

> consejos:
> Elegir gzip para velocidad, bzip2 para mejor ratio, xz para máxima compresión.
> Siempre verificar integridad y permisos antes de transferir backups.
> Comprimir a través de SSH permite backups remotos sin ocupar espacio local.
> Usar exclusiones para no incluir carpetas temporales o irrelevantes.

# Expresiones regulares y busquedas avanzadas

Una Expresión Regular (Regex) es un patrón de búsqueda que describe un conjunto de cadenas de texto. Se utilizan principalmente con comandos como grep, sed, awk y en editores de texto.

## Metacaracteres Básicos

- Punto (.): Representa cualquier carácter excepto un salto de línea.
  - grep "c.sa" coincidirá con "casa", "cosa", "cesa".
- Anclajes: Definen la posición del patrón.
  - Circunflejo (^): Indica el inicio de una línea.
    - grep "^Linux" (Líneas que empiezan por Linux).
  - Dólar ($): Indica el final de una línea.
    - grep "final$" (Líneas que terminan en "final").

```bash
echo "abc" | grep ".b." # Coincide porque b está en medio
^inicio # Coincide con líneas que empiezan con 'inicio'
fin$ # Coincide con líneas que terminan con 'fin'
```

## Corchetes y Rangos []

Permiten definir un conjunto de caracteres posibles para una sola posición.

- [aeiou]: Cualquier vocal.
- [a-z]: Cualquier letra minúscula.
- [0-9]: Cualquier dígito.
- [^0-9]: Cualquier carácter que no sea un dígito (el ^ dentro de corchetes funciona como negación).
- [A-Za-z0-9]: Cualquier carácter alfanumérico.
- \w : cualquier carácter alfanumérico (letra, número o _)
- \W : lo contrario de \w
- \d : dígito [0-9]
- \D : no dígito
- \s : espacio, tab o salto de línea
- \S : no espacio

```bash
grep "[A-Z][0-9]" archivo.txt # Coincide con una letra mayúscula seguida de un número
```

## Cuantificadores

Definen cuántas veces debe aparecer el carácter o grupo anterior.

|Cuantificador|Significado|Tipo|
|-------------|-----------|----|
|*|0 o más veces|Básico|
|?|0 o 1 vez|Extendido|
|+|1 o más veces|Extendido|
|{n}|Exactamente n veces|Extendido|
|{n,m}|Entre n y m veces|Extendido|

```bash
grep -E "a{2,4}" archivo.txt # Coincide con 'aa', 'aaa' o 'aaaa'
```

## POSIX Básico (BRE) vs Extendido (ERE)

En Linux, existen dos estándares principales de Regex. La diferencia radica en qué caracteres necesitan ser "escapados" con una barra invertida \ para ser interpretados como metacaracteres.

- Básico (BRE): Usado por grep por defecto. Metacaracteres como (, ), {, } necesitan escape: \( , \{.

- Extendido (ERE): Usado por grep -E (o egrep). Es más limpio porque no requiere tantos escapes para símbolos avanzados como +, ? o |.

## Clases de Caracteres POSIX

En lugar de rangos manuales, puedes usar clases predefinidas que son más legibles:

- [:alnum:]: Alfanuméricos.
- [:alpha:]: Letras.
- [:digit:]: Números.
- [:space:]: Espacios, tabuladores.

## Alternancia y Paréntesis

Estos pertenecen mayoritariamente al estándar Extendido:

- Alternancia (|): Funciona como un "O" lógico.
  - grep -E "perro|gato" coincidirá con cualquiera de los dos.
- Paréntesis (): Sirven para agrupar patrones.
  - grep -E "video(juego|teca)" coincidirá con "videojuego" o "videoteca".

```bash
grep -E "rojo|azul" archivo.txt # Coincide con 'rojo' o 'azul'
grep -E "(rojo|azul) claro" archivo.txt # Coincide con 'rojo claro' o 'azul claro'
```

## Comandos de Búsqueda Avanzada

- Grep (Global Regular Expression Print): Es la herramienta reina para buscar texto.
```bash
grep -r "error" /var/log/       # Búsqueda recursiva en carpetas
grep -i "linux" archivo.txt     # Ignorar mayúsculas/minúsculas
grep -v "comentario" archivo    # Invertir búsqueda (mostrar lo que NO coincide)
grep -E "^[0-9]{3}" archivo     # Uso de Regex extendida
```
- Sed (Stream Editor): Editor de flujo para transformar texto sobre la marcha.
```bash
echo "2026-01-11" | sed -E 's/([0-9]{4})-([0-9]{2})-([0-9]{2})/\3\/\2\/\1/'
# Salida: 11/01/2026

# Sustituir todas las apariciones (Global)
sed 's/viejo/nuevo/g' archivo.txt
```
- C. Awk: Procesador de textos basado en columnas.
```bash
# Imprimir la primera y tercera columna de /etc/passwd (separado por :)
awk -F ":" '{ print $1, $3 }' /etc/passwd
```
  
# Shell 
# Redirecciones y pipelines
# Procesos
# Networking
# Dispositivos de almacenamiento externo

En Linux, los dispositivos externos (USB, discos duros, tarjetas SD) no aparecen como unidades separadas (E:, F:), sino que deben ser "anclados" a un directorio existente en tu árbol de archivos. Este proceso se llama montar.

## Identificar el nombre del dispositivo

Antes de trabajar con un dispositivo, debes saber cómo lo reconoce el kernel. En Linux, los dispositivos de almacenamiento se representan como archivos dentro de /dev/.

- SATA/USB: Se suelen nombrar como /dev/sda, /dev/sdb, etc.
- Particiones: Se indican con un número al final: /dev/sdb1 (primera partición del segundo disco).
- NVMe: Se nombran como /dev/nvme0n1.

```bash
lsblk        # List Block devices: Muestra una estructura de árbol muy clara.
sudo fdisk -l # Listado técnico detallado de todas las particiones.
ls -l /dev/disk/by-uuid/ # Muestra el identificador único (UUID), útil para montajes permanentes.
```

## Montar y Desmontar dispositivos

Para acceder a los archivos de un USB, necesitamos un Punto de Montaje (una carpeta vacía).

### Crear el punto de montaje

Normalmente se usan las carpetas /mnt (para montajes temporales) o /media/usuario (para 
dispositivos extraíbles).

```bash
sudo mkdir /mnt/mi_usb
```

### Montar (mount)

```bash
sudo mount /dev/sdb1 /mnt/mi_usb
```

### Desmontar (umount)

Es vital para evitar la pérdida de datos. Nota: El comando es umount (sin la primera 'n').

```bash
sudo umount /mnt/mi_usb
# O también usando el nombre del dispositivo:
sudo umount /dev/sdb1
```

> Error común: Si intentas desmontar mientras estás dentro de la carpeta o un programa usa un archivo de ahí, recibirás el error target is busy. Debes salir de la carpeta (cd ..) para poder desmontar.

```bash```
```bash```
```bash```

## Dispositivos extraíbles y Automontaje

En entornos de escritorio (GNOME, KDE), el sistema monta los dispositivos automáticamente en /media/nombre_usuario/. Sin embargo, en servidores o terminal, es importante conocer estos archivos:

- /etc/fstab: Es el archivo de configuración donde se definen qué particiones se montan automáticamente al arrancar el sistema.
- mount -a: Monta todos los dispositivos configurados en el fstab que no estén montados aún.

## Formatear y preparar el dispositivo (Bonus)
Si necesitas borrar un dispositivo y darle un formato nuevo, se utiliza la familia de comandos mkfs (Make File System):

- FAT32 (Universal): sudo mkfs.vfat /dev/sdb1
- NTFS (Windows): sudo mkfs.ntfs /dev/sdb1
- EXT4 (Linux Nativo): sudo mkfs.ext4 /dev/sdb1