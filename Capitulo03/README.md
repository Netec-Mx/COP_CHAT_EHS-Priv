# Análisis de Indicadores de Accidentabilidad y Visualización de Datos EHS con Microsoft 365 Copilot en Excel

## Metadatos del Laboratorio

| Atributo | Detalle |
|---|---|
| **Duración estimada** | 90 minutos |
| **Complejidad** | Media |
| **Nivel Bloom** | Aplicar (Apply) |
| **Módulo** | Módulo 3 — Análisis de Datos de Accidentabilidad |
| **Laboratorio ID** | 03-00-01 |
| **Prerrequisitos** | Prácticas 1 y 2 completadas (o experiencia equivalente con Copilot) |

---

## Descripción General

En este laboratorio los participantes utilizarán **Microsoft 365 Copilot integrado en Excel** para procesar un dataset de 12 meses de accidentabilidad de una planta industrial ficticia. A través de cuatro bloques de trabajo progresivos, aplicarán metodologías de Análisis Causa Raíz (ACR) —específicamente los **5 Por Qué** y el **Diagrama de Ishikawa**— con asistencia de IA, identificarán tendencias en indicadores clave de desempeño EHS (TRIR, LTIR, Índice de Frecuencia e Índice de Gravedad), y seleccionarán las representaciones visuales más adecuadas para comunicar los resultados a diferentes audiencias. El laboratorio refleja un flujo de trabajo real de análisis de seguridad industrial, integrando el juicio del especialista EHS con la capacidad analítica de Copilot.

---

## Objetivos de Aprendizaje

Al finalizar este laboratorio, el participante será capaz de:

- [ ] Utilizar Copilot en Excel para realizar un análisis exploratorio de datos de accidentabilidad, calcular indicadores EHS clave (TRIR, LTIR, Índice de Frecuencia, Índice de Gravedad) e identificar valores atípicos en el dataset.
- [ ] Aplicar las metodologías de los 5 Por Qué y el Diagrama de Ishikawa con el apoyo de Copilot para identificar causas raíz y factores contribuyentes en los incidentes más significativos del dataset.
- [ ] Interpretar tendencias temporales, patrones por área y por turno, y correlaciones entre variables de seguridad utilizando Copilot como asistente analítico.
- [ ] Seleccionar y generar las representaciones visuales más adecuadas para cada tipo de dato EHS y construir un dashboard básico de indicadores en Excel con orientación de Copilot.

---

## Prerrequisitos

### Conocimientos Requeridos

| Área | Nivel Requerido |
|---|---|
| Microsoft Excel (tablas, fórmulas básicas, gráficas) | Intermedio |
| Uso general de Microsoft 365 Copilot | Básico (Prácticas 1 y 2 completadas) |
| Conceptos de indicadores EHS: TRIR, LTIR, Frecuencia, Gravedad | Familiaridad conceptual |
| Metodologías ACR: 5 Por Qué, Diagrama de Ishikawa | Conocimiento teórico (Lección 3.1) |

### Accesos y Recursos Requeridos

| Recurso | Estado Requerido |
|---|---|
| Licencia Microsoft 365 Copilot activa | ✅ Activa y verificada |
| Copilot visible en la cinta de opciones de Excel | ✅ Habilitado por TI |
| Archivo `Dataset_Accidentabilidad_PlantaFicticia.xlsx` | ✅ Cargado en OneDrive/SharePoint por el instructor |
| Acceso a OneDrive o SharePoint corporativo | ✅ Sesión iniciada |
| Conexión a Internet estable (mínimo 10 Mbps) | ✅ Verificada |

> ⚠️ **ADVERTENCIA CRÍTICA — Almacenamiento en la nube obligatorio:** Copilot en Excel **únicamente** funciona con archivos almacenados en OneDrive o SharePoint Online. Si el archivo está guardado localmente en el disco duro, el botón de Copilot aparecerá deshabilitado (atenuado). Antes de comenzar, verifique que el archivo se encuentre en la nube.

> 🔒 **Privacidad de datos:** Durante toda la práctica utilice **exclusivamente** los datos ficticios del dataset proporcionado. Está estrictamente prohibido ingresar datos reales de empleados, información confidencial de la empresa o datos sensibles de seguridad en los prompts de Copilot.

---

## Entorno del Laboratorio

### Configuración de Hardware

| Componente | Especificación Mínima |
|---|---|
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 (o superior) |
| RAM | 8 GB (16 GB recomendado para múltiples aplicaciones abiertas) |
| Pantalla | Resolución 1920×1080 (se recomienda monitor secundario) |
| Almacenamiento libre | 10 GB mínimo |
| Conexión a Internet | 10 Mbps mínimo, estable |

### Configuración de Software

| Aplicación | Versión / Estado |
|---|---|
| Microsoft Excel | Microsoft 365 Apps for Enterprise (canal actual) |
| Microsoft 365 Copilot | Licencia activa, integrada en Excel |
| Microsoft Edge | Versión estable más reciente (Chromium) |
| OneDrive / SharePoint Online | Sesión activa con cuenta corporativa |

### Configuración Previa al Laboratorio

Siga estos pasos **antes** de iniciar el Bloque 1:

**Paso de configuración A — Verificar ubicación del archivo en la nube:**

1. Abra Microsoft Edge y navegue a su OneDrive corporativo:
   ```
   https://onedrive.live.com  (cuenta personal)
   — o —
   https://<su-tenant>.sharepoint.com  (cuenta corporativa)
   ```
2. Localice la carpeta **`Módulo 3 - Práctica`** creada por el instructor.
3. Confirme que el archivo **`Dataset_Accidentabilidad_PlantaFicticia.xlsx`** está presente.

**Paso de configuración B — Abrir el archivo desde la nube:**

1. Haga clic sobre el archivo en OneDrive/SharePoint para abrirlo directamente en Excel Online, **o** ábralo con "Abrir en la aplicación de escritorio" (recomendado para mejor rendimiento de Copilot).
2. Verifique que en la barra de título aparezca el ícono de nube ☁️ junto al nombre del archivo, confirmando que está sincronizado.

**Paso de configuración C — Verificar Copilot en Excel:**

1. En la cinta de opciones de Excel, busque la pestaña **Inicio** o **Copilot**.
2. Confirme que el botón **Copilot** (ícono de estrella ✨) está visible y habilitado (no atenuado).
3. Haga clic en el botón para abrir el panel de Copilot en el lado derecho de la pantalla.

> 💡 **Tip del instructor:** Si el botón de Copilot aparece atenuado, el archivo no está en la nube o la licencia no está activa. Consulte la sección de Solución de Problemas al final de este laboratorio.

---

## Procedimiento Paso a Paso

El laboratorio se divide en **cuatro bloques** de trabajo. El tiempo estimado por bloque se indica al inicio de cada uno.

---

### BLOQUE 1: Exploración de Datos y Cálculo de Indicadores EHS con Copilot

**⏱️ Tiempo estimado: 20 minutos**

**Objetivo del bloque:** Realizar un análisis exploratorio del dataset de accidentabilidad, comprender su estructura, identificar valores atípicos y calcular los indicadores clave de desempeño EHS utilizando Copilot como asistente analítico.

---

#### Paso 1.1 — Explorar la estructura del dataset con Copilot

**Objetivo:** Obtener una comprensión rápida de la estructura, contenido y calidad de los datos disponibles.

**Instrucciones:**

1. Con el archivo `Dataset_Accidentabilidad_PlantaFicticia.xlsx` abierto y el panel de Copilot visible, asegúrese de que los datos estén formateados como **Tabla de Excel** (seleccione cualquier celda del rango de datos → pestaña **Insertar** → **Tabla**).
2. Haga clic en el panel de Copilot y escriba el siguiente prompt:

   ```text
   Analiza esta tabla de datos de accidentabilidad.
   Proporciona:
   1. Un resumen de la estructura: número de filas, columnas y tipo de dato en cada columna.
   2. Los rangos de fechas cubiertos.
   3. Las áreas de planta y turnos presentes en el dataset.
   4. Cualquier valor faltante, duplicado o atípico que identifiques.
   Presenta el resumen en formato de lista estructurada.
   ```

3. Presione **Enter** y espere la respuesta de Copilot (10–30 segundos).
4. Lea detenidamente el resumen generado. **Anote en papel o en un documento Word** los hallazgos principales: total de incidentes, período cubierto, áreas identificadas, turnos y cualquier anomalía señalada.

**Resultado esperado:** Copilot devolverá un resumen estructurado indicando, por ejemplo: 144 registros de incidentes (12 meses × ~12 registros/mes), columnas como Fecha, Área, Turno, Tipo de Incidente, Días Perdidos, Causa Reportada, Horas Trabajadas, entre otras. También señalará si existen celdas vacías o valores inconsistentes.

**Verificación:** El resumen de Copilot debe mencionar al menos: (a) el número total de registros, (b) las áreas de planta presentes, (c) los tipos de turno, y (d) si se detectaron o no valores atípicos o faltantes.

---

#### Paso 1.2 — Calcular indicadores EHS clave con Copilot

**Objetivo:** Obtener el cálculo de los cuatro indicadores principales de accidentabilidad para el período completo del dataset.

**Instrucciones:**

1. En el panel de Copilot, ingrese el siguiente prompt. Asegúrese de adaptar los nombres de columna según lo que Copilot reportó en el paso anterior (si las columnas tienen nombres diferentes, ajuste el prompt):

   ```text
   Usando los datos de esta tabla, calcula los siguientes indicadores
   EHS para el período completo (12 meses):

   1. TRIR (Total Recordable Incident Rate):
      Fórmula: (Número de incidentes registrables × 200,000) / Horas trabajadas totales

   2. LTIR (Lost Time Injury Rate):
      Fórmula: (Número de incidentes con días perdidos × 200,000) / Horas trabajadas totales

   3. Índice de Frecuencia:
      Fórmula: (Número total de accidentes × 1,000,000) / Horas hombre trabajadas

   4. Índice de Gravedad:
      Fórmula: (Total de días perdidos × 1,000,000) / Horas hombre trabajadas

   Presenta los resultados en una tabla con: Indicador, Valor calculado,
   Interpretación breve (1 oración).
   Luego, agrega las fórmulas de Excel correspondientes que puedo
   insertar en una nueva hoja de cálculo.
   ```

2. Presione **Enter** y espere la respuesta.
3. Revise los valores calculados. Si Copilot proporciona fórmulas de Excel, copie cada fórmula y péguela en la hoja **"Indicadores"** del archivo (créela si no existe: clic derecho en la pestaña de hoja → **Insertar** → **Hoja de cálculo**).
4. Verifique que los resultados de las fórmulas en Excel coincidan con los valores que Copilot calculó directamente.

**Resultado esperado:** Una tabla con los cuatro indicadores calculados (valores numéricos con 2 decimales) y sus interpretaciones. Por ejemplo: TRIR = 4.17 (por encima del promedio de la industria manufacturera de 3.2, según benchmarks de OSHA). Las fórmulas de Excel deben referenciar correctamente las columnas del dataset.

**Verificación:** Los cuatro indicadores deben estar calculados. Las fórmulas de Excel deben producir resultados idénticos a los de Copilot. Si hay discrepancia, solicite a Copilot que explique el cálculo paso a paso.

---

#### Paso 1.3 — Análisis descriptivo por mes

**Objetivo:** Obtener un resumen estadístico mensual que permita identificar meses de mayor incidentalidad.

**Instrucciones:**

1. En el panel de Copilot, ingrese:

   ```text
   Genera un resumen estadístico mensual de los incidentes.
   Para cada mes, muestra:
   - Total de incidentes
   - Total de días perdidos
   - Tipo de incidente más frecuente
   - Área con mayor número de incidentes

   Identifica los 3 meses con mayor número de incidentes y
   los 3 meses con mayor número de días perdidos.
   ¿Hay alguna correlación visible entre ambas métricas?
   ```

2. Revise la respuesta y **tome nota** de los meses identificados como críticos. Estos serán utilizados en el Bloque 3.

**Resultado esperado:** Una tabla mensual con las métricas solicitadas, seguida de un párrafo de análisis que identifique los meses pico y comente si los meses con más incidentes coinciden con los de mayor severidad (días perdidos).

**Verificación:** La tabla debe contener exactamente 12 filas (una por mes). Los meses identificados como críticos deben ser consistentes con los datos del dataset.

---

### BLOQUE 2: Análisis Causa Raíz Asistido por Copilot (ACR)

**⏱️ Tiempo estimado: 25 minutos**

**Objetivo del bloque:** Aplicar las metodologías de los 5 Por Qué y el Diagrama de Ishikawa con el apoyo de Copilot para analizar los incidentes más significativos del dataset, identificando causas raíz y factores contribuyentes.

---

#### Paso 2.1 — Identificar los incidentes prioritarios para el ACR

**Objetivo:** Seleccionar los incidentes más relevantes del dataset para aplicar el análisis causa raíz.

**Instrucciones:**

1. En el panel de Copilot, ingrese:

   ```text
   De los datos de esta tabla, identifica:
   1. El tipo de incidente más frecuente (por número de ocurrencias).
   2. El incidente con mayor número de días perdidos acumulados.
   3. El área de planta con mayor tasa de incidentalidad.

   Para cada uno, proporciona: nombre/descripción, número de ocurrencias
   o días perdidos, y el período en que se concentraron.
   Estos serán los casos de análisis para el análisis causa raíz.
   ```

2. Anote los tres casos identificados. En los pasos siguientes aplicará ACR al **caso 1** (más frecuente) y al **caso 2** (mayor severidad).

**Resultado esperado:** Copilot identificará, por ejemplo: (1) "Resbalones y caídas" como tipo más frecuente con 28 ocurrencias; (2) "Atrapamiento en maquinaria" como el de mayor severidad con 47 días perdidos acumulados; (3) "Área de Producción - Línea B" como la zona de mayor riesgo.

**Verificación:** Los casos identificados deben poder verificarse manualmente filtrando la tabla de Excel (use el Autofiltro de Excel para confirmar los conteos).

---

#### Paso 2.2 — Aplicar los 5 Por Qué al incidente más frecuente

**Objetivo:** Construir una cadena causal completa para el tipo de incidente más frecuente utilizando la metodología de los 5 Por Qué con Copilot.

**Instrucciones:**

1. Basándose en el caso 1 identificado en el paso anterior (adapte la descripción al incidente real del dataset), ingrese el siguiente prompt en Copilot. El ejemplo usa "resbalones y caídas" — **reemplácelo con el incidente real de su dataset**:

   ```text
   Actúa como un especialista en EHS con experiencia en análisis
   causa raíz en plantas de manufactura.

   Incidente analizado: "Resbalones y caídas en el área de
   carga y descarga — 28 ocurrencias en los últimos 12 meses,
   concentradas en el turno nocturno durante los meses de
   octubre a diciembre."

   Aplica la metodología de los 5 Por Qué para identificar
   la causa raíz sistémica. Presenta el análisis con este formato:

   PROBLEMA: [descripción]
   Por Qué 1: [pregunta] → [causa identificada]
   Por Qué 2: [pregunta] → [causa identificada]
   Por Qué 3: [pregunta] → [causa identificada]
   Por Qué 4: [pregunta] → [causa identificada]
   Por Qué 5: [pregunta] → [causa raíz sistémica]

   CAUSA RAÍZ IDENTIFICADA: [síntesis en 1-2 oraciones]

   ACCIONES CORRECTIVAS SISTÉMICAS (mínimo 3):
   - Acción 1: [descripción] | Responsable: [rol] | Plazo: [tiempo]
   - Acción 2: [descripción] | Responsable: [rol] | Plazo: [tiempo]
   - Acción 3: [descripción] | Responsable: [rol] | Plazo: [tiempo]
   ```

2. Revise la cadena de 5 Por Qué generada. Evalúe si cada nivel de causa explica lógicamente el nivel anterior. Si detecta un salto lógico, solicite a Copilot que lo corrija con el siguiente prompt de seguimiento:

   ```text
   En el Por Qué 3, la causa identificada no explica
   suficientemente la causa del Por Qué 2. ¿Puedes replantear
   ese nivel con una causa más específica y verificable?
   ```

3. **Copie el análisis completo** de los 5 Por Qué y péguelo en una nueva hoja del archivo Excel llamada **"ACR - 5 Por Qué"**.

**Resultado esperado:** Una cadena lógica de 5 niveles causales que lleva desde el síntoma observable (resbalones) hasta una causa sistémica (por ejemplo: ausencia de un programa formal de inspección de pisos con registro documentado). Las tres acciones correctivas deben ser específicas, asignables y medibles.

**Verificación:** Verifique que la causa raíz identificada sea de naturaleza **sistémica o de gestión** (no debe ser simplemente "el operario no tuvo cuidado"). Una causa raíz verdadera siempre apunta a un fallo en procesos, sistemas o controles organizacionales.

---

#### Paso 2.3 — Generar el Diagrama de Ishikawa para el incidente de mayor severidad

**Objetivo:** Construir un análisis de Ishikawa estructurado por categorías para el incidente con mayor impacto en días perdidos.

**Instrucciones:**

1. Basándose en el caso 2 identificado (adapte al incidente real del dataset), ingrese el siguiente prompt. El ejemplo usa "atrapamiento en maquinaria":

   ```text
   Genera un análisis de Ishikawa (Diagrama de Espina de Pescado)
   para el siguiente problema de seguridad industrial:

   PROBLEMA (cabeza del pescado): "Atrapamiento en maquinaria
   en el área de producción — 5 incidentes en 12 meses,
   generando 47 días perdidos acumulados."

   Organiza las causas potenciales en las 6 categorías clásicas:

   🔵 MANO DE OBRA (factores humanos y de comportamiento)
   🔴 MÁQUINA (factores de equipo e instalaciones)
   🟢 MÉTODO (procedimientos y prácticas de trabajo)
   🟡 MATERIAL (insumos, herramientas, EPP)
   🟠 MEDIO AMBIENTE (condiciones físicas del entorno)
   🟣 MEDICIÓN (sistemas de monitoreo y registro)

   Proporciona mínimo 3 causas potenciales por categoría.
   Para cada causa, indica si es: [CONFIRMADA por datos],
   [PROBABLE - requiere verificación] o [POSIBLE - hipótesis].
   Al final, señala las 3 causas con mayor probabilidad de
   ser la causa raíz real, justificando tu selección.
   ```

2. Revise el análisis generado. Identifique las categorías con mayor densidad de causas (esto indica las áreas de mayor riesgo sistémico).
3. **Copie el análisis de Ishikawa** y péguelo en una nueva hoja llamada **"ACR - Ishikawa"**.
4. Como paso adicional, solicite a Copilot que compare ambos análisis:

   ```text
   Comparando el análisis de 5 Por Qué del incidente de
   resbalones y caídas con el Diagrama de Ishikawa del
   atrapamiento en maquinaria, ¿qué factores causales
   aparecen en ambos análisis? ¿Qué nos indica esto sobre
   los problemas sistémicos de gestión de seguridad en
   esta planta?
   ```

**Resultado esperado:** Un Diagrama de Ishikawa con 18+ causas potenciales distribuidas en las 6 categorías, cada una clasificada por nivel de certeza. Las 3 causas prioritarias deben estar justificadas con referencia a los datos del dataset. El análisis comparativo debe identificar al menos 2 factores causales comunes entre ambos incidentes (por ejemplo: falta de capacitación documentada y ausencia de inspecciones periódicas).

**Verificación:** Confirme que las causas clasificadas como [CONFIRMADA por datos] puedan efectivamente verificarse en el dataset de Excel (por ejemplo, si Copilot dice "mayor incidentalidad en turno nocturno", filtre la tabla para confirmarlo).

---

### BLOQUE 3: Identificación de Tendencias y Patrones

**⏱️ Tiempo estimado: 20 minutos**

**Objetivo del bloque:** Utilizar Copilot para identificar tendencias temporales, patrones por área y turno, y correlaciones entre variables que permitan anticipar riesgos y diseñar estrategias preventivas.

---

#### Paso 3.1 — Análisis de tendencias temporales

**Objetivo:** Identificar si la accidentabilidad muestra tendencias crecientes, decrecientes o estacionales a lo largo de los 12 meses.

**Instrucciones:**

1. En el panel de Copilot, ingrese:

   ```text
   Analiza la tendencia temporal de los incidentes en este dataset.
   Específicamente:

   1. ¿La accidentabilidad general muestra una tendencia creciente,
      decreciente o estable a lo largo de los 12 meses?
      Apoya tu respuesta con los datos numéricos.

   2. ¿Existen patrones estacionales? (por ejemplo, mayor
      incidentalidad en ciertos meses o trimestres)

   3. ¿Hay algún mes que represente un punto de inflexión
      significativo (cambio brusco al alza o a la baja)?
      ¿Qué podría explicarlo?

   4. Proyecta (de forma estimada) cómo podría comportarse
      la accidentabilidad en los próximos 3 meses si no se
      implementan cambios, basándote en la tendencia actual.

   Usa datos específicos del dataset para respaldar cada punto.
   ```

2. Anote los hallazgos de tendencia. Estos serán utilizados en el Bloque 4 para seleccionar el tipo de gráfica más adecuado.

**Resultado esperado:** Un análisis de tendencia que identifique, por ejemplo, un incremento del 15% en el Q3, una reducción en enero-febrero (posiblemente por menor actividad productiva), y un pico en octubre. La proyección debe estar claramente marcada como estimada.

**Verificación:** La tendencia identificada por Copilot debe ser consistente con los datos. Cree una tabla dinámica rápida en Excel (Insertar → Tabla dinámica → Filas: Mes, Valores: Conteo de incidentes) para confirmar visualmente la tendencia.

---

#### Paso 3.2 — Análisis por área y por turno

**Objetivo:** Identificar qué áreas y turnos concentran mayor riesgo y determinar si existen correlaciones entre variables.

**Instrucciones:**

1. En el panel de Copilot, ingrese:

   ```text
   Realiza un análisis de incidentalidad por área de planta
   y por turno de trabajo:

   ANÁLISIS POR ÁREA:
   - Ranking de áreas por número total de incidentes
   - Ranking de áreas por días perdidos acumulados
   - ¿El área con más incidentes es también la de mayor severidad?

   ANÁLISIS POR TURNO:
   - Comparativa de incidentes por turno (matutino/vespertino/nocturno)
   - ¿El turno nocturno presenta mayor severidad (días perdidos/incidente)?
   - ¿Hay tipos de incidente que se concentren en turnos específicos?

   CORRELACIONES:
   - ¿Existe correlación entre el área de trabajo y el tipo de incidente?
   - ¿Existe correlación entre el turno y la severidad del incidente?

   Presenta los resultados en tablas comparativas y señala
   las 3 combinaciones área-turno de mayor riesgo.
   ```

2. Identifique las **3 combinaciones área-turno de mayor riesgo** señaladas por Copilot. Estas serán el foco de las recomendaciones preventivas.
3. Solicite a Copilot que genere recomendaciones específicas:

   ```text
   Basándote en las 3 combinaciones área-turno de mayor riesgo
   identificadas, propón una estrategia de intervención preventiva
   para cada una. Cada estrategia debe incluir:
   - Medida de control principal (eliminación/sustitución/
     ingeniería/administrativa/EPP — jerarquía de controles)
   - Indicador de seguimiento
   - Plazo de implementación recomendado
   ```

**Resultado esperado:** Tablas comparativas por área y turno, identificación de correlaciones (por ejemplo: los atrapamientos ocurren 80% en el turno nocturno en el Área de Producción), y 3 estrategias preventivas específicas con jerarquía de controles aplicada correctamente.

**Verificación:** Verifique al menos una correlación identificada filtrando manualmente la tabla de Excel (Filtro por Área + Filtro por Turno → contar incidentes). La cifra debe coincidir con lo reportado por Copilot.

---

#### Paso 3.3 — Síntesis del análisis para audiencias ejecutivas

**Objetivo:** Generar un resumen ejecutivo conciso de los hallazgos del análisis para presentación a la dirección.

**Instrucciones:**

1. En el panel de Copilot, ingrese:

   ```text
   Con base en todo el análisis realizado (indicadores EHS,
   análisis causa raíz, tendencias y patrones), redacta un
   resumen ejecutivo de máximo 200 palabras con el siguiente
   formato:

   RESUMEN EJECUTIVO — ANÁLISIS DE ACCIDENTABILIDAD
   Planta Industrial Ficticia | Período: [meses del dataset]

   SITUACIÓN ACTUAL:
   [2-3 oraciones con los indicadores clave y su comparación
   con benchmarks de la industria]

   HALLAZGOS CRÍTICOS:
   [3 puntos de bala con los hallazgos más importantes]

   CAUSAS RAÍZ IDENTIFICADAS:
   [2 puntos de bala con las causas sistémicas principales]

   RECOMENDACIONES PRIORITARIAS:
   [3 acciones específicas, ordenadas por impacto esperado]

   Usa un tono formal, orientado a la toma de decisiones,
   sin tecnicismos excesivos para una audiencia directiva.
   ```

2. Guarde este resumen en una nueva hoja llamada **"Resumen Ejecutivo"**.

**Resultado esperado:** Un texto de 150–200 palabras, estructurado, con datos numéricos específicos del dataset, causas raíz identificadas en el Bloque 2 y recomendaciones alineadas con los hallazgos del Bloque 3.

**Verificación:** El resumen debe mencionar al menos dos indicadores calculados en el Bloque 1 (TRIR, LTIR o sus equivalentes) y al menos una causa raíz identificada en el Bloque 2.

---

### BLOQUE 4: Visualización Óptima y Construcción del Dashboard EHS

**⏱️ Tiempo estimado: 25 minutos**

**Objetivo del bloque:** Determinar con Copilot qué tipo de representación visual es más adecuada para cada conjunto de datos EHS y construir un dashboard básico de indicadores en Excel.

---

#### Paso 4.1 — Seleccionar el tipo de gráfica adecuado para cada dato

**Objetivo:** Aprender a seleccionar el tipo de visualización más efectivo para comunicar diferentes tipos de datos de seguridad a diferentes audiencias.

**Instrucciones:**

1. En el panel de Copilot, ingrese:

   ```text
   Soy un especialista EHS que necesita presentar los resultados
   del análisis de accidentabilidad a tres audiencias diferentes:
   (A) Dirección General, (B) Jefes de Área, (C) Operarios en planta.

   Para cada uno de los siguientes conjuntos de datos, recomienda:
   - El tipo de gráfica más adecuado
   - Por qué es la mejor opción para ese dato y audiencia
   - Qué variable va en cada eje (o segmento, en caso de circular)
   - Un título sugerido para la gráfica

   CONJUNTOS DE DATOS:
   1. Evolución mensual del número total de incidentes (12 meses)
   2. Comparación de incidentes por área de planta
   3. Distribución de tipos de incidente (resbalones, atrapamientos, etc.)
   4. Tendencia del TRIR mensual vs. benchmark de la industria
   5. Relación entre turno de trabajo y severidad (días perdidos)
   6. Proporción de incidentes con y sin días perdidos

   Presenta las recomendaciones en una tabla con columnas:
   Dato | Audiencia | Tipo de gráfica | Justificación | Ejes/Segmentos | Título sugerido
   ```

2. Revise las recomendaciones de Copilot. Anote los tipos de gráfica sugeridos para cada conjunto de datos.

**Resultado esperado:** Una tabla con 6 filas de recomendaciones. Copilot debe sugerir, por ejemplo: línea de tiempo para tendencias mensuales, barras horizontales para comparación por área, gráfica de pastel para distribución de tipos, línea con área para TRIR vs. benchmark, barras apiladas para turno vs. severidad, y donut para proporción con/sin días perdidos.

**Verificación:** Evalúe si las justificaciones de Copilot son coherentes con principios de visualización de datos (por ejemplo: las gráficas de pastel son adecuadas para proporciones de hasta 5-6 categorías; las de línea son ideales para tendencias temporales).

---

#### Paso 4.2 — Generar las gráficas en Excel con Copilot

**Objetivo:** Utilizar Copilot para crear directamente las gráficas más importantes en Excel.

**Instrucciones:**

1. En el panel de Copilot, ingrese el siguiente prompt para crear la primera gráfica:

   ```text
   Crea una gráfica de línea que muestre la evolución mensual
   del número total de incidentes durante los 12 meses del dataset.
   - Eje X: Mes (enero a diciembre)
   - Eje Y: Número de incidentes
   - Título: "Tendencia Mensual de Incidentes — Planta Industrial 2024"
   - Añade una línea de tendencia lineal (trendline)
   - Coloca la gráfica en una nueva hoja llamada "Dashboard EHS"
   ```

2. Si Copilot genera la gráfica directamente, verifique que esté correctamente configurada. Si Copilot proporciona instrucciones paso a paso en lugar de crearla directamente, siga estos pasos manuales:
   - Seleccione los datos de mes y conteo de incidentes.
   - Vaya a **Insertar** → **Gráficos recomendados** → **Línea**.
   - Haga clic derecho sobre la línea → **Agregar línea de tendencia** → **Lineal**.
   - Mueva la gráfica a la hoja "Dashboard EHS".

3. Repita el proceso para crear las siguientes gráficas adicionales. Use prompts similares adaptados a cada caso:

   ```text
   Crea una gráfica de barras horizontales que compare el número
   total de incidentes por área de planta durante los 12 meses.
   Ordena las barras de mayor a menor incidentalidad.
   Título: "Incidentes por Área de Planta — Ranking Anual"
   Colócala en la hoja "Dashboard EHS" junto a la gráfica anterior.
   ```

   ```text
   Crea una gráfica de pastel que muestre la distribución porcentual
   de los tipos de incidente registrados en el dataset.
   Muestra el porcentaje en cada segmento.
   Título: "Distribución por Tipo de Incidente"
   Colócala en la hoja "Dashboard EHS".
   ```

4. Una vez creadas las tres gráficas, organícelas visualmente en la hoja "Dashboard EHS" para que formen un panel coherente.

**Resultado esperado:** Una hoja "Dashboard EHS" con tres gráficas correctamente tituladas, con ejes etiquetados y datos del dataset. La gráfica de tendencia debe mostrar una línea de tendencia visible. Las gráficas deben ser legibles a resolución 1920×1080.

**Verificación:** Haga clic en cada gráfica y verifique en la barra de fórmulas que los datos fuente referencian correctamente la tabla del dataset (no valores estáticos copiados).

---

#### Paso 4.3 — Añadir tarjetas de indicadores KPI al dashboard

**Objetivo:** Complementar las gráficas con los indicadores numéricos calculados en el Bloque 1 para crear un dashboard completo.

**Instrucciones:**

1. En el panel de Copilot, ingrese:

   ```text
   Quiero agregar tarjetas de KPI al dashboard en la hoja
   "Dashboard EHS". Para cada uno de los siguientes indicadores,
   proporciona instrucciones para crear una celda formateada
   que muestre el valor de forma destacada:

   KPI 1: TRIR (valor calculado)
   KPI 2: LTIR (valor calculado)
   KPI 3: Índice de Frecuencia (valor calculado)
   KPI 4: Índice de Gravedad (valor calculado)
   KPI 5: Total de incidentes en el período
   KPI 6: Total de días perdidos

   Para cada KPI, sugiere:
   - Formato de celda recomendado (color, tamaño de fuente)
   - Si el valor es "alto" o "bajo" respecto a benchmarks típicos
     de la industria manufacturera
   - Un ícono o indicador visual de estado (🟢 bueno / 🟡 atención / 🔴 crítico)
   ```

2. Siga las instrucciones de Copilot para crear las tarjetas KPI en la parte superior de la hoja "Dashboard EHS".
3. Vincule cada tarjeta KPI a las fórmulas creadas en la hoja "Indicadores" (use referencias de celda, no valores estáticos).
4. Solicite a Copilot una última validación del dashboard:

   ```text
   Revisa el dashboard que hemos construido. Considerando que
   será presentado a la Dirección General de una planta industrial,
   ¿qué elementos adicionales recomendarías agregar para hacerlo
   más efectivo para la toma de decisiones? Proporciona máximo
   3 recomendaciones específicas y aplicables.
   ```

**Resultado esperado:** Un dashboard con 6 tarjetas KPI en la parte superior (con código de color semáforo) y las 3 gráficas en la parte inferior. Las tarjetas deben estar vinculadas a fórmulas, no a valores estáticos. Copilot debe proporcionar 3 recomendaciones de mejora concretas (por ejemplo: agregar filtro por período, incluir comparativa con año anterior, añadir tabla de incidentes pendientes de cierre).

**Verificación:** Modifique manualmente un valor en el dataset (cambie un "1" por un "2" en la columna de días perdidos) y verifique que las tarjetas KPI y las gráficas se actualicen automáticamente. Deshaga el cambio (Ctrl+Z) después de la verificación.

---

## Validación y Pruebas del Laboratorio

Al finalizar los cuatro bloques, realice las siguientes verificaciones de completitud:

### Lista de Verificación Final

| # | Elemento a Verificar | Criterio de Éxito | ✅/❌ |
|---|---|---|---|
| 1 | Hoja "Indicadores" | Contiene los 4 indicadores EHS (TRIR, LTIR, IF, IG) calculados con fórmulas vinculadas al dataset | |
| 2 | Hoja "ACR - 5 Por Qué" | Contiene la cadena completa de 5 niveles causales para el incidente más frecuente, con causa raíz sistémica identificada | |
| 3 | Hoja "ACR - Ishikawa" | Contiene el análisis de Ishikawa con las 6 categorías y mínimo 3 causas por categoría, con clasificación de certeza | |
| 4 | Hoja "Resumen Ejecutivo" | Contiene el texto de 150-200 palabras con indicadores, causas raíz y recomendaciones | |
| 5 | Hoja "Dashboard EHS" | Contiene mínimo 3 gráficas correctamente tituladas y 6 tarjetas KPI | |
| 6 | Gráficas vinculadas | Las gráficas referencian el dataset original (no valores estáticos) | |
| 7 | KPIs con semáforo | Las tarjetas KPI incluyen indicador de estado (🟢/🟡/🔴) | |
| 8 | Análisis comparativo ACR | Existe al menos un análisis que identifica factores causales comunes entre los dos incidentes analizados | |

### Prueba de Integridad del Dashboard

1. En la hoja del dataset, aplique un filtro para mostrar solo los incidentes del **primer semestre** (enero–junio).
2. Observe si las gráficas del dashboard cambian. **Si cambian:** las gráficas están correctamente vinculadas. **Si no cambian:** las gráficas pueden contener datos estáticos; corrija referenciando las celdas del dataset.
3. Elimine el filtro (Datos → Borrar filtro) para restaurar la vista completa.

---

## Solución de Problemas

### Problema 1: El botón de Copilot en Excel aparece atenuado o no responde

**Síntoma:** El botón Copilot en la cinta de opciones de Excel está en color gris, no es clickeable, o al hacer clic no abre el panel lateral.

**Causa:** Este problema tiene dos causas posibles: (a) el archivo Excel está guardado localmente en el disco duro y no en OneDrive/SharePoint — Copilot en Excel **requiere** que el archivo esté en la nube; (b) la licencia de Microsoft 365 Copilot no está activa o no ha sido asignada a la cuenta del usuario.

**Solución:**

Para la causa (a) — archivo local:
1. En Excel, vaya a **Archivo** → **Guardar como** → **OneDrive** o **SharePoint**.
2. Seleccione la biblioteca de práctica del curso y guarde el archivo.
3. Espere a que aparezca el ícono de sincronización ☁️ en la barra de título.
4. Cierre y vuelva a abrir el archivo desde OneDrive/SharePoint.
5. El botón de Copilot debería estar habilitado.

Para la causa (b) — licencia inactiva:
1. Abra Microsoft Edge y navegue a `https://portal.office.com`.
2. Verifique que su cuenta tenga el ícono de Copilot visible en el portal.
3. Si no aparece, contacte al administrador de TI para verificar la asignación de licencia.
4. El administrador debe confirmar que la licencia **"Microsoft 365 Copilot"** está asignada al usuario en el Centro de Administración de Microsoft 365.

---

### Problema 2: Copilot en Excel genera resultados incorrectos o no reconoce las columnas del dataset

**Síntoma:** Copilot responde con valores numéricos que no coinciden con el dataset, menciona columnas con nombres incorrectos, o indica que "no puede encontrar los datos solicitados" a pesar de que la tabla está visible.

**Causa:** El dataset no está formateado como **Tabla de Excel** (con la función Tabla oficial de Excel, no solo un rango de celdas con formato visual). Copilot en Excel analiza los datos a través de la estructura de Tabla; si los datos son un rango simple, Copilot puede no reconocer correctamente los encabezados o los tipos de dato.

**Solución:**

1. Seleccione cualquier celda dentro del rango de datos del dataset.
2. Vaya a **Insertar** → **Tabla** (o presione `Ctrl + T`).
3. En el cuadro de diálogo, verifique que el rango sea correcto y que la opción **"La tabla tiene encabezados"** esté marcada.
4. Haga clic en **Aceptar**.
5. Asigne un nombre descriptivo a la tabla: haga clic en la tabla → pestaña **Diseño de tabla** → campo **Nombre de tabla** → escriba `TblAccidentabilidad`.
6. Guarde el archivo (Ctrl + S) y espere a que se sincronice con OneDrive.
7. Regrese al panel de Copilot y repita el prompt. Ahora Copilot debería reconocer correctamente los encabezados y tipos de dato.

> 💡 **Tip adicional:** Si los encabezados de columna contienen caracteres especiales, espacios excesivos o están en filas combinadas, esto puede confundir a Copilot. Asegúrese de que cada encabezado sea una cadena de texto simple y única en la fila 1 de la tabla.

---

## Limpieza y Cierre del Laboratorio

Al finalizar el laboratorio, realice los siguientes pasos para cerrar correctamente el entorno de trabajo:

1. **Guardar el archivo final:**
   - Presione `Ctrl + S` para guardar todos los cambios.
   - Verifique que el ícono de sincronización ☁️ en la barra de título no muestre pendientes de carga.
   - El archivo debe quedar guardado en OneDrive/SharePoint con el nombre: `Dataset_Accidentabilidad_PlantaFicticia_Completado_[SuNombre].xlsx`

2. **Renombrar el archivo para entrega:**
   - En OneDrive/SharePoint, haga clic derecho sobre el archivo → **Cambiar nombre**.
   - Use el formato: `Lab03-[SuNombre]-[Fecha].xlsx` (ejemplo: `Lab03-JuanGarcia-20240615.xlsx`).

3. **Compartir con el instructor (si aplica):**
   - En OneDrive/SharePoint, haga clic derecho sobre el archivo → **Compartir**.
   - Ingrese el correo del instructor y asigne permisos de **Solo lectura**.
   - Haga clic en **Enviar**.

4. **Cerrar el panel de Copilot:**
   - Haga clic en la **X** del panel de Copilot para cerrarlo.
   - Esto libera recursos del sistema si continuará trabajando con otras aplicaciones.

5. **Verificar privacidad de datos:**
   - Revise rápidamente las hojas del archivo para confirmar que no contiene datos reales de empleados ni información confidencial de la empresa.
   - Confirme que todos los datos corresponden al dataset ficticio proporcionado.

> ⚠️ **No elimine** el archivo del dataset original (`Dataset_Accidentabilidad_PlantaFicticia.xlsx`) de la biblioteca de SharePoint del curso. Este archivo es compartido y será utilizado por otros participantes.

---

## Resumen del Laboratorio

### Lo que se logró en este laboratorio

En este laboratorio de 90 minutos aplicó un flujo de trabajo completo de análisis de seguridad industrial asistido por IA, cubriendo cuatro dimensiones fundamentales de la gestión EHS:

| Bloque | Habilidad desarrollada | Herramienta clave |
|---|---|---|
| **Bloque 1** | Análisis exploratorio y cálculo de indicadores TRIR, LTIR, IF, IG | Copilot en Excel + Tablas |
| **Bloque 2** | Análisis Causa Raíz: 5 Por Qué e Ishikawa con IA | Copilot + Metodología ACR |
| **Bloque 3** | Identificación de tendencias, patrones y correlaciones | Copilot + Tablas dinámicas |
| **Bloque 4** | Selección de visualizaciones y construcción de dashboard EHS | Copilot + Gráficas de Excel |

### Conceptos Clave Reforzados

- **Tres niveles de causa en ACR:** causa inmediata → causa contributiva → causa raíz sistémica. Solo corregir la causa raíz previene la recurrencia.
- **Copilot como amplificador del juicio experto:** la IA genera hipótesis y estructura análisis; el especialista EHS valida, descarta y toma decisiones.
- **Prompts estructurados = resultados de calidad:** un prompt con contexto del incidente, metodología solicitada y formato de salida produce análisis directamente utilizables en informes profesionales.
- **La visualización debe servir a la audiencia:** diferentes audiencias (dirección, jefes de área, operarios) requieren diferentes niveles de detalle y tipos de representación visual.
- **Integridad del dato sobre la velocidad:** siempre verifique manualmente al menos una muestra de los resultados generados por Copilot contra los datos originales.

### Recursos de Referencia

| Recurso | Descripción | Enlace |
|---|---|---|
| Documentación oficial de Copilot en Excel | Guía de uso de Copilot integrado en Microsoft Excel | [learn.microsoft.com/es-es/copilot/microsoft-365/microsoft-365-copilot-in-excel](https://learn.microsoft.com/es-es/copilot/microsoft-365/microsoft-365-copilot-in-excel) |
| Metodología 5 Por Qué — ASQ | Referencia técnica de la técnica iterativa de análisis causal | [asq.org/quality-resources/five-whys](https://asq.org/quality-resources/five-whys) |
| Guía ACR — OSHA | Guía oficial de análisis causa raíz para entornos industriales | [osha.gov/root-cause-analysis](https://www.osha.gov/root-cause-analysis) |
| Indicadores EHS — OSHA Recordkeeping | Definiciones y fórmulas oficiales de TRIR y LTIR | [osha.gov/recordkeeping](https://www.osha.gov/recordkeeping) |
| ISO 45001:2018 | Estándar internacional de gestión de seguridad y salud en el trabajo | [iso.org/iso-45001](https://www.iso.org/iso-45001-occupational-health-and-safety.html) |
| Mejores prácticas de visualización de datos — Microsoft | Guía de gráficas en Excel para análisis de datos | [support.microsoft.com/es-es/excel](https://support.microsoft.com/es-es/office/tipos-de-gr%C3%A1ficos-disponibles-en-office-a6187218-807e-4103-9e0a-27cdb19afb90) |

---

> 📝 **Nota para el instructor:** Los participantes que no hayan completado satisfactoriamente este laboratorio (específicamente los Bloques 1 y 2) no podrán avanzar al Laboratorio 4, ya que los análisis ACR y los indicadores calculados aquí son la base del flujo acumulativo de los módulos siguientes. Utilice los archivos de checkpoint disponibles en SharePoint para que los participantes rezagados puedan continuar desde un estado consistente.

---
