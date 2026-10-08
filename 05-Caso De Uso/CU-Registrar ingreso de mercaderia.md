## Caso de uso: Registrar ingreso de mercadería

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** el proveedor debe estar registrado en el sistema. Si el pago se realiza en el momento, debe existir un turno de caja abierto. <br>

**Camino básico:** <br>
1. El usuario indica el proveedor y el número de remito (si lo hay), carga cada producto recibido con su cantidad e ingresa el importe total del remito. <br>
2. El sistema muestra el resumen del ingreso y solicita confirmación. <br>
3. El usuario confirma el ingreso. <br>
4. El sistema registra el ingreso, actualiza el stock de cada producto cargado y deja los costos unitarios pendientes de completar por el empleador. <br>
5. El usuario indica que el pago se realiza en el momento. <br>
6. Se ejecuta el caso de uso Registrar pago a proveedor para el ingreso registrado. <br>

**Caminos alternativos:** <br>
**1.a** El usuario tiene rol Empleador. <br>
1.a.1 El sistema permite cargar además el costo unitario de cada producto. En el paso 4, el sistema actualiza también el precio de costo vigente de cada producto y el ingreso no queda con costos pendientes. Continúa en el paso 2. <br>
**5.a** El usuario indica que el pago queda pendiente. <br>
5.a.1 El sistema deja el ingreso con saldo pendiente igual a su importe total, para pagarlo más adelante mediante el caso de uso Registrar pago a proveedor. Fin del caso de uso. <br>

**Escenario de éxito:** el stock queda actualizado con la mercadería recibida, y el pago queda registrado o pendiente según lo indicado. <br>

**Escenario de fracaso:** no aplica — el ingreso de mercadería se registra igual aunque el pago quede pendiente. <br>

**Postcondiciones:** el stock de los productos ingresados aumenta según la cantidad recibida; el ingreso queda registrado con su importe total y su saldo pendiente; si lo registró un empleado, los costos unitarios quedan pendientes de completar.
