# Reglas De Negocio

### 1. Hechos<br>
### 01 — Turnos de atención
El negocio se organiza en turno mañana y turno tarde. La fecha de un turno es la fecha en que se abrió, aunque el turno termine después de la medianoche; todas las operaciones registradas mientras está abierto pertenecen a esa fecha.

### 02 — Medio de pago
Una venta puede ser abonada mediante efectivo o transferencia, o mediante una combinación de ambos dentro de una misma operación. No se aceptan pagos con tarjeta ni con QR. Una venta también puede quedar fiada (ver hecho 04).

### 03 — Margen de ganancia
El margen de ganancia aplicado al precio de venta puede variar según el producto.

### 04 — Venta fiada
El negocio vende fiado únicamente a clientes del barrio registrados en el sistema. Cada cliente con fiado posee una cuenta corriente donde se registran los cargos (ventas fiadas) y los pagos que realiza.

### 05 — Pagos sobre la cuenta corriente
El cliente puede cancelar su deuda en forma total o parcial. Los pagos se aplican sobre el saldo total de la cuenta corriente y no sobre una venta fiada en particular.

### 06 — Cambio de turno
Al cerrar un turno se retira todo el efectivo de la caja. El turno siguiente inicia con el monto de efectivo que se decida en ese momento.

### 07 — Pago a proveedores
La mercadería recibida puede pagarse en el momento o quedar pendiente. El pago en efectivo se realiza con dinero de la caja; si el efectivo no alcanza, se avisa al empleador y se paga por transferencia. Un ingreso puede pagarse en uno o más pagos.

---

### 2. Restricciones<br>
### 01 — Acceso según rol
Los empleados no podrán realizar las operaciones que sean exclusivas del empleador.

### 02 — Condición para otorgar fiado
Solo se podrá registrar una venta fiada a un cliente habilitado para fiado. No existe un límite de crédito ni un plazo máximo de deuda fijos: el empleador decide a su criterio qué clientes están habilitados, y puede inhabilitar a un cliente, por ejemplo, cuando considera que su deuda es muy vieja o excesiva.

### 03 — Monto máximo de un pago de fiado
El monto de un pago registrado sobre la cuenta corriente no podrá superar el saldo adeudado por el cliente.

### 04 — Un único turno abierto
Solo puede existir un turno abierto a la vez. No se podrá abrir un turno nuevo sin haber cerrado el anterior.

### 05 — Operaciones con turno abierto
No se podrán registrar ventas, pagos de fiado, pagos a proveedores, retiros ni aportes si no hay un turno abierto.

### 06 — Turno cerrado
Una vez cerrado, un turno no puede modificarse ni se le pueden registrar nuevas operaciones.

### 07 — Arqueo ciego
Al cerrar el turno, el usuario debe ingresar el efectivo contado antes de que el sistema le muestre el efectivo esperado.

### 08 — Monto máximo de un pago a proveedor
El monto de un pago asociado a un ingreso de mercadería no podrá superar el saldo pendiente de ese ingreso.

### 09 — Costos de la mercadería
Solo el empleador puede ver y modificar el precio de costo de los productos. El ingreso de mercadería registra productos, cantidades e importe total del remito, sin costos unitarios; el empleador actualiza luego el precio de costo de cada producto desde la gestión de productos.

---

### 3. Acciones Disparadores<br>
### 01 Actualización de Stock 
Al confirmar una transacción de salida o entrada, se dispara la actualización del inventario en tiempo real. En una venta fiada el stock se descuenta al confirmar la venta, aunque todavía no haya sido abonada.

### 02 — Cargo en cuenta corriente
Al confirmar una venta fiada se genera un cargo por el total de la venta en la cuenta corriente del cliente, y el importe no se incorpora al balance de caja.

### 03 — Pago de fiado
Al registrar un pago sobre la cuenta corriente se reduce el saldo adeudado del cliente y el importe se incorpora al balance de caja del turno en que se cobra.

### 04 — Movimiento de caja
Toda entrada o salida de dinero (venta de contado, pago de fiado, pago a proveedor, retiro o aporte) genera un movimiento de caja asociado al turno abierto, con su medio de pago y monto.

### 05 — Cierre de turno
Al cerrar un turno el sistema calcula el efectivo esperado, lo compara con el efectivo contado, registra la diferencia y marca el turno como cerrado.

### 06 — Pago a proveedor
Al registrar un pago a un proveedor se reduce el saldo pendiente del ingreso asociado (si lo hay) y se genera un movimiento de salida de caja en el turno abierto con su medio de pago. Solo los pagos en efectivo reducen el efectivo esperado de la caja.

---

### 4. Cálculos<br>
### 01 — Ganancia bruta por producto
La ganancia bruta obtenida por un producto se determinará a partir de la diferencia entre su precio de venta y su precio de costo.

### 02 — Total de ventas por turno
El total vendido de un turno se calculará como la sumatoria de los importes totales (totalVenta) de todas las ventas registradas durante dicho turno.

### 03 — Total de ventas de un período
El total facturado durante un período se calculará como la sumatoria de los importes totales (totalVenta) de todas las ventas registradas dentro de dicho período.

### 04 — Saldo de la cuenta corriente
El saldo adeudado por un cliente se calculará como la sumatoria de los totales de sus ventas fiadas menos la sumatoria de los pagos que realizó sobre su cuenta corriente.

### 05 — Efectivo esperado del turno
El efectivo esperado al cierre de un turno se calculará como el monto inicial de caja más los movimientos de entrada en efectivo (ventas de contado, pagos de fiado y aportes) menos los movimientos de salida en efectivo (pagos a proveedores y retiros) registrados en ese turno.

### 06 — Diferencia de caja
La diferencia de caja de un turno se calculará como el efectivo contado menos el efectivo esperado. Un valor positivo indica un sobrante y un valor negativo, un faltante.

### 07 — Saldo pendiente de un ingreso de mercadería
El saldo pendiente de un ingreso se calculará como su monto total menos la sumatoria de los pagos al proveedor asociados a ese ingreso.
