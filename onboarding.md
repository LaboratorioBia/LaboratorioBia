## Guía de Estilo y Buenas Prácticas**

### **Introducción**
Esta guía establece las normas para el desarrollo de proyectos dentro de nuestro equipo. Nuestro objetivo es mantener un código limpio, consistente y fácil de mantener. Estas prácticas se aplican a nomenclaturas, definiciones de variables, clases, directorios y documentación.

---

### **1. Estandarización de Nomenclaturas**

#### **1.1 Nombres de Variables y Funciones**
- **Formato**: Usar `snake_case` para variables y funciones.
- **Prefijos específicos**:
  - Para funciones de CRUD:
    - `create_`: Crear un recurso.
    - `read_`: Leer un recurso.
    - `update_`: Actualizar un recurso.
    - `delete_`: Eliminar un recurso.
  - Para funciones auxiliares:
    - `get_`: Obtener datos o configuraciones.
    - `set_`: Establecer valores.
    - `process_`: Procesar datos.
    - `calculate_`: Realizar cálculos.
    - `validate_`: Validar datos.
- **Ejemplo**:
  ```python
  def calculate_total_price(items):
      # Calcula el precio total de los items
      pass
  ```

#### **1.2 Nombres de Clases**
- **Formato**: Usar `PascalCase` para clases.
- **Sufijos específicos**:
  - `Controller`: Clases que gestionan la lógica del flujo (MVC o REST APIs).
  - `Service`: Clases que contienen la lógica de negocio.
  - `Adapter`: Clases que interactúan con sistemas externos.
  - `Repository`: Clases que encapsulan el acceso a datos.
- **Ejemplo**:
  ```python
  class SalesReportService:
      # Maneja la lógica de generación de reportes de ventas
      pass
  ```

#### **1.3 Directorios**
- **Formato**: Usar nombres en **minúscula** separados por guiones bajos (`snake_case`) para directorios.
- **Directorio raíz**: Cada directorio debe representar una capa de la aplicación o un módulo específico.
- **Ejemplo**:
  ```plaintext
  /rpa/
  ├── /tasks/
  ├── /workflows/
  ├── /adapters/
  ├── /config/
  └── /utils/
  ```

---

### **2. Estándar de Documentación**

#### **2.1 Docstrings Detallados**
- **Formato**: Usar **Google Style** para la documentación interna.
- **Idioma**: Español, para facilitar la comprensión del equipo.

#### **Ejemplo de Docstring para una Función**
```python
def calculate_total_price(items):
    """
    Calcula el precio total de los items.

    Args:
        items (list): Lista de diccionarios con información del item. 
                      Cada diccionario debe incluir las claves `price` (float) y `quantity` (int).

    Returns:
        float: Precio total calculado.
    """
    return sum(item['price'] * item['quantity'] for item in items)
```

#### **Ejemplo de Docstring para una Clase**
```python
class SalesReportService:
    """
    Servicio para la generación de reportes de ventas.

    Métodos:
        generate_report(data): Genera un reporte en formato Excel.
        send_report(email): Envía el reporte por correo electrónico.
    """
    def generate_report(self, data):
        """
        Genera un reporte en formato Excel a partir de los datos proporcionados.

        Args:
            data (list): Lista de diccionarios con las ventas.

        Returns:
            str: Ruta al archivo generado.
        """
        pass
```

---

### **3. Uso de Swagger para APIs**
- Usaremos **Swagger** (o OpenAPI) para documentar APIs REST. 
- Todas las rutas deben incluir:
  - Descripción clara del endpoint.
  - Ejemplo de entrada y salida.
  - Posibles códigos de error.
- **Ejemplo de Documentación en Swagger**:
```yaml
paths:
  /sales:
    get:
      summary: Obtiene la lista de ventas.
      description: Retorna una lista de ventas con detalles como precio, cantidad, y fecha.
      responses:
        200:
          description: Lista de ventas obtenida con éxito.
        400:
          description: Error en la solicitud.
```

---

### **4. Estándar de Definición de Proyectos**
- **Idiomas**:
  - Todo el algoritmo debe estar en inglés (variables, funciones, clases).
  - La documentación (docstrings, comentarios) estará en español.
- **Organización del Proyecto**:
  - Cada módulo debe separarse por función (tareas, adaptadores, workflows).
  - Los nombres de los archivos deben reflejar claramente su contenido.
- **Ejemplo**:
  ```plaintext
  /rpa/
  ├── main.py                  # Punto de entrada principal.
  ├── /tasks/                  # Tareas específicas del RPA.
  │   ├── __init__.py
  │   ├── calculate_price.py
  ├── /adapters/               # Adaptadores externos.
  │   ├── api_adapter.py
  │   └── database_adapter.py
  └── /config/                 # Configuración compartida.
      ├── settings.py
      └── logger.py
  ```

---

### **5. Recomendaciones Generales**
1. **Nombrado Consistente**:
   - Todos los nombres deben ser intuitivos y descriptivos.
2. **Principios SOLID**:
   - Aplica separación de responsabilidades: cada clase o función debe tener un propósito claro.
3. **Pruebas**:
   - Escribe pruebas unitarias y de integración para cada módulo.
4. **Revisiones de Código**:
   - Usa herramientas como GitHub Actions para validar estándares automáticamente.

---

### **6. Guía de Implementación para Nuevos Desarrolladores**
- **Paso 1**: Familiarízate con la estructura del proyecto y las convenciones de nomenclatura.
- **Paso 2**: Consulta los docstrings para entender la funcionalidad de cada módulo.
- **Paso 3**: Usa ejemplos y plantillas existentes como base para nuevas implementaciones.
- **Paso 4**: Sigue los estándares al escribir código, incluyendo nombres en inglés y docstrings en español.

---

### **Conclusión**
Esta guía proporciona una base sólida para desarrollar proyectos de forma estandarizada y colaborativa. Cualquier duda o sugerencia debe discutirse en las revisiones de código o reuniones del equipo.

---
