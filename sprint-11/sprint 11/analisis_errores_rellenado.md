# Análisis de errores · Visión artificial para el cliente (Sprint 11)

## 1. Qué se ha hecho y con qué datos

El cliente es **TurisData**. Se ha entrenado un modelo para clasificar imágenes de alojamientos y elementos turísticos en cinco clases: `apartamentos`, `camping`, `casa_rural`, `hotel` y `piscina`.

En este Colab se ha utilizado un **dataset sintético**, generado automáticamente por el propio cuaderno; no son fotografías reales descargadas de Internet. Se crearon 60 imágenes por clase (300 en total), con dibujos generados por código, ruido visual y un 12 % de imágenes ambiguas para simular etiquetas dudosas. Por tanto, no se aplica una licencia fotográfica externa: son imágenes sintéticas generadas para la práctica.

La partición fue:
- Entrenamiento: 180 imágenes (60 %).
- Validación: 60 imágenes (20 %).
- Prueba: 60 imágenes (20 %).

Las imágenes se redimensionaron a 48 × 48 píxeles. Se mantuvieron conjuntos separados para entrenar, elegir el umbral con validación y medir el resultado final con prueba.

## 2. Resultados

| Clase | Precisión | Recall |
|---|---:|---:|
| apartamentos | 0,86 | 0,86 |
| camping | 0,46 | 0,60 |
| casa_rural | 0,67 | 0,62 |
| hotel | 0,82 | 0,82 |
| piscina | 1,00 | 0,83 |

Exactitud en prueba: **transfer + fine-tuning 0,750 (75,0 %)** · **desde cero 0,683 (68,3 %)**.  
F1 macro: **transfer 0,749** · **desde cero 0,678**.

El modelo con transferencia y fine-tuning obtiene mejores resultados que el modelo entrenado desde cero.

## 3. La matriz de confusión

La matriz (filas = clase real; columnas = clase predicha), en el orden apartamentos, camping, casa_rural, hotel y piscina, es:

| Real \ Predicha | apartamentos | camping | casa_rural | hotel | piscina |
|---|---:|---:|---:|---:|---:|
| apartamentos | 12 | 0 | 0 | 2 | 0 |
| camping | 0 | 6 | 4 | 0 | 0 |
| casa_rural | 0 | 5 | 8 | 0 | 0 |
| hotel | 2 | 0 | 0 | 9 | 0 |
| piscina | 0 | 2 | 0 | 0 | 10 |

La confusión principal es entre **casa_rural y camping**: hay 5 imágenes de casa_rural clasificadas como camping y 4 de camping como casa_rural (9 errores en total). También se confunden apartamentos y hotel (4 errores en total), y piscina con camping (2 errores).

## 4. Los errores

Se muestran diez errores de mayor confianza que aparecen en la salida del Colab. La confianza es la probabilidad máxima asignada por el modelo.

| Foto | Verdadera | Predicha | Confianza | Hipótesis de causa | Mejora propuesta |
|---|---|---|---:|---|---|
| img_043.png | apartamentos | hotel | 96 % | Los edificios comparten formas y ventanas; el dibujo tiene bastante ruido. | Añadir ejemplos más variados de apartamentos y hoteles y mejorar la resolución. |
| img_045.png | camping | casa_rural | 95 % | La tienda y la casa tienen siluetas triangulares y colores parecidos. | Añadir imágenes variadas de tiendas y casas rurales y reforzar esas diferencias en el entrenamiento. |
| img_020.png | camping | casa_rural | 94 % | La forma triangular de la tienda puede parecer el tejado de una casa. | Incorporar más ejemplos de camping con distintas formas y colores. |
| img_046.png | casa_rural | camping | 93 % | La casa rural se parece visualmente a una tienda de campaña. | Revisar ejemplos ambiguos y añadir más imágenes claras de casas rurales. |
| img_012.png | piscina | camping | 92 % | El ruido y los colores del fondo pueden ocultar las características de la piscina. | Añadir piscinas con distintos encuadres y fondos. |
| img_037.png | hotel | apartamentos | 92 % | Ambos tipos de alojamiento aparecen como edificios con ventanas. | Añadir ejemplos que muestren rasgos diferenciadores de hoteles y apartamentos. |
| img_043.png | camping | casa_rural | 89 % | La tienda tiene una forma y unos colores similares a los de una casa. | Aumentar la variedad de tiendas y revisar las etiquetas ambiguas. |
| img_025.png | casa_rural | camping | 87 % | El tejado triangular y el entorno verde se parecen a una escena de camping. | Añadir ejemplos de casas rurales desde distintos ángulos y con más detalles. |
| img_041.png | casa_rural | camping | 84 % | La silueta del edificio puede confundirse con una tienda. | Mejorar la variedad del conjunto de entrenamiento y revisar las imágenes dudosas. |
| img_010.png | casa_rural | camping | 81 % | La forma triangular y el color del tejado recuerdan a una tienda de campaña. | Añadir más ejemplos diferenciados de ambas clases. |

**Conclusión del análisis:** los errores se concentran sobre todo en camping y casa_rural. Las imágenes sintéticas tienen ruido y algunas se han creado intencionadamente como ambiguas, por lo que el modelo puede aprender señales visuales poco claras. También hay confusión entre edificios de apartamentos y hoteles.

## 5. Recomendación al cliente

El umbral se eligió usando el conjunto de validación. Con un umbral de **0,7**, en la prueba el modelo decide solo el **80 %** de las fotos y acierta el **77 %** de las que acepta; el 20 % restante debe revisarlo una persona.

Recomiendo mantener la revisión humana y no utilizar el modelo para clasificar automáticamente todas las imágenes. El umbral permite que el sistema se abstenga cuando tiene poca confianza, aunque no evita todos los errores: algunas predicciones equivocadas tienen una confianza alta.

## 6. Riesgos de IA responsable

1. **Riesgo:** el dataset es sintético y pequeño, por lo que puede no representar fotografías reales de alojamientos, con iluminación, perspectivas y entornos diferentes. **Medida:** probar el modelo con fotografías reales obtenidas con permiso o licencia abierta, ampliar el conjunto de datos y evaluar de nuevo antes de ponerlo en producción.
2. **Riesgo:** el modelo puede equivocarse con mucha confianza o perjudicar a clases menos representadas o visualmente parecidas. **Medida:** mantener un umbral de confianza, derivar los casos dudosos a una persona, revisar las etiquetas y controlar los resultados por clase.

