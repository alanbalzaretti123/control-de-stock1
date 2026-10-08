## CU-04 — Registrar movimiento de caja

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** <br>
El usuario debe estar logueado en el sistema. <br>
Debe existir un turno abierto. <br>

**Camino básico:** <br>
1. El usuario indica que desea registrar un retiro o un aporte de dinero en la caja. <br>
2. El sistema solicita el tipo de movimiento (retiro o aporte), el monto y el motivo. <br>
3. El usuario ingresa los datos y confirma. <br>
4. El sistema registra el movimiento de caja en efectivo asociado al turno abierto y al usuario. <br>

**Caminos alternativos:** <br>
**3.a** El monto ingresado es inválido (cero, negativo o no numérico). <br>
3.a.1 El sistema informa que el monto es inválido. Vuelve al paso 3. <br>

**Escenario de éxito:** el movimiento queda registrado y se tiene en cuenta en el efectivo esperado del turno. <br>

**Escenario de fracaso:** no se registra el movimiento por un monto inválido. <br>

**Postcondiciones:** el movimiento queda registrado en el turno abierto e incluido en el balance de caja.
