# Estructura_de_Datos_Evaluaci-n2_Equipo-2

# Proyecto 1: Implementación de Grafos y Recorrido BFS

## 📋 Descripción del Proyecto
Este proyecto consiste en la implementación desde cero de una estructura de datos **Grafo (Graph)** y el algoritmo de búsqueda en anchura **(Breadth-First Search - BFS)**.

La característica principal de este desarrollo es que **no utiliza librerías externas** para la gestión de la memoria del algoritmo; en su lugar, se implementó una estructura de datos lineal tipo **Cola (Queue)** propia para gestionar el orden de visita de los vértices, cumpliendo con los requisitos estrictos de la asignación.

---

## ✅ Objetivos y Requisitos Cumplidos
El código cubre el 100% de los puntos solicitados en la especificación del proyecto:

1.  **Clase `Queue` Propia:** * Implementación de una cola FIFO.
    * Operaciones: `enqueue`, `dequeue`, `first`, `is_empty`, `size`.
2.  **Estructura `Graph`:** * Representación del grafo utilizando listas de adyacencia (Diccionario de Conjuntos).
3.  **Método `bfs(start)`:** * Retorna el orden de visita de los vértices.
4.  **Método `bfs_parents(start)`:** * Retorna un diccionario `parent[v]` esencial para la reconstrucción de caminos.
5.  **Método `path_unweighted(start, goal)`:** * Retorna la ruta (lista de vértices) si existe camino.
    * Retorna `None` si no existe conexión.

---

## 🛠️ Detalles de Implementación Técnica

### 1. Estructura de Datos: Cola (`Queue`)
Se diseñó una clase contenedora que gestiona una lista dinámica, asegurando el comportamiento *First-In, First-Out* necesario para el algoritmo BFS.
* **Manejo de Errores:** Levanta `IndexError` si se intenta desencolar de una estructura vacía.

### 2. Estructura de Datos: Grafo (`Graph`)
* **Eficiencia:** Se utilizó un diccionario donde las claves son los vértices y los valores son conjuntos (`set`) de vecinos. Esto evita aristas duplicadas automáticamente y mejora la velocidad de búsqueda.
* **Funcionalidades Extra:** Además de lo solicitado, se añadieron métodos para:
    * Calcular grados: `degree`, `in_degree`, `out_degree`.
    * Eliminación segura: `remove_edge`, `remove_vertex`.
    * Verificación: `has_edge`.

---

## 💻 Guía de Uso

### Inicialización
```python
if __name__ == "__main__":
    # Prueba 1: Grafo conexo
    g1 = Graph(directed=False)
    g1.add_edge("A", "B")
    g1.add_edge("A", "C")
    g1.add_edge("B", "D")
    g1.add_edge("C", "D")
    g1.add_edge("D", "E")
    print("PROYECTO 1: PRUEBAS")
    print("-" * 20)
    print("1. BFS en grafo conexo:")
    print(f"Orden de visita: {g1.bfs('A')}")

    # Prueba 2: Grafo con 2 componentes
    g2 = Graph(directed=False)
    g2.add_edge("Nodo_A1", "Nodo_A2")
    g2.add_edge("Nodo_B1", "Nodo_B2")

    print("\n2. Grafo con 2 componentes:")
    print(f"Visita desde componente A: {g2.bfs('Nodo_A1')}")

    # Prueba 3: Rutas no ponderadas
    print("\n3. Rutas no ponderadas:")
    ruta_con = g1.path_unweighted("A", "E")
    ruta_sin = g2.path_unweighted("Nodo_A1", "Nodo_B1")

    print(f"Ruta con camino (A a E): {ruta_con}")
    print(f"Ruta sin camino (A1 a B1): {ruta_sin}")
```
## 👀 Casos de prueba
### Demo

| Prueba | Descripción | Resultado Esperado |
| :--- | :--- | :--- |
| **1. Grafo Conexo** | Ejecutar BFS en un grafo donde todos los nodos están conectados. | Lista completa de nodos ordenados por nivel. |
| **2. Grafo Disconexo** | Ejecutar BFS en un grafo con 2 componentes aisladas. | El recorrido se limita solo a la componente inicial. |
| **3. Rutas** | Buscar caminos existentes e inexistentes. | Devuelve la lista de ruta o `None` respectivamente. |

## 👷 Autores
### Ariff Iazid Medina Gómez
### Joaquin Uriona
### Jesús Omar Uc Domínguez
