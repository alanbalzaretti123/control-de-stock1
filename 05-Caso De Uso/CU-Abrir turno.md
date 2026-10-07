## Caso de uso: Abrir turno

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** <br>
El usuario debe estar logueado en el sistema. <br>
No debe existir otro turno abierto. <br>

**Camino básico:** <br>
1. El usuario indica que desea abrir un turno. <br>
2. El sistema solicita el tipo de turno (mañana o tarde) y el monto de efectivo con el que inicia la caja. <br>
3. El usuario ingresa el tipo de turno y el monto inicial y confirma. <br>
4. El sistema registra el turno como abierto, con la fecha y hora de apertura y el usuario responsable. <br>

**Caminos alternativos:** <br>
**1.a** Ya existe un turno abierto. <br>
1.a.1 El sistema informa que debe cerrarse el turno abierto antes de abrir uno nuevo. Fin del caso de uso. <br>
**3.a** El monto inicial ingresado es inválido (negativo o no numérico). <br>
3.a.1 El sistema informa que el monto es inválido. Vuelve al paso 3. <br>
**3.b** Ya existe un turno del mismo tipo en la fecha actual. <br>
3.b.1 El sistema informa que ese turno ya fue registrado. Vuelve al paso 3. <br>

**Escenario de éxito:** el turno queda abierto y se pueden registrar operaciones de caja. <br>

**Escenario de fracaso:** el turno no se abre porque ya hay un turno abierto o porque ese turno ya fue registrado en la fecha. <br>

**Postcondiciones:** existe un turno abierto con su monto inicial de caja; la fecha del turno es la fecha de apertura.
