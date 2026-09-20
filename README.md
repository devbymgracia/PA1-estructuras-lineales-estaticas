# README — Evaluación PA1

> **Curso:** Algoritmo y Estructura de Datos Basados en Inteligencia Artificial  
> **NRC:** 4682
> **Evaluación:** PA1 — Estructuras lineales estáticas  
> **Equipo:** Grupo 3 

## 1. Integrantes

| Integrante | Rol | Aporte principal |
|---|---|---|
| Mariagracia Cadillo Jiménez | Coordinador | Repositorio- READ ME- Actividad 4|
| [Nombre 2] | [Rol] | [Aporte] |
| [Nombre 3] | [Rol] | [Aporte] |
| [Nombre 4] | [Rol] | [Aporte] |

## 2. Descripción y objetivo

**Problema:**  
Una coordinación académica necesita organizar información de talleres estudiantiles: registrar cantidades de inscritos, ordenar resultados, realizar consultas puntuales y representar la distribución de estudiantes por aulas y horarios. En esta primera etapa se trabaja únicamente con estructuras lineales estáticas.

**Objetivo:**  
Diseñar una solución clara y sustentada técnicamente usando arreglos unidimensionales y matrices, aplicando algoritmos de búsqueda de valores extremos, inserción, ordenamiento y recorrido de matrices.

**Solución desarrollada:**  
- **Análisis y selección de estructura (Actividad 1):** [resumen]
- **Vectores (Actividad 2):** [resumen]
- **Matrices (Actividad 3):** [resumen]
**Matrices especiales (Actividad 4):** se explicaron la matriz cuadrada y la matriz poco densa, y se justificó con un ejemplo del caso académico que una matriz poco densa es más conveniente cuando la mayoría de las combinaciones de aula y horario no tienen estudiantes.

## 3. Estructura del repositorio

```
PA1-estructuras-lineales-estaticas/
└── README.md
```

## 4. Cómo revisar

**Pasos de revisión:**
1. Leer el desarrollo de cada actividad en la sección 5 de este README.
2. Consultar la matriz de participación en la sección 6.
3. Ver el video de exposición (sección 7).


## 5. Desarrollo de la evaluación

### Actividad 1. Análisis del problema y selección de estructura

[Pegar aquí el desarrollo de la Actividad 1.]

### Actividad 2. Modelado y operaciones con vectores

[Pegar aquí el desarrollo de la Actividad 2.]

### Actividad 3. Matrices y recorrido completo de datos

[Pegar aquí el desarrollo de la Actividad 3.]

### Actividad 4. Matrices especiales y decisión técnica

#### 4.1 Matriz cuadrada

Una matriz cuadrada es aquella que tiene la misma cantidad de filas y columnas (n x n).

```
[ 1  2  3 ]
[ 4  5  6 ]
[ 7  8  9 ]
```

#### 4.2 Matriz poco densa

Una matriz poco densa es aquella en la que la mayoría de sus posiciones contienen valores 0 o no contienen información relevante, mientras que solo algunas posiciones contienen datos.

```
[20   0   0   0]
[ 0   0  15   0]
[ 0   0   0   0]
[ 0  18   0   0]
```

#### 4.3 Ejemplo aplicado al caso académico

En el caso de los talleres estudiantiles, las filas representan aulas y las columnas bloques horarios. Si solamente algunas aulas tienen estudiantes registrados en determinados horarios, la matriz tendrá muchas posiciones con valor 0 y pocas con datos.

Matriz completa de 4 aulas x 5 bloques (20 celdas):

```
          B1   B2   B3   B4   B5
Aula 1  [ 20    0    0    0    0 ]
Aula 2  [  0    0   15    0    0 ]
Aula 3  [  0    0    0    0    0 ]
Aula 4  [  0   18    0    0    0 ]
```

Solo 3 de las 20 celdas tienen datos (15 %), y el 85 % son ceros. Representación compacta, con índices desde 0:

| Fila | Columna | Valor |
|---|---|---|
| 0 | 0 | 20 |
| 1 | 2 | 15 |
| 3 | 1 | 18 |

Pseudocódigo para construir la representación compacta:

```
Para i desde 0 hasta 3:
    Para j desde 0 hasta 4:
        Si matriz[i][j] ≠ 0:
            Agregar (i, j, matriz[i][j]) a la lista
```

#### 4.4 Justificación

- Se evita almacenar y procesar posiciones sin información.
- La matriz completa guarda 20 valores. La compacta guarda 3 registros de 3 datos (9 valores), por lo que usa menos de la mitad de memoria.
- La ventaja crece si el sistema se amplía a más aulas y horarios, porque la cantidad de ceros crece más rápido que los datos reales.
- Si casi todas las aulas estuvieran ocupadas en todos los horarios, la matriz completa sería mejor, porque cada dato compacto necesita 3 valores y el ahorro desaparecería.



## 6. Matriz de participación

| Integrante | Desarrollo | Pruebas | Documentación | Exposición | Evidencia de participación |
|---|---|---|---|---|---|
| Mariagracia Cadillo Jiménez  | Alta | Media | Alta | Sí | Creó el repositorio, redactó la Actividad 4, armó el README base y expuso en el video. Commits en el historial del repositorio. |
| [Nombre 2] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc] |
| [Nombre 3] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |
| [Nombre 4] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |

## 7. Video de exposición

**Video de YouTube:** [PEGAR AQUÍ EL ENLACE]


## 8. Conclusiones

- [Conclusión 1]
- [Conclusión 2]
Los algoritmos sobre vectores y el recorrido de matrices por filas y columnas permiten registrar, consultar y organizar la información de inscritos y de ocupación de aulas de forma ordenada.

---

MENSAJE PARA EL GRUPO 
Ya está creado el repositorio: [LINK]. Cada uno debe:
1. Entrar al README.md y hacer clic en el lápiz (Edit).
2. Pegar su actividad en la sección 5, debajo de su título.
3. Llenar su nombre, rol y aporte en la sección 1, y su fila en la sección 6 (con evidencia real).
4. Agregar 1 conclusión sobre su actividad en la sección 8, borrando los textos entre corchetes que sobren.
5. Hacer Commit changes con su usuario.
Fecha límite: martes, 22 de septiembre . De ahí,  grabar el video (cada uno de sus partes), todos con cámara prendida.

**Última actualización:** [DD/MM/AAAA]
