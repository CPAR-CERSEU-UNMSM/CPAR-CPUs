
1. Problema matemático relacionado a los fractales o a patrones geométricos que se repiten cuando se hace zoom en la figura.
2. El ejercicio es simple, que pasa si nosotros elevamos un número al cuadrado, y ese número al cuadrado. Si el número es mayor a 1 en algún momento explota o tendemos al infinito. Si el número es menor a 1, el resultado se hace más chiquito y tiene a cero. Podríamos decir que el primer caso es una repetición no estable porque explota en algun momento. En cambio al segunda es estable porque tiende a un solo número y este número cero es conocido.

<img src="./Figures_teaching/mandelbrot1.png" alt="drawing" width="800"/>

3. Mandelbrot quería mapear qué áreas son estables y cuales inestables para ver si hay algún patrón, si es simétrico o algo y lo que encontró es lo siguiente. Áreas en el sector negro son áreas estables y las áreas de colores son no estables.

<img src="./Figures_teaching/mandelbrot.png" alt="drawing" width="800"/>

4. - Intel (Copyright Intel Corporation) tiene ya programado Mandelbrot en C y podemos usarlo para determinar el speedup de una aplicación más compleja que corre en serial y en paralelo.

### Calcular el speedup de la aplicación Mandelbrot

1. Clonar el repositorio de Intel:

```
git clone https://github.com/oneapi-src/oneAPI-samples.git
```

2. Ir a la locación del código MandelBrot:

```
cd ~/oneAPI-samples/DirectProgramming/C++SYCL/CombinationalLogic/mandelbrot
```

El archivo fuente de Mandelbrot se encuentra en la carpeta `src` y se denomina `mandel.hpp`. El archivo `main.cpp` es también importante y contiene las instrucciones para correr mandelbrot de forma serial o paralela y contabilizar los tiempos.

3. Crear un archivo denominado `build.sh` usando la función `nano` y ejecutarlo usando el comando `sh build.sh`. 

```
mkdir build
cd build
cmake ..
make
```

4. Antes de ejecutar, tenemos que asegurarnos que `cmake` esté instalado. Probar primero en la consola el comando `cmake ..`. En caso no esté instalado, obtendremos un error como se muestra en la figura. De ser así, instalarlo con el comando `sudo apt install cmake`

<img src="./Figures_teaching/Pasted image 20240325114034.png.png" alt="drawing" width="800"/>

5. Luego vamos a crear otro archivo denominado `run.sh` usando la función `nano` y lo ejecutamos con el comando `sh run.sh`

```
cd build
make run
```

6. Visualizar los resultados
7. Calcular el Speedup
