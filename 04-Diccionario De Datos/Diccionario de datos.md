# Diccionario de Datos - STOCKIFY

Listado organizado con las definiciones precisas y rigurosas de los datos del sistema de control de stock del almacén. Describe el significado de cada almacenamiento, de sus datos elementales y de las relaciones entre componentes, siguiendo la notación de la metodología estructurada.

---

## Notación

| Símbolo | Relación | Significado |
| :--- | :--- | :--- |
| `=` | Definición | "está compuesto de". |
| `+` | Secuencial | Componentes que siempre están presentes. |
| `[ \| ]` | Selección | Alternativas; solo se elige una. |
| `vi{ }vf` | Repetición | El componente se itera entre vi y vf veces. |
| `( )` | Opcional | El componente puede estar o no (repetición 0{ }1). |
| `@` | Identificador | Campo que no se repite ni admite nulos (clave primaria). Si una estructura tiene más de un campo con `@`, la clave primaria es compuesta: la combinación de esos campos no se repite. |

---

## Almacenamientos

Usuario = @nombreUsuario + contraseña + nombreCompleto + rol + estadoUsuario

Categoria = @nombreCategoria + (descripcionCategoria)

Proveedor = @cuit + razonSocial + (telefono) + (email) + (direccion) + estadoProveedor

Producto = @codigoBarras + nombreProducto + (descripcionProducto) + nombreCategoria + cuit + precioCosto + precioVenta + stockActual + stockMinimo + (fechaVencimiento) + estadoProducto

Cliente = @idCliente + nombreCliente + apellidoCliente + (telefono) + limiteCredito + saldoDeuda

Turno = @fechaTurno + @tipoTurno + nombreUsuario + horaApertura + (horaCierre) + montoInicialCaja + (montoContado) + (diferenciaCaja) + estadoTurno

Venta = @numeroComprobante + fechaVenta + fechaTurno + tipoTurno + nombreUsuario + condicionVenta + (idCliente) + 1{DetalleVenta}n + 0{DetallePago}n + totalVenta + estadoVenta

DetalleVenta = @numeroComprobante + @codigoBarras + cantidad + precioUnitario + costoUnitario + subtotal

DetallePago = @numeroComprobante + @medioPago + monto

MovimientoCaja = @numeroMovimiento + fechaTurno + tipoTurno + nombreUsuario + fechaHoraMovimiento + tipoMovimiento + medioPago + monto + (numeroComprobante) + (numeroRecibo) + (idPagoProveedor) + (motivo)

PagoFiado = @numeroRecibo + idCliente + fechaPago + fechaTurno + tipoTurno + nombreUsuario + 1{MedioPagoFiado}n + montoTotal

MedioPagoFiado = @numeroRecibo + @medioPago + monto

IngresoMercaderia = @idIngreso + cuit + (numeroRemito) + fechaIngreso + nombreUsuario + 1{DetalleIngreso}n + medioPago + montoTotal

DetalleIngreso = @idIngreso + @codigoBarras + cantidad + costoUnitario

PagoProveedor = @idPagoProveedor + cuit + fechaPago + monto + (concepto)

---

## Estructuras con relación de selección

Dato elemental cuyo valor se elige de un conjunto cerrado de alternativas:

    rol = [ Empleador | Empleado ]
    tipoTurno = [ mañana | tarde ]
    medioPago = [ efectivo | transferencia ]
    estado = [ activo | inactivo ]
    estadoVenta = [ confirmada | anulada ]
    condicionVenta = [ contado | fiado ]
    estadoTurno = [ abierto | cerrado ]
    tipoMovimiento = [ venta | pagoFiado | pagoProveedor | retiro | aporte ]

---

## Datos elementales

Mínimas unidades indivisibles de datos, con su nombre, descripción, longitud, tipo y dominio de valores admisibles.

| Nombre | Descripción | Longitud | Tipo | Dominio |
| :--- | :--- | :---: | :--- | :--- |
| nombreUsuario | Nombre de acceso al sistema (único). | 30 | Alfanumérico | Texto libre |
| contraseña | Contraseña almacenada cifrada (hash). | 255 | Alfanumérico | Texto libre |
| nombreCompleto | Nombre y apellido del usuario. | 80 | Alfanumérico | Texto libre |
| rol | Rol del usuario dentro del sistema, determina las funcionalidades habilitadas. | 15 | Alfanumérico | Discreto: {(D, Empleador); (E, Empleado)} |
| nombreCategoria | Nombre del rubro/categoría del producto (ej.: comestibles, limpieza). | 50 | Alfanumérico | Texto libre |
| descripcionCategoria | Descripción de la categoría. | 150 | Alfanumérico | Texto libre |
| cuit | CUIT del proveedor, utilizado como identificador del mismo. | 13 | Alfanumérico | Formato XX-XXXXXXXX-X |
| razonSocial | Razón social del proveedor. | 100 | Alfanumérico | Texto libre |
| telefono | Teléfono de contacto (proveedor o cliente). | 30 | Numérico | Texto libre |
| email | Correo electrónico de contacto del proveedor. | 80 | Alfanumérico | Texto libre |
| calle | Nombre de la calle del domicilio. | 80 | Alfanumérico | Texto libre |
| numero | Número o altura del domicilio. | 10 | Alfanumérico | Texto libre |
| codigoPostal | Código postal del domicilio. | 8 | Alfanumérico | Texto libre |
| localidad | Localidad del domicilio. | 50 | Alfanumérico | Texto libre |
| codigoBarras | Código de barras del producto, utilizado como identificador del mismo. Identifica una combinación específica de marca y presentación. Se guarda como texto para no perder los ceros a la izquierda y admitir códigos de distinta longitud (EAN-8, UPC-12, EAN-13 o códigos internos). | 20 | Alfanumérico | Solo dígitos |
| nombreProducto | Nombre del producto. | 100 | Alfanumérico | Texto libre |
| descripcionProducto | Descripción del producto. | 200 | Alfanumérico | Texto libre |
| precioCosto | Costo de adquisición vigente del producto. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| precioVenta | Precio de venta vigente del producto al público. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| stockActual | Cantidad disponible en inventario. | — | Numérico (entero) | Continuo: {vi: 0; vf: n} |
| stockMinimo | Umbral mínimo que dispara la alerta de reposición. | — | Numérico (entero) | Continuo: {vi: 0; vf: n} |
| fechaVencimiento | Fecha de vencimiento del producto, cuando corresponda. | — | Fecha | Fecha válida, posterior a la fecha de ingreso del producto |
| idCliente | Número que identifica al cliente con cuenta de fiado; lo asigna el sistema al registrarlo. | — | Numérico (entero) | Continuo: {vi: 1; vf: n} |
| nombreCliente | Nombre del cliente con cuenta de fiado. | 50 | Alfanumérico | Texto libre |
| apellidoCliente | Apellido del cliente con cuenta de fiado. | 50 | Alfanumérico | Texto libre |
| limiteCredito | Monto máximo que el cliente puede adeudar en su cuenta corriente; lo define el empleador. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| saldoDeuda | Saldo actual de la cuenta corriente del cliente (ventas fiadas menos pagos realizados). | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| fechaTurno | Fecha en la que se abrió el turno. Si el turno termina después de la medianoche, sus operaciones conservan esta fecha. | — | Fecha | Fecha válida, no posterior a la fecha actual |
| tipoTurno | Franja horaria del turno. | 10 | Alfanumérico | Discreto: {(M, mañana); (T, tarde)} |
| montoInicialCaja | Monto de efectivo con el que inicia la caja, decidido al abrir el turno. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| horaApertura | Hora en la que se abrió el turno. | — | Hora | Hora válida |
| horaCierre | Hora en la que se cerró el turno; vacía mientras el turno está abierto. | — | Hora | Hora válida |
| montoContado | Efectivo contado en la caja al cerrar el turno (arqueo). | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| diferenciaCaja | Efectivo contado menos efectivo esperado al cierre: positivo es sobrante, negativo es faltante. | 12,2 | Numérico (decimal) | Continuo: {vi: -n; vf: n} |
| estadoTurno | Indica si el turno está abierto (admite operaciones) o cerrado. | — | Alfanumérico | Dominio {(A, abierto); (C, cerrado)} |
| numeroMovimiento | Número que identifica un movimiento de caja. | — | Numérico (entero) | Continuo: {vi: 1; vf: n} |
| fechaHoraMovimiento | Fecha y hora en que se registró el movimiento de caja. | — | Fecha/Hora | Fecha y hora válida, no posterior al momento actual |
| tipoMovimiento | Origen del movimiento de caja. Venta, pago de fiado y aporte son entradas; pago a proveedor y retiro son salidas. | 15 | Alfanumérico | Dominio {(V, venta); (F, pagoFiado); (P, pagoProveedor); (R, retiro); (A, aporte)} |
| motivo | Motivo de un retiro o aporte de dinero. | 150 | Alfanumérico | Texto libre |
| numeroComprobante | Número de comprobante/ticket asociado a una venta. | — | Numérico (entero) | Continuo: {vi: 1; vf: n} |
| fechaVenta | Fecha y hora de la venta. | — | Fecha/Hora | Fecha y hora válida, no posterior al momento actual |
| condicionVenta | Indica si la venta se abonó en el momento (contado) o se cargó a la cuenta corriente del cliente (fiado). | — | Alfanumérico | Dominio {(C, contado); (F, fiado)} |
| totalVenta | Importe total de la venta. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| cantidad | Cantidad de unidades vendidas o ingresadas del producto. | — | Numérico (entero) | Continuo: {vi: 1; vf: n} |
| precioUnitario | Precio unitario de venta del producto al momento de la operación. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| costoUnitario | Costo unitario del producto al momento de la operación (venta o ingreso). | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| subtotal | Subtotal de la línea (cantidad x precioUnitario). | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| medioPago | Medio de pago utilizado para abonar una venta, un pago de fiado o un ingreso de mercadería. | 15 | Alfanumérico | Discreto: {(E, efectivo); (T, transferencia)} |
| fechaPago | Fecha en la que se realizó un pago a un proveedor o un pago de fiado. | — | Fecha | Fecha válida, no posterior a la fecha actual |
| numeroRecibo | Número de recibo entregado al cliente al registrar un pago sobre su cuenta corriente. | — | Numérico (entero) | Continuo: {vi: 1; vf: n} |
| idIngreso | Número que identifica un ingreso de mercadería; lo asigna el sistema. | — | Numérico (entero) | Continuo: {vi: 1; vf: n} |
| numeroRemito | Número del remito entregado por el proveedor junto con la mercadería, cuando lo hay (ej.: 0001-00012345). | 20 | Alfanumérico | Texto libre |
| idPagoProveedor | Número que identifica un pago realizado a un proveedor; lo asigna el sistema. | — | Numérico (entero) | Continuo: {vi: 1; vf: n} |
| fechaIngreso | Fecha en la que se recibió la mercadería. | — | Fecha | Fecha válida, no posterior a la fecha actual |
| montoTotal | Importe total abonado por un ingreso de mercadería o por un pago de fiado. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| monto | Importe abonado a un proveedor, correspondiente a una línea de pago de una venta o de un fiado, o de un movimiento de caja. | 12,2 | Numérico (decimal) | Continuo: {vi: 0; vf: n} |
| concepto | Detalle o motivo del pago realizado al proveedor. | 150 | Alfanumérico | Texto libre |
| estadoUsuario | Indica si el usuario puede acceder al sistema (activo) o fue dado de baja, por ejemplo al dejar de trabajar en el negocio (inactivo). | — | Booleano | Dominio {(1, activo); (0, inactivo)} |
| estadoProveedor | Indica si al proveedor se le siguen realizando pedidos y pagos (activo) o se dejó de operar con él (inactivo). | — | Booleano | Dominio {(1, activo); (0, inactivo)} |
| estadoProducto | Indica si el producto se sigue comercializando y puede venderse (activo) o fue discontinuado del catálogo (inactivo), sin borrarse del historial de ventas pasadas. | — | Booleano | Dominio {(1, activo); (0, inactivo)} |
| estadoVenta | Estado de la venta: confirmada o anulada. La deuda de una venta fiada no se controla por venta sino en la cuenta corriente del cliente. | — | Alfanumérico | Dominio {(C, confirmada); (A, anulada)} |
