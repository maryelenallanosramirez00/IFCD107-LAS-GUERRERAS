# Informe de modelado · TurisData Canarias · «Precio y cancelación»

**Equipo:** Las Guerreras · **Elaborado por:** Marysol · **Fecha:** 12/11/2026

## 1. Resumen para el gerente (máx. 6 líneas)

Se han desarrollado dos modelos: uno para estimar el precio por noche y otro para detectar reservas con riesgo de cancelación.  
El modelo de precio con interacciones obtiene un error medio absoluto de 6,758 € por noche (MAE).  
Para cancelaciones se ha elegido, mediante validación cruzada sobre train, un umbral de 0,25.  
Las hipótesis de coste son 284 € por cancelación no prevista (FN) y 103 € por falsa alarma (FP).  
En el conjunto de test, el coste estimado baja de 156.484 € sin modelo a 58.331 € con el umbral elegido: un ahorro de 98.153 € (63 %).  
La recomendación es usar el aviso como apoyo a la revisión de reservas, no como decisión automática.

## 2. Datos y variables

Se han utilizado 6.000 reservas y 20 columnas, incluyendo las dos variables derivadas `mes_llegada` y `temporada_alta`. La semilla utilizada es `SEMILLA = 42`.

**Modelo de precio:** la variable objetivo es `precio_noche`. Se utilizaron `tipo_habitacion` (convertida en variables 0/1 mediante `get_dummies`) y `temporada_alta`. Se excluyeron `cancelada` (no se conoce al reservar y produciría fuga de información), `id_reserva` (identificador sin valor predictivo para el precio) y las demás columnas, que no se incluyeron en este modelo. Las fechas se resumieron en `temporada_alta`.

La partición del modelo de precio fue de 4.800 reservas para train y 1.200 para test (80 % / 20 %).

**Modelo de cancelación:** la variable objetivo es `cancelada`. Se utilizaron 15 variables predictoras: numéricas (`antelacion_dias`, `noches`, `adultos`, `ninos`, `precio_noche`, `peticiones_especiales`, `cliente_repetidor`, `cancelaciones_previas`, `temporada_alta`) y categóricas (`tipo_habitacion`, `regimen`, `canal`, `pais_origen`, `tarifa`, `deposito`). La partición estratificada fue también de 4.800 reservas para train y 1.200 para test. La proporción de cancelaciones fue 0,459 tanto en train como en test.

## 3. Regresión: precio por noche

| Modelo | MAE (€) | RMSE (€) | R² |
|---|---:|---:|---:|
| Baseline (media) | 25,564 | 33,328 | -0,002 |
| Lineal | 7,239 | 9,704 | 0,915 |
| Lineal con interacciones | 6,758 | 8,936 | 0,928 |

**Lectura para el cliente:** el modelo lineal estima un precio base de 67,3 € para una habitación estándar en temporada baja. Respecto a esa referencia, los coeficientes estimados son: familiar +45,0 €, suite +101,2 €, superior +28,4 € y temporada alta +22,4 €.

El modelo con interacciones reduce el MAE en aproximadamente 0,48 € por noche respecto al lineal y alcanza un R² de 0,928. La mejora existe, pero es moderada. En el cuaderno no se ha realizado un análisis específico de residuos, por lo que no se puede concretar en qué tipos de reserva falla más el modelo.

## 4. Clasificación: cancelación

| Modelo | AUC | AP | Recall (umbral) | Precisión (umbral) |
|---|---:|---:|---:|---:|
| Baseline (clasificador mayoritario) | 0,500 | 0,459 | 0 % | No aplicable |
| Regresión logística | 0,746 | 0,729 | 92 % | 53 % |

El baseline mayoritario predice la clase más frecuente (no cancelación); por eso no detecta cancelaciones y su precisión para avisos no es aplicable. La regresión logística discrimina mejor que el azar: AUC = 0,746 y AP = 0,729.

**Matriz de confusión en test con umbral 0,25:**

| | Predice que se mantiene | Predice que cancela |
|---|---:|---:|
| Realmente se mantiene | 204 (VN) | 445 (FP) |
| Realmente cancela | 44 (FN) | 507 (VP) |

Con este umbral se detecta el 92 % de las cancelaciones (recall), aunque el 47 % de los avisos son falsas alarmas (precisión del 53 %). El cuaderno no calcula *odds ratios*, por lo que no se identifican aquí los factores que más aumentan o reducen el riesgo.

## 5. De las métricas a los euros

- **Hipótesis de coste** de una cancelación no prevista (FN): **284 € por reserva**. Se estima que una reserva media dura 5,5 noches y cuesta 102,87 € por noche; si solo se consigue revender la mitad de las noches, la pérdida aproximada es `0,5 × 5,52 × 102,87 ≈ 284 €`.
- **Hipótesis de coste** de una falsa alarma (FP): **103 € por reserva**. Se aproxima al precio medio de una noche (102,87 €), como hipótesis de compensación por tener que alojar al cliente en otro establecimiento.
- **Umbral elegido con validación cruzada:** **0,25**, seleccionado probando umbrales sobre probabilidades obtenidas mediante validación cruzada de 5 particiones en train. El conjunto test no se utilizó para elegirlo.
- **Coste en test:** sin modelo **156.484 €** · umbral 0,5 **78.439 €** · umbral elegido (0,25) **58.331 €**. El ahorro frente a no utilizar el modelo es de **98.153 € (63 %)**.

**Análisis de sensibilidad:** la siguiente tabla recoge el umbral óptimo y el coste mínimo en train al cambiar las hipótesis de coste. Los costes totales se calculan sobre las predicciones de validación cruzada en train.

| Hipótesis | Coste FN (€) | Coste FP (€) | Umbral óptimo | Coste mínimo en train (€) | Sin modelo en train (€) |
|---|---:|---:|---:|---:|---:|
| La nuestra | 284 | 103 | 0,25 | 223.121 | 625.652 |
| FN el doble | 568 | 103 | 0,15 | 249.011 | 1.251.304 |
| FP la mitad | 284 | 51,50 | 0,15 | 124.506 | 625.652 |
| FP el doble | 284 | 206 | 0,40 | 354.720 | 625.652 |

Cuando aumenta el coste de no detectar una cancelación, el umbral baja a 0,15 para detectar más posibles cancelaciones. Cuando aumenta el coste de una falsa alarma, el umbral sube a 0,40 para reducir avisos incorrectos. La tabla de sensibilidad corresponde a train; no se han recalculado los costes de test para cada escenario alternativo.

## 6. Recomendación de negocio

Se recomienda utilizar el umbral de 0,25 para generar avisos de reservas con riesgo de cancelación y que el personal del hotel revise esos casos antes de tomar medidas. En test, el coste estimado con este umbral es 58.331 €, frente a 156.484 € sin modelo, un ahorro estimado de 98.153 € (63 %) bajo las hipótesis establecidas.

El modelo detecta 507 de las 551 cancelaciones reales del test, pero genera 445 falsas alarmas. Por ello, no conviene cancelar reservas ni comprometer habitaciones automáticamente basándose solo en la predicción.

**Límites:** los datos son sintéticos y corresponden a un único hotel; los costes de FN y FP son hipótesis, no importes contables observados. El comportamiento de los clientes puede cambiar con el tiempo y el rendimiento puede variar en otros hoteles o temporadas. El resultado económico es una estimación sobre el conjunto de test, no una garantía de ahorro futuro.

## 7. IA responsable

Se deben revisar posibles sesgos asociados al país de origen y al canal de reserva, ya que el modelo utiliza ambas variables. Una tasa de riesgo diferente entre grupos no debe interpretarse automáticamente como una característica individual del cliente.

El aviso debe servir como apoyo a una revisión humana, no para discriminar clientes, imponer depósitos o modificar precios de forma automática. También se debe evitar perjudicar a clientes reubicados por una falsa alarma y comprobar periódicamente el rendimiento del modelo por grupos y a lo largo del tiempo.

El cuaderno no documenta una auditoría específica de sesgos ni una revisión de resultados por país o canal. Por tanto, estas medidas quedan como precauciones y comprobaciones pendientes antes de un uso real.

## 8. Cómo reproducirlo

- **Semilla:** `SEMILLA = 42`.
- **Datos:** `reservas_turisdata.csv`, descargado desde el repositorio del curso mediante la función `dato()`.
- **Ejecución:** abrir `reto_S07.ipynb` en Google Colab y ejecutar todas las celdas de arriba abajo, en orden.
- **Versiones:** el cuaderno no registra las versiones de Python, pandas, NumPy, scikit-learn ni Matplotlib. Deben añadirse si se requiere reproducibilidad exacta.

## 9. Revisión con la rúbrica

**Revisado por:** Marysol · **Fecha:** 12/11/2026

La valoración se basa en las evidencias que aparecen en este informe. En los aspectos que requieren ejecutar el cuaderno o consultar el historial de trabajo, se indica la limitación en lugar de dar por comprobado algo que no queda documentado.

| Criterio | Nivel (1–4) | Prueba: una frase de lo que se ha comprobado |
|---|---:|---|
| Corrección técnica | **4** | Se presentan baselines para ambos problemas, métricas adecuadas (MAE, RMSE y R² para regresión; AUC, AP, recall y precisión para clasificación), matriz de confusión y umbral seleccionado mediante validación cruzada en train, sin utilizar test para elegirlo. También se explicitan las hipótesis de coste y se incluye análisis de sensibilidad. |
| Reproducibilidad | **3** | Se documentan la semilla (42), el conjunto de datos, la partición train/test y los pasos para ejecutar el cuaderno. No obstante, faltan las versiones de Python y de las bibliotecas, y esta revisión del informe no permite confirmar por sí sola que el cuaderno se ejecute de principio a fin y reproduzca exactamente las cifras. |
| Análisis y comunicación al cliente | **4** | El informe traduce los resultados a euros, compara el coste de usar y no usar el modelo, explica el umbral recomendado y comunica sus límites con una recomendación comprensible para el gerente. |
| IA responsable | **3** | Se identifican riesgos concretos relacionados con país de origen y canal, se propone supervisión humana y se advierte contra decisiones automáticas. Falta documentar qué se solicitó a la IA, qué respuestas se comprobaron y qué cambios se realizaron, además de una auditoría efectiva de sesgos. |

**Lo primero que mejoraríamos:** completar la documentación de reproducibilidad (versiones de las bibliotecas y comprobación de ejecución completa) y añadir un registro transparente del uso de IA: para qué se utilizó, qué resultados se verificaron manualmente y qué modificaciones se hicieron.

