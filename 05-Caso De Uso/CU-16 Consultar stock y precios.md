## CU-16 — Consultar stock y precios

**Actores:** Empleado o Empleador (primario). <br>

**Precondiciones:** el usuario debe estar logueado. <br>

**Camino básico:** <br>
1. El usuario ingresa a la consulta de productos, opcionalmente indicando un nombre o código de barras a buscar. <br>
2. El sistema muestra el listado de productos con código de barras, nombre, precio de venta y cantidad disponible en stock, marcando los productos cuyo stock actual es menor o igual a su stock mínimo. <br>

**Caminos alternativos:** <br>
**1.a** La búsqueda no encuentra productos coincidentes. <br>
1.a.1 El sistema informa que no se encontraron productos. Vuelve al paso 1. <br>
**2.a** El usuario tiene rol Empleador. <br>
2.a.1 El sistema muestra además el precio de costo de cada producto. <br>
**2.b** El usuario, con rol Empleador, indica que desea imprimir el listado de stock. <br>
2.b.1 El sistema genera el documento imprimible con el listado mostrado. Fin del caso de uso. <br>

**Escenario de éxito:** el usuario visualiza el stock y los precios habilitados para su rol. <br>

**Escenario de fracaso:** no aplica (una búsqueda sin resultados no es un fracaso del caso de uso). <br>

**Postcondiciones:** ninguna (es una consulta de solo lectura), salvo la generación del documento si se solicitó impresión.