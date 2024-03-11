# Clase 1. Introducción a comandos básicos de Linux con un virtual machine

El sistema operativo en el cual vamos a trabajar es Linux. En caso no se tenga Linux como sistema operativo, vamos a instalar una máquina virtual (**Virtual Machine de Ubuntu**). Primero debemos instalar un Oracle VM Virtual Box Manager. Para ello, ir a la siguiente web de [virtual box](https://www.virtualbox.org/wiki/Downloads) y descargar el instalador segun el sistema operativo que se tenga (Mac o Windows):

<img src="./Figures_teaching/Pasted image 20240310223840.png" alt="drawing" width="800"/>

Luego de descargar el instalador, ejecutarlo y usar las instrucciones por defecto. 

<img src="./Figures_teaching/Pasted image 20240310223959.png" alt="drawing" width="100"/>

Una vez instalada la aplicación, accedemos al **Virtualbox manager** dónde podemos organizar diferentes máquinas virtuales. 

<img src="./Figures_teaching/Pasted image 20240310224335.png" alt="drawing" width="800"/>

Por el momento no tenemos todavía Ubuntu (Linux) como sistema operativo y debemos instalarlo. Para ello tenemos que crear algo denominado *Imagen vdi* que tiene la configuración de nuestro sistema operativo Ubuntu. Nosotros podemos descargar cada elemento o dependencia por separado, pero también podemos instalar *Imágenes* ya predeterminadas y ajustarlas a nuestras necesidades. Esa será nuestra siguiente acción.  Para ello iremos a la siguiente web [osboxes](https://www.osboxes.org/ubuntu/#ubuntu-22-04-jammy-vbox) y descargamos la versión "Ubuntu 22.04 Jammy Jellyfish":

<img src="./Figures_teaching/Pasted image 20240310225509.png" alt="drawing" width="500"/>

En la opción *Info*, guardar el usuario y contraseña que nos servirá para acceder a nuestra *Imagen* una vez instalada y configurada. 

<img src="./Figures_teaching/Pasted image 20240310225558.png" alt="drawing" width="500"/>


Luego, regresamos al **Virtualbox manager** y hacemos clic en la opción new <img src="./Figures_teaching/Pasted image 20240310230541.png" alt="drawing" width="70"/>. Ahí, colocamos un nombre a nuestra *Imagen*, el tipo de sistema operativo y la versión así como se muestra en la figura:

<img src="./Figures_teaching/Pasted image 20240310230900.png" alt="drawing" width="600"/>

Luego, debemos configurar el hardware en base a nuestro hardware local. Para ello damos memoria RAM y número de procesadores necesarios en base a nuestros requerimientos. Para esta sesión, indicamos (alrededor de) 4 GB de memoria RAM y 4 procesadores (para poder realizar aplicaciones en paralelo). Debemos tomar en cuenta que la configuración de nuestra máquina virtual puede modificarse pero es más complejo hacerlo una vez creada. 

<img src="./Figures_teaching/Pasted image 20240310231314.png" alt="drawing" width="600"/>

Luego tenemos que definir el tamaño de nuestro disco duro virtual. El tamaño por defecto es de 25 GB y es un tamaño adecuado para nuestra sesión. Debemos tomar en cuenta que el valor que pongamos será consumido de nuestro disco duro local. 

<img src="./Figures_teaching/Pasted image 20240310232825.png" alt="drawing" width="600"/>

Luego, selecionamos la opción *usar un hard disk existente* y en la opción add <img src="./Figures_teaching/Pasted image 20240310233240.png" alt="drawing" width="50"/> y añadimos la *Imagen* descargada y hacemos clic en *choose*. Cómo se puede observar, el espacio virtual máximo posible es de 500 GB, pero el espacio real ocupado es solo 8 GB. Luego *next* y luego *finish*:

<img src="./Figures_teaching/Pasted image 20240310233341.png" alt="drawing" width="600"/>

La configuración final de nuestra *Imagen* (máquina virtual) es la siguiente:

<img src="./Figures_teaching/Pasted image 20240310233956.png" alt="drawing" width="800"/>

Para ingresar, hacemos doble clic <img src="./Figures_teaching/Pasted image 20240310234930.png" alt="drawing" width="150"/>, y colocamos la contraseña que guardamos antes. 

<img src="./Figures_teaching/Pasted image 20240310235610.png" alt="drawing" width="800"/>

Una vez dentro, tenemos una ventana muy similar a una ventana de Windows con las aplicaciones básicas instaladas como Mozilla Firefox, Libre Office, etc. Para poder interactuar con el sistema, usamos la combinación **Ctrl + Alt + T** para abrir la consola. 

<img src="./Figures_teaching/Pasted image 20240311000205.png" alt="drawing" width="800"/>

Para esta sesión, hay algunas aplicaciones que necesitamos, por ejemplo, el sistema de control de versiones GIT y el compilador **g++**. Si probamos directamente en la línea de comando, el resultado nos arrojará un error y esto debido a que estas aplicaciones no están instaladas.

<img src="./Figures_teaching/Pasted image 20240311000549.png" alt="drawing" width="800"/>

Para instalar estas aplicaciones, vamos a usar las función `sudo apt update` primero para poder actualizar la lista de repositorios de dónde Ubuntu instalará los programas o aplicaciones que requiramos. `sudo` significa **super user** y `apt` es el software manager para la instalación de software. Para poder instalar el compilador, usamos el comando `sudo apt install build-essential`. 

<img src="./Figures_teaching/Pasted image 20240311001617.png" alt="drawing" width="800"/>

Para instalar GIT, usamos el comando `sudo apt install git`

<img src="./Figures_teaching/Pasted image 20240311001742.png" alt="drawing" width="600"/>

Finalmente instalaremos **htop** (`sudo apt install htop`) que nos permite ver el estado del sistema. Es el equivalente al control manager de Windows para ver que procesos están corriendo, el uso de los procesadores y memoria RAM, etc. Para salir, damos a **Ctrl + C**

<img src="./Figures_teaching/Pasted image 20240311002131.png" alt="drawing" width="800"/>

### Comandos básicos en Linux

- `ls`: revisar el contenido de un directorio
- `pwd`: obtener la ruta de un directorio
- `nano [archivo]`: abrir un archivo y modificarlo
- `cd [directory-name]`: ir al directorio
- `cd ..`: ir al nivel superior (en el sistema de archivos)
- `cd -`: regresar al directorio anterior
- `mkdir [-option] [directory-name]`: crear una nueva carpeta
- `touch [-option] [file-name]`: crear un archivo nuevo
- `rmdir [-option] [directory-name]`: remover una carpeta
- `rm [-option] [file-name]`: remover un archivo
### Referencias

- https://linuxconfig.org/how-to-install-g-the-c-compiler-on-ubuntu-20-04-lts-focal-fossa-linux
- https://www.makeuseof.com/how-to-import-vdi-file-into-virtualbox/









