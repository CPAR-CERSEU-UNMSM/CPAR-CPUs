# Clase 2. Introducción al sistema de control de versiones GIT

## Control de versiones

Sistema que hace seguimiento a cada modificación o cambio en un código, algoritmo, servidor de IT, website, documento. Un ejemplo de control de versiones es **GIT** o **google docs**.

<img src="./Figures_teaching/Pasted image 20240309233350.png" alt="drawing" width="400"/>

## Esquema básico de un sistema GIT

Git consiste en uno o varios **repositorios locales** y **remotos**. Los **repositorios locales** son personales y los tenemos en nuestra computadora personal por ejemplo. El trabajo aquí puede ser offline pero debe estar sincronizado al repositorio remoto. El o los **repositorios remotos** contienen el estado del arte o la versión actualizada del repositorio y están guardados en la nube en plataformas como *GitLab*, *GitHub* o *Bitbucket*.

<img src="./Figures_teaching/Pasted image 20240309233852.png" alt="drawing" width="700"/>

## Locaciones de GIT

Para manejar GIT, hay algunos componentes importantes que debemos conocer y nos permitirán entender mejor cómo funciona GIT. 
- El primer elemento es el llamado **working tree**, es el ambiente donde nosotros trabajamos y tenemos los archivos que vamos a guardar mediante el comando _commit_. 
- Una vez que tenemos idea de lo que vamos a guardar, pasamos al **área de preparación** que incluye todos los archivos a ser incluidos en el _commit_. Por ejemplo, algunas veces modificamos dos archivos que están relacionados y los queremos guardar juntos, entonces pensaremos en un commit que incluya los dos archivos y no dos commits por separado. 
- Luego, todos los commits de un proyecto se almacenan en el **repositorio local** que está en nuestra computadora local y estos tres elementos forman parte del **área personal** del proyecto.
- Finalmente, el almacenamiento final del proyecto se realiza en la nube o algún **repositorio remoto** como **GitLab** o **GitHub** que se considera que contiene el proyecto completo y es nuestra fuente de consulta del proyecto en caso se necesite de una referencia. La idea es tener nuestros repositorios, local y global, sincronizados.

<img src="./Figures_teaching/Pasted image 20240309234800.png" alt="drawing" width="700"/>

## Comandos claves en git

1. `git init`: crea nuestro repositorio
2. `git status`: muestra el status del repositorio. Nos permite observar qué cambios se han realizado, qué nuevos archivos no están siendo parte del sistema de control, etc
3. `git add .`: añade todos los archivos que hayan tenido cambios durante nuestra sesión de trabajo al área de preparación
4. `git commit`: crea un foto instantánea de nuestro repositorio en un momento específico. Con un commit, nosotros guardamos la historia del repositorio. Lo ideal es hacer commits de lo que uno quiera guardar y de manera frecuente
5. `git push`: guardar lo creado/modificado en el repositorio local hacia el repositorio global. El repositorio global almacena nuestro trabajo en la nube y es como el repositorio de referencia. Los proveedores de repositorios globales son: GitLab, GitHub, Bitbucket, entre otros
6. `git pull`: actualizar el repositorio local con respecto al global
7. `git reset --hard`:  elimina todo los cambios que no hayan pasado por un commit. En el marco de este curso, vamos a usarlo en caso hagamos cambios en el repositorio remoto del curso y no tengamos derechos de autoría del mismo

## Referencias:

- [https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud](https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud)
- [https://git-scm.com/docs](https://git-scm.com/docs)










