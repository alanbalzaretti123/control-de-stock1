## Caso de uso: Completar costos de ingreso

**Actores:** Empleador (primario). <br>

**Precondiciones:** <br>
El usuario debe estar logueado con rol Empleador. <br>
Debe existir al menos un ingreso de mercadería con costos pendientes. <br>

**Camino básico:** <br>
1. El empleador indica que desea completar los costos de un ingreso de mercadería. <br>
2. El sistema muestra los ingresos con costos pendientes, con su proveedor, fecha e importe total. <br>
3. El empleador selecciona un ingreso. <br>
4. El sistema muestra los productos del ingreso con sus cantidades. <br>
5. El empleador ingresa el costo unitario de cada producto y confirma. <br>
6. El sistema registra los costos del ingreso y actualiza el precio de costo vigente de cada producto. <br>

**Caminos alternativos:** <br>
**5.a** Algún costo ingresado es inválido (negativo o no numérico). <br>
5.a.1 El sistema informa qué costo es inválido. Vuelve al paso 5. <br>
**5.b** La sumatoria de cantidad × costo unitario no coincide con el importe total del remito. <br>
5.b.1 El sistema advierte la diferencia y solicita confirmación. Si el empleador confirma, continúa en el paso 6; si no, vuelve al paso 5. <br>

**Escenario de éxito:** el ingreso queda con todos sus costos completos y los productos con su precio de costo actualizado. <br>

**Escenario de fracaso:** no se registran los costos por haber valores inválidos. <br>

**Postcondiciones:** el ingreso no tiene costos pendientes y el precio de costo vigente de sus productos queda actualizado.
