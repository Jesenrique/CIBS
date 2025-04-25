# Ejercicio CiberKillChain - Defensa

## Enunciado

Diseñar una estrategia defensiva basada en la matriz MITRE ATT&CK para el mismo escenario utilizado en la parte ofensiva.

Alumno: Jesús Enrique García Garnica

Sistema a proteger: Planta de tratamiento de agua utilizada en un centro de salud, con sensores, bombas, y sistemas de monitoreo basados en Raspberry Pi.

Objetivo del ataque: analizar cada fase del ataque previamente planteado y proponer controles, técnicas de detección, y medidas de mitigación para evitar saboteos y perdida de contratos.

## Reconnaissance
Técnicas usadas:

- User Behavior Analysis
https://d3fend.mitre.org/technique/d3f:UserBehaviorAnalysis/

- Physical Access Mediation
https://d3fend.mitre.org/technique/d3f:PhysicalAccessMediation/

- Password Authentication
https://d3fend.mitre.org/technique/d3f:PasswordAuthentication/

  - Se recomienda instalar cámaras de videovigilancia con inteligencia artificial que detecten rostros, midan el tiempo de permanencia de personas en áreas sensibles y generen alertas por comportamiento inusual.

  - Al no poder instalar cerraduras para ejecutar paradas del sistema, se debe implementar un sistema de alarma sonora que se active ante cualquier entrada con un debido log.

  - Configurar firewalls y políticas de red para bloquear el acceso a aplicaciones y sitios web no autorizados, como WhatsApp Web, desde los dispositivos del sistema.

## Weaponization
Técnicas usadas:
- Sender MTA Reputation Analysis
https://d3fend.mitre.org/technique/d3f:SenderMTAReputationAnalysis/

- User Training
https://attack.mitre.org/mitigations/M1017/

- Network Allowlists
https://attack.mitre.org/mitigations/M0807/

Puedo:
  - Capacitar al personal en prevención de amenazas, uso seguro de la red y detección de actividades sospechosas.

  - Colocar la Raspberry Pi dentro de un gabinete cerrado con cerradura, evitando manipulaciones no autorizadas.

Decido:
  - Implementar un sistema de validación física y lógica del hardware, asegurando que solo personal autorizado pueda interactuar con la Raspberry Pi (con cerradura física + whitelist de dispositivos).


## Delivery
Técnica usada:
- Biometric Authentication
https://d3fend.mitre.org/technique/d3f:BiometricAuthentication/

Decido:
- Establecer control de acceso biométrico obligatorio para pacientes y personal de la empresa y visitantes ingresen a zonas críticas del sistema.

## Exploit 
Técnica usada:
- Exploit Protection
https://attack.mitre.org/mitigations/M1050/

- Software Process and Device Authentication
https://attack.mitre.org/mitigations/M0813/

Puedo:
- Inhabilitar físicamente los puertos USB de la Raspberry Pi para evitar conexiones no autorizadas.
- Implementar un sistema de monitoreo de archivos que detecte y alerte sobre modificaciones no autorizadas.

Decido:
- Aplicar una política de autenticación para dispositivos extraíbles, permitiendo únicamente aquellos previamente firmados y validados por el sistema.

## Installation
Técnicas usadas:
- Restrict File and Directory Permissions
https://attack.mitre.org/mitigations/M1022/

Puedo:
- Denegar cualquier intento de instalación de servicios o tareas al inicio del sistema sin aprobación explícita.
- Restringir permisos de ejecución en carpetas del sistema y monitorear cambios.

Decido:
- Implementar mecanismos automáticos que detecten y eliminen archivos sospechosos para evitar persistencia de código malicioso y se tenga un constante monitoreo del sistema.

## Command & Control
Técnica usada:
- Multi-factor Authentication
https://attack.mitre.org/mitigations/M1032/

Puedo:
- Permitir únicamente conexiones Bluetooth firmadas y validadas en una lista blanca.

Decido:
- Permitir únicamente conexiones Bluetooth firmadas y validadas en una lista blanca. Encriptar todas las contraseñas de red almacenadas en el sistema para evitar su extracción. Denegar cualquier intento de conexión SSH que no sea firmada, que no provenga de una IP o dirección MAC previamente registrada.
  
## Actions on Objectives
  - Cifrar la data de la base de datos. Implementar control de acceso a la BD por rol. Denegar eliminación de datos.
  - Implementar un sistema redundante o sistema espejo que actúe como mecanismo de verificación, comparando en tiempo real la lógica de operación contra la data real de los sensores y actuadores. Este sistema bloquea o alerta cualquier comando que contradiga el estado esperado, evitando acciones peligrosas o maliciosas.
  - Implementar modelos de IA para analizar datos y genere una alerta cuando detecte situaciones anomalas y fuera del contexto normal de la operación.