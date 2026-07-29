# Concesionario-examen
El diseño de la base de datos para el concesionario de vehículos se realizó siguiendo principios de normalización y escalabilidad, con el objetivo de garantizar la integridad de los datos y facilitar futuras ampliaciones del sistema.

Se definieron las entidades principales: Vehículo, Cliente, Vendedor, Venta y Mantenimiento, ya que representan los elementos fundamentales del negocio. Cada entidad contiene atributos relevantes que permiten almacenar información detallada y precisa.

La entidad Vehículo utiliza el VIN como clave primaria debido a que es un identificador único. Además, se incluye un atributo de disponibilidad que permite gestionar el inventario en tiempo real.
Para gestionar las ventas, se creó la entidad Venta, la cual se relaciona con Cliente y Vendedor mediante claves foráneas, permitiendo identificar quién realizó la compra y quién la gestionó.
Dado que una venta puede incluir uno o varios vehículos, se implementó una relación muchos a muchos entre Venta y Vehículo, resuelta mediante la tabla intermedia VentaVehiculo. Esta decisión evita redundancias y mantiene la consistencia del modelo.

La entidad Mantenimiento permite registrar servicios realizados a los vehículos, incluso si no han sido vendidos. Por esta razón, la relación con Cliente es opcional, permitiendo flexibilidad en el registro de servicios.

El diseño general cumple con las formas normales básicas, evitando redundancia de datos y asegurando consistencia en las relaciones entre entidades.
La base de datos implementa diversas restricciones para garantizar la integridad de los datos:

    • Claves primarias (PK): Cada tabla posee una clave primaria única que identifica cada registro.
    
    • Claves foráneas (FK): Se utilizan para mantener la integridad referencial entre las tablas, asegurando que las relaciones sean válidas.
    
    • Restricción de unicidad: El atributo VIN en la tabla Vehículo es único, evitando duplicidad de vehículos en el sistema. 
    
    • Restricciones de dominio: Se definen valores válidos para atributos como método de pago, tipo de servicio y estado del vehículo.
    
    • Disponibilidad del vehículo: Cuando un vehículo es vendido, su atributo “disponible” debe actualizarse automáticamente a “no disponible”.
    
    • Integridad referencial: No se puede registrar una venta sin un cliente o vendedor válido.
    
    • Relación opcional: En la entidad Mantenimiento, el cliente puede ser nulo, permitiendo registrar servicios antes de la venta del vehículo.
    

El modelo UML establece las siguientes relaciones entre entidades:

    • Cliente a Venta: Relación uno a muchos (1:N), ya que un cliente puede realizar múltiples compras, pero cada venta pertenece a un solo cliente.
    
    • Vendedor a Venta: Relación uno a muchos (1:N), debido a que un vendedor puede gestionar múltiples ventas.
    
    • Venta a Vehículo: Relación muchos a muchos (N:M), resuelta mediante la tabla intermedia VentaVehiculo, ya que una venta puede incluir varios vehículos y un vehículo podría estar asociado a muchas ventas.
    
    • Vehículo a Mantenimiento: Relación uno a muchos (1:N), permitiendo que un vehículo tenga múltiples registros de mantenimiento.
    
    • Cliente a Mantenimiento: Relación uno a muchos (1:N) opcional, ya que un cliente puede solicitar múltiples servicios, pero no todos los mantenimientos requieren un cliente asociado.
    

Estas relaciones permiten representar de manera clara y estructurada la lógica del negocio del concesionario, facilitando tanto el almacenamiento como la consulta eficiente de la información
