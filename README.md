

# [DER](https://github.com/Horacio1991/SQL_Coderhouse/blob/main/DER%20Coder.jpg)


# [SCRIPT](https://github.com/Horacio1991/SQL_Coderhouse/blob/main/PrimerEntrega.sql)


# ENVIOS CODER

Es una aplicación diseñada para facilitar y optimizar el proceso de envío y entrega de paquetes a través de servicios de mensajería y correos. Su objetivo principal es gestionar de manera eficiente todas las etapas del proceso de envío, desde la recepción del paquete hasta su entrega final al destinatario.

## Características Principales

- **Registro de Paquetes**: Permite a los usuarios ingresar los detalles de los paquetes enviados, como el remitente, el destinatario, la descripción y el valor del contenido, así como la fecha de envío y otros detalles relevantes.

- **Asignación de Empleados y Vehículos**: Facilita la asignación de empleados y vehículos para la entrega de paquetes, garantizando una distribución eficiente de los recursos y una gestión óptima de las rutas de entrega.

- **Seguimiento de Envíos**: Proporciona a los usuarios la capacidad de realizar un seguimiento en tiempo real del estado de los envíos, desde su recepción en la sucursal hasta su entrega final al destinatario, brindando actualizaciones sobre la ubicación y el estado de entrega de los paquetes.

- **Gestión de Clientes**: Permite la gestión de la información de los clientes, incluyendo el registro de nuevos clientes, la actualización de datos de contacto y la visualización de los paquetes asociados a cada cliente.

- **Generación de Informes y Análisis**: Ofrece herramientas para generar informes y análisis sobre diferentes aspectos del negocio, como el rendimiento de los empleados, los costos de envío, la satisfacción del cliente y otros indicadores clave de desempeño.

# Descripción de las Tablas

## Tabla **SUCURSAL**

- **Descripción**: Esta tabla almacena información sobre las sucursales.
- **Columnas**:
  - `COD_SUCURSAL`: El identificador único de la sucursal (clave primaria).
  - `DIRECCION`: La dirección de la sucursal.
  - `TELEFONOS`: Los números de teléfono asociados a la sucursal.

## Tabla **EMPLEADO**

- **Descripción**: Almacena datos sobre los empleados.
- **Columnas**:
  - `COD_EMPLEADO`: Identificador único del empleado (clave primaria, autoincremental).
  - `COD_SUCURSAL`: Referencia al código de la sucursal a la que pertenece el empleado.
  - `NOMBRE`: Nombre del empleado (con un valor predeterminado si no se proporciona).
  - `APELLIDO`: Apellido del empleado.
  - `DOMICILIO`: Domicilio del empleado.
  - `TELEFONOS`: Números de teléfono del empleado.

## Tabla **AUTOMOVIL**

- **Descripción**: Almacena información sobre los automóviles.
- **Columnas**:
  - `COD_AUTOMOVIL`: Identificador único del automóvil (clave primaria, autoincremental).
  - `COD_SUCURSAL`: Referencia al código de la sucursal a la que pertenece el automóvil.
  - `COD_EMPLEADO`: Referencia al código del empleado asociado al automóvil.
  - `PATENTE`: Número de patente del automóvil.
  - `MODELO`: Modelo del automóvil.

## Tabla **CLIENTE**

- **Descripción**: Contiene datos sobre los clientes.
- **Columnas**:
  - `COD_CLIENTE`: Identificador único del cliente (clave primaria).
  - `NOMBRE`: Nombre del cliente.
  - `APELLIDO`: Apellido del cliente.
  - `DOMICILIO`: Domicilio del cliente.
  - `TELEFONOS`: Números de teléfono del cliente.

## Tabla **PAQUETE**

- **Descripción**: Almacena detalles sobre los paquetes.
- **Columnas**:
  - `COD_PAQUETE`: Identificador único del paquete (clave primaria).
  - `COD_CLIENTE`: Referencia al código del cliente asociado al paquete.
  - `COD_EMPLEADO`: Referencia al código del empleado responsable del paquete.
  - `FECHA_ENVIO`: Fecha de envío del paquete.
  - `ESTADO`: Estado del paquete (verdadero o falso).

## Tabla **PRODUCTO**

- **Descripción**: Guarda información sobre los productos.
- **Columnas**:
  - `COD_PRODUCTO`: Identificador único del producto (clave primaria).
  - `COD_PAQUETE`: Referencia al código del paquete al que pertenece el producto.
  - `NOMBRE`: Nombre del producto.
  - `DESCRIPCION`: Descripción detallada del producto.
  - `PESO`: Peso del producto (decimal con precisión de 10,2).
  - `PRECIO`: Precio del producto (decimal con precisión de 10,2).
 
### Vista: vista_paquetes_por_cliente
Esta vista muestra información detallada sobre los paquetes enviados por cliente, incluyendo el código del cliente, nombre, apellido, código del paquete, fecha de envío, estado del paquete, así como los productos asociados a cada paquete con su nombre, descripción, peso y precio.

### Vista: vista_empleados_por_sucursal
Esta vista proporciona información sobre los empleados asignados a cada sucursal, mostrando el código de la sucursal, dirección, así como el código, nombre, apellido, domicilio y teléfonos de cada empleado.

### Vista: vista_envios_por_fecha
Esta vista muestra los detalles de los envíos realizados dentro de un rango de fechas específico. Incluye el código del paquete, fecha de envío, código del cliente y empleado, nombre y apellido del cliente y empleado, así como información detallada sobre los productos enviados, como nombre, descripción, peso y precio.

### Función: calcular_total_envios_por_cliente
Esta función calcula el total de envíos realizados por un cliente específico. Recibe como parámetro el código del cliente y devuelve el número total de envíos realizados por ese cliente.

### Función: obtener_productos_por_paquete
Esta función devuelve una lista de productos asociados a un paquete específico. Toma como entrada el código del paquete y devuelve una cadena de caracteres que enumera los nombres de los productos separados por comas.

### Función: calcular_peso_total_paquete
Esta función calcula el peso total de un paquete específico. Recibe como parámetro el código del paquete y devuelve una cadena de caracteres que representa el peso total seguido de las unidades "KG".

### Procedimiento almacenado: sp_actualizar_estado_paquete
Este procedimiento almacenado actualiza el estado de un paquete específico. Toma como entrada el código del paquete y el nuevo estado y actualiza el estado del paquete en la tabla correspondiente.

### Procedimiento almacenado: sp_obtener_envios_por_fecha
Este procedimiento almacenado devuelve detalles sobre los envíos realizados dentro de un rango de fechas específico. Toma como parámetros las fechas de inicio y fin y devuelve información detallada sobre los paquetes enviados dentro de ese período.

### Trigger: tr_estado_paquete
Este trigger se activa después de actualizar el estado de un paquete y registra el cambio en una tabla de registro. Registra el código del paquete, la fecha del cambio, el estado anterior y el estado actual del paquete en la tabla `LOG_CAMBIOS_PAQUETE`.

