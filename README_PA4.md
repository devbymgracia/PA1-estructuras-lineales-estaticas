# README — Evaluación

> **Curso:** Algoritmo y Estructura de Datos Basados en IA  
> **Código:** 4682  
> **Evaluación:** [ PA4 ]  
> **Equipo:** [Grupo 6]  

## 1. Integrantes

| Integrante | Rol | Aporte principal |
|---|---|---|
| [Nombre 1] | [Rol] | [Aporte] |
| Mauricio Del Carpio Torres | Integrante | Actividad 3 |
| [Nombre 3] | [Rol] | [Aporte] |
| [Nombre 4] | [Rol] | [Aporte] |


## 2. Descripción y objetivo

Actividad 1. Recursividad aplicada
Actividad 2. Ordenamiento recursivo 
Actividad 3. Modelado del problema mediante grafos

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

Actividad 4. Argumentación final 

## 4. Evidencias

Agregar aquí capturas, resultados, pruebas o enlaces que demuestren el funcionamiento.

- [Evidencia 1]
- [Evidencia 2]
- [Evidencia 3]

## 5. Matriz de participación

| Integrante | Desarrollo | Pruebas | Documentación | Exposición | Evidencia de participación |
|---|---|---|---|---|---|
| [Nombre 1] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |
| Mauricio Del Carpio | Alta | Alta | Alta | Sí | [Commits, avances, etc.] |
| [Nombre 3] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |
| [Nombre 4] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |


## 6. Video de exposición

**Video público de YouTube:** [PEGAR AQUÍ EL ENLACE]

Todos los integrantes deben participar en la exposición con sus cámaras prendidas y explicar el procedimiento, la solución desarrollada y las decisiones tomadas.

## 7. Conclusiones

- [Conclusión 1]
- [Conclusión 2]
- [Conclusión 3]

---

**Última actualización:** [DD/MM/AAAA]
