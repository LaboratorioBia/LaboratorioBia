# Development Guide for BIA Laboratory

## Overview

This repository serves as a central hub for all the coding and development standards within the company. It provides clear guidelines for naming conventions, repository structure, reusable components, and the documentation for each project or service.

## Repository Structure and Naming Conventions

### General Naming Conventions

To standardize project naming across different repositories, follow the structure below:

- **Microservices:** `APP_name_service`
- **RPA Automations:** `RPA_name_rpa`
- **Dashboards:** `DASH_name_dashboard`
- **Frontend Applications:** `FRONT_name_front`

Example:
- `APP_CustomerService`
- `RPA_OrderProcessing`
- `DASH_SalesOverview`
- `FRONT_WebPortal`

### Repository Folders

Each service or module should reside in its own repository to maintain modularity and facilitate version control. For smaller or general-purpose services, a shared repository may be used.

- **One repository per microservice**: Each critical or standalone microservice should have its own repository.
- **Shared repository for smaller services**: Small, generic services can be grouped together in a "monorepo" for general utilities.

### Example Repositories
- `Logistics/Dashboards`: Contains all dashboards related to logistics operations.
- `Logistics/AutomationsRPA`: Repository for all RPA automations within the logistics area.
- `Negotiations/AutomationsRPA`: Repository for RPA automations within the negotiations area.

---

## Reusable Components

### Core Data Central (`CoreDataCentral`)

`CoreDataCentral` is a reusable class that connects to SAP's CDS to retrieve information. It is designed to be shared across multiple projects. This class is stored in the **SharedModules** repository and can be integrated into any service that requires access to SAP data.

### How to Use in Projects

1. **Import the Class:**
   - For Python: Add the dependency to your `requirements.txt` or install via pip:
     ```bash
     pip install coredatacentral
     ```
   - For Node.js: Install the package using npm:
     ```bash
     npm install coredatacentral
     ```

2. **Documentation**: Refer to the `SharedModules/CoreDataCentral` repository for detailed documentation on how to integrate and use this class.

### Versioning

All reusable components, including `CoreDataCentral`, will follow semantic versioning (`MAJOR.MINOR.PATCH`). Ensure that your project specifies the required version to avoid compatibility issues.

---

## Development Workflow

### Repository Guidelines

- **Microservices**: One repository per service to ensure independent deployment and scaling.
- **Smaller Services**: These can be grouped in a shared repository under `GeneralServices/` or similar.
  
### Continuous Integration

We use CI/CD pipelines to automate the process of testing, building, and deploying microservices and reusable components. Each repository is linked to our CI/CD pipeline, ensuring every change is tested before it reaches production.

---

## For New Developers

Welcome to the team! Below is a quickstart guide to help you get started:

1. **Set Up Your Environment**: Follow the setup instructions in the `onboarding.md` file.
2. **Understand the Naming Conventions**: All repositories and components follow specific naming standards (see the section on naming conventions).
3. **Check Reusable Components**: Before writing new code, check if there's an existing module or class you can reuse from the `SharedModules` repository.
4. **Version Control**: Ensure that you use GitHub branches and follow the versioning standards for each project.

For any questions or clarifications, please reach out to your team lead or check the `docs` folder for more detailed documentation.

---

### Future Improvements

- **Modularization of Services**: We are constantly improving our microservice architecture and may introduce new modules for better scalability and performance.
- **Centralized Documentation**: A full developer documentation site is under construction, and will be linked here once available.

---


## VERSION ESPAÑOL

¡Claro! Aquí tienes una versión en español del README para tu repositorio en GitHub:

---

# Guía de Desarrollo para Laboratorio BIA

## Descripción General

Este repositorio sirve como un centro de referencia para todos los estándares de desarrollo y codificación dentro de la empresa. Proporciona pautas claras para las convenciones de nombres, la estructura de los repositorios, componentes reutilizables, y la documentación para cada proyecto o servicio.

## Estructura de Repositorios y Convenciones de Nombres

### Convenciones Generales de Nombres

Para estandarizar el nombramiento de los proyectos en los diferentes repositorios, sigue la siguiente estructura:

- **Microservicios:** `APP_nombre_servicio`
- **Automatizaciones RPA:** `RPA_nombre_rpa`
- **Dashboards:** `DASH_nombre_dashboard`
- **Aplicaciones Frontend:** `FRONT_nombre_front`

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

### Core Data Central (`CoreDataCentral`)

`CoreDataCentral` es una clase reutilizable que se conecta a los CDS de SAP para recuperar información. Está diseñada para ser compartida en múltiples proyectos. Esta clase se almacena en el repositorio **SharedModules** y puede integrarse en cualquier servicio que necesite acceso a datos de SAP.

### Cómo Usar en Proyectos

1. **Importar la Clase:**
   - Para Python: Añade la dependencia en tu archivo `requirements.txt` o instálalo usando pip:
     ```bash
     pip install coredatacentral
     ```
   - Para Node.js: Instala el paquete usando npm:
     ```bash
     npm install coredatacentral
     ```

2. **Documentación**: Consulta el repositorio `SharedModules/CoreDataCentral` para obtener la documentación detallada sobre cómo integrar y usar esta clase.

### Control de Versiones

Todos los componentes reutilizables, incluida la clase `CoreDataCentral`, seguirán el control de versiones semántico (`MAYOR.MENOR.PARCHE`). Asegúrate de que tu proyecto especifique la versión requerida para evitar problemas de compatibilidad.

---

## Flujo de Trabajo de Desarrollo

### Directrices de Repositorios

- **Microservicios**: Un repositorio por servicio para asegurar despliegue y escalabilidad independientes.
- **Servicios más pequeños**: Pueden agruparse en un repositorio compartido bajo `ServiciosGenerales/` o similar.

### Integración Continua

Utilizamos pipelines de CI/CD para automatizar el proceso de pruebas, construcción y despliegue de microservicios y componentes reutilizables. Cada repositorio está vinculado a nuestra pipeline de CI/CD, asegurando que cada cambio sea probado antes de ser implementado en producción.

---

## Para Nuevos Desarrolladores

¡Bienvenido al equipo! Aquí tienes una guía rápida para empezar:

1. **Configura Tu Entorno**: Sigue las instrucciones de configuración en el archivo `onboarding.md`.
2. **Comprende las Convenciones de Nombres**: Todos los repositorios y componentes siguen estándares de nombramiento específicos (consulta la sección de convenciones de nombres).
3. **Verifica los Componentes Reutilizables**: Antes de escribir código nuevo, verifica si ya existe algún módulo o clase que puedas reutilizar desde el repositorio `SharedModules`.
4. **Control de Versiones**: Asegúrate de usar ramas en GitHub y seguir los estándares de versionado para cada proyecto.

Para cualquier duda o aclaración, por favor contacta a tu líder de equipo o revisa la carpeta `docs` para obtener documentación más detallada.

---

### Mejoras Futuras

- **Modularización de Servicios**: Estamos mejorando constantemente nuestra arquitectura de microservicios y es posible que introduzcamos nuevos módulos para mejorar la escalabilidad y el rendimiento.
- **Documentación Centralizada**: Estamos construyendo un sitio de documentación completo para desarrolladores, que será enlazado aquí una vez esté disponible.




