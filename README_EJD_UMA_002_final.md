# EJD-UMA-002 v1.0 - Tree Edit Distance y Proyeccion MDS sobre Arboles Federados

Ejercicio doctoral · Programa de Doctorado en Tecnologias Informaticas · Universidad de Malaga

| Campo | Detalle |
|-------|---------|
| Codigo | EJD-UMA-002 |
| Version | 1.0 |
| Referencia | Ejercicio propuesto por el Prof. E. Lopez Rubio como continuacion de EJD-UMA-001 |
| Autor | Ing. Edgar O. Herrera Logrono, M.Sc. en Inteligencia Artificial, VIU Espana |
| Directores propuestos | Prof. Ezequiel Lopez Rubio · Prof. Juan Miguel Ortiz de Lazcano, UMA |
| Dataset | NSL-KDD (Network Security Lab, Dalhousie University) |
| Fecha | Marzo 2026 |

---

## Objetivo

Al revisar el ejercicio EJD-UMA-001 sobre Random Forest Federado, el Prof. Lopez Rubio propuso calcular una medida de distancia estructural entre los arboles de decision aprendidos durante el ciclo federado. La tecnica indicada es la Tree Edit Distance (TED), que cuantifica el numero minimo de operaciones elementales necesarias para transformar un arbol en otro. Con la matriz de distancias obtenida, se aplica Multidimensional Scaling (MDS) para proyectar los arboles en un plano bidimensional.

El objetivo es verificar si la distribucion espacial de los arboles revela algun patron aprovechable para mejorar el mecanismo de agregacion del sistema federado.

---

## Estructura del notebook

| Seccion | Contenido |
|---------|-----------|
| Parametros configurables | N de arboles, semilla, limites de conversion, ajustables antes de ejecutar |
| Seccion 1 | Preparacion del entorno |
| Seccion 2 | Carga de datos NSL-KDD |
| Seccion 3 | Entrenamiento y seleccion estratificada de arboles por quintil de F1-Score |
| Seccion 4 | Conversion a formato zss y calculo de la matriz TED |
| Seccion 5 | Proyeccion MDS y Figura 1 |
| Seccion 6 | Analisis de patrones: cohesion intra/inter nodo y correlacion F1-Score |
| Conclusiones | Generadas automaticamente segun los resultados reales de cada ejecucion |
| Resumen final | Estado de ejecucion por modulo con porcentaje de completitud |

---

## Resultados obtenidos

| Metrica | Valor |
|---------|-------|
| Arboles analizados | 60 (20 por nodo) |
| Pares TED calculados | 1.770 |
| Stress MDS normalizado | 0.2843 |
| Distancia TED media global | 620.3 |
| Nodo con mayor cohesion | Salud (ratio inter/intra: 0.98) |
| Estado de ejecucion | 100% |

---

## Precision metodologica

La muestra de 20 arboles por nodo se selecciona por estratificacion de quintil de F1-Score individual, de forma que todos los niveles de rendimiento esten representados. La conversion de arboles scikit-learn a formato zss aplica un limite de profundidad 6 y 200 nodos por arbol, declarado como limitacion metodologica que reduce la precision en arboles muy profundos.

El Stress MDS normalizado de 0.2843 supera el umbral aceptable de 0.20, lo que indica que el plano bidimensional no captura con suficiente fidelidad la variabilidad estructural de los arboles. En consecuencia, los patrones visuales son indicativos, no definitivos. Una extension natural seria aplicar tecnicas de reduccion no lineal como t-SNE o UMAP.

---

## Como ejecutarlo

El notebook esta disenado para correr en Google Colab sin configuracion adicional.

1. Abrir Google Colab (colab.research.google.com)
2. Ir a File, Open notebook, GitHub y pegar la URL de este repositorio
3. Ajustar los parametros configurables si se desea variar el experimento
4. Ejecutar con Runtime, Run all

Al finalizar, el notebook imprime las conclusiones calculadas automaticamente y el resumen de estado por modulo.

---

## Stack tecnico

Python 3.12, scikit-learn 1.6, zss 1.2.0 (algoritmo Zhang-Shasha), sklearn.manifold.MDS, NumPy, Pandas, Matplotlib, Seaborn, SciPy.

---

## Control de cambios

| Version | Fecha | Descripcion |
|---------|-------|-------------|
| 1.0 | Mar 2026 | Version inicial. Calculo de matriz TED sobre 60 arboles federados, proyeccion MDS, analisis de cohesion intra e inter nodo. |

---

## Repositorios del proceso doctoral

| Codigo | Repositorio | Contenido |
|--------|-------------|-----------|
| EJD-UMA-001 | [RF_Federado_Ejercicio_Doctoral_UMA](https://github.com/eoherrera/RF_Federado_Ejercicio_Doctoral_UMA) | Random Forest Federado, comparativa de configuraciones |
| EJD-UMA-001 v8.0 | [RF_Federado_Ejercicio_Doctoral_UMA_v8](https://github.com/eoherrera/RF_Federado_Ejercicio_Doctoral_UMA_v8) | Fed-TRUST: Coeficiente de Veracidad V_i y agregacion ponderada |
| EJD-UMA-002 | Este repositorio | Tree Edit Distance y proyeccion MDS |
| EJD-UMA-003 | [EJD_UMA_003_NaiveBayes_Federado](https://github.com/eoherrera/EJD_UMA_003_NaiveBayes_Federado) | Clasificador Naive Bayes Federado con mezcla de distribuciones |

---

Ing. Edgar O. Herrera Logrono, M.Sc. en Inteligencia Artificial, VIU Espana
Analista Senior de Seguridad de la Informacion, IESS Ecuador
Candidato CRISC, ISACA
Candidato doctoral, Programa de Doctorado en Tecnologias Informaticas, Universidad de Malaga
