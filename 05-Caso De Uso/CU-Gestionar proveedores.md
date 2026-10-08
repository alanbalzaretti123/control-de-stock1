## CU-11 — Gestionar proveedores

**Actores:** Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado con rol Empleador. <br>

**Camino básico** (alta de proveedor): <br>
1. El empleador indica que desea dar de alta un nuevo proveedor. <br>
2. El sistema solicita CUIT y razón social, y opcionalmente teléfono, email y dirección. <br>
3. El empleador completa los datos y confirma. <br>
4. El sistema valida que el CUIT no esté registrado previamente y, si es válido, da de alta al proveedor. <br>

**Caminos alternativos:** <br>
**1.a** El empleador indica que desea modificar un proveedor existente. <br>
1.a.1 El sistema muestra los datos actuales del proveedor. <br>
1.a.2 El empleador ingresa los nuevos valores y confirma. <br>
1.a.3 El sistema actualiza el proveedor. Fin del caso de uso. <br>
**1.b** El empleador indica que desea dar de baja un proveedor existente. <br>
1.b.1 El sistema verifica si el proveedor tiene productos activos asociados; en tal caso, advierte al empleador y solicita confirmación antes de continuar. <br>
1.b.2 El empleador confirma la baja. <br>
1.b.3 El sistema marca al proveedor como inactivo. Fin del caso de uso. <br>
**1.c** El empleador indica que desea consultar el listado de proveedores. <br>
1.c.1 El sistema muestra el listado de proveedores registrados junto con los productos asociados a cada uno. Fin del caso de uso. <br>
**4.a** El CUIT ya está registrado en otro proveedor. <br>
4.a.1 El sistema informa que el CUIT ya existe y no da de alta al proveedor. Vuelve al paso 3. <br>

**Escenario de éxito:** el proveedor queda dado de alta, modificado, dado de baja, o se obtiene el listado consultado. <br>

**Escenario de fracaso:** el alta no se concreta por un CUIT duplicado. <br>

**Postcondiciones:** el registro de proveedores queda actualizado (según la acción elegida), o no se modifica en caso de una consulta.