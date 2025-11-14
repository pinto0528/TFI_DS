## [[CU2 - Solicitar Repuestos]]

### Información General

- Actor principal: Personal de Mecánica
- Precondición: El usuario debe estar autenticado.
- Postcondición: Se generó la solicitud de repuesto, que queda registrada en el sistema y notificada al personal correspondiente.

---

### Escenario Principal de Éxito

1. El usuario selecciona la opción de generar una nueva Solicitud de Repuesto.
    
2. El usuario selecciona el repuesto o insumo requerido y la cantidad necesaria.
    
3. El paso 2 se repite según la cantidad de repuestos a solicitar.
    
4. El sistema muestra un resumen de la solicitud creada.
    
5. El usuario confirma la solicitud.
    
6. El sistema registra la solicitud de manera exitosa y notifica al personal de inventario. 

---
### Cursos Alternativos

a. Fallas del sistema

- Si el sistema presenta un fallo, se reinicia forzosamente en un estado nuevo


b. Repuesto no registrado

- Si el repuesto seleccionado no está registrado:  

1. El sistema informa al usuario.
    
2. El usuario puede cancelar la solicitud de el repuesto no registrado, o cancelar la operación.  
  

c. Usuario no confirma la solicitud

- Si el usuario no confirma la solicitud en el paso 5:

1. La solicitud no se genera y se retorna al paso 2 para modificar o completar los datos.    

d. Usuario decide finalizar la operación

1. Si no se cargó información en el sistema, el sistema finaliza la operación inmediatamente.
    
2. d2. Si se cargó información, el sistema solicita confirmación antes de cerrar la operación y luego finaliza la misma

## [[CU3 - Actualizar Estado de Reparacion]]
### Información General

- Actor principal: Personal de Mecánica
- Precondición: El actor debe haber iniciado sesión en el sistema con un rol de "Personal de Mecánica" o superior y debe existir previamente una SolicitudReparacion registrada en el sistema.
- Postcondición: Se crea y persiste una nueva entrada en el historial de la SolicitudReparación , registrando el nuevo estado, los detalles, la fecha/hora y el usuario responsable. El estado principal de la reparación se actualiza.


---

### Escenario Principal de Éxito

1. El usuario selecciona la opción "Actualizar Estado de Reparación"
    
2. El sistema solicita el nuevo estado y las observaciones correspondientes.
    
3. El usuario registra la información sobre el avance de la reparación en los campos del formulario.
    
4. El usuario confirma la operación para guardar la nueva actualización.
    
5. El sistema valida los datos ingresados.
    
6. El sistema muestra un mensaje de confirmación
    
7. El sistema actualiza la información. El caso de uso finaliza.


---

### Cursos Alternativos

4a. El usuario cancela la operación

- Descripción: Después de rellenar el formulario en el paso 3, el usuario se arrepiente y presiona el botón "Cancelar".
    
- Resultado: El sistema descarta toda la información ingresada en el formulario y el caso de uso finaliza sin realizar cambios.


5a. Los datos ingresados son inválidos

- Descripción: El sistema detecta que falta información obligatoria o que algún dato tiene un formato incorrecto (por ejemplo, el campo "detalles" está vacío).
    
- Resultado: El sistema no guarda la información. Muestra un mensaje de error específico al usuario (ej: "El campo 'Detalles' es obligatorio") y el flujo regresa al paso 2, permitiendo al usuario corregir los datos en el formulario.


5b. Falla del sistema

- Descripción: Ocurre un error inesperado que impide al sistema persistir los cambios (ej: se pierde la conexión con la base de datos).
    
- Resultado: El sistema muestra un mensaje de error genérico al usuario ("No se pudo guardar la actualización, intente nuevamente") y el caso de uso termina de forma anormal.

## [[CU4 - Ingresar Nuevo Repuesto]]
### Información General

- Actor principal: Personal de inventario.
- Precondición: El usuario debe estar autenticado y haber seleccionado la operación correspondiente
- Postcondición: Se registró un nuevo repuesto

---

### Escenario Principal de Éxito

1. El sistema solicita la información a cargar.
    
2. El usuario carga la información de la pieza a ingresar
    
3. El usuario envia la informacion
    
4. El sistema valida los datos.
    
5. El sistema le solicita al usuario confirmar la operación.
    
6. El usuario confirma la operación.
    
7. El sistema registra el producto y actualiza el stock.
    
8. El sistema informa sobre la operación exitosa.

---
### Cursos Alternativos

*a. El sistema puede fallar

- El sistema se reinicia forzosamente en un estado nuevo. 


3a. Se produjo un error en el envío de la información

- El sistema informa el error.
    
- Se regresa al paso 2.


4a. Los datos no son válidos

- El sistema informa del error.
    
- Se regresa al paso 1.


6a. El usuario cancela la operación

- El sistema informa al usuario de la cancelación.
    
- Se regresa al paso 1.


7a. Error durante la actualización

- El sistema informa del error. 
    
- Se regresa al paso 1.


*b. El usuario desea finalizar la operación

- El sistema solicita la confirmación del cierre
    
- El sistema finaliza la operación