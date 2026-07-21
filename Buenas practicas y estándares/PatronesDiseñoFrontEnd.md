# FrontEnd Architecture

Este proyecto utiliza dos patrones principales para construir aplicaciones escalables y fáciles de mantener:

- **Atomic Design** → Organiza los componentes visuales.
- **Feature-Based Architecture** → Organiza la lógica del negocio.

La combinación de ambos permite separar responsabilidades, reutilizar código y facilitar el crecimiento del proyecto.

---

# Estructura General

```
src/
│
├── app/            # Rutas (Next.js App Router)
├── components/     # Componentes reutilizables (Atomic Design)
├── features/       # Lógica del negocio
├── hooks/          # Hooks globales
├── services/       # Cliente HTTP
├── store/          # Estado global
├── lib/            # Configuración
├── utils/          # Funciones auxiliares
├── types/          # Tipos globales
└── styles/         # Estilos
```

---

# Atomic Design

Atomic Design organiza la interfaz desde lo más pequeño hasta una página completa.

```
Atoms
   ↓
Molecules
   ↓
Organisms
   ↓
Templates
   ↓
Pages
```

## Atoms

Son los componentes básicos.

Ejemplos:

- Button
- Input
- Label
- Icon
- Badge

> Solo renderizan información. No contienen lógica de negocio.

---

## Molecules

Combinan varios átomos para crear componentes reutilizables.

Ejemplos:

- SearchInput
- UserCard
- FormField

---

## Organisms

Representan secciones completas de la interfaz.

Ejemplos:

- Navbar
- Sidebar
- UserTable
- LoginForm

---

## Templates

Definen la estructura de una página.

Ejemplo:

```
Header
Sidebar
Main Content
Footer
```

Un Template únicamente organiza componentes; no realiza llamadas a APIs ni contiene lógica de negocio.

---

## Pages

Son las rutas de Next.js.

Su responsabilidad es conectar el Template con las Features.

---

# Feature-Based Architecture

Cada módulo del negocio vive dentro de una **Feature**.

Ejemplo:

```
features/
│
├── users/
├── roles/
├── catalogs/
└── automation/
```

Cada Feature contiene únicamente lo necesario para funcionar.

```
users/
│
├── components/
├── hooks/
├── services/
├── schemas/
├── types/
└── utils/
```

De esta forma, toda la lógica relacionada con Usuarios permanece aislada del resto del sistema.

---

# Flujo de la Aplicación

La información siempre sigue el mismo recorrido:

```
Usuario
   ↓
Page
   ↓
Feature
   ↓
Hook
   ↓
Service
   ↓
API
   ↓
Backend
```

Los componentes visuales **nunca** consumen APIs directamente.

---

# Manejo del Estado

Se utilizan distintos mecanismos según la necesidad.

| Herramienta | Uso |
|------------|-----|
| useState | Estado local de un componente |
| Zustand | Estado compartido entre pantallas |
| TanStack Query | Datos obtenidos del Backend (cache, refetch, sincronización) |

---

# Responsabilidades

| Carpeta | Responsabilidad |
|----------|-----------------|
| components | Componentes reutilizables |
| features | Lógica del negocio |
| hooks | Comportamiento reutilizable |
| services | Comunicación con la API |
| store | Estado global |
| utils | Funciones auxiliares |
| types | Interfaces y tipos |
| schemas | Validaciones (Zod) |

---

# Buenas Prácticas

✅ Cada componente debe tener **una única responsabilidad**.

✅ Mantener la lógica del negocio dentro de las **Features**, no en los componentes.

✅ Centralizar todas las llamadas HTTP en **Services**.

✅ Reutilizar componentes antes de crear nuevos.

✅ Utilizar TypeScript evitando `any`.

✅ Crear Hooks para reutilizar comportamiento.

✅ Mantener los componentes pequeños y fáciles de leer.

✅ Evitar rutas relativas largas (`../../../`); usar aliases (`@/features`, `@/components`).

✅ Nombrar archivos de forma consistente:
- `UserTable.tsx`
- `useUsers.ts`
- `user.service.ts`
- `user.schema.ts`

---

# Principios de Desarrollo

El proyecto sigue principios ampliamente utilizados en desarrollo de software:

- **SOLID** → Cada módulo tiene una responsabilidad clara y puede extenderse sin modificar código existente.
- **DRY (Don't Repeat Yourself)** → Evitar duplicar lógica; reutilizar componentes, hooks y utilidades.
- **KISS (Keep It Simple)** → Priorizar soluciones simples y fáciles de entender.
- **YAGNI (You Aren't Gonna Need It)** → Desarrollar únicamente la funcionalidad necesaria.

---

# Resumen

La arquitectura busca separar claramente la **interfaz** de la **lógica del negocio**:

- **Atomic Design** organiza cómo se construye la interfaz.
- **Features** organizan cómo funciona el negocio.
- **Hooks** reutilizan comportamiento.
- **Services** centralizan la comunicación con el Backend.
- **Store** comparte estado entre componentes.

Esta separación facilita el mantenimiento, la escalabilidad y la incorporación de nuevos desarrolladores al proyecto.
