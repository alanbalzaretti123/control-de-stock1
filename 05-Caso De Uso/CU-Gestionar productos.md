## Caso de uso: Gestionar productos

**Actores:** Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado con rol Empleador. <br>

**Camino básico** (alta de producto): <br>
1. El empleador indica que desea dar de alta un nuevo producto. <br>
2. El sistema solicita código de barras (o código interno si el producto no tiene), nombre, descripción (opcional), categoría, proveedor, unidad de medida (unidad o kilogramo), precio de costo, margen de ganancia, stock inicial y stock mínimo. <br>
3. El empleador completa los datos. <br>
4. El sistema calcula el precio de venta a partir del costo y el margen, redondeado al múltiplo de $10 superior, lo muestra y solicita confirmación. <br>
5. El empleador confirma. <br>
6. El sistema valida que el código de barras no esté registrado previamente y, si es válido, da de alta el producto en el catálogo. <br>

**Caminos alternativos:** <br>
**1.a** El empleador indica que desea modificar un producto existente. <br>
1.a.1 El sistema muestra los datos actuales del producto y solicita los campos a editar (por ejemplo, el precio de costo luego de un ingreso de mercadería, o el stock actual para corregir una diferencia con el stock real). <br>
1.a.2 El empleador ingresa los nuevos valores y confirma. <br>
1.a.3 Si se modificó el precio de costo o el margen, el sistema recalcula el precio de venta y lo muestra para su confirmación (el empleador puede ajustarlo como en 5.a). <br>
1.a.4 El sistema actualiza el producto. Fin del caso de uso. <br>
**1.b** El empleador indica que desea dar de baja un producto existente. <br>
1.b.1 El sistema solicita confirmación. <br>
1.b.2 El empleador confirma. <br>
1.b.3 El sistema marca el producto como inactivo, sin eliminarlo del historial de ventas. Fin del caso de uso. <br>
**5.a** El empleador ajusta manualmente el precio de venta calculado (por ejemplo, para dejar un precio redondo). <br>
5.a.1 El sistema recalcula el margen de ganancia a partir del precio ingresado y lo muestra. Continúa en el paso 6. <br>
**5.b** El precio de venta ingresado es menor al precio de costo. <br>
5.b.1 El sistema advierte que el producto se vendería a pérdida y solicita confirmación. Si el empleador confirma, continúa en el paso 6; si no, vuelve al paso 5. <br>
**6.a** El código de barras ya está registrado en otro producto. <br>
6.a.1 El sistema informa que el código ya existe y no da de alta el producto. Vuelve al paso 3. <br>


**Escenario de éxito:** el producto queda dado de alta, modificado o dado de baja según la acción elegida. <br>

**Escenario de fracaso:** el alta no se concreta por un código de barras duplicado. <br>

**Postcondiciones:** el catálogo de productos queda actualizado (alta, modificación o baja aplicada).
