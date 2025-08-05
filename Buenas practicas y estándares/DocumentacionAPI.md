# 📘 Estándar Corporativo para Documentación de APIs en Swagger (Django REST Framework)

Este documento define las **buenas prácticas** para documentar endpoints de **Django REST Framework** utilizando **Swagger** (con `drf-yasg` o `drf-spectacular`), garantizando que las APIs sean **claras, autodescriptivas y fáciles de consumir**.

---

## 🎯 Objetivo

- Proporcionar **documentación legible y estandarizada** para los consumidores de la API.
- Definir **cómo describir endpoints, parámetros, respuestas y códigos de error**.
- Asegurar que los desarrolladores mantengan la documentación **actualizada y alineada con el código**.

---

## **1. Librerías recomendadas**

Para generar la documentación de Swagger en Django REST Framework:

- **[drf-yasg](https://drf-yasg.readthedocs.io/)** (Documentación muy flexible con decoradores).
- **[drf-spectacular](https://drf-spectacular.readthedocs.io/)** (Más alineado a OpenAPI 3.0).

> **Nota:** Escoge la que más se adapte al proyecto. Este estándar aplica para ambas.

---

## **2. Documentar Endpoints con drf-yasg**

### **Decorador `swagger_auto_schema`**

Usa el decorador en **views** o **viewsets** para describir parámetros, cuerpos y respuestas.

**Ejemplo básico:**

```python
from drf_yasg.utils import swagger_auto_schema
from drf_yasg import openapi
from rest_framework import status, viewsets
from rest_framework.response import Response

class PedidoViewSet(viewsets.ViewSet):
    @swagger_auto_schema(
        operation_description="Obtiene el detalle de un pedido por su ID",
        manual_parameters=[
            openapi.Parameter(
                'pedido_id',
                openapi.IN_PATH,
                description="ID del pedido a consultar",
                type=openapi.TYPE_INTEGER
            ),
        ],
        responses={
            200: openapi.Response('Pedido encontrado', schema=openapi.Schema(
                type=openapi.TYPE_OBJECT,
                properties={
                    'id': openapi.Schema(type=openapi.TYPE_INTEGER),
                    'cliente': openapi.Schema(type=openapi.TYPE_STRING),
                    'total': openapi.Schema(type=openapi.TYPE_NUMBER),
                }
            )),
            404: "Pedido no encontrado"
        }
    )
    def retrieve(self, request, pedido_id=None):
        """Retorna el detalle de un pedido."""
        pedido = {"id": pedido_id, "cliente": "Juan Pérez", "total": 1500}
        return Response(pedido, status=status.HTTP_200_OK)
```

## **3. Documentar con drf-spectacular (OpenAPI 3)**

Si utilizas `drf-spectacular`, la documentación se hace con el decorador `extend_schema`.

### **Ejemplo básico:**

```python
from drf_spectacular.utils import extend_schema, OpenApiParameter, OpenApiResponse
from rest_framework import status, viewsets
from rest_framework.response import Response

class PedidoViewSet(viewsets.ViewSet):
    @extend_schema(
        description="Obtiene el detalle de un pedido por su ID",
        parameters=[
            OpenApiParameter(name='pedido_id', description='ID del pedido', required=True, type=int),
        ],
        responses={
            200: OpenApiResponse(description="Pedido encontrado", response={
                "type": "object",
                "properties": {
                    "id": {"type": "integer"},
                    "cliente": {"type": "string"},
                    "total": {"type": "number"},
                }
            }),
            404: OpenApiResponse(description="Pedido no encontrado")
        }
    )
    def retrieve(self, request, pedido_id=None):
        """Retorna el detalle de un pedido."""
        pedido = {"id": pedido_id, "cliente": "Juan Pérez", "total": 1500}
        return Response(pedido, status=status.HTTP_200_OK)
```

## **4. Buenas prácticas de documentación**

- **Usar descripciones claras**: Explica **qué hace** el endpoint y **para qué sirve**.

- **Documentar parámetros y ejemplos:**

  - Parámetros de consulta (`query params`).

  - Parámetros de ruta (`path params`).

  - Cuerpo de la petición (`request body`).

- **Incluir códigos de estado:** Describe todos los posibles `HTTP status codes` (200, 400, 404, 500, etc.).

- **Definir esquemas de respuesta:** Usar `Schema` para describir la estructura del JSON.

- **Agregar ejemplos** de peticiones y respuestas esperadas.

- **Mantener consistencia** entre nombres y convenciones de la API.

## **5. Ejemplo Completo de Documentación**

### **Endpoint: Crear Pedido**

```python
from drf_yasg.utils import swagger_auto_schema
from drf_yasg import openapi
from rest_framework import status, viewsets
from rest_framework.response import Response

class PedidoViewSet(viewsets.ViewSet):

    @swagger_auto_schema(
        operation_description="Crea un nuevo pedido para un cliente.",
        request_body=openapi.Schema(
            type=openapi.TYPE_OBJECT,
            required=['cliente', 'productos'],
            properties={
                'cliente': openapi.Schema(type=openapi.TYPE_STRING, description='Nombre del cliente'),
                'productos': openapi.Schema(
                    type=openapi.TYPE_ARRAY,
                    items=openapi.Items(type=openapi.TYPE_INTEGER),
                    description='IDs de los productos incluidos en el pedido'
                )
            }
        ),
        responses={
            201: openapi.Response('Pedido creado exitosamente'),
            400: openapi.Response('Datos inválidos')
        }
    )
    def create(self, request):
        """Crea un nuevo pedido para un cliente."""
        return Response({"mensaje": "Pedido creado"}, status=status.HTTP_201_CREATED)
```

## **6. Resumen rápido (Checklist)**

- Descripción clara de cada endpoint.

- Parámetros documentados (path, query, body).

- Esquemas de respuesta definidos.

- Códigos de estado documentados.

- Ejemplos incluidos (cuando aplique).

## **🔒 Nota:**

- La documentación debe **actualizarse con cada cambio en los endpoints.**

- Si un endpoint cambia pero **no se actualiza la documentación**, esto puede causar **fallos en integraciones externas**
