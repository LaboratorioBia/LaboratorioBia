# Estándar Corporativo de Nomenclatura para Enrutado (kebab-case)

Este documento define las reglas oficiales para el **nombrado de rutas** en proyectos **web** (Django, Vite, Next.js), utilizando **kebab-case** para mantener URLs **legibles, consistentes y amigables para SEO**.

---

## 🎯 Objetivo

Establecer una **convención uniforme** para las rutas de los proyectos web, que facilite la lectura y el mantenimiento, además de mejorar la experiencia del usuario y el posicionamiento en buscadores.

---

## **1. kebab-case**

- **Definición:**  
  Todas las letras en **minúscula**, separadas por **guiones (`-`)**.
- **Uso:**
  - **Rutas de acceso (URLs)**
  - **Carpetas y archivos asociados a las rutas (en frameworks con enrutado basado en archivos)**

**Ejemplos:**

```text
/crear-usuario
/productos/detalle-producto
/mi-cuenta/configuracion
```

## **2. Enrutado en Django**

En Django, las rutas se definen en `urls.py` utilizando kebab-case:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('crear-usuario/', views.crear_usuario, name='crear-usuario'),
    path('detalle-producto/<int:producto_id>/', views.detalle_producto, name='detalle-producto'),
    path('mi-cuenta/configuracion/', views.configuracion_cuenta, name='configuracion-cuenta'),
]
```

**Puntos clave:**

- Las rutas siempre en kebab-case.

- Los nombres de vistas y funciones siguen la convención de snake_case (PEP8).

- Para rutas dinámicas, usar <<tipo:parametro>>.

## **3. Enrutado en Vite (React Router)**

En Vite, usando **React Router**, las rutas también deben definirse en **kebab-case**:

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import CrearUsuario from "./pages/crear-usuario";
import DetalleProducto from "./pages/detalle-producto";
import ConfiguracionCuenta from "./pages/mi-cuenta/configuracion";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/crear-usuario" element={<CrearUsuario />} />
        <Route
          path="/detalle-producto/:productoId"
          element={<DetalleProducto />}
        />
        <Route
          path="/mi-cuenta/configuracion"
          element={<ConfiguracionCuenta />}
        />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

**Puntos clave:**

- Carpetas y archivos en kebab-case (pages/crear-usuario.jsx).

- Parámetros dinámicos con :nombreParametro.

## **4. Enrutado en Next.js (con rutas dinámicas)**

En Next.js, el enrutado se basa en el nombre de las carpetas/archivos dentro de `app` o `pages`. Se recomienda **kebab-case** para las rutas y carpetas:

**Estructura de carpetas:**

```plaintext

app/
├── crear-usuario/
│ └── page.tsx
├── detalle-producto/
│ └── [producto-id]/
│ └── page.tsx
└── mi-cuenta/
└── configuracion/
└── page.tsx
```

**Ejemplo dinámico (`[producto-id]`):**

```tsx
import { useParams } from "next/navigation";

export default function DetalleProducto() {
  const { "producto-id": productoId } = useParams();

  return <h1>Detalle del producto: {productoId}</h1>;
}
```

**Puntos clave:**

- Carpetas y archivos en kebab-case.

- Rutas dinámicas entre corchetes ([producto-id]).

- Mantener coherencia entre nombres de carpetas y URL.

---

## **Resumen de reglas**

| **Contexto**       | **Convención**                          | **Ejemplo**                                                                |
| ------------------ | --------------------------------------- | -------------------------------------------------------------------------- |
| Rutas estáticas    | kebab-case                              | `/crear-usuario`                                                           |
| Rutas dinámicas    | kebab-case                              | `/detalle-producto/:id`                                                    |
| Carpetas (Next.js) | kebab-case                              | `app/detalle-producto/`                                                    |
| Parámetros         | snake_case o kebab-case según framework | `<producto_id>` (Django), `:productoId` (React), `[producto-id]` (Next.js) |

---

## **🔒 Nota:**

- Evitar mayúsculas, guiones bajos (`_`) o espacios en rutas.

- Los nombres deben ser **descriptivos y orientados a la acción o al contenido.**

- Mantener consistencia entre **URL, carpeta y componente.**
