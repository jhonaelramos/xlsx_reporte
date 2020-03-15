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

La principal diferencia entre este y el programa anterior es que hemos agregado dos objetos de formato que podemos usar para formatear celdas en la hoja de cálculo.

Los objetos de formato representan todas las propiedades de formato que se pueden aplicar a una celda en Excel, como fuentes, formato de números, colores y bordes. Esto se explica con más detalle en la sección The Format Class.

Por ahora evitaremos entrar en detalles y solo usaremos una cantidad limitada de la funcionalidad de formato para agregar un formato simple:

```
# Add a bold format to use to highlight cells.
bold = workbook.add_format({'bold': True})

# Add a number format for cells with money.
dinero = workbook.add_format({'num_format': '$#,##0'})
```

Luego podemos pasar estos formatos como un tercer parámetro opcional al metodo worksheet.write() Método para formatear los datos en la celda:
```
write(row, column, token, [format])
```

Me gusta esto:
```
worksheet.write(row, 0, 'Total', bold)
```

Lo que nos lleva a otra nueva característica en este programa. Para agregar los encabezados en la primera fila de la hoja de trabajo, utilizamos write() Me gusta esto:

```
worksheet.write('A1', 'Item', bold)
worksheet.write('B1', 'Costo', bold)
```

Entonces, en lugar de (row, col) Nosotros usamos el excel 'A1' notación de estilo Ver https://xlsxwriter.readthedocs.io/working_with_cell_notation.html#cell-notation para más detalles, pero no se preocupe demasiado por ahora. Es solo un poco de azúcar sintáctica para ayudar a diseñar las hojas de trabajo.
