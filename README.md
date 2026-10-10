# Comparación de modelos preentrenados para análisis de sentimientos

Actividad 4 — Gestión de proyectos de inteligencia artificial.

## Propósito y caso de uso
Comparar tres modelos de Hugging Face para clasificar opiniones de clientes de supermercados en español como POS, NEU o NEG.

## Ecosistema Hugging Face
- **Models:** modelos preentrenados y fichas técnicas.
- **Datasets:** conjuntos de datos para entrenamiento y evaluación.
- **Spaces:** aplicaciones interactivas para probar prototipos.

## Datos
`data/opiniones_supermercado.csv`: 30 opiniones **sintéticas** creadas para la práctica (10 por clase). No son reseñas reales. Campos: `id` identificador, `texto` opinión, `etiqueta` clase de referencia, `origen` procedencia.

## Modelos
- `pysentimiento/robertuito-sentiment-analysis`
- `cardiffnlp/twitter-xlm-roberta-base-sentiment`
- `nlptown/bert-base-multilingual-uncased-sentiment` (se agrupan 1–2 estrellas como NEG, 3 como NEU y 4–5 como POS).

## Reproducción en Google Colab
1. Abrir `notebooks/Actividad4_Comparacion_Modelos.ipynb`.
2. Activar GPU desde Entorno de ejecución > Cambiar tipo de entorno de ejecución.
3. Ejecutar las celdas en orden e instalar dependencias.
4. La autenticación con Hugging Face es opcional para los modelos públicos; si se requiere, usar Secrets con `HF_TOKEN`, nunca pegarlo en código.
5. Subir `data/opiniones_supermercado.csv` cuando lo pida el notebook.
6. Guardar CSV y PNG generados en `results/`. Verificar la GPU, versiones y fecha de ejecución.
7. Para publicar el repositorio, cargar toda esta estructura a GitHub sin incluir tokens ni información privada.

## Resultados observados
| Modelo | Accuracy | F1 macro | Latencia media (ms) |
|---|---:|---:|---:|
| RoBERTuito | 0.8333 | 0.8333 | 12.59 |
| XLM-RoBERTa | 0.9333 | 0.9327 | 22.57 |
| BERT multilingüe | 0.7667 | 0.7277 | 11.33 |

XLM-RoBERTa lideró accuracy y F1 macro en este conjunto; BERT multilingüe fue más rápido. Son resultados de una única ejecución reportada por el estudiante, no una validación de producción.

## Límites y mejoras
Solo 30 ejemplos sintéticos y una medición de latencia por modelo; no se estima variabilidad entre ejecuciones ni generalización. Antes de desplegar: usar opiniones reales autorizadas, ampliar el conjunto de evaluación, medir desempeño por clase y repetir latencias en condiciones controladas. Las licencias, versiones, tamaños y requisitos de uso de cada checkpoint deben confirmarse en las fichas oficiales antes de cualquier distribución o uso comercial.

## Organización
- `data/`: dataset.
- `notebooks/`: notebook de Colab.
- `results/`: métricas, predicciones y gráficos observados.
- `src/`: scripts de soporte.
- `requirements.txt`: dependencias.

## Fuente
Datos sintéticos redactados para este ejercicio; el procedimiento de evaluación está contenido en el notebook.
