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