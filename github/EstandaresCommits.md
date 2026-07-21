# Estándares para Commits

## Objetivo

Mantener un historial de cambios limpio, entendible y fácil de auditar, permitiendo identificar rápidamente qué se modificó, por qué y quién realizó el cambio.

Todos los commits deben seguir el estándar **Conventional Commits**.

---

# Formato

```
<tipo>(<alcance>): <descripción>
```

### Ejemplos

```
feat(auth): agregar autenticación con JWT

fix(users): corregir validación de correo electrónico

docs(readme): actualizar guía de instalación

refactor(api): simplificar lógica de creación de perfiles

test(profile): agregar pruebas unitarias del servicio

style(button): corregir formato del componente

chore(ci): actualizar versión de Node
```

---

# Tipos Permitidos

| Tipo | Uso |
|-------|-----|
| feat | Nueva funcionalidad |
| fix | Corrección de errores |
| docs | Cambios en documentación |
| style | Cambios de formato (sin afectar lógica) |
| refactor | Refactorización sin cambiar comportamiento |
| perf | Mejoras de rendimiento |
| test | Agregar o modificar pruebas |
| build | Cambios relacionados con compilación o dependencias |
| ci | Cambios en CI/CD |
| chore | Tareas de mantenimiento |
| revert | Revertir un commit |

---

# Alcance (Scope)

El alcance debe indicar el módulo afectado.

Ejemplos:

```
feat(auth):
fix(profile):
docs(api):
refactor(frontend):
test(users):
ci(github):
```

Scopes sugeridos:

- auth
- api
- backend
- frontend
- ui
- profile
- users
- workflow
- database
- security
- docs
- github
- infrastructure

---

# Descripción

La descripción debe:

- escribirse en minúsculas
- comenzar con un verbo en infinitivo
- ser clara y corta
- no terminar en punto

Correcto

```
feat(users): agregar búsqueda por nombre

fix(login): corregir expiración del token

refactor(api): separar servicio de autenticación
```

Incorrecto

```
feat: Cosas nuevas

Update

Cambios

Arreglos

Se hicieron modificaciones
```

---

# Commits Atómicos

Cada commit debe representar **un único cambio lógico**.

Correcto:

```
feat(profile): agregar carga de fotografía

test(profile): agregar pruebas del servicio

docs(profile): documentar endpoint
```

Incorrecto:

```
feat(profile): agregar foto, actualizar documentación y corregir login
```

---

# Frecuencia

Se recomienda realizar commits pequeños y frecuentes.

Evitar:

- Commits gigantes.
- Cambios de múltiples funcionalidades en un solo commit.
- Commits con cientos de archivos sin relación.

---

# Mensajes Prohibidos

Nunca utilizar mensajes como:

```
Update

Cambios

Fix

Arreglos

asd

.

Prueba

test

último

commit

final
```

---

# Breaking Changes

Cuando un cambio rompe compatibilidad:

```
feat(api)!: cambiar estructura de respuesta

BREAKING CHANGE: el endpoint /users devuelve un nuevo formato.
```

---

# Referenciar Issues

Cuando aplique:

```
fix(auth): corregir expiración del token (#142)

feat(profile): agregar exportación PDF (#87)
```

---

# Antes de realizar un Commit

Verificar que:

- El proyecto compila correctamente.
- No existan errores de lint.
- Las pruebas pasen correctamente.
- No existan archivos temporales.
- No se incluyan credenciales.
- No existan secretos o tokens.
- Solo se incluyan archivos relacionados con el cambio.

---

# Antes de crear un Pull Request

Confirmar que:

- Todos los commits siguen este estándar.
- La rama está actualizada con `main`.
- Los conflictos fueron resueltos.
- El código fue probado.
- La documentación fue actualizada si aplica.

---

# Ejemplos

## Nueva funcionalidad

```
feat(profile): agregar exportación a Word
```

## Corrección

```
fix(users): validar documento obligatorio
```

## Refactor

```
refactor(api): dividir servicio de perfiles
```

## Documentación

```
docs(readme): actualizar guía de despliegue
```

## CI/CD

```
ci(github): agregar validación de lint
```

## Base de datos

```
feat(database): crear tabla de auditoría
```

---

# Buenas Prácticas

✅ Un commit = un cambio lógico.

✅ Commits pequeños.

✅ Mensajes descriptivos.

✅ Utilizar siempre Conventional Commits.

✅ Evitar commits innecesarios.

✅ Mantener el historial limpio y fácil de leer.

---

# Ejemplo de Historial

```
feat(auth): agregar autenticación OAuth2

feat(profile): implementar editor de perfiles

fix(profile): corregir validación de experiencia

refactor(profile): desacoplar servicio de exportación

test(profile): agregar pruebas de integración

docs(api): documentar endpoint de perfiles

ci(github): ejecutar pruebas en Pull Requests
```
