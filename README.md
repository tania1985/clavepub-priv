# clavepub-priv
**README: Configuración de Acceso SSH y Conexión Remota**

Este README proporciona instrucciones detalladas sobre cómo configurar el acceso SSH en GitHub y cómo conectarse al usuario admin de otra máquina utilizando claves pública y privada.

### Configuración de Acceso SSH en GitHub:

1. **Generación de Claves SSH:**
    - Abra la terminal en su sistema.
    - Ejecute el siguiente comando para generar un par de claves SSH:
      ```
      ssh-keygen -t rsa -b 4096 -C "tu_correo@ejemplo.com"
      ```
      (Reemplace "tu_correo@ejemplo.com" con su dirección de correo electrónico de GitHub).
    - Cuando se le solicite, presione "Enter" para aceptar la ubicación predeterminada del archivo de clave.
    - Ingrese una frase de contraseña segura cuando se le solicite, o simplemente presione "Enter" si no desea una.

2. **Agregar Clave SSH a ssh-agent:**
    - Inicie el agente SSH ejecutando el siguiente comando:
      ```
      eval "$(ssh-agent -s)"
      ```
    - Agregue su clave privada SSH al ssh-agent ejecutando:
      ```
      ssh-add ~/.ssh/id_rsa
      ```

3. **Agregar Clave SSH a su Cuenta de GitHub:**
    - Copie el contenido de su clave pública SSH ejecutando:
      ```
      pbcopy < ~/.ssh/id_rsa.pub
      ```
    - Inicie sesión en su cuenta de GitHub.
    - Vaya a "Settings" -> "SSH and GPG keys" -> "New SSH key".
    - Pegue su clave SSH en el campo "Key" y déle un título descriptivo.
    - Haga clic en "Add SSH key".

### Conexión al Usuario Admin de Otra Máquina mediante Claves Pública y Privada:

1. **Copiar Clave Pública SSH al Servidor Remoto:**
    - En la terminal, ejecute el siguiente comando para copiar su clave pública SSH al servidor remoto:
      ```
      ssh-copy-id admin@remoteserver
      ```
      (Reemplace "admin" con el nombre de usuario y "remoteserver" con la dirección IP o nombre de dominio del servidor remoto).

2. **Conexión SSH al Usuario Admin en la Máquina Remota:**
    - Una vez que su clave pública SSH esté instalada en el servidor remoto, puede conectarse al usuario admin ejecutando:
      ```
      ssh admin@remoteserver
      ```
      (Nuevamente, reemplace "admin" y "remoteserver" con el nombre de usuario y la dirección del servidor remoto).

Ahora está conectado al usuario admin en la máquina remota utilizando claves pública y privada SSH.

**¡Importante!**
Asegúrese de que la máquina remota tenga SSH habilitado y permita la autenticación mediante claves públicas. Además, asegúrese de tener los permisos adecuados para conectarse al usuario admin en la máquina remota.
