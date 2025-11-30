# 🏦 Simulación y Optimización de Servicio - Banco de Colombia

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Status](https://img.shields.io/badge/Status-Completado-green)
![Type](https://img.shields.io/badge/Simulaci%C3%B3n-Eventos%20Discretos-orange)

Este repositorio contiene el código fuente y el análisis de resultados de una simulación de colas (modelo M/M/1) diseñada para optimizar la asignación de cajeros en el **Banco de Colombia**.

## 📋 Descripción del Problema

El Banco de Colombia no cuenta con cajeros electrónicos, por lo que toda la operación (pagos y retiros) recae sobre tres cajas físicas. La gerencia necesita determinar la configuración óptima para prestar el mejor servicio sin demoras excesivas.

**La pregunta clave:**
¿Cómo se deben distribuir las 3 cajas disponibles?
* ¿2 exclusivas para Retiros y 1 para Pagos?
* ¿1 exclusiva para Retiros y 2 para Pagos?

## ⚙️ Metodología y Parámetros

Para resolver esto, se desarrolló un simulador de **Eventos Discretos** en Python con las siguientes características:

* **Modelo de Colas:** M/M/1 (Llegadas de Poisson, tiempos de servicio exponenciales, servidores independientes).
* **Duración:** Se simularon días operativos de 8 horas (480 minutos).
* **Robustez:** Se ejecutaron **10 réplicas** del modelo para obtener promedios estadísticos confiables.

### Datos de Entrada y Probabilidades

El comportamiento de los usuarios se modeló utilizando las siguientes tablas de parámetros y probabilidades:

#### Tabla 1: Tiempos de Servicio y Llegada
| Tipo de Acción | Tipo de Usuario | Exp. Uso Servicio (Media) | Exp. Llegada (Media) |
| :--- | :--- | :---: | :---: |
| **Retiro** | Rápido | 1 min | 1 min |
| | Normal | 2 min | 2 min |
| | Lento | 3 min | 3 min |
| | Muy Lento | 4 min | 3 min |
| **Consignación o Pago** | Rápido | 3 min | 1 min |
| | Normal | 3 min | 2 min |
| | Lento | 5 min | 3 min |
| | Muy Lento | 7 min | 4 min |

#### Tabla 2: Probabilidades por Tipo de Usuario
Las probabilidades asignadas a cada perfil de usuario dentro de la simulación son:

| Tipo de Acción | Tipo de Usuario | Probabilidad |
| :--- | :--- | :---: |
| **Retiro** | Rápido | 0,23 |
| | Normal | 0,40 |
| | Lento | 0,17 |
| | Muy lento | 0,20 |
| **Consignación o pago** | Rápido | 0,10 |
| | Normal | 0,20 |
| | Lento | 0,30 |
| | Muy lento | 0,40 |
