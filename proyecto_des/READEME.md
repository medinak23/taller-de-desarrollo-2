Configurar el nombre y correo de usuario en Git:

bash
Copiar código
git config --global user.name "edwin"
git config --global user.email "edwin.franco@correounivalle.edu.co"
Estos comandos establecen el nombre y el correo electrónico que se usarán globalmente en Git para los commits. Esto es necesario para que Git sepa quién realiza los cambios en los proyectos.

Intentar crear una rama nueva antes de inicializar el repositorio:

bash
Copiar código
git checkout -b feature
Aquí intentas crear y cambiar a una nueva rama llamada feature, pero Git da un error: "not a git repository". Esto ocurre porque no has inicializado un repositorio Git en tu carpeta actual.

Inicializar un repositorio Git:

bash
Copiar código
git init proyecto_des
Este comando crea un nuevo repositorio Git vacío en la carpeta proyecto_des.

Moverse al directorio del proyecto:

bash
Copiar código
cd proyecto_des
Cambias de directorio para trabajar dentro del repositorio recién creado.

Crear una nueva rama feature:

bash
Copiar código
git checkout -b feature
Aquí, creas la rama feature y cambias a ella. Las ramas permiten trabajar en funcionalidades o cambios específicos sin afectar la rama principal.

Crear un archivo y hacer un commit:

bash
Copiar código
echo "texto inicial" > archivo.txt
git add archivo.txt
git commit -m "commit inicial"
echo "texto inicial" crea un archivo llamado archivo.txt con ese contenido.
git add archivo.txt agrega el archivo al área de staging (preparación para commit).
git commit -m "commit inicial" guarda los cambios en el historial de Git.
Hacer más cambios y commits:

bash
Copiar código
echo "texto agregado en feature" >> archivo.txt
git commit -am "segundo commit en feature"
echo "Nuevo texto agregado" >> archivo.txt
git commit -am "tercer commit en feature"
Cada bloque de comandos:

Agrega más texto a archivo.txt.
Usa git commit -am para añadir todos los cambios en archivos ya rastreados y hacer el commit.
Intentar cambiar a la rama master:

bash
Copiar código
git checkout master
Aquí recibes un error porque la rama master no existe aún. Luego, creas la rama:

bash
Copiar código
git checkout -b master
Fusionar cambios de feature en master:

bash
Copiar código
git merge feature
No se fusiona nada porque ambos están actualizados. Luego usas git reset para revertir el último commit en master y haces un rebase:

bash
Copiar código
git reset --hard HEAD~1
git rebase feature
Esto aplica los cambios de feature en master.

Crear una rama hotfix para una corrección urgente:

bash
Copiar código
git checkout -b hotfix
echo "Corrección urgente" >> archivo.txt
git commit -am "Hotfix"
git checkout -b hotfix crea y cambia a la rama hotfix para una corrección urgente.
Haces la corrección en el archivo archivo.txt y luego haces el commit.
Usar cherry-pick para aplicar el hotfix en master:
bash
Copiar código
git checkout master
git cherry-pick hotfix
El comando git cherry-pick hotfix aplica los cambios realizados en la rama hotfix en master.

Gestionar un conflicto de fusión:
bash
Copiar código
git checkout feature
echo "cambio en feature" > conflicto.txt
git checkout master
echo "cambio en master" > conflicto.txt
Aquí creas un conflicto al modificar el mismo archivo (conflicto.txt) en ambas ramas (feature y master).

Luego intentas fusionar:

bash
Copiar código
git merge feature
Se genera un conflicto de fusión, y Git te pide que lo resuelvas manualmente. Después de resolver el conflicto, haces el commit final con la corrección.

Verificar el estado final:
bash
Copiar código
git status
Esto indica que el árbol de trabajo está limpio y todos los cambios han sido confirmados correctamente.

Crear y editar un archivo READEME.md:
bash
Copiar código
touch READEME.md
code READEME.md
Creas un archivo vacío llamado READEME.md (probablemente querías escribir README.md) y lo abres con tu editor de código.

El conflicto se resolvió manualmente editando el archivo conflicto.txt, eliminando las marcas de conflicto insertadas por Git y seleccionando qué cambios querías conservar. Después de esto, se añadió el archivo modificado con git add y se completó la fusión con un commit.