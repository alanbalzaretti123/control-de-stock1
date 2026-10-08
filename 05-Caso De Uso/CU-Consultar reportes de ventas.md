## CU-18 — Consultar reportes de ventas

**Actores:** Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado con rol Empleador. <br>

**Camino básico:** <br>
1. El empleador indica el tipo de reporte que desea consultar (productos más vendidos, cantidad de ventas, o total vendido por turno) y el filtro correspondiente: fecha desde y fecha hasta para los productos más vendidos y la cantidad de ventas (pueden coincidir para consultar un único día), o el turno para el total por turno. <br>
2. El sistema calcula y muestra el resultado: para productos más vendidos, el nombre y la cantidad total vendida de cada producto en el período indicado; para cantidad de ventas, la cantidad de ventas no anuladas realizadas en el período indicado; para total por turno, el total vendido en efectivo, el total por transferencia y el total general de ese turno. <br>

**Caminos alternativos:** <br>
**2.a** No hay datos para el filtro solicitado. <br>
2.a.1 El sistema informa que no hay datos para el período seleccionado. <br>
**2.b** El empleador indica que desea imprimir el reporte mostrado. <br>
2.b.1 El sistema genera el documento imprimible. Fin del caso de uso. <br>

**Escenario de éxito:** el empleador obtiene el reporte solicitado, con el detalle correspondiente a su tipo, opcionalmente impreso. <br>

**Escenario de fracaso:** no hay datos disponibles para el filtro solicitado. <br>

**Postcondiciones:** ninguna (es una consulta), salvo la generación del documento si se solicitó impresión.
