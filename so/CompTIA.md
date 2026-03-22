<div align="center">
  <img src="../assets/linux.svg" width="200" alt="Logo de Linux">
</div>

## Índice
- [Conceptos Fundamentales de Seguridad (Tema 1)](#conceptos-fundamentales-de-seguridad-tema-1)
  - [La Tríada CIA y el No Repudio](#la-tríada-cia-y-el-no-repudio)
  - [Marco de Ciberseguridad (NIST)](#marco-de-ciberseguridad-nist)
  - [Gestión de Identidad y Acceso (IAM)](#gestión-de-identidad-y-acceso-iam)
  - [Controles de Seguridad](#controles-de-seguridad)
    - [Clasificación por Implementación](#clasificación-por-implementación)
    - [Tipos Funcionales (Cuándo actúan)](#tipos-funcionales-cuándo-actúan)
  - [Análisis de Deficiencias (Gap Analysis)](#análisis-de-deficiencias-gap-analysis)
  - [Funciones y Responsabilidades](#funciones-y-responsabilidades)
  - [Unidades de Negocio de Seguridad](#unidades-de-negocio-de-seguridad)
    - [SOC (Security Operations Center)](#soc-security-operations-center)
    - [Desarrollo y Operaciones (DevSecOps)](#desarrollo-y-operaciones-devsecops)
    - [Respuesta a Incidentes (CIRT / CSIRT / CERT)](#respuesta-a-incidentes-cirt--csirt--cert)
- [Tipos de Amenazas (Tema 2)](#tipos-de-amenazas-tema-2)
  - [Conceptos Clave: Vulnerabilidad, Amenaza y Riesgo](#conceptos-clave-vulnerabilidad-amenaza-y-riesgo)
  - [Atributos de los Actores de Amenazas](#atributos-de-los-actores-de-amenazas)
  - [Perfiles de Atacantes](#perfiles-de-atacantes)
    - [Hackers y Hacktivistas](#hackers-y-hacktivistas)
    - [Amenazas Avanzadas (Estados Nación y Crimen Organizado)](#amenazas-avanzadas-estados-nación-y-crimen-organizado)
    - [Amenazas Internas (Insiders)](#amenazas-internas-insiders)
  - [Superficie de Ataque](#superficie-de-ataque)
  - [Vectores Tecnológicos](#vectores-tecnológicos)
    - [Software Vulnerable](#software-vulnerable)
    - [Vectores de Red](#vectores-de-red)
    - [Vectores basados en Señuelos (Baiting)](#vectores-basados-en-señuelos-baiting)
    - [Vectores basados en Mensajes](#vectores-basados-en-mensajes)
  - [El Factor Humano: Ingeniería Social](#el-factor-humano-ingeniería-social)
    - [Suplantación y Pretexting](#suplantación-y-pretexting)
    - [Phishing y Pharming](#phishing-y-pharming)
  - [Cadena de Suministro (Supply Chain)](#cadena-de-suministro-supply-chain)
  - [Compromiso de Correo Electrónico Empresarial (BEC)](#compromiso-de-correo-electrónico-empresarial-bec)
  - [Typosquatting (Allanamiento de error tipográfico)](#typosquatting-allanamiento-de-error-tipográfico)
  - [Desinformación y Malinformación](#desinformación-y-malinformación)
  - [Watering Hole Attack (Ataque de abrevadero)](#watering-hole-attack-ataque-de-abrevadero)
- [Algoritmos Criptográficos (Tema 3)](#algoritmos-criptográficos-tema-3)
  - [Cifrado Simétrico (Symmetric Encryption)](#cifrado-simétrico-symmetric-encryption)
  - [Cifrado Asimétrico (Asymmetric Encryption)](#cifrado-asimétrico-asymmetric-encryption)
  - [Hashing](#hashing)
  - [Firmas Digitales](#firmas-digitales)
  - [Longitud de la Clave](#longitud-de-la-clave)
  - [Infraestructura de Clave Pública (PKI)](#infraestructura-de-clave-pública-pki)
  - [Autoridades Certificadoras (CA)](#autoridades-certificadoras-ca)
  - [Certificados Digitales](#certificados-digitales)
  - [El Proceso de Registro (CSR)](#el-proceso-de-registro-csr)
  - [Ciclo de Vida y Revocación](#ciclo-de-vida-y-revocación)
  - [Almacenamiento Seguro](#almacenamiento-seguro)
  - [Soluciones Criptográficas](#soluciones-criptográficas)
  - [Cifrado de Almacenamiento (Confidencialidad)](#cifrado-de-almacenamiento-confidencialidad)
  - [Cifrado de Bases de Datos](#cifrado-de-bases-de-datos)
  - [Intercambio de Claves y Secreto de Reenvío Perfecto (PFS)](#intercambio-de-claves-y-secreto-de-reenvío-perfecto-pfs)
  - [Protección de Contraseñas (Salting y Stretching)](#protección-de-contraseñas-salting-y-stretching)
  - [Tecnologías Emergentes y Ofuscación](#tecnologías-emergentes-y-ofuscación)
- [Implementación de la gestión de identidades y accesos (Tema 4)](#implementación-de-la-gestión-de-identidades-y-accesos-tema-4)
  - [Autenticación](#autenticación)
    - [Gestión de Contraseñas](#gestión-de-contraseñas)
    - [Autenticación de Multifactores (MFA)](#autenticación-de-multifactores-mfa)
    - [Autenticación Biométrica](#autenticación-biométrica)
    - [Tokens de Autenticación](#tokens-de-autenticación)
    - [Autenticación sin Contraseña (Passwordless)](#autenticación-sin-contraseña-passwordless)
  - [Autorizacion](#autorizacion)
    - [Modelos de Control de Acceso](#modelos-de-control-de-acceso)
    - [Principio de Mínimo Privicio](#principio-de-mínimo-privicio)
    - [Ciclo de Vida de la Cuenta (Aprovisionamiento)](#ciclo-de-vida-de-la-cuenta-aprovisionamiento)
    - [Políticas y Restricciones de Acceso](#políticas-y-restricciones-de-acceso)
    - [Administración de Acceso con Privilegios (PAM)](#administración-de-acceso-con-privilegios-pam)
  - [Administración](#administración)
    - [Windows](#windows)
    - [Linux](#linux)
    - [Servicios de Directorio (LDAP)](#servicios-de-directorio-ldap)
    - [Inicio de Sesión Único (SSO) con Kerberos](#inicio-de-sesión-único-sso-con-kerberos)
    - [Federación de Identidades](#federación-de-identidades)
    - [Protocolos de Federación y API](#protocolos-de-federación-y-api)
- [Arquitectura de Red Empresarial (Tema 5)](#arquitectura-de-red-empresarial-tema-5)
  - [Modelado de Red (Modelo OSI)](#modelado-de-red-modelo-osi)
  - [Infraestructura de Conmutación (Capa 2)](#infraestructura-de-conmutación-capa-2)
  - [Infraestructura de Enrutamiento y Segmentación (Capa 3)](#infraestructura-de-enrutamiento-y-segmentación-capa-3)
  - [Análisis de la Superficie de Ataque](#análisis-de-la-superficie-de-ataque)
  - [Aislamiento Físico (Air-Gap)](#aislamiento-físico-air-gap)
  - [Consideraciones Arquitectónicas Modernas](#consideraciones-arquitectónicas-modernas)
  - [Ubicación del Dispositivo y Defensa en Profundidad](#ubicación-del-dispositivo-y-defensa-en-profundidad)
  - [Atributos de los Dispositivos](#atributos-de-los-dispositivos)
  - [Cortafuegos (Firewalls)](#cortafuegos-firewalls)
  - [Servidores Proxy](#servidores-proxy)
  - [Sistemas de Detección y Prevención (IDS/IPS)](#sistemas-de-detección-y-prevención-idsips)
  - [Tecnologías Avanzadas](#tecnologías-avanzadas)
  - [Balanceadores de Carga](#balanceadores-de-carga)
  - [Arquitectura de Acceso Remoto](#arquitectura-de-acceso-remoto)
  - [VPN de Capa de Transporte (TLS)](#vpn-de-capa-de-transporte-tls)
  - [VPN de Capa de Red (IPsec)](#vpn-de-capa-de-red-ipsec)
  - [Acceso a Escritorio Remoto](#acceso-a-escritorio-remoto)
  - [Shell Seguro (SSH)](#shell-seguro-ssh)
  - [Gestión Fuera de Banda (OOB) y Servidores de Salto](#gestión-fuera-de-banda-oob-y-servidores-de-salto)
  

# Conceptos Fundamentales de Seguridad (Tema 1)

La seguridad de la información (Infosec) es la protección de los datos contra accesos no autorizados, ataques o daños. Se basa en un proceso continuo de evaluación, configuración y supervisión de sistemas.

El objetivo principal es garantizar que la información de una organización esté protegida frente a amenazas internas y externas.

## La Tríada CIA y el No Repudio

Para que un sistema sea seguro, debe cumplir con tres propiedades fundamentales conocidas como Tríada CIA:

- Confidencialidad: Solo personas autorizadas pueden leer la información.
  - Ejemplo: Cifrar un correo electrónico para que solo el destinatario pueda leerlo.
- Integridad: Los datos no se modifican sin autorización durante su almacenamiento o transferencia.
  - Ejemplo: Un sistema de firmas digitales que detecta si un contrato fue alterado.
- Disponibilidad: La información está accesible cuando las personas autorizadas la necesitan.
  - Ejemplo: Mantener servidores con respaldo eléctrico para que la web no se caiga.
- No Repudio: Garantiza que una persona no pueda negar haber realizado una acción (crear o enviar algo).Normalmente se consigue mediante:
  - Firmas digitales
  - Certificados digitales
  - Registros de auditoría (logs)
- Ejemplo: Un registro de auditoría que confirma quién firmó un documento legal.

## Marco de Ciberseguridad (NIST)

El National Institute of Standards and Technology (NIST) desarrolló un marco de ciberseguridad muy utilizado para organizar las funciones de seguridad.

Este marco divide las tareas en cinco funciones principales:

- Identificar: Desarrollar políticas y evaluar riesgos y activos.
  - Ejemplos:
    - Inventario de activos
    - Evaluación de riesgos
    - Definición de políticas de seguridad
- Proteger: Instalar y operar activos de TI con seguridad integrada.
  - Ejemplos:
    - Control de acceso
    - Cifrado de datos
    - Formación de empleados
- Detectar: Monitoreo continuo para hallar amenazas.
  - Ejemplos:
    - Sistemas de monitoreo
    - Análisis de registros
    - Alertas de seguridad
- Responder: Analizar y erradicar amenazas detectadas.
  - Ejemplos:
    - Contener un ataque
    - Investigar la causa
    - Comunicar el incidente
- Recuperar: Restaurar sistemas y datos tras un ataque.
  - Ejemplos:
    - Restauración desde copias de seguridad
    - Recuperación de servicios
    - Mejora de controles tras el incidente

## Gestión de Identidad y Acceso (IAM)

La Gestión de Identidad y Acceso (IAM) controla cómo los usuarios interactúan con los recursos de un sistema.

En este modelo existen dos elementos:
- Sujetos (Subjects): usuarios o dispositivos
- Objetos (Objects): recursos como archivos, bases de datos o servidores

El proceso de acceso se divide en cuatro pasos:
- Identificación: Crear una cuenta única (ID) para el usuario.
  - Ejemplo: Introducir un nombre de usuario
- Autenticación: Probar que eres quien dices ser (ej. mediante una contraseña o certificado)
  - Ejemplo:
    - Contraseña
    - Token
    - Certificado digital
    - Huella biométrica
- Autorización: Determinar qué permisos tienes sobre un recurso (ej. solo lectura o control total).
  - Ejemplo:
    - Solo lectura
    - Escritura
    - Control total
- Registro (Accounting): Rastrear las acciones realizadas por el sujeto en los registros de auditoría.
  - Sirve para:
    - Auditorías
    - Investigaciones de incidentes
    - Cumplimiento normativo
  - Este modelo también se conoce como AAA:
    - Authentication
    - Authorization
    - Accounting

## Controles de Seguridad

Los controles son herramientas o procedimientos para proteger la confidencialidad, integridad y disponibilidad.

### Clasificación por Implementación

- Gerencial: Supervisión y selección de controles (ej. evaluación de riesgos).
  - Evaluaciones de riesgo
  - Políticas de seguridad
  - Auditorías
- Operacional: Ejecutado por personas (ej. guardias de seguridad o capacitación).
  - Guardias de seguridad
  - Procedimientos de respuesta a incidentes
  - Formación de empleados
  - Control físico de instalaciones
- Técnico: Sistemas de hardware/software (ej. firewalls, antivirus).
  - Firewalls
  - Antivirus
  - Sistemas IDS/IPS
  - Cifrado
- Físico: Protección de instalaciones (ej. cerraduras, cámaras, alarmas).

### Tipos Funcionales (Cuándo actúan)

Los controles también se clasifican según cuándo actúan frente a una amenaza.

- Preventivo: Actúa antes del ataque para bloquearlo (ej. listas de acceso, parches).
  - Listas de control de acceso
  - Parcheo de sistemas
  - Autenticación multifactor
- De Detección: Actúa durante el ataque para identificarlo (ej. registros/logs).
  - Sistemas de monitoreo
  - Registros de actividad
  - IDS
- Correctivo: Actúa después del ataque para reducir el impacto (ej. copias de seguridad/backups).
  - Restaurar un sistema tras una intrusión
- Recovery: Permite restaurar operaciones normales después de un ataque.
  - Restaurar sistemas desde copias de seguridad tras un ransomware.
- Otros:
  - Directivo: Reglas de comportamiento (ej. políticas, contratos).
    - Políticas de seguridad
    - Normas de uso aceptable
  - Disuasivo: Desalienta psicológicamente al atacante (ej. avisos de multas).
    - Avisos legales
    - Cámaras visibles
    - Carteles de monitoreo
  - Compensatorio: Sustituto si el control principal no es posible (ej. aislar un sistema viejo que no admite parches).
    - Aislar un sistema antiguo que no puede recibir parches de seguridad.

## Análisis de Deficiencias (Gap Analysis)

El Gap Analysis es el proceso de comparar el estado actual de seguridad de una organización con el estado ideal definido por un estándar o marco de referencia.

- Ejemplo: Comparar los controles actuales de una empresa con el marco del National Institute of Standards and Technology.

- Objetivo
  - Identificar controles faltantes
  - Detectar configuraciones incorrectas
  - Priorizar inversiones en seguridad

## Funciones y Responsabilidades

La seguridad dentro de una organización requiere que diferentes roles tengan responsabilidades definidas.

- Política de Seguridad: Documento formal que define cómo se protegerán los recursos.
- Responsabilidades Típicas:
  - Directores/Propietarios: Responsabilidad general y legal.
  - Personal Técnico (ej. ISSO): Implementar, mantener y monitorear la política.
  - Personal No Técnico: Cumplir con las políticas y la ley.

## Unidades de Negocio de Seguridad

Para que la seguridad funcione en una organización grande, se suelen crear equipos o centros especializados

### SOC (Security Operations Center)

Es el "cuartel general" donde los profesionales supervisan y protegen los activos de la empresa (finanzas, ventas, etc.) las 24 horas.

- Función: Proporcionar personal y recursos para detectar y responder rápido a incidentes.
- Ejemplo: Un equipo de analistas que recibe una alerta de que alguien está intentando entrar al servidor desde otro país a las 3 a.m. y bloquea el acceso de inmediato.

### Desarrollo y Operaciones (DevSecOps)

Este concepto se basa en "moverse a la izquierda" (shift left). Significa que la seguridad no se añade al final de un proyecto, sino que se integra desde la planificación y el diseño.

- Concepto clave: Las operaciones de seguridad se tratan como desarrollo de software, usando automatización mediante código para mejorar la detección.
- Ejemplo: Al programar una aplicación bancaria, el equipo de seguridad revisa el código cada vez que el programador sube un cambio, en lugar de esperar a que la app esté terminada para buscar errores.

### Respuesta a Incidentes (CIRT / CSIRT / CERT)

Los equipos de respuesta a incidentes actúan como punto central cuando ocurre un incidente de seguridad.

- Siglas comunes:
  - CIRT – Computer Incident Response Team
  - CSIRT – Computer Security Incident Response Team
  - CERT – Computer Emergency Response Team
- Funciones principales:
  - Identificar incidentes
  - Contener ataques
  - Erradicar amenazas
  - Recuperar sistemas

A veces trabajan dentro del SOC o como equipo independiente.

- Ejemplo: Si una empresa sufre un ataque de ransomware, el CSIRT decide:
  - aislar los sistemas
  - analizar el malware
  - restaurar los datos desde backups.

# Tipos de Amenazas (Tema 2)

Para defender una red, primero hay que entender el riesgo. El riesgo no es algo abstracto, sino el resultado de una fórmula:

> Riesgo = Probabilidad × Impacto

Esto significa que un evento poco probable pero con gran impacto puede ser tan peligroso como uno muy probable con impacto moderado.

## Conceptos Clave: Vulnerabilidad, Amenaza y Riesgo

Antes de analizar ataques es importante entender cuatro conceptos básicos.

- Activo (Asset)
Un activo es cualquier recurso que tiene valor para una organización y debe protegerse.
- Ejemplos:
  - Datos de clientes
  - Servidores
  - Sistemas de pago
  - Propiedad intelectual
  - Infraestructura de red

- Vulnerabilidad: Es una debilidad en un sistema que puede ser explotada.
  - Puede existir en:
    - hardware
    - software
    - configuraciones
    - procesos
    - seguridad física
  - Ejemplo: 
    - Software sin actualizar
    - Contraseña débil
    - Puerto de red innecesariamente abierto
- Amenaza: Una amenaza es la posibilidad de que alguien o algo explote una vulnerabilidad. El camino o método utilizado para realizar el ataque se llama vector de ataque.
  - Ejemplo: Un atacante aprovecha una vulnerabilidad en un servidor web para ejecutar código malicioso.
- Riesgo: El riesgo es el nivel real de peligro para la organización. Se calcula evaluando:
  - la probabilidad de que ocurra el ataque
  - el impacto que tendría sobre los activos

## Atributos de los Actores de Amenazas

Para clasificar a un atacante, el examen de CompTIA analiza varios atributos.

- Ubicación: Indica si el atacante está dentro o fuera de la organización.
  - Interno: empleado o persona con acceso autorizado
  - Externo: atacante desde Internet
- Sofisticación / Capacidad: Nivel técnico del atacante.
  - Bajo: uso de herramientas automáticas
  - Alto: desarrollo de exploits propios
- Recursos / Financiamiento: Capacidad económica o tecnológica del atacante.
  - Individuos con recursos limitados
  - Grupos criminales organizados
  - Gobiernos o agencias estatales
- Motivación: Razón por la que el atacante realiza el ataque.
  - Ejemplos:
    - dinero
    - espionaje
    - ideología política
    - sabotaje
    - venganza personal

## Perfiles de Atacantes

### Hackers y Hacktivistas

- Hacker Autorizado (White Hat): Tiene permiso para buscar fallos (Pentesting).
- Hacker No Autorizado (Black Hat): Entra en sistemas sin permiso para fines maliciosos.
- Atacante sin formación (Script Kiddie): Alguien con poca habilidad que solo usa herramientas que otros hicieron.
- Hacktivista: Ataca para promover una agenda política o social (ej. robar datos para avergonzar a una empresa).

### Amenazas Avanzadas (Estados Nación y Crimen Organizado)

- Estado Nación: Atacantes financiados por gobiernos con grandes recursos técnicos. Sus objetivos suelen ser:
  - espionaje
  - sabotaje
  - desinformación
- APT (Amenaza Persistente Avanzada) Una APT es un ataque prolongado y dirigido donde el atacante intenta mantener acceso a la red durante largos periodos. Características principales:
  - ataques sigilosos
  - objetivos específicos
  - acceso persistente a sistemas comprometidos
- Crimen Organizado: Grupos criminales que buscan principalmente beneficio económico. Actividades comunes:
  - fraude
  - robo de datos
  - ransomware
  - extorsión
- Competidores: Empresas que intentan robar secretos comerciales o propiedad intelectual para obtener ventaja en el mercado.

### Amenazas Internas (Insiders)

Las amenazas internas provienen de personas que ya tienen acceso legítimo a la organización.

- Insiders malintencionados: Empleados que buscan beneficio personal o venganza.
  - Ejemplos:
    - robo de datos
    - sabotaje de sistemas
- Insiders no intencionales: Usuarios que causan problemas por error o descuido.
  - Ejemplos:
    - perder un USB con datos sensibles
    - enviar información confidencial al destinatario equivocado
- Shadow IT: Ocurre cuando empleados utilizan:
  - software
  - servicios en la nube
  - aplicaciones
  - sin aprobación del departamento de TI.
Esto crea nuevos riesgos de seguridad.

## Superficie de Ataque

La superficie de ataque es la suma total de todos los puntos donde un atacante puede intentar entrar o extraer datos de un sistema. Comprender los métodos de infiltración es esencial para implementar los controles adecuados.

Incluye:
- aplicaciones
- servicios de red
- dispositivos
- usuarios


- Vector de amenaza/ataque: Es la ruta específica o herramienta que usa el atacante.
  - email malicioso
  - puerto abierto
  - sitio web comprometido
  - ingeniería social
- Estrategia fundamental: Reducir la superficie de ataque limitando el acceso únicamente a:
  - servicios necesarios
  - puertos esenciales
  - usuarios autorizados

## Vectores Tecnológicos

### Software Vulnerable

Casi ningún software es perfecto. Las fallas en el código permiten eludir controles.
- Estrategia: 
  - Gestión de parches.
  - Actualizar software para corregir vulnerabilidades conocidas.
  - Si una aplicación no puede actualizarse, se puede aplicar un control compensatorio, como aislarla de la red.
- Escaneo de vulnerabilidades:
  - Escaneo con agentes
    - software instalado en cada sistema
    - permite análisis más detallado
  - Escaneo sin agentes
    - análisis remoto desde la red
    - no requiere instalar software en los equipos

### Vectores de Red

- Ataque Remoto: No requiere una sesión previa; el atacante envía código a través de la red.
- Ataque Local: Requiere que el atacante ya tenga una sesión iniciada o credenciales válidas.
  - una sesión activa
  - acceso físico
  - credenciales válidas
- Puntos débiles comunes:
  - puertos abiertos innecesarios
  - falta de cifrado en comunicaciones
  - contraseñas por defecto
  - servicios mal configurados

### Vectores basados en Señuelos (Baiting)

Se ofrece algo atractivo para que la víctima caiga en la trampa:

- Dispositivos extraíbles: Dejar un USB infectado en un parking (USB Drop) esperando que alguien lo conecte.
- Archivos maliciosos: Ocultar código en PDFs, imágenes o instaladores de software.

### Vectores basados en Mensajes

Los atacantes usan comunicaciones para engañar a las víctimas.

- Email e IM: Uso de archivos adjuntos o enlaces.
- SMS (Smishing): Muy difícil de monitorear por las empresas ya que depende del proveedor de telefonía.
- Clic Cero (Zero-click): Los ataques más peligrosos, donde el exploit se activa solo con recibir el mensaje, sin que el usuario haga nada.

## El Factor Humano: Ingeniería Social

Se considera al ser humano como el eslabón más débil del sistema. "Hackear al humano" es manipularlo para que revele información o realice acciones.

### Suplantación y Pretexting

- Suplantación (Impersonation): Pretender ser otra persona (soporte técnico, un jefe, un repartidor).
- Pretexting: Crear una historia creíble (el "pretexto") para ganar confianza.
- Tácticas psicológicas:
  - Urgencia/Miedo: "Si no lo haces ahora, se borrará tu cuenta".
  - Autoridad: "Soy el director de TI y necesito tu clave".
  - Consenso/Agrado: "Todos los de tu equipo ya me dieron acceso".
  - Simpatía / agrado: El atacante intenta generar confianza personal.

### Phishing y Pharming

- Phishing: Uso de ingeniería social + suplantación de identidad (normalmente vía email) para robar credenciales.
- Pharming: Es más técnico; redirige al usuario de un sitio web legítimo a uno falso dañando la resolución de nombres (DNS). El usuario escribe la URL correcta, pero va al sitio del atacante.

## Cadena de Suministro (Supply Chain)

En lugar de atacarte a ti, atacan a tus proveedores.

- Proveedores y Socios: Un atacante puede entrar en tu red usando las credenciales de un proveedor de mantenimiento o un servicio externo.
- MSP (Proveedores de Servicios Gestionados): Son objetivos críticos porque tienen acceso a las redes de cientos de clientes a la vez.

## Compromiso de Correo Electrónico Empresarial (BEC)

A diferencia del phishing masivo, el BEC (Business Email Compromise) es un ataque de "guante blanco" altamente sofisticado y dirigido.

- El Objetivo: Una persona específica con poder de decisión (ejecutivos, directores financieros o gerentes con acceso a presupuestos).
- La Táctica: El atacante realiza un reconocimiento previo exhaustivo para imitar el lenguaje y tono de un colega, socio o proveedor de confianza.
- Sin rastro técnico: A menudo no incluyen enlaces sospechosos ni malware, sino que usan puramente la persuasión para que la víctima autorice transferencias bancarias fraudulentas o entregue datos confidenciales.
- Suplantación real: El atacante puede incluso intentar tomar el control de una cuenta de correo legítima de la empresa para enviar los mensajes desde dentro.

## Typosquatting (Allanamiento de error tipográfico)

Es una técnica que se aprovecha de los errores que cometen los usuarios al escribir una dirección en el navegador.

- Nombres de dominio similares: El atacante registra dominios como gogle.com o ejenplo.com (conocidos como dominios primos o doppelganger).
- Subdominios secuestrados: Usar un dominio de confianza para crear un subdominio engañoso, por ejemplo: empresa.enmicrosoft.com. El usuario ve "microsoft.com" y baja la guardia.
- Inconsistencias en el cliente de correo: Manipular el campo "De" (From) para que el nombre mostrado no coincida con la dirección de correo real.

## Desinformación y Malinformación

- Desinformación: Intención deliberada de engañar mediante noticias o datos falsos.
- Malinformación: La repetición de rumores o datos falsos por parte de terceros sin que estos tengan necesariamente la intención de engañar (el atacante usa a otros para amplificar su mentira).
- SEO Malicioso: Usar estas tácticas para que sitios falsos aparezcan en los primeros resultados de búsqueda de Google.

## Watering Hole Attack (Ataque de abrevadero)

En lugar de atacar una red corporativa muy protegida, el atacante identifica un sitio web de terceros que los empleados suelen visitar por confianza o necesidad.

- proceso:
  - El atacante identifica sitios que los empleados suelen visitar.
  - Compromete ese sitio web.
  - Inserta código malicioso.
  - Cuando los empleados acceden al sitio, sus equipos se infectan.

# Algoritmos Criptográficos (Tema 3)

La criptografía ("escritura secreta") es el arte de asegurar la información mediante su codificación. Se diferencia de la "seguridad por oscuridad" en que, aunque un atacante sepa dónde está el mensaje, no puede entenderlo sin la clave.

- Texto plano: Mensaje original sin cifrar.
- Texto cifrado: Mensaje encriptado e ilegible.
- Algoritmo: El proceso matemático para cifrar y descifrar.
- Criptoanálisis: El arte de romper sistemas criptográficos (ej. ataques de fuerza bruta que prueban todas las llaves posibles).

## Cifrado Simétrico (Symmetric Encryption)

Utiliza la misma clave secreta tanto para cifrar como para descifrar.

- Características: Es muy rápido y se usa para el cifrado masivo de datos.
- Desventaja: El intercambio de claves es difícil; si un atacante intercepta la clave, la seguridad se rompe.

> Ejemplo: Alice cifra un archivo "HolaMundo" con una clave. Envía el archivo ilegible a Bob, quien usa esa misma clave para leerlo.

## Cifrado Asimétrico (Asymmetric Encryption)

Utiliza un par de claves relacionadas: una pública (que todos conocen) y una privada (secreta y personal).

- Funcionamiento: Si cifras con la clave pública de alguien, solo su clave privada puede descifrarlo.
- Uso: Es más lento que el simétrico, por lo que suele usarse para intercambiar claves simétricas de forma segura.

> Ejemplo: Bob publica su clave pública. Alice la usa para cifrar un mensaje. Solo Bob, con su clave privada, puede leer el contenido.

## Hashing

Un algoritmo de hash convierte cualquier entrada en una cadena de bits de longitud fija.

- Propiedades: Es unidireccional (no se puede volver al mensaje original) y resistente a colisiones (dos entradas diferentes no deben dar el mismo hash).
- Objetivo: Garantizar la integridad (que los datos no hayan cambiado).
- Algoritmos comunes:
  - SHA-256: Muy seguro, produce 256 bits.
  - MD5: 128 bits, más rápido pero menos seguro hoy en día.

> Ejemplo: Al descargar un archivo, calculas su hash y lo comparas con el del fabricante. Si son iguales, el archivo no ha sido manipulado.

## Firmas Digitales

Combinan el hashing y el cifrado asimétrico para garantizar autenticidad, integridad y no repudio.

- Alice crea un hash de su mensaje y lo cifra con su clave privada (esta es la firma).
- Bob recibe el mensaje, descifra la firma con la clave pública de Alice para obtener el hash original.
- Bob calcula su propio hash del mensaje recibido. Si ambos coinciden, sabe que el mensaje es de Alice y no fue alterado.

## Longitud de la Clave

La seguridad depende de qué tan grande es el espacio de claves (rango de valores posibles).

- Bits: A más bits, más difícil es un ataque de fuerza bruta.
- Ejemplos de seguridad equivalente:
  - AES (Simétrico): 128 o 256 bits.
  - RSA (Asimétrico): Requiere 2048 bits para ser seguro.
  - ECC (Curva Elíptica): Logra la misma seguridad que RSA pero con solo 256 bits, lo que lo hace más eficiente.

## Infraestructura de Clave Pública (PKI)

La Infraestructura de Clave Pública (PKI) es el marco de hardware, software, personas y procesos necesarios para crear, gestionar, distribuir, utilizar, almacenar y revocar certificados digitales. Su objetivo principal es establecer confianza.

## Autoridades Certificadoras (CA)

La CA es la entidad de confianza que emite certificados digitales.

- Función: Valida la identidad de quien solicita un certificado y lo firma digitalmente para garantizar su autenticidad.
- Jerarquía de Confianza:
  - CA Raíz (Root CA): Es la autoridad máxima. Su certificado está autofirmado. En organizaciones grandes, la CA raíz se suele mantener offline para protegerla.
  - CA Intermedias: Emiten certificados a los usuarios finales en nombre de la CA raíz, lo que añade una capa de seguridad.

## Certificados Digitales

Un certificado es un "contenedor" para una clave pública.

- Estándar X.509: Es el formato estándar utilizado por la mayoría de los certificados
- Atributos clave:
  - Nombre común (CN): Antiguamente identificaba el dominio (ej. www.google.com), pero hoy está en desuso.
  - Nombre Alternativo del Sujeto (SAN): El estándar actual. Permite que un solo certificado proteja múltiples dominios o direcciones IP.

## El Proceso de Registro (CSR)

Para obtener un certificado, no envías tu clave privada. Envías una CSR (Certificate Signing Request).

- Generas tu par de claves (pública y privada).
- Creas la CSR con tu clave pública e información de identidad.
- La CA firma la CSR y te devuelve el certificado completado.

## Ciclo de Vida y Revocación

Los certificados no duran para siempre. Pueden ser invalidados antes de su fecha de vencimiento si la clave privada se pierde o es robada.

- CRL (Lista de Revocación de Certificados): Una lista publicada por la CA con todos los certificados revocados. Los navegadores la consultan periódicamente.
- OCSP (Online Certificate Status Protocol): Un método más rápido que la CRL. El navegador pregunta en tiempo real por el estado de un certificado específico.

## Almacenamiento Seguro

Las claves son el "eslabón débil" si se guardan como archivos comunes.

- HSM (Hardware Security Module): Un dispositivo físico dedicado a generar y proteger claves criptográficas.
- TPM (Trusted Platform Module): Un chip en la placa base de las computadoras que almacena claves de cifrado y asegura el arranque del sistema.
- Custodia de Claves (Key Escrow): Almacenar una copia de las claves con un tercero de confianza para poder recuperarlas si se pierden.
  - M de N: Control que requiere que un quórum de personas (ej. 2 de 3 administradores) autorice la recuperación de una clave.

## Soluciones Criptográficas

Para elegir la solución correcta, primero debemos saber dónde están los datos:

- Datos en reposo (At rest): Almacenados en discos, SSD o cintas.
- Datos en tránsito (In transit): Viajando por la red (web, email).
- Datos en uso (In use): Procesándose en la memoria RAM o CPU.

## Cifrado de Almacenamiento (Confidencialidad)

Como el cifrado asimétrico es lento, para cifrar archivos grandes se usa un sistema híbrido:

- DEK (Data Encryption Key): Una clave simétrica (rápida) cifra los datos.
- KEK (Key Encryption Key): Una clave asimétrica (segura) cifra a la DEK.
- FDE (Full Disk Encryption): Cifra todo el disco (incluyendo sectores vacíos y metadatos). Protege contra el robo físico de la laptop.
- Cifrado de archivos/volúmenes: Cifra carpetas o particiones específicas (ej. BitLocker, FileVault).

## Cifrado de Bases de Datos

- TDE (Transparent Data Encryption): Cifra la base de datos completa a nivel de archivos.
- Always Encrypted: Los datos se cifran en el cliente y llegan cifrados al servidor; el administrador de la base de datos no puede ver el contenido, solo el usuario con la clave.

## Intercambio de Claves y Secreto de Reenvío Perfecto (PFS)

Para que dos personas hablen por internet de forma segura, necesitan intercambiar una clave simétrica sin que nadie la vea.

- Diffie-Hellman (D-H): Permite que dos partes generen un secreto compartido a través de un canal público inseguro.
- PFS (Perfect Forward Secrecy): Asegura que, si alguien roba la clave privada del servidor en el futuro, no pueda descifrar las sesiones pasadas. Utiliza claves efímeras (temporales) que se borran tras cada sesión.

## Protección de Contraseñas (Salting y Stretching)

Las contraseñas no se guardan tal cual, se guardan sus hashes. Pero para evitar ataques de "tablas arcoíris" (diccionarios de hashes):

- Salting (Salado): Se añade un valor aleatorio a la contraseña antes de hacer el hash para que dos usuarios con la misma contraseña tengan hashes diferentes.
- Key Stretching: El proceso de hash se repite miles de veces (ej. PBKDF2) para ralentizar los ataques de fuerza bruta.

## Tecnologías Emergentes y Ofuscación

- Blockchain: Un libro de transacciones descentralizado donde cada bloque tiene el hash del anterior, garantizando que nadie pueda borrar o alterar el pasado sin romper la cadena.
- Esteganografía: Ocultar un mensaje dentro de otro archivo (ej. un texto secreto dentro de una foto de un gatito).
- Tokenización: Sustituir un dato sensible (como el número de tarjeta) por un "token" aleatorio. Es reversible pero el token no tiene valor por sí mismo si es robado.

# Implementación de la gestión de identidades y accesos (Tema 4)

## Autenticación

La autenticación es el proceso de verificar que un usuario es quien dice ser. Un buen diseño debe equilibrar confidencialidad (que las credenciales no se filtren), integridad (que no sean falsificables) y disponibilidad (que el proceso sea ágil para el usuario).

- Factores de Autenticación:
  - Algo que conoces: Contraseñas, frases de contraseña (más largas y seguras) o PIN (específicos de un dispositivo).
  - Algo que tienes: Tarjetas inteligentes, llaves de seguridad o teléfonos (factores de propiedad).
  - Algo que eres: Biometría (huellas, rostro, iris).
  - Algún lugar donde estás: Basado en la ubicación geográfica o dirección IP.

### Gestión de Contraseñas

Las políticas de contraseñas son críticas para mitigar ataques. Se recomienda:

- Longitud y Complejidad: Requisitos mínimos para dificultar ataques de fuerza bruta.
- Caducidad: Aunque el NIST ya no recomienda el cambio periódico forzado si no hay evidencia de compromiso, muchos sistemas aún lo usan.
- Administradores de Contraseñas: Herramientas (como LastPass o iCloud Keychain) que generan contraseñas aleatorias y las almacenan en una "bóveda" protegida por una contraseña maestra.

### Autenticación de Multifactores (MFA)

La MFA combina dos o más factores diferentes (ej. una contraseña + una huella digital). Usar dos contraseñas no es MFA, ya que ambas pertenecen al mismo factor (conocimiento).

- 2FA (Autenticación de dos factores): Es un subconjunto de MFA que utiliza exactamente dos factores.

### Autenticación Biométrica

Consiste en el registro (creación de una plantilla matemática) y la posterior comparación durante el acceso. Sus métricas de eficacia son:

- FRR (Tasa de Falso Rechazo): Error tipo I (inconveniente para el usuario).
- FAR (Tasa de Falsa Aceptación): Error tipo II (riesgo de seguridad grave).
- CER (Tasa de Error de Cruce): El punto donde FRR y FAR son iguales; se usa para comparar la precisión de diferentes sistemas.

### Tokens de Autenticación

- Tokens Físicos:
  - OTP (Contraseña de un solo uso): Basada en tiempo (TOTP) o en contador (HOTP).
  - Claves de Seguridad: Dispositivos USB/NFC (como YubiKey) que usan estándares como FIDO U2F.
- Tokens Blandos (Soft Tokens): Aplicaciones en el móvil (Google Authenticator, Microsoft Authenticator) que generan códigos o reciben notificaciones push. Son más seguros que los SMS, los cuales son vulnerables a interceptación.

### Autenticación sin Contraseña (Passwordless)

Este modelo elimina el factor de conocimiento. Utiliza estándares como FIDO2 y WebAuthn.

- El usuario usa un gesto local (PIN de Windows Hello o Touch ID).
- El dispositivo (autenticador) genera un par de claves.
- La clave pública se registra en el servicio web (parte de confianza).
- La atestación (ratificación) permite al dispositivo demostrar que es una raíz de confianza legítima sin identificar de forma única al individuo, protegiendo su privacidad.

## Autorizacion

La autorización es la fase de la gestión de identidades y accesos (IAM) que rige cómo se asignan privilegios a usuarios y servicios en una red. Su objetivo es gestionar el impacto de estas asignaciones y garantizar la responsabilidad de las acciones realizadas tanto por usuarios regulares como administrativos.

### Modelos de Control de Acceso

Un modelo de control de acceso define los principios bajo los cuales los usuarios reciben derechos y permisos sobre los recursos.

- Control de Acceso Discrecional (DAC)
  - Definición: Se basa en la primacía del propietario del recurso.
  - Funcionamiento: El propietario tiene control total y puede modificar la Lista de Control de Acceso (ACL) para otorgar derechos a otros.
  - Características: Es el modelo más flexible y el predeterminado en Windows y Linux.Debilidad: Es difícil de administrar de forma centralizada y vulnerable al abuso de cuentas comprometidas.
- Control de Acceso Obligatorio (MAC)
  - Definición: Se basa en niveles de habilitación de seguridad y etiquetas de clasificación (ej. Secreto, Confidencial).
  - Funcionamiento: El sistema impone reglas no discrecionales que ninguna cuenta de usuario puede cambiar.
  - Reglas Críticas:
    - Read Down: Un usuario solo puede leer archivos de su nivel o inferior.
    - Write Up: Evita que usuarios con alta autorización repliquen información en documentos de menor nivel para prevenir filtraciones.
- Control de Acceso Basado en Funciones (RBAC)
  - Definición: Los permisos se definen según las tareas o funciones laborales (roles).
  - Funcionamiento: Los usuarios adquieren derechos de forma implícita al ser asignados a una función o grupo de seguridad, no directamente.
  - Escalabilidad: Es más eficiente para organizaciones grandes que la asignación individual de permisos.
- Control de Acceso Basado en Atributos (ABAC)
  - Definición: El modelo más detallado, donde el acceso se decide mediante una combinación de atributos del sujeto, del objeto y del contexto.
  - Atributos comunes: Dirección IP, sistema operativo, hora del día o ubicación geográfica.

### Principio de Mínimo Privicio

Otorgar a una entidad solo los derechos mínimos necesarios para completar su tarea autorizada

- Beneficio: Mitiga el riesgo si una cuenta es comprometida.
- Riesgo de Acumulación: Se debe evitar la acumulación de autorizaciones, donde un usuario conserva privilegios de funciones anteriores que ya no necesita

### Ciclo de Vida de la Cuenta (Aprovisionamiento)

El aprovisionamiento es el proceso de configurar una cuenta siguiendo estándares de buenas prácticas.

- Verificación de identidad: Confirmar la identidad legal y realizar comprobaciones de antecedentes.
- Emisión de credenciales: Registro de contraseñas, biométricos o tokens.Asignación de activos: Entrega de hardware y software necesario.
- Creación de permisos: Configuración de derechos según el modelo elegido (RBAC, MAC, etc.).
- Desaprovisionamiento: Eliminación de derechos y desactivación de la cuenta cuando el empleado deja la empresa.

### Políticas y Restricciones de Acceso

- Atributos y Perfiles
  - Una cuenta se define por un SID (Identificador de Seguridad), nombre y credencial.
  - En entornos Windows, los GPO (Objetos de Directiva de Grupo) se usan para definir y aplicar estas políticas a nivel de dominio o unidad organizacional (OU).
- Restricciones Basadas en Contexto
  - Ubicación: Restricción por dirección IP o geolocalización (GPS).
  - Tiempo:
    - Restricción horaria: Horas permitidas para iniciar sesión.
    - Tiempo de viaje imposible: Alerta si se intenta iniciar sesión desde dos ubicaciones distantes en un tiempo físicamente imposible.

### Administración de Acceso con Privilegios (PAM)

La PAM se enfoca en proteger las cuentas que pueden realizar cambios críticos en el sistema.
- Estación de Trabajo Administrativa Segura (SAW): Equipos con superficie de ataque reducida exclusivos para tareas administrativas.
- Modelos de implementación:
  - Elevación temporal: Uso de comandos como sudo o UAC.
  - Bóveda de contraseñas: Las credenciales se "sacan" de un repositorio por tiempo limitado bajo justificación.
  - Credenciales efímeras: Cuentas que se crean para una tarea y se destruyen al finalizar.

## Administración

La administración de identidades gestiona cómo se identifican las entidades y cómo se verifica esa identidad en diferentes entornos (locales, de red o remotos).

| Protocolo | Base tecnica | Uso Principal|
|-----------|-------------|-------------|
| `Kerberos` | Tickets / Simétrico |Redes internas (Active Directory)|
| `SAML` | XML |SSO en aplicaciones Web / Empresa|
| `OAuth` | JSON / Tokens |Autorización de API y Apps móviles|
| `LDAP` | X.500 |Consulta y gestión de directorios|


### Windows

- Inicio de sesión local: El servicio LSASS compara la credencial con un hash en la base de datos SAM (Security Accounts Manager).
- Inicio de sesión de red: Utiliza protocolos como Kerberos o NTLM para validar la identidad ante un controlador de dominio.
- Inicio de sesión remoto: Se realiza a través de VPN, Wi-Fi empresarial o portales web, creando una conexión segura entre el cliente y el servidor de autenticación.

### Linux

- Los nombres de usuario se guardan en /etc/passwd.
- Los hashes de las contraseñas se almacenan en /etc/shadow.
- PAM (Pluggable Authentication Module): Marco que permite integrar diferentes métodos de autenticación (tarjetas inteligentes, servicios de directorio, etc.).

### Servicios de Directorio (LDAP)

Un servicio de directorio almacena información sobre usuarios, equipos y grupos de forma centralizada.

- LDAP (Lightweight Directory Access Protocol): El estándar más común (basado en X.500).
- Nombre Distinguido (DN): Identificador único de un objeto compuesto por atributos:
  - CN (Common Name): Nombre del objeto (ej. bobby).
  - OU (Organizational Unit): Unidad organizativa (ej. Marketing).
  - DC (Domain Component): Componentes del dominio (ej. dc=google, dc=com).

### Inicio de Sesión Único (SSO) con Kerberos

El SSO permite al usuario autenticarse una vez y acceder a múltiples sistemas sin reintroducir credenciales.

- KDC (Key Distribution Center): El intermediario de confianza que consta de dos servicios:
  - AS (Authentication Service): Emite el TGT (Ticket Granting Ticket).
  - TGS (Ticket Granting Service): Emite los tickets de servicio para acceder a aplicaciones específicas.
- Seguridad: Utiliza marcas de tiempo para evitar ataques de repetición y admite autenticación mutua (el servidor también demuestra su identidad al cliente).

### Federación de Identidades

La federación permite que una empresa confíe en las identidades gestionadas por otra red (ej. usar tu cuenta de Google para entrar en Twitter).

Componentes Clave:
- IdP (Identity Provider): El servicio que posee la identidad del usuario y lo autentica.
- SP (Service Provider) / RP (Relying Party): El recurso al que el usuario quiere acceder y que confía en el IdP.

### Protocolos de Federación y API

- SAML (Security Assertion Markup Language)
  - Uso: Principalmente para aplicaciones web y nubes federadas.
  - Formato: Basado en XML y transmitido por HTTP/HTTPS o SOAP.
  - Funcionamiento: El IdP firma digitalmente una "afirmación" (assertion) que el SP verifica para otorgar acceso.
- OAuth y OpenID Connect
  - OAuth (Open Authorization): Diseñado para autorizar el acceso a recursos (APIs) sin compartir la contraseña. Utiliza tokens de acceso en formato JWT (JSON Web Token).
  - OpenID Connect (OIDC): Una capa de identidad sobre OAuth que permite la autenticación (confirmar quién es el usuario).

# Arquitectura de Red Empresarial (Tema 5)

La arquitectura de red es la selección y colocación de medios, dispositivos y protocolos para admitir flujos de trabajo empresariales seguros.

- Infraestructura: Medios y dispositivos que admiten la conectividad básica.
- Aplicaciones: Servicios que se ejecutan sobre la infraestructura (ej. correo, facturación).
- Activos de datos: Información creada y almacenada.

## Modelado de Red (Modelo OSI)

Para analizar la seguridad, se utiliza el modelo de Interconexión de Sistemas Abiertos (OSI):

- Capa 1 (Física): Cables, fibra óptica, ondas de radio.
- Capa 2 (Enlace de datos): Conmutación (Switches) y direcciones MAC.
- Capa 3 (Red): Enrutamiento (Routers) y direcciones IP.
- Capa 4 (Transporte): Protocolos TCP (confiable) y UDP (no confiable).
- Capa 7 (Aplicación): Servicios finales como navegación web (HTTP) o DNS.

## Infraestructura de Conmutación (Capa 2)

La conmutación local organiza cómo los nodos se conectan físicamente en una LAN.

- Cableado estructurado: Uso de puertos de pared, patch panels y switches.
- Switch de Capa 3: Dispositivo que combina funciones de conmutación y enrutamiento.
- Seguridad del puerto:
  - Filtrado MAC: Limita qué dispositivos pueden conectarse según su dirección física.
  - 802.1X (EAPOL): Protocolo de autenticación basado en puertos que utiliza un servidor RADIUS para validar a cualquier dispositivo antes de darle acceso.

## Infraestructura de Enrutamiento y Segmentación (Capa 3)

El enrutamiento permite la creación de redes lógicas y subredes mediante direcciones IP.

- VLAN (Virtual LAN): Segmenta hosts en diferentes dominios de difusión aunque estén en el mismo switch físico. Por ejemplo, separar teléfonos VoIP de estaciones de trabajo.
- Zonas de Seguridad:
  - Zona Pública: Internet (no confiable).
  - Zona Desmilitarizada (DMZ): Contiene servidores de cara al público (web, correo) que aceptan conexiones externas pero tienen acceso restringido a la red interna.
  - Zona Privada (LAN): Intranet empresarial con altos niveles de confianza.

## Análisis de la Superficie de Ataque

La superficie de ataque es la suma de todos los puntos donde un atacante puede intentar entrar.

- Defensa en profundidad: Implementar múltiples capas de protección (controles físicos, lógicos y administrativos).
- Riesgos Comunes:
  - Redes "planas": Si no hay segmentación, una vez que el atacante entra al perímetro, tiene libertad total de movimiento lateral.
  - Shadow IT: Hardware o software instalado sin supervisión del departamento de TI.

## Aislamiento Físico (Air-Gap)

- Definición: Hosts o redes que no tienen conexión física ni inalámbrica con ninguna otra red externa.
- Casos de uso: Autoridades de Certificación (CA) raíz, sistemas de control industrial críticos o estaciones para análisis de malware.
- Vector de riesgo: El intercambio de datos mediante memorias USB es el principal punto de vulnerabilidad.

## Consideraciones Arquitectónicas Modernas

Al diseñar una red, se deben balancear varios factores:

- Escalabilidad: Capacidad de aumentar o disminuir recursos según la carga de trabajo. Las redes locales (on-premises) suelen tener baja escalabilidad comparadas con la nube.
- Disponibilidad y Resiliencia: Garantizar que el firmware esté actualizado y que existan acuerdos de nivel de servicio (SLA) cuando se depende de terceros.
- Transferencia de Riesgo: Contratar servicios externos para administrar la infraestructura bajo penalizaciones si fallan las métricas de rendimiento.

## Ubicación del Dispositivo y Defensa en Profundidad

La selección de controles se rige por el principio de defensa en profundidad, protegiendo zonas críticas mediante controles en cada capa del modelo OSI

Tipos de Controles por Ubicación:

- Controles Preventivos: Se colocan usualmente en el borde de un segmento (ej. cortafuegos) para garantizar confidencialidad e integridad.
- Controles Detectivos: Se ubican dentro del perímetro para monitorear el tráfico entre hosts e identificar amenazas que evadieron el borde.
- Controles Correctivos: Situados en el flujo de tráfico para mitigar errores o irregularidades detectadas.

## Atributos de los Dispositivos

Los atributos determinan cómo se integra un dispositivo en la topología.

- Pasivo vs. Activo:
  - Pasivo: No requiere configuración en el host ni transferencia de datos directa (ej. sensores de monitoreo).
  - Activo: Realiza análisis o filtrado y requiere credenciales o que los hosts lo usen como puerta de enlace.
- En línea (Inline): El dispositivo es parte física del cableado. No requiere cambios en la IP o topología de enrutamiento.
- Modos de Falla:
  - Apertura automática (Fail-open): Prioriza la disponibilidad; el acceso se conserva si el dispositivo falla.
  - Cierre automático (Fail-close): Prioriza la seguridad; el acceso se bloquea ante una falla.

## Cortafuegos (Firewalls)

Son controles preventivos que filtran el tráfico según reglas de una Lista de Control de Acceso (ACL).

Tipos de Filtrado y Capacidades:

- Filtrado de Paquetes: Inspecciona encabezados IP (direcciones origen/destino), protocolos (TCP/UDP/ICMP) y puertos.
- Sin Estado (Stateless): Analiza cada paquete de forma independiente. Es rápido pero vulnerable a ataques complejos.
- Inspección con Estado (Stateful): Rastrea sesiones activas en una tabla de estados. Si un paquete pertenece a una conexión permitida, pasa sin más inspección.
- Capa 7 (Capa de Aplicación): Inspecciona la carga útil para verificar que el protocolo coincida con el puerto (ej. detectar malware usando el puerto 80).

## Servidores Proxy

Funcionan bajo un modelo de almacenamiento y reenvío, deconstruyendo y reconstruyendo paquetes.

- Proxy Directo (Forward): Gestiona el tráfico saliente de clientes internos hacia internet (ej. filtro de contenido web).
- Proxy Inverso (Reverse): Gestiona el tráfico entrante desde internet hacia servidores internos, aplicando reglas de filtrado antes de reenviar la solicitud.

## Sistemas de Detección y Prevención (IDS/IPS)

- IDS (Detección): Analiza el tráfico en tiempo real y genera alertas o registros si coincide con una firma, pero no bloquea el tráfico. Utiliza sensores pasivos (puertos SPAN o TAP).
- IPS (Prevención): Dispositivo inline capaz de responder activamente para detener ataques, como bloquear el origen o restablecer la conexión.

## Tecnologías Avanzadas

- NGFW (Next-Generation Firewall): Combina cortafuegos tradicional con IPS, inspección profunda de paquetes (DPI) y conocimiento de aplicaciones (Capa 7).
- UTM (Unified Threat Management): Centraliza múltiples funciones (firewall, antimalware, spam, etc.) en un solo dispositivo. Ideal para PYMES, pero crea un único punto de falla.
- WAF (Web Application Firewall): Protege específicamente servidores web y bases de datos contra inyecciones de código y ataques DoS a nivel de aplicación.

## Balanceadores de Carga

Distribuyen las solicitudes entre varios servidores para mejorar la escalabilidad y disponibilidad.

- Capa 4: Decisiones basadas en IP y puertos.
- Capa 7: Decisiones basadas en URL, cookies o tipos de datos.
- Afinidad/Persistencia: Asegura que un cliente se mantenga conectado al mismo servidor durante su sesión.

## Arquitectura de Acceso Remoto

El acceso remoto implica que el dispositivo del usuario no tiene una conexión física directa a la red local.

- VPN (Red Privada Virtual): Es el modelo estándar actual. Utiliza un túnel cifrado para mantener la privacidad de los datos a través de los enrutadores de los ISP.
- VPN de Cliente a Sitio (Remote Access): Utilizada por teletrabajadores para conectar su host a la puerta de enlace (gateway) VPN de la empresa.
- VPN de Sitio a Sitio: Conecta oficinas completas (sucursales) con la oficina central de forma automática.
- Túnel de Host a Host: Asegura el tráfico entre dos equipos específicos cuando la red interna no es de confianza.

## VPN de Capa de Transporte (TLS)

Utiliza certificados digitales para la autenticación y el cifrado.

- Funcionamiento: El certificado del servidor identifica la puerta de enlace. Se puede requerir autenticación mutua si el cliente también presenta un certificado.
- Protocolos: Puede usar TCP (más fácil para cortafuegos) o UDP (mejor rendimiento para voz/video, conocido como DTLS).
- Seguridad: Se deben usar versiones modernas (TLS 1.2 o 1.3). Las anteriores están obsoletas.

## VPN de Capa de Red (IPsec)

Opera en la Capa 3 del modelo OSI, lo que permite asegurar todo el tráfico sin configurar aplicaciones individuales.

- Protocolos Principales:
  - AH (Authentication Header): Proporciona integridad y autenticación (hash de todo el paquete), pero no cifra los datos (no hay confidencialidad).
  - ESP (Encapsulating Security Payload): Proporciona cifrado, integridad y autenticación. Es el protocolo más utilizado.

- Intercambio de Claves de Internet (IKE):
Es el protocolo que gestiona la autenticación mutua y el intercambio de claves (Asociación de Seguridad - SA).
  - IKEv2: Es la versión preferida actualmente. Admite autenticación EAP (para servidores RADIUS), recorrido NAT (para pasar por routers domésticos) y MOBIKE (mantiene la conexión activa al cambiar entre Wi-Fi y datos móviles).

## Acceso a Escritorio Remoto

Permite interactuar gráficamente con un host remoto (servidor de terminal).

- RDP (Remote Desktop Protocol): Protocolo de Microsoft, cifrado de forma predeterminada.
- VNC (Virtual Network Computing): Alternativa multiplataforma utilizada por diversos proveedores.
- VPN HTML5 (Clientless): Permite el acceso al escritorio directamente desde el navegador web sin instalar software cliente, utilizando WebSockets.

## Shell Seguro (SSH)

Es el estándar para la administración remota por línea de comandos y transferencia de archivos (SFTP).

- Autenticación: Utiliza un par de claves (pública/privada). La clave pública se instala en el servidor y la privada permanece con el usuario.
- Gestión de Claves: Si una clave privada se compromete, se debe revocar la clave pública del servidor inmediatamente.
- Comandos básicos:
  - ssh usuario@ip: Conexión básica.
  - ssh-keygen: Genera el par de claves.
  - scp: Copia archivos de forma segura entre hosts.

## Gestión Fuera de Banda (OOB) y Servidores de Salto

Técnicas para administrar la infraestructura de forma aislada del tráfico de producción.

- Gestión en Banda (In-band): El tráfico administrativo comparte la misma red que los usuarios. Debe estar cifrado (SSH, TLS, RDP).
- Gestión Fuera de Banda (OOB): Utiliza una red dedicada físicamente o conexiones serie/módem para administrar dispositivos. Es más seguro y funciona incluso si la red principal falla.
- Servidor de Salto (Jump Server/Bastion Host): Es un host ultra-protegido que sirve como único punto de entrada para administrar otros servidores. Los administradores se conectan primero al servidor de salto y, desde allí, acceden a la red de gestión.
