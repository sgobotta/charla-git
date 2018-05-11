# Introducción a GIT

### ¿Por qué Git?

Somos varios en un proyecto, o trabajo práctico:  
¿Cómo compartimos nuestro código con unx compañerx?  
¿Cómo hacemos para poder trabajar al mismo tiempo? No siempre queremos esperar que nuestrx compañerx termine una actualización para poder continuar trabajando.  
¿Cómo sabemos cuándo y sobre qué estuvo trabajando otrx compañerx?

Git es un programa que nos permite versionar código, de manera tal que podamos:
+ juntar nuestro propio código con el de otrx
+ volver a versiones anteriores de nuestros archivos
+ poder administrar todo aquel código que sabemos que funciona como esperamos
que funcione
+ flexibilizar el trabajo en paralelo entre integrantes para el desarrollo de nuevas características.

### Conceptos básicos a saber

Git trabaja con repositorios donde hay archivos o, mejor dicho, contenido.
Un Repositorio no es más que un directorio. En nuestro caso, un directorio con
archivos de texto que contienen el código que escribimos.  
Los Repositorios pueden ser **locales** y **remotos**. Entonces, existirá un
repositorio remoto en alguna Url, accesible por todo el grupo de trabajo, y
también el mismo repositorio en la computadora de cada integrante del grupo.

Cuando empezamos a utilizar git para un proyecto, el repositorio remoto está vacío, es decir, no tiene contenido.

#### Publicar cambios (push)

Cuando queremos compartir nuestro trabajo con lxs demás, lo que hacemos es
subir los cambios del repositorio **local** al repositorio **remoto**. Lo que
estaríamos haciendo es un **push** del repositorio **local** al repositorio **remoto**. De alguna manera lo que en realidad hacemos es incluir nuestro código en el repositorio que todxs ven, es decir, sincronizarlo con el trabajo que acabamos de hacer.

#### Obtener cambios (pull)

Ahora supongamos que nuestrx compañerx estuvo trabajando en cierta funcionalidad
y nos dice que hizo **push** al repositorio remoto. Lo que posiblemente
querramos hacer es traernos sus cambios a nuestro repositorio local. En Git lo llamamos **pull** de un repositorio.
Cada vez que hacemos **pull** del repositorio remoto obtendremos todos los
cambios que **no** tengamos en nuestro repositorio.


#### ¿Cómo se gestionan los cambios en Git? (commit)
Supongamos que ya escribimos nuestra primer Clase, sabemos que funciona y queremos guardar el gran trabajo que hicimos. Lo que queremos hacer es un **commit** de nuestro código. Estamos guardando nuestros cambios en el repositorio **local**, o sea que no estamos afectando el trabajo de otrxs. Asimismo, los otrxs no saben en qué estuvimos trabajando.

Pensemos en un **commit** como el contenido de los cambios que realizamos. El **commit** puede estar compuesto por el contenido de uno o varios archivos.
Al hacer **push** del repositorio local al repositrio remoto, lo que subimos es uno o varios **commit**.

### Estructura de los Repositorios I

#### Commit

Con lo visto antes podemos entender que los repositorios tienen archivos, que fueron subidos por **commits** en cierta fecha. La historia de un repositorio se basa en ellos.

A través de ellos podemos ver qué contenido de cierto archivo fue agregado o
eliminado (por ejemplo, qué lineas de código fueron subidas). **Son la línea
en el tiempo de los cambios que sufrió un repositorio**.

***Para tener en cuenta:*** los **commit** representan el contenido de los cambios realizados y están identificados unívocamente por un hash. Se guardan localmente y no afectan el repositorio remoto hasta que no se realice un **push**.

#### Branch

Como dijimos antes, a través de git podemos actualizar un repositorio mediante **pushs**. Lo que aún no sabemos es cómo trabajar en equipo de manera eficiente, con el objetivo de no "pisar" nuestro trabajo con el que están realizando nuestrxs compañerxs. Para solucionar éste problema git nos provee de ramas (branches).  
Para entender el concepto de branch debemos entender que a través de Git podemos realizar múltiples copias de nuestro repositorio, trabajar sobre una de ellas y luego unirla con el repositorio original.
El repositorio original no es más que una **branch**, creada por defecto con el nombre de **master**. Esta estrategia nos permite trabajar de forma independiente, en una tarea en particular (crear cierta funcionalidad, realizar un fix de un bug, por ejemplo).

Cuando trabajamos en git siempre estamos *parados* sobre una branch. Cuando recién creamos un repositorio nuestra branch será la llamada **master**. Cuando creamos una **branch** obtenemos una copia del repositorio, y pasamos a estar *parados* sobre la **branch** nueva.  
Dentro de una **branch** trabajaremos de la misma manera que en la original (master). Podemos realizar modificaciones, operaciones de **commit** y **push**.  

Como ya dijimos, la branch **master** debería representar nuestro repositorio en un estado funcional y presentable (es nuestro código fuente, lo que sabemos que funciona, o al menos eso se espera de una branch master). Entre **branches** podemos realizar lo que llamamos **merge**, *juntar* el contenido de una rama con otra. Git se enterará de las diferencias que existen entre los archivos subidos, y las actualizaciones realizadas.  
En la práctica, cada usuario del repositorio trabaja en una **branch** propia. Generalmente siempre se parte de la branch **master**, se crea una nueva rama con un nombre descriptivo (por ejemplo, descripción de la actualización, funcionalidad o fix que se vaya a trabajar), se realizan modificaciones, se realiza el o los **commit** correspondientes y finalmente se realiza el **push** al repositorio **remoto**.
Mediante interfaces de usuario en la web es posible mezclar cómodamente las actualizaciones de una branch en otra (no necesariamente la rama **master**), aunque también es posible realizar ésta operacion desde una terminal.


---

### Proveedores de respositorios

Las dos opciones mas populares son [**GitLab**][gitlab-url] y [**Github**][github-url].

[gitlab-url]:https://about.gitlab.com/
[github-url]:https://github.com/

Para seguir realizando pruebas es recomendable crearse una cuenta en alguna de las alternativas presentadas.

### Instalación en Linux

Algunas distribuciones Linux ya cuentan con git. De lo contrario, abrimos una terminal e ingresamos:
```bash
  sudo apt-get install git
```
[**Aquí**][git-install-url] también encontraran las instrucciones oficiales.

[git-install-url]:https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

### Configuración

En una terminal ingresamos el nombre e e-mail que utilizamos al registrarnos en una de las alternativas.

```bash
  git config --global user.name <nombreDeUsuarix>
  git config --global user.email <emailDeUsuarix>
```

Podemos corroborar los cambios ingresando:

```bash
  git config --global user.name
  git config --global user.email
```


### Operaciones sobre la terminal

La interfaz de git es muy amplia. No existe una sola manera de realizar cambios en un repositorio de git. Sin embargo hay operaciones básicos que siempre serán utilizadas o, al menos, son un buen empujón para empezar a darse maña con git.

#### Creación de repositorio

Existen maneras de crear un repositorio localmente y subirlo a los gestores online. Aquí mostraremos una manera simple de gestionarlo:

Primero, unx persona del grupo debe crear un repositorio en una de las alternativas web dadas y copiar el enlace. Es una Url que termina en .git

El siguiente paso deben realizarlo todxs los integrantes del grupo, traer el repositorio a cada computadora, es decir, clonar el repositorio localmente. Elegimos la carpeta donde queremos guardar todos nustros futuros repositorios e ingresamos:

*éste comando creará una carpeta con el nombre del repositorio y dentro estará el contenido*
```bash
  git clone <urlDelRepositorioRemoto>
```
Como ya dijimos, el repositorio es un historial de **commits**. Cada commit representa los archivos (contenido) modificados. Al clonar un repositorio, git trae todos los commit que existan en el repositorio remoto hacia una carpeta en nuestra computadora.

Encontraremos entre los archivos una carpeta ***.git*** donde git mantiene un estado de referencia de nuestros cambios, branches, entre otros.


#### Consultar branch y estado actual del repositorio local

Cada vez que realizamos modificaciones sobre los archivos, git las reconoce. Lo que hace es comprar todos los **commit** existentes con los archivos que vamos modificando. Podemos consultar el contenido que sufrió cambios utilizando el siguiente comando:

```bash
  git status
```
En el caso que no haya cambios, git señalará:
```bash
  On branch master
  nothing to commit, working directory clean
```

De lo contrario:

```bash
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   <nombre de archivo modificado>

no changes added to commit (use "git add" and/or "git commit -a")
```

También podemos obtener un listado con todas las ramas y aquella en la que estamos parados actualmente:

```bash
  git branch
```
Output:
```bash
  * master
```

#### Obtener cambios

Supongamos que otrx compañerx de grupo realizó cambios sobre el repositorio. Es muy importante contar con un directorio limpio antes de traernos los cambios. Con ***git status*** podremos saber si el directorio está apto para realizar un **pull**.

*supongamos que nombreDeBranch = master*
```bash
  git pull origin <nombreDeBranch>
```
Lo que hicimos fue traernos el contenido de todos los **commit** que existen en la **branch** master.
A modo informativo les comento que **origin** hace referencia a la url del repositorio remoto. No vamos a cambiar ese parámetro por ahora.

#### Realizar cambios en la historia del repositorio local

Una vez que hemos modificado algún archivo, podemos verificar los cambios escribiendo ***git status***. Conociendo el nombre del archivo podremos escribir en una terminal:

```bash
  git add <ruta hacia el archivo>
```

Agregar todos los archivos modificados

```bash
  git add .
```

El programa ***git add*** selecciona los archivos que queremos subir al repositorio remoto. Si volvemos a escribir ***git status*** podemos visualizarlos.

Realizar un commit de manera local no presenta ningún riesgo al repositorio remoto. Sin embargo, debemos ser prudentes con los archivos que nos comprometemos a modificar. No está de más decir que commit significa "compromiso".
Con éste sermón me refiero a que inicialmente no es deseable realizar cambios sobre los mismos archivos, o las misma líneas de un archivo que un compañero esté modificando. Ésto generaría conflictos en el repositorio. Existen maneras muy simples de solucionar ésto, de hecho es una práctica muy frecuente, pero a ésta altura no querríamos entrometernos con ésta problemática.
Luego de haber agregados los archivos con ***git add*** procedemos a realizar un **commit**:

```bash
  git commit -m "<Un mensaje que describa los cambios que realizamos>"
```
El commit se realizará sobre la **branch** local en la que estamos parados actualmente.

Si ingresamos el siguiente comando podremos ver el último commit que hemos hecho en la **branch** local.

```bash
  git show
```
Obtendremos los detalles del último commit.

```bash
  commit 7cb50a28b65449baf2c720bb4ba60f12a375f72c
  Author: Santiago <sgobotta@gmail.com>
  Date:   Thu May 10 13:22:31 2018 -0300

      El mensaje que escribimos en el commit
```

También podemos obtener una lista con todos los commit:

```bash
  git log
```

#### Subir los cambios al repositorio remoto

Repetimos: los cambios que subimos al repositorio están representados por **commits**. Solamente al haber realizado un commit nos encontramos capaces de subir los cambios. Si queremos ver un historial de commits podemos escribir ***git log***, pero no es necesario para poder subirlos al repositorio remoto.
En una terminal escribimos:

*supongamos que nombreDeBranch = master*
```bash
  git push origin <nombreDeBranch>
```
Debemos ingresar mail y password que git utilizará para validar el acceso al repositorio remoto.

Una vez realizado con éxito podremos ver nuestros **commit** en el historial de la web que hayamos elegido para gestionar nuestro repositorio.

#### Mezclar cambios (merge)

***¿Qué sucede si yo estuve realizando commits mientras mi compañerx publica cambios?***

Supongamos que estamos parados en la rama **master**. Unx compañerx realizó un **push** y nosotrxs tenemos **commits** en el repositorio local, que aún no hemos *pusheado* al repositorio remoto.

Si nos disponemos a hacer **push** vamos a obtener un mensaje parecido a este:
```bash
  To https://github.com/miUsuario/nombreDelRepo.git
  ! [rejected]        master -> master (fetch first)
  error: failed to push some refs to 'https://github.com/miUsuario/nombreDelRepo.git'
  hint: Updates were rejected because the remote contains work that you do
  hint: not have locally. This is usually caused by another repository pushing
  hint: to the same ref. You may want to first integrate the remote changes
  hint: (e.g., 'git pull ...') before pushing again.
  hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

Aprender a leer los logs es importante para entender **cómo** encarar la resolución de un problema. Vayamos paso por paso:

Primero nos dice que falló en ejecutar el programa **push** a la url de nuestro repositorio.

Luego recibimos un posible caso de lo que podría estar sucediendo. *Las actualizaciones fueron rechazadas porque el repositorio remoto contiene trabajo que nosotrxs no tenemos localmente*.

¡Está clarísimo! Git no nos va a permitir hacer **push** si no tenemos el repositorio local sincronizado con el remoto. En nuestro caso, no tenemos los cambios que realizó nuestrx compañerx hace instantes.

Nosotrxs ya sabemos como actualizarlo pero, ¿qué sucede cuando hacemos **git pull origin master** luego de haber realizado **commits** mientras estábamos parados en master tambien?

Dado que ahora sabemos que existen **commits** locales sin *commitear*, en la rama master, y que en el respotorio remoto hay otros **commits** que nosotros no tenemos localmente, deberíamos actualizar el repositorio para mezclar nuestrxs commits con los que están en el repositorio remoto.

A partir de aquí podemos encontrarnos en dos situaciones muy distintas, comparando el contenido de los commits locales y remotos:

1. el contenido de nuestros **commit** locales no tiene nada que ver con el contenido de los commits remotos que aún debemos actualizar.
2. el contenido de los **commit** locales modificó parte del contenido que ha sido publicado en los **commit** del repositorio remoto



1 . Si nos encontramos en el primer paso significa que nosotros hicimos **commit** de archivos distintos a los que están en los commit pendientes de **pull**, o bien podríamos haber modificado un mismo archivo que está pendiente de **pull**, pero no las líneas exactas que nuestrx compañerx publicó.
En ése caso procedemos a hacer **pull**. Se producirá un **merge** automáticamente, se mezclarán las actualizaciones de los **commit** que nos traemos remotamente con los **commit** locales.

```bash
  git pull origin master
```
Un merge no es más que un commit, con un mensaje, y un contenido. Con la diferencia que en vez de que nosotrxs tengamos que hacer **git add <nombreArchivo>**, git define el contenido, y los archivos que afectan al commit, automáticamente. Git nos pedirá que escribamos un mensaje de **merge** y aceptemos.

*En los usuarios Linux se va a desplegar el programa **nano** en la terminal, escriben el mensaje y al finalizar utilizan el atajo Ctrl+X para guardar y cerrar)*

El output es parecido a esto:

```bash
  remote: Counting objects: 3, done.
  remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
  Unpacking objects: 100% (3/3), done.
  From https://github.com/miUsuario/nombreDelRepo
  * branch            master     -> FETCH_HEAD
  * [new branch]      master     -> origin/master
  Merge made by the 'recursive' strategy.
  bubble-sort.hs | 1 +
  1 file changed, 1 insertion(+)
  create mode 100644 bubble-sort.hs

```

Recordemos que el comando ***git show*** nos muestra el último commit. Si lo ejecutamos podremos ver que se produjo un **commit** automáticamente, con el contenido que represente el **merge**.

```bash
  commit b916de28b5deccce17da5aa729e531b80b5bde0c
  Author: Santiago <sgobotta@gmail.com>
  Date:   Thu May 10 16:43:52 2018 -0300

      Se agregó el algoritmo para el árbol.
```

Ahora sí podremos publicar los cambios con **git push**.

```bash
  Counting objects: 5, done.
  Delta compression using up to 4 threads.
  Compressing objects: 100% (4/4), done.
  Writing objects: 100% (5/5), 510 bytes | 0 bytes/s, done.
  Total 5 (delta 0), reused 0 (delta 0)
  To https://github.com/miUsuario/nombreDelRepo.git
    5174708..7cb50a2  master -> master
```

2 . El otro caso tiene en cuenta la situación en la que alguien publicó un contenido y nosotrxs hemos estado editando el mismo contenido en el repositorio local.

Cuando querramos publicar los **commit** y luego pushear, sucederá lo mismo que en el caso anterior: debemos traernos los cambios. La diferencia es que como se han realizado modificaciones en las mismas líneas (ésto es el contenido) de un mismo archivo, el **merge** automático fallará.

Luego de realizar **git pull origin master** obtendremos algo de éste estilo:

```bash
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/miUsuario/nombreDelRepo
 * branch            master     -> FETCH_HEAD
   7cb50a2..035a371  master     -> origin/master
Auto-merging nombreDelArchivoComitteado
CONFLICT (content): Merge conflict in nombreDelArchivoComitteado
Automatic merge failed; fix conflicts and then commit the result.
```
A ésta altura git no sabe qué debe ser integrado en el repositorio luego del pull, ya que los dos archivos poseen distinto contenido en la misma línea, es por eso que falló el **merge** automático. La mezcla de contenido se realizó de forma parcial: en lugar de reemplazar contenido y perder información (o implementaciones, si hablamos de código) nos ofrece la chance de elegir qué ha de ser *commiteado* en el **merge**.

Decimos que el merge fue parcial porque ciertos segmentos del contenido están en conflicto. Si observamos el archivo nos daremos cuenta que git conservó el contenido que queremos publicar nosotros y el que ya estaba publicado cuando decidimos hacer **git pull**.

Aquel contenido en conflicto que pertenece al **commit** que realizamos nosotrxs localmente está encerrado entre símbolos **<** con el tag **HEAD**, mientras que el contenido en conflicto traído del repositorio remoto está encerrado entre símbolos **>** con el hash del **commit** al que pertenece (el hash es un identificador del commit en el que ése contenido fue añadido).

```bash
  <<<<<<< HEAD
  class Employee extends User //contenido que agregamos nosotrxs
  =======
  class Employee //contenido que nos trajimos del repositorio remoto
  >>>>>>> 035a3718cf101867cc0a0617b50d23f68dd77f11
```

Lo que debemos hacer es eliminar todos los símbolos (<, >, =), los tags, y editar el resto del contenido. Si queremos podemos agregar más contenido, o borrarlo, lo que estamos queriendo hacer no es mas que un commit como cualquier otro, solo que git no nos dejará hacer **push** de eśte archivo mientras se encuentre en conflicto (es decir, mientras tenga los símbolos y tags).

Cuando hemos finalizado la edición, procedemos a añadirlo al workspace:

```bash
  git add nombreDelArchivo
```

Escribimos el commit, idealmente con un comentario que haga referencia a la resolución de tal conflicto.

```bash
  git commit -m "Conflicts solved in nombreDeArchivo.js"
```

Ahora sí podemos publicar los cambios en el repo remoto.

```bash
  git push origin master
```

#### Trabajando en diferentes ramas (branching)

Olvidémonos de todo lo que aprendimos :)
Salvo casos particulares (no entraremos en detalles ahora), idealmente **NUNCA NADIE** realiza un **push** a la rama **master**. Recordemos que aquella rama es la que contiene el código fuente importante, la última versión estable por decirlo de una manera muy burda. Para poder trabajar de manera ordenada elegimos separar nuestro trabajo en distintas ramas. El proceso es más simple de lo que creemos. En un principio lo que queremos lograr es:
+ Crear una nueva rama a partir de la rama master
+ Realizar modificaciones sobre ésta copia (rama) que se desprendió de la rama master.
+ Realizar commits locales sobre ésta nueva rama
+ Realizar un push de los commit al repositorio remoto
+ Mezclar los cambios con la rama principal (master)

Para crear una branch nos conviene tener un repositorio actualizado y limpio de la rama principal, para ello realizamos un **pull**. Debemos estar *parados* sobre la rama **master** y ejecutar:

```bash
  git pull origin master
```

Luego procedemos a crear una nueva rama que será guardada de manera **local**. Para ello debemos elegir un nombre. Si, por ejemplo, vamos a trabajar en el modelo de un usuario podríamos utilizar: user-model-creation.
Es una convención en git separar las palabras de una branch con un guión del medio.

```bash
  git checkout -b <nombre de la nueva rama>
```
Nos aparecerá el siguiente mensaje:
```bash
  Switched to a new branch <nombre de la nueva rama>
```

A partir de ahora podemos trabajar como describimos anteriormente. Modificamos un archivo, lo agregamos utilizando ***git add***, y realizamos un commit local con ***git commit -m "descripción de la tarea realizada"***. Tengamos en cuenta que para realizar un commit **no** es necesario haber realizado la tarea en su **totalidad**.
Los **commit** deben ser descriptivos y simples, pero solamente la práctica contínua nos ayuda a definir qué es simple y qué no. Por lo tanto no resultaría ridículo realizar un **commit** de una Clase que aún no *haga nada*. El siguiente **commit** podría estar contenido por modificaciones a esa clase que representen un nuevo método, getters y setters y su respectivo test.

*(No está mal realizar varios commit de un mismo archivo modificado varias veces, de eśta manera es fácil observar el desarrollo y crecimiento del código fuente. Por el contrario, resulta tedioso observar un commit compuesto de mas de 50, 100 o más líneas).*

En pocas palabras, cuando sabemos que hemos escrito una porción de código que funciona y que es indispensable para el software que estamos desarrollando, por más mínima que sea, es conveniente realizar un commit.

Ahora ya tenemos nuestros commit realizados en la rama local que elegimos, queremos subirlos al repositorio remoto. Lo haremos de la misma manera que lo hicimos antes, pero apuntando a la nueva rama en el comando a git.

*Si elegimos para la nueva branch el nombre 'user-model-creation', escribimos:*
```bash
  git push origin user-model-creation
```

Deberíamos recibir un output parecido a esto:

```bash
  Counting objects: 3, done.
  Delta compression using up to 4 threads.
  Compressing objects: 100% (2/2), done.
  Writing objects: 100% (3/3), 268 bytes | 0 bytes/s, done.
  Total 3 (delta 1), reused 1 (delta 0)
  remote: Resolving deltas: 100% (1/1), completed with 1 local object.
  To https://<url del repositorio remoto>.git
   * [new branch]      user-model-creation -> user-model-creation

```
Lo que nos dice es que la branch local ***user-model-creation*** ahora fue copiada al repositorio remoto con el nombre ***user-model-creation***

*Nota: es posible hacer push de ramas donde aún no se han realizado commits. La rama existirá también en el repositorio remoto, aunque estará vacía. El procedimiento es 'git checkout -b < nombreBranch >' y luego 'git push origin <nombreBranch>'*

El siguiente paso debería ser mezclar los commit realizados en la nueva rama con la rama principal (master).
Como ya dije, en git existen varias maneras de hacer lo mismo. Podríamos hacerlo desde la terminal, pero por una cuestión de simplicidad y practicidad vamos a utilizar un método que se utiliza muchísimo y es bastante sencillo.

Si vamos a la web del repositorio, vemos que podemos elegir ver los cambios de una **branch** en particular. Si elegimos la branch que acabamos de *pushear* podremos ver los nuevos **commit** que realizamos.

Si elegimos **Github**, debemos presionar el botón **New pull request** que está a la derecha del nombre de la branch. Veremos que aparecen dos selectores con distintas ramas unidas por una flecha al estilo **<-**

La interfaz nos indica que queremos juntar los cambios de la branch de la derecha (seleccionamos user-model-creation) con los de la izquierda (master).
Debajo podremos ver la comparación entre el contenido de las ramas. Si hicimos todo como fue indicado, deberíamos poder leer un mensaje en color verde diciendo: ***Able to merge***. Escribimos un mensaje resumiendo los cambios que todos esos commit contienen y apretamos el botón **Pull Request**.

Lo que acabamos de hacer es hacer un pedido de **merge** del contenido que *pusheamos* con el contenido que ya existía en la rama **master**.
Es una costumbre realizar éste tipo de pedidos para que alguien que administre el repositorio pueda validar los cambios subidos antes de mezclarlos con la rama principal (master). En éste caso, ustedes mismos administraran su repositorio y podrían tomarse el atrevimiento de aprobar los pedidos.

La interfaz nos redirigirá a otra pantalla donde podemos encontrar el mensaje: ***This branch has no conflicts with the base branch***. También deberíamos encontrar un botón con el mensaje **Merge pull request**. Al confirmar la operación, todos los commit que forman parte de la rama que creamos (user-model-creation) ahora también se agregaron a la historia de la rama principal (master).

Tenemos que tener en cuenta que éstos cambios están ahora reflejados en la rama principal del repositorio remoto, pero no en la rama principal de nuestro repositorio local, únicamente existen en la rama user-model-creation tanto local como remota. Para actualizar nuestra rama principal debemos cambiar de rama en nuestro directorio de trabajo local.

Para cambiar de ramas utilizaremos un comando parecido al de creación:

```bash
  git checkout master
```

Ahora estamos *parados* en la rama principal. Para obtener los cambios realizamos un pull tal como lo hicimos antes:

```bash
  git pull origin master
```

Es importante tener el repositorio actualizado en la rama principal, por eso es indispensable comunicar a los demás usuarios del repositorio que hemos realizado cambios. No todos estan todo el tiempo atentos  a los nuevos cambios que surgen en el repositorio, aunque deberían!

Repasando, la próxima vez que necesitemos trabajar en una nueva funcionalidad lo conveniente es crear una nueva rama, las cuales deberían desprenderse de una rama principal, en nuestro ejemplo, la rama **master**. Por eso debemos estar actualizados localmente a los últimos cambios en el repositorio remoto.


### Estructura de los Repositorios II

#### gitignore

En un directorio local que contiene un repositorio git podemos alojar archivos para sincronizarlos con el repositorio remoto. Existen casos en los que no es deseable compartir todos los archivos que existen en aquel directorio local. Por ejemplo, a veces alojamos archivos de configuración que usamos para correr nuestros programas de manera local, o archivos que contienen información sensible, como claves de APIs u otro tipo de datos de autenticación. Para poder administrar archivos y que git no los tenga en cuenta, podemos crear un archivo llamado **.gitignore**.
Este tipo de archivo reconoce patrones en los nombres de los archivos. Si algun archivo dentro de nuestro directorio contiene un nombre parecido, no lo tendrá en cuenta al realizar **git status** y mucho menos podremos hacer **git add** sobre el.
Cada patron, que representa el nombre de un archivo, se escribe línea por línea. También podemos escribir el nombre completo del archivo. Por ejemplo:

*.gitignore*
```
  nombre-de-archivo
  todos-los-archivos-de-este-directorio/*
  el-arhivo-readme-de-este-directorio/README.md
  *.json #Todos los archivos .json del repositorio
  #un comentario
```

Los archivos comentados no serán tenidos en cuenta.
También podemos usar operadores lógicos dentro de .gitignore, por ejemplo:

*.gitignore*
```
  !config.json
```
El archivo config.json **no** será ignorado.

