# Laboratorio de Git

## Objetivos

***1. Crear un repositorio en local***

- Abre tu terminal y navega hasta el directorio donde deseas crear el repositorio.

  ```Terminal bash
    $ cd 'Laboratorio de Git (Entrega)'
  ```

- Crea una carpeta con el nombre del repositorio.

  ```Terminal bash
    $ mkdir LaboratorioGit
  ```

- Ingresa a la carpeta que acabas de crear.

  ```Terminal bash
    $ cd LaboratorioGit
  ```

- Inicializa el repositorio de Git.

  ```Terminal bash
    $ git init
  ```

  > Esto creará una carpeta oculta ***.git*** y se podrá trabajar con un repositorio en local.

***2. Subir el repositorio a GitHub***

- Crea un nuevo repositorio en GitHub.

  ```[GitHub](https://github.com/)
    github.com > New repository > Create repository
  ```

- Copia el URL del repositorio que acabas de crear en GitHub

  ```Terminal bash
    Por seguridad SSH:
    git@github.com:JavierBlancoDelaCruz/LaboratorioGit.git
  ```

- Conecta tu repositorio local con el repositorio en GitHub.

  ```Terminal bash
    $ git remote add origin git@github.com:JavierBlancoDelaCruz/LaboratorioGit.git
  ```

  > origin será el nombre que se le asigna al servidor que recibirá los push.

- Verifica que la conexión se haya establecido correctamente.

  ```Terminal bash
    $ git remote -v
  ```

  > Con este comando podrá verse el repositorio con el que se ha establecido la conexión viendo el nombre que se le ha dado al servidor (origin) y la URL del mismo.

***3. Hacer un commit y un push***

- Crea un archivo en la carpeta del repositorio.

  ```Explorador de archivos de VSCode
    LaboratorioGit > nuevoarchivo.js
  ```

  > Aparecerá como "Untracked" bajo el símbolo de una U en el explorador.

- Añade el archivo al staging.

  ```Terminal bash
    git add .
  ```

  > Esto cambiará la U de *"Untracked"* por una A de "Añadido" y pasará a estar en estado *"Staged"* y por tanto, preparado para hacer un commit, ya que ahora Git sabrá que se quieren guardar esos cambios.

- Crea un commit con un mensaje descriptivo.

  ```Terminal bash
    $ git commit -m "Creado nuevoarchivo.js listo para guardar en el repositorio local"
  ```

  > El commit guarda el archivo que estaba *"Staged"* en el repositorio local.

- Sube los cambios al repositorio en GitHub.

  ```Terminal bash
    $ git push -u origin master
  ```

  > Al ser la primera vez que se suben los cambios al repositorio remoto, se usa el flag -u (enlaza la rama local con la del servidor y en caso de no existir la crea), origin (nombre asignado al servidor), master (rama local de trabajo que se sube). Como ambos reposiorios (el local y el remoto) ya estarán enlazados, el resto de veces ya solo hará falta usar git push.

***4. Crear una rama***

- Crea una rama nueva llamada "development".

  ```Terminal bash
    $ git branch development
  ```

- Cambia a la nueva rama.

  ```Terminal bash
    $ git checkout development 
  ```

  > Los pasos de creación y cambio a la rama se pueden unificar usando el comando:
  $ git checkout -b development

- Realiza algunos cambios en el archivo que creaste.

  *nuevoarchivo.js*

  ```nuevoarchivo.js
    - console.log("Soy un nuevo archivo :D");
    + console.log("Soy un  archivo modificado :)");
  ```

- Añade y haz un commit con los cambios en la rama "development".

  ```Terminal bash
    $ git add .
    $ git commit -m "nuevoarchivo.js modificado en rama development"

    O simplente de forma unificada:

    $ git commit -am "nuevoarchivo.js modificado en rama development"
  ```

- Sube los cambios a Github.

  ```Terminal bash
    $ git push -u origin development
  ```

  > Como es la primera vez que se sube esta rama de trabajo no se podrá usar solo git push porque habrá que enlazarla con el servidor que la recibirá.

***5. Hacer un merge***

- Vuelve a la rama "main".

  ```Terminal bash
    $ git checkout master
  ```

- Haz un merge de la rama "development" a la rama "main".

  ```Terminal bash
    $ git merge development
  ```

- Si no hay conflictos, los cambios realizados en la rama "development" se incorporarán a la rama "main".

  En este caso, se ha podido hacer un *fast forward merge* (se habrá hecho 1 inserción por una delección), por lo que no habrá conflictos y el *merge* se realizará sin problemas.

- Haz un push de los cambios al repositorio en GitHub.

  ```Terminal bash
    $ git push
  ```

  > Como ya se habían subido los cambios por primera vez anteriormente para esta rama, ahora sí s epuede usar directamente un git push.
  Tras este push se podrá ver en GitHub como ha cambiado el mensaje del commit en el archivo que habí aen la rama master y pasa a ser el mismo que el archivo de la rama development con la que se ha fusionado y de la que se han quedado los cambios.
