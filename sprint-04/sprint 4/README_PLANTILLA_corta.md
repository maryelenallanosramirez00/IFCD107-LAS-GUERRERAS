# Herramientas internas · TurisData Canarias

> **README corto** para la entrega en nivel mínimo con explicación. Cópialo como `README.md`, sustituye lo que está entre `<...>` y borra este aviso. Si tu equipo llega más lejos, usa `README_PLANTILLA.md`.

**Equipo:** <Las Guerreras> · **Fecha:** <04/11/2026>

## Qué hace
Este script en Python (`kpis.py`) lee el fichero CSV de reservas de TurisData Canarias, calcula tres KPIs (ocupación aproximada, ingreso medio por reserva y tasa de cancelación por canal) y los exporta a un fichero JSON. Controla los errores más habituales (fichero inexistente, columnas que faltan, filas defectuosas) mostrando un mensaje claro y devolviendo un código de salida en lugar de romperse.


## Cómo se ejecuta y se prueba
```
python kpis.py reservas_turisdata.csv salida.json --capacidad 40
python test_kpis.py
```
Salida esperada: OK: 6000 reservas analizadas, 0 descartadas -> salida.json

Resultado de las pruebas: <12 de 12 superadas>

## Quién hizo qué
| Parte 							| La escribí yo 	| La copié y la expliqué |
|---|---|---|
| `tasa_cancelacion_por_canal` e `ingreso_medio_por_reserva` 	| <Las guerreras> 	| <Las guerreras> |
| `_convertir_fila` y `leer_reservas`				| <Las guerreras>	| <Las guerreras> |
| `exportar_json` y `main`					| <Las guerreras>	| <Las guerreras> |

## Explicación de una función:
tasa_cancelacion_por_canal
total = {}
    canceladas = {}
    for r in reservas:
        canal = r["canal"]
        total[canal] = total.get(canal, 0) + 1
        if r["cancelada"] == 1:
            canceladas[canal] = canceladas.get(canal, 0) + 1
    tasas = {}
    for canal in total:
        tasas[canal] = round(100 * canceladas.get(canal, 0) / total[canal], 1)
    return tasas

Con esta función calculamos qué porcentaje de reservas se cancelan en cada canal.

Creamos dos diccionarios: total, donde apuntamos cuántas reservas tiene cada canal, y canceladas, donde apuntamos solo las canceladas. 
Recorremos las reservas una por una y vamos sumando. Con .get(canal, 0) le decimos que, si el canal todavía no existe, empiece desde 0 en vez de dar error.

Al final calculamos el porcentaje.

## Errores que controla
En la parte de Terminal nos aparece el siguiente error, por ejemplo cuando le quitamos columnas, no aparece este mensaje. ERROR: Faltan columnas obligatorias: ['precio_noche']

## Uso de IA
En este caso no hemos utilizado la IA, solamente el solucionario y a nuestro profe.

## Qué mejoraríamos
Nuestro conocimiento de python
