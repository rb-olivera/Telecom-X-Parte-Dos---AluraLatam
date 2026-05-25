# Telecom X – PARTE DOS

Este proyecto es la segunda parte del Challenge de Alura Latam – Data Science. Toma como base el análisis exploratorio de la Parte Uno y avanza hacia el **modelado predictivo de churn** usando Machine Learning.

---

### 🚀 Objetivos

- Preparar los datos para modelado: encoding, escalado y división train/test.
- Entrenar y comparar modelos de clasificación: **Regresión Logística** y **Random Forest**.
- Evaluar el desempeño con métricas adecuadas para datos desbalanceados (Precision, Recall, F1-Score, ROC-AUC).
- Identificar las variables más influyentes en la predicción de churn.

---

### 🛠️ Tecnologías utilizadas

- Python 3.11
- Bibliotecas: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `joblib`
- Google Colab / Jupyter Notebook

---

### 📂 Estructura del repositorio

```
Telecom-X-Parte-Dos---AluraLatam/
│
├── Telecom_X_ParteDos.ipynb   # Notebook principal: EDA + Modelado + Evaluación
├── data/
│   └── df_clientes_clean.csv  # Dataset limpio exportado desde Parte Uno
├── image/
│   ├── Distribucion_Clientes.png
│   ├── churn_tipo_contrato.png
│   ├── cargos_mensuales_churn.png
│   └── roc_curve.png          # Curva ROC comparativa de modelos
├── models/                    # Modelos entrenados (generados al ejecutar el notebook)
│   ├── random_forest_churn.pkl
│   ├── logistic_regression_churn.pkl
│   └── scaler.pkl
├── requirements.txt
└── README.md
```

---

### ⚙️ Instalación y uso

1. Clona este repositorio:
   ```bash
   git clone https://github.com/rb-olivera/Telecom-X-Parte-Dos---AluraLatam.git
   ```

2. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

3. Abre el notebook principal:
   ```bash
   jupyter notebook Telecom_X_ParteDos.ipynb
   ```
   O ábrelo directamente en [Google Colab](https://colab.research.google.com/).

---

### 📊 Resultados del modelado

Se entrenaron y compararon dos modelos de clasificación para predecir la cancelación de clientes:

| Modelo               | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|----------------------|----------|-----------|--------|----------|---------|
| Regresión Logística  | ~0.80    | ~0.64     | ~0.56  | ~0.60    | ~0.85   |
| Random Forest        | ~0.80    | ~0.66     | ~0.49  | ~0.56    | ~0.83   |

> Los valores exactos se encuentran en el notebook al ejecutarlo. Se usó `class_weight='balanced'` para manejar el desbalance de clases (~26% churn).

**Variables más influyentes** (según Random Forest):
- `Antiguedad_Meses` — clientes nuevos tienen mayor riesgo
- `Cargos_Mensuales` / `Cargos_Totales` — cargos altos sin valor percibido aumentan el churn
- `Tipo_Contrato_Two year` — contratos largos reducen significativamente el churn
- `Servicio_Internet_Fiber optic` — asociado a mayor tasa de abandono

---

### 🔎 Principales hallazgos

- Los clientes con **contratos mensuales** presentan una tasa de abandono 4× mayor que los de contratos anuales.
- La **antigüedad baja** (primeros meses) es el predictor más fuerte de churn.
- Los clientes con **cargos mensuales altos + contrato mensual + sin servicios adicionales** forman el segmento de mayor riesgo.
- El método de pago **cheque electrónico** se asocia con mayor churn que los pagos automáticos.

---

### 💡 Recomendaciones

1. **Retención temprana**: programa de onboarding proactivo en los primeros 90 días.
2. **Migración de contratos**: incentivos para pasar de mensual a anual (descuentos, meses bonificados).
3. **Scoring de riesgo**: usar el modelo RF para identificar clientes en riesgo antes de que cancelen.
4. **Revisión de precios en Fiber optic**: la alta tasa de churn sugiere problemas de percepción de valor.

---

### 👩‍💻 Autora

Proyecto desarrollado por [Rebeca Olivera](https://github.com/rb-olivera) como parte del programa de formación en Data Science – Alura Latam & Oracle.
