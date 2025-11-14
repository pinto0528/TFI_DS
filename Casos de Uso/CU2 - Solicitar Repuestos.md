## Texto de Caso de Uso:

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

[[Textos de Casos de Uso]]

## Diagrama de Secuencia

![[Pinto/Facultad/Diseño de Sistemas/TFI/Diagramas/Diagramas de Secuencia/DSCU2.png]]

[[Diagramas de Secuencia]]

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

[[Contratos]]