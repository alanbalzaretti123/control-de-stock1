## Caso de uso: Consultar productos a reponer

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado. <br>

**Camino básico:** <br>
1. El usuario indica que desea consultar los productos a reponer, opcionalmente filtrando por proveedor o por categoría. <br>
2. El sistema muestra los productos activos cuyo stock actual es menor o igual a su stock mínimo, agrupados por proveedor, con su nombre, stock actual, stock mínimo y unidad de medida. <br>

**Caminos alternativos:** <br>
**2.a** No hay productos a reponer para el filtro indicado. <br>
2.a.1 El sistema informa que no hay productos a reponer. Fin del caso de uso. <br>
**2.b** El usuario indica que desea imprimir la lista. <br>
2.b.1 El sistema genera el documento imprimible con la lista mostrada. Fin del caso de uso. <br>

**Escenario de éxito:** el usuario obtiene la lista de productos a reponer, opcionalmente impresa. <br>

**Escenario de fracaso:** no aplica (que no haya productos a reponer no es un fracaso del caso de uso). <br>

**Postcondiciones:** ninguna (es una consulta), salvo la generación del documento si se solicitó impresión.
