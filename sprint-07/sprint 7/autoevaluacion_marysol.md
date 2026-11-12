## 1. Autoevaluación (cada persona, unos 5 minutos)

**Nombre:** Marysol

**Repaso rápido** (las mismas preguntas de «Antes de entregar» del reto en una página; contesta Sí / No / A medias):

| Pregunta | Mi respuesta |
|---|---|
| ¿La regresión tiene baseline y métricas en euros (MAE, RMSE) y R²? | **Sí.** Se comparan baseline, modelo lineal y modelo con interacciones con MAE, RMSE y R². |
| ¿La clasificación tiene baseline, matriz de confusión, AUC/AP y umbral justificado? | **Sí.** Se incluyen baseline, matriz de confusión, AUC = 0,746, AP = 0,729 y umbral 0,25 elegido mediante validación cruzada en train. |
| ¿Los costes de FN y FP son hipótesis explícitas con análisis de sensibilidad? | **Sí.** Se explicitan las hipótesis de 284 € para FN y 103 € para FP y se comparan escenarios de sensibilidad. |
| ¿La recomendación tiene cifras y límites? | **Sí.** La recomendación incluye un ahorro estimado de 98.153 € (63 %) en test y explica los límites del modelo. |
| ¿No hay fuga de datos y el test se usó una sola vez? | **A medias.** El informe explica que `cancelada` se excluyó del modelo de precio y que el umbral se eligió con validación cruzada en train. No queda documentado expresamente que el conjunto test se consultara una sola vez. |
| ¿El cuaderno se ejecuta entero y el README tiene versiones y semilla? | **A medias.** Se indica la semilla 42 y cómo ejecutar el cuaderno, pero faltan las versiones de Python y de las bibliotecas y no se aporta evidencia de ejecución completa. |
| ¿Está subido a Git, con autoevaluación y coevaluación? | **A medias.** Los documentos están preparados, pero la subida efectiva de cada archivo y su confirmación mediante *commit* deben realizarse en GitHub. |

**Puntúate de 1 a 4** en cada criterio de la rúbrica:

| Criterio | Mi puntuación (1–4) | Por qué (una frase) | Qué haría para subir un punto |
|---|---|---|---|
| Corrección técnica | **4** | El trabajo del equipo presenta baselines, métricas apropiadas, matriz de confusión, umbral justificado y análisis de sensibilidad. | Profundizar en el análisis de residuos y en la interpretación de los factores asociados al riesgo, si procede. |
| Reproducibilidad | **3** | Se documentan la semilla, los datos y el procedimiento general, pero faltan las versiones del entorno y confirmar la ejecución completa. | Añadir versiones de Python y bibliotecas y registrar una ejecución íntegra del cuaderno. |
| Análisis y comunicación al cliente | **4** | El informe convierte las métricas en euros, cuantifica el ahorro estimado y comunica recomendación y límites. | Añadir ejemplos operativos de revisión de avisos y análisis de errores por tipo de reserva. |
| IA responsable | **3** | Se advierten posibles sesgos por país de origen y canal y se recomienda supervisión humana; no consta una auditoría por grupos. | Registrar el uso real de IA y realizar comprobaciones de sesgo antes de un uso real. |

- **Lo que más me costó fue** elaborar el informe de modelado y traducir las métricas a una recomendación para el gerente, porque había que justificar el umbral y explicar el ahorro estimado y los límites del modelo.
- **He usado IA para** apoyar la elaboración y revisión del informe; he contrastado las cifras incluidas, la matriz de confusión, el umbral 0,25, las hipótesis de costes y las limitaciones descritas. El informe no incluye un registro detallado de todas las consultas realizadas a la IA.

---

## 2. Coevaluación (durante la review, unos 10 minutos)

**Trabajo revisado de (persona o equipo):** Las Guerreras — informe de modelado «Precio y cancelación»  **Revisado por (yo):** Cande, Elena, Marysol y Montse (coevaluación conjunta)

**¿Está lo que pide el reto?** Marca ✔ (sí), ✘ (no) o — (no procede).

| Entregable (nómbralo) | ¿Está y se entiende? | Comentario breve |
|---|---|---|
| Informe de regresión del precio por noche | ✔ | Compara baseline, modelo lineal y modelo con interacciones; incluye MAE, RMSE y R² y explica los coeficientes en euros. |
| Informe de clasificación de cancelaciones | ✔ | Incluye baseline, AUC, AP, matriz de confusión, recall, precisión y umbral 0,25 seleccionado mediante validación cruzada en train. |
| Análisis económico, sensibilidad y recomendación | ✔ | Explicita los costes hipotéticos de FN y FP, compara escenarios, estima el ahorro y comunica los límites y la necesidad de revisión humana. |

**Puntuación (1–4) de quien revisa:**

| Criterio | Puntuación | Comentario breve |
|---|---|---|
| Corrección técnica | 4 | Presenta baselines, métricas adecuadas, matriz de confusión y umbral elegido con validación cruzada en train; incluye costes y sensibilidad. |
| Reproducibilidad | 3 | Indica semilla, datos y pasos de ejecución, pero faltan las versiones de las bibliotecas y evidencia documentada de ejecución completa. |
| Análisis y comunicación al cliente | 4 | Traduce los resultados a euros, cuantifica el ahorro estimado y explica la recomendación y sus límites. |
| IA responsable | 3 | Identifica riesgos por país de origen y canal y recomienda supervisión humana; falta documentar el uso concreto de IA y auditar sesgos por grupos. |

- **Lo que está muy bien:** el informe conecta el rendimiento de los modelos con el impacto económico, explica el umbral y evita presentar las predicciones como decisiones automáticas.
- **Lo que yo cambiaría, y por qué:** añadiría las versiones de Python y de las bibliotecas, documentaría una ejecución completa del cuaderno y registraría qué tareas se apoyaron en IA y qué se verificó manualmente. Así mejoraría la reproducibilidad y la transparencia.

> Se valora el **trabajo**, no a la persona. Frases que ayudan: «Me ha ayudado que …», «Yo cambiaría … porque …».
