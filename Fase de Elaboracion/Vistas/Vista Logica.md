### **Subsistemas y capas del sistema**

**Capa de Presentación (UI Web):**  
Proporciona las interfaces gráficas para los diferentes tipos de usuarios: operador, técnico, jefe de taller e inventarista.

**Capa de Aplicación (Use Cases):**  
Gestiona los casos de uso del sistema. Se encarga de coordinar las operaciones entre las distintas entidades, validar las reglas de negocio y orquestar el flujo de la información.

**Capa de Dominio (Core):**  
Contiene las entidades, interfaces y reglas de negocio principales. Representa el núcleo lógico del sistema y define su comportamiento esencial.

**Capa de Infraestructura (Data):**  
Implementa los mecanismos de acceso a datos y la comunicación con servicios externos. Incluye repositorios, conexiones a la base de datos y adaptadores técnicos.

---

### **Subsistemas y sus funciones principales**

|**Subsistema**|**Funciones principales**|
|---|---|
|**Gestión de Reparaciones**|Registro de vehículos, seguimiento del estado de reparación y generación de informes.|
|**Gestión de Repuestos y Stock**|Verificación de stock, actualización de cantidades e ingreso de nuevos repuestos.|
|**Gestión de Solicitudes de Compra**|Generación automática de solicitudes ante falta de stock y registro de compras.|
|**Gestión de Usuarios y Roles**|Control de accesos y validación de acciones de acuerdo con el rol asignado.|
|**Consultas e Informes**|Consulta del estado de las reparaciones y generación de reportes técnicos.|

---

### **Interfaces entre subsistemas**

| **Subsistema origen** | **Subsistema destino**      | **Interfaz requerida**                              |
| --------------------- | --------------------------- | --------------------------------------------------- |
| **Reparaciones**      | **Repuestos**               | Verificación de stock y solicitud de repuestos.     |
| **Repuestos**         | **Compras**                 | Generación de solicitudes de compra automáticas.    |
| **Usuarios**          | **Reparaciones / Informes** | Validación de permisos y control de acceso por rol. |
| **Reparaciones**      | **Informes**                | Generación y redacción de informes técnicos.        |
