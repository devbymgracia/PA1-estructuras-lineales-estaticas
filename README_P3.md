# README — Evaluación

> **Curso:** ALGORITMO Y ESTRUCTURA DE DATOS BASADOS EN INTELIGENCIA ARTIFICIAL  -  
> **Código:** 4682  
> **Evaluación:** [ PA3 ]  
> **Equipo:** [Grupo 6]  

## 1. Integrantes

| Integrante | Rol | Aporte principal |
|---|---|---|
| Mariagracia Cadillo | Participante | Actividad 4 + video |
| Mauricio Del Carpio | Participante | Actividad 1 + Video |
| Diana Romero | Participante | Actividad 3 + Conclusiones + video |
| [Cristian Correa] | [Participante] | [Actividad 2 + creacion del README + Informe + video] |


## 2. Descripción y objetivo

**Problema:**  
Determinar cómo utilizar las estructuras de datos pila (LIFO) y cola (FIFO) para organizar las acciones y solicitudes de los estudiantes en una unidad de servicios académicos, considerando el orden correcto de procesamiento.

**Objetivo:**  
Comprender y aplicar las estructuras de datos pila y cola mediante el diseño de algoritmos y representaciones gráficas, identificando sus características, operaciones principales y aplicaciones prácticas para resolver situaciones reales de manera eficiente.

**Solución desarrollada:**  
Se desarrollaron algoritmos para apilar, desapilar, encolar, desencolar, visualizar el tope o frente y verificar si las estructuras están vacías. Asimismo, se compararon ambas estructuras para identificar su aplicación adecuada: la pila para revertir acciones recientes y la cola para atender solicitudes académicas según su orden de llegada.

### Actividad 1. Pila LIFO 
Expliquen qué caracteriza a una estructura LIFO y desarrollen una representación gráfica de una pila para el caso propuesto. Diseñen algoritmos para apilar, desapilar, visualizar el elemento del tope y verificar si la pila está vacía. Indiquen una aplicación concreta del caso donde la pila sea la estructura más adecuada. 

### 1.1 ¿Qué es una pila LIFO?
Una pila es una estructura de datos que sigue el principio LIFO (“Last In, First Out”): el último elemento en entrar es el primero en salir. Todas las operaciones se hacen por un solo extremo, llamado tope. Para llegar a un elemento del fondo hay que retirar antes los que están encima.
Ejemplo: en una unidad de servicios académicos, el sistema guarda las acciones realizadas sobre el registro de un estudiante. Si hay que revertir cambios, se deshace primero la acción más reciente.

### 1.2 Representación gráfica de una pila
Para el caso se registran tres acciones del estudiante, en este orden:
1. Registro de matrícula
2. Subida de constancia de estudios
3. Actualización de datos

    BASE                                                 TOPE (TOP)
                                            
REGISTRO DE MATRICULA --> CONSTANCIA DE ESTUDIOS --> ACTUALIZACIÓN DE DATOS
                       
                        --> ORDEN DE ATENCIÓN -->

### 1.3 Algoritmo para apilar (push)
Se implementa con un arreglo. La variable tope indica la posición del último elemento (-1 si la pila está vacía).

```
// 1.3. Apilar una acción
    public void apilar(String accion) {
        if (tope == capacidad - 1) {
            System.out.println("La pila esta llena");
            return;
        }

        tope++;
        pila[tope] = accion;

        System.out.println("Solicitud apilada correctamente");
    }
```
### 1.4 Algoritmo para desapilar (pop)
El objetivo es retirar la acción que está en el tope.
```
// 1.4. Desapilar una acción
    public void desapilar() {
        if (tope == - 1) {
            System.out.println("La pila esta vacia");
            return;
        }

        String accion = pila[tope];
        pila[tope] = null;
        tope--;

        System.out.println("Accion revertida: " + accion);
    }
```

### 1.5 Algoritmo para visualizar el tope (peek)
Permite consultar cuál fue la última acción registrada sin retirarla

```
// 1.5. Visualizar el tope de la pila
    public void verTope() {
        if (tope == - 1) {
            System.out.println("La pila esta vacia");
        } else {

        System.out.println("Ultima accion: " + pila[tope]);
    }
}
```

### 1.6 Algoritmo para verificar si la pila está vacía (isEmpty) 

```
// 1.6. Verificar si la pila esta vacia
    public void pilaVacia() {
        if (tope == - 1) {
            System.out.println("La pila esta vacia");
        } else {

        System.out.println("La pila contiene acciones registradas");
    }
}
```
Atributos necesarios de la clase: 

```
private String[] pila;
private int tope = -1;
private int capacidad;

public Pila(int capacidad) {
      this.capacidad = capacidad;
      this.pila = new String[capacidad];
}
```

### 1.7 Aplicación concreta de la pila en el caso propuesto
La pila se utiliza para llevar el historial de acciones recientes del estudiante en el sistema académico y permitir deshacer cambios.
Las acciones se registran en este orden:
      1. Registro de matrícula
      2. Subida de constancia de estudios
      3. Actualización de datos
      
Si el estudiante comete un error y pide revertir, el sistema deshace primero la actualización de datos, luego la constancia y, por último, la matrícula.

Motivo: la pila es la estructura más adecuada porque su principio LIFO coincide con la forma en que se revierten los cambios: siempre se deshace primero lo último que se hizo. Con una cola habría que recorrer o reordenar los elementos para llegar a la acción más reciente, lo que añade lógica innecesaria. Con la pila, apilar y desapilar tienen costo O(1).


### Actividad 2. Cola FIFO

2.1 ¿Qué es una cola FIFO?

Es una estructura de datos que trabaja junto con el principio del Fifo “First in, First out” en otras palabras el primero en entrar es el primero en salir.

Un ejemplo es sobre una unidad de servicios académicos, una cola permite organizar las solicitudes pendientes y deben atenderlas respetando  el orden de llegada.

2.2 Representación gráfica de una cola

Para el ejemplo gráfico escogí tres estudiantes que presentan solicitudes de atención:

1. Solicitud de Ana
2. Solicitud de Franco
3. Solicitud de Carlos
Estas solicitudes se procesan en el mismo orden en que fueron recibidas


│   Ana Solicitud     │    Franco Solicitud    │   Carlos Solicitud    │

      → Orden de atención →
La solicitud de Ana será atendida primero, seguido por Franco y finalmente Carlos.

2.3. Algoritmos para encolar

Para este ejemplo utilizaremos una cola de implementar un arreglo circular. Las variables “Frente, Final y Cantidad” que permiten controlar elementos almacenados.

```
// 2.3. Encolar una solicitud
    public void encolar(String solicitud) {
        if (cantidad == capacidad) {
            System.out.println("La cola esta llena");
            return;
        }

        cola[finalCola] = solicitud;
        finalCola = (finalCola + 1) % capacidad;
        cantidad++;

        System.out.println("Solicitud agregada correctamente");
    }
```
2.4 Algoritmos para desencolar
El objetivo de desencolar es retirar la solicitud que está frente de la cola.

```
// 2.4. Desencolar una solicitud
    public void desencolar() {
        if (cantidad == 0) {
            System.out.println("La cola esta vacia");
            return;
        }

        String solicitud = cola[frente];
        cola[frente] = null;

        frente = (frente + 1) % capacidad;
        cantidad--;

        System.out.println("Solicitud atendida: " + solicitud);

        if (cantidad == 0) {
            frente = 0;
            finalCola = 0;
        }
    }
```

2.5 Algoritmo para visualizar el frente

Aquí consultamos cuál es la siguiente solicitud que debe atenderse sin retirarla.

```
// 2.5. Visualizar el frente de la cola
    public void verFrente() {
        if (cantidad == 0) {
            System.out.println("La cola esta vacia");
        } else {
            System.out.println("Siguiente solicitud: " + cola[frente]);
        }
    }
```
2.6 Algoritmo para verificar si la cola está vacía

```
// 2.6. Verificar si la cola esta vacia
    public void colaVacia() {
        if (cantidad == 0) {
            System.out.println("La cola esta vacia");
        } else {
            System.out.println("La cola contiene solicitudes pendientes");
        }
    }
```
2.7 Aplicación concreta de la cola en el caso propuesto

La cola se utiliza para administrar las solicitudes académicas que esperan a ser atendidas.

Las solicitudes llegan en este orden:

1. Solicitud de Matrícula.
2. Solicitud de constancia de estudios
3. Solicitud de actualización de datos

El sistema atenderá primero la solicitud de matrícula, luego la constancia y finalmente la actualización de datos.

Motivo:
La cola es preferible porque su principio FIFO permite atender las solicitudes según  su orden de llegada. esto facilita una gestión organizada de los trámites pendientes y evita alterar la secuencia de atención. 

    
### Actividad 3. Selección de estructura para situaciones reales

#### 3.1 Determinación del uso de pilas o colas

Las pilas y las colas son estructuras de datos que permiten organizar elementos según diferentes criterios de procedimiento. 

Pila (LIPO): El último elemento ingresado es el primero en salir.
Cola (FIFO): El primer elemento ingresado es el primero en salir.

#### 3.2 Analisis de cada situación

| Situación | Estructura | Justificación tecnica | 
|---|---|---|
| Registro de acciones recientes para revertir cambios | Pila | Se utiliza porque las acciones se deshacen en orden inverso al que fueron ejecutadas. La última acción realizada debe revertirse primero (LIFO). |
| Atención de solicitudes en orden de llegada | Cola | Se utiliza una cola porque las solicitudes deben atenderse respetando su orden de ingreso. La primera solicitud registrada será la primera en procesarse (FIFO).  | 
| Procesamiento donde el último ingresado debe atenderse primero | Pila | Se utiliza una pila porque el elemento más reciente debe procesarse antes que los anteriores. Esto corresponde al comportamiento LIFO.  | 
| Flujo de espera de trámites pendientes | Cola | Se utiliza una cola porque los trámites deben organizarse según su orden de llegada, garantizando una atención ordenada y evitando que los trámites más antiguos queden relegados. |

### Actividad 4. Comparación y argumentación

#### 4.1 Comparación entre pila y cola

| Criterio | Pila (Stack) | Cola (Queue) |
|---|---|---|
| **Principio de funcionamiento** | LIFO (Last In, First Out): el último en entrar es el primero en salir. | FIFO (First In, First Out): el primero en entrar es el primero en salir. |
| **Operaciones principales** | `push` (apilar), `pop` (desapilar), `peek` (ver el tope), `isEmpty`. | `enqueue` (encolar), `dequeue` (desencolar), `peek` (ver el frente), `isEmpty`. |
| **Forma de acceso** | Un solo extremo: el tope. Se inserta y se elimina por el mismo lado. | Dos extremos: se inserta por el final y se elimina por el frente. |
| **Analogía** | Una pila de platos: se toma el último que se colocó. | Una fila de personas: atienden primero al que llegó primero. |
| **Ventajas en contexto** | Ideal para revertir o deshacer acciones y para procesos anidados. | Ideal para atender solicitudes en orden de llegada, de forma justa. |
| **Ejemplos de aplicación** | Deshacer/rehacer en un editor, historial de navegación, llamadas a funciones (recursión). | Cola de impresión, atención de solicitudes, turnos de atención. |

|

**Representación gráfica**

```
PILA (LIFO)                COLA (FIFO)

  push ↓   ↑ pop           enqueue →  [A][B][C][D]  → dequeue
  ┌─────┐                              final      frente
  │  D  │ ← tope
  │  C  │
  │  B  │
  │  A  │
  └─────┘
```

En ambas estructuras, las operaciones principales tienen un costo de O(1).

#### 4.2 Conclusión grupal

La selección correcta de la estructura mejora la solución porque hace que la forma de guardar los datos coincida con la forma en que el problema los procesa. La cola (FIFO) conviene cuando se debe atender en orden de llegada, y la pila (LIFO) cuando hay que deshacer o revertir el último paso. Elegir mal obliga a agregar lógica extra, más compleja y propensa a errores, mientras que la estructura correcta mantiene las operaciones simples y eficientes.



## 4. Evidencias
##AQUI PONEN SUS PARTES
Agregar aquí capturas, resultados, pruebas o enlaces que demuestren el funcionamiento.

- [Evidencia 1]
- [Evidencia 2]
- [Evidencia 3]

## 5. Matriz de participación

| Integrante | Desarrollo | Pruebas | Documentación | Exposición | Evidencia de participación |
|---|---|---|---|---|---|
| Mariagracia Cadillo | Alta | Alta | Alta | Sí | Avtividad 4 + video |
| Mauricio Del Carpio | Alta | Alta | Alta | Sí] | [Commits, avances, etc.] |
| Diana Romero | Alta | Alta | Alta | Sí | Actividad 3 + Conclusiones + video |
| [Cristian Correa] | [Alta] | [Alta] | [Alta] | [Sí] | [Actividad 2 + Creacion del README + Informe + video] |


## 6. Video de exposición

**Video público de YouTube:** [PEGAR AQUÍ EL ENLACE]

Todos los integrantes deben participar en la exposición con sus cámaras prendidas y explicar el procedimiento, la solución desarrollada y las decisiones tomadas.

## 7. Conclusiones

- Las pilas y las colas son estructuras de datos fundamentales que permiten organizar y procesar información de acuerdo con diferentes principios. La pila utiliza LIFO, mientras que la cola utiliza FIFO, lo que determina el orden en que se insertan y eliminan los elementos.

- La aplicación de pilas y colas en los servicios académicos permite mejorar la organización de los procesos. La pila facilita la reversión de acciones recientes, mientras que la cola permite atender solicitudes respetando el orden de llegada, evitando desorganización en los procedimientos.

- La correcta selección de una estructura de datos contribuye a desarrollar soluciones más eficientes, simples y ordenadas. Comprender las diferencias entre pila y cola permite elegir la estructura más adecuada según las necesidades del problema, optimizando las operaciones y reduciendo la complejidad innecesaria de los algoritmos.
---

**Última actualización:** [03/11/2026]
