
# Estándar para RPAs - Guía Completa

---

## Aclaración General

> **Importante:**  
> Este estándar se propone como un ejemplo de estructura organizacional para proyectos de RPAs, integrando buenas prácticas de desarrollo y una arquitectura sólida que permita implementar los principios **SOLID** de manera clara y entendible para cualquier desarrollador.
> 
> Los **RPAs automatizados**, que se ejecutarán en un servidor o entorno similar, **deben cumplir con la estructura** aquí establecida, ya que estarán organizados por área y se reutilizarán componentes como *services*, *adapters* y otros módulos según sea necesario.
> 
> Por otro lado, para los **RPAs ejecutables por el usuario** (o pequeñas aplicaciones de escritorio), se podrá adaptar la estructura incorporando, por ejemplo, una carpeta adicional para la interfaz gráfica (GUI) que permita la interacción o parametrización del proceso. En estos casos se podrán emplear frameworks como Tkinter, Flask, Flet, entre otros, siempre cumpliendo con las buenas prácticas de desarrollo.

---

## Introducción

Este documento ofrece una guía detallada para la implementación y organización de **RPAs** (Robotic Process Automation) en dos escenarios:
- **RPAs Automatizados:** Diseñados para ejecutarse de forma automática en servidores, organizados por áreas funcionales y con reutilización de código en módulos comunes.
- **RPAs Ejecutables (Aplicaciones de Escritorio):** Pequeñas aplicaciones empaquetadas (por ejemplo, como .exe) que permiten la interacción del usuario mediante interfaces gráficas.

La idea es disponer de una estructura modular y escalable que garantice la mantenibilidad y el cumplimiento de los principios de diseño robusto.

---

## Principios de la Arquitectura

La arquitectura propuesta tiene como objetivos:
- **Separación de Responsabilidades:** Cada módulo (adapters, services, tasks, etc.) cumple una función específica.
- **Reutilización de Código:** Facilitar la reutilización de componentes comunes en distintos módulos o áreas.
- **Adaptabilidad:** Permitir ajustes en la estructura según el tipo de RPA (automatizado vs. ejecutable), sin perder de vista las buenas prácticas y principios **SOLID**.

---

## Estructura del Proyecto

### 1. RPAs Automatizados (Servidor)

Estos RPAs están diseñados para ejecutarse de forma automática en un entorno servidor. Se recomienda organizarlos por área funcional, donde cada área incorpora sus propios módulos de *adapters*, *services*, *tasks*, etc. La estructura sugerida es la siguiente:

### **Estructura del proyecto por repositorio en GitHub**
```plaintext
/RPA_template
├── /RPA
│   ├── main.py                  # Punto de entrada principal / Main entry point
│   ├── /tasks                   # Tareas específicas / Specific tasks
│   │   ├── __init__.py
│   │   ├── task_1.py
│   │   └── task_2.py
│   ├── /workflows               # Flujos de trabajo organizados / Organized workflows
│   │   ├── __init__.py
│   │   ├── workflow_1.py
│   │   └── workflow_2.py
│   ├── /config                  # Configuración compartida / Shared configuration
│   │   ├── settings.py
│   │   ├── logger.py
│   │   └── constants.py
│   ├── /adapters                # Adaptadores externos / External adapters
│   │   ├── sap_adapter.py
│   │   └── db_adapter.py
│   ├── /services                # Servicios adicionales como envío de notificaciones
│   │   ├── email.py
│   │   └── telegram.py
│   ├── /utils                   # Funciones reutilizables / Reusable utilities
│   │   └── file_operations.py
├── /airflow                     # Configuración de Airflow / Airflow configuration
│   ├── dags/
│   │   ├── rpa_dag_1.py         # DAG para workflow_1 / DAG for workflow_1
│   ├── plugins/                 # Plugins personalizados / Custom plugins
├── tests/                       # Pruebas / Tests
├── Dockerfile                   # Contenedor para despliegue / Container for deployment
├── requirements.txt             # Dependencias / Dependencies
└── README.md
```

> **Nota:**  
> Esta estructura es un punto de partida. Cada proyecto debe evaluar sus necesidades particulares y, si es necesario, adaptar o extender la organización de carpetas manteniendo siempre la claridad y modularidad.

---

### 2. RPAs Ejecutables (Aplicaciones de Escritorio)

En algunos casos, los RPAs se empaquetan como aplicaciones ejecutables (por ejemplo, .exe) para que el usuario final pueda interactuar o parametrizar el proceso. En estos escenarios se recomienda agregar una carpeta dedicada a la interfaz gráfica. La estructura sugerida es la siguiente:

```
📂 my_rpa_project/
├── 📂 adapters/       # Lógica de integración y transformación de datos
├── 📂 services/       # Servicios reutilizables (envío de correos, notificaciones, etc.)
├── 📂 tasks/          # Scripts y tareas automatizadas
├── 📂 config/         # Configuraciones generales
├── 📂 logs/           # Registros de ejecución
├── 📂 tests/          # Pruebas unitarias
├── 📂 GUI/            # Componentes de la interfaz gráfica
│   ├── components/    # Elementos de UI reutilizables (botones, formularios, etc.)
│   ├── views/         # Ventanas o vistas principales
│   └── controllers/   # Lógica de interacción entre la GUI y el RPA
├── 📄 main.py         # Punto de entrada que integra la lógica del RPA con la interfaz
├── 📄 README.md       # Documentación del proyecto
```

> **Frameworks y Consideraciones:**  
> Para la implementación de la interfaz gráfica se pueden utilizar frameworks como:
> - **Tkinter:** Biblioteca estándar de Python para GUIs.
> - **Flask/Flet:** Para interfaces web ligeras que se empaqueten como aplicaciones de escritorio.
> - **Otros:** Evaluar según los requerimientos específicos del proyecto.
> 
> La clave es asegurar que, tanto la parte automatizada como la interactiva, se desarrollen bajo buenas prácticas, garantizando una arquitectura modular y escalable.

---

## Conclusión

Este estándar ofrece un marco de referencia flexible para el desarrollo de RPAs, diferenciando claramente entre:
- **RPAs Automatizados:** Que se ejecutan en un entorno servidor, organizados por área funcional y con reutilización de módulos comunes.
- **RPAs Ejecutables (Aplicaciones de Escritorio):** Que incorporan una interfaz gráfica para la interacción del usuario.

Se recomienda evaluar cada caso de uso y ajustar la estructura de carpetas y módulos según la complejidad y los requerimientos específicos del proyecto, siempre manteniendo un enfoque en la mantenibilidad, la claridad y la aplicación de principios de diseño robustos.
