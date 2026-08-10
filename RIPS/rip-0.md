---
rip: 0
title: Propósito, Estándares y Directrices de Evaluación de Inversiones de las RIP
status: Borrador (Draft)
type: Estándar (Standards Track)
category: Inversión (Investment)
created: 2026-09-08
---

## ¿Qué es una RIP?

RIP corresponde a *Ruby Investment Proposal* (Propuesta de Inversión de Ruby). Una RIP es un documento formal de diseño y análisis que proporciona información a la comunidad de RUBY, o describe una nueva tesis de inversión, estrategia o asignación de cartera para el ecosistema. La RIP debe proporcionar una especificación técnica y cuantitativa rigurosa de la hipótesis financiera, los modelos de valoración, el análisis histórico y los parámetros de riesgo. El autor de la RIP es responsable de generar consenso dentro de la comunidad, incorporar revisiones por pares y defender la tesis antes de la votación comunitaria.


## Justificación de las RIP

Las RIPs están concebidas como los mecanismos principales para proponer la asignación de capital, recopilar aportes cuantitativos de la comunidad y documentar las decisiones analíticas que rigen el respaldo en activos del mundo real (RWA) de RUBY. Debido a que las RIPs se mantienen como archivos de texto, *notebooks* de Jupyter y reportes en un repositorio versionado, su historial de revisiones sirve como el registro histórico transparente y auditable de las estrategias del fondo.

Para los tenedores y analistas de RUBY, las RIPs proporcionan una forma estandarizada de rastrear el rendimiento, las supuestas hipótesis y la validación de *backtesting* de cada activo en la cartera.

## Especificación de Metodologías de Valoración

Toda RIP cuantitativa que proponga la adquisición de un activo o una estrategia de cartera DEBE incorporar al menos tres metodologías de valoración independientes dentro de su documentación adjunta o *notebook* de Jupyter (`.ipynb`):

1. **Modelo de Flujo de Caja Descontado (DCF):** Proyecta los flujos de caja libre (FCF) futuros descontados a valor presente utilizando el costo promedio ponderado del capital (WACC). Los autores deben definir explícitamente las tasas de crecimiento terminal, las proyecciones de EBIT y las hipótesis fiscales.
2. **Filtrado Cuantitativo por Múltiplos:** Evalúa el activo en relación con sus promedios históricos y pares del sector utilizando múltiplos clave de valoración:
   - **P/E (Precio/Beneficio):** Evalúa la valoración general respecto a las ganancias.
   - **P/FCF (Precio/Flujo de Caja Libre):** Evalúa la generación de efectivo en relación con la capitalización de mercado.
   - **P/OCF (Precio/Flujo de Caja Operativo):** Mide el efectivo proveniente de las operaciones principales excluyendo las distorsiones de gastos de capital.
3. **Valoración Basada en Activos o Relativa:** Métricas de valoración de apoyo adaptadas a la industria específica (por ejemplo, EV/EBITDA, Precio/Valor en Libros) para verificar de forma cruzada el valor intrínseco frente a la cotización de mercado.

## Requisitos de Análisis Estadístico e Histórico

Las RIPs no deben depender únicamente de valoraciones puntuales. Cada propuesta debe incluir análisis estadísticos históricos y parámetros de *backtesting*:

- **Medias Móviles (SMA y EMA):** Análisis de Medias Móviles Simples (por ejemplo, de 50 y 200 días) y Medias Móviles Exponenciales para determinar macro-tendencias y zonas de impulso de entrada y salida.
- **Backtesting bajo Regímenes de Mercado:** Simulación del comportamiento histórico del activo frente a cambios macroeconómicos o de mercado específicos. Por ejemplo, si un activo muestra una alta correlación con el S&P 500, la RIP debe modelar cómo se comportó el activo durante las caídas (*drawdowns*) o repuntes históricos del S&P 500 en horizontes de 30, 90 y 365 dias.
- **Matrices de Volatilidad y Correlación:** Cálculo histórico de la beta en relación con índices de referencia y métricas de duración de las caídas.

## Objetivos, Horizontes Temporales, Métricas de Rendimiento y Gestión de Riesgo Operativo

Toda propuesta de inversión debe definir claramente los siguientes parámetros críticos que serán objeto de revisión exhaustiva por parte de la comunidad y los analistas:

- **Precio Objetivo (Target Price):** Estimación fundamentada del valor esperado del activo basada en los modelos cuantitativos presentados.
- **CAGR Esperado (Compound Annual Growth Rate):** Tasa de crecimiento anual compuesta proyectada para el activo o estrategia durante el horizonte de inversión.
- **Máximo Drawdown Esperado:** Límite máximo de caída histórica o proyectada que la estrategia está dispuesta a tolerar frente a escenarios adversos de mercado.
- **Plazo Temporal:** Un horizonte de ejecución y mantenimiento **no mayor a dos años**, estableciendo la ventana temporal máxima proyectada para que la tesis alcance su valor objetivo.
- **Estrategia de Stop-Loss y Stop-Win:** Límites estrictos de protección de capital y toma de ganancias. Se deben especificar los porcentajes o niveles de precio de salida automática tanto para limitar pérdidas como para asegurar rendimientos positivos.

## Ciclo de Vida de una RIP

**Idea** - Concepto previo al borrador compartido en canales comunitarios o foros.

**Draft (Borrador)** - La primera etapa formalmente rastreada. El autor de la RIP abre un *Pull Request* con la especificación en `.md`, el `.pdf` de soporte y los archivos de análisis en `.ipynb`.

**Review (Revisión)** - Analistas y estrategas de la comunidad revisan por pares las hipótesis del DCF, la lógica del *backtesting*, los objetivos de precio, las métricas de CAGR y *drawdown*, los plazos y los parámetros de riesgo.

**Last Call (Última Llamada)** - Ventana de revisión final de 14 días para la propuesta refinada antes de pasar a una votación de gobernanza vinculante.

**Votación (Snapshot)** - La propuesta se envía al espacio de [Snapshot](https://snapshot.org/#/s:rubyfoundation.eth) bajo la regla *un token, un voto*.

**Aprobada / Ejecutada** - Una vez aprobada, la tesis se integra en el flujo de datos del panel (*dashboard*) y se ejecuta a través de la estructura de tesorería designada.

## ¿Qué contiene una RIP exitosa?

- **Preámbulo:** Metadatos de cabecera (número de RIP, título, autor, estado, fecha de creación).
- **Resumen (Abstract):** Sumario ejecutivo conciso de la tesis de inversión.
- **Modelos de Valoración:** Ejecución detallada del DCF y filtrado por múltiplos multivariable.
- **Datos Estadísticos y de Backtesting:** Indicadores SMA/EMA, pruebas de correlación histórica, CAGR esperado y máximo *drawdown* proyectado.
- **Objetivos y Gestión de Riesgos:** Precio objetivo, plazo temporal (máximo 2 años), reglas de *stop-loss* y *stop-win* sujetas a revisión comunitaria.