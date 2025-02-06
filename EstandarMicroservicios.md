# Guía de Desarrollo y Estándares de Microservicios en Prebel

## **Introducción**
Esta guía establece los estándares de desarrollo, estructura de repositorios y buenas prácticas dentro de nuestra organización Prebel para la creación de microservicios. Su objetivo es garantizar un desarrollo eficiente, organizado y escalable en todos nuestros microservicios.

---

## ** Estructura de Repositorios**
Para mantener una organización eficiente en GitHub, se establecen las siguientes convenciones:

### ** Organización General**
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

## ** Desarrollo de Microservicios**

#### **Ejemplo de estructura con Django Rest Framework**
```
📂 SERVICE_Nombre
│── 📂 service_nombre/
│   ├── 📂 apps/
│   │   ├── 📂 modulo_x/
│   │   │   ├── models.py  (Definición de modelos de BD)
│   │   │   ├── serializers.py  (Serialización de datos)
│   │   │   ├── views.py  (Controladores de los endpoints)
│   │   │   ├── urls.py  (Rutas del microservicio)
│   │   │   ├── services.py  (Lógica de negocio)
│   │   │   ├── adapters.py  (Consultas internas y externas)
│   │   │   ├── permissions.py  (Manejo de permisos y autenticación)
│   │   │   ├── validators.py  (Validaciones personalizadas)
│   │   │   ├── tasks.py  (Tareas asíncronas con Celery)
│   ├── 📂 config/
│   │   ├── settings.py  (Configuraciones principales)
│   │   ├── urls.py  (Rutas globales del servicio)
│   │   ├── wsgi.py  (Entrada WSGI para producción)
│   │   ├── asgi.py  (Para WebSockets y ASGI)
│   ├── manage.py  (Comando de administración de Django)
│── 📂 tests/  (Pruebas unitarias e integración)
│── 📂 docs/  (Documentación de API con Swagger/OpenAPI)
│── 📄 Dockerfile  (Configuración para contenedores)
│── 📄 docker-compose.yml  (Orquestación para desarrollo local)
│── 📄 requirements.txt  (Dependencias del proyecto)
│── 📄 README.md  (Explicación específica del microservicio)
```

---

## **📌 Explicación de la Estructura**
| **Directorio/Archivo** | **Descripción** |
|----------------|----------------|
| **`apps/`** | Contiene los módulos del microservicio. Cada módulo tiene su propia carpeta con modelos, lógica y endpoints. |
| **`models.py`** | Definición de modelos de base de datos con Django ORM. |
| **`serializers.py`** | Conversión entre modelos y datos JSON para API REST. |
| **`views.py`** | Controladores que manejan las solicitudes HTTP y usan `services.py`. |
| **`urls.py`** | Rutas específicas del módulo para la API. |
| **`services.py`** | Contiene la lógica de negocio para mantener `views.py` limpio. |
| **`adapters.py`** | Contiene consultas a bases de datos y acceso a datos externos. |
| **`permissions.py`** | Reglas de permisos y autenticación. |
| **`validators.py`** | Validaciones personalizadas para los datos de entrada. |
| **`tasks.py`** | Tareas asíncronas ejecutadas con Celery. |
| **`config/`** | Configuración global del servicio, incluyendo `settings.py` y `urls.py`. |
| **`tests/`** | Pruebas unitarias e integración para validar la funcionalidad del servicio. |
| **`docs/`** | Contiene la documentación API generada con Swagger/OpenAPI. |
| **`Dockerfile`** | Configuración para desplegar el servicio en un contenedor Docker. |
| **`docker-compose.yml`** | Permite ejecutar el servicio junto con dependencias en local. |
| **`requirements.txt`** | Lista de dependencias del microservicio. |

---

---

## ** Comunicación entre Servicios**
### ** Métodos de Comunicación**
📌 **Opciones disponibles:**
- **API Gateway** (Kong o Nginx) → Redirige peticiones a los servicios adecuados.
- **Mensajería Asíncrona** (Kafka o RabbitMQ) → Para eventos entre aplicaciones.
- **Base de Datos Compartida** → Solo en casos justificados.

Cuando un microservicio necesita datos de otro:
1. **Llamadas Directas API** → Un servicio consulta otro mediante API REST.
2. **Eventos Asíncronos** → Kafka(Ejemplo) permite la comunicación sin acoplamiento.
3. **Base de Datos Compartida** → Solo en escenarios donde se necesite consistencia estricta.

📌 **Más información (Ejemplos)**:
- [API Gateway con Kong](https://docs.konghq.com/)
- [Mensajería con Kafka](https://kafka.apache.org/)

---


---

## **📌 ¿Por qué usamos `adapter.py`?**
En esta arquitectura se ha optado por el uso del patrón **Adapter**, ya que un microservicio puede necesitar interactuar con **múltiples fuentes de datos**, incluyendo bases de datos, APIs externas, archivos y otros servicios internos.

📌 **Beneficios del uso de `adapter.py`:**
- **Desacoplamiento:** Separa la lógica de acceso a datos de la lógica de negocio.
- **Flexibilidad:** Permite cambiar la fuente de datos (de una API a otra, o de una base de datos a otra) sin afectar la capa de negocio.
- **Cumple con la Arquitectura Hexagonal:** Facilita la integración con múltiples interfaces externas sin modificar la lógica central.
- **Mantenimiento Simplificado:** Centraliza las consultas en un solo lugar, facilitando su actualización.

📌 **Ejemplo de Implementación de `adapter.py`:**
```python
import requests
from django.db import connection

class UserAdapter:
    """Adapter para manejar conexión con BD y APIs externas"""
    @staticmethod
    def get_users_from_db():
        with connection.cursor() as cursor:
            cursor.execute("SELECT * FROM users")
            return cursor.fetchall()

    @staticmethod
    def get_users_from_external_api():
        response = requests.get("https://external-api.com/users")
        return response.json()
```
📌 **Ejemplo de uso en `services.py`**
```python
from .adapter import UserAdapter

class UserService:
    def obtener_usuarios(self):
        usuarios_db = UserAdapter.get_users_from_db()
        usuarios_api = UserAdapter.get_users_from_external_api()
        return usuarios_db + usuarios_api
```



## **Documentación con Swagger en DjangoRF**
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

## **📌 Ubicación de las Funcionalidades Clave**
1️⃣ **Consultas a Base de Datos y APIs Externas**  → `adapters.py`
2️⃣ **Lógica de Negocio**  → `services.py`
3️⃣ **Endpoints de API**  → `views.py`
4️⃣ **Permisos y Seguridad**  → `permissions.py`
5️⃣ **Manejo de Configuración**  → `config/settings.py`
6️⃣ **Pruebas y Validaciones**  → `tests/` y `validators.py`

---

## **📌 Comunicación entre Microservicios**
Existen tres maneras en que los microservicios pueden comunicarse:

1️⃣ **API Gateway (Para llamadas HTTP síncronas)**
   - Se usa **Kong o Nginx** para redirigir peticiones entre servicios.
   - Ejemplo: `/api/usuarios → SERVICE_Usuarios`

2️⃣ **Mensajería Asíncrona (Para eventos entre servicios)**
   - Se usa **Kafka o RabbitMQ** para enviar eventos.
   - Ejemplo: SERVICE_Pedidos envía un mensaje "pedido_creado" a SERVICE_Facturacion.

3️⃣ **Base de Datos Compartida (Solo en casos específicos)**
   - Puede usarse replicación de bases de datos si se requiere acceso compartido.

---

## **📌 Desarrollo en Local con Docker Compose**
Para ejecutar el servicio en un entorno de desarrollo, se usa `docker-compose.yml`:
```yaml
version: '3.8'
services:
  service_usuarios:
    build: ./backend/SERVICE_Usuarios
    ports:
      - "8001:8000"
  service_pedidos:
    build: ./backend/SERVICE_Pedidos
    ports:
      - "8002:8000"
```
📌 **Ejecutar con:**
```bash
docker-compose up
```

## **🎯 Conclusión**
✅ **Cada microservicio tiene su propia estructura modular.**  
✅ **La lógica de negocio está separada en `services.py` y `adapters.py`.**  
✅ **El desarrollo en local se facilita con Docker Compose.**  
✅ **Se documenta cada servicio con Swagger/OpenAPI.**  

