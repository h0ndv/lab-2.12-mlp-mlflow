# IEI097 · Actividad 2.12 — MLP + MLflow

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/h0ndv/lab-2.12-mlp-mlflow/blob/main/IEI097_Lab2.12_MLP_MLflow.ipynb)

Perceptrón multicapa para clasificar tumores de mama (Breast Cancer Wisconsin, 569 registros, 30 variables) con 12 experimentos registrados en MLflow y la interfaz publicada con ngrok.

## Contenido

| Archivo | Qué es |
|---|---|
| `IEI097_Lab2.12_MLP_MLflow.ipynb` | Notebook ejecutado de punta a punta, con hipótesis, experimentos y respuestas de cierre |
| `IEI097_Lab2.12_MLP_MLflow.pdf` | El mismo notebook en PDF, con las salidas y las figuras |
| `runs.csv` | Las 12 ejecuciones exportadas con `mlflow.search_runs()` |
| `datos/breast_cancer.csv` | Copia del conjunto de datos para reproducir sin credenciales de Kaggle |
| `evidencias/` | Capturas de la interfaz de MLflow y figuras generadas por el notebook |

## Cómo reproducir

1. Abrir el notebook en Colab con el badge de arriba.
2. Crear el secreto `NGROK_AUTHTOKEN` en Colab Secrets y habilitar su acceso desde el notebook.
3. Ejecutar todas las celdas en orden.

La semilla es el número de lista sin puntos ni dígito verificador: `SEED = 20217700`. La partición, la inicialización de los pesos y el orden de las muestras quedan fijados con esa semilla.

## Resultados

| Run | Escalado | Capas | Activación | Exactitud prueba | Recall maligno |
|---|---|---|---|---|---|
| A | No | (30,) | relu | 0,9561 | 0,9048 |
| B | Sí | (30,) | relu | 0,9912 | 0,9762 |
| C | Sí | (64, 32) | relu | 0,9912 | 0,9762 |
| D | Sí | (64, 32) | tanh | 0,9737 | 0,9524 |
| E | Sí | (64, 32) | relu, alpha 0,5 | 0,9912 | 0,9762 |
| F | Sí | (64, 32) | relu, lr 0,0005 | 0,9912 | 0,9762 |

Cinco semillas sobre la configuración C: exactitud entre 0,9825 y 0,9912, recall maligno entre 0,9524 y 0,9762. La réplica con la semilla original coincide con C en todas las métricas.

## Entorno

pandas 2.3.3, scikit-learn 1.9.1, mlflow 3.1.4, Python 3.12. Las versiones quedan registradas al inicio del notebook.
