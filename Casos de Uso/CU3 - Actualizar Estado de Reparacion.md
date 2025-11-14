## Texto de Caso de Uso

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

[[Textos de Casos de Uso]]
## Diagrama de Secuencia

![[Pinto/Facultad/Diseño de Sistemas/TFI/Diagramas/Diagramas de Secuencia/DSCU3.png]]

[[Diagramas de Secuencia]]
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

[[Contratos]]