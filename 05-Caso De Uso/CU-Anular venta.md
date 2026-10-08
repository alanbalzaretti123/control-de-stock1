## Caso de uso: Anular venta

**Actores:** Empleador (primario). <br>

**Precondiciones:** <br>
El usuario debe estar logueado con rol Empleador. <br>
Debe existir un turno de caja abierto. <br>

**Camino básico:** <br>
1. El empleador indica que desea anular una venta e ingresa su número de comprobante. <br>
2. El sistema muestra el detalle de la venta: fecha, productos, cantidades, total, condición (contado o fiado) y medios de pago. <br>
3. El empleador ingresa el motivo de la anulación y confirma. <br>
4. El sistema marca la venta como anulada, registrando la fecha y hora, el usuario y el motivo. <br>
5. El sistema repone el stock de cada producto de la venta. <br>
6. El sistema registra en el turno abierto un movimiento de salida de caja por cada medio de pago con el que se abonó la venta, por el mismo monto. <br>

**Caminos alternativos:** <br>
**1.a** No existe una venta con el número de comprobante ingresado. <br>
1.a.1 El sistema informa que la venta no existe. Vuelve al paso 1. <br>
**2.a** La venta ya está anulada. <br>
2.a.1 El sistema informa que la venta ya fue anulada. Fin del caso de uso. <br>
**6.a** La venta fue fiada. <br>
6.a.1 El sistema verifica que el saldo adeudado por el cliente sea mayor o igual al total de la venta; si lo es, el total de la venta deja de sumar a la cuenta corriente del cliente y no se registra ningún movimiento de caja. Fin del caso de uso. <br>
6.a.2 Si el saldo es menor, el sistema informa que la venta no puede anularse porque el cliente ya pagó parte de ella, y revierte los pasos 4 y 5. Fin del caso de uso. <br>

**Escenario de éxito:** la venta queda anulada, el stock repuesto y su efecto revertido en la caja o en la cuenta corriente del cliente. <br>

**Escenario de fracaso:** la venta no se anula porque no existe, ya estaba anulada, o es una venta fiada que el cliente ya pagó en parte. <br>

**Postcondiciones:** la venta queda registrada como anulada con su motivo y deja de contarse en los totales de ventas; el stock de sus productos queda repuesto; la devolución de dinero queda reflejada en el balance de caja del turno abierto, o el saldo del cliente queda reducido si era fiada.
