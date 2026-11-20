# Sprint 10 · Autoevaluación y coevaluación

**Integrante:** Marysol  
**Equipo:** Las Guerreras  
**Reto:** ¿Vale la pena la red?

## 1. Autoevaluación

### Repaso rápido

Esta autoevaluación es individual, pero valora un trabajo realizado conjuntamente por las cuatro integrantes. Hemos colaborado en el cuaderno, los ejercicios, el entrenamiento y diagnóstico de la MLP, la comparación con Boosting y la preparación del informe.

| Pregunta | Mi respuesta |
|---|---|
| ¿El cuaderno se ejecuta de arriba abajo, con semillas fijas? | Sí |
| ¿La partición es única y la prueba se usa una sola vez? | Sí |
| ¿Hay al menos un MLP y un modelo de árboles/boosting comparados con las mismas métricas? | Sí |
| ¿Hay curvas de aprendizaje y un diagnóstico explícito de sobreajuste? | Sí |
| ¿La comparación tiene incertidumbre (varias semillas o bootstrap)? | Sí |
| ¿El informe recomienda algo concreto, con coste y límites? | Sí |
| ¿Hay al menos dos riesgos de IA responsable específicos? | Sí |

### Puntuación personal (1–4)

| Criterio | Mi puntuación (1–4) | Por qué | Qué haría para subir un punto |
|---|---:|---|---|
| Corrección técnica | 3 | He participado en el trabajo conjunto y en la revisión de los resultados y ejercicios del cuaderno. | Repasar con más profundidad el código y practicar la interpretación de las métricas. |
| Reproducibilidad | 3 | El trabajo compara los modelos con las mismas particiones y utiliza tres semillas para la MLP. | Repetir la ejecución completa desde un entorno reiniciado y comprobar que se obtienen los mismos resultados. |
| Análisis y comunicación al cliente | 3 | Hemos comparado las métricas, el intervalo de confianza y el tiempo de entrenamiento para justificar la recomendación. | Explicar con más ejemplos cómo se traducen los resultados en decisiones para el establecimiento. |
| IA responsable | 3 | El informe incluye riesgos de predicciones incorrectas y de posibles diferencias entre grupos de clientes, junto con medidas. | Añadir comprobaciones más detalladas del rendimiento por grupos. |

- **Lo que más me costó fue** valorar si la diferencia entre los modelos era realmente significativa y revisar que las conclusiones estuvieran justificadas, porque requiere relacionar varios conceptos y no quedarse únicamente con los valores numéricos.
- **He usado IA para** resolver dudas, aclarar conceptos y mejorar la redacción; lo que hemos comprobado en equipo a mano es la ejecución de las celdas, las salidas, las métricas y los diagnósticos obtenidos.

**Mi aprendizaje principal:** contrastar las métricas, el intervalo de confianza, el coste de entrenamiento y la coherencia del informe.

---

## 2. Coevaluación

**Trabajo revisado:** trabajo del equipo formado por Cande, Montse, Marysol y Elena.  
**Revisado por:** Montse

Montse realiza la revisión del trabajo conjunto y comprueba que los entregables responden a lo solicitado en el reto.

### ¿Está lo que pide el reto?

| Entregable | ¿Está y se entiende? | Comentario breve de la revisión |
|---|:---:|---|
| Cuaderno `reto_vale_la_pena.ipynb` | ✔ | Recoge el proceso de trabajo y los ejercicios del reto. Se debe ejecutar de arriba abajo para reproducir los resultados. |
| Comparación de modelos | ✔ | Se comparan Boosting y MLP mediante las mismas métricas y se consideran varias semillas para la red. |
| Diagnóstico de sobreajuste | ✔ | La función `diagnostico` se ejecuta y las tres semillas devuelven «sin sobreajuste claro». |
| Informe `informe_comparativo.md` | ✔ | Incluye resultados, recomendación, coste, riesgos de IA responsable y limitaciones. |

### Puntuación de la revisión realizada por Marysol

| Criterio | Puntuación (1–4) | Comentario breve |
|---|---:|---|
| Corrección técnica | 3 | Los ejercicios y las métricas están incluidos y se han comprobado los resultados obtenidos. |
| Reproducibilidad | 3 | Se indican los pasos para ejecutar el cuaderno y se utilizan semillas y particiones comunes. |
| Análisis y comunicación al cliente | 3 | La recomendación de mantener Boosting está justificada por el empate estadístico y el menor tiempo de entrenamiento. |
| IA responsable | 3 | Se describen riesgos concretos y medidas de supervisión y revisión. |

- **Lo que está muy bien:** el equipo ha comparado los modelos con criterios comunes y no ha afirmado que la MLP sea mejor solo por obtener un AUC ligeramente superior. También se ha tenido en cuenta el coste de entrenamiento.
- **Lo que yo cambiaría, y por qué:** reforzaría la explicación visual de las curvas y añadiría, en una siguiente versión, una comprobación del rendimiento por grupos de clientes. Esto ayudaría a interpretar mejor el comportamiento del modelo y sus posibles sesgos.

> La revisión de Marysol valora los entregables y el resultado del trabajo conjunto, no a las personas. Las puntuaciones reflejan una valoración orientativa del trabajo realizado y pueden ajustarse si la revisión final detecta algún aspecto distinto.
