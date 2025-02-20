# 🏗️ Clean Architecture en React y Django - Guía Completa

## 📌 Introducción
Este documento proporciona una guía detallada para la implementación de **Clean Architecture** en aplicaciones web utilizando **React** para el Frontend y **Django** para el Backend.

El objetivo es estructurar el proyecto de manera modular, escalable y mantenible, siguiendo buenas prácticas de desarrollo.

## 🏛️ Principios de Clean Architecture

Clean Architecture busca separar la aplicación en capas con el fin de mejorar:
- **Mantenibilidad** 📌 (Cada módulo tiene su responsabilidad)
- **Escalabilidad** 🚀 (Fácil de expandir sin afectar otras partes del sistema)
- **Pruebas** ✅ (Cada capa puede ser testeada de manera independiente)


## 📂 Estructura del Proyecto

El proyecto está organizado en dos directorios principales:
```
📂 my_project/
├── 📂 frontend/  # Aplicación React
├── 📂 backend/   # Aplicación Django
├── 📂 database/  # Configuración de la Base de Datos
├── 📂 deployment/ # Configuración de despliegue
├── 📄 README.md  # Documentación
```

---

## 📌 1️⃣ Estructura del Frontend (React)

```
📂 frontend/src/
├── 📂 adapters/       # Transformación de datos
├── 📂 components/     # Componentes reutilizables
│   ├── common/       # Botones, modales, inputs
│   ├── layout/       # Header, Sidebar, Footer
│   ├── pages/        # Componentes específicos de cada página
├── 📂 hooks/          # Hooks personalizados
├── 📂 pages/          # Páginas principales
│   ├── Home/
│   │   ├── Home.jsx  # Contenedor principal
│   │   ├── components/  # Componentes específicos de Home
│   │   ├── hooks/    # Hooks específicos de Home
│   │   ├── services/ # Llamadas a API de Home
├── 📂 services/       # Comunicación con API
├── 📂 store/          # Estado global (Redux, Context API)
├── 📂 styles/         # Estilos globales
├── 📂 utils/          # Utilidades generales
├── 📄 main.tsx        # Punto de entrada
```

### 🔹 Comunicación con el Backend
📌 **React** consume la API de Django a través de **REST API o GraphQL**.
```typescript
import axios from "axios";

const API_URL = process.env.REACT_APP_API_URL || "http://localhost:8000/api";

export const getUsers = async () => {
  return axios.get(`${API_URL}/users/`);
};
```

---

## 📌 2️⃣ Estructura del Backend (Django + Django REST Framework)

```
📂 backend/service_nombre/
├── 📂 apps/
│   ├── 📂 users/
│   │   ├── models.py      # Modelos de BD
│   │   ├── serializers.py # Serialización
│   │   ├── views.py       # Controladores
│   │   ├── urls.py        # Rutas del microservicio
│   │   ├── services.py    # Lógica de negocio
│   │   ├── adapters.py    # Consultas internas y externas
│   │   ├── permissions.py # Manejo de permisos
│   │   ├── validators.py  # Validaciones
│   │   ├── tasks.py       # Tareas asíncronas
├── 📂 config/
│   ├── settings.py  # Configuraciones principales
│   ├── urls.py      # Rutas globales
│   ├── wsgi.py      # Entrada WSGI
│   ├── asgi.py      # Para WebSockets y ASGI
├── 📂 tests/        # Pruebas unitarias
├── 📂 docs/         # Documentación API con Swagger
├── 📄 manage.py     # Script de Django
├── 📄 Dockerfile    # Configuración para Docker
├── 📄 requirements.txt # Dependencias
```

### 🔹 Comunicación entre Microservicios
1️⃣ **API Gateway (Kong o Nginx)** → Redirige peticiones entre microservicios.
2️⃣ **Mensajería Asíncrona (Kafka o RabbitMQ)** → Comunicación sin acoplamiento.
3️⃣ **Base de Datos Compartida** (Solo si es estrictamente necesario).

Ejemplo de `adapters.py` para desacoplar la lógica de acceso a datos:
```python
import requests
from django.db import connection

class UserAdapter:
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

---

## 📌 3️⃣ Despliegue con Docker y Kubernetes

### **Ejemplo de `docker-compose.yml`** para levantar el backend y la base de datos en local:
```yaml
version: '3.8'
services:
  backend:
    build: ./backend
    ports:
      - "8000:8000"
    depends_on:
      - database
  database:
    image: postgres:14
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```

### **Ejecución del Proyecto** 🚀
```bash
# Clonar el repositorio
$ git clone https://github.com/Prebel/my_project.git && cd my_project

# Iniciar backend (Django)
$ cd backend && python manage.py runserver

# Iniciar frontend (React)
$ cd frontend && npm start

# Ejecutar con Docker
$ docker-compose up
```

---

## 📌 4️⃣ Conclusión
✅ **Separación clara de responsabilidades** en cada capa.  
✅ **Escalabilidad** al permitir crecimiento sin afectar otras partes del sistema.  
✅ **Fácil integración** con APIs externas y microservicios.  
✅ **Despliegue eficiente** con Docker/Kubernetes.  

Con esta estructura, el proyecto se mantiene **modular, flexible y listo para la producción**. 🚀


