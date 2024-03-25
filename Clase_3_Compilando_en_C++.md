# test

## Ejemplo 1: Hello World in C

En este ejemplo, vamos a recordar como correr un job simple "Hello World" para refrescar nuestros conocimientos en Jupyter notebook.

1. En nuestra terminal, vamos a escribir el comando para crear un nuevo archivo `nano hello_A.cpp`. Este archivo será nuestro archivo fuente que contiene las instrucciones que deseamos compilar. En este caso y a diferencia de los ejercicios anteriores, vamos a colocar la extensión típica de C que es `.cpp`
2. Al inicio del archivo añadimos `#include <stdio.h>` para indicar al compilador que inserte el contenido de la librería estandar `stdio` en el archivo fuente que estamos creando.
3. Finalmente escribimos el cuerpo del programa _hello world_ dentro de la funcion `int main()`. Esta función debe retornar un valor entero (`int` o _integer_) al final de la ejecución de la función `main`. Por ello, como buena práctica terminamos el código con `return 0;`. La función `printf` viene del término en inglés imprimir con formato (_"print formatted"_) e imprime un conjunto de caracteres (o _string_) en C++. Para mayor información, visitar el siguiente [enlace](https://cplusplus.com/reference/cstdio/printf/).

```
#include <stdio.h>

int main()
{
    printf("Hello World");

    return 0;
}
```

4. Una vez creado el archivo fuente vamos a compilarlo. Para ello, usaremos el compilador `g++`. Para ello, primero, verificar si el compilador está instalado y qué versión está instalada con el comando `g++ --version`:

<img src="./Figures_teaching/Pasted image 20240325001000.png" alt="drawing" width="700"/>

5. Para compilar, usamos el comando `g++ -o hello hello_A.cpp`. Esta sintaxis usada tiene el siguiente formato, primero el compilador `g++`, el flag `-o` indica que luego de este sigue el nombre del ejecutable o archivo binario y su ubicación, en caso no se encuentre en nuestra misma carpeta de trabajo. En nuestro caso, el nombre del ejecutable es `hello`. Finalmente, se coloca el nombre y ubicación del archivo fuente que en nuestro caso es `hello_A.cpp`. Al ejecutar, veremos que aparece en nuestra carpeta de trabajo un archivo nuevo llamado `hello`:

<img src="./Figures_teaching/Pasted image 20240325001600.png" alt="drawing" width="700"/>

6. Para ejecutar nuestro archivo binario, usamos el comando `/.hello`

## Ejemplo 2: Calcular el Speedup

## Conceptos previos

- **Speedup**: Medida del rendimiento relativo entre dos arquitecturas o estrategias de paralelización para ejecutar un mismo problema

$$
Speedup = \frac{T_{base}}{T_{optimizado}}
$$
- **SIMD (Single Instruction Multiple Data) o Vectorización**: Ejecución de una misma instrucción sobre distintos datos en varias unidades de procesamiento.

### A. Calcular el tiempo de ejecución base ($T_{base}$)

1.  El siguiente archivo fuente `vector.cpp` presenta una suma y multiplicación de dos vectores (`v1` y `v2`) producidos de forma aleatoria y definidos como punto flotante en las líneas 11-21.
2. El tamaño de los vectores (`vsize`) es 1000 y vamos a repetir la multiplicación 200 veces (`repetitions`).
3. Guardamos el resultado de la suma y la multiplicación en los vectores `v3` y `v4` que son primero producidos en las líneas 25-27.
4. La suma y multiplicación de los vectores `v1` y `v2` se ejecuta en las líneas 33-35.
5. En las líneas 37-38 visualizamos el valor de los vectores `v3` y `v4` mediante el comando `std::cout`.

```
#include <cstdio>
#include <vector>
#include <stdlib.h>
#include <iostream>

int main(){

        int repetitions = 200;
        int vsize = 1000;

        std::vector<float> v1(vsize);
        std::vector<float> v2(vsize);

        std::cout << "Entrada: \n";

        for (size_t i = 0; i < vsize; i++) {
                v1[i] = static_cast<float>((rand() % vsize)) / vsize;
                v2[i] = static_cast<float>((rand() % vsize)) / vsize;
                std::cout << "v1[" << i << "] = " << v1[i] << "\n";
                std::cout << "v2[" << i << "] = " << v2[i] << "\n";
        }

//      #pragma omp parallel for
//      #pragma omp parallel      
        for(size_t j = 0; j < repetitions; j++){
                std::vector<float> v3(vsize);
                std::vector<float> v4(vsize);

                std::cout << "Repeticion #" << j << "\n";

                // Add and multiply random vectors
//              #pragma omp simd
                for(size_t i = 0; i < vsize; i++){
                      v3[i] = v1[i] + v2[i];
                      v4[i] = v1[i] * v2[i];
                      std::cout << "v3[" << i << "] = " << v3[i] << "\n";
                      std::cout << "v4[" << i << "] = " << v4[i] << "\n";
                }
        }

        return 0;
}
```

6. Compilamos el archivo `vector.cpp` bajo el nombre `vector_sequencial`, usando el comando `g++ -o vector_sequencial vector.cpp`
7. Lo que requerimos para este ejercicio no es el resultado de vector_sequencial sino el tiempo que requiere para ejecutar. Para obtener este valor, usamos el comando `time ./vector_sequencial` y guardamos el tiempo de usuario: *User time = 0.211s*

<img src="./Figures_teaching/Pasted image 20240325003059.png" alt="drawing" width="700"/>

### B. Calcular el tiempo optimizado 1 ($T^1_{optimizado}$)

1. El siguiente ejercicio presenta el mismo código que `vector.cpp` con la diferencia que estamos activando el la opción `#pragma omp parallel for` (paralelización por _threads_ o hilos) en la línea 23. El nuevo archivo fuente es llamado ahora `vector_1.cpp`
2. El objetivo es ver el incremento del rendimiento debido a una paralelización por threads para este ejemplo simple.
3. Para ello, tenemos que ejecutar los mismos pasos anteriores.

```
#include <cstdio>
#include <vector>
#include <stdlib.h>
#include <iostream>

int main(){

        int repetitions = 200;
        int vsize = 1000;

        std::vector<float> v1(vsize);
        std::vector<float> v2(vsize);

        std::cout << "Entrada: \n";

        for (size_t i = 0; i < vsize; i++) {
                v1[i] = static_cast<float>((rand() % vsize)) / vsize;
                v2[i] = static_cast<float>((rand() % vsize)) / vsize;
                std::cout << "v1[" << i << "] = " << v1[i] << "\n";
                std::cout << "v2[" << i << "] = " << v2[i] << "\n";
        }

        #pragma omp parallel for
//      #pragma omp parallel      
        for(size_t j = 0; j < repetitions; j++){
                std::vector<float> v3(vsize);
                std::vector<float> v4(vsize);

                std::cout << "Repeticion #" << j << "\n";

                // Add and multiply random vectors
//              #pragma omp simd
                for(size_t i = 0; i < vsize; i++){
                      v3[i] = v1[i] + v2[i];
                      v4[i] = v1[i] * v2[i];
                      std::cout << "v3[" << i << "] = " << v3[i] << "\n";
                      std::cout << "v4[" << i << "] = " << v4[i] << "\n";
                }
        }

        return 0;
}
```

4. Compilamos el archivo `vector_1.cpp` bajo el nombre `vector_paralelo`, usando el comando `g++ -o vector_paralelo vector_1.cpp`
5. Lo que requerimos para este ejercicio no es el resultado de vector_sequencial sino el tiempo que requiere para ejecutar. Para obtener este valor, usamos el comando `time ./vector_paralelo` y guardamos el tiempo de usuario: *User time = 0.185s*

<img src="./Figures_teaching/Pasted image 20240325004014.png" alt="drawing" width="700"/>

### C. Calcular el tiempo optimizado 2 ($T^2_{optimizado}$)

1. El siguiente ejercicio presenta el mismo código que `vector.cpp` con la diferencia que estamos activando el la opción `#pragma omp simd` (paralelización por instrucciones SIMD) en la línea 32. El nuevo archivo fuente es llamado ahora `vector_2.cpp`
2. El objetivo es ver el incremento del rendimiento debido a una paralelización por instrucciones SIMD.
3. Para ello, tenemos que ejecutar los mismos pasos anteriores. 

```
#include <cstdio>
#include <vector>
#include <stdlib.h>
#include <iostream>

int main(){

        int repetitions = 200;
        int vsize = 1000;

        std::vector<float> v1(vsize);
        std::vector<float> v2(vsize);

        std::cout << "Entrada: \n";

        for (size_t i = 0; i < vsize; i++) {
                v1[i] = static_cast<float>((rand() % vsize)) / vsize;
                v2[i] = static_cast<float>((rand() % vsize)) / vsize;
                std::cout << "v1[" << i << "] = " << v1[i] << "\n";
                std::cout << "v2[" << i << "] = " << v2[i] << "\n";
        }

//      #pragma omp parallel for
//      #pragma omp parallel      
        for(size_t j = 0; j < repetitions; j++){
                std::vector<float> v3(vsize);
                std::vector<float> v4(vsize);

                std::cout << "Repeticion #" << j << "\n";

                // Add and multiply random vectors
                #pragma omp simd
                for(size_t i = 0; i < vsize; i++){
                      v3[i] = v1[i] + v2[i];
                      v4[i] = v1[i] * v2[i];
                      std::cout << "v3[" << i << "] = " << v3[i] << "\n";
                      std::cout << "v4[" << i << "] = " << v4[i] << "\n";
                }
        }

        return 0;
}
```

4. Compilamos el archivo `vector_2.cpp` bajo el nombre `vector_paralelo`, usando el comando `g++ -o vector_simd vector_2.cpp`
5. Lo que requerimos para este ejercicio no es el resultado de vector_sequencial sino el tiempo que requiere para ejecutar. Para obtener este valor, usamos el comando `time ./vector_simd y guardamos el tiempo de usuario: *User time = 0.185s*

<img src="./Figures_teaching/Pasted image 20240325005305.png" alt="drawing" width="700"/>

### D. Calcular el Speedup1 y Speedup2

$Speedup = \frac{T_{base}}{T^1_{optimizado}}$ = $\frac{0.211}{0.185}$ = 1.14

$Speedup = \frac{T_{base}}{T^2_{optimizado}}$ = $\frac{0.211}{0.115}$ = 1.83

- Ambas alternativas ofrecen una mejora en la performancia de nuestro programa. Sin embargo, el ejercicio es muy pequeño para poder tener resultados más concluyentes.
- En cursos posteriores nosotros veremos otras herramientas de Intel como _VTune_ y _Advisor_ que nos pueden ayudar a optimizar nuestros programas de manera mucho más eficiente.
