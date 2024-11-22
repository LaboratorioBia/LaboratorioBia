# Guía de Desarrollo para Laboratorio BIA

## Descripción General

Este repositorio sirve como un centro de referencia para todos los estándares de desarrollo y codificación dentro de la empresa. Proporciona pautas claras para las convenciones de nombres, la estructura de los repositorios, componentes reutilizables, y la documentación para cada proyecto o servicio.

## Estructura de Repositorios y Convenciones de Nombres

### Convenciones Generales de Nombres

Para estandarizar el nombramiento de los proyectos en los diferentes repositorios, sigue la siguiente estructura:

- **Microservicios:** `SERVICE_nombre_servicio`
- **Automatizaciones RPA:** `RPA_nombre_rpa`
- **Dashboards:** `DASH_nombre_dashboard`
- **Aplicaciones Frontend:** `FRONT_nombre_front`
- **Aplicaciones Pequeñas** `APP_nombre_app`
- **Por Area** `area/tipo_desarrollo`

Ejemplos:
- `APP_ServicioClientes`
- `RPA_ProcesamientoPedidos`
- `DASH_VentasMensuales`
- `FRONT_PortalWeb`

### Carpetas en los Repositorios

Cada servicio o módulo debe residir en su propio repositorio para mantener la modularidad y facilitar el control de versiones. Para servicios más pequeños o de propósito general, se puede utilizar un repositorio compartido.

- **Un repositorio por microservicio**: Cada microservicio crítico o independiente debe tener su propio repositorio.
- **Repositorio compartido para servicios pequeños**: Los servicios pequeños y genéricos se pueden agrupar en un "monorepo" para utilidades generales.

### Ejemplos de Repositorios
- `Logistica/Tableros`: Contiene todos los dashboards relacionados con las operaciones logísticas.
- `Logistica/AutomatizacionesRPA`: Repositorio para todas las automatizaciones RPA dentro del área de logística.
- `Negociaciones/AutomatizacionesRPA`: Repositorio para las automatizaciones RPA dentro del área de negociaciones.

---

## Componentes Reutilizables

### CoreConnector (`CoreConnector`)

`CoreConnector` es una clase reutilizable que se conecta a las CDS de SAP para consultar información. Está diseñada para ser compartida en múltiples proyectos. Esta clase se almacena en el repositorio **CoreConnector** y puede integrarse en cualquier servicio que necesite acceso a datos de SAP.

### Cómo Usar en Proyectos

1. **Importar la Clase:**
   from CoreConnector import CDSConnector

2. **Documentación**: Consulta el repositorio `CoreConnector/documentation` para obtener la documentación detallada sobre cómo integrar y usar esta clase.

### Control de Versiones

Todos los componentes reutilizables, incluida la clase `CoreConnector`, seguirán el control de versiones semántico (`MAYOR.MENOR.PARCHE`). Asegúrate de que tu proyecto especifique la versión requerida para evitar problemas de compatibilidad.

---

## Flujo de Trabajo de Desarrollo

### Directrices de Repositorios

- **Microservicios**: Un repositorio por servicio para asegurar despliegue y escalabilidad independientes.
- **Servicios más pequeños**: Pueden agruparse en un repositorio compartido bajo `GeneralServices/` o similar.

### Integración Continua

Utilizamos pipelines de CI/CD para automatizar el proceso de pruebas, construcción y despliegue de microservicios y componentes reutilizables. Cada repositorio está vinculado a nuestra pipeline de CI/CD, asegurando que cada cambio sea probado antes de ser implementado en producción.

---

## Para Nuevos Desarrolladores

¡Bienvenido al equipo! Aquí tienes una guía rápida para empezar:

1. **Configura Tu Entorno**: Sigue las instrucciones de configuración en el archivo `onboarding.md`.
2. **Comprende las Convenciones de Nombres**: Todos los repositorios y componentes siguen estándares de nombramiento específicos (consulta la sección de convenciones de nombres).
3. **Verifica los Componentes Reutilizables**: Antes de escribir código nuevo, verifica si ya existe algún módulo o clase que puedas reutilizar desde el repositorio `CoreConnector`.
4. **Control de Versiones**: Asegúrate de usar ramas en GitHub y seguir los estándares de versionado para cada proyecto.

Para cualquier duda o aclaración, por favor contacta a tu líder de equipo o revisa la carpeta `docs` para obtener documentación más detallada.

---

### Mejoras Futuras

- **Modularización de Servicios**: Estamos mejorando constantemente nuestra arquitectura y es posible que introduzcamos nuevos módulos para mejorar la escalabilidad y el rendimiento.
- **Documentación Centralizada**: Estamos construyendo un sitio de documentación completo para desarrolladores, que será enlazado aquí una vez esté disponible.




