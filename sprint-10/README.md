# Sprint 10 · Entregable

- **Reto:** *¿Vale la pena la red?*
- **Qué se entrega:** *Cuaderno reto_vale_la_pena.ipynb, con los ejercicios y experimentos realizados.
Informe informe_comparativo.md, con los resultados, la comparación de modelos, el diagnóstico y las conclusiones.*
- **Quién hizo qué:**
  Persona 1: preparación del cuaderno y realización de los ejercicios 1 y 2.
  Persona 2: entrenamiento de las variantes MLP, análisis de las tres semillas, diagnóstico del sobreajuste y ejercicio 3.
  Persona 3: comparación entre Boosting y MLP, ejercicio 4, interpretación de las métricas y elaboración del informe comparativo.
- **Cómo reproducirlo:** Cómo reproducirlo
Abrir el cuaderno reto_vale_la_pena.ipynb en Google Colab.
Comprobar que el archivo reservas_turisdata.csv está disponible.
Seleccionar Entorno de ejecución → Reiniciar y ejecutar todo.
Ejecutar las celdas de arriba abajo, sin saltarse pasos.
Comprobar que se generan los resultados de los modelos, las métricas de evaluación y las gráficas.
Verificar que los resultados coinciden con los recogidos en informe_comparativo.md
La comparación utiliza las mismas particiones de entrenamiento, validación y prueba. La MLP se ejecuta con tres semillas para comprobar la estabilidad de sus resultados.
Conclusión del reto
La comparación no muestra una diferencia estadísticamente significativa entre los modelos. Por tanto, se recomienda mantener el Boosting como referencia, ya que ofrece resultados similares con un menor coste de entrenamiento
