## CU-03 — Cerrar turno

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** <br>
El usuario debe estar logueado en el sistema. <br>
Debe existir un turno abierto. <br>

**Camino básico:** <br>
1. El usuario indica que desea cerrar el turno abierto. <br>
2. El sistema solicita el monto de efectivo contado en la caja, sin mostrar el efectivo esperado. <br>
3. El usuario cuenta el efectivo, ingresa el monto y confirma. <br>
4. El sistema calcula el efectivo esperado (monto inicial + entradas en efectivo − salidas en efectivo) y la diferencia con el efectivo contado. <br>
5. El sistema muestra el resumen del turno: monto inicial, entradas y salidas por medio de pago, efectivo esperado, efectivo contado y diferencia (faltante o sobrante). <br>
6. El sistema registra el cierre con la hora de cierre y marca el turno como cerrado. <br>

**Caminos alternativos:** <br>
**3.a** El monto ingresado es inválido (negativo o no numérico). <br>
3.a.1 El sistema informa que el monto es inválido. Vuelve al paso 3. <br>

**Escenario de éxito:** el turno queda cerrado con su diferencia de caja registrada. <br>

**Escenario de fracaso:** no aplica; el turno siempre puede cerrarse, aunque exista una diferencia de caja. <br>

**Postcondiciones:** el turno queda cerrado y no admite nuevas operaciones ni modificaciones; la diferencia de caja queda registrada para que la revise el empleador. Se retira todo el efectivo de la caja.
