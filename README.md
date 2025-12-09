# Taller: Algoritmo de Shor

## Descripción general

Este repositorio contiene un cuaderno Jupyter/Colab que introduce, explica e implementa el algoritmo de Shor, uno de los métodos cuánticos más importantes para la factorización de enteros. El notebook desarrolla tanto los fundamentos matemáticos clásicos como la implementación mediante circuitos cuánticos utilizando Qiskit.

El objetivo del taller es proporcionar una ruta de aprendizaje completa que combina teoría, visualizaciones y experimentación directa.

---

## Contenido del cuaderno

### 1. Aritmética modular y congruencias

Se presenta una revisión de los conceptos básicos necesarios para comprender el algoritmo:

- Operación módulo  
- Congruencias enteras  
- Propiedades de la exponenciación modular  
- Visualización de la función  

$$
f_{a,N}(x) = a^x \bmod N
$$

El cuaderno incluye gráficos que muestran cómo se comporta la secuencia modular para distintos valores de \( a \) y \( N \), lo que prepara el terreno para comprender el período.

---

### 2. Exponenciación modular y búsqueda del período

Antes de la parte cuántica, se explica cómo obtener el período \( r \) de manera clásica mediante:

- Métodos directos  
- Exponenciación modular recursiva  
- Identificación del período mediante inspección y cálculo  

El período \( r \) es fundamental porque, si \( a \) es coprimo con \( N \), se cumple:

$$
a^r \equiv 1 \pmod{N}
$$

y este valor permite recuperar los factores de \( N \).

---

### 3. Obtención de factores a partir del período

Una vez conocido el período \( r \), se utilizan las siguientes relaciones:

$$
\gcd(a^{r/2} - 1, N)
$$

$$
\gcd(a^{r/2} + 1, N)
$$

El cuaderno implementa:

- Cálculo del máximo común divisor (método de Euclides)  
- Verificación de condiciones válidas (como que \( r \) sea par)  
- Ejemplos completos para números como 371 y 247  

---

## Parte cuántica del taller

### 4. Algoritmo cuántico de Shor

La segunda parte del cuaderno implementa la versión cuántica del algoritmo, basada en encontrar el período mediante estimación de fase cuántica (QPE).

El cuaderno desarrolla:

- El circuito de estimación de fase  
- El registro de conteo de \( n \) qubits  
- El registro auxiliar para la operación modular  
- Construcción de operadores controlados que implementan  

$$
a^k \bmod N
$$

- Aplicación de la Transformada de Fourier Cuántica inversa (QFT)

Todo el circuito está implementado manualmente sin usar atajos predefinidos, con el fin de comprender cada componente.

---

### 5. Ejecución y análisis de resultados

El cuaderno:

- Ejecuta el circuito en el simulador Aer de Qiskit  
- Extrae la distribución de mediciones  
- Convierte las mediciones binarias en fases  
- Utiliza fracciones continuas para aproximar el período \( r \)  
- Evalúa posibles valores de \( r \)  
- Recupera factores no triviales de \( N \)

Se generan tanto tablas como histogramas para facilitar la interpretación de los resultados obtenidos.

---

## Requisitos

El notebook es compatible con Google Colab y entornos locales con Jupyter Notebook. Dependencias principales:

