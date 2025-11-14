### **Usuario**

**Descripción:** Representa a la persona que interactúa con el sistema, como técnicos, supervisores u otros roles autorizados.  
**Atributos:** `idUsuario`, `nombre`, `rol`  
**Relaciones clave:**

- Crea solicitudes de reparación.
- Redacta informes.

---

### **Solicitud de Reparación**

**Descripción:** Solicitud registrada para ejecutar reparaciones en un vehículo.  
**Atributos:** `idSolicitud`, `fecha`, `tipo`, `estado`, `observaciones`  
**Relaciones clave:**

- Es creada por un Usuario.
- Está asociada a un Vehículo.
- Genera Solicitudes de Repuesto.
- Genera Informes.

---

### **Vehículo**

**Descripción:** Activo físico que requiere mantenimiento o reparación.  
**Atributos:** `idVehiculo`, `placa`, `tipo`, `estado`  
**Relaciones clave:**

- Se asocia a una o más Solicitudes de Reparación.

---

### **Solicitud de Repuesto**

**Descripción:** Solicitud generada para obtener las piezas necesarias para una reparación.  
**Atributos:** `idSolicitudRepuesto`, `fecha`, `estado`  
**Relaciones clave:**

- Generada por una Solicitud de Reparación.
- Incluye uno o más Repuestos.
- Puede generar una Solicitud de Compra si no hay stock disponible.

---

### **Repuesto**

**Descripción:** Componente físico requerido para reparar un vehículo.  
**Atributos:** `idRepuesto`, `nombre`, `cantidadDisponible`, `proveedor`  
**Relaciones clave:**

- Es incluido en una Solicitud de Repuesto.

---

### **Compra de Repuesto**

**Descripción:** Documento que formaliza la necesidad de adquirir un repuesto no disponible en stock.  
**Atributos:** `idSolicitudCompra`, `fecha`, `estado`  
**Relaciones clave:**

- Puede ser generada a partir de una Solicitud de Repuesto.

---

### **Informe**

**Descripción:** Documento elaborado tras una reparación, con información técnica o administrativa.  
**Atributos:** `idInforme`, `tipo`, `fecha`, `detalles`  
**Relaciones clave:**

- Es generado por una Solicitud de Reparación.
- Es redactado por un Usuario.