## Caso de uso: Registrar ingreso de mercadería

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** el proveedor debe estar registrado en el sistema. Si el pago se realiza en el momento, debe existir un turno de caja abierto. <br>

**Camino básico:** <br>
1. El usuario indica el proveedor y el número de remito (si lo hay), y carga cada producto recibido con su cantidad y costo unitario. <br>
2. El sistema calcula el monto total del ingreso (sumatoria de cantidad × costo unitario) y solicita confirmación. <br>
3. El usuario confirma el ingreso. <br>
4. El sistema registra el ingreso, actualiza el stock y el precio de costo vigente de cada producto cargado. <br>
5. El usuario indica que el pago se realiza en el momento. <br>
6. Se ejecuta el caso de uso Registrar pago a proveedor para el ingreso registrado. <br>

**Caminos alternativos:** <br>
**5.a** El usuario indica que el pago queda pendiente. <br>
5.a.1 El sistema deja el ingreso con saldo pendiente igual a su monto total, para pagarlo más adelante mediante el caso de uso Registrar pago a proveedor. Fin del caso de uso. <br>

**Escenario de éxito:** el stock queda actualizado con la mercadería recibida, y el pago queda registrado o pendiente según lo indicado. <br>

**Escenario de fracaso:** no aplica — el ingreso de mercadería se registra igual aunque el pago quede pendiente. <br>

**Postcondiciones:** el stock de los productos ingresados aumenta según la cantidad recibida y su precio de costo queda actualizado; el ingreso queda registrado con su monto total y su saldo pendiente.
