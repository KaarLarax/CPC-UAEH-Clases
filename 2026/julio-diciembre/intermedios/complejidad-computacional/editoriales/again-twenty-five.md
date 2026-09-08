# A. Again Twenty Five!

**Autor:** Codeforces

**Link:** https://codeforces.com/problemset/problem/630/A

## Descripción

El gerente de recursos humanos estaba decepcionado nuevamente. El último solicitante falló la entrevista de la misma manera que los 24 anteriores. "¿Acaso doy una tarea tan difícil?" — pensó el gerente. "Simplemente elevar el número 5 a la potencia de $n$ y obtener los últimos dos dígitos del número. Sí, por supuesto, $n$ puede ser bastante grande, y uno no puede encontrar la potencia usando una calculadora, pero necesitamos personas que sean capaces de pensar, no solo seguir instrucciones."

¿Podrías pasar la entrevista en la empresa de visión artificial en IT City?

## Entrada

La única línea de la entrada contiene un solo entero $n$ ($2 \leq n \leq 2 \cdot 10^{18}$) — la potencia a la cual debes elevar el número 5.

## Salida

Imprime los últimos dos dígitos de $5^n$ sin espacios entre ellos.

## Ejemplos

### Ejemplo de entrada

```text
2
```

### Ejemplo de salida

```text
25
```

## Temas identificados

### Programación

- Observación matemática.
- Patrones en potencias.
- Complejidad constante $O(1)$.

### Matemáticas

- Propiedades de las potencias.
- Aritmética modular (implícita).

## Propuesta de solución

**Autor de la propuesta:** KaarLarax

El problema pide los últimos dos dígitos de $5^n$ para $n \geq 2$. La clave está en observar el patrón de los últimos dos dígitos de las potencias de 5:

- $5^1 = 5$ (un solo dígito)
- $5^2 = 25$
- $5^3 = 125$ (últimos dos dígitos: 25)
- $5^4 = 625$ (últimos dos dígitos: 25)
- $5^5 = 3125$ (últimos dos dígitos: 25)

Para cualquier $n \geq 2$, los últimos dos dígitos de $5^n$ son siempre **25**.

Esto se debe a que $5^n$ para $n \geq 2$ siempre es múltiplo de 25, y específicamente termina en 25 porque $5^n = 5^2 \cdot 5^{n-2} = 25 \cdot 5^{n-2}$, y multiplicar 25 por cualquier potencia de 5 mantiene los últimos dos dígitos como 25.

Por lo tanto, la solución es simplemente imprimir 25, sin importar el valor de $n$.

## Observaciones

- El valor de $n$ puede ser extremadamente grande (hasta $2 \cdot 10^{18}$), pero esto no afecta la respuesta.
- No es necesario calcular $5^n$ ni usar aritmética de grandes números.
- La respuesta es siempre la misma para cualquier $n \geq 2$.
- Este es un problema de observación, no de cálculo.

## Restricciones

$n$ puede ser hasta $2 \cdot 10^{18}$, pero como la respuesta es siempre 25, no hay necesidad de realizar ningún cálculo. La complejidad es $O(1)$ independientemente del tamaño de $n$.

## Estados o estructura de la solución

No se necesitan estructuras de datos ni estados. Solo se lee $n$ y se imprime 25.

## Casos base

- $n = 2$: $5^2 = 25$, la respuesta es 25.
- $n = 3$: $5^3 = 125$, los últimos dos dígitos son 25.
- $n = 10^{18}$: la respuesta sigue siendo 25.

## Transiciones o algoritmo

1. Leer $n$.
2. Imprimir 25.

```mermaid
flowchart LR
    A[Leer n] --> B[Imprimir 25]
    B --> C[Terminar]
```

## Correctitud

Para cualquier $n \geq 2$, se cumple que $5^n$ termina en 25. Esto se puede demostrar por inducción:

- Caso base: $5^2 = 25$, termina en 25.
- Paso inductivo: Si $5^k$ termina en 25, entonces $5^{k+1} = 5^k \cdot 5$. Si $5^k$ termina en 25, entonces $5^k = 100m + 25$ para algún entero $m$. Así, $5^{k+1} = (100m + 25) \cdot 5 = 500m + 125 = 100(5m + 1) + 25$, que también termina en 25.

Por lo tanto, el algoritmo que siempre imprime 25 es correcto para todo $n \geq 2$.

## Complejidad computacional

- Tiempo: $O(1)$.
- Memoria: $O(1)$.

## Implementación

### C++

**Autor de la implementación:** KaarLarax

```cpp
#include <bits/stdc++.h>

using namespace std;

#define edl '\n'

int32_t main() {
    ios_base::sync_with_stdio(false), cin.tie(nullptr);
    int n;
    cin >> n;
    cout << 25 << edl;
    return 0;
}
```

## Casos límite

- $n = 2$: el valor mínimo, la respuesta es 25.
- $n = 2 \cdot 10^{18}$: el valor máximo, la respuesta sigue siendo 25.
