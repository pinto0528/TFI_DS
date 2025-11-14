## Texto de Caso de Uso:
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

[[Pinto/Facultad/Diseño de Sistemas/TFI/Fase de Inicio/Especificacion/Textos de Casos de Uso]]
## Diagrama de Secuencia

![[Pinto/Facultad/Diseño de Sistemas/TFI/Diagramas/Diagramas de Secuencia/DSCU4.png]]

[[Diagramas de Secuencia]]



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

[[Contratos]]

## Diagrama de Colaboracion

![[Pinto/Facultad/Diseño de Sistemas/TFI/Diagramas/Diagramas de Colaboracion/DCCU4.png]]
[[Diagramas de Colaboracion]]