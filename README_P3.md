# README — Evaluación

> **Curso:** ALGORITMO Y ESTRUCTURA DE DATOS BASADOS EN INTELIGENCIA ARTIFICIAL  -  
> **Código:** 4682  
> **Evaluación:** [ PA3 ]  
> **Equipo:** [Grupo 6]  

## 1. Integrantes

| Integrante | Rol | Aporte principal |
|---|---|---|
| [Nombre 1] | [Rol] | [Aporte] |
| Mauricio Del Carpio | Participante | Actividad 1 + Video |
| Diana Romero | Participante | Actividad 3 + Conclusiones + video |
| [Nombre 4] | [Rol] | [Aporte] |
| [Nombre 5] | [Rol] | [Aporte] |

## 2. Descripción y objetivo

**Problema:**  
Determinar cómo utilizar las estructuras de datos pila (LIFO) y cola (FIFO) para organizar las acciones y solicitudes de los estudiantes en una unidad de servicios académicos, considerando el orden correcto de procesamiento.

**Objetivo:**  
Comprender y aplicar las estructuras de datos pila y cola mediante el diseño de algoritmos y representaciones gráficas, identificando sus características, operaciones principales y aplicaciones prácticas para resolver situaciones reales de manera eficiente.

**Solución desarrollada:**  
Se desarrollaron algoritmos para apilar, desapilar, encolar, desencolar, visualizar el tope o frente y verificar si las estructuras están vacías. Asimismo, se compararon ambas estructuras para identificar su aplicación adecuada: la pila para revertir acciones recientes y la cola para atender solicitudes académicas según su orden de llegada.

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

La elección depende del orden en que deben procesarse los elementos. Las pilas son apropiadas cuando se necesita atender primero el elemento mas reciente, mientras que las colas son ideales cuando se requiere respetar el orden de llegada. Estas estructuras permiten organizar eficientemente los datos y optimizar los procesos de atención y procesamiento.


## 4. Evidencias
##AQUI PONEN SUS PARTES
Agregar aquí capturas, resultados, pruebas o enlaces que demuestren el funcionamiento.

- [Evidencia 1]
- [Evidencia 2]
- [Evidencia 3]

## 5. Matriz de participación

| Integrante | Desarrollo | Pruebas | Documentación | Exposición | Evidencia de participación |
|---|---|---|---|---|---|
| [Nombre 1] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |
| Mauricio Del Carpio | Alta | Alta | Alta | Sí] | [Commits, avances, etc.] |
| Diana Romero | Alta | Alta | Alta | Sí | Actividad 3 + video |
| [Nombre 4] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |
| [Nombre 5] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |

## 6. Video de exposición

**Video público de YouTube:** [PEGAR AQUÍ EL ENLACE]

Todos los integrantes deben participar en la exposición con sus cámaras prendidas y explicar el procedimiento, la solución desarrollada y las decisiones tomadas.

## 7. Conclusiones

- Las pilas y las colas son estructuras de datos fundamentales que permiten organizar y procesar información de acuerdo con diferentes principios. La pila utiliza LIFO, mientras que la cola utiliza FIFO, lo que determina el orden en que se insertan y eliminan los elementos.

- La aplicación de pilas y colas en los servicios académicos permite mejorar la organización de los procesos. La pila facilita la reversión de acciones recientes, mientras que la cola permite atender solicitudes respetando el orden de llegada, evitando desorganización en los procedimientos.

- La correcta selección de una estructura de datos contribuye a desarrollar soluciones más eficientes, simples y ordenadas. Comprender las diferencias entre pila y cola permite elegir la estructura más adecuada según las necesidades del problema, optimizando las operaciones y reduciendo la complejidad innecesaria de los algoritmos.
---

**Última actualización:** [03/11/2026]
