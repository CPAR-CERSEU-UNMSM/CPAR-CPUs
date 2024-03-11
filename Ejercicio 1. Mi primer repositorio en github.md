# Ejercicio 1. Mi primer repositorio en github

En este ejercicio aprenderemos los pasos básicos del sistema de control de versiones GIT.

1. Verificar si se tiene instalado GIT. Para ello, ir a la línea de comando en su sistema operativo y escribir: `git --version`

<img src="./Figures_teaching/Pasted image 20240311001742.png" alt="drawing" width="400"/>

2. En caso no esté instalado, usar el comando `sudo apt install git`
3. Una vez que se tiene GIT instalado, crear una carpeta dónde se desee almacenar el projecto con la función `mkdir proyecto_1`.
4. Abrir `Open git bash here`o la línea de comando (dependiendo de tu sistema operativo) en tu carpeta *proyecto_1* y escribir el comando `git status` (muestra el status del repositorio). **Qué observamos y por qué pasa eso?**
5. En el mismo git bash, escribir el comando `git init` (crea nuestro repositorio). El repositorio local que toma el nombre de tu carpeta *proyecto_1*. Al hacer estamos creando automáticamente elementos importantes de un sistema GIT. **Podrías nombrar qué elementos estamos creando?**
6. Revisar el estado del nuevo repositorio GIT usando el comando `git status`. **Qué observamos?** **Está el repositorio al día?**
7. Agregar un archivo de texto llamado *text1.txt* y dentro del archivo escribir el nombre y apellido. Luego en git bash, volver a revisar el estado de tu repostorio. **Qué observamos? Ha cambiado algo con respecto al estado anterior?** **Describa sus observaciones.**
8. Añadir el archivo al área de preparación suponiendo que ya queremos guardar esos cambios en el archivo de texto *text1.txt*. Para eso, usa el comando `git add text1.txt` (añade solo el archivo *text1.txt*) o `git add .` (añade todos los archivos creados). Ambos comandos para este caso deberían hacer lo mismo. **Puede explicar por qué?**
9. Luego de usar el comando `git add`, volver a revisar el estado del repositorio con `git status`. Algo ha cambiado, **puede explicar qué ha cambiado?** **Dentro del flujo de trabajo de git, dónde se encuentra el archivo text1.txt**. (Tipp: Opciones son, working tree, área de preparación o repositorio local)
10. Empezar a escribir la historia de tu repositorio tomando una foto instantánea de este cambio. Para eso usar el comando `git commit -m "MENSAJE"`. Recuerda que mientras más explicito sea el MENSAJE, mejor será la historia deL repostorio. Una vez hecho esto, verificaR el status del repositorio  con `git status`. **Algo ha cambiado? Describa sus observaciones. Están todos los componentes de git al día?**.
11. Los cambios elaborados solo se han hecho de manera local, para poder guardarlos en la nube o en un repositorio remoto, debemos crear una cuenta en [git hub](https://github.com/) o [git lab](https://gitlab.com/users/sign_in) o [bitbucket](https://bitbucket.org/).
12. Una vez creada la cuenta, crear un repositorio remoto con el nombre *proyecto_1*. Elige un repositorio en blanco (abajo un ejemplo de como luce en github). Para gitlab, elige el repositorio en blanco y algo similar a la figura de abajo se mostrará:

<img src="./Figures_teaching/Pasted image 20240310001819.png" alt="drawing" width="800"/>

13. Colocar el nombre, una descripción, elige hacerlo público y sin README y crear el repositorio.
14. Una vez creado, conectarlo al repositorio local siguiendo los pasos indicados en la misma web. Primero, configurar el repositorio local para conectarse al repositorio remoto:
<img src="./Figures_teaching/Pasted image 20240310001929.png" alt="drawing" width="1200"/>

15. Seguir lo pasos para connectar ambos repositorios
<img src="./Figures_teaching/Pasted image 20240310001937.png" alt="drawing" width="1200"/>

16. Finalmente, utilizar `git push`  para sincronizar los cambios en ambos repositorios y revisar el status con `git status`. **Qué diferencias hay ahora?**
