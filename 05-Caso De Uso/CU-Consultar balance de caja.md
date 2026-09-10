**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** debe existir al menos un turno registrado en el período consultado. <br>

**Camino básico:** <br>
1. El usuario indica el turno (mañana o tarde) de una fecha puntual, o un rango de días, que desea consultar. <br>
2. El sistema muestra el monto inicial de caja, el total de ventas y el detalle de cada operación realizada en el período indicado. <br>

**Caminos alternativos:** <br>
**1.a** No existen operaciones registradas para el período indicado. <br>
1.a.1 El sistema informa que no hay movimientos registrados en el período seleccionado. <br>
**2.a** El usuario tiene rol Empleador. <br>
2.a.1 El sistema muestra además el costo de la mercadería vendida y la ganancia bruta del período. <br>
**2.b** El usuario, con rol Empleador, indica que desea imprimir el balance. <br>
2.b.1 El sistema genera el documento imprimible. Fin del caso de uso. <br>

**Escenario de éxito:** el usuario visualiza el balance con el nivel de detalle habilitado para su rol. <br>

**Escenario de fracaso:** no hay movimientos registrados para el período consultado. <br>

**Postcondiciones:** ninguna (es una consulta), salvo la generación del documento si se solicitó impresión.