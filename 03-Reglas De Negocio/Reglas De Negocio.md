# Reglas De Negocio

### 1. Hechos<br>
### 01 — Turnos de atención
El negocio se organiza en turno mañana y turno tarde.

### 02 — Medio de pago
Una venta puede ser abonada mediante efectivo o transferencia, o mediante una combinación de ambos dentro de una misma operación.

### 03 — Margen de ganancia
El margen de ganancia aplicado al precio de venta puede variar según el producto.

### 04 — Venta fiada
El negocio vende fiado únicamente a clientes del barrio registrados en el sistema. Cada cliente con fiado posee una cuenta corriente donde se registran los cargos (ventas fiadas) y los pagos que realiza.

### 05 — Pagos sobre la cuenta corriente
El cliente puede cancelar su deuda en forma total o parcial. Los pagos se aplican sobre el saldo total de la cuenta corriente y no sobre una venta fiada en particular.

---

### 2. Restricciones<br>
### 01 — Acceso según rol
Los empleados no podrán realizar las operaciones que sean exclusivas del empleador.

### 02 — Condición para otorgar fiado
No se podrá registrar una venta fiada a un cliente cuya deuda esté excedida (el saldo de su cuenta corriente más el total de la nueva venta supera su límite de crédito) o sea vieja (tiene saldo pendiente y su último pago, o su primera venta fiada si nunca pagó, supera el plazo máximo de deuda). El límite de crédito de cada cliente y el plazo máximo de deuda los define el empleador.

### 03 — Monto máximo de un pago de fiado
El monto de un pago registrado sobre la cuenta corriente no podrá superar el saldo adeudado por el cliente.

---

### 3. Acciones Disparadores<br>
### 01 Actualización de Stock 
Al confirmar una transacción de salida o entrada, se dispara la actualización del inventario en tiempo real. En una venta fiada el stock se descuenta al confirmar la venta, aunque todavía no haya sido abonada.

### 02 — Cargo en cuenta corriente
Al confirmar una venta fiada se genera un cargo por el total de la venta en la cuenta corriente del cliente, y el importe no se incorpora al balance de caja.

### 03 — Pago de fiado
Al registrar un pago sobre la cuenta corriente se reduce el saldo adeudado del cliente y el importe se incorpora al balance de caja del turno en que se cobra.

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
