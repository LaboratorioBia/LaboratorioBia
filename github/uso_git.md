
# 🛠️ Guía de Uso de GitHub para Proyectos de Desarrollo

Esta guía proporciona las mejores prácticas y el flujo de trabajo adecuado para el uso de **GitHub** en proyectos colaborativos. Desde la creación de repositorios hasta la gestión de ramas y solicitudes de cambios.

---

## 📌 Índice

1. [Creación de un Repositorio](#creación-de-un-repositorio)
2. [Clonación de un Repositorio Existente](#clonación-de-un-repositorio-existente)
3. [Configuración Inicial](#configuración-inicial)
4. [Flujo de Trabajo con Ramas](#flujo-de-trabajo-con-ramas)
5. [Buenas Prácticas de Commit](#buenas-prácticas-de-commit)
6. [Subir Cambios y Pull Requests](#subir-cambios-y-pull-requests)
7. [Recomendaciones para Trabajo en Equipo](#recomendaciones-para-trabajo-en-equipo)
8. [Buenas Prácticas de Seguridad](#buenas-prácticas-de-seguridad)
9. [Errores Comunes y Cómo Evitarlos](#errores-comunes-y-cómo-evitarlos)

---

## 📥 Creación de un Repositorio

1. Inicia sesión en [GitHub](https://github.com/).
2. Haz clic en el botón **"New"** o **"Nuevo repositorio"**.
3. Completa los siguientes campos:
   - **Nombre del repositorio:** Específico y claro (ejemplo: `rpa-finanzas`).
   - **Descripción:** Breve resumen del propósito del repositorio.
   - **Visibilidad:** Pública o privada según necesidad.
   - **Inicializa este repositorio con un README:** (Opcional)
4. Haz clic en **"Create repository"**.

---

## 🔄 Clonación de un Repositorio Existente

Para trabajar con un repositorio existente, clónalo en tu máquina local:

```bash
git clone https://github.com/usuario/repositorio.git
```

> **Nota:** Cambia `usuario` y `repositorio` por el nombre correcto del usuario y del repositorio.

---

## ⚙️ Configuración Inicial

1. Configura tu nombre y correo en Git:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
```

2. Verifica la configuración:

```bash
git config --list
```

3. (Opcional) Configura el repositorio remoto si no se clonó directamente:

```bash
git remote add origin https://github.com/usuario/repositorio.git
```

---

## 🌿 Flujo de Trabajo con Ramas

1. **Crea una nueva rama** para trabajar en una funcionalidad o corrección específica:

```bash
git checkout -b nombre-de-la-rama
```

> Ejemplos de nombres de ramas:
> - `feature/nueva-funcionalidad`
> - `fix/correccion-error`
> - `hotfix/parche-urgente`

2. Cambia de rama cuando sea necesario:

```bash
git checkout nombre-de-la-rama
```

3. Actualiza tu rama con los últimos cambios de la rama principal:

```bash
git checkout main
git pull origin main
git checkout nombre-de-la-rama
git merge main
```

---

## ✅ Buenas Prácticas de Commit

1. **Comandos básicos de commit:**

```bash
git add .    # Agrega todos los cambios
git commit -m "TIPO: Descripción clara del cambio"
```

2. **Tipos de commits sugeridos:**
- `FEATURE:` Nueva funcionalidad (`git commit -m "FEATURE: Agregar validación de email"`)
- `FIX:` Corrección de errores (`git commit -m "FIX: Soluciona error en el login"`)
- `REFACTOR:` Mejora del código sin cambiar la funcionalidad (`git commit -m "REFACTOR: Simplificar lógica de validación"`)
- `DOCS:` Cambios en la documentación (`git commit -m "DOCS: Actualizar guía de instalación"`)

3. **Recomendaciones:**
- Escribe mensajes concisos pero descriptivos.
- Usa el tiempo presente: _"Agrega"_ en lugar de _"Agregado"._

---

## 🚀 Subir Cambios y Pull Requests

1. **Sube tus cambios a tu rama remota:**
```bash
git push origin nombre-de-la-rama
```

2. **Crea una Pull Request (PR):**
   - Ve a la página del repositorio en GitHub.
   - Haz clic en **"Compare & pull request"**.
   - Agrega una descripción clara del cambio.
   - Asigna revisores si es necesario.
   - Haz clic en **"Create pull request"**.

3. **Fusionar la rama:**  
   El responsable del proyecto (o el revisor) debe revisar y aprobar los cambios antes de fusionarlos con la rama principal (`main` o `master`).

---

## 👥 Recomendaciones para Trabajo en Equipo

- Cada miembro debe trabajar en su propia rama.
- Realiza **pull** frecuentes de la rama principal para mantener tu código actualizado.
- Realiza revisiones de código antes de fusionar cambios.
- Utiliza **issues** o **proyectos** en GitHub para gestionar tareas y bugs.

---

## 🔒 Buenas Prácticas de Seguridad

- No subas archivos sensibles como:
  - Entornos virtuales (ejemplo: `.venv/` o `env/`)
  - Archivos de configuración con contraseñas
  - Claves API o tokens de autenticación

- Utiliza un archivo `.gitignore` para excluir archivos que no deben ser subidos:

```
# Entornos virtuales
venv/
env/

# Archivos sensibles
*.env
config/secrets.json

# Archivos del sistema
.DS_Store
Thumbs.db
```

- Usa variables de entorno para manejar contraseñas y claves.

---

## ⚠️ Errores Comunes y Cómo Evitarlos

1. **Olvidé agregar archivos al commit:**

```bash
git add archivo.py
git commit --amend
```

2. **Subí un archivo sensible por error:**

```bash
git rm --cached archivo_sensible.ext
git commit -m "REMOVE: Eliminar archivo sensible"
git push origin main
```

3. **Conflictos al fusionar ramas:**

- Git mostrará los conflictos en los archivos involucrados.
- Resuelve los conflictos manualmente.
- Confirma los cambios:

```bash
git add archivo_en_conflicto.py
git commit -m "FIX: Resolver conflictos de fusión"
git push origin nombre-de-la-rama
```

---

## 🎯 Conclusión

Seguir estas buenas prácticas en el uso de GitHub permitirá:
- Evitar conflictos de código.
- Mantener un historial limpio y claro.
- Facilitar la colaboración entre desarrolladores.
- Proteger la seguridad del proyecto.

Trabajemos en equipo y aprovechemos al máximo las capacidades de GitHub para garantizar un flujo de trabajo eficiente y profesional.
