Semana 5 — Método de Monte Carlo

Física Computacional — 106018C · Cálculo: Fortran · Gráficas y verificación: Python

En esta semana se usan números aleatorios para calcular: el área de un círculo (y con ella $\pi$), una integral en una dimensión y el error estadístico de esas estimaciones. Es la continuación directa de la Semana 4: el mismo generador, el mismo cambio de intervalo $x = A + (B-A)\,u$ y los mismos acumuladores, ahora al servicio de un cálculo.

Archivos
Archivo	Contenido
Semana_05_MonteCarlo_ESTUDIANTES.ipynb	Ejemplos guiados (secciones 0–5) y Taller 5 con sus plantillas.
Semana_05_MonteCarlo.pdf	Láminas de la clase.
Contenido del notebook
Sección	Tema
0	Preparación de Colab e instalación de gfortran.
1	Generador de Fortran: random_number y random_seed.
2	Cálculo de $\pi$ por acierto y error.
3	Error estadístico: $\sigma_{\hat\pi} = 1.642/\sqrt{N}$.
4	Integración por el método de valor medio.
5	Efecto de un generador deficiente: el LCG $(57, 1, 256)$.
Anexo A	Teorema central del límite (opcional).

Ejecute los ejemplos en orden antes de empezar el Taller: el Taller se apoya en las fórmulas y los programas de esas secciones.

Taller 5 — Cálculo de $\pi$ y convergencia
Parte	Programa	Qué debe obtener
A	taller5_pi.f90	La media y la desviación estándar de $\hat\pi$ en 20 corridas, para $N = 10^2, \ldots, 10^7$, y la pendiente de $\log_{10} s$ contra $\log_{10} N$.
B	taller5_seno.f90	$\int_0^{\pi/2} \sin x\,dx$ por valor medio y por acierto y error, con la media y la desviación de cada método en 1000 repeticiones.
C	taller5_lcg.f90	$\hat\pi$ con coordenadas tomadas del LCG $(57, 1, 256)$ en lugar de random_number.
D	—	Respuestas a las preguntas de interpretación, en el notebook.

Cada programa trae bloques TODO que describen qué debe obtener, no cómo programarlo. Mientras estén vacíos, el programa compila y escribe el valor provisional −1.

Flujo de trabajo
Complete los bloques TODO de un programa.
Ejecute su celda %%writefile y luego la celda de compilación. Si modifica el programa, repita las dos.
Repita con los tres programas.
Ejecute la celda PASS/FAIL. Tiene cinco controles y debe terminar en RESUMEN: 5/5 PASS. La celda detecta archivos .dat más antiguos que su .f90, así que no basta con editar el código: hay que volver a compilarlo y ejecutarlo.
Responda las preguntas de la Parte D y redacte el informe.

Un PASS confirma el resultado numérico; no reemplaza la revisión del código, de los comentarios ni de las respuestas.

Entrega

En su repositorio, en la carpeta Taller_5/:

el notebook completado y ejecutado;
taller5_pi.f90, taller5_seno.f90 y taller5_lcg.f90;
convergencia.dat, pendiente.dat, seno.dat y lcg.dat;
convergencia_pi.png.

En Moodle, en un solo envío: el informe de una página en PDF (plantilla LaTeX del curso) y el enlace a la carpeta Taller_5/ de su repositorio. El informe debe incluir contexto, método, resultados, un obstáculo o decisión de implementación, una conclusión y la declaración de uso de herramientas de IA.

Antes de entregar
 El notebook se ejecuta completo desde una sesión nueva de Colab.
 Completé los diez bloques TODO y puedo explicar cada uno.
 La verificación muestra 5/5 PASS.
 Respondí las preguntas de la Parte D.
 El informe ocupa una página y cita los resultados de mi propia corrida.
Errores frecuentes
División entera. En Fortran, 79/100 vale 0. Convierta el contador con real(n, dp) antes de dividir.
Contadores grandes. Con $N = 10^7$ en ciclos anidados, use integer(8) para los contadores, como en las plantillas.
Interpretar una sola corrida. El error de una corrida fluctúa; $\sigma/\sqrt{N}$ es una escala típica, no un límite. Para comparar métodos o medir la convergencia se usan varias corridas.
Archivos desactualizados. Si la verificación indica que un .dat es anterior a su .f90, vuelva a compilar y ejecutar ese programa.