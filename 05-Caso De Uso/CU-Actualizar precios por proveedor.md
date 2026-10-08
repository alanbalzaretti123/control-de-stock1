## CU-12 — Actualizar precios por proveedor

**Actores:** Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado con rol Empleador y debe existir al menos un proveedor con productos asociados. <br>

**Camino básico:** <br>
1. El empleador indica el proveedor cuyos precios desea actualizar. <br>
2. El sistema muestra los productos activos asociados a ese proveedor con su categoría, precio de costo, margen de ganancia y precio de venta vigentes. <br>
3. El empleador indica que el cambio se aplica a todos los productos mostrados. <br>
4. El empleador ingresa el porcentaje de variación del costo (positivo para un aumento, negativo para una baja). <br>
5. El sistema calcula, para cada producto elegido, el nuevo precio de costo y el nuevo precio de venta según su margen de ganancia, redondeado al múltiplo de $10 superior, y muestra una vista previa con los valores anteriores y los nuevos. <br>
6. El empleador confirma. <br>
7. El sistema actualiza el precio de costo y el precio de venta de los productos elegidos. <br>

**Caminos alternativos:** <br>
**1.a** El proveedor indicado no tiene productos activos asociados. <br>
1.a.1 El sistema informa que el proveedor no tiene productos asociados. Vuelve al paso 1. <br>
**3.a** El empleador indica que el cambio se aplica solo a los productos de una categoría. <br>
3.a.1 El empleador selecciona la categoría. <br>
3.a.2 El sistema muestra solo los productos del proveedor que pertenecen a esa categoría. Continúa en el paso 4. <br>
**3.b** El empleador indica que desea seleccionar los productos uno por uno. <br>
3.b.1 El empleador marca los productos a los que se aplica el cambio. Continúa en el paso 4. <br>
**4.a** El porcentaje ingresado es inválido (cero, menor o igual a −100, o no numérico). <br>
4.a.1 El sistema informa que el porcentaje es inválido. Vuelve al paso 4. <br>
**6.a** El empleador no confirma la vista previa. <br>
6.a.1 El sistema no aplica ningún cambio. Vuelve al paso 3. <br>

**Escenario de éxito:** los productos elegidos quedan con su precio de costo y su precio de venta actualizados, conservando su margen de ganancia. <br>

**Escenario de fracaso:** no se aplica el cambio por no haber productos asociados o por un porcentaje inválido. <br>

**Postcondiciones:** los productos elegidos del proveedor quedan con su precio de costo y su precio de venta actualizados; el margen de ganancia de cada uno no cambia.
