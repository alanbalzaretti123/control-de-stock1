## CU-10 — Registrar pago a proveedor

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** <br>
El usuario debe estar logueado en el sistema. <br>
Debe existir un turno de caja abierto. <br>
El proveedor debe estar registrado en el sistema. <br>

**Camino básico:** <br>
1. El usuario indica el proveedor al que desea pagar. <br>
2. El sistema muestra los ingresos de mercadería de ese proveedor con saldo pendiente. <br>
3. El usuario selecciona el ingreso que desea pagar. <br>
4. El usuario ingresa el medio de pago y el monto. <br>
5. El sistema valida que el monto no supere el saldo pendiente del ingreso y solicita confirmación. <br>
6. El usuario confirma. <br>
7. El sistema registra el pago asociado al ingreso, reduce su saldo pendiente y registra un movimiento de salida de caja en el turno abierto con ese medio de pago. <br>

**Caminos alternativos:** <br>
**2.a** El proveedor no tiene ingresos con saldo pendiente, o el pago no corresponde a un ingreso registrado. <br>
2.a.1 El usuario ingresa el concepto del pago. Continúa en el paso 4. <br>
**4.a** El usuario indica que el pago se realiza combinando efectivo y transferencia, ingresando el monto de cada uno. <br>
4.a.1 El sistema registra un pago por cada medio de pago. Continúa en el paso 5. <br>
**5.a** El monto supera el saldo pendiente del ingreso. <br>
5.a.1 El sistema informa que el monto supera lo adeudado por ese ingreso. Vuelve al paso 4. <br>
**5.b** El monto en efectivo supera el efectivo esperado en la caja del turno. <br>
5.b.1 El sistema advierte que el efectivo de la caja no alcanza y sugiere avisar al empleador para pagar por transferencia o dejar el pago pendiente. Vuelve al paso 4. <br>

**Escenario de éxito:** el pago queda registrado y reflejado en el balance de caja del turno. <br>

**Escenario de fracaso:** el pago no se registra porque el monto supera el saldo pendiente o el efectivo de la caja no alcanza. <br>

**Postcondiciones:** el pago queda registrado; si está asociado a un ingreso, el saldo pendiente de ese ingreso se reduce; la salida de dinero queda incluida en el balance de caja del turno abierto.
