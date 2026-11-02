
---

```markdown
# Modelo Supervisado con Scikit-Learn (Detección de Malware)

Este repositorio contiene una prueba de concepto para clasificar tráfico de red como normal o malicioso utilizando un modelo de aprendizaje supervisado (K-Nearest Neighbors) con Python y Scikit-Learn.

El objetivo fue analizar el comportamiento del algoritmo al enfrentarse a conjuntos de datos reales de capturas de tráfico infectado. Los datos provienen de la campaña *2017-01-19-pseudoDarkleech-Rig-V-sends-Cerber* (tomados originalmente de [malware-traffic-analysis.net](https://www.malware-traffic-analysis.net/2017/01/19/index2.html)).

## Contenido del repositorio

- `MetodoSupervisadoSklearn.py`: Script principal que realiza el preprocesamiento, entrenamiento y predicción.
- `Analisis_de_trafico_sklearn.ipynb`: El mismo flujo de trabajo en formato Jupyter Notebook, útil para seguir el paso a paso y visualizar las gráficas de reducción de dimensionalidad.
- `trafico.csv`: Dataset utilizado para el entrenamiento del modelo.
- `trafico_prueba_2016.csv` y `trafico_prueba_2017.csv`: Conjuntos de datos reservados para evaluar la predicción del modelo con datos no vistos.

## Requisitos

El proyecto está desarrollado en Python 3. Necesitarás las siguientes librerías:

```bash
pip install pandas numpy scikit-learn matplotlib mglearn
```

## Cómo ejecutarlo

1. Clona el repositorio:
   ```bash
   git clone https://github.com/damianra/ModeloSupervisadoSklearn.git
   cd ModeloSupervisadoSklearn
   ```

2. Para ver el análisis paso a paso con las visualizaciones, abre el notebook:
   ```bash
   jupyter notebook Analisis_de_trafico_sklearn.ipynb
   ```

3. Para ejecutar el script directamente desde la terminal:
   ```bash
   python MetodoSupervisadoSklearn.py
   ```
   *Nota: Asegúrate de que los archivos CSV estén en el mismo directorio de ejecución.*

## Flujo técnico (resumen)

1. **Preprocesamiento**: Se agrupan los paquetes por características clave (Tiempo, Puertos, IP fuente, Protocolo, Longitud) y se calcula su frecuencia.
2. **Codificación**: Se usa `LabelEncoder` para transformar las variables categóricas en numéricas y que el algoritmo pueda procesarlas.
3. **Escalado y Reducción**: Se aplica `MinMaxScaler` y PCA (Análisis de Componentes Principales) para normalizar los datos y permitir su visualización en 2D con `mglearn`.
4. **Modelo**: Se entrena un `KNeighborsClassifier` (con k=2) usando los datos de entrenamiento etiquetados (M = Malware, N = Normal).
5. **Evaluación**: Se aplica el modelo a los archivos de prueba para predecir la etiqueta de tráfico desconocido.

## Notas y limitaciones

- El modelo muestra un porcentaje de acierto muy alto en estos datasets específicos, pero hay que tener en cuenta que se trata de datos de 2016-2017.
- Este proyecto es un ejercicio práctico y de experimentación. No está diseñado para ser usado en un entorno de producción real sin antes reentrenarlo con tráfico actual, ampliar las características (features) y aplicar técnicas de validación cruzada para descartar overfitting.

---
*Desarrollado por Damian Ramirez.*
```
