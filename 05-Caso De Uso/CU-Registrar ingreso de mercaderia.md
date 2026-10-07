## Caso de uso: Registrar ingreso de mercadería

**Actores:** Empleado o Empleador (primario), Proveedor (secundario). <br>

**Precondiciones:** el proveedor debe estar registrado en el sistema. Si el pago se realiza en el momento desde la caja, debe existir un turno de caja abierto. <br>

**Camino básico:** <br>
1. El usuario indica el proveedor, el número de remito, y carga cada producto recibido con su cantidad y costo unitario. <br>
2. El sistema actualiza el stock y el precio de costo vigente de cada producto cargado. <br>
3. El usuario indica si el pago se realiza en el momento (efectivo o transferencia) o si queda pendiente. <br>
4. Si el pago es en el momento, el sistema registra un movimiento de salida de caja en el turno abierto; si el pago queda pendiente, registra el ingreso sin asociarle un pago inmediato. <br>

**Caminos alternativos:** <br>
**3.a** La caja no cuenta con dinero suficiente en efectivo para pagar en el momento. <br>
3.a.1 El sistema sugiere realizar el pago por transferencia. Vuelve al paso 3. <br>

**Escenario de éxito:** el stock queda actualizado con la mercadería recibida, y el pago (si corresponde) queda reflejado en caja. <br>

**Escenario de fracaso:** no aplica — el ingreso de mercadería se registra igual aunque el pago quede pendiente. <br>

**Postcondiciones:** el stock de los productos ingresados aumenta según la cantidad recibida; si se realizó el pago en el momento, el egreso queda reflejado en el balance de caja del turno correspondiente.