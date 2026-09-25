# EV2_IA_Laboratorio

Laboratorio Práctico: Predicción de Costos de Envío (Logística E-Commerce)

## Contexto

Una empresa de logística de e-commerce necesita estimar el costo total de envío
(`costo_envio`, en USD) de cada paquete antes de procesarlo, para ajustar en tiempo
real las tarifas de cobro de su sitio web.

## ¿Qué hace el programa?

El notebook `E2 - LAB/Evaluacion2_IA_Grupo5.ipynb` resuelve el laboratorio en cuatro pasos:

1. **Carga y limpieza de datos.** Lee `lab_costos_envio.csv` y trata los valores nulos
   para dejar el dataset listo para el modelado.
2. **Codificación de variables.** Separa las predictoras (`X`) de la variable objetivo
   (`y = costo_envio`) y aplica codificación One-Hot Encoding (`get_dummies`) para
   convertir las variables categóricas (`tipo_servicio`, `es_fragil`) en numéricas.
3. **Entrenamiento.** Divide los datos en 80% entrenamiento y 20% prueba
   (`random_state=42`) y entrena un modelo de **Regresión Lineal**
   (`LinearRegression` de scikit-learn).
4. **Evaluación.** Predice sobre el conjunto de prueba y calcula **R²** y **MAE**,
   comparándolos con los umbrales mínimos de aprobación. Finalmente muestra una tabla
   con los primeros 10 registros contrastando el costo real, el predicho y su diferencia.

## Variables del dataset

| Columna | Descripción |
| --- | --- |
| `id_paquete` | Identificador del paquete (no se usa como predictora) |
| `peso_kg` | Peso del paquete en kilogramos |
| `distancia_km` | Distancia de envío en kilómetros |
| `tipo_servicio` | Categoría del servicio de envío (Express / Estandar) |
| `es_fragil` | Indicador de si el paquete es frágil (Si / No) |
| `costo_envio` | Variable objetivo: costo de envío en USD |

## Resultados obtenidos

| Métrica | Umbral mínimo | Resultado obtenido | Cumple |
| --- | --- | --- | --- |
| R² | > 0.90 | **0.9830** | Sí |
| MAE | ≤ 3.50 USD | **2.8098 USD** | Sí |

## Cómo ejecutarlo

Abrir el notebook en Jupyter o Google Colab y ejecutar las celdas en orden. La primera
celda verifica que exista el archivo `lab_costos_envio.csv` y lo descarga
automáticamente desde el repositorio si no se encuentra.

## Estructura

```
E2 - LAB/
├── 620454-Lab-Regresión.pdf       # Enunciado del laboratorio
├── Evaluacion2_IA_Grupo5.ipynb    # Notebook con la solución
└── lab_costos_envio.csv           # Dataset de costos de envío
```
