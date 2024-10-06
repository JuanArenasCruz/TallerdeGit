
# Registro de Actividad de Git

## Pasos Seguidos

1. **Configuración Inicial:**
   - Creé repositorio local, luego configuré mi nombre y correo electrónico de Git con los comandos:
     ```bash
     git init TallerdeGit # Con este comando creé el repositorio con el nombre TallerdeGit.
     git config --global user.name "JuanArenasCruz" # Este comando configuró el nombre de usuario.
     git config --global user.email "juan.arenas.cruz@correounivalle.edu.co"  # Este comando configuró el correo.
     ```

2. **Creación de Ramas:**
   - Creé una rama `feature` y realicé algunos cambios.
     ```bash
     git checkout -b feature # Creé la rama feature y me posisioné en ella.
     echo "Texto inicial" > archivo.txt # Creé el archivo.txt y escribí en él.
     git add archivo.txt # Guardé el archivo.txt.
     git commit -m "Commit inicial" # Hice el  primer commit.
     echo "Texto agregado en feature" >> archivo.txt # Le agregué más contenido al archivo.txt.
     git commit -am "Segundo commit en feature" # Realicé el segundo commit.
     echo "Tercer texto en feature" >> archivo.txt # Agregué un más contenido al archivo.txt.
     git commit -am "Tercer commit en feature" # Hice el tercer commit.
     git log # Utilicé este comando para verificar que todo se guardó correctamente.
     ```

3. **Regreso a la Rama Master y Fusión:**
   - Creé la rama `master` y fusioné los cambios de la rama `feature` usando dos técnicas.
     ```bash
     git checkout -b master # creé la rama master y me posisioné en ella.
     git merge feature  # Fusioné los cambios de la rama `feature` en la rama `master`.
     ```

   - Revertí el merge y realicé un rebase:
     ```bash
     git reset --hard HEAD~1 # Con este comando deshace la fusión, regeresndo la rama `master` a su estado anterior.
     git rebase feature # Apliqué los cambion de la rama `feature` a la rama `master`.
     git log # Verifiqué que todo se guardo.
     ```

4. **Creación de un Hotfix:**
   - Creé una rama `hotfix` y agregué un cambio crítico, luego hice un cherry-pick en la rama `master`.
     ```bash
     git checkout -b hotfix # creé la rama hotfix y me posisioné en ella.
     echo "Corrección urgente" >> archivo.txt # Agregué un cambio crítico al archivo.txt.
     git commit -am "Hotfix" # Realicé en commit 
     git checkout master # Me posicioné en la rama `master`.
     git log hotfix # Utilicé este comado para obtener el hash del commit de `hotfix`.
     git cherry-pick hotfix # Apliqué el commit de la rama `hotfix` en la rama `master.
     ```

5. **Uso de Reflog:**
   - Exploré el historial y restauré un commit perdido utilizando `git reflog`.
     ```bash
     git reflog # Este comando me permitió ver el historial completo de mi repositorio.
     git checkout 0485f46 # Restauré el commit seleccionado.
     ```

6. **Creación de Conflictos:**
   - Creé conflictos entre dos ramas modificando las mismas líneas de código en ambas ramas y luego los resolví.
     ```bash
     git checkout feature # Me posicioné en la rama `feature`.
     echo "Cambio en feature" > conflicto.txt # Creé y modifiqué el archivo conflicto.txt
     git add conflicto.txt # Guardé el archivo conflicto.txt.
     git commit -am "Cambio en feature" # Realicé el commit con el mensaje de "Cambio en feature".
     
     git checkout master # Me posicioné en la rama `master`.
     echo "Cambio en master" > conflicto.txt # Modifiqué el archivo conflicto.txt
     git add conflicto.txt # Guardé el archivo conflicto.txt.
     git commit -am "Cambio en master" # Hice el commit con el mensaje de "Cambio en master"
     
     git merge feature  # Esto generó un conflicto
     ```

7. **Resolución de Conflictos:**
   - Abrí el archivo `conflicto.txt`, resolví el conflicto manualmente y luego hice un commit.
     ```bash
     vim conflicto.txt # Utilicé este comando para abrir el archivo y modificarlo
     
     "<<<<<<< HEAD
     Cambio en master
     =======
     Cambio en feature
     >>>>>>> feature"  # Borré todo el contenido del archivo conflicto.txt para eliminar conflicto reemplazándolo.
       
     
     "Cambio en master y cambio en feature" # Reemplacé lo anterior por esto .

     git add conflicto.txt # Guardé el archivo modificado.
     git commit -m "Resuelto conflicto entre master y feature" # Hice el commit final, verificando que el conflicto se resolvió.
     ```

8. **Resultados:**
   - Se completó el merge con éxito y el conflicto se resolvió. El flujo de trabajo de Git fue comprendido a través de la práctica de ramas, commits, merge, rebase, cherry-pick, y la resolución de conflictos.
