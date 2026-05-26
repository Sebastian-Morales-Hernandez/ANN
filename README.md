# Clasificación de Gestos de la Lengua de Señas Mexicana (LSM) mediante sEMG y Redes Neuronales Artificiales (ANN)

Este repositorio contiene el desarrollo de un sistema de adquisición, preprocesamiento y clasificación de señales de electromiografía de superficie (sEMG) para el reconocimiento de las señas **A, B y C** de la Lengua de Señas Mexicana (LSM). El proyecto ha sido desarrollado utilizando el sistema de adquisición **BIOPAC MP36** y una arquitectura de **Red Neuronal Artificial (ANN)** implementada en TensorFlow/Keras.

## 👥 Equipo de Desarrollo
**Aguilar Hernández Ximena Laís**
**Azamar Solano Víctor Felipe**
**Cabrera Martínez Danna Paola**
**Morales Hernández Sebastián**

*Facultad de Ingeniería / Programa de Ingeniería Biomédica, Universidad Veracruzana.*

---

## 📁 Estructura del Repositorio

Para mantener el repositorio organizado y con un aspecto profesional, se recomienda la siguiente estructura de archivos:

```text
├── README.md                 # Documentación principal del proyecto (este archivo)
├── src/                      # Código fuente del proyecto
│   └── ann3musculos.py       # Script principal de procesamiento y entrenamiento de la ANN
└── data/                     # Carpeta con las tomas de muestras en formato de texto plano (.txt)
    ├── (Archivos de los sujetos de prueba)
```

📊 Descripción del Dataset y Metodología
1. Adquisición de Datos
Hardware: Sistema BIOPAC MP36.

Frecuencia de Muestreo (fs): 2000 Hz.

Sujetos: 4 sujetos de prueba (independientes al equipo de desarrollo) en 2 sesiones de registro.

Variación Metodológica: Se incluyó un cambio en el diseño experimental basado en la diferencia del número de músculos capturados (configuración espacial de canales), aportando mayor variabilidad y robustez al dataset.

Clases: 3 clases correspondientes a las señas estáticas A, B y C de la LSM.

2. Pipeline de Preprocesamiento
Filtrado Pasabanda: Filtro Butterworth de 4.º orden con frecuencias de corte de 20 Hz a 450 Hz para eliminar artefactos de movimiento y alta frecuencia.

Rectificación: Aplicación de valor absoluto a la señal filtrada.

Ventaneo: Segmentación en ventanas continuas. Se generó un total de 234 ventanas útiles.

3. Extracción de Características (Features)
Por cada ventana temporal se extrajeron 4 descriptores matemáticos esenciales:

Root Mean Square (RMS): Indicador de la energía y potencia de la contracción.

Mean Absolute Value (MAV): Indicador de la intensidad media de la señal rectificada.

Varianza (VAR): Medida de la dispersión y dinámica del ruido.

Waveform Length (WL): Longitud de la onda, que describe la complejidad temporal de la señal (característica dominante en el dataset).

🧠 Arquitectura de la Red Neuronal (ANN)
El modelo clasificador consiste en una red neuronal secuencial totalmente conectada (Dense) optimizada con técnicas de regularización para evitar el sobreajuste (overfitting):

Capa de Entrada: Ajustada a las 4 características extraídas.

Capa Oculta 1: 32 neuronas con activación ReLU + Batch Normalization + Dropout (20%).

Capa Oculta 2: 16 neuronas con activación ReLU + Batch Normalization + Dropout (20%).

Capa de Salida: 3 neuronas con activación Softmax (una por cada seña de la LSM).

Compilación:

Optimizador: Adam (Learning Rate = 0.005).

Función de Pérdida: Categorical Crossentropy.

Callbacks: Early Stopping (paciencia de 15 épocas) y Reduce Learning Rate on Plateau.

📈 Resultados Preliminares
División del Dataset: 85% para desarrollo (con división interna de 15% para validación) y 15% para prueba final aislado.

Métrica de Desempeño: Se alcanzó una precisión (Accuracy) del 88.89% en el conjunto de prueba que el modelo jamás vio durante el entrenamiento.

Análisis de Convergencia: El uso combinado de Batch Normalization y Dropout permitió obtener curvas de aprendizaje estables, donde el conjunto de validación mantuvo un rendimiento óptimo, demostrando una alta capacidad de generalización arquitectónica.

🛠️ Requisitos e Instalación
Para ejecutar este código de forma local o en un entorno como Google Colab, necesitas tener instaladas las siguientes librerías de Python:

Bash
pip install numpy pandas scipy matplotlib tensorflow scikit-learn
Ejecución del Proyecto
Clona este repositorio:

Bash
git clone [https://github.com/Sebastian-Morales-Hernandez/ANN.git](https://github.com/Sebastian-Morales-Hernandez/ANN.git)
Asegúrate de colocar los archivos .txt dentro de la carpeta data/ o en la raíz del script según corresponda. (Nota: Debido al tamaño de los archivos a 2000 Hz, el dataset completo podría estar enlazado externamente).

Ejecuta el script de entrenamiento:

Bash
python src/ann3musculos.py
📜 Licencia y Referencias
Este proyecto se realiza con fines académicos.

Artículo Base de Referencia: Dunai, L. et al. (2025). Prosthetic Hand Based on Human Hand Anatomy Controlled by Surface Electromyography and Artificial Neural Network. MDPI Technologies. DOI: 10.3390/technologies13010021.
