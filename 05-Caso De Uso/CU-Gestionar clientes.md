## Caso de uso: Gestionar clientes

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado. El alta de clientes puede realizarla cualquier usuario; la modificación, la habilitación o inhabilitación y la consulta de la cuenta corriente solo el Empleador. <br>

**Camino básico** (alta de cliente): <br>
1. El usuario indica que desea dar de alta un nuevo cliente para fiado. <br>
2. El sistema solicita nombre, apellido y, opcionalmente, teléfono. <br>
3. El usuario completa los datos y confirma. <br>
4. El sistema da de alta al cliente, habilitado para fiado y con saldo adeudado en cero. <br>

**Caminos alternativos:** <br>
**1.a** El empleador indica que desea modificar los datos de un cliente. <br>
1.a.1 El sistema muestra los datos actuales del cliente. <br>
1.a.2 El empleador ingresa los nuevos valores y confirma. <br>
1.a.3 El sistema actualiza el cliente. Fin del caso de uso. <br>
**1.b** El empleador indica que desea habilitar o inhabilitar a un cliente para fiado. <br>
1.b.1 El sistema muestra el estado actual del cliente y su saldo adeudado, y solicita confirmación del cambio. <br>
1.b.2 El empleador confirma. <br>
1.b.3 El sistema actualiza el estado del cliente. Fin del caso de uso. <br>
**1.c** El empleador indica que desea consultar la cuenta corriente de un cliente. <br>
1.c.1 El sistema muestra el saldo adeudado del cliente y el detalle de sus ventas fiadas y pagos realizados, ordenados por fecha. Fin del caso de uso. <br>
**3.a** Ya existe un cliente registrado con el mismo nombre y apellido. <br>
3.a.1 El sistema advierte la coincidencia y muestra los datos del cliente existente. <br>
3.a.2 El usuario confirma que se trata de otra persona. Continúa en el paso 4. Si no confirma, finaliza sin dar de alta al cliente. <br>

**Escenario de éxito:** el cliente queda dado de alta, modificado, habilitado o inhabilitado, o se obtiene su cuenta corriente, según la acción elegida. <br>

**Escenario de fracaso:** el alta no se concreta porque el cliente ya estaba registrado. <br>

**Postcondiciones:** el registro de clientes queda actualizado según la acción elegida, o no se modifica en caso de una consulta.
