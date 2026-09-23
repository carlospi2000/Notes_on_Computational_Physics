# Semana 3 — Lectura de archivos y mínimos cuadrados en Fortran

Material de trabajo para el curso **Física Computacional — 106018C**.

## Objetivo

Implementar en Fortran 2008 un ajuste lineal por mínimos cuadrados para estimar la aceleración de la gravedad a partir de mediciones de un péndulo simple.

El flujo de trabajo será:

```text
Datos originales en Excel
        ↓
Limpieza y documentación con Python
        ↓
pendulo_limpio.dat
        ↓
Lectura y ajuste lineal en Fortran
        ↓
Cálculo de g y R²
        ↓
Visualización e interpretación
```

## Archivos suministrados

### `Semana_03_MinimosCuadrados_Fortran-4.ipynb`

Notebook principal de la actividad. Está diseñado para ejecutarse en Google Colab e incluye:

* ciclos en Fortran;
* lectura de archivos con `open`, `read`, `iostat` y `close`;
* teoría del método de mínimos cuadrados;
* ejemplos completos;
* ejercicios para completar;
* instrucciones de la tarea;
* visualización en Python;
* verificación final PASS/FAIL.

### `100_mediciones_pendulo_minimos_cuadrados.xlsx`

Archivo con las 100 mediciones originales del experimento.

Los datos deben revisarse antes de realizar el ajuste. Algunas mediciones contienen errores de registro, datos faltantes, duplicados o condiciones que no satisfacen la aproximación de ángulo pequeño.

### `script_limpieza_pendulo_estudiantes.py`

Script de Python para documentar y ejecutar la limpieza de los datos.

Los estudiantes deben completar:

1. El ángulo máximo aceptado para la aproximación de ángulo pequeño.
2. Las correcciones justificadas.
3. Las exclusiones que requieren interpretación experimental.

El script debe generar:

```text
pendulo_limpio.dat
informe_limpieza.xlsx
```

## Cómo comenzar

1. Descargue los tres archivos del repositorio.

2. Abra [Google Colab](https://colab.research.google.com/).

3. Seleccione **Archivo → Subir notebook**.

4. Cargue:

```text
Semana_03_MinimosCuadrados_Fortran-4.ipynb
```

5. Ejecute las celdas del notebook en orden.

6. Cuando el notebook lo solicite, cargue:

```text
100_mediciones_pendulo_minimos_cuadrados.xlsx
script_limpieza_pendulo_estudiantes.py
```

## Programa en Fortran

El programa principal de la tarea debe llamarse:

```text
ajuste_pendulo.f90
```

Para compilarlo y ejecutarlo:

```bash
gfortran -std=f2008 -Wall -Wextra -fcheck=all \
-o ajuste_pendulo ajuste_pendulo.f90

./ajuste_pendulo
```

El programa debe:

* leer `pendulo_limpio.dat`;
* procesar un número desconocido de filas;
* convertir las longitudes de centímetros a metros;
* calcular el período de cada medición;
* ajustar \(T^2=aL+b\);
* calcular la pendiente, el intercepto y \(R^2\);
* estimar

$$
g=\frac{4\pi^2}{a};
$$

* generar `resultados_ajuste.dat`.

## Formato de `resultados_ajuste.dat`

El archivo debe contener una sola fila, sin encabezado, con los valores:

```text
N  a  b  R2  g
```

## Consideraciones importantes

* No modifique directamente los datos originales del archivo Excel.
* Toda corrección o exclusión debe quedar documentada.
* No excluya una medición únicamente porque se aleja de la tendencia.
* Un número de oscilaciones diferente de 10 no implica que la medición sea inválida.
* Convierta la longitud a metros antes de calcular \(g\).
* El ajuste por mínimos cuadrados debe realizarse en Fortran.
* Python debe utilizarse para la limpieza y la visualización.
* Todos los programas deben incluir comentarios que expliquen sus secciones y las líneas más importantes.
* Cada estudiante debe poder explicar su código y justificar sus decisiones.

## Entregables

Cada estudiante debe entregar:

```text
informe_limpieza.xlsx
pendulo_limpio.dat
ajuste_pendulo.f90
resultados_ajuste.dat
ajuste_pendulo_y_residuos.png
informe.pdf
```

También debe presentar la salida del programa con los valores de:

* número de mediciones \(N\);
* pendiente \(a\);
* intercepto \(b\);
* coeficiente \(R^2\);
* aceleración de la gravedad \(g\).

## Verificación final

Antes de entregar:

1. Compile el programa con las opciones indicadas.
2. Ejecute la celda PASS/FAIL del notebook.
3. Compruebe que todos los archivos solicitados hayan sido generados.
4. Incluya el resumen PASS/FAIL en el informe.
5. Verifique que puede explicar el funcionamiento de cada ciclo y acumulador.

## Uso de inteligencia artificial

El uso de herramientas de inteligencia artificial debe declararse en el informe, indicando:

* la herramienta utilizada;
* el propósito de su uso;
* cómo se verificaron las respuestas o el código generado.

El estudiante continúa siendo responsable de comprender y poder explicar todo el código entregado.
