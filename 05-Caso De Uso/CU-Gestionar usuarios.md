## CU-15 — Gestionar usuarios

**Actores:** Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado con rol Empleador. <br>

**Camino básico** (alta de usuario): <br>
1. El empleador indica que desea dar de alta un nuevo usuario. <br>
2. El sistema solicita nombre de usuario, nombre completo, rol (empleador o empleado) y una contraseña inicial. <br>
3. El empleador completa los datos y confirma. <br>
4. El sistema valida que el nombre de usuario no esté registrado y, si es válido, da de alta al usuario en estado activo. <br>

**Caminos alternativos:** <br>
**1.a** El empleador indica que desea modificar un usuario existente. <br>
1.a.1 El sistema muestra los datos actuales del usuario (nombre completo y rol). El nombre de usuario no puede modificarse. <br>
1.a.2 El empleador ingresa los nuevos valores y confirma. <br>
1.a.3 El sistema actualiza el usuario. Fin del caso de uso. <br>
**1.b** El empleador indica que desea restablecer la contraseña de un usuario (por ejemplo, porque la olvidó). <br>
1.b.1 El empleador ingresa una nueva contraseña y confirma. <br>
1.b.2 El sistema actualiza la contraseña del usuario. Fin del caso de uso. <br>
**1.c** El empleador indica que desea dar de baja un usuario (por ejemplo, porque dejó de trabajar en el negocio). <br>
1.c.1 El sistema solicita confirmación. <br>
1.c.2 El empleador confirma. <br>
1.c.3 El sistema marca al usuario como inactivo, sin eliminar las operaciones que registró. Fin del caso de uso. <br>
**1.d** El empleador indica que desea reactivar un usuario dado de baja. <br>
1.d.1 El sistema marca al usuario como activo. Fin del caso de uso. <br>
**1.a.2.a / 1.c.2.a** El cambio dejaría al sistema sin ningún usuario Empleador activo. <br>
El sistema informa que debe existir al menos un empleador activo y no aplica el cambio. Fin del caso de uso. <br>
**4.a** El nombre de usuario ya está registrado. <br>
4.a.1 El sistema informa que el nombre de usuario ya existe. Vuelve al paso 3. <br>

**Escenario de éxito:** el usuario queda dado de alta, modificado, con su contraseña restablecida, dado de baja o reactivado según la acción elegida. <br>

**Escenario de fracaso:** el alta no se concreta por un nombre de usuario duplicado, o el cambio no se aplica porque dejaría al sistema sin empleador activo. <br>

**Postcondiciones:** el registro de usuarios queda actualizado según la acción elegida.
