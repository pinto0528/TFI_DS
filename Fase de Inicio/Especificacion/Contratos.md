## [[CU2 - Solicitar Repuestos]]
## Contrato

Actor Principal: Personal de Mecánica

Propósito: Permitir al Personal de Mecánica registrar una nueva solicitud de repuesto en el sistema, validando los datos e informando el resultado.

### Precondiciones

- El usuario (Personal de Mecánica) debe estar autenticado en el sistema.
    
- El usuario debe tener los permisos asignados para "Crear Solicitudes". 

### Postcondiciones (En caso de éxito)

- Se creo una nueva instancia de SolicitudRepuesto en la base de datos.
    
- La nueva solicitud se cargo con los datos idRepuesto y cantidad especificados.
    
- La nueva solicitud se registro con un estado inicial.

### Errores / Excepciones

- Datos inválidos (ej. cantidad <= 0): El sistema informa el error y permite al usuario corregir los datos en el formulario.
    
- Repuesto no registrado: El sistema informa que el idRepuesto no existe y permite cancelar o reingresar.
    
- Usuario no confirma: El usuario cancela en el diálogo de confirmación. La solicitud no se genera y el sistema retorna al formulario.
    
- Fallo del sistema: La operación se cancela, se informa al usuario y no se genera la solicitud.
## [[CU3 - Actualizar Estado de Reparacion]]
## Contrato

Actor Principal: Personal de Mecánica

Propósito: Permitir al Personal de Mecánica registrar un nuevo estado o avance en una SolicitudReparacion existente, validando los datos y persistiendo el cambio en el sistema.

### Precondiciones

- El usuario (Personal de Mecánica) debe estar autenticado en el sistema.
    
- El usuario debe tener los permisos asignados para "Actualizar Reparaciones".
    
- Debe existir una instancia de SolicitudReparacion a la cual se le añadirá la actualización.


### Postcondiciones (En caso de éxito)

- Se creó una nueva entrada en el historial de la SolicitudReparacion.
    
- La nueva entrada del historial se registró con el nuevoEstado y las observaciones proporcionadas por el usuario.
    
- El estado general de la SolicitudReparacion se actualizó para reflejar el nuevoEstado más reciente.
    
- Los cambios fueron persistidos de forma atómica en la base de datos.


### Errores / Excepciones

- Datos inválidos (corresponde a 5a): Si el nuevoEstado o las observaciones están vacíos o no cumplen con el formato requerido. El sistema informa el error específico y permite al usuario corregir los datos en el formulario.
    
- Usuario no confirma (corresponde a 4a): El usuario cancela la operación en el formulario. No se realiza ningún cambio en el sistema.
    
- Fallo del sistema (corresponde a 5b): Ocurre un error al intentar guardar los datos (ej. falla de conexión con la base de datos). La operación se cancela, se informa al usuario del problema y no se realiza ningún cambio en la SolicitudReparacion.
## [[CU4 - Ingresar Nuevo Repuesto]]
## Contrato

Actor Principal:  
Personal de Inventario

Propósito:  
Permitir al Personal de Inventario registrar un nuevo repuesto en el sistema, validando los datos ingresados, solicitando confirmación del usuario e informando el resultado final de la operación.

  
### Precondiciones

- El usuario (Personal de Inventario) debe estar autenticado en el sistema.
    
- El usuario debe haber seleccionado la opción “Ingresar nuevo repuesto”.
    
- El sistema debe encontrarse en estado operativo (sin errores previos).  

### Postcondiciones (En caso de éxito)

- Se creó un nuevo registro de Repuesto en la base de datos con la información ingresada (nombre, código, descripción, cantidad, proveedor, etc.).
    
- El stock general de inventario se actualizó correctamente.
    
- El sistema generó una notificación confirmando la operación exitosa.  

### Errores / Excepciones

3a. Error en el envío de la información:  
El sistema informa el error de comunicación. El usuario puede reintentar el envío o volver a ingresar los datos (retorna al paso 2).

4a. Datos inválidos:  
El sistema detecta que los datos son incorrectos o incompletos (por ejemplo, campos vacíos, cantidad ≤ 0 o código duplicado).  
El sistema muestra un mensaje de error y permite al usuario corregir los datos (retorna al paso 1).

6a. Cancelación por parte del usuario:  
El usuario cancela la operación durante el diálogo de confirmación.  
El sistema informa la cancelación y retorna al formulario inicial (paso 1).

7a. Error durante la actualización:  
Se produce un error interno al registrar el repuesto o actualizar el stock.  
El sistema informa el error y retorna al estado previo sin realizar modificaciones.

a. Fallo general del sistema:  
El sistema falla durante el proceso. Se reinicia forzosamente en un estado limpio. No se registra el repuesto ni se modifican datos.

b. Cierre voluntario del usuario:  
El usuario elige finalizar la operación.  
El sistema solicita confirmación del cierre, y al confirmarse, finaliza la sesión o regresa al menú principal sin registrar cambios.**