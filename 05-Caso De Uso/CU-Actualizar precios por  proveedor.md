## Caso de uso: Actualizar precios por proveedor

**Actores:** Empleador (primario). <br>

**Precondiciones:** debe existir al menos un proveedor con productos asociados. <br>

**Camino básico:** <br>
1. El empleador indica el proveedor cuyos precios desea actualizar. <br>
2. El sistema muestra los productos asociados a ese proveedor con su precio de venta vigente. <br>
3. El empleador ingresa el porcentaje de aumento a aplicar. <br>
4. El sistema calcula el nuevo precio de venta de cada producto y solicita confirmación. <br>
5. El empleador confirma. <br>
6. El sistema actualiza el precio de venta de todos los productos del proveedor. <br>

**Caminos alternativos:** <br>
**1.a** El proveedor indicado no tiene productos asociados. <br>
1.a.1 El sistema informa que el proveedor no tiene productos asociados. Vuelve al paso 1. <br>
**3.a** El empleador ingresa un porcentaje inválido (negativo o no numérico). <br>
3.a.1 El sistema informa que el porcentaje es inválido. Vuelve al paso 3. <br>

**Escenario de éxito:** los productos del proveedor quedan con el precio actualizado. <br>

**Escenario de fracaso:** no se aplica el aumento por no haber productos asociados o por un porcentaje inválido. <br>

**Postcondiciones:** los productos del proveedor indicado quedan con su precio de venta actualizado.