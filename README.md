# kmeans-vanish-segmentation

# <img src="https://img.icons8.com/?size=50&id=wBVr33b_6fzI&format=png&color=000000" align="center"/> K-Means Clustering: Vanish Market Segmentation
### Segmentación de Mercado con K-Means de Marca Vanish

> **EN** · Unsupervised Machine Learning project applying K-Means clustering to identify key market segments for the Vanish brand within a retail
> cleaning products dataset. Four distinct segments were identified, providing strategic insights for market positioning and growth opportunities.
>
> **ES** · Proyecto de Machine Learning no supervisado que aplica K-Means clustering para identificar segmentos clave de mercado de la marca Vanish
> dentro de un dataset de productos de limpieza retail. Se identificaron 4 segmentos distintos con hallazgos estratégicos para posicionamiento y
> oportunidades de crecimiento.

---

## <img src="https://img.icons8.com/?size=40&id=Ihw7rsNxtanQ&format=png&color=000000" align="center"/> Overview / Descripción

**Context / Contexto:**
Vanish represents **19.7% of total portfolio sales** across a dataset of 122,002 transactions (Jan 2022–Jul 2023). 
This project segments Vanish's 28,377 records into meaningful clusters to guide strategic decisions.

**Vanish representa el 19.7% de las ventas totales** del portafolio sobre 122,002 transacciones (ene 2022–jul 2023). 
Este proyecto segmenta los 28,377 registros de Vanish en clusters significativos para orientar decisiones estratégicas.

---

## <img src="https://img.icons8.com/?size=40&id=80431&format=png&color=000000" align="center"/> Tools / Herramientas

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-b48cba?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-B8A9C9?style=flat&logo=scikit-learn&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-d19999?style=flat&logo=numpy&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-487070?style=flat)
![Jupyter](https://img.shields.io/badge/Jupyter-C4A882?style=flat&logo=jupyter&logoColor=white)

---

## <img src="https://img.icons8.com/?size=40&id=81350&format=png&color=000000" align="center"/> Methodology / Metodología

### <img src="https://img.icons8.com/?size=25&id=TyCKx8nVDY0n&format=png&color=000000" align="center"/> Data Preparation / Preparación de Datos
- Filtered 28,377 Vanish records from 122,002 total transactions
- Built aggregation table: one row per product-region combination
- Filtrado de 28,377 registros de Vanish del total de transacciones
- Tabla de agregación: un registro por combinación producto-región

### <img src="https://img.icons8.com/?size=25&id=v0qkjNOz5TXt&format=png&color=000000" align="center"/> Feature Engineering / Ingeniería de Características

| Dimension | Features |
|---|---|
| Economic value | `sales_total`, `sales_mean`, `price_mean` |
| Volume / turnover | `units_total`, `units_mean`, `weekly_avg_units` |
| Performance | `var_pct_mean`, `above_avg_ratio`, `high_value_ratio` |

### <img src="https://img.icons8.com/?size=25&id=eYYTdLLHOr9O&format=png&color=000000" align="center"/> Standardization / Estandarización
- Applied `StandardScaler`. Essential for K-Means (distance-based)
- Aplicado `StandardScaler`. Esencial para K-Means (basado en distancias)

### <img src="https://img.icons8.com/?size=25&id=m9l0TYn8mjwN&format=png&color=000000" align="center"/> Optimal K Selection / Selección del K óptimo

Used 4 validation metrics simultaneously to select k=4:

| Metric | Purpose | Result |
|---|---|---|
| **Elbow Method (Inertia)** | Minimize within-cluster distance | Elbow at k=4 |
| **Silhouette Score** | Cluster cohesion vs separation | Best at k=4 |
| **Davies-Bouldin Index** | Inter-cluster distance | Minimum at k=4 |
| **Calinski-Harabasz** | Cluster density & separation | Peak at k=4 |

### <img src="https://img.icons8.com/?size=25&id=iXyB8gYxLEaa&format=png&color=000000" align="center"/> Model / Modelo
```python
KMeans(
    n_clusters = 4,
    init       = 'k-means++',  # intelligent initialization
    n_init     = 50,           # 50 random starts → avoids local minima
    max_iter   = 500
)
```

### <img src="https://img.icons8.com/?size=25&id=433QkkKdmU3P&format=png&color=000000" align="center"/> Visualization / Visualización
- PCA 2D scatter → clusters in reduced dimensionality space
- Heatmap of cluster profiles
- Boxplots by cluster
- Market share analysis: Vanish vs total market

---

## <img src="https://img.icons8.com/?size=40&id=80351&format=png&color=000000" align="center"/> Key Findings / Hallazgos Principales

### 4 Identified Segments / 4 Segmentos Identificados

| Cluster | Name / Nombre | Profile / Perfil |
|---|---|---|
| 0 | **Alto Rendimiento** | Highest sales, only cluster with positive var_pct → strategic priority |
| 1 | **Presencia Marginal** | Minimum sales, few active weeks → candidates for repositioning |
| 2 | **Premium Alto Valor** | Highest price, 99% high-value weeks → premium positioning |
| 3 | **Mercado Masivo** | Low price, highest volume & turnover → volume driver |

### Strategic Insights / Recomendaciones Estratégicas

**Strengths / Fortalezas:**
- Cluster 0 (Alto Rendimiento) drives disproportionate revenue
- Cluster 2 (Premium) demonstrates successful high-price positioning
- Cluster 3 (Masivo) ensures broad market presence through volume

**Opportunities / Oportunidades:**
- Cluster 1 (Marginal): investigate low-performing product-region combinations → reposition or discontinue
- Cross-selling from Cluster 3 to Cluster 2 in high-potential regions
- Replicate Cluster 0 success patterns in underperforming areas

---

## <img src="https://img.icons8.com/?size=40&id=PhymLYNNjf3I&format=png&color=000000" align="center"/> Repository Structure / Estructura del Repositorio

    kmeans-vanish-segmentation/
    ├── notebook/
    │   └── kmeans_vanish_segmentation.ipynb
    ├── data/
    │   └── clustering_resultados_vanish.csv    # Cluster assignments
    ├── README.md
    └── requirements.txt                        # Python libraries

---

*Project developed as part of the Data Scientist Certificate · 
Proyecto desarrollado como parte del certificado Científico de Datos — EBAC (2026)* <img src="https://img.icons8.com/?size=35&id=FgMs84V9yrMV&format=png&color=000000" align="center"/>
