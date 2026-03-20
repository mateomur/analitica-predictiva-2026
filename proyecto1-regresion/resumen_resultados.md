# 📊 Resumen de Resultados — Proyecto 1: Regresión

**Dataset:** California Housing (scikit-learn)  
**Variable objetivo:** `MedHouseVal` — Valor medio de vivienda (en cientos de miles de USD)  
**Integrantes:** Christopher Andres Obando Rivera · Mateo Murcia Valles

---

## Comparación de modelos

| Modelo | R² Score | MAE (USD) | Notas |
|---|---|---|---|
| Regresión Lineal | 0.6352 | $47,240 | Línea base |
| Reg. Regularizada (Ridge / Lasso / ElasticNet) | 0.6352 | $47,240 | Sin mejora sobre lineal — datos bien escalados |
| **Random Forest** | **0.7825** | **$32,560** | ✅ **Mejor modelo** |
| SVR (kernel RBF) | 0.7511 | $35,790 | Buen desempeño, costoso computacionalmente |
| Red Neuronal (MLP) | 0.7594 | $36,670 | Competitivo, sensible a hiperparámetros |

---

## Mejores hiperparámetros encontrados

| Modelo | Parámetros óptimos (GridSearchCV) |
|---|---|
| Ridge | `alpha = 0.01` |
| Lasso | `alpha = 0.0001` |
| ElasticNet | `alpha = 0.0001`, `l1_ratio = 0.2` |
| Random Forest | `n_estimators = 100`, `max_depth = None`, `min_samples_split = 2` |
| SVR | `C = 10`, `epsilon = 0.2`, `kernel = 'rbf'` |
| Red Neuronal | `hidden_layer_sizes = (50,)`, `learning_rate_init = 0.01` |

---

## Conclusiones

- **La regularización no aportó mejora** sobre la regresión lineal. Esto sugiere que las variables predictoras ya estaban bien escaladas y que el modelo lineal no sufría de overfitting severo.
- **Random Forest fue el modelo ganador**, con el R² más alto (0.7825) y el menor error absoluto ($32,560). Su capacidad para capturar relaciones no lineales entre variables como `MedInc` y la ubicación geográfica (`Latitude`, `Longitude`) explica su superioridad.
- **SVR y la Red Neuronal** mostraron resultados competitivos, pero requieren mayor costo computacional y ajuste de hiperparámetros más cuidadoso.
- El **R² máximo alcanzado fue ~0.78**, lo que indica que aún hay variabilidad en el precio de las viviendas no explicada por las variables disponibles (factores como calidad de la construcción, acceso a servicios, etc., no están en el dataset).
