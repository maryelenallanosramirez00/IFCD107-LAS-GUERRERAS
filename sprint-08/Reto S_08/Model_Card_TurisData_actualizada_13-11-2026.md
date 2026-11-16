# Model card · Predicción de cancelaciones de reservas · TurisData Canarias

**Equipo:** Las Guerreras (Cande, Montse, Marysol y Elena) · **Fecha:** 13/11/2026 · **Versión del modelo:** 1.0 · **Contacto:** Pendiente de asignar.

> Documento de 1–2 páginas para el cliente y para quien mantenga el modelo. Sé concreto y honesto con los límites.

## 1. Resumen
El modelo estima la probabilidad de que una reserva se cancele. Su objetivo es ayudar al equipo de TurisData a identificar reservas que podrían necesitar seguimiento y a planificar mejor la actividad. Las predicciones sirven como apoyo al personal responsable; no deben convertirse en decisiones automáticas.

## 2. Modelo campeón
- **Familia y algoritmo:** Modelo lineal de clasificación: regresión logística (`logistica`).
- **Hiperparámetros finales:** `max_iter=1000`.
- **Preprocesado:** Pipeline. Variables numéricas: imputación con la mediana y escalado. Variables categóricas: imputación con la categoría más frecuente y codificación One-Hot.
- **Librerías y versiones:** Python 3.13.18, NumPy 2.4.6, pandas 2.2.3 y scikit-learn 1.6.1. No se han confirmado en la ejecución compartida las versiones de las demás librerías.

## 3. Por qué este campeón (y no otro)
| Criterio | Peso acordado | Resultado del campeón | Mejor rival y diferencia |
|---|---|---|---|
| Rendimiento (AUC en validación cruzada) | 50 % | 0,7546 ± 0,0136 | `arbol_podado`: 0,7194; diferencia aproximada de 0,035 a favor de la logística. |
| Explicabilidad (1–5) | 30 % | 4 | `arbol_podado`: 5; sus reglas son más fáciles de leer, aunque su AUC es menor (0,719). |
| Coste (ajuste, predicción, tamaño) | 20 % | 0,057 s de ajuste; 12,1 ms para predecir 1.000 reservas; 4,2 KB | `arbol_podado`: 0,037 s; 8,8 ms por 1.000 reservas; 11,0 KB. Como referencia, `random_forest` ocupa aproximadamente 11.847 KB. Los tiempos y tamaños pueden variar según el ordenador. |

**Puntuación global con los pesos acordados:** `logistica` 0,920; `arbol_podado` 0,904; `lightgbm_ajustado` 0,684. Los valores de coste y la puntuación global pueden variar ligeramente entre equipos.

**Análisis de sensibilidad:** Sí, el campeón cambia cuando cambian los pesos:

| Pesos (rendimiento / explicabilidad / coste) | Campeón |
|---|---|
| 0,5 / 0,3 / 0,2 (acordados) | `logistica` |
| 0,8 / 0,1 / 0,1 (solo rendimiento) | `logistica` |
| 0,4 / 0,4 / 0,2 (equilibrado) | `arbol_podado` |
| 0,2 / 0,6 / 0,2 (explicabilidad primero) | `arbol_podado` |

Con los pesos acordados gana la regresión logística. Si se da más importancia a la explicabilidad, gana el árbol podado.

## 4. Datos de entrenamiento
- **Fuente, periodo, número de reservas y tasa de cancelación:** Archivo `reservas_turisdata.csv`, descargado desde la carpeta `datos/` del repositorio del curso IFCD107. Contiene 6.000 reservas, con fechas desde el 01/01/2024 hasta el 30/12/2025. Hay 2.754 cancelaciones y 3.246 reservas no canceladas: tasa global del 45,9 %. Se utilizaron 4.800 registros para entrenamiento y 1.200 para test.
- **Variables usadas y excluidas:** Las 15 variables de entrada son `antelacion_dias`, `noches`, `adultos`, `ninos`, `precio_noche`, `peticiones_especiales`, `cliente_repetidor`, `cancelaciones_previas`, `temporada_alta`, `tipo_habitacion`, `regimen`, `canal`, `pais_origen`, `tarifa` y `deposito`. La variable objetivo es `cancelada`. `temporada_alta` se calcula a partir del mes de `fecha_llegada` (enero, febrero, marzo, julio, agosto y diciembre). `fecha_reserva` y `fecha_llegada` se leen como fechas, pero no se incluyen directamente entre las variables predictoras. No se ha facilitado un listado de otras columnas excluidas ni sus motivos.
- **Limitaciones:** El periodo disponible abarca dos años. No se ha confirmado si el conjunto es sintético o real ni si todos los canales y grupos de clientes están suficientemente representados.

## 5. Rendimiento
- **Validación cruzada (train):** AUC 0,7546 ± 0,0136 · AP 0,7183. Recall y precisión con el umbral elegido: pendientes de recuperar del Sprint 7 o de calcular con el procedimiento indicado por el profesor.
- **Test (una sola evaluación):** AUC 0,7623 para `logistica`. El test se utilizó una sola vez para evaluar al campeón.
- **Umbral de decisión:** debe utilizarse el umbral definido y justificado en el Sprint 7, comparando el coste de una cancelación no prevista con el de una falsa alarma. El valor numérico de ese umbral no aparece en los datos compartidos.
- **Rendimiento por subgrupos:** no se han compartido resultados desglosados por canal, país o tipo de tarifa; queda pendiente de medir.

## 6. Uso previsto y usos NO previstos
- **Uso previsto:** Estimar el riesgo de cancelación de una reserva y ayudar al personal de TurisData a priorizar revisiones y acciones de seguimiento.
- **NO usar para:** Denegar reservas, cobrar más a clientes por su país de origen, penalizar automáticamente a clientes ni tomar decisiones sin revisión humana.

## 7. Explicabilidad
La regresión logística tiene una valoración de explicabilidad de 4 sobre 5. Puede explicarse al gerente mostrando cómo influyen las variables de entrada en la probabilidad estimada. Para justificar una predicción concreta hay que consultar los coeficientes del modelo y relacionarlos con las variables. No se han compartido todavía los coeficientes ni un análisis de importancia de variables, por lo que esa explicación concreta queda pendiente.

## 8. Riesgos e IA responsable
- **Sesgos posibles y medición:** Podrían existir diferencias de rendimiento por país de origen, canal o tipo de tarifa. No se han compartido mediciones por subgrupos.
- **Impacto de los errores:** Una falsa alarma puede provocar contactos innecesarios con clientes; una cancelación no detectada puede dificultar la planificación del alojamiento.
- **Medidas aplicadas y pendientes:** El modelo se plantea como apoyo a la decisión, no como mecanismo automático. Queda pendiente medir resultados por subgrupos, definir el umbral operativo y establecer un proceso de revisión humana.

## 9. Mantenimiento
- **Qué vigilar en producción:** Cambios en las variables de entrada, tasa real de cancelación frente a la prevista y rendimiento del modelo cuando haya nuevos datos etiquetados.
- **Frecuencia de reentrenamiento:** No se ha fijado una frecuencia. Se recomienda revisar periódicamente el rendimiento y valorar un nuevo entrenamiento si se observa un deterioro sostenido o cambios relevantes en los datos.
- **Coste y responsable:** No se dispone de una estimación económica ni de una persona responsable asignada; deben definirse antes del despliegue.

## 10. Cómo reproducirlo
Semillas: `SEMILLA = 42` para los modelos y la validación cruzada; `SEMILLA_TEST = 7` para la partición entrenamiento/test. Versiones comprobadas: Python 3.13.18, NumPy 2.4.6, pandas 2.2.3 y scikit-learn 1.6.1. Ejecutar `reto_S08.ipynb` en orden y conservar `leaderboard_S08.csv`. La evaluación final del test corresponde únicamente a `logistica` y no debe repetirse para comparar otros modelos.
