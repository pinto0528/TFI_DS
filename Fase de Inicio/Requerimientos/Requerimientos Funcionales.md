## **Requerimientos Funcionales**

### **Módulo: Chofer**

- **RFC01:** El sistema deberá permitir el registro de vehículos para reparación, incluyendo los datos personales del chofer, los datos del vehículo y una descripción del problema.
- **RFC02:** El sistema deberá generar automáticamente un número de reparación único por cada registro exitoso.
- **RFC03:** El sistema deberá permitir la consulta del estado de las reparaciones asociadas al número de legajo del chofer.

---

### **Módulo: Jefe de Taller**

- **RFT01:** El sistema deberá permitir la consulta de las solicitudes de repuestos generadas por el personal de mecánica.
- **RFT02:** El sistema deberá permitir la aprobación o el rechazo de solicitudes de repuestos e insumos.
- **RFT03:** El sistema deberá permitir la consulta del estado de las reparaciones en curso y finalizadas.

---

### **Módulo: Personal de Mecánica**

- **RFM01:** El sistema deberá permitir la generación de solicitudes de repuestos e insumos asociados a las reparaciones.
- **RFM02:** El sistema deberá permitir el registro de actualizaciones sobre el estado de una reparación, identificada por su número de reparación.
- **RFM03:** El sistema deberá mostrar el historial completo de actualizaciones correspondientes a cada número de reparación.

---

### **Módulo: Personal de Inventario**

- **RFI01:** El sistema deberá permitir la generación manual de solicitudes de compra con el fin de mantener niveles de stock adecuados.
- **RFI02:** El sistema deberá permitir la actualización del stock, incluyendo el ingreso de nuevas piezas y la modificación de las cantidades disponibles.

---

### **Módulo: Sistema General**

- **RFS01:** El sistema deberá validar la existencia del número de legajo antes de ejecutar cualquier operación asociada al chofer o al vehículo.
- **RFS02:** El sistema deberá realizar un control automático del stock ante la aprobación de una solicitud de repuestos.
- **RFS03:** El sistema deberá generar automáticamente una solicitud de compra cuando el stock sea insuficiente para atender una solicitud aprobada.