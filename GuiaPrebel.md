# Guía General de Desarrollo en Prebel

## **Introducción**

Prebel desarrolla y mantiene una variedad de soluciones tecnológicas, incluyendo:

- **Microservicios** (SERVICE\_nombre)
- Aplicaciones Web (APP\_nombre)
- **Frontends** (FRONT\_nombre)
- **Automatizaciones RPA** (RPA\_nombre)
- **Aplicaciones de Escritorio** (TOOL\_nombre)

Cada uno de estos componentes sigue un estándar interno de desarrollo para garantizar escalabilidad, mantenibilidad y eficiencia. Esta guía proporciona una visión general del ecosistema de desarrollo y referencias a documentación detallada para cada tipo de proyecto.

---

## **1. Estructura de Repositorios**

Dependiendo del tipo de desarrollo, los repositorios en GitHub se organizan de la siguiente manera:

### **1.1 Microservicios**

Cada microservicio tiene su propio repositorio y comparte un repositorio con su frontend correspondiente.

```
📦 Prebel (Organización en GitHub)
│── 📂 Aplicacion1
│   ├── 🗂 SERVICE_Usuarios
│   ├── 🗂 SERVICE_Pedidos
│   ├── 🗂 SERVICE_Facturacion
│   ├── 🗂 FRONT_Aplicacion1
```

### **1.2 Aplicaciones Web**

Cada aplicación tiene un solo repositorio, que contiene tanto el backend como el frontend, ya que se despliegan juntos.

```
📂 Aplicaciones
│── 🗂 APP_GestionClientes
│── 🗂 APP_RegistroInventario
```

### **1.3 Automatizaciones RPA**

Las automatizaciones RPA se agrupan en repositorios por área de negocio, facilitando su despliegue con Apache Airflow y Docker.

```
📂 Automatizaciones RPA
│── 🗂 RPA_Logistica
│── 🗂 RPA_Finanzas
│── 🗂 RPA_Produccion
```

### **1.4 Aplicaciones de Escritorio**

Las herramientas de escritorio (pequeñas aplicaciones con interfaz gráfica en .exe) se almacenan en un solo repositorio organizado por áreas.

```
📂 Herramientas de Escritorio
│── 🗂 TOOL_Logistica
│   ├── ValidadorStock/
│   ├── ReportePedidos/
│── 🗂 TOOL_Finanzas
│   ├── ConciliacionBancaria/
│   ├── ConversorMonedas/
```

📌 **Reglas:**

- **Microservicios** → Un repositorio por microservicio y su frontend.
- **Aplicaciones Monolíticas** → Backend y frontend en el mismo repositorio.
- **Automatizaciones RPA** → Repositorios por área.
- **Aplicaciones de Escritorio** → Un solo repositorio con subcarpetas por área.

---

## **2. Estándares por Tipo de Proyecto**

Cada tipo de proyecto sigue una documentación específica con buenas prácticas y guías detalladas. Consulta cada una según sea necesario:

- **Microservicios:** [Guía de Desarrollo de Microservicios](./EstandarMicroservicios.md)
- **Aplicaciones Web:** (Pendiente de documentar)
- **Frontends:** (Pendiente de documentar)
- **Automatizaciones RPA:** (Pendiente de documentar)
- **Aplicaciones de Escritorio:** (Pendiente de documentar)

Cada documento contiene detalles sobre:

- Estructura de archivos y carpetas
- Convenciones de nomenclatura
- Buenas prácticas de desarrollo
- Flujo de CI/CD y despliegue

---

## **3. Buenas Prácticas y Convenciones**

Para garantizar eficiencia y legibilidad en el código, se siguen estándares establecidos en un documento separado. Consulta las buenas prácticas y convenciones aquí:

�[� ](https://kafka.apache.org/)[Guía de Estándares](https://kafka.apache.org/)[ de Código y Buenas Prácticas](./guia_estandares_codigo.md)

---

## **Conclusión**

Esta guía sirve como introducción al ecosistema de desarrollo en Prebel. Se recomienda a todos los desarrolladores seguir las normas establecidas y consultar la documentación específica según el tipo de proyecto que estén implementando. Para cualquier duda, contactar con el equipo de arquitectura.

