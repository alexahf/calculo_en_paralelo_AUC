# Avances 10-04-2018

# Integrantes
- Alejandro Hernández 87806
- Federico Riveroll 105898
- Pablo Soria 111969

# Individual

Consideramos tres posibles alternativas para la implementación del cálculo del AUC:
- Utilizando sumas de Riemman.
- Urilizando el método de Simpson basado en trapecios curvilíneos.
- Utilizando caminatas aleatorias.

Cada uno de los integrantes procedió a investigar sobre cada una de las alternativas planteadas y su factibilidad de implementación, así como comenzar a analizar de qué forma podría desarrollarse la implementación y cuál camino se seguiría.

- Alejandro Hernández
Leí la siguiente referencia, para intentar comprender como se realizariá la paralelización en el caso puntual del calculo de AUC. Asimismo, analice los siguientes trabajos xxxx y llegue a la conclusión de que es posible su implementación; no obstante, aun estoy investigando más pues no me queda tan claro como sería la distribución de los threads. Inicialmente, considero que se podría paralelizar del área de cada rectángulo por thread, pero falta analizar si el numero de recatangulos y por ende el numero de particiones se asignaría de forma manual, o es posible incorporar al algoritmo algún método para la elección de la partición adecuada. 
En este sentido, continua el trabajo de investigación ya más enfocado a la implementación.


- Federico Riveroll
Leí la siguiente referencia, para determinar como se podría impementar el algoritmo utilizando caminatas aleatorias.... 


- Pablo Soria
Leí el siguiente trabajo  que detalla el método de Simpson, el cual a primera vista se aprecia de fácil implementación pues consiste en aproximar el área bajo la curva utilizando un polinomio cuadrático....


# Equipo
Comentamos sobre cual de las tres alternativas resulta más viable de aplicar, en términos de simplicidad, de precisión y de exactitud; sin embargo, no nos hemos decantado por alguno en particular, pues todavia tenemos incertidumbre en esencia de la paralelización más que del algoritmo a utilizar, razón por la cual, decidimos el transitar en conjunto por las tres vias para ver si en el camino nos resulta más 

Para estructurar los avances decidimos generar el siguiente cronograma para las primeras tres entregas:

- 10-04-2018: Entrega primer avance.

- 12-04-2018: Revisión de investigación implementaciones.

- 14-04-2018: Pruebas iniciales implementación y revisión de alternativas.

- 17-04-2018: Entrega segundo avance.

- 20-04-2018: En caso de implementación exitosa, buscar robustecer el algoritmo. En otro caso, buscar soluciones a problematica puntual.

- 22-04-2018: Revisión de nuevo algoritmo y fallas detectadas en el mismo.

- 24-04-2018: Entrega tercer avance.


