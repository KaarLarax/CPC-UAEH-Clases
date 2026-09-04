# Introducción a la Complejidad Computacional: Big O, Tiempo y Memoria

**Autor: Carlos Alberto Lara Hernandez - Kaarlarax**

Cuando queremos resolver un problema de programación competitiva, siempre hay diferentes maneras de resolverlo, lo mejor sería seleccionar la manera más óptima; pero la pregunta más importante es: ¿qué herramienta o método utilizaremos para saber qué manera es la más óptima? La respuesta nos lleva aquí al tema de hoy.

La **Complejidad computacional** nos indica cuál es el esfuerzo computacional que utiliza nuestro algoritmo o manera de resolver un problema; dado que no basta solo que funcione el código, si no que **entre en el límite de tiempo y memoria permitidos**, nuestra gran amiga la complejidad computacional nos ayudará a entender todo mejor.

A continuación, aprenderemos qué es la notación Big O ($O$), cómo analizar tu código línea por línea y cómo evitar el temido **TLE (Time Limit Exceeded)**.

---

## 1. ¿Qué es una Operación $O(1)$?

En términos sencillos, una operación $O(1)$ (tiempo constante) es aquella que tarda exactamente la misma cantidad de tiempo en ejecutarse sin importar qué tan grande sea la entrada.

Analicemos un ejemplo línea por línea:

```cpp
int a = 5;          // O(1) - Asignar un valor toma un tiempo fijo.
int b = 10;         // O(1) - Otra asignación constante.
int suma = a + b;   // O(1) - La CPU suma dos números en un ciclo de reloj.
cout << suma;       // O(1) - Imprimir un número simple.

```

**Conclusión:** Todo el bloque de código se ejecuta en tiempo $O(1)$. No importa si sumamos `5 + 10` o `1000000 + 2000000`, la computadora tardará lo mismo.

---

## 2. Complejidad Temporal (Big O) y Casos Comunes

Para calcular la complejidad total de un programa, sumamos la complejidad de sus partes, pero **solo nos quedamos con el término dominante** (el "peor de los casos"). Si un algoritmo tiene una parte $O(n)$ y otra $O(n^2)$, la complejidad final es $O(n^2)$.

Veamos los escenarios principales:

### A. Ciclo Simple: $O(n)$

```cpp
int n = 1000;
for (int i = 0; i < n; i++) {
    cout << i << "\n"; // Esta línea O(1) se ejecuta 'n' veces.
}

```

El tiempo de ejecución crece linealmente. Si $n$ se duplica, el tiempo de ejecución se duplica. Su complejidad es **$O(n)$**.

### B. Ciclos Anidados: $O(n^2)$

```cpp
int n = 1000;
for (int i = 0; i < n; i++) {            // Se ejecuta 'n' veces
    for (int j = 0; j < n; j++) {        // Por cada 'i', se ejecuta 'n' veces
        cout << i << " " << j << "\n";   // O(1) ejecutado n * n veces
    }
}

```

Su complejidad es **$O(n^2)$** (tiempo cuadrático).

> **Nota importante:** ¿Es $O(n^2)$ una complejidad mala? **Depende del tamaño de tu entrada ($n$).** En programación competitiva, los jueces suelen procesar unas $10^8$ operaciones por segundo. Si $n = 1000$, entonces $n^2 = 1,000,000$ (esto pasará rapidísimo). Pero si $n = 10^5$, $n^2 = 10^{10}$ operaciones, lo que tomará muchos segundos y resultará en un **TLE**.

---

## 3. Optimizando un algoritmo: El truco de Gauss

Supongamos que el problema nos pide sumar todos los números del 1 al $N$.

### El enfoque Lineal (La trampa del TLE)

La primera idea suele ser usar un ciclo simple:

```cpp
long long suma = 0;
for(int i = 1; i <= n; i++) {
    suma += i;
}

```

Esto es **$O(n)$**. Pero, ¿qué pasa si el problema dice que $N = 10^{10}$? El ciclo iterará diez mil millones de veces, superando el límite de un segundo del juez. Nos dará **TLE**.

### La solución Matemática $O(1)$

En lugar de sumar uno por uno, busquemos un patrón (el método que descubrió Gauss en la primaria). Si sumamos del 1 al 100:

- $1 + 100 = 101$
- $2 + 99 = 101$
- $3 + 98 = 101$

Notamos que los extremos siempre suman $(n + 1)$, y como estamos emparejando números, tenemos exactamente $\frac{n}{2}$ pares. De aquí deducimos la fórmula mágica:

$$\text{Suma} = \frac{n \times (n + 1)}{2}$$

```cpp
long long suma = (n * (n + 1)) / 2; // Una sola operación matemática

```

**¡Felicidades!** Acabas de reducir un algoritmo que daba TLE con complejidad $O(n)$, a un algoritmo perfecto con complejidad **$O(1)$**.

---

## 4. Complejidad Espacial (Memoria)

Así como analizamos cuánto tiempo toma un algoritmo, debemos saber **cuánta memoria RAM consume**. Los ejemplos anteriores solo declaran variables simples (`int`, `long long`), por lo que su complejidad espacial es **$O(1)$**.

Sin embargo, cuando usamos **arreglos (Arrays) o Vectores**, la memoria crece. Para calcularlo en bytes, debes recordar los tamaños de los tipos de datos (un `int` estándar pesa 4 bytes).

**¿Cuánto pesa un arreglo en C++?**

```cpp
int arreglo[1000];

```

- Tenemos 1000 enteros.
- Cada entero pesa 4 bytes.
- Total: $1000 \times 4 = 4000 \text{ bytes}$.
- Esto es aproximadamente **$4 \text{ KB}$**.

Si declararas un arreglo gigante `int arreglo[100000000]`, pesaría unos $400 \text{ MB}$, lo cual podría causarte un **Memory Limit Exceeded (MLE)** si el juez solo permite $256 \text{ MB}$.

---

## Problemas de Práctica

Ahora que entiendes cómo analizar el tiempo de tu código y cómo una simple fórmula matemática puede salvarte de un TLE, es hora de programarlo.

**Resuelve el siguiente problema aplicando la suma de Gauss:**

- [CPCJudge - Problema: Gauss, el pequeño matemático del bosque](https://cpcjudge.com/problem/gausssuma)

### Problemas Recomendados

- []()

### Editorial de Problemas

- [Editorial de Problemas](editoriales/readme.md)

## Recursos Adicionales

En esta sección encontraras algunos recursos externos para poder entender más y mejorar tu comprensión acerca del tema.

Links y recursos:

- [omega up - Notación Asintótica](https://omegaup.com/course/introduccion_a_algoritmos/assignment/notacion_asintotica#problems/algoritmos-2-1)

- [Introduction to Big-O](https://www.youtube.com/watch?v=zUUkiEllHG0)
- [Complete Guide On Complexity Analysis – Data Structure and Algorithms Tutorial](https://www.geeksforgeeks.org/complete-guide-on-complexity-analysis/)