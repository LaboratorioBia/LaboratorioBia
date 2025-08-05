# 🎨 Estándar Corporativo de Nomenclatura para Frontend

Este documento define las reglas oficiales para el **nombrado de componentes, variables, funciones, carpetas y archivos** en proyectos Frontend, asegurando consistencia en toda la base de código.

---

## 🎯 Objetivo

Establecer un **criterio uniforme** para la nomenclatura utilizada en el desarrollo Frontend, facilitando la **lectura, mantenimiento y escalabilidad** de los proyectos.

---

## **1. PascalCase**

- **Definición:**  
  Todas las palabras inician con **mayúscula** y **sin separadores** (ni guiones ni guiones bajos).
- **Uso:**
  - **Componentes React/etc.**
  - **Archivos de componentes**

**Ejemplos:**

```tsx
<MiComponente/>
export const BotonPrincipal = () {}
export function HeaderLayout () {}
```

## **2. camelCase**

- **Definición:**
  La primera palabra va en **minúscula** y las siguientes comienzan con **mayúscula**, sin separadores.

- **Uso:**

  - **Variables**

  - **Funciones**

  - **Archivos y carpetas no relacionados a componentes**

**Ejemplos:**

```js
let miVariable;
const calcularTotal = () => {};
function obtenerDatosUsuario() {}
```

---

## **Resumen de reglas**

| **Contexto**            | **Convención** | **Ejemplo**        |
| ----------------------- | -------------- | ------------------ |
| Componentes             | PascalCase     | `MiComponente`     |
| Archivos de componentes | PascalCase     | `HeaderLayout.jsx` |
| Variables               | camelCase      | `totalPedido`      |
| Funciones               | camelCase      | `calcularTotal()`  |
| Carpetas genéricas      | camelCase      | `utils`            |

---

## **🔒 Nota:**

- **Evitar** el uso de guiones (`-`) o guiones bajos (`_`) en nombres.

- Mantener la **consistencia en toda la base de código** es prioridad.

- El nombre debe **representar claramente** el propósito del archivo, componente o función.
