```plantuml

' Fondo transparente
skinparam backgroundColor transparent

' Color del texto de los objetos
skinparam ObjectFontColor white
skinparam ObjectBorderColor white
skinparam ObjectBackgroundColor transparent

' Color de flechas y etiquetas
skinparam ArrowColor white
skinparam ArrowFontColor white

' Desactivar sombras para más claridad
skinparam shadowing false

Object Vehiculo
Object Usuario
Object Chofer
Object Informe
Object Repuesto
Object CompraRepuesto
Object Reparacion
Object SolicitudRepuesto
Object LineaSolicitudRepuesto
Object LineaCompraRepuesto
Object Rol

  
Usuario "*" --> "*" Rol: pertenece
Chofer "1"--> "1..*" Vehiculo : entrega
Vehiculo "1" --> "1..*" Reparacion : necesita
Usuario "1" --> "1..*" Reparacion : realiza
Informe "1" --> "1..*" Reparacion : detalla
SolicitudRepuesto "1" --> "1..*" LineaSolicitudRepuesto : incluye
CompraRepuesto "1"-->"1..*" LineaCompraRepuesto : incluye
SolicitudRepuesto "1"-->"1" CompraRepuesto : asociada
LineaCompraRepuesto "1"-->"1" Repuesto : tiene
LineaSolicitudRepuesto "1" --> "1" Repuesto : tiene
Usuario "1" --> "1..*" CompraRepuesto : autoriza
Usuario "1" --> "1..*" Vehiculo : recibe
Usuario "1" --> "1..*" SolicitudRepuesto : genera
Reparacion "1" --> "1..*" SolicitudRepuesto : asociada


```

