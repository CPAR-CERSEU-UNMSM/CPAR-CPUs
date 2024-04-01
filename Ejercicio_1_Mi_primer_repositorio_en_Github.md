# Ejercicio 1. Mi primer repositorio en GitHub

En este ejercicio aprenderemos los pasos básicos del sistema de control de versiones GIT.

1. Verificar si se tiene instalado GIT. Para ello, ir a la línea de comando (**Ctrl + Alt + T**) en su sistema operativo y escribir: `git --version`

<img src="./Figures_teaching/Pasted image 20240311001742.png" alt="drawing" width="400"/>

2. En caso no esté instalado, usar el comando `sudo apt install git`
3. Una vez que se tiene GIT instalado, crear una carpeta dónde se desee almacenar el projecto con la función `mkdir proyecto1`
4. Con el comando `cd proyecto_1` ir a la carpeta proyecto 1
5. En la línea de comando `git status` (muestra el status del repositorio). **¿Qué observamos y por qué pasa eso?**
6. En la misma línea de comando, escribir el comando `git init` (crea nuestro repositorio). El repositorio local que toma el nombre de tu carpeta *proyecto1*. Al hacer estamos creando automáticamente elementos importantes de un sistema GIT. **¿Podrías nombrar qué elementos estamos creando?**
7. Revisar el estado del nuevo repositorio GIT usando el comando `git status`. **¿Qué observamos?** **¿Está el repositorio al día?**
8. Luego, usando la función `touch test1` vamos a crear el documento test1
9. Abrir el documento test1 con la función `nano test1` y colocar `Mi nombre es XXXXX`. Guardar el contenido con la combinación **Ctrl + o**

<img src="./Figures_teaching/Pasted image 20240311112052.png" alt="drawing" width="400"/>

6. Volver a revisar el estado de tu repostorio. **¿Qué observamos? ¿Ha cambiado algo con respecto al estado anterior?** Describa sus observaciones
5. Añadir el archivo al área de preparación suponiendo que ya queremos guardar esos cambios en el archivo de texto *text1.txt*. Para eso, usa el comando `git add text1.txt` (añade solo el archivo *text1.txt*) o `git add .` (añade todos los archivos creados). Ambos comandos para este caso deberían hacer lo mismo. **¿Puede explicar por qué?**
6. Luego de usar el comando `git add`, volver a revisar el estado del repositorio con `git status`. Algo ha cambiado, **¿puede explicar qué ha cambiado?** **Dentro del flujo de trabajo de git, ¿dónde se encuentra el archivo text1.txt?**. (Tip: las opciones son: working tree, área de preparación o repositorio local)
7. Empezar a escribir la historia de tu repositorio tomando una foto instantánea de este cambio. Para eso usar el comando `git commit -m "MENSAJE"`. Recuerda que mientras más explicito sea el MENSAJE, mejor será la historia del repostorio. Una vez hecho esto, verificar el status del repositorio  con `git status`. **¿Algo ha cambiado? Describa sus observaciones. ¿Están todos los componentes de git al día?**
8. Los cambios elaborados sólo se han hecho de manera local, para poder guardarlos en la nube o en un repositorio remoto, debemos crear una cuenta en [GitHub](https://github.com) o [GitLab](https://gitlab.com/users/sign_in) o [Bitbucket](https://bitbucket.org).
9. Antes de sincronizar nuestro repositorio local con el global, debemos crear un *personal token* en GitHub para que éste reconozca que somos nosotros los dueños de ambos repositorios
10. Para crear el **token**, debemos ir a la configuración de nuestra propia cuenta en GitHub

<img src="./Figures_teaching/Pasted image 20240317000532.png" alt="drawing" width="400"/>

11. Luego, en la opción *Developer settings*, buscar dentro de *Personal access tokens* la opción *Tokens (classic)*

<img src="./Figures_teaching/Pasted image 20240317000840.png" alt="drawing" width="400"/>

12. Una vez encontrada la opción, general un nuevo token y copiar el código que aparece pues este aparecerá solo una vez. Usen el token cuando sea necesario

<img src="./Figures_teaching/Pasted image 20240317001135.png" alt="drawing" width="400"/>

13. Una vez creada la cuenta, crear un repositorio remoto con el nombre *proyecto1*. Elige un repositorio en blanco (abajo un ejemplo de como luce en GitHub)

<img src="./Figures_teaching/Pasted image 20240310001819.png" alt="drawing" width="400"/>

14. Colocar el nombre, una descripción, elige hacerlo público y sin README y crear el repositorio.
15. Una vez creado, conectarlo al repositorio local siguiendo los pasos indicados en la misma web. Primero, configurar el repositorio local para conectarse al repositorio remoto:

<img src="./Figures_teaching/Pasted image 20240310001929.png" alt="drawing" width="700"/>

16. Seguir lo pasos para connectar ambos repositorios

<img src="./Figures_teaching/Pasted image 20240310001937.png" alt="drawing" width="700"/>

17. Finalmente, utilizar `git push`  para sincronizar los cambios en ambos repositorios y revisar el status con `git status`. **¿Qué diferencias hay ahora?**

### Cómo pegar y copiar de Windows to Ubuntu

Para poder realizar `git push` con el protocolo `https`, necesitamos nuestras credenciales, nombre de usuario, y token recién creados. En el caso de que nuestras credenciales se encuentren en nuestra máquina host o sistema operativo Windows, debemos encontrar una forma de copiar y pegar texto de Windows a Ubuntu y viceversa. Si probamos **Ctrl + C**  o **Ctrl + V** vamos a ver que no funciona. Por ello tenemos que seguir algunos pasos adicionales.

1. Primero iremos a la configuración de la máquina virtual, *General*, *Advanced* y revisar si las opciones de *Shared Clipboard* y *Drag and Drop* están marcadas cómo **Bidireccionales**

<img src="./Figures_teaching/Pasted image 20240324225127.png" alt="drawing" width="700"/>

2. Luego, en la opción *Storage* debemos instalar nuestro **Virtual Box Guest Additions ISO**. Éste se encuentra dentro de *Program Files/Oracle/VirtualBox*. 

<img src="./Figures_teaching/Pasted image 20240324225722.png" alt="drawing" width="700"/>

3. Luego, al abrir Ubuntu, encontraremos una nueva carpeta denominada **VBox_GAs** 

<img src="./Figures_teaching/Pasted image 20240324230342.png" alt="drawing" width="700"/>

4. Abrir esta carpeta y abrir la terminal dentro de esta carpeta. En esta carpeta, ejecutar el siguiente comando `sudo ./VBoxLinuxAdditions.run`. 
5. Finalmente, luego de reiniciar la máquina virtual, las opciones de copiar y pegar quedarán habilitadas.

### Paso alternativo en caso "git push" con https no funcione - SSH

Existen dos formas para sincronizar un repositorio remoto con un repositorio local. Hasta ahora, hemos utilizado el protocolo `https`. Alternativamente se puede utilizar el protocolo `ssh` (Secure Shell). `ssh` es un protocolo encriptado que ofrece una transferencia de información más eficiente y segura entre repositorios. El protocolo por defecto de GitHub es `http`, pero nosotros podemos forzar usar un protocolo `ssh` del siguiente modo:

1. Primero vamos a verificar si en nuestro sistema hay una llave ssh instalada de forma local. Para ello, en el terminal ejecutar el comando `cd ~/.ssh` y luego con `ls -la` verificar el contenido de la carpeta ssh:

<img src="./Figures_teaching/Pasted image 20240324232929.png" alt="drawing" width="700"/>

2. Dado que estamos buscando dos archivos del tipo `id_rsa` y `id_rsa.pub`. Dado que no lo tenemos instalado, debemos instalarlo ejecutando el comando `ssh-keygen -t rsa -b 4096 -C "lucianagoku@hotmail.com"` y hacer enter + enter + enter sin la necesidad de configurar o escribir nada cuando haya preguntas o acciones para realizar: 

<img src="./Figures_teaching/Pasted image 20240324233445.png" alt="drawing" width="700"/>

3. Luego de ejecutar el paso dos, y al revisar el contenido de la carpeta ssh, veremos los archivos deseaos que se han creado (`id_rsa` y `id_rsa.pub`). El archivo de extensión `.pub` es un archivo de domino público que puede ser compartida.

<img src="./Figures_teaching/Pasted image 20240324233640.png" alt="drawing" width="700"/>

4. El archivo de extensión `.pub` es un archivo de domino público que puede ser compartida. Con el comando `cat id_rsa.pub`, abrimos el archivo y copiamos su contenido para ser guardado en nuestro perfil de github. 

<img src="./Figures_teaching/Pasted image 20240324234024.png" alt="drawing" width="700"/>

5. En nuestro perfil de github, debemos dirigirnos a la configuración del perfil. 

<img src="./Figures_teaching/Pasted image 20240324231342.png" alt="drawing" width="700"/>

6. Dentro de las opciones de la configuración, ir a la opción denominada *SSH and GPG keys*. En esta opción hacer click en *New SSH key*

<img src="./Figures_teaching/Pasted image 20240324234422.png" alt="drawing" width="700"/>

7. Finalmente, se añade un nombre y se pega la clave pública:

<img src="./Figures_teaching/Pasted image 20240324234609.png" alt="drawing" width="700"/>
