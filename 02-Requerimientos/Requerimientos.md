# Requerimientos del Sistema (Almacén)

## 1. Requerimientos Funcionales (RF)

1. Requerimientos funcionales

RF-01 —
El sistema permitira al empleador dar de alta, modificar y dar de baja productos.

RF-02 —
El sistema registrará y consultará el código de barras y el precio de venta de cada producto, disponibles para empleados y empleador. El costo de cada producto solo será visible para el empleador.

RF-03 —
El sistema consultara la cantidad disponible de cada producto.

RF-04 —
El sistema permitira a los empleados registrar las ventas realizadas.

RF-05 —
El sistema identificara los productos mediante su código de barras al momento de realizar una venta.

RF-06 —
El sistema permitira consultar cuáles son los productos más vendidos.

RF-07 —
El sistema permitira consultar la cantidad de ventas realizadas en una fecha determinada.

RF-08 —
El sistema permitira consultar el total vendido durante cada turno y el total correspondiente a ambos turnos.

RF-09 —
El sistema permitira consultar balances de caja correspondientes a los turnos y períodos determinados.

RF-10 —
El sistema permitira al empleador registrar y consultar los proveedores del negocio.

RF-11 —
El sistema registrara los pagos realizados a los proveedores por la mercadería adquirida.

RF-12 —
El sistema permitira al empleador generar e imprimir reportes de la información registrada.

RF-13 —
El sistema diferenciara las funcionalidades disponibles para los empleados y el empleador según su rol.

RF-14 —
El sistema permitirá aplicar un aumento de precio masivo a todos los productos asociados a un proveedor determinado.

RF-15 —
El sistema permitirá registrar una venta fiada a un cliente registrado, cargando el total de la venta en su cuenta corriente.

RF-16 —
El sistema permitirá registrar pagos totales o parciales sobre la cuenta corriente de un cliente, reduciendo su saldo adeudado.

RF-17 —
Las ventas fiadas generarán un comprobante con el detalle de productos, cantidades y precios, igual que una venta de contado.

RF-18 —
El stock se descontará al momento de la venta fiada, independientemente de si fue abonada o no.

RF-19 —
El importe de una venta fiada no se incorporará al balance de caja; lo que se incorpora es cada pago que el cliente realice sobre su cuenta corriente, en el turno en que se cobra.

RF-20 —
El sistema permitirá registrar un pago combinado (parte en efectivo, parte en transferencia) para una misma venta.

RF-21 —
El sistema permitirá a empleados y empleador abrir un turno de caja, indicando el tipo de turno (mañana o tarde) y el monto de efectivo con el que inicia la caja.

RF-22 —
El sistema permitirá cerrar el turno abierto registrando el efectivo contado en la caja, calculando el efectivo esperado y registrando la diferencia (faltante o sobrante) entre ambos.

RF-23 —
El sistema permitirá registrar retiros y aportes de dinero en la caja del turno abierto, indicando monto y motivo.

---

## 2. Requerimientos No Funcionales (RNF)
RNF-01 —
El sistema sera intuitivo y fácil de usar.

RNF-02 —
El sistema debe minimizar los errores de carga que generan faltantes o sobrantes de caja al finalizar el turno.

RNF-03 —
El sistema debe responder con rapidez al registrar una venta.

RNF-04 —
El sistema debe ser compatible con un lector de código de barras.

RNF-05 —
	El sistema debe garantizar la persistencia de la información (stock, ventas, balances, fiados) para que no se pierdan datos entre turnos.

---

## 3. Requerimientos de Dominio (RD)

RD-01 —
El margen de ganancia utilizado para determinar el precio de venta podrá variar según el producto.

RD-02 —
Cada cliente con fiado posee una cuenta corriente: las ventas fiadas suman a su saldo adeudado y los pagos lo reducen, sin imputarse a una venta en particular.

