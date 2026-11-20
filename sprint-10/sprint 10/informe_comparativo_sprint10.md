# Informe comparativo · ¿Vale la pena la red? (Sprint 10)

## 1. Pregunta y respuesta

Recomendamos **mantener el boosting de árboles** como modelo de referencia para predecir cancelaciones hoteleras. La comparación estadística da empate entre los modelos y el boosting necesita mucho menos tiempo de entrenamiento: 0,744 segundos frente a 10,995 segundos de media para la MLP.

## 2. Resultados

| Modelo | AUC | AP | F1 | Exactitud |
|---|---:|---:|---:|---:|
| Boosting de árboles | 0,738 | 0,721 | 0,639 | 0,672 |
| MLP (media de 3 semillas) | 0,743 | 0,722 | 0,637 | 0,682 |

AUC de validación del MLP: **0,744 ± 0,002**.

Diferencia de AUC (MLP − boosting): **+0,006**.  
Intervalo del 95 %: **[-0,005, +0,018]**.

La diferencia **no es mayor que el ruido**, porque el intervalo contiene el cero. Por tanto, el veredicto estadístico es **Empate**.

## 3. Curva comentada

Las curvas de aprendizaje muestran que la pérdida de validación alcanza su mínimo en estas épocas:

- Semilla 1: época 30 de 36.
- Semilla 2: época 29 de 35.
- Semilla 3: época 31 de 37.

**Diagnóstico:** Las tres redes MLP presentan un comportamiento similar y no muestran sobreajuste claro. La pérdida de validación alcanza su mínimo entre las épocas 29 y 31. La parada temprana evita prolongar innecesariamente el entrenamiento.

## 4. Coste

- **Tiempo de entrenamiento:** boosting, 0,744 segundos; MLP, 10,995 segundos de media.
- **Complejidad:** boosting, 200 iteraciones con árboles de profundidad máxima 4; MLP, 4.417 pesos.
- **Explicabilidad:** limitada en ambos modelos. La MLP es especialmente difícil de interpretar directamente.

## 5. Riesgos de IA responsable

1. **Riesgo:** que el modelo prediga incorrectamente la cancelación de una reserva y provoque decisiones inadecuadas en la planificación del hotel.  
   **Medida:** utilizar las predicciones como apoyo, revisar los casos importantes y no automatizar decisiones sensibles sin supervisión.

2. **Riesgo:** que el rendimiento sea diferente según el país de origen o el canal de reserva, generando resultados desiguales para algunos grupos.  
   **Medida:** comprobar periódicamente las métricas por grupos y revisar posibles diferencias antes de utilizar el modelo en producción.

## 6. Límites y siguiente paso

El análisis utiliza un conjunto de datos y una partición concreta. Los resultados no garantizan que los modelos funcionen igual con reservas reales nuevas, otros hoteles o temporadas diferentes. También habría que revisar el efecto del umbral de clasificación, porque los costes de una falsa alarma y de no detectar una cancelación pueden ser distintos.

**Siguiente paso:** probar el modelo con datos reales de otro periodo y evaluar su rendimiento por país de origen y canal de reserva. También convendría ajustar el umbral según las necesidades del establecimiento.

## Uso de la IA

Pedimos ayuda a la IA para comprender las métricas, interpretar los resultados y redactar las conclusiones. Comprobamos manualmente los valores ejecutando las celdas del notebook y revisando las salidas. Ajustamos la recomendación para reflejar que el intervalo de confianza incluye el cero y que, por tanto, no se puede afirmar que la MLP sea mejor.

## Revisión con la rúbrica

Revisado por: Marysol
Fecha: 19/11/2026

| Criterio | Nivel (1–4) | Prueba: una frase de lo que has comprobado |
|---|---:|---|
| Corrección técnica |  | Se han ejecutado las funciones de evaluación y las comprobaciones del notebook. |
| Reproducibilidad |  | Se han utilizado las mismas particiones para comparar los modelos y tres semillas para la MLP. |
| Análisis y comunicación al cliente |  | Se han comparado las métricas, el coste de entrenamiento y el intervalo de confianza. |
| IA responsable |  | Se han identificado riesgos de errores de predicción y posibles diferencias entre grupos. |

**Lo primero que mejoraríamos:** comprobar el rendimiento con datos reales de otros periodos y revisar las métricas por grupos.
