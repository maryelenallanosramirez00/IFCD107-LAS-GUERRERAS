# Autoevaluación y coevaluación · Sprint 11
## Grupo: Las Guerreras

**Nombre:** Cande

## 1. Autoevaluación

### Repaso rápido

| Pregunta | Mi respuesta |
|---|---|
| ¿El cuaderno se ejecuta de arriba abajo con semillas fijas? | Sí |
| ¿El dataset tiene carpeta por clase y hemos comprobado su contenido? | Sí |
| ¿Entrenamiento, validación y prueba están separados y la prueba se usó una vez? | Sí |
| ¿Hay un modelo con transfer learning y una referencia para compararlo? | Sí |
| ¿Hay métricas por clase y matriz de confusión interpretadas? | Sí |
| ¿Hay al menos 6 errores analizados con hipótesis y mejora? | Sí |
| ¿El demostrador devuelve clase, confianza y «revisar a mano»? | A medias |
| ¿Documentamos origen y licencia de los datos y al menos dos riesgos de IA responsable? | Sí |

### Puntuación personal (1–4)

| Criterio | Mi puntuación | Por qué | Qué haría para subir un punto |
|---|---:|---|---|
| Corrección técnica | 3 | He participado en el trabajo del grupo y comprendo el flujo general del modelo y su evaluación. | Repasar y comprobar de forma independiente cada celda y sus resultados. |
| Reproducibilidad | 3 | El cuaderno utiliza semillas fijas y separa entrenamiento, validación y prueba. | Volver a ejecutar el cuaderno completo desde el principio y comprobar que los resultados se reproducen. |
| Análisis y comunicación al cliente | 3 | Hemos comparado los modelos, interpretado las métricas y explicado las confusiones principales. | Profundizar en los errores por imagen y justificar mejor cada recomendación. |
| IA responsable | 3 | Hemos indicado que los datos son sintéticos y recogido riesgos y medidas de supervisión. | Concretar cómo se validaría el modelo con fotografías reales antes de utilizarlo. |

- **Lo que más me costó fue** entender la diferencia entre transfer learning, fine-tuning y entrenar desde cero, porque requiere relacionar las salidas del modelo con las características de las imágenes.
- **He usado IA para** ayudar a organizar y redactar explicaciones y documentación; **lo que he comprobado a mano es** los resultados de exactitud, F1 y las métricas de precisión y recall por clase.

## 2. Coevaluación

**Trabajo revisado de:** Las Guerreras (grupo completo)  
**Revisado por (yo):** Cande

La coevaluación valora el entregable común del equipo. No se atribuyen tareas individuales que no estén documentadas.

### ¿Está lo que pide el reto?

| Entregable | ¿Está y se entiende? | Comentario breve |
|---|---|---|
| Cuaderno de entrenamiento y comparación de modelos | ✔ | Se comparan transfer learning con fine-tuning y el modelo entrenado desde cero. |
| Evaluación: métricas por clase y matriz de confusión | ✔ | Se muestran precisión, recall, F1 y exactitud; se identifican confusiones entre clases. |
| Análisis de errores y recomendaciones | ✔ | Se estudian errores, se plantean hipótesis y se proponen mejoras; conviene revisar que el demostrador quede completo. |

### Puntuación del trabajo revisado (1–4)

| Criterio | Puntuación | Comentario breve |
|---|---:|---|
| Corrección técnica | 3 | El flujo de trabajo y la comparación están realizados; el resultado en prueba del modelo elegido es 75 %. |
| Reproducibilidad | 3 | Se fijan semillas y se separan los conjuntos de datos. |
| Análisis y comunicación al cliente | 3 | Se interpretan las métricas y destaca la confusión entre camping y casa_rural. |
| IA responsable | 3 | Se reconoce el carácter sintético del dataset y la necesidad de revisión humana y validación con datos reales. |

- **Lo que está muy bien:** el grupo ha comparado dos enfoques y no se ha quedado solo con la exactitud global; también ha revisado resultados por clase y errores.
- **Lo que yo cambiaría, y por qué:** completaría y probaría el demostrador para asegurar que devuelve clase, confianza y aviso de «revisar a mano». También validaría el sistema con fotografías reales antes de recomendar su uso.

---


