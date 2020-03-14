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
workbook = xlsxwriter.Workbook('Expenses01.xlsx')
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
for item, cost in (expenses):
    worksheet.write(row, col,     item)
    worksheet.write(row, col + 1, cost)
    row += 1

# Escribe un total usando una fórmula.
worksheet.write(row, 0, 'Total')
worksheet.write(row, 1, '=SUM(B1:B4)')

workbook.close()
```
