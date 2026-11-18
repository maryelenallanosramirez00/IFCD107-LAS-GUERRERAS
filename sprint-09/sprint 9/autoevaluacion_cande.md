# Autoevaluación y coevaluación · Sprint 9 «Conocer al huésped»
**Nombre:** Cande  **Equipo:** Montse, Cande, Marysol y Elena  **Responsabilidad principal propuesta:** Recomendador de experiencias
> **Antes de subirlo:** este archivo es un borrador individual. Cada persona debe leerlo, corregir cualquier tarea o valoración que no refleje su trabajo real y completar su coevaluación cuando el docente asigne el trabajo que debe revisar.
## Reparto de responsabilidades del equipo
| Integrante | Responsabilidad principal | Tareas |
|---|---|---|
| Montse | Segmentación de huéspedes | Explorar variables, interpretar grupos y proponer perfiles y acciones comerciales. |
| Cande | Recomendador | Comparar popularidad e item-item y revisar RMSE y precision@3. |
| Marysol | Revisión y validación técnica | Ejecutar el cuaderno, comprobar estandarización, tamaños y perfiles, y probar `recomendar()`. |
| Elena | Documentación y comunicación | Preparar la ficha, integrar el mapa PCA y redactar IA responsable y limitaciones. |

## 1. Autoevaluación

### Repaso rápido

| Pregunta | Mi respuesta |
|---|---|
| ¿El cuaderno se ejecuta de arriba abajo, con semillas fijas? | Sí. Marysol confirmó que se reinició y ejecutó todo sin errores. |
| ¿Hemos escalado antes de agrupar y justificado `k` con silueta y con negocio? | Sí. Se confirmó la estandarización; k-means con k = 4 obtuvo silueta 0,431 y se justificaron cuatro perfiles. |
| ¿El mapa PCA tiene segmentos coloreados y el % de varianza en los ejes? | Sí. Los ejes muestran 43 % y 26 %, aproximadamente 69 % en conjunto. |
| ¿La ficha tiene nombre, tamaño, perfil y acción por segmento? | Sí. La ficha recoge los cuatro segmentos, sus tamaños, perfiles y acciones. |
| ¿El recomendador está evaluado con RMSE y precision@3 y comparado con la popularidad? | Sí. Se comparan popularidad e item-item con ambas métricas. |
| ¿`recomendar` no propone experiencias ya valoradas? | Sí. Marysol lo comprobó con los usuarios 1, 2 y 3; las tres pruebas devolvieron `set()`. |
| ¿Hay al menos dos riesgos específicos de IA responsable? | Sí. Se incluyen riesgos de discriminación, sesgo de popularidad y privacidad, con medidas. |
| ¿Cada persona ha hecho *commit* de su parte? | A medias / pendiente de comprobar. Cada integrante debe confirmar su archivo y su commit individual. |

### Mi contribución

**Mi responsabilidad principal:** Recomendador de experiencias.  
**Tareas que debo confirmar que he realizado:** Trabajar con los métodos de recomendación, comparar popularidad e item-item y analizar las métricas RMSE y precision@3.
### Puntuación personal propuesta (1–4)

| Criterio | Mi puntuación (1–4) | Por qué | Qué haría para subir un punto |
|---|---:|---|---|
| Corrección técnica | 3 | El trabajo de mi área está integrado en el cuaderno y/o la ficha, y se han contrastado los resultados disponibles. | Revisar de nuevo los resultados con los datos originales y documentar más pruebas. |
| Reproducibilidad | 3 | Marysol confirmó que el cuaderno se reinicia y ejecuta de principio a fin sin errores. | Documentar las versiones del entorno y repetir la ejecución en otro entorno. |
| Análisis y comunicación al cliente | 3 | La entrega explica los cuatro segmentos, las acciones comerciales y la comparación del recomendador. | Relacionar cada decisión con más evidencias y revisar la claridad con una persona externa. |
| IA responsable | 3 | La ficha identifica riesgos de discriminación, sesgo de popularidad y privacidad, con medidas de mitigación. | Concretar controles de seguimiento y la base jurídica antes de trabajar con datos reales. |

- **Lo que más me costó fue** comparar los métodos de recomendación y entender qué indican las métricas de evaluación, **porque** necesitaba interpretar los resultados y explicarlos de forma comprensible.
- **He usado IA para** aclarar conceptos y organizar la explicación de los resultados del recomendador; **lo que he comprobado a mano es** los valores de RMSE y precision@3, el método seleccionado y las recomendaciones devueltas por el prototipo.

## 2. Coevaluación

**Trabajo revisado de (persona o equipo):** Pendiente de que el docente lo asigne durante la review.  
**Revisado por (yo):** Cande

> No completar esta parte hasta saber qué persona o equipo corresponde revisar. La coevaluación se hace sobre el trabajo asignado, no sobre una persona elegida por cuenta propia.
### ¿Está lo que pide el reto?

| Entregable | ¿Está y se entiende? | Comentario breve |
|---|---|---|
| Cuaderno `.ipynb` ejecutable | Pendiente | Completar durante la review del trabajo asignado. |
| `ficha_segmentos.md` y mapa `mapa_pca.png` | Pendiente | Completar durante la review del trabajo asignado. |
| Recomendador y evaluación | Pendiente | Completar durante la review del trabajo asignado. |

### Puntuación de quien revisa

| Criterio | Puntuación (1–4) | Comentario breve |
|---|---:|---|
| Corrección técnica | Pendiente | Completar con evidencia durante la review. |
| Reproducibilidad | Pendiente | Completar con evidencia durante la review. |
| Análisis y comunicación al cliente | Pendiente | Completar con evidencia durante la review. |
| IA responsable | Pendiente | Completar con evidencia durante la review. |

- **Lo que está muy bien:** pendiente de la review.
- **Lo que yo cambiaría, y por qué:** pendiente de la review.

## 3. Entrega individual

- [ ] Guardar/subir este archivo como `autoevaluacion_cande.md` en `sprint-09/`.
- [ ] Hacer commit con el mensaje `Subo mi autoevaluación`.
- [ ] Completar la coevaluación después de la asignación del docente.
