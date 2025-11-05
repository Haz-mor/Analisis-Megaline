# 📱 Análisis-Megaline

## 🌟 Resumen del Proyecto

Este proyecto consiste en analizar el comportamiento de los clientes de la compañía de telecomunicaciones **Megaline**. El objetivo es construir un modelo de Machine Learning para recomendar uno de los dos nuevos planes de la compañía, **Smart** o **Ultra**, basándose en el comportamiento de uso de un cliente.

Se llevó a cabo un proceso de *pipeline* completo, que incluyó la exploración de datos, el entrenamiento y la comparación de diferentes modelos de clasificación, la selección del mejor modelo y una prueba de cordura (*sanity check*) para asegurar su rendimiento.

## 🎯 Objetivo

Desarrollar un modelo de clasificación que recomiende el plan de Megaline (Smart o Ultra) a un nuevo cliente con la **mayor exactitud posible**.

## 📊 Datos (Dataset `users_behavior.csv`)

El conjunto de datos utilizado es `users_behavior.csv`. Contiene **3214 entradas** y **5 columnas** de datos.

### 🏷️ Características (Features)

Todas las características de entrada son de tipo `float64`, sin valores nulos:

* `calls`
* `minutes`
* `messages`
* `mb_used`

### 🎯 Variable Objetivo (Target)

* `is_ultra`: Variable binaria que indica si el plan del cliente es Ultra (1) o Smart (0). Es de tipo `int64`.

| Columna | Tipo de Dato | Recuento No Nulo |
| :--- | :--- | :--- |
| `calls` | `float64` | 3214 |
| `minutes` | `float64` | 3214 |
| `messages` | `float64` | 3214 |
| `mb_used` | `float64` | 3214 |
| `is_ultra` | `int64` | 3214 |

## 🧪 Metodología

### División de Datos

El dataset fue dividido en tres conjuntos para entrenamiento, validación y prueba:

* Conjunto de entrenamiento: **1928** muestras.
* Conjunto de validación: **643** muestras.
* Conjunto de prueba: **643** muestras.

### Entrenamiento y Comparación de Modelos

Se entrenaron tres modelos diferentes y se ajustaron sus hiperparámetros para ver cuál se desempeñaba mejor en el conjunto de validación, con el objetivo de encontrar el modelo más preciso antes de la prueba final.

| Modelo | Métrica | Mejor Exactitud (Validación) | Hiperparámetros Óptimos |
| :--- | :--- | :--- | :--- |
| **Bosque Aleatorio** | Exactitud | **0.7978** | `{'estimators': 50, 'depth': 10}` |
| Árbol de Decisión | Exactitud | 0.7745 | Profundidad de 7 |
| Regresión Logística | Exactitud | 0.6936 | N/A |

**Conclusión de Modelado:** El **Bosque Aleatorio** fue seleccionado como el mejor modelo para la fase final.

## 🚀 Prueba Final y Conclusión

El modelo seleccionado (Bosque Aleatorio) se evaluó en el conjunto de prueba y se comparó con un modelo de referencia (*dummy*) que predice la opción más común ('Smart' = 0).

* **Exactitud del Modelo de Referencia (Base):** 0.6952
* **Exactitud de nuestro modelo (Bosque Aleatorio):** **0.7947**

**Resultado:**
> **¡El modelo ha pasado la prueba de cordura!**
>
> Es significativamente más preciso que simplemente adivinar la opción más común.
