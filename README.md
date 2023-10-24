# cmuchachos-2023
Taller sobre Git para la Semana de la Ciencia en la Ciudad de los Muchachos

## Pasos previos al taller
1. Instalar [git](https://git-scm.com/download/win) (Usar *64-bit Git for Windows Setup.* y dejar toda la configuración por defecto)
2. Instalar [Visual Studio Code](https://code.visualstudio.com/)
3. Nos creamos una cuenta en [Github](https://github.com/)
4. Crear una clave privada SSH y la configuramos en Github

    4.1  Abrimos Powershell

    4.2 Ejecutamos el comando `ssh-keygen -t ed25519` y presionamos enter hasta que el comando finalice, al final debe salir algo como *The key's randomart image is...*

    4.3 Accedemos a la parte de configuración de claves SSH de Github ([Link](https://github.com/settings/keys)) y pinchamos en *New SSH key* arriba a la derecha

    4.4 Ejecutamos el comando `cat ~/.ssh/id_ed25519.pub` en Powershell y copiamos el resultado que nos da, debería empezar por *ssh-ed25519...*

    4.4 Una vez estamos aqui en donde pone *Title* ponemos nuestro nombre y en *Key* ponemos el contenido que hemos copiado en el paso 3.4

    4.5 Ahora ejecutamos el siguiente comando en Powershell, esto configurará por defecto la clave que hemos creado para utilizarla en Github dentro de nuestro ordenador

    ```powershell
    $contentToAdd = @"
    Host github.com
        User git
        IdentityFile ~/.ssh/id_ed25519
        IdentitiesOnly yes
    "@
        
    Add-Content "~/.ssh/config" $contentToAdd
    ```

    4.5 Ahora para comprobar que funciona ejecutaremos el siguiente comando:
    ```
    git clone git@github.com:christiangonre/cmuchachos-2023.git
    ```
    Si el comando no da ningún error y ves una carpeta creada con el nombre cmuchachos-2023 es que todo hay ido genial!
