# Data Science & Business Analytics: Case Studies

Este repositorio contiene una serie de proyectos prácticos que integran análisis de retail, web scraping avanzado, modelos predictivos de fuga, estimación de valor de vida del cliente (CLTV) e inferencia causal.

## 📋 Contenido del Proyecto

1.  [Análisis de Retail y Rentabilidad (GMROI)](#1-análisis-de-retail)
2.  [Web Scraping Inmobiliario con Playwright](#2-web-scraping-inmobiliario)
3.  [Predicción de Churn y Análisis de Lift](#3-predicción-de-churn)
4.  [Modelado de CLTV (Gamma-Gamma vs Regresión)](#4-modelado-de-cltv)
5.  [Inferencia Causal y Uplift Modeling](#5-inferencia-causal)

---

## 1. Análisis de Retail

**Objetivo:** Integrar datos de ventas, inventario y maestros de productos para calcular la eficiencia del inventario.

* **Métricas Clave:**
    * **GMROI:** $GMROI = \frac{\text{Utilidad Bruta}}{\text{Inventario Promedio a Costo}}$
    * **Markdown %:** $\text{Markdown \%} = \left(1 - \frac{\text{Ingreso Real}}{\text{Ingreso Potencial}}\right) \times 100$

### Top 5 Categorías más Rentables
| Categoría | GMROI | Markdown % |
| :--- | :--- | :--- |
| Hogar | 94.05 | 6.98% |
| Relojería | 86.07 | 4.75% |
| Carnes | 84.14 | 5.39% |
| Informática | 81.55 | 6.69% |
| Muebles | 81.40 | 3.76% |

---

## 2. Web Scraping Inmobiliario

**Objetivo:** Extracción automatizada y asíncrona de datos de Portal Inmobiliario para la comuna de Huechuraba utilizando **Playwright**.

* **Proceso:** Navegación por paginación, scroll dinámico y filtrado de precios en UF/m².
* **Resultados de la Extracción:**

| Métrica | Casas | Deptos |
| :--- | :--- | :--- |
| Propiedades filtradas | 670 | 489 |
| Mediana precio (UF) | 8,570 | 5,750 |
| Precio por m² (UF/m²) | 62.43 | 66.06 |

---

## 3. Predicción de Churn

**Objetivo:** Clasificación de clientes en riesgo de fuga mediante un modelo de **Random Forest** y validación mediante análisis de deciles.

* **Performance:** El modelo alcanzó una precisión del 83% para la clase positiva (fuga).
* **Curva de Ganancia:** El análisis de deciles muestra que el **Top 20%** de los clientes con mayor riesgo concentran el **76.7%** de las fugas reales.



---

## 4. Modelado de CLTV

**Objetivo:** Comparar la robustez de una Regresión Lineal tradicional frente al modelo probabilístico **Gamma-Gamma** para predecir el valor monetario futuro.

* **Hallazgo:** El modelo Gamma-Gamma aplica un efecto de *shrinkage* (encogimiento) en clientes con gastos extremos (*outliers*), proporcionando estimaciones más conservadoras y realistas que la regresión lineal.
* **Parámetros Gamma-Gamma optimizados:** $p=0.9749, q=6.4411, v=339.2870$.

---

## 5. Inferencia Causal

**Objetivo:** Estimar el Efecto del Tratamiento (CATE) de una campaña publicitaria sobre el comportamiento del cliente.

* **Metodología:** Comparación entre **S-Learner** (Single Learner) y **T-Learner** (Two Learners) usando Random Forest Regressor.
* **Conclusión:** Se detectó una correlación de **-0.3815** entre el ingreso y el CATE, indicando que la publicidad tiene un mayor impacto (*uplift*) en clientes con niveles de ingreso más bajos.



---

## 🛠️ Requisitos

```bash
pip install pandas numpy matplotlib seaborn scikit-learn playwright scipy nest_asyncio
playwright install chromium
