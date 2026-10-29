# Semana 7 — Arreglos: integración y derivación numérica

**Física Computacional — 106018C** · Capítulo 3: Arreglos y memoria dinámica · Fortran y Python

## Contenido

| Archivo | Descripción |
|---|---|
| `slides.pdf` | Láminas de la clase |
| `Arreglos_int_deriv_ESTUDIANTES-7.ipynb` | Notebook de trabajo: ejemplos, ejercicios de calentamiento y Taller 7 |

## Temas

1. **Arreglos en Fortran:** declaración, límites, `allocatable`, secciones, `-fcheck=bounds` y arreglos como argumentos.
2. **Listas y arreglos en Python:** listas frente a arreglos de NumPy, índices base 0 frente a base 1, copias y vistas.
3. **Integración (Fortran):** trapecio, Simpson, extrapolación de Richardson e integración de Romberg.
4. **Derivación (Python):** diferencias adelantada, atrasada, central y de cinco puntos, segunda derivada, paso óptimo y datos tabulados.

## Cómo usar el notebook

Se puede abrir en Google Colab o en Jupyter local. Los programas de Fortran se escriben con `%%writefile` y se compilan con `gfortran` desde el mismo notebook. Para comprobarlo:

```bash
gfortran --version
```

Compile siempre con `-fcheck=bounds` mientras desarrolla.

## Ejercicios de calentamiento (no calificados)

1. Regla de Simpson con secciones de arreglo (Fortran).
2. Derivadas sobre una tabla de cinco puntos (Python).

Cada ejercicio indica los valores que se deben obtener. Conviene resolverlos antes de empezar el taller.

## Taller 7

**Problema:** oscilador amortiguado $x(t) = e^{-\gamma t}\cos(\omega t)$, y el valor de $\pi$.

| Parte | Lenguaje | Tarea |
|---|---|---|
| B | Fortran | Módulo de integración de Romberg; energía disipada en 3 s, comparada con $E(0) - E(T)$ |
| C | Python | Velocidad y aceleración a partir de las posiciones, con cinco fórmulas de diferencias finitas |
| D | Fortran | El mismo módulo, sin cambios, para $\pi = \int_0^1 \frac{4}{1+x^2}\,dx$; comparación con Monte Carlo |

**Entrega**

- Código en la carpeta `taller_oscilador_romberg/` de su repositorio, con los nombres de archivo que indica el notebook.
- Pseudocódigo marco de Romberg con sus tres espacios completos.
- Reporte de una página (plantilla del curso) en Moodle, con el enlace a la carpeta del repositorio.
- La celda de verificación del notebook debe dar **4 de 4 PASS**.

No se permiten funciones de biblioteca que integren o deriven (`np.gradient`, `np.trapz`, `scipy.integrate`, etc.).

## Referencias

- S. J. Chapman, *Fortran for Scientists and Engineers*, 4.ª ed., McGraw-Hill, 2018, caps. 8 y 9.
- M. T. Heath, *Scientific Computing: An Introductory Survey*, 2.ª ed. revisada, SIAM, 2018, cap. 8.
- R. H. Landau, M. J. Páez y C. C. Bordeianu, *Computational Physics: Problem Solving with Python*, 4.ª ed., Wiley.
