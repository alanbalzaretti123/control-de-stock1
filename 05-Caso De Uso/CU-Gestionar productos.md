## Caso de uso: Gestionar productos

**Actores:** Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado con rol Empleador. <br>

**Camino básico** (alta de producto): <br>
1. El empleador indica que desea dar de alta un nuevo producto. <br>
2. El sistema solicita código de barras, nombre, descripción (opcional), categoría, proveedor, precio de costo, precio de venta, stock inicial, stock mínimo y fecha de vencimiento (opcional). <br>
3. El empleador completa los datos y confirma. <br>
4. El sistema valida que el código de barras no esté registrado previamente y, si es válido, da de alta el producto en el catálogo. <br>

**Caminos alternativos:** <br>
**1.a** El empleador indica que desea modificar un producto existente. <br>
1.a.1 El sistema muestra los datos actuales del producto y solicita los campos a editar. <br>
1.a.2 El empleador ingresa los nuevos valores y confirma. <br>
1.a.3 El sistema actualiza el producto. Fin del caso de uso. <br>
**1.b** El empleador indica que desea dar de baja un producto existente. <br>
1.b.1 El sistema solicita confirmación. <br>
1.b.2 El empleador confirma. <br>
1.b.3 El sistema marca el producto como inactivo, sin eliminarlo del historial de ventas. Fin del caso de uso. <br>
**4.a** El código de barras ya está registrado en otro producto. <br>
4.a.1 El sistema informa que el código ya existe y no da de alta el producto. Vuelve al paso 3. <br>

<<<<<<< HEAD
**Escenario de éxito:** el producto queda dado de alta, modificado o dado de baja según la acción elegida. <br>
=======
1.El empleador inicia el alta de un nuevo producto.<br>
2.El sistema solicita código de barras, nombre, descripción (opcional), categoría, proveedor, precio de costo, precio de venta, stock inicial, stock mínimo.<br>
3.El empleador completa los datos y confirma.<br>
4.El sistema valida que el código de barras no esté registrado previamente.<br>
5.El sistema da de alta el producto en el catálogo.<br>
>>>>>>> 2363b5be0f0ad71d8cddd85738ed9392a2426829

**Escenario de fracaso:** el alta no se concreta por un código de barras duplicado. <br>

<<<<<<< HEAD
**Postcondiciones:** el catálogo de productos queda actualizado (alta, modificación o baja aplicada).
=======
1.a El empleador elige modificar un producto existente.    1.a.1 El sistema muestra los datos actuales del producto seleccionado.    1.a.2 El empleador edita los campos deseados y confirma.    1.a.3 El sistema actualiza el producto. Fin del caso de uso.

1.b El empleador elige dar de baja un producto existente.    1.b.1 El sistema solicita confirmación.    1.b.2 El empleador confirma.    1.b.3 El sistema marca el producto como inactivo, sin eliminarlo del historial de ventas. Fin del caso de uso.

4.a El código de barras ya está registrado en otro producto.    4.a.1 El sistema muestra el mensaje "código de barras ya registrado". Vuelve al paso 2.

**Escenario de éxito:** el producto queda dado de alta, modificado o dado de baja según la acción elegida.

**Escenario de fracaso:** el alta no se concreta por un código de barras duplicado.
>>>>>>> 2363b5be0f0ad71d8cddd85738ed9392a2426829
