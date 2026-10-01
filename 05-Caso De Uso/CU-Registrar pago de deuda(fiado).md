## Caso de uso: Registrar pago de deuda (fiado)

**Actores:** Empleado o Empleador (primario).

**Precondiciones:** el cliente debe tener un saldo adeudado mayor a cero.

**Camino básico:**
1. El usuario busca al cliente por nombre y apellido e indica que desea registrar un pago sobre su cuenta corriente.<br>
2. El sistema muestra el saldo total adeudado por el cliente.<br>
3. El usuario ingresa el medio de pago y el monto a abonar.<br>
4. El sistema valida que el monto no supere el saldo adeudado y, si es válido, registra el pago, reduce el saldo del cliente e incorpora el importe al balance de caja del turno.<br>

**Caminos alternativos:**<br>
**3.a** El usuario indica que el pago se realiza combinando más de un medio de pago, ingresando el monto correspondiente a cada uno.<br>
  3.a.1 El sistema valida que la suma de los montos ingresados sea igual al monto total a abonar. Continúa en el paso 4.<br>
**4.a** El monto ingresado supera el saldo adeudado por el cliente.<br>
  4.a.1 El sistema informa que el monto supera la deuda del cliente. Vuelve al paso 3.<br>

**Escenario de éxito:** el pago queda registrado y el saldo adeudado del cliente se reduce en ese importe.<br>

**Escenario de fracaso:** el pago no se registra porque el monto ingresado supera la deuda del cliente.<br>

**Postcondiciones:** el saldo adeudado por el cliente se reduce según el monto pagado; si el pago cubre la totalidad de la deuda, el saldo queda en cero. El pago no queda vinculado a ninguna venta en particular — el cliente salda su cuenta corriente en conjunto, sin importar de qué compras provino la deuda.<br>