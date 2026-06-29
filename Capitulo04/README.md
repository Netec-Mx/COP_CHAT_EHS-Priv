# Taller de Consolidación — Análisis Predictivo y Reporte Integral de Seguridad Patrimonial

## Metadatos

| Campo            | Detalle                                      |
|------------------|----------------------------------------------|
| **Duración**     | 90 minutos                                   |
| **Complejidad**  | Alta                                         |
| **Nivel Bloom**  | Aplicar (Apply)                              |
| **Módulo**       | 4 — Auditoría Inteligente y Seguridad Patrimonial |
| **Práctica**     | 4 de 4 (Taller de Consolidación)             |

---

## Descripción General

Este laboratorio es el taller de consolidación del bloque analítico del curso. Los participantes trabajarán con un escenario complejo de seguridad patrimonial que integra registros de auditorías de seis meses, bitácoras de incidentes en Excel, descripciones textuales de observaciones de cámaras CCTV y reportes de rondines de vigilancia. Utilizando Microsoft 365 Copilot como asistente cognitivo, analizarán múltiples fuentes de datos para identificar patrones de riesgo recurrentes, detectar tendencias predictivas y generar un reporte integral de hallazgos que sirva como activo preventivo para la organización. El laboratorio aplica directamente los conceptos de detección inteligente de actos inseguros y condiciones inseguras estudiados en la Lección 4.1.

---

## Objetivos de Aprendizaje

Al finalizar este laboratorio, el participante será capaz de:

- [ ] Referenciar múltiples documentos en SharePoint desde Copilot para realizar un análisis integrado de seguridad patrimonial, identificando actos inseguros recurrentes y condiciones inseguras persistentes.
- [ ] Aplicar prompts estructurados con rol, instrucciones numeradas y referencias normativas para extraer patrones de riesgo a partir de descripciones textuales de registros de CCTV y bitácoras técnicas.
- [ ] Interpretar y sintetizar información proveniente de fuentes heterogéneas (auditorías, bitácoras, CCTV, rondines) para construir un análisis de tendencias predictivas en seguridad patrimonial.
- [ ] Generar un reporte integral de hallazgos en Microsoft Word con Copilot, que incluya resumen ejecutivo, mapa de riesgos, hallazgos críticos con evidencia, análisis predictivo y plan de acción preventivo.

---

## Prerrequisitos

### Conocimiento Previo

- Haber completado las Prácticas 1, 2 y 3 del curso satisfactoriamente.
- Comprensión de la taxonomía de actos inseguros y condiciones inseguras (Lección 4.1).
- Familiaridad con los conceptos de seguridad patrimonial: control de accesos, rondines, CCTV, perímetro de seguridad.
- Haber revisado el material sobre detección de actos inseguros y condiciones inseguras del Módulo 4.

### Accesos y Configuración Requerida

- Licencia de Microsoft 365 Copilot activa y verificada en Word y Excel.
- Acceso a la carpeta **Módulo 4 — Práctica 4** en SharePoint del curso (URL proporcionada por el instructor).
- Los siguientes archivos deben estar disponibles en la carpeta de SharePoint **antes de iniciar el laboratorio**:

| Archivo                                      | Tipo    | Descripción                                                        |
|----------------------------------------------|---------|--------------------------------------------------------------------|
| `Auditorias_Seguridad_Patrimonial_6M.docx`   | Word    | Registros de auditorías de los últimos 6 meses (texto estructurado)|
| `Bitacora_Incidentes_Patrimonial.xlsx`        | Excel   | Bitácora de incidentes patrimoniales (datos tabulares)             |
| `Registros_CCTV_Observaciones.docx`          | Word    | Descripciones textuales de observaciones de cámaras de seguridad  |
| `Reportes_Rondines_Vigilancia.docx`          | Word    | Reportes de rondines de vigilancia (últimos 6 meses)               |
| `Plantilla_Reporte_Integral_EHS.docx`        | Word    | Plantilla base para el reporte integral de hallazgos               |

> ⚠️ **IMPORTANTE — Privacidad de Datos:** Todos los archivos de práctica contienen **datos ficticios**. Está estrictamente prohibido ingresar información personal real de empleados, datos confidenciales de la empresa o información sensible de seguridad en los prompts de Copilot. Recuerde este principio durante toda la práctica.

> ⚠️ **IMPORTANTE — Almacenamiento en la Nube:** Copilot en Word y Excel **solo funciona con archivos almacenados en OneDrive o SharePoint**. No trabaje con archivos guardados localmente en su disco duro.

---

## Entorno de Laboratorio

### Hardware Recomendado

| Componente       | Especificación Mínima                                         |
|------------------|---------------------------------------------------------------|
| Procesador       | Intel Core i5 8ª gen. o AMD Ryzen 5 equivalente              |
| RAM              | 8 GB (16 GB recomendado para múltiples aplicaciones abiertas) |
| Pantalla         | Resolución 1920×1080 (monitor secundario recomendado)         |
| Conexión         | Internet estable ≥ 10 Mbps                                    |
| Almacenamiento   | 10 GB libres en disco                                         |

### Software Requerido

| Aplicación                  | Versión / Acceso                                              |
|-----------------------------|---------------------------------------------------------------|
| Microsoft Word              | Microsoft 365 Apps (canal actual), archivo en SharePoint      |
| Microsoft Excel             | Microsoft 365 Apps (canal actual), archivo en SharePoint      |
| Microsoft SharePoint Online | Acceso vía navegador o cliente integrado en M365              |
| Microsoft 365 Copilot       | Licencia activa, habilitada en Word y Excel                   |
| Microsoft Edge              | Versión estable más reciente (navegador recomendado)          |

### Configuración Inicial del Entorno

Antes de comenzar los pasos del laboratorio, ejecute la siguiente verificación:

**1. Verificar acceso a SharePoint y archivos de práctica:**

```
1. Abra Microsoft Edge y navegue a la URL de SharePoint del curso
   (proporcionada por el instructor).
2. Localice la carpeta: Módulo 4 — Práctica 4
3. Confirme que los 5 archivos listados en la tabla de prerrequisitos
   están presentes y accesibles.
4. Si algún archivo falta, contacte al instructor ANTES de continuar.
```

**2. Verificar que Copilot está activo en Word:**

```
1. Abra el archivo Plantilla_Reporte_Integral_EHS.docx desde SharePoint
   (NO lo descargue al disco local).
2. En la cinta de opciones, verifique que aparece el botón "Copilot"
   (ícono de estrella de colores) en la pestaña Inicio o en la barra lateral.
3. Si no aparece, contacte al administrador de TI — la licencia puede
   no estar activa en su cuenta.
```

**3. Abrir todos los archivos necesarios en pestañas separadas:**

```
1. Abra los siguientes archivos desde SharePoint en Microsoft Edge
   (cada uno en una pestaña separada del navegador o en Word Online):
   - Auditorias_Seguridad_Patrimonial_6M.docx
   - Registros_CCTV_Observaciones.docx
   - Reportes_Rondines_Vigilancia.docx
   - Plantilla_Reporte_Integral_EHS.docx
2. Abra Bitacora_Incidentes_Patrimonial.xlsx en Excel Online
   (desde SharePoint, clic derecho > Abrir en Excel Online).
3. Mantenga todas las pestañas abiertas durante el laboratorio.
```

---

## Procedimiento Paso a Paso

El laboratorio se divide en tres bloques de trabajo que deben completarse en secuencia:

| Bloque | Actividad                                          | Tiempo Estimado |
|--------|----------------------------------------------------|-----------------|
| 1      | Análisis multi-fuente con Copilot                  | 25 minutos      |
| 2      | Análisis de registros técnicos (CCTV y bitácoras)  | 25 minutos      |
| 3      | Generación del reporte integral de hallazgos       | 35 minutos      |
| —      | Verificación y cierre                              | 5 minutos       |

---

### BLOQUE 1 — Análisis Multi-Fuente con Copilot (25 minutos)

#### Paso 1.1: Revisión Inicial de Fuentes de Datos

**Objetivo:** Familiarizarse con el contenido de los cuatro archivos de práctica antes de iniciar el análisis asistido por IA.

**Instrucciones:**

1. En la pestaña del archivo `Auditorias_Seguridad_Patrimonial_6M.docx`, lea los encabezados principales y las primeras observaciones de cada mes. Identifique mentalmente los tipos de hallazgos que aparecen (no los analice en profundidad todavía).

2. En la pestaña de `Bitacora_Incidentes_Patrimonial.xlsx`, observe las columnas disponibles. El archivo debe contener columnas similares a:

   | Fecha | Área | Tipo de Incidente | Descripción | Severidad | Responsable | Estado |
   |-------|------|-------------------|-------------|-----------|-------------|--------|

3. Haga clic en la pestaña del archivo `Registros_CCTV_Observaciones.docx` y lea los primeros dos registros para entender el formato de las observaciones textuales de cámaras.

4. Revise brevemente `Reportes_Rondines_Vigilancia.docx` para identificar la estructura de los reportes de rondín.

5. En su cuaderno o en un documento de notas aparte, anote: ¿Qué tipos de riesgos patrimoniales anticipa encontrar en estos documentos? (Ejemplo: accesos no autorizados, fallas en iluminación perimetral, comportamientos sospechosos, etc.)

**Resultado Esperado:** El participante tiene una visión general del contenido de las cuatro fuentes de datos y ha formulado hipótesis iniciales sobre los riesgos presentes.

**Verificación:** Confirme que puede navegar entre los cuatro archivos abiertos en SharePoint/Word Online sin necesidad de descargarlos localmente.

---

#### Paso 1.2: Análisis Integrado de Auditorías con Copilot (Referenciación Multi-Documento)

**Objetivo:** Utilizar Copilot en Word para analizar simultáneamente los registros de auditorías y los reportes de rondines, identificando actos inseguros y condiciones inseguras recurrentes.

**Instrucciones:**

1. Navegue a la pestaña del archivo `Plantilla_Reporte_Integral_EHS.docx` (este será su documento de trabajo principal durante todo el laboratorio).

2. Abra el panel de Copilot haciendo clic en el botón **Copilot** en la cinta de opciones (o use el atajo `Alt + I` si está disponible).

3. En el panel de Copilot, haga clic en el ícono de **adjuntar archivo** (ícono de clip 📎) y adjunte los siguientes archivos desde SharePoint:
   - `Auditorias_Seguridad_Patrimonial_6M.docx`
   - `Reportes_Rondines_Vigilancia.docx`

   > 💡 **Nota:** Si la función de adjuntar no está disponible en su versión, puede referenciar los archivos escribiendo `/` seguido del nombre del archivo en el campo de prompt de Copilot. Consulte con el instructor si tiene dudas sobre el método de referenciación en su entorno.

4. Una vez adjuntados los archivos, ingrese el siguiente prompt en el panel de Copilot:

   ```text
   Eres un experto en seguridad patrimonial e industrial con conocimiento
   en normas STPS, ISO 45001 y mejores prácticas de control de accesos y
   vigilancia perimetral.

   Analiza los dos documentos adjuntos (registros de auditorías de 6 meses
   y reportes de rondines de vigilancia) y realiza lo siguiente:

   1. Identifica los ACTOS INSEGUROS recurrentes que aparecen en múltiples
      auditorías o rondines (menciona en cuántos registros aparece cada uno).
   2. Identifica las CONDICIONES INSEGURAS persistentes que se repiten a lo
      largo del período analizado.
   3. Señala las ÁREAS O ZONAS con mayor concentración de hallazgos.
   4. Clasifica cada hallazgo recurrente según su nivel de riesgo:
      CRÍTICO, ALTO, MEDIO o BAJO.
   5. Indica si existe alguna tendencia de INCREMENTO o DISMINUCIÓN en la
      frecuencia de cada tipo de hallazgo a lo largo de los 6 meses.

   Presenta los resultados en formato de tabla estructurada.
   ```

5. Presione **Enter** y espere la respuesta de Copilot (puede tomar entre 15 y 45 segundos dependiendo del volumen de los documentos).

6. Revise la tabla generada. Si algún hallazgo le parece incompleto o ambiguo, formule un prompt de seguimiento como:

   ```text
   Amplía el análisis del hallazgo "[nombre del hallazgo]".
   ¿En qué fechas específicas se registró y en qué áreas?
   ¿Qué norma o estándar podría estar siendo incumplido?
   ```

7. Copie la tabla generada por Copilot y péguela en la sección **"Análisis de Hallazgos Recurrentes"** de la plantilla `Plantilla_Reporte_Integral_EHS.docx`. Use `Ctrl+V` para pegar con formato, o `Ctrl+Shift+V` para pegar como texto sin formato si el formato original interfiere con la plantilla.

**Resultado Esperado:** Una tabla estructurada con al menos 6–8 hallazgos recurrentes clasificados por tipo (acto inseguro / condición insegura), nivel de riesgo, frecuencia de aparición y tendencia en el período de 6 meses.

**Verificación:** Confirme que la tabla incluye columnas de: Tipo de Hallazgo, Descripción, Área/Zona, Frecuencia, Nivel de Riesgo y Tendencia. Si faltan columnas, solicite a Copilot que regenere la tabla con el formato completo.

---

#### Paso 1.3: Análisis de Patrones Ocultos con Copilot

**Objetivo:** Identificar patrones de riesgo que no son evidentes al analizar cada fuente individualmente, sino que emergen al cruzar información de múltiples documentos.

**Instrucciones:**

1. Con los mismos archivos adjuntos en el panel de Copilot, ingrese el siguiente prompt:

   ```text
   Basándote en el análisis anterior de los registros de auditorías y
   reportes de rondines, identifica PATRONES DE RIESGO CRUZADOS que no
   serían evidentes al analizar cada documento por separado. Por ejemplo:

   - ¿Existe correlación entre los días/turnos con más hallazgos en auditorías
     y los horarios con más incidentes en rondines?
   - ¿Hay zonas donde tanto las auditorías como los rondines reportan problemas
     simultáneos y persistentes?
   - ¿Se identifican secuencias de eventos que podrían indicar un riesgo
     sistémico (por ejemplo: falla de iluminación → acceso no autorizado →
     incidente patrimonial)?

   Presenta tus hallazgos como una lista de "Patrones de Riesgo Identificados"
   con una breve explicación de la evidencia que sustenta cada patrón.
   ```

2. Revise la respuesta y seleccione los 3 patrones más relevantes para la organización ficticia del escenario.

3. Copie estos patrones y agréguelos en la sección **"Patrones de Riesgo Cruzados"** de la plantilla.

**Resultado Esperado:** Al menos 3 patrones de riesgo cruzados identificados con evidencia sustentada en múltiples fuentes.

**Verificación:** Cada patrón debe referenciar al menos dos fuentes de datos distintas (auditoría + rondín, o rondín + bitácora) para validar el cruce de información.

---

### BLOQUE 2 — Análisis de Registros Técnicos para Prevención (25 minutos)

#### Paso 2.1: Análisis de Observaciones de Cámaras CCTV con Copilot

**Objetivo:** Utilizar Copilot para extraer información preventiva de las descripciones textuales de registros de video de cámaras de seguridad.

**Instrucciones:**

1. En el panel de Copilot del documento `Plantilla_Reporte_Integral_EHS.docx`, elimine los archivos adjuntos anteriores y adjunte únicamente:
   - `Registros_CCTV_Observaciones.docx`

2. Ingrese el siguiente prompt estructurado:

   ```text
   Eres un analista de seguridad patrimonial especializado en interpretación
   de registros de videovigilancia y prevención de riesgos.

   Analiza las descripciones textuales de los registros de cámaras CCTV
   del documento adjunto y realiza lo siguiente:

   1. Identifica todos los COMPORTAMIENTOS DE RIESGO observados
      (accesos no autorizados, merodeo, manipulación de equipos sin
      autorización, permanencia en zonas restringidas, etc.).
   2. Identifica las CONDICIONES DEL ENTORNO que representan riesgo
      patrimonial (puntos ciegos de cámara, fallas de iluminación,
      barreras físicas comprometidas, etc.).
   3. Clasifica cada hallazgo por NIVEL DE AMENAZA: CRÍTICO, ALTO,
      MEDIO o BAJO.
   4. Señala los HORARIOS Y DÍAS con mayor concentración de eventos
      de riesgo.
   5. Identifica las CÁMARAS O ZONAS DE COBERTURA con mayor frecuencia
      de eventos, sugiriendo si requieren refuerzo de vigilancia.

   Presenta los resultados en dos secciones: (A) Tabla de Comportamientos
   de Riesgo y (B) Tabla de Condiciones del Entorno.
   ```

3. Revise la respuesta. Si Copilot identifica algún evento ambiguo, use este prompt de seguimiento:

   ```text
   Para el evento registrado en [cámara/zona/fecha], ¿qué tipo de
   incidente patrimonial podría estar anticipando este comportamiento?
   ¿Qué medida preventiva inmediata recomendarías?
   ```

4. Copie ambas tablas generadas y agréguelas en la sección **"Análisis de Registros de Videovigilancia"** de la plantilla.

**Resultado Esperado:** Dos tablas estructuradas: una de comportamientos de riesgo y otra de condiciones del entorno, con clasificación por nivel de amenaza y horarios de mayor concentración.

**Verificación:** Confirme que la tabla de comportamientos incluye al menos una referencia a horarios críticos y que la tabla de condiciones del entorno menciona al menos una recomendación de mejora de cobertura.

---

#### Paso 2.2: Análisis de Bitácora de Incidentes en Excel con Copilot

**Objetivo:** Utilizar Copilot en Excel para analizar la bitácora de incidentes patrimoniales e identificar tendencias estadísticas y patrones temporales.

**Instrucciones:**

1. Cambie a la pestaña del archivo `Bitacora_Incidentes_Patrimonial.xlsx` en Excel Online.

2. Haga clic en el botón **Copilot** en la cinta de opciones de Excel (debe aparecer en la pestaña Inicio o en una pestaña dedicada).

3. En el panel de Copilot de Excel, ingrese el siguiente prompt:

   ```text
   Analiza los datos de esta bitácora de incidentes patrimoniales y
   proporciona lo siguiente:

   1. ¿Cuántos incidentes se registraron por mes? Muestra la tendencia
      en los últimos 6 meses (¿aumentando, disminuyendo o estable?).
   2. ¿Cuáles son los 3 tipos de incidente más frecuentes?
   3. ¿Qué áreas o zonas concentran el mayor número de incidentes?
   4. ¿Existe algún patrón por día de la semana o turno horario?
   5. ¿Cuántos incidentes tienen estado "Abierto" o "Pendiente"
      (sin resolución)?
   6. Genera un resumen ejecutivo de 3-4 oraciones con los hallazgos
      más importantes.
   ```

4. Revise la respuesta. Si Copilot ofrece crear una tabla dinámica o un gráfico, acéptelo haciendo clic en **"Insertar en hoja"** o **"Crear gráfico"** según corresponda.

5. Solicite a Copilot que genere una visualización adicional con el siguiente prompt:

   ```text
   Crea una tabla que muestre la distribución de incidentes por área
   y por nivel de severidad. Incluye totales por fila y columna.
   ```

6. Tome una captura de pantalla de la tabla generada en Excel (use `Windows + Shift + S` para captura de área).

7. Regrese al documento `Plantilla_Reporte_Integral_EHS.docx` y pegue la captura de pantalla en la sección **"Análisis Estadístico de Incidentes"** de la plantilla. Añada debajo el resumen ejecutivo generado por Copilot en Excel.

**Resultado Esperado:** Una tabla de distribución de incidentes por área y severidad, más un resumen ejecutivo de 3–4 oraciones con los hallazgos estadísticos más importantes.

**Verificación:** El resumen ejecutivo debe mencionar explícitamente: tendencia mensual, tipo de incidente más frecuente y área con mayor concentración de eventos.

---

#### Paso 2.3: Síntesis Multi-Fuente — Identificación de Tendencias Predictivas

**Objetivo:** Integrar los hallazgos de las tres fuentes analizadas (auditorías+rondines, CCTV, bitácora) para formular un análisis predictivo de riesgos futuros.

**Instrucciones:**

1. Regrese al documento `Plantilla_Reporte_Integral_EHS.docx` y abra el panel de Copilot.

2. Adjunte los cuatro archivos de práctica simultáneamente:
   - `Auditorias_Seguridad_Patrimonial_6M.docx`
   - `Registros_CCTV_Observaciones.docx`
   - `Reportes_Rondines_Vigilancia.docx`
   - (Para la bitácora, copie el resumen ejecutivo generado en Excel y péguelo directamente en el prompt como texto)

3. Ingrese el siguiente prompt de análisis predictivo:

   ```text
   Eres un experto en análisis predictivo de seguridad patrimonial.
   Basándote en toda la información analizada de las siguientes fuentes:
   - Registros de auditorías de 6 meses
   - Observaciones de cámaras CCTV
   - Reportes de rondines de vigilancia
   - Resumen de bitácora de incidentes: [PEGAR AQUÍ EL RESUMEN
     EJECUTIVO GENERADO EN EL PASO 2.2]

   Realiza un ANÁLISIS PREDICTIVO DE RIESGOS que incluya:

   1. TENDENCIAS IDENTIFICADAS: ¿Qué patrones de riesgo muestran
      una trayectoria de incremento que podría materializarse en un
      incidente grave en los próximos 30-90 días si no se interviene?
   2. ESCENARIOS DE RIESGO PROBABLE: Describe 2-3 escenarios concretos
      de incidentes que podrían ocurrir basándote en los patrones
      observados (usa el formato: "Si [condición actual persiste],
      existe alta probabilidad de [tipo de incidente] en [área/zona]").
   3. FACTORES AGRAVANTES: ¿Qué condiciones actuales podrían amplificar
      la materialización de estos riesgos?
   4. VENTANAS DE VULNERABILIDAD: ¿En qué horarios, días o períodos
      la organización presenta mayor exposición al riesgo patrimonial?

   Basa cada afirmación en evidencia específica de los documentos
   analizados. No hagas afirmaciones sin respaldo en los datos.
   ```

4. Revise cuidadosamente la respuesta. Recuerde que Copilot genera análisis basados en los datos proporcionados, pero **usted como profesional de EHS debe validar** que las tendencias identificadas son coherentes con el contexto del escenario.

5. Si alguna afirmación predictiva le parece infundada o genérica, use este prompt de validación:

   ```text
   La afirmación "[citar la afirmación]" parece genérica.
   ¿Puedes citar evidencia específica de los documentos analizados
   que respalde esta predicción? Si no hay evidencia suficiente,
   indícalo claramente.
   ```

6. Copie el análisis predictivo validado y péguelo en la sección **"Análisis Predictivo de Riesgos"** de la plantilla.

**Resultado Esperado:** Un análisis predictivo estructurado con tendencias identificadas, 2–3 escenarios de riesgo probable, factores agravantes y ventanas de vulnerabilidad, todos respaldados en evidencia de los documentos analizados.

**Verificación:** Cada escenario de riesgo debe seguir el formato condicional ("Si [condición] persiste, existe probabilidad de [incidente] en [área]") y debe citar al menos una fuente de evidencia específica.

---

### BLOQUE 3 — Generación del Reporte Integral de Hallazgos (35 minutos)

#### Paso 3.1: Estructuración del Reporte con Copilot en Word

**Objetivo:** Utilizar Copilot en Word para estructurar y completar las secciones del reporte integral de hallazgos a partir de todo el análisis previo.

**Instrucciones:**

1. Asegúrese de estar trabajando en el archivo `Plantilla_Reporte_Integral_EHS.docx` en Word Online (o Word de escritorio con el archivo guardado en SharePoint).

2. Verifique que las secciones anteriores ya contienen el contenido pegado en los Bloques 1 y 2:
   - Análisis de Hallazgos Recurrentes (Paso 1.2)
   - Patrones de Riesgo Cruzados (Paso 1.3)
   - Análisis de Registros de Videovigilancia (Paso 2.1)
   - Análisis Estadístico de Incidentes (Paso 2.2)
   - Análisis Predictivo de Riesgos (Paso 2.3)

3. Abra el panel de Copilot y adjunte los cuatro archivos de práctica nuevamente.

4. Ingrese el siguiente prompt para generar el **Resumen Ejecutivo** del reporte:

   ```text
   Eres un consultor senior de seguridad patrimonial redactando un
   reporte ejecutivo para la Dirección General de una empresa de
   manufactura mediana.

   Basándote en los documentos adjuntos y en el análisis realizado
   (que incluye hallazgos de auditorías, observaciones CCTV, rondines
   y bitácora de incidentes de los últimos 6 meses), redacta un
   RESUMEN EJECUTIVO para el reporte integral de seguridad patrimonial
   que incluya:

   - Contexto del período analizado (2-3 oraciones)
   - Principales hallazgos críticos (máximo 4 puntos clave)
   - Nivel de riesgo general actual de la organización
     (CRÍTICO / ALTO / MEDIO / BAJO) con justificación breve
   - Urgencia de intervención y consecuencias de no actuar
   - Llamada a la acción para la Dirección (1-2 oraciones)

   Tono: Profesional, directo y orientado a la toma de decisiones.
   Extensión: Máximo 300 palabras.
   Usa datos específicos del análisis para respaldar cada punto.
   ```

5. Revise el resumen ejecutivo generado. Si necesita ajustar el tono o agregar información específica, use:

   ```text
   Ajusta el resumen ejecutivo para incluir [información específica]
   y asegúrate de que el nivel de urgencia quede claramente comunicado
   sin ser alarmista.
   ```

6. Copie el resumen ejecutivo aprobado y péguelo en la sección **"Resumen Ejecutivo"** al inicio de la plantilla.

**Resultado Esperado:** Un resumen ejecutivo de máximo 300 palabras, con tono profesional y orientado a la toma de decisiones, que incluya nivel de riesgo general y llamada a la acción.

**Verificación:** El resumen debe mencionar al menos 3 hallazgos específicos del análisis (no genéricos) y debe incluir un nivel de riesgo general claramente definido.

---

#### Paso 3.2: Construcción del Mapa de Riesgos Identificados

**Objetivo:** Generar con Copilot una representación estructurada del mapa de riesgos que consolide todos los hallazgos del análisis.

**Instrucciones:**

1. En el panel de Copilot (con los archivos adjuntos), ingrese el siguiente prompt:

   ```text
   Basándote en todos los hallazgos identificados durante el análisis
   (auditorías, CCTV, rondines y bitácora de incidentes), genera un
   MAPA DE RIESGOS en formato de tabla con las siguientes columnas:

   | ID | Riesgo Identificado | Fuente de Evidencia | Área/Zona Afectada |
   Probabilidad (Alta/Media/Baja) | Impacto (Alto/Medio/Bajo) |
   Nivel de Riesgo Combinado | Tipo (Patrimonial/EHS/Operativo) |

   Para el "Nivel de Riesgo Combinado" usa la siguiente matriz:
   - Probabilidad Alta + Impacto Alto = CRÍTICO
   - Probabilidad Alta + Impacto Medio = ALTO
   - Probabilidad Media + Impacto Alto = ALTO
   - Probabilidad Media + Impacto Medio = MEDIO
   - Cualquier combinación con Baja = BAJO

   Incluye mínimo 8 riesgos identificados. Ordena la tabla de mayor
   a menor nivel de riesgo combinado.
   ```

2. Revise la tabla generada. Asegúrese de que los riesgos listados corresponden a hallazgos reales de los documentos analizados, no a riesgos genéricos inventados por Copilot.

3. Si detecta riesgos que no tienen respaldo en los documentos, elimínelos manualmente de la tabla y solicite a Copilot que los reemplace:

   ```text
   El riesgo "[nombre del riesgo]" no tiene evidencia en los documentos
   analizados. Reemplázalo por un riesgo que sí esté documentado en
   los registros de auditoría o CCTV.
   ```

4. Copie la tabla del mapa de riesgos y péguelo en la sección **"Mapa de Riesgos Identificados"** de la plantilla.

**Resultado Esperado:** Una tabla de mapa de riesgos con mínimo 8 entradas, ordenadas por nivel de riesgo combinado, con evidencia referenciada para cada riesgo.

**Verificación:** Confirme que la tabla tiene al menos 2 riesgos clasificados como CRÍTICO, que cada riesgo cita su fuente de evidencia, y que la tabla está ordenada correctamente de mayor a menor riesgo.

---

#### Paso 3.3: Redacción de Hallazgos Críticos con Evidencia

**Objetivo:** Desarrollar la sección de hallazgos críticos del reporte con narrativa técnica detallada y evidencia sustentada.

**Instrucciones:**

1. Identifique los **3 hallazgos más críticos** de su mapa de riesgos (los de nivel CRÍTICO o ALTO más alto).

2. Para cada uno de los 3 hallazgos, ingrese el siguiente prompt en Copilot (repita el proceso tres veces, uno por hallazgo):

   ```text
   Redacta la sección de "Hallazgo Crítico" para el siguiente riesgo
   identificado en el análisis de seguridad patrimonial:

   Riesgo: [NOMBRE DEL HALLAZGO CRÍTICO]
   Nivel: [CRÍTICO / ALTO]
   Área: [ÁREA O ZONA AFECTADA]

   La sección debe incluir:
   1. DESCRIPCIÓN DEL HALLAZGO: Qué se observó, dónde y cuándo
      (basado en los documentos analizados).
   2. EVIDENCIA DOCUMENTADA: Cita las fuentes específicas que
      respaldan este hallazgo (auditoría del [mes], registro CCTV
      del [fecha], etc.).
   3. ANÁLISIS DE CAUSA RAÍZ PROBABLE: ¿Por qué existe este riesgo?
      (falla de proceso, falta de recursos, comportamiento humano, etc.)
   4. CONSECUENCIAS POTENCIALES: ¿Qué podría ocurrir si no se corrige?
   5. NORMA O ESTÁNDAR APLICABLE: Indica la normativa relevante
      (NOM-STPS, ISO 45001, etc.).

   Extensión: 150-200 palabras por hallazgo. Tono técnico-profesional.
   ```

3. Revise y valide cada sección generada. Recuerde que como profesional de EHS, usted es responsable de la precisión del contenido antes de incluirlo en un reporte oficial.

4. Copie las tres secciones de hallazgos críticos y péguelas en la sección **"Hallazgos Críticos con Evidencia"** de la plantilla.

**Resultado Esperado:** Tres secciones de hallazgos críticos, cada una con descripción, evidencia, causa raíz, consecuencias y norma aplicable, con extensión de 150–200 palabras.

**Verificación:** Cada hallazgo debe citar al menos dos fuentes de evidencia distintas y debe referenciar una norma o estándar específico (no genérico).

---

#### Paso 3.4: Generación del Plan de Acción Preventivo

**Objetivo:** Crear el plan de acción preventivo que cierre el reporte integral con acciones concretas, responsables y fechas.

**Instrucciones:**

1. En el panel de Copilot (con archivos adjuntos), ingrese el siguiente prompt:

   ```text
   Eres el responsable de seguridad patrimonial de una empresa de
   manufactura. Basándote en todos los hallazgos críticos y el análisis
   predictivo de riesgos identificados, genera un PLAN DE ACCIÓN
   PREVENTIVO estructurado en la siguiente tabla:

   | # | Acción Preventiva | Hallazgo que Atiende | Tipo de Acción
   (Inmediata/Corto Plazo/Mediano Plazo) | Responsable Sugerido |
   Plazo de Implementación | Recursos Requeridos | Indicador de Éxito |

   Criterios para la clasificación de plazos:
   - INMEDIATA: Debe ejecutarse en las próximas 24-72 horas
   - CORTO PLAZO: 1-4 semanas
   - MEDIANO PLAZO: 1-3 meses

   Incluye mínimo 10 acciones preventivas. Prioriza las acciones
   inmediatas para los hallazgos de nivel CRÍTICO. Asegúrate de que
   cada acción sea específica, medible y asignable a un rol
   organizacional (no a personas con nombre real).

   Agrega al final una nota sobre los indicadores clave de desempeño
   (KPIs) que deberían monitorearse mensualmente para verificar la
   efectividad del plan.
   ```

2. Revise el plan de acción generado. Asegúrese de que:
   - Las acciones inmediatas corresponden a los hallazgos CRÍTICOS identificados.
   - Los responsables son roles organizacionales (Jefe de Seguridad, Supervisor de Turno, Gerente de Planta), **no nombres reales de personas**.
   - Los plazos son realistas para el tipo de acción propuesta.

3. Si necesita ajustar alguna acción, use:

   ```text
   La acción #[número] necesita ser más específica. ¿Puedes detallar
   exactamente qué debe hacerse, quién lo ejecuta y cómo se verifica
   que se completó?
   ```

4. Copie el plan de acción y péguelo en la sección **"Plan de Acción Preventivo"** de la plantilla.

5. Después de pegar el plan, agregue manualmente debajo una nota con el siguiente texto (adáptelo al contexto del escenario):

   ```
   NOTA DE VALIDACIÓN: Este plan de acción fue generado con asistencia
   de Microsoft 365 Copilot y ha sido revisado y validado por el
   responsable de EHS. Todos los datos utilizados en el análisis son
   ficticios y de uso exclusivo para esta práctica de laboratorio.
   Fecha de generación: [FECHA ACTUAL]
   ```

**Resultado Esperado:** Una tabla de plan de acción con mínimo 10 acciones preventivas, clasificadas por tipo y plazo, con responsables por rol y KPIs de seguimiento.

**Verificación:** Confirme que hay al menos 3 acciones clasificadas como INMEDIATA para hallazgos CRÍTICOS, y que todos los responsables son roles organizacionales (no nombres personales).

---

#### Paso 3.5: Revisión Final y Formato del Reporte con Copilot

**Objetivo:** Utilizar Copilot para revisar la coherencia, consistencia y calidad profesional del reporte completo antes de su entrega.

**Instrucciones:**

1. Desplácese al inicio del documento `Plantilla_Reporte_Integral_EHS.docx` para verificar que todas las secciones están completas:
   - [ ] Resumen Ejecutivo
   - [ ] Análisis de Hallazgos Recurrentes
   - [ ] Patrones de Riesgo Cruzados
   - [ ] Análisis de Registros de Videovigilancia
   - [ ] Análisis Estadístico de Incidentes
   - [ ] Análisis Predictivo de Riesgos
   - [ ] Mapa de Riesgos Identificados
   - [ ] Hallazgos Críticos con Evidencia (3 hallazgos)
   - [ ] Plan de Acción Preventivo
   - [ ] Nota de Validación

2. En el panel de Copilot, ingrese el siguiente prompt de revisión:

   ```text
   Revisa el documento completo y realiza lo siguiente:

   1. Identifica cualquier INCONSISTENCIA entre secciones (por ejemplo,
      si un hallazgo se menciona con diferente nivel de riesgo en
      distintas secciones del reporte).
   2. Verifica que el TONO sea uniforme y profesional en todo el documento.
   3. Señala si alguna sección está INCOMPLETA o le falta información
      relevante según los estándares de un reporte de seguridad patrimonial.
   4. Sugiere 2-3 mejoras específicas de redacción o estructura que
      elevarían la calidad profesional del reporte.

   Presenta tus observaciones como una lista numerada de comentarios
   de revisión.
   ```

3. Implemente las mejoras sugeridas por Copilot que considere pertinentes. No está obligado a aceptar todas las sugerencias; use su criterio profesional.

4. Guarde el documento (el guardado es automático en SharePoint/OneDrive, pero puede usar `Ctrl+S` para forzar el guardado).

5. Verifique que el documento está guardado correctamente en SharePoint comprobando que el ícono de guardado no muestra un indicador de cambios pendientes.

**Resultado Esperado:** Un reporte integral de hallazgos completo, coherente y con formato profesional, guardado correctamente en SharePoint.

**Verificación:** Todas las secciones de la lista de verificación del paso 1 deben estar marcadas como completas. El documento debe tener un mínimo de 8–10 páginas de contenido sustantivo.

---

## Validación y Pruebas

Al finalizar el laboratorio, el participante debe poder demostrar lo siguiente:

### Lista de Verificación de Entregables

| # | Criterio de Validación                                                                          | Estado |
|---|------------------------------------------------------------------------------------------------|--------|
| 1 | El reporte integral está guardado en SharePoint (no en disco local)                            | ☐      |
| 2 | El Resumen Ejecutivo menciona nivel de riesgo general y al menos 3 hallazgos específicos       | ☐      |
| 3 | La tabla de Hallazgos Recurrentes incluye tendencia temporal (6 meses)                         | ☐      |
| 4 | Se identificaron al menos 3 Patrones de Riesgo Cruzados con evidencia multi-fuente             | ☐      |
| 5 | El análisis de CCTV incluye tabla de comportamientos Y tabla de condiciones del entorno        | ☐      |
| 6 | El Análisis Estadístico de Excel incluye distribución por área y severidad                     | ☐      |
| 7 | El Análisis Predictivo incluye al menos 2 escenarios con formato condicional y evidencia       | ☐      |
| 8 | El Mapa de Riesgos tiene mínimo 8 entradas ordenadas por nivel de riesgo combinado             | ☐      |
| 9 | Los 3 Hallazgos Críticos incluyen causa raíz, evidencia y norma aplicable                     | ☐      |
| 10| El Plan de Acción tiene mínimo 10 acciones con responsables por rol (no nombres personales)   | ☐      |
| 11| La Nota de Validación está incluida al final del plan de acción                               | ☐      |
| 12| El documento fue revisado con Copilot para consistencia y coherencia (Paso 3.5)               | ☐      |

### Prueba de Calidad del Análisis Predictivo

Para validar la calidad del análisis predictivo generado, responda las siguientes preguntas sin consultar el reporte:

1. ¿Cuál es el área o zona de mayor riesgo identificada en el análisis multi-fuente?
2. ¿En qué horario o turno se concentra la mayor vulnerabilidad patrimonial?
3. ¿Cuál es el escenario de riesgo más probable en los próximos 30–90 días según el análisis predictivo?
4. ¿Cuáles son las 3 acciones inmediatas más urgentes del plan de acción?

Si puede responder estas preguntas con datos específicos del análisis (no respuestas genéricas), el laboratorio ha sido completado satisfactoriamente.

---

## Solución de Problemas

### Problema 1: Copilot no puede adjuntar o referenciar los archivos de SharePoint

**Síntoma:** Al intentar adjuntar archivos en el panel de Copilot dentro de Word, el botón de clip no aparece, o al hacer clic en él no muestra los archivos de SharePoint disponibles. Copilot responde que no puede acceder al documento referenciado.

**Causa:** Este problema ocurre típicamente por una de tres razones: (a) el archivo está abierto en modo de solo lectura o no está sincronizado correctamente con SharePoint; (b) la versión de Microsoft 365 Apps no está en el canal actual y no tiene la función de referenciación multi-documento habilitada; o (c) la sesión de autenticación de Microsoft 365 ha expirado y Copilot no tiene permisos para acceder a los archivos en la nube.

**Solución:**
```
Paso 1: Cierre y vuelva a abrir el archivo desde SharePoint
        (no desde la copia local en caché).
Paso 2: Verifique que el archivo está en modo de edición
        (no solo lectura): en la barra superior debe decir
        "Editando" o no debe mostrar "Vista protegida".
Paso 3: Cierre sesión en Microsoft 365 y vuelva a iniciarla:
        Archivo > Cuenta > Cerrar sesión > Iniciar sesión.
Paso 4: Si la función de adjuntar no está disponible, use el
        método alternativo: copie el contenido relevante del
        documento fuente (máximo 3,000 palabras) y péguelo
        directamente en el prompt de Copilot como texto,
        indicando: "El siguiente texto proviene del archivo
        [nombre del archivo]: [TEXTO COPIADO]"
Paso 5: Si el problema persiste, contacte al instructor para
        obtener el archivo de checkpoint con el análisis
        pre-cargado y continúe desde el Bloque 3.
```

---

### Problema 2: Copilot genera hallazgos genéricos o inventados que no corresponden a los documentos analizados

**Síntoma:** Las tablas o análisis generados por Copilot incluyen riesgos, normas o eventos que no aparecen en los archivos de práctica. Las respuestas parecen ser relleno genérico de seguridad industrial en lugar de análisis específico de los documentos proporcionados.

**Causa:** Copilot puede "alucinar" (generar contenido plausible pero no fundamentado en los documentos) cuando los prompts son demasiado amplios, cuando los documentos adjuntos son muy extensos y el modelo no los procesa completamente, o cuando el prompt no especifica explícitamente que las respuestas deben basarse exclusivamente en la información proporcionada.

**Solución:**
```
Paso 1: Agregue al inicio de su prompt la instrucción explícita:
        "Basa tu respuesta EXCLUSIVAMENTE en la información
        contenida en los documentos adjuntos. Si no encuentras
        evidencia para algún punto, indícalo claramente con
        'Sin evidencia en los documentos disponibles'."

Paso 2: Si el documento es muy extenso, divida el análisis:
        analice primero los primeros 3 meses de auditorías,
        luego los últimos 3 meses, y finalmente solicite a
        Copilot que consolide ambos análisis.

Paso 3: Para validar si un hallazgo es real o inventado,
        use el prompt: "¿En qué parte específica del documento
        [nombre] aparece la evidencia para el hallazgo
        '[descripción]'? Cita el párrafo o sección exacta."

Paso 4: Si Copilot no puede citar evidencia específica,
        elimine ese hallazgo del análisis y reemplácelo
        manualmente con un hallazgo que sí esté documentado.

Nota: Este problema ilustra una limitación real de la IA
      generativa que los profesionales de EHS deben conocer:
      la validación humana es siempre indispensable antes
      de incluir análisis de Copilot en reportes oficiales.
```

---

## Limpieza del Entorno

Al finalizar el laboratorio, realice las siguientes acciones de cierre:

1. **Guardar el reporte final:**
   ```
   Confirme que Plantilla_Reporte_Integral_EHS.docx está guardado
   en SharePoint (el indicador de guardado en la barra superior
   no debe mostrar cambios pendientes).
   Renombre el archivo como: Reporte_Integral_[SusIniciales]_[Fecha].docx
   Ejemplo: Reporte_Integral_JGM_2024-11-15.docx
   ```

2. **Limpiar el historial de Copilot (opcional, según política de la organización):**
   ```
   En el panel de Copilot, haga clic en los tres puntos (...)
   y seleccione "Nueva conversación" para limpiar el contexto
   de la sesión actual.
   ```

3. **Cerrar archivos de práctica:**
   ```
   Cierre las pestañas de los archivos de práctica en el navegador:
   - Auditorias_Seguridad_Patrimonial_6M.docx
   - Bitacora_Incidentes_Patrimonial.xlsx
   - Registros_CCTV_Observaciones.docx
   - Reportes_Rondines_Vigilancia.docx
   NO elimine estos archivos — son compartidos con todos los
   participantes del curso.
   ```

4. **Verificar que no se usaron datos reales:**
   ```
   Confirme que durante toda la práctica utilizó exclusivamente
   los datos ficticios de los archivos de práctica.
   Si por error ingresó información personal real o datos
   confidenciales en algún prompt de Copilot, notifique
   inmediatamente al instructor.
   ```

5. **Compartir el reporte con el instructor (si se requiere):**
   ```
   En SharePoint, haga clic en "Compartir" en su archivo
   Reporte_Integral_[SusIniciales]_[Fecha].docx y compártalo
   con el correo del instructor con permisos de "Solo lectura".
   ```

---

## Resumen

### Lo que Aprendió en Este Laboratorio

Este taller de consolidación integró las competencias desarrolladas a lo largo del Módulo 4 en un flujo de trabajo completo de análisis de seguridad patrimonial. Los puntos clave que debe llevarse son:

1. **La referenciación multi-documento en Copilot es una capacidad diferenciadora:** Al analizar simultáneamente auditorías, registros de CCTV y reportes de rondines, Copilot puede identificar patrones cruzados que serían invisibles al analizar cada fuente de forma aislada. Esta capacidad transforma el análisis de seguridad de reactivo a predictivo.

2. **La calidad del prompt determina la calidad del análisis:** Los prompts con definición de rol, instrucciones numeradas, criterios de clasificación explícitos y solicitud de evidencia producen resultados accionables. Los prompts vagos producen respuestas genéricas.

3. **La validación humana es indispensable:** Copilot puede alucinar o generar contenido plausible pero no fundamentado. El profesional de EHS debe siempre verificar que los hallazgos generados corresponden a evidencia real en los documentos antes de incluirlos en reportes oficiales.

4. **El análisis predictivo cualitativo asistido por IA tiene valor real:** Al estructurar correctamente la síntesis multi-fuente, Copilot puede identificar tendencias de incremento, ventanas de vulnerabilidad y escenarios de riesgo probable que fundamentan decisiones preventivas antes de que ocurra un incidente.

5. **El reporte integral como activo organizacional:** Un reporte bien estructurado —con resumen ejecutivo, mapa de riesgos, hallazgos con evidencia y plan de acción con KPIs— no es solo un documento de auditoría; es un activo preventivo que puede orientar inversiones en seguridad, fundamentar decisiones gerenciales y demostrar cumplimiento normativo.

### Recursos Adicionales

| Recurso | Descripción | URL |
|---------|-------------|-----|
| Microsoft Copilot para M365 — Documentación oficial | Guía completa de uso de Copilot en aplicaciones de Microsoft 365 | https://learn.microsoft.com/es-es/copilot/microsoft-365/ |
| ISO 45001:2018 — Resumen oficial | Sistema de Gestión de la Seguridad y Salud en el Trabajo | https://www.iso.org/iso-45001-occupational-health-and-safety.html |
| NOM-030-STPS-2009 | Servicios Preventivos de Seguridad y Salud en el Trabajo | https://www.dof.gob.mx/nota_detalle.php?codigo=5120760 |
| OSHA — Hazard Identification | Guía de identificación y evaluación de peligros | https://www.osha.gov/safety-management/hazard-identification |
| INSST — Auditoría del Sistema de Prevención | Guía práctica de auditorías de seguridad industrial | https://www.insst.es/materias/gestion-de-la-prevencion/auditoria-del-sistema-de-prevencion-de-riesgos-laborales |

### Próximos Pasos

Con la finalización de este laboratorio, ha completado el bloque analítico del curso (Módulos 1–4). En el **Módulo 5** comenzará a construir agentes de IA especializados en seguridad industrial utilizando **Microsoft Copilot Studio**. Asegúrese de que el administrador de TI haya habilitado su acceso al entorno de Power Platform con el rol de **Environment Maker** antes de la siguiente sesión, ya que este proceso puede tomar hasta 24 horas en algunos entornos corporativos.

---

> 📋 **Nota Final del Instructor:** Este laboratorio tiene una progresión acumulativa interna (Bloques 1 → 2 → 3). Si un participante no puede completar el Bloque 2 por limitaciones de tiempo, proporcione el archivo de checkpoint `Checkpoint_Bloque2_Completado.docx` de la carpeta de recursos del instructor en SharePoint para que pueda continuar con el Bloque 3 (Generación del Reporte Integral). El objetivo mínimo del laboratorio es que todos los participantes completen al menos el Paso 3.4 (Plan de Acción Preventivo).
