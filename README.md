# EJD-UMA-002 v1.0 — Tree Edit Distance y Proyeccion MDS sobre Arboles Federados
## Ejercicio Doctoral — Programa de Doctorado en Tecnologias Informaticas
### Universidad de Malaga

| Campo | Detalle |
|-------|---------|
| **Codigo** | EJD-UMA-002 |
| **Version** | 1.0 |
| **Referencia** | Ejercicio propuesto por Prof. E. Lopez Rubio — continuacion del EJD-UMA-001 |
| **Autor** | Edgar O. Herrera Logroño · M.Sc. Inteligencia Artificial — VIU Espana |
| **Directores** | Prof. Ezequiel Lopez Rubio · Prof. Juan Miguel Ortiz de Lazcano — UMA |
| **Fecha** | Marzo 2026 |

---

## Origen del ejercicio

Al revisar el ejercicio EJD-UMA-001 sobre Random Forest Federado, el Prof. Lopez Rubio propuso calcular una medida de distancia estructural entre los arboles de decision aprendidos durante el ciclo federado. La tecnica indicada es la Tree Edit Distance (TED), que cuantifica el numero minimo de operaciones elementales necesarias para transformar un arbol en otro. Con la matriz de distancias obtenida, se aplica Multidimensional Scaling (MDS) para proyectar los arboles en un plano bidimensional.

El objetivo es verificar si la distribucion espacial de los arboles revela algun patron aprovechable para mejorar el mecanismo de agregacion del sistema federado.

---

## Estructura del notebook

| Seccion | Contenido |
|---------|-----------|
| Parametros configurables | N de arboles, semilla, limites de conversion — ajustables antes de ejecutar |
| Seccion 1 | Preparacion del entorno |
| Seccion 2 | Carga de datos NSL-KDD |
| Seccion 3 | Entrenamiento y seleccion estratificada de arboles por quintil de F1-Score |
| Seccion 4 | Conversion a formato zss y calculo de la matriz TED |
| Seccion 5 | Proyeccion MDS y Figura 1 |
| Seccion 6 | Analisis de patrones — cohesion intra/inter nodo y correlacion F1-Score |
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

La muestra de 20 arboles por nodo se selecciona por estratificacion de quintil de F1-Score individual, de forma que todos los niveles de rendimiento esten representados. La conversion de arboles scikit-learn a formato zss aplica un limite de profundidad 6 y 200 nodos por arbol — declarado como limitacion metodologica que reduce la precision en arboles muy profundos.

El Stress MDS normalizado de 0.2843 supera el umbral aceptable de 0.20, lo que indica que el plano bidimensional no captura con suficiente fidelidad la variabilidad estructural de los arboles. En consecuencia, los patrones visuales son indicativos, no definitivos. Una extension natural seria aplicar tecnicas de reduccion no lineal como t-SNE o UMAP.

---

## Como ejecutarlo

El notebook esta disenado para correr en Google Colab sin configuracion adicional.

1. Abrir [Google Colab](https://colab.research.google.com)
2. File > Open notebook > GitHub > pegar la URL de este repositorio
3. Ajustar los parametros configurables si se desea variar el experimento
4. Runtime > Run all

Al finalizar, el notebook imprime las conclusiones calculadas automaticamente y el resumen de estado por modulo.

---

## Relacion con otros repositorios del proceso doctoral

| Codigo | Repositorio | Contenido |
|--------|-------------|-----------|
| EJD-UMA-001 | [RF_Federado_Ejercicio_Doctoral_UMA](https://github.com/eoherrera/RF_Federado_Ejercicio_Doctoral_UMA) | Random Forest Federado — comparativa de configuraciones |
| EJD-UMA-002 | Este repositorio | Tree Edit Distance y proyeccion MDS |

---

## Stack tecnico

- Python 3.12
- scikit-learn 1.6
- zss 1.2.0 (Zhang-Shasha algorithm)
- sklearn.manifold.MDS
- NumPy / Pandas / Matplotlib / Seaborn / SciPy

---

## Contexto

Este notebook forma parte del proceso de evaluacion para el ingreso al Programa de Doctorado en Tecnologias Informaticas de la Universidad de Malaga, bajo la direccion propuesta del Prof. Ezequiel Lopez Rubio y el Prof. Juan Miguel Ortiz de Lazcano.

---

**Edgar O. Herrera Logroño · M.Sc. Inteligencia Artificial — VIU Espana**
**Analista Senior SGSI — IESS Ecuador · Candidato CRISC — ISACA**
