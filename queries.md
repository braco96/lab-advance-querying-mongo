![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the companies whose name match 'Babelgum'. Retrieve only their `name` field.

<!-- Your Code Goes Here -->
- **query**: `{ "name": "Babelgum" }` // Filtramos por nombre exacto para localizar la empresa.
- **projection**: `{ "name": 1, "_id": 0 }` // Mostramos solo el nombre, ocultando el id.
- **sort**: `{}` // No necesitamos orden específico en esta búsqueda.
- **skip**: `0` // No saltamos documentos.
- **limit**: `0` // Sin límite para traer todas las coincidencias.

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

<!-- Your Code Goes Here -->
- **query**: `{ "number_of_employees": { "$gt": 5000 } }` // Selecciona compañías con más de 5000 empleados.
- **projection**: `{ "name": 1, "number_of_employees": 1, "_id": 0 }` // Mostramos nombre y número de empleados.
- **sort**: `{ "number_of_employees": -1 }` // Ordenamos de mayor a menor cantidad de empleados.
- **skip**: `0` // No omitimos documentos.
- **limit**: `20` // Restringimos el resultado a las 20 primeras compañías.

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fields.

<!-- Your Code Goes Here -->
- **query**: `{ "founded_year": { "$gte": 2000, "$lte": 2005 } }` // Filtramos años de fundación entre 2000 y 2005.
- **projection**: `{ "name": 1, "founded_year": 1, "_id": 0 }` // Mostramos únicamente nombre y año de fundación.
- **sort**: `{}` // Sin ordenamiento adicional.
- **skip**: `0` // No saltamos documentos.
- **limit**: `0` // Sin límite, obtenemos todas las coincidencias.

### 4. All the companies that had a Valuation Amount of more than 100.000.000 and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

<!-- Your Code Goes Here -->
- **query**: `{ "ipo.valuation_amount": { "$gt": 100000000 }, "founded_year": { "$lt": 2010 } }` // Valoraciones mayores a 100M antes de 2010.
- **projection**: `{ "name": 1, "ipo": 1, "_id": 0 }` // Devolvemos nombre y datos del IPO.
- **sort**: `{}` // No se requiere ordenación.
- **skip**: `0` // No se omiten documentos.
- **limit**: `0` // Sin límite para obtener todas las empresas válidas.

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

<!-- Your Code Goes Here -->
- **query**: `{ "number_of_employees": { "$lt": 1000 }, "founded_year": { "$lt": 2005 } }` // Menos de 1000 empleados y fundadas antes de 2005.
- **projection**: `{ "name": 1, "number_of_employees": 1, "_id": 0 }` // Mostramos nombre y empleados.
- **sort**: `{ "number_of_employees": 1 }` // Ordenamos ascendentemente por número de empleados.
- **skip**: `0` // No omitimos resultados.
- **limit**: `10` // Limitamos a las 10 primeras compañías.

### 6. All the companies that don't include the `partners` field.

<!-- Your Code Goes Here -->
- **query**: `{ "partners": { "$exists": false } }` // Buscamos documentos sin el campo partners.
- **projection**: `{ "name": 1, "_id": 0 }` // Solo queremos ver el nombre.
- **sort**: `{}` // Ningún orden requerido.
- **skip**: `0` // No saltamos documentos.
- **limit**: `0` // Sin límite de resultados.

### 7. All the companies that have a null type of value on the `category_code` field.

<!-- Your Code Goes Here -->
- **query**: `{ "category_code": null }` // Filtramos por valores nulos en category_code.
- **projection**: `{ "name": 1, "category_code": 1, "_id": 0 }` // Mostramos nombre y category_code para comprobar el valor.
- **sort**: `{}` // Sin ordenamiento.
- **skip**: `0` // No omitimos documentos.
- **limit**: `0` // Sin límite de búsqueda.

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

<!-- Your Code Goes Here -->
- **query**: `{ "number_of_employees": { "$gte": 100, "$lt": 1000 } }` // Empleados entre 100 y 999.
- **projection**: `{ "name": 1, "number_of_employees": 1, "_id": 0 }` // Solo nombre y número de empleados.
- **sort**: `{}` // No ordenamos.
- **skip**: `0` // No saltamos resultados.
- **limit**: `0` // Sin límite de documentos.

### 9. Order all the companies by their IPO price in a descending order.

<!-- Your Code Goes Here -->
- **query**: `{}` // No filtramos, trabajamos con todas las compañías.
- **projection**: `{ "name": 1, "ipo.valuation_amount": 1, "_id": 0 }` // Mostramos nombre y precio de IPO.
- **sort**: `{ "ipo.valuation_amount": -1 }` // Ordenamos de mayor a menor precio de IPO.
- **skip**: `0` // No omisión.
- **limit**: `0` // Sin límite.

### 10. Retrieve the 10 companies with most employees, order by the `number of employees`

<!-- Your Code Goes Here -->
- **query**: `{}` // Utilizamos todas las compañías.
- **projection**: `{ "name": 1, "number_of_employees": 1, "_id": 0 }` // Mostramos nombre y empleados.
- **sort**: `{ "number_of_employees": -1 }` // Ordenamos de mayor a menor número de empleados.
- **skip**: `0` // Sin saltos.
- **limit**: `10` // Nos quedamos con las 10 primeras.

### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.

<!-- Your Code Goes Here -->
- **query**: `{ "founded_month": { "$gt": 6 } }` // Mes de fundación posterior a junio.
- **projection**: `{ "name": 1, "founded_month": 1, "_id": 0 }` // Mostramos nombre y mes.
- **sort**: `{}` // No se especifica orden.
- **skip**: `0` // No omitimos resultados.
- **limit**: `1000` // Máximo 1000 documentos.

### 12. All the companies founded before 2000 that have an acquisition amount of more than 10.000.000

<!-- Your Code Goes Here -->
- **query**: `{ "founded_year": { "$lt": 2000 }, "acquisition.price_amount": { "$gt": 10000000 } }` // Fundadas antes de 2000 con adquisiciones altas.
- **projection**: `{ "name": 1, "acquisition.price_amount": 1, "_id": 0 }` // Mostramos nombre y monto de adquisición.
- **sort**: `{}` // Sin ordenación adicional.
- **skip**: `0` // No se omiten documentos.
- **limit**: `0` // Sin límite.

### 13. All the companies that have been acquired after 2010, order by the acquisition amount, and retrieve only their `name` and `acquisition` field.

<!-- Your Code Goes Here -->
- **query**: `{ "acquisition.acquired_year": { "$gt": 2010 } }` // Empresas adquiridas después de 2010.
- **projection**: `{ "name": 1, "acquisition": 1, "_id": 0 }` // Mostramos nombre y detalles de adquisición.
- **sort**: `{ "acquisition.price_amount": -1 }` // Ordenamos de mayor a menor monto de adquisición.
- **skip**: `0` // No omitimos resultados.
- **limit**: `0` // Sin límite.

### 14. Order the companies by their `founded year`, retrieving only their `name` and `founded year`.

<!-- Your Code Goes Here -->
- **query**: `{}` // Trabajamos con todas las compañías.
- **projection**: `{ "name": 1, "founded_year": 1, "_id": 0 }` // Solo nombre y año de fundación.
- **sort**: `{ "founded_year": 1 }` // Ordenamos cronológicamente por año de fundación.
- **skip**: `0` // No saltamos documentos.
- **limit**: `0` // Sin límite.

### 15. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `acquisition price` in a descending order. Limit the search to 10 documents.

<!-- Your Code Goes Here -->
- **query**: `{ "founded_day": { "$lte": 7 } }` // Primeros siete días del mes.
- **projection**: `{ "name": 1, "acquisition.price_amount": 1, "_id": 0 }` // Mostramos nombre y precio de adquisición.
- **sort**: `{ "acquisition.price_amount": -1 }` // Ordenamos por precio de adquisición descendente.
- **skip**: `0` // Sin omisión.
- **limit**: `10` // Solo las 10 primeras compañías.

### 16. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascending order.

<!-- Your Code Goes Here -->
- **query**: `{ "category_code": "web", "number_of_employees": { "$gt": 4000 } }` // Categoría web con más de 4000 empleados.
- **projection**: `{ "name": 1, "number_of_employees": 1, "_id": 0 }` // Nombre y número de empleados.
- **sort**: `{ "number_of_employees": 1 }` // Orden ascendente por empleados.
- **skip**: `0` // No saltamos documentos.
- **limit**: `0` // Sin límite.

### 17. All the companies whose acquisition amount is more than 10.000.000, and currency is 'EUR'.

<!-- Your Code Goes Here -->
- **query**: `{ "acquisition.price_amount": { "$gt": 10000000 }, "acquisition.price_currency_code": "EUR" }` // Adquisiciones en euros superiores a 10M.
- **projection**: `{ "name": 1, "acquisition": 1, "_id": 0 }` // Incluimos nombre y detalles de la adquisición.
- **sort**: `{}` // Sin ordenamiento.
- **skip**: `0` // No omitimos documentos.
- **limit**: `0` // Sin límite.

### 18. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.

<!-- Your Code Goes Here -->
- **query**: `{ "acquisition.acquired_month": { "$lte": 3 } }` // Primer trimestre (enero a marzo).
- **projection**: `{ "name": 1, "acquisition": 1, "_id": 0 }` // Solo nombre y adquisición.
- **sort**: `{}` // No se especifica orden.
- **skip**: `0` // No saltamos documentos.
- **limit**: `10` // Limitamos a 10 compañías.

### 19. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

<!-- Your Code Goes Here -->
- **query**: `{ "founded_year": { "$gte": 2000, "$lte": 2010 }, "$or": [ { "acquisition.acquired_year": { "$gte": 2011 } }, { "acquisition": { "$exists": false } } ] }` // Fundadas 2000-2010 y sin adquisición previa a 2011.
- **projection**: `{ "name": 1, "founded_year": 1, "acquisition": 1, "_id": 0 }` // Mostramos nombre, año de fundación y adquisición.
- **sort**: `{}` // Sin orden específico.
- **skip**: `0` // No omitimos resultados.
- **limit**: `0` // Sin límite de documentos.