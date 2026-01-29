# GitHub & Git CLI Project
> by luisplis@gmail.com

### Configuración y Preparación

Antes de empezar, necesitas preparar tu terreno.

``git init``: Crea un nuevo repositorio local.

> Ejemplo: **git init** (convierte tu carpeta actual en un proyecto de Git).

``git clone``: Descarga un proyecto que ya existe en la nube.

> Ejemplo: **git clone https://github.com/usuario/proyecto.git**

### El Ciclo de Trabajo (Guardar cambios)

Estos son los que usarás el 90% del tiempo mientras programas.

``git status``: Te dice qué archivos has modificado y cuáles vas a guardar.

> Ejemplo: **git status** (verás archivos en rojo o verde).

``git add``: Prepara tus archivos para la "foto" (commit).

> Ejemplo: **git add index.html** (prepara solo ese archivo) o **git add .** (prepara todo) o **git add -A** (todo el proyecto).

``git commit``: Guarda la "foto" de tus cambios con un mensaje explicativo.

> Ejemplo: **git commit -m "Solucionado el error en el login"**

### Sincronización (Con la nube)

Para compartir tu código o traer el de otros.

``git push``: Sube tus cambios locales al servidor.

> Ejemplo: **git push origin main**

``git pull``: Trae los cambios del servidor y los mezcla con los tuyos (Fetch + Merge).

> Ejemplo: **git pull origin main**

``git fetch``: Solo descarga la información del servidor sin tocar tu código local.

> Ejemplo: **git fetch upstream**

### Ramas y Revisión

Para trabajar en nuevas funciones sin romper lo que ya funciona.

``git branch``: Crea o lista ramas.

> Ejemplo: **git branch nueva-funcion**

``git checkout`` (o git switch): Cambia de una rama a otra.

> Ejemplo: **git checkout nueva-funcion**

git log: Muestra el historial de lo que ha pasado.

Ejemplo: git log --oneline

## Flujo de Pull Request

**El flujo de Pull Request (PR) es el corazón de la colaboración en GitHub. No es un comando de Git en sí, sino un proceso de revisión de código.** 

### 1. Preparar el terreno (Fork & Clone)

Primero, haces una copia del proyecto original en tu cuenta y la descargas.

- Comando: gh repo fork --clone (usando GitHub CLI) o git clone <url-de-tu-fork>.

> Ejemplo: Copias el proyecto "Calculadora" para poder proponer cambios.

###2. Crear una rama (Branch)

Regla de oro: Nunca trabajes directamente en main. Crea una rama para tu mejora.

- Comando: git checkout -b feature-nueva-suma

> Ejemplo: Creas un espacio aislado llamado "feature-nueva-suma".

### 3. Trabajar y subir (Commit & Push)

Haces tus cambios, los guardas localmente y los subes a tu copia en la nube.

- Comandos:
-- git add .
-- git commit -m "Añadida función de suma"
-- git push origin feature-nueva-suma

### 4. Abrir el Pull Request (PR)

Ahora le avisas al dueño del proyecto original que tienes algo que aportar.

- Acción: En la web de GitHub aparece un botón verde "Compare & pull request" o usas el comando gh pr create.

> Ejemplo: Escribes un mensaje explicando por qué tu función de suma es mejor.

### 5. Revisión y Sync (Feedback)

Si el dueño te pide cambios, simplemente modificas tus archivos, haces otro commit y push. El PR se actualiza automáticamente. Si el proyecto original avanzó, debes sincronizarte:

- Comando: git pull upstream main

> Ejemplo: El dueño dice: "¡Genial! Pero cambia el nombre de la variable x por numero1".

6. El Cierre (Merge o rebase)

**MERGE**

- Una vez aprobado, el dueño del proyecto presiona Merge.

- Comando: git merge (repositorio upstream)

> Resultado: Tus cambios ahora forman parte del código oficial del proyecto original.

El comando merge crea un nuevo commit (llamado merge commit) que tiene dos padres: el último commit de tu rama y el último commit de la rama que quieres integrar.

**Preserva el historial original de cada rama exactamente como sucedió.**

**REBASE**

El comando rebase vuelve a escribir la historia. Toma los commits de tu rama actual y los "mueve" para que comiencen justo después del último commit de la otra rama.

- Comando: git rebase <rama>

> Resultado:  Elimina tus commits de su lugar inicial y los aplica de nuevo en el punto más reciente de la otra rama.

Modifica los hashes de tus commits originales. No hay commits de "merge" adicionales. 

**Todos los cambios se hicieron uno tras otro en la misma rama.**

### Resumen de Pasos PR - pull-request

1. Fork,Copiar repo,gh repo fork
2. Branch,Crear rama,git checkout -b mi-mejora
3. Push,Subir cambios,git push origin mi-mejora
4. PR,Proponer cambios,gh pr create
5. Merge,Integrar,(Se hace en la web de GitHub)
