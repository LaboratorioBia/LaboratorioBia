# 📘 Estándar Corporativo de Nomenclatura para Repositorios

Este documento establece las **reglas oficiales** para nombrar los repositorios de la organización en GitHub, con el fin de garantizar **consistencia, trazabilidad y fácil identificación** de cada proyecto.

---

## 🎯 Objetivo

Definir una convención de nombres **clara y uniforme** que permita identificar rápidamente el propósito y tipo de cada repositorio.

## 📌 Alcance

Aplica a **todas las áreas de desarrollo** (aplicaciones, servicios, frontend, automatizaciones/RPAs) y **a cualquier nuevo repositorio** que se cree dentro de la organización.

---

## **1. Aplicaciones**

**Prefijo:** `APP_`  
**Formato del nombre:** **Snake Case** (`palabras_en_minúscula_separadas_por_guion_bajo`)

**Ejemplos:**

```text
APP_nombre_aplicacion
APP_convertibilidad
```

## **2. Servicios**

**Prefijo:** `SERVICE_`
**Formato del nombre: Snake Case**

**Ejemplos:**

```text
SERVICE_nombre_aplicacion
SERVICE_convertibilidad
```

## **3. Frontend**

**Prefijo:** `FRONT_`
**Formato del nombre: Snake Case**

**Ejemplos:**

```text Copiar
FRONT_nombre_aplicacion
FRONT_convertibilidad
```

## **4. RPA (Automatizaciones)**

**Prefijo:** `RPAS-`
**Formato del nombre: Pascal Case**(`CadaPalabraEmpiezaConMayúscula`)

**Ejemplos:**

```text
RPAS-NombreRpaOArea
RPAS-PlaneacionFinanciera
```

---

## **Resumen de las reglas**

| **Tipo de Repositorio** | **Prefijo** | **Formato** | **Ejemplo**                 |
| ----------------------- | ----------- | ----------- | --------------------------- |
| Aplicación              | `APP_`      | Snake Case  | `APP_convertibilidad`       |
| Servicio                | `SERVICE_`  | Snake Case  | `SERVICE_convertibilidad`   |
| Frontend                | `FRONT_`    | Snake Case  | `FRONT_convertibilidad`     |
| RPA                     | `RPAS-`     | Pascal Case | `RPAS-PlaneacionFinanciera` |

---

## **🏗 Ejemplo de Estructura Recomendada**

```
APP_convertibilidad/
  │
  ├── docs/                                 # Documentación del proyecto
  ├── FRONT_convertivilidad/                # Código del Front
  ├── BACK_convertibilidad/                 # Código del Back
  └── README.md                             # Información general del repositorio
```

---

## **🔒 Nota:**

- El nombre del repositorio debe representar claramente el propósito del proyecto.

- No se permiten espacios ni caracteres especiales fuera del estándar descrito.

- Mantener la convención facilita búsqueda, mantenimiento y escalabilidad de los proyectos.
