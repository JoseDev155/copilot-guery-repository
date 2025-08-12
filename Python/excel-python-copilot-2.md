¡Perfecto! Vamos a modificar el código para que puedas ingresar los datos a través de la consola y generar filas en el archivo de Excel. Utilizaremos un bucle para solicitar al usuario que ingrese los datos, y terminaremos la entrada cuando el usuario lo desee.

### Código Modificado para Ingresar Datos por Consola

```python
from openpyxl import Workbook

# Crear un nuevo libro de Excel
wb = Workbook()

# Seleccionar la hoja activa (predeterminada)
ws = wb.active

# Escribir los encabezados
ws['A1'] = 'Nombre'
ws['B1'] = 'Edad'

# Función para solicitar datos desde la consola
def ingresar_datos():
    fila = 2  # Comenzar en la segunda fila
    while True:
        nombre = input("Ingrese el nombre (o 'salir' para terminar): ")
        if nombre.lower() == 'salir':
            break
        edad = input("Ingrese la edad: ")
        
        # Agregar los datos a la hoja de cálculo
        ws[f'A{fila}'] = nombre
        ws[f'B{fila}'] = int(edad)
        
        fila += 1

# Llamar a la función para ingresar datos
ingresar_datos()

# Guardar el archivo de Excel
wb.save('datos_ingresados.xlsx')

print("Archivo de Excel 'datos_ingresados.xlsx' creado con éxito.")
```

### Explicación del Código

1. **Importar la Biblioteca**: 
   ```python
   from openpyxl import Workbook
   ```
   Importa la clase `Workbook` de la biblioteca `openpyxl`.

2. **Crear un Nuevo Libro de Excel**:
   ```python
   wb = Workbook()
   ```
   Crea una nueva instancia de `Workbook`, que representa un nuevo libro de Excel.

3. **Seleccionar la Hoja Activa**:
   ```python
   ws = wb.active
   ```
   Selecciona la hoja activa predeterminada en el libro de Excel.

4. **Escribir Encabezados**:
   ```python
   ws['A1'] = 'Nombre'
   ws['B1'] = 'Edad'
   ```
   Escribe los encabezados en las primeras celdas de la hoja.

5. **Función para Solicitar Datos**:
   ```python
   def ingresar_datos():
       fila = 2  # Comenzar en la segunda fila
       while True:
           nombre = input("Ingrese el nombre (o 'salir' para terminar): ")
           if nombre.lower() == 'salir':
               break
           edad = input("Ingrese la edad: ")
           
           ws[f'A{fila}'] = nombre
           ws[f'B{fila}'] = int(edad)
           
           fila += 1
   ```
   Esta función solicita al usuario que ingrese el nombre y la edad. Los datos se agregan a la hoja de cálculo y se pasa a la siguiente fila. El bucle termina cuando el usuario ingresa "salir".

6. **Llamar a la Función para Ingresar Datos**:
   ```python
   ingresar_datos()
   ```
   Llama a la función `ingresar_datos` para comenzar a solicitar datos del usuario.

7. **Guardar el Archivo de Excel**:
   ```python
   wb.save('datos_ingresados.xlsx')
   ```
   Guarda el libro de Excel en un archivo llamado `datos_ingresados.xlsx`.

### Resultado

Ejecutar este código te permitirá ingresar nombres y edades desde la consola. Los datos se agregarán al archivo de Excel `datos_ingresados.xlsx`.

Espero que esto te sea útil. Si tienes más preguntas o necesitas más detalles, ¡házmelo saber! 😊🚀
