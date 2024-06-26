# Ejercicio 2: MandelBrot

1. Problema matemático relacionado a los fractales o a patrones geométricos que se repiten cuando se hace zoom en la figura.
2. El ejercicio es simple: ¿qué pasa si nosotros elevamos un número al cuadrado, y ese número al cuadrado? Si el número es mayor a 1 en algún momento explota o tendemos al infinito. Si el número es menor a 1, el resultado se hace más pequeño y tiene a cero. Podríamos decir que el primer caso es una repetición no estable porque explota en algun momento. La segunda, en cambio, es estable porque tiende a un solo número y este número cero es conocido.

<img src="./Figures_teaching/mandelbrot1.png" alt="drawing" width="800"/>

3. Mandelbrot quería mapear qué áreas son estables y cuales inestables para ver si existe algún patrón, y también si son simétricas o no. Mandelbrot encontró lo siguiente: **áreas en el sector negro son estables y las áreas de colores son no estables**.

<img src="./Figures_teaching/mandelbrot.png" alt="drawing" width="800"/>

4. Intel tiene ya programado Mandelbrot en C++ y podemos usarlo para determinar el speedup de una aplicación más compleja que se ejecuta en serial y en paralelo. Pero primero debemos instalar **oneAPI Base Toolkit** en nuestra máquina virtual. **oneAPI Base Toolkit** es complementamente libre e incluye una serie de herramientas y librerías específicas para la computación de alto rendimiento en muchos tipos de arquitecturas. Para ver más detalles, revisar: [Intel-oneAPI](https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit.html#gs.77fyh4). 

### Instalar oneAPI en la máquina virtual

1. Para instalar oneAPI en nuestro sistema, ingresamos primero a la siguiente página de descarga que ya tiene seleccionado el instalador según el sistema operativo (Linux) y el manager de software (_APT Package Manager_ de Ubuntu): [link de descarga](https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html?operatingsystem=linux&distributions=aptpackagemanager)

<img src="./Figures_teaching/Pasted image 20240330220639.png" alt="drawing" width="800"/>

2. Seguir paso a paso los comandos dados. 

<img src="./Figures_teaching/Pasted image 20240330223059.png" alt="drawing" width="800"/>

**Nota**: no hay necesidad de registrarse para poder usar **oneAPI Base Toolkit**. Sin embargo, **oneAPI Base Toolkit** requiere aproximadamente 13GB de espacio en el disco virtual, así que debemos asegurarnos que tenemos el espacio necesario. Adicionalmente, cada vez que se vaya a usar alguno de los paquetes de **oneAPI Base Toolkit**, debemos usar el comando siguiente para garantizar que estos paquetes estén activos:

```
source /opt/intel/oneapi/setvars.sh
```
### Calcular el speedup de la aplicación Mandelbrot

1. Una vez instalado **oneAPI Base Toolkit** y activado los paquetes (ver nota anterior), clonar el repositorio de Intel:

```
git clone https://github.com/oneapi-src/oneAPI-samples.git
```

2. Ir a la locación del código MandelBrot:

```
cd oneAPI-samples/DirectProgramming/C++/CombinationalLogic/MandelbrotOMP
```

El archivo fuente se encuentra en la carpeta `src` y se denomina `mandel.hpp`. El archivo `main.cpp` es también importante y contiene las instrucciones para ejecutar el programa de forma serial o paralela y contabilizar los tiempos.

3. Dado que en la carpeta _MandelbrotOMP_ ya tenemos creado el archivo *Makefile* solo tenemos que ejecutarlo con el comando `make`

<img src="./Figures_teaching/Pasted image 20240330235135.png" alt="drawing" width="800"/>

Preguntas:
- **¿Podría identificar qué compilador se está usando para este ejercicio?**
- **¿Qué archivos y/o carpetas se están creando al ejecutar el comando `make`?**

4. Como se podrán percatar con el comando `ls`, se ha creado una nueva carpeta *release* y dentro de esta carpeta se tiene un ejecutable llamado *Mandelbrot*. Para ejecutar este achivo, usamos el comando `./release/Mandelbrot`. Al ejecutar, observamos algunas opciones de ejecución de Mandelbrot:

<img src="./Figures_teaching/Pasted image 20240330235643.png" alt="drawing" width="800"/>

5. Elijan la opción 1 para obtener el tiempo de ejecución serial

<img src="./Figures_teaching/Pasted image 20240330235749.png" alt="drawing" width="800"/>

6. Volver a ejecutar esta vez probando las otras opciones y calcular el Speedup usando la ecuación de la clase anterior:

$$
Speedup = \frac{T_{base}}{T_{optimizado}}
$$

7. El resultado de los fractales se puede visualizar como archivo png en la carpeta *MandelbrotOMP*

<img src="./Figures_teaching/Pasted image 20240331000052.png" alt="drawing" width="800"/>
