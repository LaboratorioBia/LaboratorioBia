# Guía de Desarrollo y Estándares de Microservicios en Prebel

## **Introducción**
Esta guía establece los estándares de desarrollo, estructura de repositorios y buenas prácticas dentro de nuestra organización Prebel para la creación de microservicios. Su objetivo es garantizar un desarrollo eficiente, organizado y escalable en todos nuestros microservicios.

---

## **1. Estructura de Repositorios**
Para mantener una organización eficiente en GitHub, se establecen las siguientes convenciones:

### **1.1 Organización General**
```
📦 Prebel (Organización en GitHub)
│── 📂 Aplicacion1
│   ├── 🗂 SERVICE_Usuarios
│   ├── 🗂 SERVICE_Proveedores
│   ├── 🗂 SERVICE_Pedidos
│   ├── 🗂 SERVICE_Facturacion
│   ├── 🗂 FRONT_Aplicacion1
│── 📂 Aplicacion2
│   ├── 🗂 SERVICE_Proveedores
│   ├── 🗂 SERVICE_OrdenesCompra
│   ├── 🗂 SERVICE_GestionAlmacenes
│   ├── 🗂 FRONT_Aplicacion2
│── 📂 Aplicacion3
│   ├── 🗂 SERVICE_Contabilidad
│   ├── 🗂 SERVICE_Costos
│   ├── 🗂 SERVICE_Reportes
│   ├── 🗂 FRONT_Aplicacion3
│── 📂 Servicios_Comunes
│   ├── 🗂 SERVICE_Proveedores
│   ├── 🗂 SERVICE_Notificaciones
│   ├── 🗂 AuthService
│   ├── 🗂 BIA-Utils
│── 📂 Infraestructura
│   ├── 🗂 Kubernetes_Configs
│   ├── 🗂 CI_CD_Pipelines
│   ├── 🗂 Terraform_Infraestructura
```
📌 **Reglas:**
- Cada microservicio y frontend tiene su propio repositorio.
- Servicios compartidos están en `Servicios_Comunes`.
- `Infraestructura` centraliza configuración y despliegue.

---

## **2. Desarrollo de Microservicios**
### **2.1 Estructura de un Microservicio**
Cada microservicio sigue una estructura estandarizada:
```
📂 SERVICE_Usuarios
│── 📂 src/
│   ├── 📂 models/
│   ├── 📂 services/
│   ├── 📂 routes/
│── 📂 tests/
│── 📂 docs/
│── 📄 Dockerfile
│── 📄 README.md
```
📌 **Reglas:**
- `models/`: Definiciones de la base de datos.
- `services/`: Lógica de negocio.
- `routes/`: Definición de endpoints.
- `tests/`: Pruebas unitarias y de integración.
- `docs/`: Documentación en OpenAPI.

#### **Ejemplo de estructura con Django Rest Framework**
```
📂 SERVICE_Usuarios
│── 📂 service_usuarios/
│   ├── 📂 apps/
│   │   ├── 📂 users/
│   │   │   ├── models.py
│   │   │   ├── serializers.py
│   │   │   ├── views.py
│   │   │   ├── urls.py
│   ├── 📂 config/
│   │   ├── settings.py
│   │   ├── urls.py
│   ├── manage.py
│── 📂 tests/
│── 📂 docs/
│── 📄 Dockerfile
│── 📄 README.md
```

---

## **3. Comunicación entre Servicios**
### **3.1 Métodos de Comunicación**
📌 **Opciones disponibles:**
- **API Gateway** (Kong o Nginx) → Redirige peticiones a los servicios adecuados.
- **Mensajería Asíncrona** (Kafka o RabbitMQ) → Para eventos entre aplicaciones.
- **Base de Datos Compartida** → Solo en casos justificados.

Cuando un microservicio necesita datos de otro:
1. **Llamadas Directas API** → Un servicio consulta otro mediante API REST.
2. **Eventos Asíncronos** → Kafka permite la comunicación sin acoplamiento.
3. **Base de Datos Compartida** → Solo en escenarios donde se necesite consistencia estricta.

📌 **Más información**:
- [API Gateway con Kong](https://docs.konghq.com/)
- [Mensajería con Kafka](https://kafka.apache.org/)

---

## **4. Documentación con Swagger en DjangoRF**
Para documentar endpoints de microservicios con Django Rest Framework, se recomienda usar `drf-yasg`.

📌 **Ejemplo de configuración**
```python
from rest_framework import routers
from django.urls import path, include
from drf_yasg.views import get_schema_view
from drf_yasg import openapi

schema_view = get_schema_view(
    openapi.Info(
        title="API Usuarios",
        default_version='v1',
        description="Documentación de API Usuarios",
    ),
)

urlpatterns = [
    path('swagger/', schema_view.with_ui('swagger', cache_timeout=0), name='schema-swagger-ui'),
]
```

---

## **5. Despliegue y Flujo de Desarrollo** *(Habilidades Avanzadas y Futuras)*
En esta sección se abordarán estrategias futuras como:
- Despliegue con Kubernetes.
- Automatización con Terraform.
- CI/CD con GitHub Actions.

---

## **Conclusión**
Este documento define la base para el desarrollo de microservicios dentro de Prebel. Para cualquier duda o mejora, por favor, consultar con el equipo de arquitectura.

