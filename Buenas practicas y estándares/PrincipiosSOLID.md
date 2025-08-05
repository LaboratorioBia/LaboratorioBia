# 🧩 Principios SOLID (Resumen Corporativo)

Los **principios SOLID** son un conjunto de buenas prácticas de desarrollo que ayudan a **crear software mantenible, escalable y fácil de entender**.

---

## **1. S – Single Responsibility Principle (SRP)**

**Una clase debe tener una única responsabilidad.**

- Cada clase/módulo debe encargarse de **una sola cosa**.
- Si una clase hace demasiado, será difícil de mantener y probar.

**Ejemplo:**

```python
# ❌ Mal: Clase hace demasiadas cosas
class Reporte:
    def generar_pdf(self): ...
    def enviar_correo(self): ...

# ✅ Bien: Separar responsabilidades
class ReportePDF:
    def generar(self): ...

class ServicioCorreo:
    def enviar(self): ...
```

## **2. O – Open/Closed Principle (OCP)**

**El código debe estar abierto a la extensión, pero cerrado a la modificación.**

- Puedes agregar **nuevas funcionalidades** sin cambiar el código existente.

### **Ejemplo:**

```python
# Con polimorfismo se pueden añadir nuevos formatos sin modificar la clase base
class CalculadoraImpuesto:
    def calcular(self, monto): ...

class ImpuestoIVA(CalculadoraImpuesto):
    def calcular(self, monto): return monto * 0.19

class ImpuestoReteFuente(CalculadoraImpuesto):
    def calcular(self, monto): return monto * 0.10
```

## **3. L – Liskov Substitution Principle (LSP)**

**Las clases hijas deben poder reemplazar a sus clases padres sin alterar el comportamiento esperado.**

- Si una subclase rompe el funcionamiento del código que usa la clase base, viola este principio.

### **Ejemplo:**

```python
class Ave:
    def volar(self): ...

class Pinguino(Ave):
    # ❌ Mal: Pinguino no vuela, rompe expectativas
    def volar(self): raise Exception("No puedo volar")
```

## **4. I – Interface Segregation Principle (ISP)**

**No obligar a las clases a implementar métodos que no necesitan.**

- Mejor varias interfaces pequeñas que una enorme.

### **Ejemplo:**

```pyton
# ❌ Mal: Interfaz obliga a implementar métodos innecesarios
class Animal:
    def volar(self): ...
    def nadar(self): ...

# ✅ Bien: Interfaces separadas
class Volador:
    def volar(self): ...

class Nadador:
    def nadar(self): ...
```

## **5. D – Dependency Inversion Principle (DIP)**

**Depender de abstracciones, no de implementaciones concretas.**

- Las clases deben depender de **interfaces o clases abstractas**, no de clases específicas.

### **Ejemplo:**

```python
# ❌ Mal: Depende de una implementación concreta
class ServicioNotificacion:
    def __init__(self):
        self.email = EmailService()

# ✅ Bien: Depender de una abstracción
class ServicioNotificacion:
    def __init__(self, servicio):
        self.servicio = servicio
```

---

## **Resumen Visual**

- **S** – Una clase = una responsabilidad.

- **O** – Extiende sin modificar.

- **L** – Subclases deben comportarse como la clase base.

- **I** – Interfaces pequeñas y específicas.

- **D** – Depender de abstracciones, no implementaciones concretas.

---

## **🔒 Nota:**

- Aplicar SOLID mejora la **modularidad, pruebas y escalabilidad** del software, reduciendo el riesgo de errores al crecer el sistema.
