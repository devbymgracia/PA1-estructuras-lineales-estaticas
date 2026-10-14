# README — Evaluación PA2

> **Curso:** Algoritmo y Estructura de Datos Basados en Inteligencia Artificial  
> **Código:** 30710  
> **Evaluación:** PA2 — Listas enlazadas  
> **Equipo:** Grupo 6  

## 1. Integrantes

| Integrante | Rol | Aporte principal |
|---|---|---|
| Mariagracia Cadillo Jiménez |   Coordinador | [Actividad1 |
| [Nombre 2] | [Rol] | [Aporte] |
| [Cristian Martin Correa Barriga] | [Rol] | [Aporte] |
| [Nombre 4] | [Rol] | [Aporte] |

## 2. Descripción y objetivo

**Problema:**  
Una organización necesita gestionar una secuencia dinámica de solicitudes de atención, donde constantemente ingresan nuevos casos, algunos se eliminan, otros deben reubicarse, y en ciertos procesos se necesita navegar en ambos sentidos o mantener un ciclo continuo de revisión.

**Objetivo:**  
Diseñar una solución usando listas enlazadas (simples, dobles y circulares) que permita representar, recorrer, insertar, buscar, modificar y eliminar solicitudes de forma dinámica.

**Solución desarrollada:**  
- **Fundamentos y representación (Actividad 1):** se explicó qué es una lista enlazada, su clasificación (simple, doble, circular) y se representó una lista de 5 solicitudes de atención.
- **Recorrido e inserción (Actividad 2):** se diseñaron algoritmos de recorrido, e inserción al inicio, al final y después de un nodo dado.
- **Búsqueda, modificación y eliminación (Actividad 3):** se diseñaron algoritmos de búsqueda por id, modificación de un nodo y eliminación con reajuste de enlaces, comparando la eficiencia según el punto de intervención.
- **Listas dobles y circulares (Actividad 4):** se plantearon situaciones del caso donde conviene cada tipo de lista, con su representación gráfica y justificación.

## 3. Estructura del repositorio

```
PA2-listas-enlazadas/
├── README.md
└── informe-PA2.pdf
```

## 4. Cómo revisar

**Pasos de revisión:**
1. Leer el desarrollo de cada actividad en la sección 5 de este README.
2. Revisar el informe en PDF (`informe-PA2.pdf`) como respaldo.
3. Consultar la matriz de participación en la sección 6.
4. Ver el video de exposición (sección 7).

## 5. Desarrollo de la evaluación

### Actividad 1. Fundamentos y representación de listas enlazadas

#### 1.1 ¿Qué es una lista enlazada?

Una lista enlazada es una estructura de datos dinámica donde cada elemento (nodo) contiene un dato y una referencia (enlace) al siguiente nodo. A diferencia de un arreglo, no ocupa un espacio fijo en memoria: puede crecer o reducirse mientras el programa se ejecuta, porque cada nodo se crea o elimina de forma independiente.

#### 1.2 Clasificación

- **Lista simple:** cada nodo apunta solo al siguiente. Se recorre en un solo sentido.
- **Lista doble:** cada nodo apunta al siguiente y al anterior. Se recorre en ambos sentidos.
- **Lista circular:** el último nodo apunta de vuelta al primero (en vez de apuntar a `null`), formando un ciclo.

#### 1.3 Representación gráfica básica

```
[Dato | Siguiente] -> [Dato | Siguiente] -> [Dato | Siguiente] -> NULL
```

#### 1.4 Representación aplicada al caso (5 nodos)

Lista de solicitudes de atención, cada nodo con un id y el motivo:

```
[S1: Consulta] -> [S2: Reclamo] -> [S3: Soporte] -> [S4: Consulta] -> [S5: Reclamo] -> NULL
```

#### 1.5 Clase Nodo

```java
public class Nodo {
    int id;
    String motivo;
    Nodo siguiente;

    public Nodo(int id, String motivo) {
        this.id = id;
        this.motivo = motivo;
        this.siguiente = null;
    }
}
```

### Actividad 2. Recorrido e inserción

#### 2.1 Recorrido completo

```java
public static void recorrer(Nodo cabeza) {
    Nodo actual = cabeza;
    System.out.println("Lista de solicitudes:");
    while (actual != null) {
        System.out.println("Solicitud " + actual.id + ": " + actual.motivo);
        actual = actual.siguiente;
    }
}
```

#### 2.2 Inserción al inicio

```java
public static Nodo insertarAlInicio(Nodo cabeza, int id, String motivo) {
    Nodo nuevo = new Nodo(id, motivo);
    nuevo.siguiente = cabeza;
    return nuevo;
}
```

**Cómo cambia la estructura:** el nuevo nodo pasa a ser la cabeza de la lista y su enlace apunta al nodo que antes era el primero.

#### 2.3 Inserción al final

```java
public static Nodo insertarAlFinal(Nodo cabeza, int id, String motivo) {
    Nodo nuevo = new Nodo(id, motivo);

    if (cabeza == null) {
        return nuevo;
    }

    Nodo actual = cabeza;
    while (actual.siguiente != null) {
        actual = actual.siguiente;
    }
    actual.siguiente = nuevo;

    return cabeza;
}
```

**Cómo cambia la estructura:** hay que recorrer toda la lista hasta encontrar el último nodo, y se enlaza el nuevo nodo ahí. La cabeza no cambia.

#### 2.4 Inserción después de un nodo dado

```java
public static void insertarDespuesDe(Nodo nodoReferencia, int id, String motivo) {
    if (nodoReferencia == null) {
        System.out.println("El nodo de referencia no existe.");
        return;
    }

    Nodo nuevo = new Nodo(id, motivo);
    nuevo.siguiente = nodoReferencia.siguiente;
    nodoReferencia.siguiente = nuevo;
}
```

**Cómo cambia la estructura:** el nuevo nodo se enlaza entre el nodo de referencia y el nodo que antes era su siguiente.

#### 2.5 Representación gráfica de los cambios

```
Antes:                       [S1] -> [S2] -> [S3]
Insertar al inicio (S0):     [S0] -> [S1] -> [S2] -> [S3]
Insertar al final (S4):      [S0] -> [S1] -> [S2] -> [S3] -> [S4]
Insertar después de S1 (SX): [S0] -> [S1] -> [SX] -> [S2] -> [S3] -> [S4]
```

### Actividad 3. Lista enlazada simple: búsqueda, modificación y eliminación

#### 3.1 Búsqueda (por id)

```java
public static Nodo buscarPorId(Nodo cabeza, int idBuscado) {
    Nodo actual = cabeza;

    while (actual != null) {
        if (actual.id == idBuscado) {
            return actual;
        }
        actual = actual.siguiente;
    }

    return null;
}
```

#### 3.2 Modificación de un nodo encontrado

```java
public static boolean modificarMotivo(Nodo cabeza, int id, String nuevoMotivo) {
    Nodo nodo = buscarPorId(cabeza, id);

    if (nodo == null) {
        return false;
    }

    nodo.motivo = nuevoMotivo;
    return true;
}
```

#### 3.3 Eliminación de un nodo

```java
public static Nodo eliminarPorId(Nodo cabeza, int id) {
    if (cabeza == null) {
        return null;
    }

    if (cabeza.id == id) {
        return cabeza.siguiente;
    }

    Nodo anterior = cabeza;
    Nodo actual = cabeza.siguiente;

    while (actual != null) {
        if (actual.id == id) {
            anterior.siguiente = actual.siguiente;
            return cabeza;
        }
        anterior = actual;
        actual = actual.siguiente;
    }

    return cabeza;
}
```

**Cómo se reajustan los enlaces:** el nodo `anterior` deja de apuntar al nodo eliminado y pasa a apuntar directamente al nodo que estaba después de él.

#### 3.4 Eficiencia según el punto de intervención

| Operación | Al inicio | Al final | En medio |
|---|---|---|---|
| Inserción | O(1) — directa | O(n) — hay que recorrer hasta el final | O(n) — hay que encontrar el nodo de referencia |
| Eliminación | O(1) — directa | O(n) — hay que llegar al penúltimo nodo | O(n) — hay que encontrar el nodo anterior |

### Actividad 4. Listas dobles y circulares

#### 4.1 Situación para lista doble

En el sistema de solicitudes de atención, a veces el personal necesita revisar el historial hacia atrás, por ejemplo para ver cuál fue la solicitud anterior a una que se está resolviendo, sin recorrer la lista desde el inicio cada vez. Una lista doblemente enlazada permite moverse en ambos sentidos.

```
NULL <- [S1] <-> [S2] <-> [S3] <-> [S4] -> NULL
```

```java
public class NodoDoble {
    int id;
    String motivo;
    NodoDoble anterior;
    NodoDoble siguiente;
}
```

#### 4.2 Situación para lista circular

El sistema también necesita un proceso de revisión continua: un supervisor recorre todas las solicitudes pendientes en orden, y al llegar a la última, debe volver a la primera para empezar un nuevo ciclo, sin reiniciar manualmente el recorrido.

```
   [S1] -> [S2] -> [S3] -> [S4]
    ^                        |
    |________________________|
```

```java
public class NodoCircular {
    int id;
    String motivo;
    NodoCircular siguiente;
}
// El siguiente del último nodo apunta al primer nodo, no a null
```

#### 4.3 Justificación

- La **lista doble** conviene cuando el proceso necesita navegar en ambas direcciones, como revisar el historial hacia atrás. Una lista simple solo permite avanzar.
- La **lista circular** conviene cuando el proceso es cíclico por naturaleza, como una revisión continua de turnos. La lista circular integra el ciclo de forma natural, sin necesidad de guardar aparte una referencia a la cabeza.

## 6. Matriz de participación

| Integrante | Desarrollo | Pruebas | Documentación | Exposición | Evidencia de participación |
|---|---|---|---|---|---|
| Mariagracia Cadillo Jiménez | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |
| [Nombre 2] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |
| [Cristian Martin Correa Barriga] | [Alta] | [Alta] | [Alta] | [Sí] | [Commits, avances, etc.] |
| [Nombre 4] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Alta/Media/Baja] | [Sí/No] | [Commits, avances, etc.] |

## 7. Video de exposición

**Video de YouTube:** [PEGAR AQUÍ EL ENLACE]

## 8. Conclusiones

- Las listas enlazadas permiten manejar una cantidad de solicitudes que cambia constantemente, a diferencia de las estructuras estáticas, porque los nodos se crean y eliminan de forma dinámica sin necesidad de definir un tamaño fijo desde el inicio.
- La inserción y eliminación al inicio de la lista son las operaciones más eficientes (O(1)), mientras que al final o en medio dependen de recorrer la lista hasta el punto de intervención (O(n)).
- Una lista doblemente enlazada es más adecuada cuando el proceso necesita navegar en ambos sentidos, y una lista circular es más adecuada cuando el proceso es cíclico por naturaleza.
- El trabajo en equipo, la distribución de actividades y el uso de GitHub permitieron documentar el proceso y dejar evidencia de la participación de cada integrante.

---

**Última actualización:** [DD/MM/AAAA]
