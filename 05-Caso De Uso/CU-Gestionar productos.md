## Caso de uso: Gestionar productos

**Actores:** Empleador (primario).

**Precondiciones:** el usuario debe estar logueado con rol Empleador.

**Postcondiciones:** el catálogo de productos queda actualizado (alta, modificación o baja aplicada).

**Camino básico** (alta de producto):

1.El empleador inicia el alta de un nuevo producto.<br>
2.El sistema solicita código de barras, nombre, descripción (opcional), categoría, proveedor, precio de costo, precio de venta, stock inicial, stock mínimo.<br>
3.El empleador completa los datos y confirma.<br>
4.El sistema valida que el código de barras no esté registrado previamente.<br>
5.El sistema da de alta el producto en el catálogo.<br>

**Caminos alternativos:**

1.a El empleador elige modificar un producto existente.    1.a.1 El sistema muestra los datos actuales del producto seleccionado.    1.a.2 El empleador edita los campos deseados y confirma.    1.a.3 El sistema actualiza el producto. Fin del caso de uso.

1.b El empleador elige dar de baja un producto existente.    1.b.1 El sistema solicita confirmación.    1.b.2 El empleador confirma.    1.b.3 El sistema marca el producto como inactivo, sin eliminarlo del historial de ventas. Fin del caso de uso.

4.a El código de barras ya está registrado en otro producto.    4.a.1 El sistema muestra el mensaje "código de barras ya registrado". Vuelve al paso 2.

**Escenario de éxito:** el producto queda dado de alta, modificado o dado de baja según la acción elegida.

**Escenario de fracaso:** el alta no se concreta por un código de barras duplicado.
