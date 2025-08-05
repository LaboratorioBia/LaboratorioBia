# 📝 Estándar Corporativo para Documentación de Código

Este documento establece las **buenas prácticas de documentación** para **funciones, clases y componentes**, con el objetivo de facilitar el **mantenimiento, la comprensión y la colaboración** en los proyectos.

---

## 🎯 Objetivo

Definir un estándar que permita **documentar lo necesario** (sin redundancias), asegurando que el código sea **autodescriptivo** y que la documentación agregue **valor real**.

---

## **1. Principios Clave**

- **No todo debe documentarse:**
  - El código **limpio y bien nombrado** no necesita comentarios innecesarios.
  - Documentar solo cuando **el propósito o lógica no sea evidente**.
- **Documentar el “por qué” y el “cómo”, no el “qué”:**
  - Evitar describir lo obvio (ej.: `# suma dos números` en `a + b`).
  - Enfocarse en el **contexto**, **decisiones importantes** y **casos especiales**.
- **Mantener actualizada la documentación:**
  - Un comentario desactualizado es peor que no tenerlo.

## **2. Documentación en Funciones**

### **Cuándo documentar:**

- Si la función **es compleja**, tiene **parámetros no evidentes** o **retorna algo importante**.
- Si hay **reglas de negocio** o **restricciones** no obvias.

### **Ejemplo en Python:**

```python
def calcular_precio_final(subtotal: float, descuento: float = 0.0, impuestos: float = 0.19) -> float:
    """
    Calcula el precio final de un pedido aplicando descuento e impuestos.

    Args:
        subtotal (float): Precio base del pedido.
        descuento (float): Descuento a aplicar (por defecto 0.0).
        impuestos (float): Porcentaje de impuestos (por defecto 0.19).

    Returns:
        float: Precio final después de aplicar descuento e impuestos.

    Nota:
        Si el descuento es mayor al 50%, se aplica una validación adicional en otro servicio.
    """
    return (subtotal - subtotal * descuento) * (1 + impuestos)
```

### **Ejemplo en JavaScript (JSDoc):**

```js
/**
 * Calcula el precio final de un pedido aplicando descuento e impuestos.
 * @param {number} subtotal - Precio base del pedido.
 * @param {number} [descuento=0] - Descuento a aplicar (0 por defecto).
 * @param {number} [impuestos=0.19] - Porcentaje de impuestos (0.19 por defecto).
 * @returns {number} Precio final después de aplicar descuento e impuestos.
 */
function calcularPrecioFinal(subtotal, descuento = 0, impuestos = 0.19) {
  return (subtotal - subtotal * descuento) * (1 + impuestos);
}
```

## **3. Documentación en Clases**

### **Cuándo documentar:**

Para describir el **propósito general** de la clase.

Si la clase representa una **entidad de negocio importante** o tiene **métodos clave**.

### **Ejemplo:**

```python
class Pedido:
    """
    Representa un pedido de cliente con métodos para calcular su valor y aplicar descuentos.
    """

    def __init__(self, cliente: str, productos: list):
        self.cliente = cliente
        self.productos = productos

    def calcular_total(self) -> float:
        """Calcula el total del pedido sumando todos los productos."""
        return sum(p['precio'] for p in self.productos)
```

## **4. Documentación en Componentes (Frontend)**

### **Cuándo documentar:**

- Si el componente es **reutilizable** y tiene **props complejas**.

- Si implementa **lógica de negocio** o **interacciones no triviales.**

### **Ejemplo en React (TypeScript):**

```tsx
/**
 * Componente de formulario para crear o editar un pedido.
 *
 * @param {Object} props - Propiedades del componente.
 * @param {Pedido} props.pedido - Pedido a editar (si existe).
 * @param {Function} props.onSubmit - Función que se ejecuta al guardar el formulario.
 */
export default function PedidoForm({
  pedido,
  onSubmit,
}: {
  pedido?: Pedido;
  onSubmit: (p: Pedido) => void;
}) {
  // Estado y lógica del formulario
  return <form>{/* Campos y botones */}</form>;
}
```

## **5. Qué NO documentar**

- **Código trivial:** Ej.: `i += 1 #` incrementa en 1 → Esto se entiende sin comentario.

- **Comentarios obvios:** Repetir el nombre de la función o variable en el comentario.

- **Código muerto o comentado:** Si ya no se usa, elimínalo.

---

## **Resumen: Cuándo documentar**

- ### **Sí documentar:**

  - Reglas de negocio complejas.

  - Parámetros y valores de retorno no evidentes.

  - Decisiones importantes y excepciones.

- ### **No documentar:**

  - Código autodescriptivo.

  - Comentarios redundantes.

  - Código temporal o desactualizado.
