# Crear archivos de Excel con Python y XlsxWriter

XlsxWriter es un módulo de Python para crear archivos Excel XLSX.

## Tutorial 1: crear un archivo XLSX simple

Comencemos creando una hoja de cálculo simple usando Python y el módulo XlsxWriter.
Supongamos que tenemos algunos datos sobre gastos mensuales que queremos convertir en un archivo Excel XLSX:

```
gastos = (
    ['Alquilar', 1000],
    ['Gas',   100],
    ['Comida',  300],
    ['Gimnasio',    50],
)
```
Para hacerlo, podemos comenzar con un pequeño programa como el siguiente:
```
import xlsxwriter

# Cree un libro de trabajo y agregue una hoja de trabajo.
workbook = xlsxwriter.Workbook('gastos01.xlsx')
worksheet = workbook.add_worksheet()

# Algunos datos que queremos escribir en la hoja de trabajo.
gastos = (
    ['Alquilar', 1000],
    ['Gas',   100],
    ['Comida',  300],
    ['Gimnasio',    50],
)

# Comience desde la primera celda. Las filas y columnas están indexadas a cero.
row = 0
col = 0

# Iterar sobre los datos y escribirlos fila por fila.
for item, costo in (gastos):
    worksheet.write(row, col,     item)
    worksheet.write(row, col + 1, costo)
    row += 1

# Escribe un total usando una fórmula.
worksheet.write(row, 0, 'Total')
worksheet.write(row, 1, '=SUM(B1:B4)')

workbook.close()
```
Este es un ejemplo simple, pero los pasos involucrados son representativos de todos los programas que usan XlsxWriter, así que vamos a dividirlo en partes separadas.

El primer paso es importar el módulo:

```
import xlsxwriter
```

El siguiente paso es crear un nuevo objeto de libro de trabajo utilizando el constructor Workbook ().
Workbook () toma un argumento, no opcional, que es el nombre de archivo que queremos crear:
```
workbook = xlsxwriter.Workbook('gastos01.xlsx')
```

**Nota**
XlsxWriter solo puede crear archivos nuevos. No puede leer ni modificar archivos existentes.
El  objeto workbook se usa para agregar una nueva hoja de trabajo a través del método add_worksheet ():

```
worksheet = workbook.add_worksheet()
```

Por defecto, los nombres de las hojas de trabajo en la hoja de cálculo serán Sheet1, Sheet2 etc., pero también podemos especificar un nombre:
```
worksheet1 = workbook.add_worksheet()        # Defaults to Sheet1.
worksheet2 = workbook.add_worksheet('Data')  # Data.
worksheet3 = workbook.add_worksheet()        # Defaults to Sheet3.
```

Luego podemos usar el objeto de la hoja de trabajo para escribir datos a través del metodo  write()

**Nota**
En XlsxWriter, las filas y columnas están indexadas a cero. La primera celda de una hoja de trabajo, A1, es (0, 0).

Entonces, en nuestro ejemplo, iteramos sobre nuestros datos y los escribimos de la siguiente manera:
```
# Iterar sobre los datos y escribirlos fila por fila.
for item, costo in (gastos):
    worksheet.write(row, col,     item)
    worksheet.write(row, col + 1, cost)
    row += 1
```
Luego agregamos una fórmula para calcular el total de los elementos en la segunda columna:
```
worksheet.write(row, 1, '=SUM(B1:B4)')
```
Finalmente, cerramos el archivo de Excel a través del metodo close()
```
workbook.close()
```

Y eso es. Ahora tenemos un archivo que puede leer Excel y otras aplicaciones de hoja de cálculo.





