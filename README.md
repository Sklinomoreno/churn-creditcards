# Predicción de Churn en Tarjetas de Crédito

Este proyecto tiene como objetivo predecir la deserción de clientes (**churn**) en tarjetas de crédito, utilizando el conjunto de datos **“Credit Card Customers”** disponible en **Kaggle**. El dataset incluye información de 10,127 clientes de un banco, con variables demográficas, socioeconómicas y de comportamiento financiero. Esto lo convierte en una excelente base para analizar el churn y mejorar las estrategias de retención.

## 📊 Dataset

El conjunto de datos contiene las siguientes variables:

| **Variable**                       | **Descripción**                                                                |
|-------------------------------------|--------------------------------------------------------------------------------|
| `CLIENTNUM`                         | Identificador único del cliente                                               |
| `Attrition_Flag`                    | Evento interno: 1 si la cuenta está cerrada, 0 si no                           |
| `Customer_Age`                      | Edad del cliente en años                                                      |
| `Gender`                            | Género: M=Masculino, F=Femenino                                               |
| `Dependent_count`                   | Número de dependientes                                                        |
| `Education_Level`                   | Nivel educativo del titular de la cuenta                                      |
| `Marital_Status`                    | Estado civil: Casado, Soltero, Divorciado, Desconocido                         |
| `Income_Category`                   | Categoría de ingresos anuales del titular                                     |
| `Card_Category`                     | Tipo de tarjeta: Blue, Silver, Gold, Platinum                                 |
| `Months_on_book`                    | Período de relación con el banco                                               |
| `Total_Relationship_Count`          | Número total de productos que tiene el cliente                                |
| `Months_Inactive_12_mon`            | Número de meses inactivos en los últimos 12 meses                              |
| `Contacts_Count_12_mon`             | Número de contactos en los últimos 12 meses                                   |
| `Credit_Limit`                      | Límite de crédito de la tarjeta                                               |
| `Total_Revolving_Bal`               | Saldo rotativo total en la tarjeta de crédito                                 |
| `Avg_Open_To_Buy`                   | Línea de crédito disponible (promedio de los últimos 12 meses)                 |
| `Total_Amt_Chng_Q4_Q1`              | Cambio en el monto de transacciones (Q4 sobre Q1)                             |
| `Total_Trans_Amt`                   | Monto total de transacciones (últimos 12 meses)                               |
| `Total_Trans_Ct`                    | Cantidad total de transacciones (últimos 12 meses)                            |
| `Total_Ct_Chng_Q4_Q1`               | Cambio en la cantidad de transacciones (Q4 sobre Q1)                           |
| `Avg_Utilization_Ratio`             | Tasa promedio de utilización de la tarjeta                                    |

Puedes acceder al dataset completo a través del siguiente [enlace a Kaggle](https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers).

## 🧑‍🔬 Metodología

1. **Preparación de los datos:** Se utilizó el conjunto de datos **“Credit Card Customers”** de Kaggle. Se realizaron tareas de limpieza y preprocesamiento, como la codificación de variables categóricas y el tratamiento de valores nulos.

2. **Técnicas de Balanceo:** Dado que el dataset presenta un desbalance en las clases (churn vs no churn), se implementó la técnica **SMOTETomek** para balancear las clases antes de entrenar los modelos.

3. **Modelos Evaluados:** Se entrenaron y evaluaron varios modelos de machine learning, incluyendo **Random Forest**, **XGBoost**, **LightGBM**, **CatBoost**, entre otros, para identificar el modelo más efectivo en la predicción del churn.

4. **Optimización de Hiperparámetros:** Para optimizar los hiperparámetros de los modelos, se utilizó **GridSearchCV** con validación cruzada.


## 📈 Resultados de Modelos

Los siguientes modelos fueron evaluados para predecir la deserción de clientes, utilizando técnicas de resampling con SMOTETomek para equilibrar las clases y la optimización de umbrales basada en el F1-score:

| **Modelo**                  | **Umbral Óptimo** | **Precision** | **Recall** | **F1-score** | **AUC** |
|-----------------------------|-------------------|---------------|------------|--------------|---------|
| **Random Forest**           | 0.3               | 0.893         | 0.898      | 0.894        | 0.933   |
| **XGBoost**                 | 0.4               | 0.904         | 0.909      | 0.905        | 0.939   |
| **LightGBM**                | 0.4               | 0.908         | 0.912      | 0.909        | 0.942   |
| **Logistic Regression**     | 0.3               | 0.868         | 0.859      | 0.863        | 0.853   |
| **ElasticNet**              | 0.3               | 0.867         | 0.858      | 0.862        | 0.853   |
| **CatBoost**                | 0.3               | 0.901         | 0.907      | 0.899        | 0.940   |
| **ANN (MLP)**               | 0.3               | 0.879         | 0.879      | 0.879        | 0.914   |
| **Naive Bayes**             | 0.3               | 0.840         | 0.723      | 0.757        | 0.813   |

## Análisis de Resultados

- **CatBoost** mostró el mejor desempeño con un AUC de 0.940 y un F1-score de 0.899, lo que lo hace el modelo más adecuado para predecir clientes en riesgo de churn.
- **XGBoost** y **LightGBM** también tuvieron buenos resultados, con AUCs cercanos a 0.939 y 0.942, respectivamente, pero no lograron superar a CatBoost en precisión y recall.
- **Logistic Regression** y **ElasticNet** tuvieron un rendimiento moderado, con AUCs de 0.853, lo que los hizo menos efectivos en el contexto de clases desbalanceadas.
- **Naive Bayes** fue el modelo menos efectivo, con un AUC de 0.813 y un F1-score de 0.757.

## 🧑‍💼 Conclusiones

- **CatBoost** es el modelo más adecuado para la predicción del churn, con un excelente balance entre precisión y recall, especialmente en la identificación de clientes que cancelan el servicio.
- Se recomienda utilizar **CatBoost** en la industria financiera para diseñar estrategias de retención personalizadas.
- Los modelos como **Naive Bayes** y **Regresión Logística** mostraron ser menos efectivos debido a la naturaleza desbalanceada de las clases.

## 🔗 Link al Dashboard

Puedes ver el dashboard interactivo con los resultados del análisis en el siguiente [enlace a Power BI](https://app.powerbi.com/view?r=eyJrIjoiYzAxMTgxZTgtZThiOS00MGVkLWJiZDItOTliYjcwZmM2NWRlIiwidCI6IjBlMGNiMDYwLTA5YWQtNDlmNS1hMDA1LTY4YjliNDlhYTFmNiIsImMiOjR9).

## 📫 Contacto

👤 **Smith Eusebio Lino Moreno**  
📧 [smlinomoreno@gmail.com](mailto:smlinomoreno@gmail.com)  
🔗 [LinkedIn](https://www.linkedin.com/in/slino-moreno)
