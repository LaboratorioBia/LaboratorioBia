### **Introducción**
Bienvenido al repositorio de **LaboratorioBia**. Este proyecto es una plantilla para construir, organizar y desplegar RPAs utilizando **Airflow** como herramienta de orquestación y **Docker** para asegurar portabilidad y escalabilidad.

Este repositorio está diseñado tanto para nuevos desarrolladores como para nuestro equipo interno. Proporciona una base estandarizada para construir soluciones automatizadas eficientes y mantener un flujo de trabajo uniforme.

---

### **Arquitectura**
La arquitectura sigue un diseño modular para garantizar la claridad, el mantenimiento y la escalabilidad. Los componentes principales son:

1. **Airflow**: Orquesta los flujos de trabajo (DAGs) para ejecutar y monitorear las tareas del RPA.
2. **Tareas (Tasks)**: Funciones específicas que realizan acciones individuales.
3. **Workflows**: Combinan tareas en flujos de trabajo organizados.
4. **Adaptadores (Adapters)**: Interactúan con sistemas externos como SAP, APIs o bases de datos.
5. **Docker**: Facilita la portabilidad y el despliegue en diferentes entornos.

---

### **Estructura del Proyecto**
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

---

---

### **Instalación**
1. Clona el repositorio:
   ```bash
   git clone https://github.com/LaboratorioBia/CoreStandardTemplates.git
   cd RPA_template
   ```

2. Configura el entorno:
   - Copiar folder RPA y llevarlo a un nuevo directorio
   - Instalar dependencias del proyecto
   ```

---

### **Ejemplo de DAG**
Este es un ejemplo de cómo configurar un DAG para ejecutar un workflow:

```python
from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime
from RPA.workflows.workflow_1 import Workflow1

with DAG(
    dag_id='rpa_workflow_1',
    schedule_interval='@daily',
    start_date=datetime(2023, 1, 1),
    catchup=False,
) as dag:

    task_1 = PythonOperator(
        task_id='task_1',
        python_callable=Workflow1().execute_task_1,
    )

    task_2 = PythonOperator(
        task_id='task_2',
        python_callable=Workflow1().execute_task_2,
    )

    task_1 >> task_2
```

---

### **Autores**
Este proyecto fue desarrollado por el equipo de **LaboratorioBia**.

---
