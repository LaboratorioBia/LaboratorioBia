# 🛠️ Guía Corporativa de Uso de Git y GitHub

Esta guía establece las **buenas prácticas y el flujo de trabajo oficial** para el uso de **Git y GitHub** en nuestros proyectos. Incluye desde la creación de repositorios hasta la colaboración segura entre equipos.

---

## 📌 Índice

1. [Uso de GitHub](#uso-de-github)
2. [Creación de un Repositorio](#creación-de-un-repositorio)
3. [Clonación de un Repositorio Existente](#clonación-de-un-repositorio-existente)
4. [Configuración Inicial](#configuración-inicial)
5. [Flujo de Trabajo con Ramas](#flujo-de-trabajo-con-ramas)
6. [Buenas Prácticas de Commit](#buenas-prácticas-de-commit)
7. [Subir Cambios y Pull Requests](#subir-cambios-y-pull-requests)
8. [Recomendaciones para Trabajo en Equipo](#recomendaciones-para-trabajo-en-equipo)
9. [Buenas Prácticas de Seguridad](#buenas-prácticas-de-seguridad)
10. [Errores Comunes y Cómo Evitarlos](#errores-comunes-y-cómo-evitarlos)

---

## **Uso de GitHub**

- **GitHub** es nuestra plataforma principal para almacenar, versionar y colaborar en proyectos.
- Todo desarrollo debe realizarse en **repositorios corporativos** con permisos adecuados.
- Los cambios deben gestionarse mediante **Pull Requests (PRs)**, **nunca** directamente sobre `main` o `develop`.

---

## **Creación de un Repositorio**

1. Inicia sesión en [GitHub](https://github.com/).
2. Haz clic en **"New repository"**.
3. Completa:
   - **Nombre:** Claro y significativo (`APP_sistema_pagos`).
   - **Descripción:** Breve pero informativa.
   - **Visibilidad:** Según corresponda (privado o público).
   - **README inicial:** Recomendado.
4. Haz clic en **"Create repository"**.

---

## **Clonación de un Repositorio Existente**

Para obtener una copia local del proyecto:

```bash
git clone https://github.com/usuario/repositorio.git
```

> Cambia `usuario` y `repositorio` por los valores reales.

---

## **Configuración Inicial**

Configura tus credenciales:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@empresa.com"
```

Verifica la configuración:

```bash
git config --list
```

---

## **Flujo de Trabajo con Ramas (Git Flow Simplificado)**

Nuestro flujo se basa en dos ramas principales:

- **`main`**: contiene el código en producción.
- **`develop`**: rama de integración para nuevas funcionalidades y cambios.

De **`develop`** salen las ramas temporales:

- `feature/nueva-funcionalidad` → Nuevas funcionalidades.
- `fix/correccion-bug` → Correcciones de errores.
- `hotfix/parche-urgente` → Parches críticos (pueden salir desde `main` si es urgente).

**Diagrama del flujo:**

```plaintext
main (producción)
│
└── develop (integración)
      │
      ├── feature/nueva-funcionalidad
      ├── fix/correccion-bug
      └── hotfix/parche-urgente
```

### **1. Crear una nueva rama desde develop**

```bash
git checkout develop
git pull origin develop
git checkout -b feature/nueva-funcionalidad
```

### **2. Integrar cambios cuando la tarea esté lista**

Cuando termines la funcionalidad:

```bash
git checkout develop
git pull origin develop
git merge feature/nueva-funcionalidad
```

Sube los cambios:

```bash
git push origin develop
```

### **3. Pull Request hacia main**

Una vez probados los cambios en `develop`, se crea un **Pull Request de `develop` → `main`** para liberar a producción.

---

## **Buenas Prácticas de Commit**

- **Estructura recomendada:**

```bash
git add .
git commit -m "TIPO: Descripción clara del cambio"
```

- **Tipos comunes:**

  - `FEATURE:` Nueva funcionalidad.
  - `FIX:` Corrección de errores.
  - `REFACTOR:` Mejora de código sin cambiar funcionalidad.
  - `DOCS:` Actualización de documentación.

- **Consejos:**
  - Mensajes **claros y concisos**.
  - Usa **tiempo presente** (“Agrega validación de usuario”).
  - Un commit por cambio **coherente**.

---

## **Subir Cambios y Pull Requests**

1. **Sube tu rama:**

```bash
git push origin nombre-de-la-rama
```

2. **Crea un Pull Request:**

[**Template para Pull Request**](./TempletePullRequests.md)

- Para integrar ramas de trabajo a `develop`.
- Y de `develop` hacia `main` cuando esté listo para producción.
- Describe el cambio de forma **clara y precisa**.
- Asigna revisores y etiquetas según corresponda.

---

## **Checklist antes de un Pull Request**

- [ ] ¿Mi rama está actualizada con `develop`?
- [ ] ¿Hice commits claros y atómicos?
- [ ] ¿Probé mi código antes de subirlo?
- [ ] ¿Agregué/actualicé documentación si era necesario?
- [ ] ¿Agregué pruebas si aplica?

---

## **Recomendaciones para Trabajo en Equipo**

- **Una funcionalidad = una rama.**
- **Pull requests pequeños:** más fáciles de revisar.
- **Revisiones de código** antes de fusionar.
- Usa **issues** para reportar errores o nuevas tareas.
- **Comunicación constante** en los PR (comentarios, sugerencias, feedback).

---

## **Buenas Prácticas de Seguridad**

- **Nunca subas**:
  - Claves, contraseñas, tokens.
  - Archivos `.env` o configuraciones sensibles.
- Usa un **.gitignore**:

```
# Entornos virtuales
venv/
env/
# Archivos sensibles
*.env
config/secrets.json
```

- Usa **variables de entorno** para datos sensibles.
- Configura **2FA** en tu cuenta de GitHub.

---

## **Errores Comunes y Cómo Evitarlos**

1. **Olvidar agregar archivos:**

```bash
git add archivo.py
git commit --amend
```

2. **Subir archivos sensibles:**

```bash
git rm --cached archivo_sensible.ext
git commit -m "REMOVE: Eliminar archivo sensible"
```

3. **Conflictos de fusión:**
   - Resuélvelos manualmente.
   - Marca como resuelto:

```bash
git add archivo_conflictivo.py
git commit -m "FIX: Resolver conflictos"
```

---

## **Conclusión**

El buen uso de Git y GitHub garantiza:

- **Historial limpio y entendible**.
- **Colaboración eficiente** entre equipos.
- **Seguridad y trazabilidad** en todos los cambios.

Cumplir estas buenas prácticas nos permite trabajar de forma **profesional, ordenada y segura**.

---
