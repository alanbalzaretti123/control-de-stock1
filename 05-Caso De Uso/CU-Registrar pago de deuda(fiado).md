## Caso de uso: Registrar pago de deuda (fiado)

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** el cliente debe tener al menos una factura impaga o pagada parcialmente. <br>

**Camino básico:** <br>
1. El usuario busca al cliente e indica que desea registrar un pago sobre su cuenta de fiado. <br>
2. El sistema muestra las facturas impagas o parcialmente pagadas del cliente, con el saldo pendiente de cada una y el saldo total adeudado. <br>
3. El usuario indica qué facturas desea saldar y el monto total a abonar. <br>
4. El sistema valida que el monto no supere la suma de los saldos pendientes seleccionados y, si es válido, distribuye el monto entre esas facturas (comenzando por la más antigua), actualiza el saldo de cada una —marcándolas como pagadas o pagadas parcial según corresponda— e incorpora el importe al balance de caja del turno. <br>

**Caminos alternativos:** <br>
**4.a** El monto ingresado supera la suma de los saldos pendientes de las facturas seleccionadas. <br>
4.a.1 El sistema informa que el monto supera la deuda seleccionada. Vuelve al paso 3. <br>

**Escenario de éxito:** el pago queda registrado y distribuido entre las facturas seleccionadas, actualizando el saldo del cliente. <br>

**Escenario de fracaso:** el pago no se registra porque el monto ingresado supera la deuda seleccionada. <br>

**Postcondiciones:** el saldo adeudado por el cliente se reduce según el monto pagado; las facturas cuyo saldo llega a cero quedan marcadas como pagadas.