## CU-01 — Iniciar sesión

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** <br>
El usuario debe tener un nombre de usuario y contraseña registrados en el sistema. <br>
El usuario debe estar en estado activo (no dado de baja). <br>

**Camino básico:** <br>
1. El usuario ingresa su nombre de usuario y contraseña. <br>
2. El sistema valida las credenciales, identifica el rol del usuario y habilita las funcionalidades correspondientes a ese rol. <br>

**Caminos alternativos:** <br>
**2.a** El nombre de usuario no existe o la contraseña es incorrecta. <br>
2.a.1 El sistema informa que las credenciales son incorrectas. Vuelve al paso 1. <br>
**2.b** El usuario existe pero está dado de baja (inactivo). <br>
2.b.1 El sistema informa que el usuario está inactivo y que debe contactar al empleador. No permite continuar. <br>

**Escenario de éxito:** el usuario accede al sistema con las funcionalidades habilitadas según su rol. <br>

**Escenario de fracaso:** el usuario no puede acceder por ingresar credenciales incorrectas o por tener su cuenta dada de baja. <br>

**Postcondiciones:** el usuario queda autenticado en el sistema, con acceso a las funcionalidades habilitadas según su rol, hasta que cierre sesión. Al cerrar sesión, el sistema vuelve a solicitar usuario y contraseña.