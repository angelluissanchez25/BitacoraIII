# BitacoraIII

## Fundamentos de Seguridad y Auditoría

### 1. Anatomía de Syslog

Como su nombre lo indica, se utiliza para que dispositivos como routers, switches, firewalls, puntos de acceso Wi-Fi y servidores Linux generen sus propios registros. Los servidores de Windows usan registros de eventos, pero pueden utilizarse junto con los servidores Syslog. Su función es almacenar eventos o mensajes de registro localmente dentro del dispositivo elegido y enviar esta información a un servidor Syslog para obtener, ordenar y filtrar todos los registros y datos que contiene.

Facilidad (Facility): Indica qué subsistema originó el mensaje (por ejemplo, auth para autenticación, cron para tareas programadas o daemon para servicios en segundo plano).
Prioridad (Severity): Define el nivel de urgencia o gravedad del evento, en una escala que va desde debug (información de depuración) hasta emerg (pánico total del sistema).

### 2. Permisos en /var/log/auth.log y Trazabilidad

Este archivo almacena información crítica sobre la seguridad del sistema. Si un usuario sin privilegios puede leerlo, podría realizar una enumeración de usuarios o descubrir credenciales que los usuarios hayan introducido por error en el campo de usuario durante un inicio de sesión fallido.

Conexión remota (SSH): En el log quedará registrado el demonio sshd, la dirección IP de origen del atacante y el punto efímero utilizado en la conexión.
Conexión local: Registrará el proceso login o gestores de pantalla, y en lugar de una IP, mostrará la terminal.

### 3. Log Management y Cumplimiento Legal

A nivel empresarial y normativo (como el RGPD), mantener los logs dispersos en las propias máquinas de producción es un riesgo inaceptable. Si un atacante compromete un servidor, su primera acción será borrar o alterar los logs locales para eliminar su rastro. Centralizar la gestión de registros (Log Management) enviándolos a un servidor externo seguro garantiza la inmutabilidad de las evidencias. Así, aunque el servidor caiga o sea vulnerado, el registro de la intrusión sobrevive en un entorno aislado y protegido, permitiendo auditorías forenses legales.

Referencias

[1]¿Qué es Syslog? Una introducción al protocolo de registro del sistema(https://blog.invgate.com/es/que-es-syslog)
[2] Canonical Ltd., "Ubuntu Server documentation," Ubuntu Documentation, 2025. [En línea]. Disponible en: https://ubuntu.com/server/docs/explanation/intro-to/security/
[3] M. B. Alonso Alegre Díez, "Gestión de Logs," Trabajo Fin de Máster, Universidad Internacional de La Rioja (UNIR), 2016. [En línea]. Disponible en: https://reunir.unir.net/bitstream/handle/123456789/3618/ALONSO-ALEGRE%20DIEZ%2C%20MARIA%20BEGO%C3%91A.pdf
