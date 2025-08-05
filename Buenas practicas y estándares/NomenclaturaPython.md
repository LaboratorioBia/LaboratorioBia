# Estándar Corporativo de Nomenclatura para Backend en Python

Este documento define las reglas oficiales para el **nombrado de archivos, funciones, variables, clases y módulos** en proyectos desarrollados con **Python**, garantizando una base de código clara, mantenible y consistente.

---

## 🎯 Objetivo

Establecer una convención de nombres alineada con las **buenas prácticas de Python (PEP 8)** y los estándares internos de la organización.

---

## **1. snake_case (Para Python)**

- **Definición:**  
  Todas las letras en **minúscula**, separadas por **guiones bajos (`_`)**.
- **Uso:**
  - **Variables**
  - **Funciones**
  - **Archivos y módulos**

**Ejemplos:**

```python
total_pedido = 1500
def calcular_total_pedido():
    return total_pedido * 1.19
```

## **2. PascalCase (para Clases)**

- **Definición:**

  Todas las palabras comienzan con **mayúscula** y no se usan separadores.

- **Uso:**

  - **Clases y modelos**

**Ejemplos:**

```python
class PedidoCliente:
  def __init__(self, nombre, total):
    self.nombre = nombre
    self.total = total
```

---

## **Resumen de reglas**

| **Contexto**       | **Convención** | **Ejemplo**               |
| ------------------ | -------------- | ------------------------- |
| Variables          | snake_case     | `total_pedido`            |
| Funciones          | snake_case     | `calcular_total_pedido()` |
| Archivos y módulos | snake_case     | `procesar_datos.py`       |
| Clases             | PascalCase     | `PedidoCliente`           |

---

## **3. Ejemplo de estructura de proyecto**

```text
backend_proyecto/
  │
  ├── app/
  │   ├── models/
  │   │   └── pedido_cliente.py     # Modelo PedidoCliente
  │   ├── services/
  │   │   └── procesar_datos.py     # Funciones y lógica de negocio
  │   └── main.py                   # Punto de entrada
  │
  └── tests/
      └── test_procesar_datos.py    # Pruebas unitarias

```

---

## **🔒 Nota:**

- Seguir siempre las recomendaciones de **PEP 8.**

- Los nombres deben ser **descriptivos y claros** sobre su función o contenido.

- Evitar abreviaturas innecesarias y nombres genéricos como `data` o `temp`.
