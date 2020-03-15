# Tutorial 2: Agregar formato al archivo XLSX

En la sección anterior creamos una hoja de cálculo simple usando Python y el módulo XlsxWriter.
Esto convirtió los datos requeridos en un archivo de Excel pero parecía un poco desnudo

Para aclarar la información, nos gustaría agregar un formato simple..

Las diferencias aquí son que hemos agregado encabezados de columna Artículo y Costo en negrita, hemos formateado la moneda en la segunda columna y hemos marcado la cadena Total en negrita.
Para hacer esto, podemos extender nuestro programa de la siguiente manera:

```
 import xlsxwriter

 # Cree un libro de trabajo y agregue una hoja de trabajo.
 workbook = xlsxwriter.Workbook('gastos.xlsx')
 worksheet = workbook.add_worksheet()

 # Agregue un formato en negrita para usar para resaltar celdas.
 bold = workbook.add_format({'bold': True})

 # Agregue un formato de número para celdas con dinero.
 money = workbook.add_format({'num_format': '$#,##0'})

 # Escribe algunos encabezados de datos.


 worksheet.write('A1', 'Item', bold)
 worksheet.write('B1', 'Costo', bold)

 # Algunos datos que queremos escribir en la hoja de trabajo.
 gastos = (
     ['Alquilar', 1000],
     ['Gas',   100],
     ['Comida',  300],
     ['Gimnasio',    50],
 )

 # Comience desde la primera celda debajo de los encabezados.
 row = 1
 col = 0

 # Iterar sobre los datos y escribirlos fila por fila.
 for item, costo in (gastos):
     worksheet.write(row, col,     item)
     worksheet.write(row, col + 1, costo, dinero)
     row += 1

 # Escribe un total usando una fórmula.
 worksheet.write(row, 0, 'Total',       bold)
 worksheet.write(row, 1, '=SUM(B2:B5)', dinero)

 workbook.close()
```
