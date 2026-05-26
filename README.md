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
