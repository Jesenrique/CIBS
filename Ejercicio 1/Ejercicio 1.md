# Ejercicio CiberKillChain - Ataque


## Enunciado

Armar una cyberkillchain usando técnicas de la matriz de Att&ck para un escenario relacionado al trabajo práctico de la carrera.

* Jesús Enrique García Garnica


### 
* Objetivo del ataque: Sabotear el funcionamiento de la institución donde se encuentra instalado el sistema con la finalidad de que pueda perder contrato y la competencia sea beneficiada.

## Reconnaissance
Técnicas usadas:
- T1591 - Gather Victim Org Information
https://attack.mitre.org/techniques/T1591

-T1592 - Gather Victim Host Information - hardwarek
https://attack.mitre.org/techniques/T1592/001

-T1594 - Search Victim-Owned Websites
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

  -Añadir un dispositivo USB sobre raspberry pi que actua como concentrador de datos los sensores para alterar los datos.
  -Enviar mensajes de correo electronico con malware al personal con acceso al sistema para tratar de adquirir las credenciales y acceder al servidor de la web del sistema.

## Delivery
- T1586 - Compromise Accounts
https://attack.mitre.org/techniques/T1586/

- Envió a persona que suplanta personal de mantenimiento, el cual logra ingresar al lugar e inyectar script en la raspberry pi.
- Identificó personas que usan whatsapp web durante su labor y envio malware.
- Identficó al personal con acceso al sistema e intento enviar malware mediante correo electronico.

## Exploit 
- T1204 - User Execution: Malicious File
https://attack.mitre.org/techniques/T1204/002/

  - Al insetar hardware en raspberry se activa script malicioso.
  - Malware enviado mediante pishing se activa al dar click.
  
## Installation
  - El archivo corre en segundo plano y persiste tras reinicios analizando la data de entrada.
  - 

## Command & Control
 - via ssh desde las raspberry se crea un canal que permita conexiones remotas.
 - Acceder a las credenciales del wifi y obtener acceso desde un lugar cercano. 
  
## Actions on Objectives
  - acceder a la base de datos, borrar, editar y eliminar datos.
  - provocar parada del sistema.
  - generar datos falsos de manera sutil que genere gastos e inversión en el sistema
