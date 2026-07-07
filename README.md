# Clustering de Países por Indicadores Socioeconómicos y de Salud

**Proyecto Final — Aprendizaje No Supervisado**  
Maestría en Inteligencia Artificial — FIUNA  
**Autor:** César Núñez

---

## Descripción

Aplicación de técnicas de clustering no supervisado sobre datos socioeconómicos y de salud de 167 países, con el objetivo de identificar perfiles de desarrollo sin utilizar etiquetas predefinidas. Los resultados se validan externamente contra el Índice de Desarrollo Humano (HDI) 2015 del PNUD.

## Dataset

**Country-Level Socioeconomic & Health Data** — [Kaggle](https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data)  
Recolectado por HELP International (~2014-2016).

| Variable | Descripción | Unidad |
|----------|-------------|--------|
| `child_mort` | Mortalidad infantil (< 5 años) | muertes / 1.000 nacidos vivos |
| `exports` | Exportaciones | % del PIB per cápita |
| `health` | Gasto en salud | % del PIB per cápita |
| `imports` | Importaciones | % del PIB per cápita |
| `income` | Ingreso neto per cápita | USD |
| `inflation` | Inflación anual | % |
| `life_expec` | Esperanza de vida | años |
| `total_fer` | Tasa de fertilidad | hijos por mujer |
| `gdpp` | PIB per cápita | USD |

El archivo `Country-data.csv` está disponible en este repositorio.

## Algoritmos implementados

| Algoritmo | Rol | Parámetros |
|-----------|-----|------------|
| K-Means | Baseline | k=3, n_init=20 |
| **Spectral Clustering** | Principal | k=3, affinity='rbf' |
| **GMM** | Principal | covariance_type='diag', n_components=5 (BIC) |

## Resultados

| Algoritmo | Silhouette | Davies-Bouldin | ARI (HDI 2015) | NMI |
|-----------|-----------|----------------|----------------|-----|
| K-Means (baseline) | 0.2717 | 1.2844 | — | — |
| Spectral Clustering | 0.2718 | 1.2378 | **0.4525** | **0.5586** |
| GMM | 0.1846 | 1.5426 | 0.3854 | 0.5398 |

## Estructura del repositorio

```
country-data/
├── Country-data.csv          # Dataset
├── Country_Clustering.ipynb  # Notebook principal
└── README.md
```

## Cómo ejecutar

El notebook se ejecuta completamente en Google Colab sin configuración adicional.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/CANM17/country-data/blob/main/Country_Clustering.ipynb)

1. Hacer clic en el badge **Open in Colab**
2. Ejecutar **Runtime → Run All**

El dataset se descarga automáticamente desde GitHub. No se requieren credenciales ni configuración adicional.

## Dependencias

Todas disponibles por defecto en Google Colab:

```
pandas, numpy, matplotlib, seaborn
scikit-learn, scipy
```

## Referencias

- HELP International (2020). *Country-Level Socioeconomic & Health Data*. Kaggle.
- UNDP (2015). *Human Development Report 2015*. United Nations Development Programme.
- Roser, M. et al. (2023). *Human Development Index*. Our World in Data.
- Von Luxburg, U. (2007). A tutorial on spectral clustering. *Statistics and Computing*, 17(4).
- Pedregosa, F. et al. (2011). Scikit-learn: Machine Learning in Python. *JMLR*, 12.
