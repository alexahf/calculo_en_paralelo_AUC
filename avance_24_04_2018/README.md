# Avances 24-04-2018

# Integrantes
- Alejandro Hernández 87806
- Federico Riveroll 105898
- Pablo Soria 111969

# Individual

- Alejandro Hernández

En virtud de que no se encontró puntualmente una implementación en CUDA para el cálculo de AUC usando Riemann y siguiendo la recomendación del profesor, opté por buscar otra extensión de C. Encontré que en esta referencia [http://www.shodor.org/media/content/petascale/materials/UPModules/AreaUnderCurve/AUC_Module_Document_pdf.pdf](http://www.shodor.org/media/content/petascale/materials/UPModules/AreaUnderCurve/AUC_Module_Document_pdf.pdf) también se incluye la implementación en OpenMP y al parecer está bastante bien documentada. Asimismo, en dicho artículo se incluye el siguiente pseudocódigo que es el que buscaría seguir:

```
All processes do the following:
0-1) Calculate the overall width of the domain of the
function and the width of a rectangle.
• If MY_THREAD_NUM == 0,
• WIDTH = X_RIGHT – X_LEFT
• RECTANGLE_WIDTH = WIDTH / NUMBER_OF_RECTANGLES
0-1) Calculate the number of rectangles for which the
process is responsible.
• If MY_THREAD_NUM == (1 mod OUR_NUMBER_OF_THREADS),
• OUR_NUMBER_OF_RECTANGLES = NUMBER_OF_RECTANGLES/
NUMBER_OF_PROCESSES
• If OUR_RANK == NUMBER_OF_PROCESSES – 1,
• OUR_NUMBER_OF_RECTANGLES = OUR_NUMBER_OF_RECTANGLES
+ NUMBER_OF_RECTANGLES mod NUMBER_OF_PROCESSES
0) Calculate the left x-boundary of the process.
• If MY_THREAD_NUM == (2 mod OUR_NUMBER_OF_THREADS),
• OUR_X_LEFT = (OUR_RANK * (NUMBER_OF_RECTANGLES/
NUMBER_OF_PROCESSES)) * RECTANGLE_WIDTH + X_LEFT
2-4) For each rectangle, parallelized by thread,
2) Calculate the x-value of the left side of the
rectangle:
• my_current_rectangle_left = OUR_X_LEFT +
my_current_rectangle_id * RECTANGLE_WIDTH
3) Calculate the height of the rectangle:
• my_current_rectangle_height =
FUNC(my_current_rectangle_left)
4) Calculate the area of the rectangle:
• our_areas[my_current_rectangle_id] =
RECTANGLE_WIDTH * my_current_rectangle_height
5) Calculate the total sum for the process.
• If MY_THREAD_NUM == 0,
• for each rectangle,
• our_total_sum = our_total_sum +
our_areas[my_current_rectangle_id]
6) Calculate the overall total sum.
• Each process sends our_total_sum to Rank 0
• Rank 0 adds sums to the_total_sum
```

Como lo había hecho con CUDA, en el caso de OpenMP he estado buscando una imagen de docker que me permita hacer pruebas de forma local; no obstante, aún no he encontrado alguno bueno, por lo que en caso de
