# Ejercicio 1. Mi primer repositorio en github

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

6. Volver a revisar el estado de tu repostorio. Qué observamos? Ha cambiado algo con respecto al estado anterior? Describa sus observaciones
5. Añadir el archivo al área de preparación suponiendo que ya queremos guardar esos cambios en el archivo de texto *text1.txt*. Para eso, usa el comando `git add text1.txt` (añade solo el archivo *text1.txt*) o `git add .` (añade todos los archivos creados). Ambos comandos para este caso deberían hacer lo mismo. **¿Puede explicar por qué?**
6. Luego de usar el comando `git add`, volver a revisar el estado del repositorio con `git status`. Algo ha cambiado, **¿puede explicar qué ha cambiado?** **Dentro del flujo de trabajo de git, dónde se encuentra el archivo text1.txt**. (Tipp: Opciones son, working tree, área de preparación o repositorio local)
7. Empezar a escribir la historia de tu repositorio tomando una foto instantánea de este cambio. Para eso usar el comando `git commit -m "MENSAJE"`. Recuerda que mientras más explicito sea el MENSAJE, mejor será la historia deL repostorio. Una vez hecho esto, verificaR el status del repositorio  con `git status`. **Algo ha cambiado? Describa sus observaciones. ¿Están todos los componentes de git al día?**
8. Los cambios elaborados solo se han hecho de manera local, para poder guardarlos en la nube o en un repositorio remoto, debemos crear una cuenta en [git hub](https://github.com/) o [git lab](https://gitlab.com/users/sign_in) o [bitbucket](https://bitbucket.org/).
9. Una vez creada la cuenta, crear un repositorio remoto con el nombre *proyecto1*. Elige un repositorio en blanco (abajo un ejemplo de como luce en GitHub). Para GitLab, elige el repositorio en blanco y algo similar a la figura de abajo se mostrará:

<img src="./Figures_teaching/Pasted image 20240310001819.png" alt="drawing" width="400"/>

11. Colocar el nombre, una descripción, elige hacerlo público y sin README y crear el repositorio.
12. Una vez creado, conectarlo al repositorio local siguiendo los pasos indicados en la misma web. Primero, configurar el repositorio local para conectarse al repositorio remoto:

<img src="./Figures_teaching/Pasted image 20240310001929.png" alt="drawing" width="400"/>

13. Seguir lo pasos para connectar ambos repositorios

<img src="./Figures_teaching/Pasted image 20240310001937.png" alt="drawing" width="400"/>

14. Finalmente, utilizar `git push`  para sincronizar los cambios en ambos repositorios y revisar el status con `git status`. **Qué diferencias hay ahora?**
