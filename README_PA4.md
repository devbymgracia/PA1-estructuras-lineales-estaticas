# README — Evaluación

> **Curso:** Algoritmo y Estructura de Datos Basados en IA  
> **Código:** 4682  
> **Evaluación:** [ PA4 ]  
> **Equipo:** [Grupo 6]  

## 1. Integrantes

| Integrante | Rol | Aporte principal |
|---|---|---|
| Diana Romero Pariona | Integrante | Actividad 1 |
| Mauricio Del Carpio Torres | Integrante | Actividad 3 |
| Cristian Martin Correa Barriga | Integrante | Actividad 2 |
| Mariagracia Cadillo Jiménez | Integrante | Actividad 4 |


## 2. Descripción y objetivo

Actividad 1. Recursividad aplicada

1.1 ¿Qué es la recursividad?
La recursividad es una técnica de programación en la que una función o algoritmo se llama a sí mismo para resolver un problema. En cada llamada, el problema se reduce a una versión más pequeña o sencilla hasta llegar a una condición que permite detener las llamadas.

1.2 ¿Cómo se relaciona con el principio divide y vencerás?
La recursividad se relaciona con el principio de divide y vencerás, porque ambos permiten resolver problemas complejos dividiéndolos en partes más pequeñas y fáciles de solucionar.

Este principio tiene tres pasos:
Dividir: separar el problema principal en problemas más pequeños.
Resolver: solucionar cada problema mediante llamadas recursivas.
Combinar: reunir los resultados para obtener la solución final.

1.3 Diseño de un algoritmo recursivo aplicado al caso

Caso propuesto: Registro y procesamiento de notas de estudiantes.
Algoritmo SumarNotas(notas, cantidad)

    Si cantidad = 0 Entonces
        Retornar 0
    FinSi

    Retornar notas[cantidad - 1] +
             SumarNotas(notas, cantidad - 1)

FinAlgoritmo


Ejemplo de ejecución:
Supongamos que un estudiante tiene las siguientes calificaciones:
Nota 1: 15
Nota 2: 18
Nota 3: 16
Nota 4: 14

El algoritmo realiza las siguientes operaciones:

SumarNotas([15,18,16,14], 4)

= 14 + SumarNotas([15,18,16], 3)
= 14 + 16 + SumarNotas([15,18], 2)
= 14 + 16 + 18 + SumarNotas([15], 1)
= 14 + 16 + 18 + 15 + SumarNotas([], 0)
= 63

4. Identificación de los elementos de la recursividad
| Elemento | Explicación |
| Caso base | Cuando la cantidad de notas es igual a 0, el algoritmo devuelve 0.|
| Caso recursivo | Se suma la última nota y se vuelve a llamar a la función con una cantidad menor de notas.|
| Condición de finalización | Las llamadas terminan cuando la cantidad de notas llega a 0.| 

Actividad 2. Ordenamiento recursivo 

2.1 Algoritmo Merge Sort

Para el ordenar la información de las ubicaciones del campus utilizaremos el algoritmo Merge Sort

Este algoritmo utiliza el principio de divide y vencerás, es una frase usada por el propio Julio Cesar y el resto de conquistadores, lo que quiere decir es dividir una lista de elementos en partes más pequeñas, ordena cada parte y finalmente combina los resultados para obtener una lista ordenada.

```
Datos Iniciales:                                   Resultado Esperado:

-Laboratorios                                     -Administración
-Entrada                                          -Auditorio
-Auditorio                                        -Biblioteca
-Cafetería                                        -Cafeteria
-Biblioteca                                       -Entrada
-Administración                                   -Laboratorios
```
2.2 Funcionamiento paso a paso

Paso 1:

Primero dividimos la lista original en dos partes.

```
[Laboratorios, Entrada, Auditorio]

[Cafetería, Biblioteca, Administración]
```

Paso 2: División en elementos individuales

Vamos a seguir dividiendo las listas hasta que cada tenga un solo elemento.
```
[Laboratorios]        [Entrada]           [Auditorio]

[Cafetería]           [Biblioteca]        [Administración]
```

Paso 3: Comparación y Combinación

Comparamos elementos y las combinamos siguiendo el orden alfabético.
```
[Laboratorios] + [Entrada]

[Entrada, Laboratorios]
```

Paso 4: Resultado final

Después combinar todas las partes obtenemos:
```
-Administración
-Auditorio
-Biblioteca
-Cafetería
-Entrada
-Laboratorios
```
2.3 Algoritmo Merge Sort
```
public class MergeSortCampus {
    // Metodo principal de ordenamiento
    public static void mergeSort(String[] datos) {

        // Caso base
        if (datos.length <= 1) {
            return;
        }

        // Dividir la lista en dos partes
        int mitad = datos.length / 2;

        String[] izquierda =
                Arrays.copyOfRange(datos, 0, mitad);

        String[] derecha =
                Arrays.copyOfRange(datos, mitad, datos.length);

        // Llamadas recursivas
        mergeSort(izquierda);
        mergeSort(derecha);

        // Combinar las partes ordenadas
        mezclar(datos, izquierda, derecha);
    }
```

Función para combinar listas:

```
public static void mezclar(
            String[] datos,
            String[] izquierda,
            String[] derecha) {

        int i = 0;
        int j = 0;
        int k = 0;

        while (i < izquierda.length &&
                j < derecha.length) {

            if (izquierda[i].compareToIgnoreCase(
                    derecha[j]) <= 0) {

                datos[k] = izquierda[i];
                i++;

            } else {

                datos[k] = derecha[j];
                j++;
            }

            k++;
        }

        // Copiar elementos restantes de izquierda
        while (i < izquierda.length) {
            datos[k] = izquierda[i];
            i++;
            k++;
        }

        // Copiar elementos restantes de derecha
        while (j < derecha.length) {
            datos[k] = derecha[j];
            j++;
            k++;
        }
```

2.4 Script de MergeSortCampus

```
package com.lideratec;

import java.util.Arrays;

public class MergeSortCampus {
    // Metodo principal de ordenamiento
    public static void mergeSort(String[] datos) {

        // Caso base
        if (datos.length <= 1) {
            return;
        }

        // Dividir la lista en dos partes
        int mitad = datos.length / 2;

        String[] izquierda =
                Arrays.copyOfRange(datos, 0, mitad);

        String[] derecha =
                Arrays.copyOfRange(datos, mitad, datos.length);

        // Llamadas recursivas
        mergeSort(izquierda);
        mergeSort(derecha);

        // Combinar las partes ordenadas
        mezclar(datos, izquierda, derecha);
    }

    // Metodo para combinar las listas
    public static void mezclar(
            String[] datos,
            String[] izquierda,
            String[] derecha) {

        int i = 0;
        int j = 0;
        int k = 0;

        while (i < izquierda.length &&
                j < derecha.length) {

            if (izquierda[i].compareToIgnoreCase(
                    derecha[j]) <= 0) {

                datos[k] = izquierda[i];
                i++;

            } else {

                datos[k] = derecha[j];
                j++;
            }

            k++;
        }

        // Copiar elementos restantes de izquierda
        while (i < izquierda.length) {
            datos[k] = izquierda[i];
            i++;
            k++;
        }

        // Copiar elementos restantes de derecha
        while (j < derecha.length) {
            datos[k] = derecha[j];
            j++;
            k++;
        }
    }

    public static void main(String[] args) {

        String[] lugares = {
                "Laboratorios",
                "Entrada",
                "Auditorio",
                "Cafeteria",
                "Biblioteca",
                "Administracion"
        };

        System.out.println("Lugares originales:");

        for (String lugar : lugares) {
            System.out.println(lugar);
        }

        mergeSort(lugares);

        System.out.println("\nLugares ordenados:");

        for (String lugar : lugares) {
            System.out.println(lugar);
        }
    }
}
```
2.5 Resultado de ejecucion
Lista desordenada:

```
Laboratorios
Entrada
Auditorio
Cafeteria
Biblioteca
Administracion
```

Lista Ordenada:

```
Administracion
Auditorio
Biblioteca
Cafeteria
Entrada
Laboratorios
```

ACTIVIDAD 3. MODELADO DEL PROBLEMA MEDIANTE GRAFOS

3.1 Modelo del grafo

Representamos el campus como un grafo ponderado no dirigido. Los pesos son distancias de caminata en metros. Usamos aristas no dirigidas porque los caminos se pueden recorrer en ambos sentidos. Si hubiera un tramo de sentido obligatorio, se modelaría como arista dirigida.

Nodos: E (Entrada), AD (Admisión), B (Biblioteca), C (Cafetería), AU (Auditorio), P (Pabellón de aulas), L (Laboratorio de cómputo).

Aristas: E-AD (50), E-C (80), E-B (120), AD-B (70), C-AU (100), B-P (90), B-L (150), AU-P (60), P-L (70).

Usamos lista de adyacencia porque el grafo tiene pocas conexiones:

E: (AD,50), (C,80), (B,120)
AD: (E,50), (B,70)
B: (E,120), (AD,70), (P,90), (L,150)
C: (E,80), (AU,100)
AU: (C,100), (P,60)
P: (B,90), (AU,60), (L,70)
L: (B,150), (P,70)

Búsqueda: origen = E, destino = L, criterio = menor distancia total.

3.2 Uso de DFS y BFS

DFS (búsqueda en profundidad) conviene para explorar toda la estructura, por ejemplo para verificar que todas las ubicaciones sean alcanzables desde la entrada o para listar rutas alternativas de evacuación. Avanza por una rama hasta el final y retrocede, usa pila o recursión y consume poca memoria. Su limitación es que la primera ruta que encuentra no es la más corta: podría hallar C-AU-P-L (310 m), peor que la óptima.

BFS (búsqueda en anchura) conviene para hallar la ruta con menos tramos, por ejemplo cuando un estudiante quiere pasar por la menor cantidad de edificios. Explora por niveles usando una cola y garantiza el menor número de aristas. Su limitación es que ignora los metros y consume más memoria.

3.3 Aporte de A*

DFS y BFS son búsquedas ciegas porque no saben dónde está la meta. A* es una búsqueda heurística que usa la fórmula f(n) = g(n) + h(n), donde g es el costo real recorrido desde el origen y h es una estimación de lo que falta hasta la meta (aquí, la distancia en línea recta al Laboratorio). A* siempre expande el nodo con menor f. Si h nunca sobrestima el costo real (heurística admisible), garantiza la ruta óptima explorando menos nodos.

Valores de h hacia L: E = 230, AD = 220, B = 120, C = 190, AU = 100, P = 60, L = 0.

Ejecución de E a L:
1. Se expande E. Resultan AD con f = 270, C con f = 270 y B con f = 240.
2. Se expande B (menor f). Resultan P con f = 270 y L con f = 270.
3. Hay empate en 270 y se elige L por tener menor h. L es la meta.

Resultado: la ruta óptima es E-B-L con 270 m (E-AD-B-L también mide 270 m). A* expandió solo 2 nodos y no exploró cafetería ni auditorio.

Relación con la IA: A* es un ejemplo de búsqueda heurística, porque usa conocimiento del problema para decidir hacia dónde buscar. Esto permite que el módulo de orientación responda rápido a consultas como "¿cómo llego al laboratorio?", igual que en mapas, videojuegos y robots.


### Actividad 4. Argumentación final

#### 4.1 Comparación de las alternativas

Comparamos DFS, BFS y A* sobre el mismo problema: llegar de la Entrada (E) al Laboratorio de cómputo (L) en el grafo del campus.

| Criterio | DFS | BFS | A* |
|---|---|---|---|
| **Cómo recorre el grafo** | Avanza por una rama hasta el final y retrocede (pila o recursión). | Explora por niveles (cola). | Expande el nodo con menor f(n) = g(n) + h(n). |
| **Ruta que obtiene de E a L** | Puede hallar C-AU-P-L (310 m), peor que la óptima. | E-B-L, la de menos tramos (2 aristas). | E-B-L con 270 m, la de menor distancia. |
| **¿Considera los metros?** | No. | No: solo cuenta tramos. | Sí: usa g(n) y una estimación h(n). |
| **Nodos explorados** | Puede recorrer ramas innecesarias. | Explora por niveles, incluso nodos alejados de la meta. | Solo 2 nodos (E y B): no exploró cafetería ni auditorio. |
| **Limitación** | La primera ruta que encuentra no es la más corta. | Ignora las distancias y usa más memoria. | Necesita una buena heurística (aquí, la distancia en línea recta). |
| **Cuándo conviene en el campus** | Verificar que todas las ubicaciones sean alcanzables o listar rutas de evacuación. | Pasar por la menor cantidad de edificios. | Guiar a un estudiante a un destino concreto por la ruta más corta. |

#### 4.2 Solución recomendada

Recomendamos implementar **A\*** como algoritmo principal del módulo de orientación, porque el sistema debe encontrar la ruta más conveniente entre un origen y un destino específico. En nuestro caso, A* obtuvo la ruta óptima de 270 m expandiendo solo 2 nodos, mientras que DFS pudo devolver una ruta de 310 m y BFS, aunque halló E-B-L, no tiene en cuenta las distancias y podría equivocarse en otro grafo.

Como apoyo, proponemos usar **BFS** cuando el estudiante quiera pasar por la menor cantidad de edificios, y **DFS** para verificar que todas las ubicaciones sean alcanzables o para explorar rutas alternativas. Para mostrar las ubicaciones ordenadas, usamos **Merge Sort**, un algoritmo recursivo de divide y vencerás con costo O(n log n), que ordena la lista de lugares del campus por nombre.

#### 4.3 Relación con aplicaciones básicas de IA

- **Búsqueda heurística:** A* usa conocimiento del problema (h(n)) para decidir hacia dónde buscar, en lugar de probar todas las opciones, igual que un agente inteligente que toma decisiones informadas.
- **Navegación y mapas:** el módulo de orientación modela el campus como un grafo y calcula la mejor ruta, igual que las aplicaciones de mapas.
- **Videojuegos y robots:** A* se usa para que personajes y robots encuentren su camino hacia una meta evitando recorridos innecesarios.
- **Asistentes virtuales:** un asistente del campus podría responder "¿cómo llego al laboratorio?" con una ruta calculada y justificada.

#### 4.4 Conclusión técnica

Cada algoritmo responde a una necesidad distinta: DFS explora, BFS busca el recorrido con menos tramos y A* llega a una meta específica de forma eficiente usando una heurística. Elegir el algoritmo según el contexto, y no uno solo para todo, es lo que hace que la solución sea eficiente y justificable. Por eso recomendamos A* como núcleo del módulo, apoyado en BFS y DFS para consultas puntuales, y en Merge Sort para organizar la información del campus.

## 4. Evidencias

Agregar aquí capturas, resultados, pruebas o enlaces que demuestren el funcionamiento.

- [Evidencia 1]
- [Evidencia 2]
- [Evidencia 3]

## 5. Matriz de participación

| Integrante | Desarrollo | Pruebas | Documentación | Exposición | Evidencia de participación |
|---|---|---|---|---|---|
| Diana Romero Pariona | Alta | Alta| Alta| Sí | Actividad 1 + video + informe +README |
| Mauricio Del Carpio | Alta | Alta | Alta | Sí | Actividad 3 + video + informe + README |
| Cristian Martin Correa Barriga | Alta | Alta | Alta | Sí | Actividad 2 + Video + Informe + README |
| Mariagracia Cadillo Jiménez | Alta | Alta | Alta | Sí | Actividad 4 + video + informe + READ ME |


## 6. Video de exposición

**Video público de YouTube:** [https://youtu.be/dATz26iOGr0?si=1K-DyHgRAem2MF75]

Todos los integrantes deben participar en la exposición con sus cámaras prendidas y explicar el procedimiento, la solución desarrollada y las decisiones tomadas.

## 7. Conclusiones

- [La recursividad permite recorrer las ubicaciones del campus de manera organizada, evitando repetir lugares mediante una estructura de control de visitados. Además, facilita la implementación de algoritmos que trabajan con estructuras como árboles y grafos.]
- [El algoritmo Merge Sort es una alternativa adecuada para organizar alfabéticamente las ubicaciones del campus. Su enfoque recursivo permite dividir el conjunto de datos en partes pequeñas y obtener finalmente una lista ordenada de manera eficiente.]
- [Los grafos permiten representar las ubicaciones y conexiones del campus. DFS facilita la exploración de las ubicaciones, BFS permite encontrar recorridos con menor cantidad de conexiones cuando estas tienen el mismo costo y A* permite buscar rutas considerando las distancias y una estimación hacia el destino.]
- .[En conclusión, la integración de estos algoritmos permite desarrollar una solución tecnológica que facilita la orientación dentro de una institución educativa y demuestra cómo las estructuras de datos y los algoritmos pueden aplicarse en problemas reales.]
---

**Última actualización:** [24/11/2026]
