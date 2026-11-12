# Sprint 7 · Entregable

Reto: Precio y cancelación.

Qué se entrega:

reto_S07.ipynb: cuaderno de Google Colab con la carga y preparación de los datos, análisis exploratorio, modelos de regresión para predecir el precio por noche y clasificación para detectar cancelaciones, evaluación de resultados y análisis de costes.
informe_modelado.md: informe con los resultados obtenidos, comparación de modelos, interpretación de métricas, análisis económico, recomendaciones para TurisData y riesgos de IA responsable.

README.md: instrucciones para ejecutar el cuaderno, versiones de las librerías, semilla utilizada y documentación del trabajo.
autoevaluacion_nombre.md: autoevaluación individual de cada una de las cuatro integrantes.

Quién hizo qué:

Montse: Preparación, carga y exploración de los datos, selección de variables predictoras y comprobación de posibles fugas de información.

Marysol: Desarrollo del modelo de clasificación de cancelaciones mediante regresión logística, evaluación de resultados con matriz de confusión, AUC y AP, y revisión del trabajo mediante la rúbrica.

Elena: Desarrollo de los modelos de regresión para predecir el precio por noche, comparación mediante MAE, RMSE y R², definición de costes de errores y análisis de umbrales y sensibilidad económica.

Cande: Elaboración y organización del informe, documentación de los resultados, preparación del README y redacción de las conclusiones y recomendaciones para TurisData.

Cómo reproducirlo:

Abrir el archivo reto_S07.ipynb en Google Colab.
Comprobar que se dispone de conexión a Internet para descargar reservas_turisdata.csv desde el repositorio del curso.
Ejecutar todas las celdas del cuaderno de arriba abajo, respetando el orden establecido.
Mantener la semilla SEMILLA = 42 para facilitar la reproducción de los resultados.
Comprobar las métricas de los modelos, las matrices de confusión y los cálculos de costes.
Consultar informe_modelado.md para interpretar los resultados y conocer las recomendaciones.
Subir los archivos correspondientes a la carpeta sprint-07/ del repositorio del equipo.
