
# Reporte de Desempeño del Modelo de Red Neuronal

## 1. Separación y Evaluación del Modelo

El dataset utilizado corresponde al **Breast Cancer Wisconsin** incluido en *scikit-learn*.Se realizó una separación estratificada en **80% entrenamiento y 20% prueba**:

- **Conjunto de entrenamiento:** 456 muestras
- **Conjunto de prueba:** 113 muestras

Además, los datos fueron **escalados** para mejorar la estabilidad del entrenamiento de la red neuronal.

Se implementó una red neuronal con la siguiente configuración:

- **Entradas:** 30 características
- **Capa oculta:** 64 neuronas con activación *ReLU*
- **Salida:** 2 clases (benigno/maligno)
- **Tasa de aprendizaje (lr):** 0.3
- **Entrenamiento:** 100 épocas con *batch size* de 12

---

## 2. Resultados Pre-Entrenamiento (Pesos Aleatorios)

**Métricas iniciales (antes de backpropagation):**

- Exactitud: **54%**
- Recall para clase “cáncer presente”: **0.80**
- Recall para clase “cáncer ausente”: **0.10**
- F1-macro: **0.41**

➡️ El modelo sin entrenamiento se comporta como un clasificador muy sesgado hacia la clase mayoritaria (maligno), prácticamente fallando en identificar casos negativos.

---

## 3. Resultados Post-Entrenamiento (Backpropagation)

**Métricas después de 100 épocas:**

- Exactitud global: **97%**
- F1-score clase 0 (benigno): **0.96**
- F1-score clase 1 (maligno): **0.98**
- Recall promedio: **0.96**
- Matriz de confusión: solo 3 errores en 113 casos.

➡️ El modelo logra **altísima capacidad predictiva**, mostrando que la red neuronal aprendió correctamente la estructura del dataset.

---

## 4. Diagnóstico del Modelo

- **Bias (sesgo):** **Bajo**. El modelo predice ambas clases de manera equilibrada y sin preferencia marcada.
- **Varianza:** **Baja a media**. El desempeño en test es consistente con el entrenamiento, sin indicios claros de inestabilidad.
- **Nivel de ajuste:** **Fit (ajuste adecuado)**. El modelo no muestra señales de underfitting ni de overfitting en la partición train/test empleada.

---

## 5. Propuesta de Mejora

Aunque el modelo ya presenta un desempeño excelente, se podrían aplicar técnicas de mejora para reforzar su robustez en escenarios más amplios:

1. **Validación cruzada o conjunto de validación** para confirmar que el ajuste se mantiene en diferentes particiones de datos.
2. **Early Stopping** para detener el entrenamiento si no mejora en validación.
3. **Reducción de la tasa de aprendizaje** para un aprendizaje más estable.

Estas técnicas no son estrictamente necesarias en este caso, pero permitirían asegurar que el modelo mantenga su rendimiento frente a datos nuevos o distribuciones ligeramente distintas.

---

## 6. Conclusión

El modelo de red neuronal aplicado al dataset de cáncer de mama mostró un **ajuste adecuado (fit)**, alcanzando un 97% de exactitud en prueba.
No presenta señales de underfitting ni de overfitting en la separación train/test utilizada.

Con una ligera incorporación de técnicas adicionales de validación, el modelo puede consolidarse como una herramienta predictiva confiable y generalizable en aplicaciones reales.
