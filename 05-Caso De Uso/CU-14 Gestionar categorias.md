## CU-14 — Gestionar categorías

**Actores:** Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado con rol Empleador. <br>

**Camino básico** (alta de categoría): <br>
1. El empleador indica que desea dar de alta una nueva categoría. <br>
2. El sistema solicita el nombre y, opcionalmente, una descripción. <br>
3. El empleador completa los datos y confirma. <br>
4. El sistema valida que el nombre no esté registrado y, si es válido, da de alta la categoría. <br>

**Caminos alternativos:** <br>
**1.a** El empleador indica que desea modificar una categoría existente. <br>
1.a.1 El sistema muestra los datos actuales de la categoría. <br>
1.a.2 El empleador ingresa los nuevos valores y confirma. <br>
1.a.3 El sistema actualiza la categoría. Fin del caso de uso. <br>
**1.b** El empleador indica que desea eliminar una categoría. <br>
1.b.1 El sistema verifica que la categoría no tenga productos asociados y solicita confirmación. <br>
1.b.2 El empleador confirma. <br>
1.b.3 El sistema elimina la categoría. Fin del caso de uso. <br>
**1.b.1.a** La categoría tiene productos asociados. <br>
El sistema informa que no puede eliminarse mientras tenga productos asociados. Fin del caso de uso. <br>
**4.a** Ya existe una categoría con ese nombre. <br>
4.a.1 El sistema informa que la categoría ya existe. Vuelve al paso 3. <br>

**Escenario de éxito:** la categoría queda dada de alta, modificada o eliminada según la acción elegida. <br>

**Escenario de fracaso:** el alta no se concreta por un nombre duplicado, o la eliminación no se concreta porque la categoría tiene productos asociados. <br>

**Postcondiciones:** el registro de categorías queda actualizado según la acción elegida.
