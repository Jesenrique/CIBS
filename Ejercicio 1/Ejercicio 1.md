# Ejercicio CiberKillChain - Ataque


## Enunciado

Armar una cyberkillchain usando técnicas de la matriz de Att&ck para un escenario relacionado al trabajo práctico de la carrera.

Alumno: Jesús Enrique García Garnica

El sistema víctima es una planta de tratamiento de agua compuesta de sensores de presión, bombas hidráulicas, sistemas de monitoreo basado en Raspberry pi, etc. Ubicada en un centro de salud que tiene como finalidad generar agua que cumpla con cierta normativa y que será utilizada por distintos equipos médicos.

Objetivo del ataque: Sabotear el funcionamiento de la planta de tratamiento con la finalidad de que pueda perder contrato y la competencia sea beneficiada.

## Reconnaissance
Técnicas usadas:
- T1591 - Gather Victim Org Information
https://attack.mitre.org/techniques/T1591

- T1592 - Gather Victim Host Information - hardwarek
https://attack.mitre.org/techniques/T1592/001

- T1594 - Search Victim-Owned Websites
https://attack.mitre.org/techniques/T1594

  - El sistema esta ubicado en un lugar de acceso publico donde transitan demasiadas personas sin importar la hora, permitiendo vigilar el lugar y determinar mejores horarios de alto y bajo movimiento de personas.
  - El lugar especifico donde se encuentra el sistema no esta protegido con cerraduras.
  - Es facil suplantar personal de mantenimiento y entrar directamente al sitio de instalación.
  - Sistema operativo de equipos con Windows (algunos usan Whatsapp Web)  

## Weaponization
Técnicas usadas:
- T1200 - Hardware Additions.
https://attack.mitre.org/techniques/T1200

- T1078 - Valid Accounts: Local Accounts
https://attack.mitre.org/techniques/T1078/003/

Puedo:
- Enviar mensajes de correo electronico con malware al personal con acceso al sistema para tratar de adquirir las credenciales y acceder al servidor de la web del sistema.

Decido:
- Crear un dispositivo USB que pueda correr sobre Raspberry pi y que permita alterar ciertos parámetros de manera sutil y genere fallos y paros de operación.

## Delivery
Técnica usada:
- T1589.001 - Gather Victim Identity Information
https://attack.mitre.org/techniques/T1589/001/

Puedo:
- Suplantar a un paciente haciendo pasar por perdido o confundido e ingresar al lugar donde esta ubicado el sistema.

Puedo:
- Suplantar personal de salud (enfermero) e imgresar al lugar donde esta instalado el sistema.

Decido:
- Suplantar a personal de mantenimiento con herramientas puede ser más fácil pasar desapercibido.

## Exploit 
Técnica usada:
- T1204 - User Execution: Malicious File
https://attack.mitre.org/techniques/T1204/002/

Puedo:
- Al insertar una USB, se activa automáticamente un script malicioso que establece un canal de acceso remoto vía Wi-Fi y permite la manipulación de datos.

Decido:
- Al insertar la USB en la Raspberry Pi, se ejecuta automáticamente un script malicioso diseñado para alterar progresivamente los datos recibidos de los sensores, generando fallos sutiles en el funcionamiento del sistema. 

## Installation
Técnicas usadas:
- T1546.001 - Event Triggered Execution: Change Default File Association
https://attack.mitre.org/techniques/T1546/001/

- T1037.005 - Boot or Logon Initialization Scripts
https://attack.mitre.org/techniques/T1037/005/

Puedo:
- Configurar el script para que se copie automáticamente al sistema de archivos de la Raspberry Pi y se ejecute al iniciar el dispositivo.

Decido:
- Una vez insertada la USB, el script malicioso se copia a la Raspberry Pi y se configura como un servicio del sistema que se inicia automáticamente con el encendido. Esto garantiza que el comportamiento malicioso persista incluso tras reinicios.

## Command & Control
Técnica usada:
- T1021.004 - Remote Services: SSH
https://attack.mitre.org/techniques/T1021/004/

Puedo:
- Intentar acceder al sistema vía Bluetooth si me encuentro cerca, estableciendo una conexión directa para manipulación de datos.

Decido:
- El script que se activa automáticamente al insertar la USB obtiene las credenciales de la red WiFi guardadas en el sistema, Con esta información se establece una conexión SSH desde un servidor externo hacia la Raspberry Pi, permitiendo al atacante tener control remoto persistente del sistema.
  
## Actions on Objectives
  - acceder a la base de datos, borrar, editar y eliminar datos.
  - provocar parada del sistema.
  - generar datos falsos de manera sutil que genere gastos e inversión en el sistema
