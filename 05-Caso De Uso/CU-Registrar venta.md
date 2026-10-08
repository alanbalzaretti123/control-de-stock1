## Caso de uso: Registrar venta

**Actores:** Empleado o Empleador (primario).

**Precondiciones:**<br>
- El usuario debe estar logueado en el sistema.<br>
- Debe existir un turno de caja abierto.<br>

**Camino básico:**<br>
1. El usuario ingresa el código de barras de cada producto que desea vender.<br>
2. Por cada producto ingresado, el sistema lo busca y valida el stock disponible.<br>
3. El usuario indica que finalizó la carga de productos.<br>
4. El sistema calcula el total de la venta.<br>
5. El usuario indica el medio de pago.<br>
6. El sistema registra el pago, descuenta el stock de cada producto vendido, genera el comprobante y registra un movimiento de caja por cada medio de pago en el turno abierto.

**Caminos alternativos:**<br>
**1.a** El producto no tiene código de barras.<br>
  1.a.1 El usuario busca el producto por nombre o ingresa su código interno.<br>
  1.a.2 El sistema muestra los productos que coinciden y el usuario selecciona el que desea vender. Continúa en el paso 2.<br>
**2.a** El código de barras ingresado no corresponde a ningún producto registrado.<br>
  2.a.1 El sistema informa que el producto no fue encontrado y no agrega ninguna línea por ese código. Vuelve al paso 1.<br>
**2.b** El producto no tiene stock suficiente para la cantidad solicitada.<br>
  2.b.1 El sistema agrega la línea igual, dejando el stock del producto en cero o negativo, y registra un aviso de diferencia de stock para que el empleador lo revise más adelante.<br>
**2.c** El producto se vende por kilogramo.<br>
  2.c.1 El sistema solicita el peso vendido.<br>
  2.c.2 El usuario ingresa el peso en kilogramos (por ejemplo, 0,250).<br>
  2.c.3 El sistema calcula el subtotal como el peso por el precio por kilogramo y agrega la línea a la venta. Vuelve al paso 1.<br>
**5.a** El usuario indica que la venta es fiada e indica el cliente correspondiente.<br>
  5.a.1 El sistema muestra el saldo adeudado del cliente y verifica que esté habilitado para fiado; si está inhabilitado, informa que no puede otorgarse el fiado y finaliza sin registrar la venta; caso contrario, descuenta el stock, genera un cargo por el total de la venta en la cuenta corriente del cliente y no incorpora el importe al balance de caja. Fin del caso de uso.<br>
**5.a.a** El cliente no está registrado en el sistema.<br>
  5.a.a.1 El usuario da de alta al cliente mediante el caso de uso Gestionar clientes. Continúa en el paso 5.a.1.<br>
**5.b** El usuario indica que el pago se realiza combinando más de un medio de pago, ingresando el monto correspondiente a cada uno.<br>
  5.b.1 El sistema valida que la suma de los montos ingresados sea igual al total de la venta. Continúa en el paso 6.<br>

**Escenario de éxito:** la venta queda registrada, el stock se actualiza y el importe se refleja en el balance de caja del turno (o queda pendiente de cobro si fue fiada).

**Escenario de fracaso:** la venta no se concreta porque el cliente está inhabilitado para fiado (la falta de stock ya no impide la venta, solo genera un aviso a revisar).

**Postcondiciones:**<br>
- El stock de los productos vendidos queda descontado.<br>
- Se genera un registro de venta (comprobante) asociado al turno correspondiente.<br>
- Si la venta fue abonada (total o parcialmente) al momento, el importe se incorpora al balance de caja del turno. Si fue fiada, se genera un cargo en la cuenta corriente del cliente y el importe no se incorpora al balance de caja hasta que el cliente pague.