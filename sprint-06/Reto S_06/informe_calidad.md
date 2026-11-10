# Informe de calidad del dato · `reservas_sucio.csv`

**Equipo:** Las Guerreras 
**Fecha:** 09/11/2026  
**Nivel objetivo:** Extra  
**Entorno:** Google Colab

## 1. Resumen para el gerente

El fichero original contiene duplicados, datos nulos, formatos mezclados, categorías inconsistentes y valores imposibles. Se identificaron 10 defectos o incidencias de calidad. La limpieza eliminó 45 filas duplicadas y dejó 1.500 reservas; además, convirtió 14 valores imposibles en nulos y recalculó 5 antelaciones. Para predecir cancelaciones, la regresión logística obtuvo un AUC medio de 0,746 ± 0,023 en validación cruzada temporal, frente a 0,500 ± 0,000 del modelo de referencia. La evaluación temporal final obtuvo un AUC de 0,737.

## 2. Inventario de defectos

Los defectos más graves son los duplicados, los valores imposibles y los datos nulos, porque pueden alterar los recuentos, los cálculos y el entrenamiento del modelo.

| N.º | Defecto | Columna(s) | Filas/valores afectados | Cómo lo detectamos | Causa probable | Tratamiento aplicado | Por qué y riesgo |
|---:|---|---|---:|---|---|---|---|
| 1 | Filas duplicadas exactas | Todas | 45 | `crudo.duplicated().sum()` | Exportación repetida o unión de datos de distintos sistemas | `drop_duplicates()`; se conserva una copia | Evita contar dos veces una reserva. Riesgo: dos reservas legítimas idénticas en todas las columnas podrían confundirse con duplicados. |
| 2 | Valores imposibles en precio o noches | `precio_noche`, `noches` | 14 convertidos a nulo | Comprobación de los límites: precio entre 20 y 1.000 € y noches entre 1 y 60 | Error de escritura, importación o registro | Se conservan los valores dentro de los intervalos fijados; los demás se convierten en nulos | Evita que valores inválidos distorsionen el análisis. Los límites son reglas del ejercicio y los casos dudosos deben confirmarse con el cliente. |
| 3 | Valores nulos | `adultos`, `regimen`, `pais_origen`, `precio_noche` | 46, 61, 115 y 84 respectivamente antes de limpiar | `crudo.isna().sum()` | Datos no introducidos o perdidos durante la exportación | Se conservan en la limpieza inicial; la imputación se realiza dentro del pipeline y se ajusta solo con train | Evita inventar información. Una imputación inadecuada puede sesgar el modelo. |
| 4 | Precios escritos con coma decimal | `precio_noche` | 153 | `astype(str).str.contains(",").sum()` | Exportación con configuración decimal española | Sustituir la coma por un punto y convertir a numérico | Permite realizar cálculos; los textos no convertibles quedan como nulos. |
| 5 | Fechas escritas en dos formatos | `fecha_reserva` | 154 | Prueba de conversión con `%Y-%m-%d` y `%d/%m/%Y` | Exportación desde sistemas con formatos regionales distintos | Convertir cada formato por separado y combinar los resultados | Evita confundir día y mes y permite calcular intervalos. |
| 6 | Categorías inconsistentes en los canales | `canal` | 135 | `crudo["canal"].value_counts()` | Diferencias de mayúsculas, espacios y guiones bajos | Quitar espacios sobrantes, pasar a minúsculas y normalizar separadores | Evita contar un mismo canal como varias categorías. |
| 7 | Países escritos con distintas denominaciones | `pais_origen` | 94 | `crudo["pais_origen"].value_counts()` | Uso de abreviaturas, minúsculas y nombres completos | Aplicar el diccionario de equivalencias `EQUIV_PAIS` | Agrupa las variantes conocidas. Las no incluidas en el diccionario deben revisarse y no asignarse por suposición. |
| 8 | Precios extremos superiores a 1.000 € | `precio_noche` | 4 | `(precio > 1000).sum()` y diagramas de caja | Posible error de escritura o reserva excepcional | La regla aplicada convierte los precios fuera de 20–1.000 € en nulos | Reduce la influencia de valores extremos, pero un precio alto podría ser real y debe confirmarse. |
| 9 | Noches iguales o inferiores a cero | `noches` | 6 | `(crudo["noches"] <= 0).sum()` | Error de introducción o registro | Convertir los valores fuera de 1–60 en nulos | Una estancia normal no puede tener cero noches ni una duración negativa. |
| 10 | Antelaciones negativas o incoherentes con las fechas | `antelacion_dias`, `fecha_reserva`, `fecha_llegada` | 5 incoherencias | Comparación entre la diferencia de fechas y `antelacion_dias` | Error de cálculo o registro | Recalcular `antelacion_dias` como diferencia entre llegada y reserva | Mantiene la coherencia temporal, siempre que las fechas originales sean correctas. |

**Nota sobre los recuentos:** los defectos pueden coincidir en una misma reserva. Por tanto, no se deben sumar sus recuentos para calcular el número total de filas afectadas. Los 14 valores imposibles son el resultado conjunto de las reglas aplicadas a `precio_noche` y `noches`.

## 3. Antes y después de la limpieza

### 3.1. Filas, duplicados y categorías

| Indicador 				| Antes de limpiar | Después de limpiar |
|---|---:|---:|
| Filas 				| 1.545 	   | 1.500 |
| Columnas 				| 18               | 19 |
| Filas duplicadas exactas 		| 45               | 0 |
| Valores distintos de `canal` 		| 9 		   | 4 |
| Valores distintos de `pais_origen`    | 12 		   | 8 |

La tabla limpia incorpora `mes_llegada`, calculada a partir de `fecha_llegada`.

### 3.2. Valores nulos por columna

| Columna        | Antes | Después |
|---|---:|---:|
| `noches` 	 | 0 	 | 6 |
| `adultos` 	 | 46 	 | 46 |
| `regimen` 	 | 61 	 | 59 |
| `pais_origen`  | 115 	 | 112 |
| `precio_noche` | 84 	 | 87 |

Los nulos no se imputan durante la limpieza inicial. En `noches` y `precio_noche` aumentan porque la función convierte valores imposibles o fuera de los límites fijados en nulos. En otras columnas, los recuentos también cambian por la eliminación de duplicados.

### 3.3. Resumen de la función de limpieza

- Filas antes: **1.545**.
- Duplicados quitados: **45**.
- Valores imposibles convertidos a nulo: **14**.
- Antelaciones recalculadas: **5**.
- Filas después: **1.500**.
- Dimensiones: `crudo.shape = (1545, 18)` y `limpia.shape = (1500, 19)`.

La función trabaja sobre una copia y conserva la tabla original `crudo`.

## 4. Preparación de datos y modelos

### 4.1. Variables utilizadas

**Variables numéricas:** `antelacion_dias`, `noches`, `adultos`, `ninos`, `precio_noche`, `peticiones_especiales`, `cliente_repetidor`, `cancelaciones_previas`, `mes_llegada`.

**Variables categóricas:** `tipo_habitacion`, `regimen`, `canal`, `pais_origen`, `tarifa`, `deposito`.

La variable objetivo es `cancelada`. `id_reserva` no se utiliza como predictor porque es un identificador. Las fechas originales se excluyen como predictores; la información temporal se representa mediante variables derivadas y se utiliza `fecha_reserva` para ordenar la partición.

### 4.2. Pipeline de preprocesamiento

El preprocesamiento se integra en un `Pipeline` y un `ColumnTransformer`:

- **Variables numéricas:** imputación de valores ausentes con la mediana y escalado con `StandardScaler`.
- **Variables categóricas:** imputación con la categoría más frecuente y codificación con `OneHotEncoder(handle_unknown="ignore")`.

El pipeline se ajusta dentro de cada pliegue de validación cruzada y únicamente con los datos de entrenamiento de ese pliegue. En la evaluación final, se ajusta con `X_train` y se aplica a `X_test`. Así se evita utilizar información del conjunto de prueba durante el aprendizaje del preprocesamiento.

### 4.3. Comparación de modelos

Se utiliza el **AUC** como métrica. Un AUC de 0,5 representa un comportamiento equivalente al azar; cuanto más se acerca a 1, mejor capacidad tiene el modelo para ordenar los casos positivos por encima de los negativos.

La validación cruzada temporal se realiza con `TimeSeriesSplit(n_splits=5)` sobre el conjunto de entrenamiento.

| Modelo 		| AUC medio ± desviación típica |
|---|---:|
| `DummyClassifier` 	| **0,500 ± 0,000** |
| Regresión logística   | **0,746 ± 0,023** |

La regresión logística supera al modelo de referencia. Su AUC medio es 0,246 puntos superior. La desviación típica de 0,023 indica que los resultados entre los pliegues fueron relativamente estables.

**Evaluación final en el conjunto de test temporal:** AUC = **0,737**.

Estos resultados indican que el modelo distingue las reservas canceladas de las no canceladas mejor que el modelo tonto. No significan que acierte el 73,7 % de las reservas: el AUC mide la capacidad de ordenación, no el porcentaje de predicciones correctas.

## 5. Preguntas que se deben confirmar con el cliente

1. **¿Los precios fuera del intervalo de 20 a 1.000 € son errores o pueden corresponder a reservas reales?** También necesitamos confirmar si un precio igual a cero representa una reserva gratuita o un dato ausente. Mientras tanto, aplicamos la regla documentada y convertimos los valores fuera del intervalo en nulos.
2. **¿Qué equivalencias oficiales debemos utilizar para los países de origen?** Hemos unificado las variantes conocidas mediante `EQUIV_PAIS`; no asignamos automáticamente las denominaciones que no están contempladas.
3. **¿Son `fecha_reserva` y `fecha_llegada` las fechas oficiales para calcular la antelación?** Hemos recalculado `antelacion_dias` a partir de ambas, pero necesitamos confirmar que esa es la regla de negocio correcta.

## 6. IA responsable

El país de origen puede actuar como variable sensible o como proxy de características personales. Si se imputa incorrectamente, se pueden mezclar reservas de países distintos y obtener patrones engañosos. Además, el modelo podría aprender diferencias de cancelación entre grupos y producir resultados desiguales.

### 6.1. Análisis por país

La tasa de cancelación observada y el número de reservas por país son:

| País de origen | Tasa media de cancelación | Reservas |
|---|---:|---:|
| DE 		 | 0,49 (49 %) 		     | 219 |
| ES 		 | 0,45 (45 %) 		     | 388 |
| FR 		 | 0,46 (46 %) 		     | 56 |
| IT 		 | 0,60 (60 %) 		     | 77 |
| NL 		 | 0,37 (37 %) 		     | 75 |
| Nordicos 	 | 0,47 (47 %) 		     | 85 |
| UK 		 | 0,48 (48 %) 		     | 349 |
| otros 	 | 0,43 (43 %) 		     | 139 |

Hay **112 reservas sin país de origen**, que representan el **7,5 %** de las 1.500 reservas limpias.

Estas diferencias son descriptivas: no demuestran que el país cause la cancelación. Además, algunos grupos tienen menos reservas que otros, por lo que sus porcentajes pueden ser menos estables. No deben utilizarse para perjudicar a clientes de un país concreto.

### 6.2. Medidas de responsabilidad

- Analizar conjuntamente la tasa de cada grupo y el número de observaciones antes de interpretar diferencias.
- No imputar automáticamente todos los países ausentes con el país más frecuente sin justificarlo.
- Revisar el rendimiento del modelo por grupos y, si procede, comparar el modelo con y sin `pais_origen`.
- Excluir `id_reserva` como predictor.
- Utilizar solo variables que estén disponibles en el momento real en que se quiere predecir la cancelación, para evitar fuga de información.
- Documentar la ayuda solicitada a la IA y comprobar manualmente el código, las cifras y las decisiones.

## 7. Cómo reproducir el trabajo

**Archivo de datos:** `reservas_sucio.csv`  
**Cuaderno:** `reto_S06.ipynb`  
**Entorno:** Google Colab

**Versiones registradas:**

- Python: `3.13.18`
- pandas: `2.2.3`
- scikit-learn: `1.6.1`

**Orden de ejecución:**

1. Importar las librerías y cargar `reservas_sucio.csv`.
2. Ejecutar el resumen de calidad y el inventario de defectos.
3. Ejecutar `limpiar_reservas(crudo)` y comprobar el antes y el después.
4. Ordenar por `fecha_reserva` y crear la partición temporal de train y test.
5. Ajustar el preprocesamiento y los modelos mediante pipeline y validación cruzada temporal.
6. Comparar `DummyClassifier` y regresión logística.
7. Entrenar el modelo final con train y evaluar una sola vez con test.
8. Ejecutar la demostración de fuga de datos del escalado.
9. Ejecutar el análisis descriptivo por país.

Para comprobar la reproducibilidad, utilizar en Colab **Entorno de ejecución → Reiniciar y ejecutar todo**. El cuaderno debe ejecutarse de arriba abajo sin errores.

## 8. Nivel extra: partición temporal y fuga de datos

### 8.1. Partición temporal justificada

Se ordenan las reservas por `fecha_reserva`. Esta fecha se utiliza porque se conoce cuando se realiza la reserva y permite simular el escenario de uso: entrenar con reservas anteriores y evaluar con reservas posteriores.

El corte se establece en el percentil 80 de la fecha de reserva.

- **Fecha de corte calculada:** `2025-08-07 04:48:00`.
- **Periodo de train:** `2024-01-01` a `2025-08-07`.
- **Periodo de test:** `2025-08-08` a `2025-12-30`.
- **Tamaño de train:** 1.200 reservas.
- **Tamaño de test:** 300 reservas.
- **Proporción de cancelaciones en train:** 0,463 (46,3 %).
- **Proporción de cancelaciones en test:** 0,500 (50,0 %).

Esta separación evita mezclar aleatoriamente reservas de periodos posteriores con las anteriores y ofrece una evaluación más parecida a una predicción sobre reservas futuras.

### 8.2. Prueba de fuga de datos al escalar

Se comparan dos procedimientos:

- **Correcto:** ajustar `StandardScaler` solo con los datos numéricos de train y utilizar ese mismo escalador para transformar train y test.
- **Con fuga:** ajustar el escalador con los datos de train y test juntos. En este caso, las estadísticas del conjunto de prueba participan en el preprocesamiento antes de la evaluación.

Resultados de las medias aprendidas por el escalador en las tres primeras variables numéricas:

| Variable (orden de `columnas_num`) | Solo train | Train + test | Diferencia absoluta |
|---|---:|---:|---:|
| `antelacion_dias` | 89,93 | 89,04 | 0,89 |
| `noches` | 5,52 | 5,49 | 0,03 |
| `adultos` | 2,24 | 2,23 | 0,00 |

La prueba muestra que incluir test cambia las estadísticas aprendidas por el escalador. Aunque las diferencias de estas columnas sean pequeñas, el procedimiento es incorrecto: el preprocesamiento estaría utilizando información del periodo que se reserva para evaluar. Por eso, el escalador debe ajustarse solo con train. El pipeline garantiza que este ajuste se repita correctamente dentro de cada pliegue de validación.

## 9. Revisión con la rúbrica

**Esta sección debe completarla una persona del equipo que no haya elaborado el apartado revisado.** No se asigna una puntuación sin esa comprobación.

**Revisado por:** ____________________  
**Fecha:** ____________________

| Criterio | Nivel (1–4) | Evidencia comprobada |
|---|---:|---|
| Corrección técnica | Pendiente de revisión | Comprobar que el cuaderno se ejecuta completo, que la limpieza conserva `crudo` y que el pipeline se ajusta solo con train. |
| Reproducibilidad | Pendiente de revisión | Ejecutar desde cero siguiendo el README y comprobar que se obtienen las mismas cifras. |
| Análisis y comunicación al cliente | Pendiente de revisión | Comprobar que hay 8–10 defectos cuantificados y que se justifican los tratamientos y la partición temporal. |
| IA responsable | Pendiente de revisión | Revisar el análisis del país de origen, los posibles sesgos y las decisiones sobre las variables utilizadas. |

**Lo primero que mejoraríamos:** confirmar con el cliente los límites de precios y las equivalencias de países; después, estudiar el rendimiento por grupos y comparar el modelo con y sin país de origen antes de utilizarlo en un contexto real.
