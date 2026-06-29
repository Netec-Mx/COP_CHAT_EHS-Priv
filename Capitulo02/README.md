# Comunicación Ejecutiva en EHS — Conclusiones, Action Titles y Presentaciones con Copilot

## Metadatos del Laboratorio

| Atributo | Detalle |
|---|---|
| **Duración estimada** | 60 minutos |
| **Complejidad** | Media |
| **Nivel Bloom** | Aplicar (Apply) |
| **Módulo** | Módulo 2 — Interpretación Normativa y Comunicación Ejecutiva EHS |
| **Práctica** | 2 de 2 del Módulo 2 |
| **Modalidad** | Individual con revisión grupal al final |

---

## Descripción General

En este laboratorio los participantes elevarán la calidad de su comunicación ejecutiva en contextos de EHS aplicando directamente las capacidades de Microsoft 365 Copilot. Partiendo de datos brutos de una auditoría ambiental y de seguridad industrial ficticia, los participantes usarán Copilot en Word para sintetizar normas (ISO 14001, ISO 45001 y NOMs aplicables), redactar conclusiones estructuradas bajo el esquema **Hallazgo → Impacto → Recomendación**, generar *action titles* estratégicos y, finalmente, construir una presentación ejecutiva de 8 a 10 diapositivas en PowerPoint con Copilot. El laboratorio pone en práctica los principios de prompts estructurados (contexto, documento de referencia, acción, formato de salida) aprendidos en la Lección 2.1.

---

## Objetivos de Aprendizaje

Al completar este laboratorio, el participante será capaz de:

- [ ] Usar Copilot en Word para interpretar extractos de normas ambientales y de seguridad (ISO 14001, ISO 45001, NOMs) y generar resúmenes ejecutivos con obligaciones críticas de cumplimiento.
- [ ] Redactar conclusiones ejecutivas basadas en evidencia para reportes de EHS aplicando la estructura **Hallazgo + Impacto + Recomendación** con asistencia de Copilot.
- [ ] Crear *action titles* estratégicos que comuniquen el mensaje principal de cada sección de un reporte, diferenciándolos de títulos descriptivos genéricos.
- [ ] Estructurar una presentación ejecutiva de 8–10 diapositivas en PowerPoint usando Copilot que sintetice hallazgos críticos de una auditoría ambiental y de seguridad industrial de forma profesional.
- [ ] Aplicar principios de uso responsable de IA generativa, utilizando exclusivamente datos ficticios y validando los resultados generados antes de considerarlos definitivos.

---

## Prerrequisitos

### Conocimientos Previos

| Conocimiento | Nivel requerido |
|---|---|
| Uso básico de Copilot en Word (abrir panel, formular prompts, aceptar/rechazar sugerencias) | Básico — cubierto en Práctica 1 |
| Conceptos generales de EHS: auditoría, hallazgo, no conformidad, acción correctiva | Conceptual |
| Familiaridad con ISO 14001, ISO 45001 y NOMs a nivel de propósito y estructura | Conceptual |
| Navegación en SharePoint Online para abrir archivos | Básico |

### Accesos y Recursos Necesarios

| Recurso | Estado requerido |
|---|---|
| Licencia Microsoft 365 Copilot activa | ✅ Verificado antes del laboratorio |
| Copilot habilitado en Word y PowerPoint | ✅ Confirmado por TI |
| Acceso a la biblioteca SharePoint del curso | ✅ Confirmado por el instructor |
| Archivo `M2_DatosAuditoria_Ficticios.docx` cargado en SharePoint | ✅ Preparado por el instructor |
| Archivo `M2_ExtractosNormativos_Referencia.docx` cargado en SharePoint | ✅ Preparado por el instructor |
| Plantilla `M2_PlantillaReporteEHS.docx` cargada en SharePoint | ✅ Preparado por el instructor |

> **⚠️ Aviso de privacidad:** Durante todo el laboratorio, utiliza **exclusivamente los datos ficticios** proporcionados por el instructor. Está estrictamente prohibido ingresar datos reales de empleados, información confidencial de la empresa o datos sensibles de seguridad en los prompts de Copilot.

---

## Entorno del Laboratorio

### Configuración de Hardware Recomendada

| Componente | Mínimo requerido |
|---|---|
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 o superior |
| RAM | 8 GB (16 GB recomendado) |
| Resolución de pantalla | 1920×1080 |
| Conexión a Internet | 10 Mbps estables |
| Monitor secundario | Recomendado para comparar documentos simultáneamente |

### Software y Aplicaciones

| Aplicación | Versión / Acceso |
|---|---|
| Microsoft Word | Microsoft 365 Apps (canal actual), con Copilot habilitado |
| Microsoft PowerPoint | Microsoft 365 Apps (canal actual), con Copilot habilitado |
| Microsoft SharePoint Online | Acceso vía navegador: `https://[tuorganizacion].sharepoint.com` |
| Microsoft Edge | Versión estable más reciente (Chromium) |

### Preparación del Entorno — Pasos Previos al Laboratorio

Antes de iniciar los pasos del laboratorio, completa esta configuración:

**1. Verificar que Copilot está activo en Word:**
```
Abre Microsoft Word → Revisa que el botón "Copilot" aparezca 
en la cinta de opciones (pestaña "Inicio" o "Copilot").
Si no aparece: Archivo → Cuenta → Verificar licencia de Microsoft 365 Copilot.
```

**2. Acceder a los archivos de práctica en SharePoint:**
```
1. Abre Microsoft Edge.
2. Navega a: https://[tuorganizacion].sharepoint.com/sites/CursoEHS-Copilot
3. Ve a la biblioteca: "Documentos > Módulo 2 > Archivos de Práctica"
4. Confirma que existen los tres archivos:
   - M2_DatosAuditoria_Ficticios.docx
   - M2_ExtractosNormativos_Referencia.docx
   - M2_PlantillaReporteEHS.docx
5. Abre cada archivo en Word Online para confirmar acceso.
```

**3. Abrir los archivos en Word de escritorio (no en modo local):**
```
En SharePoint, selecciona el archivo → "Abrir" → "Abrir en la aplicación de escritorio"
IMPORTANTE: El archivo debe permanecer guardado en SharePoint/OneDrive.
NO descargues ni guardes una copia local; Copilot no funcionará con archivos locales.
```

---

## Pasos del Laboratorio

---

### Etapa 1 — Síntesis Normativa con Copilot en Word

**⏱ Tiempo estimado: 12 minutos**

#### Objetivo de la Etapa
Usar Copilot en Word para interpretar extractos de ISO 14001, ISO 45001 y NOMs aplicables contenidos en el archivo de referencia, y generar un resumen ejecutivo estructurado de los requisitos críticos de cumplimiento relevantes para el escenario de auditoría ficticio.

---

**Instrucciones:**

**Paso 1.1 — Abrir el archivo normativo de referencia**

1. Desde SharePoint, abre `M2_ExtractosNormativos_Referencia.docx` en Word de escritorio.
2. Revisa brevemente el contenido del documento (2–3 minutos). El archivo contiene:
   - Extracto de los requisitos de la cláusula 9.1 (Evaluación del desempeño) de **ISO 14001:2015**.
   - Extracto de los requisitos de la cláusula 9.2 (Auditoría interna) de **ISO 45001:2018**.
   - Fragmento de la **NOM-001-SEMARNAT-1996** con límites de parámetros en aguas residuales.
3. No modifiques el archivo. Solo lo usarás como referencia de contexto.

**Paso 1.2 — Abrir la plantilla de reporte y activar Copilot**

1. Abre `M2_PlantillaReporteEHS.docx` desde SharePoint en Word de escritorio.
2. Guarda una copia de trabajo con tu nombre:
   - `Archivo` → `Guardar una copia` → Guarda en la misma carpeta de SharePoint con el nombre: `M2_ReporteEHS_[TuNombre].docx`
3. Haz clic en el botón **Copilot** en la cinta de opciones para abrir el panel lateral de Copilot.

**Paso 1.3 — Formular el prompt de síntesis normativa**

En el panel de Copilot, ingresa el siguiente prompt. Adapta únicamente el nombre del sector si el instructor lo indica:

```text
Contexto: Soy el coordinador de EHS de una planta de manufactura 
metalmecánica ficticia en México llamada "Industrias Metálicas del 
Norte S.A. de C.V." (empresa ficticia para práctica).

Tarea: Con base en el documento abierto "M2_ExtractosNormativos_Referencia.docx" 
y tu conocimiento de ISO 14001:2015, ISO 45001:2018 y NOM-001-SEMARNAT-1996, 
identifica y resume los CINCO requisitos de cumplimiento más críticos 
que deben verificarse en una auditoría ambiental y de seguridad industrial 
para este tipo de operación.

Formato de salida: Tabla con columnas:
| # | Norma/Cláusula | Requisito crítico | Evidencia típica requerida | Nivel de riesgo si incumple (Alto/Medio/Bajo) |

Notas: Usa lenguaje técnico-ejecutivo. Máximo 2 líneas por requisito.
```

4. Presiona **Enter** y espera la respuesta de Copilot (15–30 segundos).

**Paso 1.4 — Insertar y ajustar el resumen normativo**

1. Revisa la tabla generada por Copilot. Verifica que los requisitos sean coherentes con el contexto EHS.
2. Si algún requisito no es relevante para una planta metalmecánica, usa el siguiente prompt de refinamiento:

```text
El requisito #[número] no aplica directamente a una planta 
metalmecánica. Reemplázalo por un requisito de ISO 45001:2018 
relacionado con control de riesgos mecánicos o gestión de 
equipos de protección personal.
```

3. Cuando estés satisfecho con la tabla, haz clic en **"Insertar"** para añadirla al documento.
4. Añade encima de la tabla el título: `1. Requisitos Críticos de Cumplimiento Normativo — Resumen Ejecutivo`
5. Guarda el documento (`Ctrl + S`).

**✅ Resultado Esperado de la Etapa 1:**
El documento `M2_ReporteEHS_[TuNombre].docx` contiene una tabla estructurada con 5 requisitos normativos críticos, con norma de referencia, descripción del requisito, evidencia requerida y nivel de riesgo. La tabla fue generada por Copilot y validada por el participante.

**🔍 Verificación:**
- [ ] La tabla tiene exactamente 5 filas de requisitos (más encabezado).
- [ ] Cada fila referencia una norma específica (ISO 14001, ISO 45001 o NOM-001).
- [ ] El nivel de riesgo está asignado en todas las filas.
- [ ] El documento está guardado en SharePoint (no localmente).

---

### Etapa 2 — Redacción de Conclusiones Ejecutivas

**⏱ Tiempo estimado: 15 minutos**

#### Objetivo de la Etapa
Transformar los datos brutos de auditoría del archivo ficticio en conclusiones ejecutivas profesionales usando la estructura **Hallazgo + Impacto + Recomendación**, con asistencia de Copilot en Word.

---

**Instrucciones:**

**Paso 2.1 — Revisar los datos brutos de auditoría**

1. Abre `M2_DatosAuditoria_Ficticios.docx` en una segunda ventana de Word (o en una pestaña del navegador si usas Word Online como referencia).
2. Lee los datos brutos. El archivo contiene notas de campo de una auditoría ficticia con los siguientes hallazgos sin estructurar:
   - Observaciones sobre el manejo de residuos peligrosos en el área de pintura.
   - Mediciones de ruido en el área de prensas que superan los límites.
   - Registros incompletos de mantenimiento de extintores.
   - Resultados de laboratorio de aguas residuales con un parámetro fuera de norma.
   - Ausencia de señalización de emergencia en dos rutas de evacuación.

**Paso 2.2 — Comprender la estructura de conclusión ejecutiva**

Antes de usar Copilot, interioriza el esquema que aplicarás. Una conclusión ejecutiva efectiva en EHS sigue este patrón:

| Elemento | Pregunta que responde | Extensión sugerida |
|---|---|---|
| **Hallazgo** | ¿Qué se encontró exactamente? | 1–2 oraciones con datos específicos |
| **Impacto** | ¿Cuál es la consecuencia real o potencial? | 1–2 oraciones con referencia normativa o de riesgo |
| **Recomendación** | ¿Qué acción concreta se debe tomar? | 1 oración con verbo de acción y plazo sugerido |

**Paso 2.3 — Generar conclusiones con Copilot**

En el panel de Copilot de tu documento `M2_ReporteEHS_[TuNombre].docx`, ingresa el siguiente prompt:

```text
Contexto: Estoy redactando el apartado de conclusiones de un reporte 
de auditoría EHS para una planta metalmecánica ficticia.

Datos brutos (del archivo M2_DatosAuditoria_Ficticios.docx):
1. En el área de pintura se encontraron 4 tambores de solvente residual 
   sin etiqueta ni hoja de datos de seguridad, almacenados junto a 
   materiales combustibles.
2. Las mediciones de ruido en el área de prensas registraron 94 dB(A) 
   de promedio, superando el límite de 85 dB(A) establecido en la 
   NOM-011-STPS-2001.
3. El 60% de los registros de mantenimiento de extintores del último 
   trimestre están incompletos o no firmados.
4. El análisis de laboratorio de aguas residuales muestra que el 
   parámetro de Sólidos Suspendidos Totales (SST) es de 280 mg/L, 
   superando el límite de 150 mg/L de la NOM-001-SEMARNAT-1996.
5. Las rutas de evacuación B y C del edificio de producción carecen 
   de señalización luminiscente según lo requerido por la NOM-003-SEGOB-2011.

Tarea: Para CADA uno de los 5 hallazgos anteriores, redacta una 
conclusión ejecutiva profesional usando estrictamente la estructura:
- HALLAZGO: [descripción precisa con dato]
- IMPACTO: [consecuencia normativa, de seguridad o ambiental]
- RECOMENDACIÓN: [acción concreta + plazo sugerido en días hábiles]

Tono: Técnico-formal, directo, sin ambigüedades.
Extensión por conclusión: máximo 6 líneas en total.
```

4. Presiona **Enter** y espera la respuesta.

**Paso 2.4 — Refinar una conclusión con prompt de seguimiento**

Elige la conclusión que consideres más débil o genérica. Usa este prompt de refinamiento:

```text
La conclusión #[número] sobre [tema] necesita más especificidad.
Por favor:
- Añade la referencia exacta al artículo o cláusula normativa aplicable.
- Fortalece el impacto mencionando la consecuencia legal o económica potencial.
- Reformula la recomendación con un verbo de acción más específico 
  (por ejemplo: "implementar", "contratar", "documentar", "capacitar").
```

**Paso 2.5 — Insertar las conclusiones en el documento**

1. Acepta e inserta las 5 conclusiones en el documento.
2. Añade el título de sección: `2. Conclusiones Ejecutivas de la Auditoría`
3. Guarda el documento (`Ctrl + S`).

**✅ Resultado Esperado de la Etapa 2:**
El documento contiene 5 conclusiones ejecutivas estructuradas bajo el esquema Hallazgo + Impacto + Recomendación, con referencias normativas específicas y acciones concretas con plazos.

**🔍 Verificación:**
- [ ] Cada conclusión tiene los tres elementos claramente diferenciados (Hallazgo, Impacto, Recomendación).
- [ ] Al menos 3 conclusiones incluyen referencia a una norma específica (NOM, ISO).
- [ ] Las recomendaciones incluyen un plazo sugerido (ej. "en un plazo de 15 días hábiles").
- [ ] El tono es técnico-formal y consistente en las 5 conclusiones.

---

### Etapa 3 — Creación de Action Titles Estratégicos

**⏱ Tiempo estimado: 10 minutos**

#### Objetivo de la Etapa
Aprender y aplicar la técnica de *action titles* (títulos de acción) para transformar encabezados descriptivos genéricos en títulos que comuniquen el mensaje principal de cada sección, usando Copilot como asistente de evaluación y generación.

---

**Instrucciones:**

**Paso 3.1 — Comprender la diferencia entre título descriptivo y action title**

Antes de usar Copilot, revisa esta comparativa conceptual:

| Tipo de título | Ejemplo | ¿Qué comunica? |
|---|---|---|
| **Descriptivo (genérico)** | "Hallazgos de Ruido Industrial" | Solo indica el tema; no dice nada sobre el resultado |
| **Action Title (estratégico)** | "El ruido en prensas supera el límite legal en 9 dB: acción correctiva urgente requerida" | Comunica el hallazgo, la magnitud y la urgencia en una sola línea |
| **Descriptivo (genérico)** | "Estado de Aguas Residuales" | Neutro, no informa sobre el resultado |
| **Action Title (estratégico)** | "SST en efluentes excede 87% el límite normativo: riesgo de sanción ambiental inmediata" | Informa el incumplimiento, la magnitud y el riesgo |

> **Regla de oro del Action Title:** Un buen título de acción puede leerse de forma aislada y transmitir el mensaje más importante de esa sección. Si el lector solo lee los títulos, debe entender la situación crítica.

**Paso 3.2 — Generar action titles con Copilot**

En el panel de Copilot de tu documento, ingresa el siguiente prompt:

```text
Tengo las siguientes secciones de un reporte ejecutivo de auditoría EHS 
para una planta metalmecánica ficticia. Los títulos actuales son descriptivos 
y no comunican el mensaje. 

Títulos descriptivos actuales:
1. "Gestión de Residuos Peligrosos"
2. "Niveles de Ruido en Área de Producción"
3. "Mantenimiento de Equipos Contra Incendio"
4. "Calidad de Aguas Residuales"
5. "Señalización de Emergencia"
6. "Resumen de Hallazgos"
7. "Acciones Correctivas Propuestas"
8. "Conclusión General"

Contexto de los hallazgos (resumido):
- Residuos: 4 tambores sin etiquetar junto a combustibles
- Ruido: 94 dB(A) vs límite de 85 dB(A) en NOM-011-STPS-2001
- Extintores: 60% de registros incompletos
- Aguas residuales: SST = 280 mg/L vs límite 150 mg/L (NOM-001)
- Señalización: 2 rutas de evacuación sin señalización requerida
- General: 5 no conformidades identificadas, 2 de nivel crítico

Tarea: Transforma CADA título descriptivo en un "action title" estratégico 
que comunique el mensaje principal de esa sección. 

Criterios para un buen action title:
- Máximo 12 palabras
- Incluye el dato o resultado más impactante cuando aplique
- Usa lenguaje activo y directo
- El lector debe entender la situación crítica solo con leer el título

Presenta el resultado en una tabla comparativa:
| # | Título descriptivo original | Action Title propuesto | Justificación (1 línea) |
```

**Paso 3.3 — Evaluar y seleccionar los mejores action titles**

1. Revisa la tabla generada por Copilot.
2. Para los títulos que consideres que pueden mejorarse, usa este prompt de refinamiento:

```text
El action title #[número] es demasiado largo / poco impactante / 
no comunica urgencia. Por favor, propón 2 alternativas adicionales 
para ese título, cada una con un enfoque diferente:
- Opción A: énfasis en el riesgo normativo/legal
- Opción B: énfasis en el impacto operativo o de seguridad
```

3. Selecciona la versión final de cada action title y crea una lista en tu documento.

**Paso 3.4 — Documentar los action titles seleccionados**

1. Inserta en el documento una nueva sección titulada: `3. Action Titles — Estructura del Reporte Ejecutivo`
2. Copia la tabla comparativa final con los 8 action titles seleccionados.
3. Guarda el documento (`Ctrl + S`).

**✅ Resultado Esperado de la Etapa 3:**
El documento contiene una tabla con 8 action titles estratégicos, comparados con sus títulos descriptivos originales, con justificación de cada elección.

**🔍 Verificación:**
- [ ] Cada action title tiene 12 palabras o menos.
- [ ] Al menos 4 de los 8 action titles incluyen un dato cuantitativo o referencia normativa específica.
- [ ] La tabla comparativa muestra claramente el contraste entre el título original y el action title.
- [ ] Los action titles de las secciones críticas (ruido, aguas residuales) comunican urgencia o riesgo.

---

### Etapa 4 — Presentación Ejecutiva con Copilot en PowerPoint

**⏱ Tiempo estimado: 18 minutos**

#### Objetivo de la Etapa
Usar Copilot en PowerPoint para crear una presentación ejecutiva de 8–10 diapositivas que sintetice los hallazgos críticos de la auditoría, aplicando los action titles y conclusiones desarrollados en las etapas anteriores.

---

**Instrucciones:**

**Paso 4.1 — Crear una nueva presentación en PowerPoint desde SharePoint**

1. Ve a la carpeta `Módulo 2 > Archivos de Práctica` en SharePoint.
2. Haz clic en `+ Nuevo` → `Presentación de PowerPoint`.
3. Cuando se abra en PowerPoint Online, haz clic en **"Abrir en la aplicación de escritorio"**.
4. Guarda la presentación con el nombre: `M2_PresentacionEjecutiva_[TuNombre].pptx` en la misma carpeta de SharePoint.

> **Nota:** Si PowerPoint de escritorio no abre el panel de Copilot automáticamente, ve a la pestaña **"Inicio"** → botón **"Copilot"**.

**Paso 4.2 — Generar la presentación con Copilot usando el documento de Word**

En el panel de Copilot de PowerPoint, ingresa el siguiente prompt:

```text
Crea una presentación ejecutiva profesional de 9 diapositivas para 
presentar los resultados de una auditoría EHS a la dirección general 
de una planta metalmecánica ficticia ("Industrias Metálicas del Norte").

Estructura de diapositivas requerida:
1. Portada: Título principal con action title de alto impacto, 
   fecha ficticia (Q4-2024), nombre del área: "Dirección de EHS"
2. Agenda / Índice: Las 8 secciones del reporte con sus action titles
3. Resumen Ejecutivo: 3 puntos clave de la auditoría (máximo 3 bullets)
4. Hallazgo Crítico #1 — Ruido Industrial: 94 dB(A) vs 85 dB(A) límite NOM-011
5. Hallazgo Crítico #2 — Aguas Residuales: SST 280 mg/L vs 150 mg/L NOM-001
6. Hallazgos de Nivel Medio: Residuos peligrosos, extintores, señalización
7. Matriz de Riesgo: Tabla con los 5 hallazgos, nivel de riesgo y prioridad
8. Plan de Acciones Correctivas: Tabla con acción, responsable ficticio, 
   plazo y norma de referencia
9. Conclusión General: 1 mensaje central impactante + próximos pasos

Requisitos de diseño:
- Tema profesional y corporativo (usa el tema "Office" o similar)
- Máximo 5 bullets por diapositiva
- Cada diapositiva debe tener un action title como encabezado (no títulos descriptivos)
- Incluir notas del presentador en cada diapositiva con el mensaje verbal clave

Tono: Ejecutivo, directo, orientado a la toma de decisiones.
Audiencia: Dirección General y Gerencia de Operaciones (no técnicos de EHS).
```

5. Presiona **Enter** y espera mientras Copilot genera la presentación (puede tomar 30–60 segundos).

**Paso 4.3 — Revisar y ajustar la presentación generada**

Una vez generada la presentación, realiza las siguientes verificaciones y ajustes:

1. **Verificar action titles:** Comprueba que los títulos de las diapositivas 3–8 coincidan (o sean consistentes) con los action titles que desarrollaste en la Etapa 3. Si hay discrepancias, actualiza manualmente los títulos de las diapositivas con tus action titles finales.

2. **Ajustar la diapositiva de Matriz de Riesgo:** Si Copilot generó una tabla, verifica que contenga los 5 hallazgos con su nivel de riesgo (Alto/Medio/Bajo). Si la tabla está incompleta, usa este prompt:

```text
La diapositiva de Matriz de Riesgo está incompleta. 
Por favor, actualiza esa diapositiva para incluir una tabla 
con los 5 hallazgos de la auditoría, con las columnas:
| Hallazgo | Norma incumplida | Nivel de riesgo | Plazo de corrección |
Usa los datos del contexto previo de la auditoría ficticia.
```

3. **Verificar las notas del presentador:** Haz clic en `Ver` → `Notas` para confirmar que cada diapositiva tiene notas con el mensaje verbal clave. Si alguna diapositiva no tiene notas, selecciónala y usa:

```text
Añade notas del presentador para la diapositiva [número] sobre 
[tema]. El mensaje verbal debe durar aproximadamente 45 segundos 
al hablar, enfocado en la urgencia de la acción correctiva 
para la audiencia ejecutiva.
```

**Paso 4.4 — Añadir consistencia visual y guardar**

1. Verifica que todas las diapositivas usen el mismo tema/plantilla visual. Si hay inconsistencias: `Diseño` → selecciona un tema corporativo uniforme.
2. Revisa que los colores de los indicadores de riesgo sean consistentes (rojo = Alto, amarillo = Medio, verde = Bajo).
3. Guarda la presentación (`Ctrl + S`).
4. Verifica que el archivo se guardó en SharePoint (no localmente): el título de la ventana debe mostrar el nombre del archivo sin el indicador de "guardado local".

**✅ Resultado Esperado de la Etapa 4:**
Una presentación ejecutiva de 9 diapositivas en PowerPoint, guardada en SharePoint, con action titles en cada diapositiva, datos cuantitativos de los hallazgos críticos, matriz de riesgo, plan de acciones correctivas y notas del presentador en cada slide.

**🔍 Verificación:**
- [ ] La presentación tiene entre 8 y 10 diapositivas.
- [ ] Los títulos de las diapositivas son action titles (no títulos descriptivos genéricos).
- [ ] La diapositiva de Matriz de Riesgo incluye los 5 hallazgos con nivel de riesgo asignado.
- [ ] La diapositiva de Plan de Acciones Correctivas incluye responsables, plazos y normas de referencia.
- [ ] Todas las diapositivas tienen notas del presentador.
- [ ] El archivo está guardado en SharePoint.

---

## Validación y Pruebas del Laboratorio

Al finalizar las 4 etapas, realiza esta validación integral:

### Lista de Verificación Final

| # | Entregable | Criterio de éxito | ✅/❌ |
|---|---|---|---|
| 1 | `M2_ReporteEHS_[TuNombre].docx` | Contiene tabla de 5 requisitos normativos críticos con norma, requisito, evidencia y nivel de riesgo | |
| 2 | `M2_ReporteEHS_[TuNombre].docx` | Contiene 5 conclusiones ejecutivas con estructura Hallazgo + Impacto + Recomendación | |
| 3 | `M2_ReporteEHS_[TuNombre].docx` | Contiene tabla comparativa de 8 action titles con justificación | |
| 4 | `M2_PresentacionEjecutiva_[TuNombre].pptx` | Presentación de 8–10 diapositivas con action titles en encabezados | |
| 5 | `M2_PresentacionEjecutiva_[TuNombre].pptx` | Diapositiva de Matriz de Riesgo con 5 hallazgos y niveles de riesgo | |
| 6 | `M2_PresentacionEjecutiva_[TuNombre].pptx` | Notas del presentador en todas las diapositivas | |
| 7 | Ambos archivos | Guardados en SharePoint (no localmente) | |
| 8 | Todos los prompts | Se usaron exclusivamente datos ficticios | |

### Prueba de Calidad Comunicativa

Realiza esta prueba rápida de efectividad de tus action titles:

1. Cierra la presentación de PowerPoint.
2. Pide a un compañero (o al instructor) que lea **únicamente los títulos** de tus 9 diapositivas sin ver el contenido.
3. Pregúntale: "¿Puedes describir la situación de la planta solo con los títulos?"
4. Si la respuesta es mayormente sí, tus action titles son efectivos.
5. Si la respuesta es no, identifica qué títulos son aún demasiado genéricos y refínalos.

### Autoevaluación con Copilot

En el panel de Copilot de Word, usa este prompt para autoevaluar la calidad de tus conclusiones:

```text
Actúa como un evaluador experto en comunicación ejecutiva de EHS.
Evalúa las siguientes 5 conclusiones ejecutivas que redacté 
[pega aquí tus 5 conclusiones] 

Criterios de evaluación:
1. ¿Cada conclusión tiene los tres elementos (Hallazgo, Impacto, Recomendación)?
2. ¿Las recomendaciones son específicas y accionables?
3. ¿El tono es apropiado para una audiencia ejecutiva?
4. ¿Hay referencias normativas específicas?

Presenta el resultado en una tabla de evaluación con puntuación 
del 1 al 5 por criterio y comentario de mejora.
```

---

## Solución de Problemas

### Problema 1: Copilot no aparece en la cinta de opciones de Word o PowerPoint

**Síntoma:** El botón "Copilot" no es visible en la pestaña "Inicio" de Word o PowerPoint, o aparece en gris (deshabilitado).

**Causa probable:** La licencia de Microsoft 365 Copilot no está activa para el usuario, Copilot no ha sido habilitado por el administrador de TI para las aplicaciones de escritorio, o la versión de las aplicaciones no está actualizada al canal actual de Microsoft 365 Apps.

**Solución:**
```
Paso 1 — Verificar licencia:
  Abre Word → Archivo → Cuenta → "Información del producto"
  Confirma que aparece "Microsoft 365 Copilot" en la lista de servicios activos.
  
Paso 2 — Verificar versión de la aplicación:
  Archivo → Cuenta → "Actualizaciones de Office" → "Actualizar ahora"
  Espera a que se instalen las actualizaciones y reinicia Word/PowerPoint.

Paso 3 — Si el botón sigue sin aparecer:
  Cierra Word/PowerPoint completamente.
  Abre el archivo directamente desde SharePoint en el navegador Edge.
  Haz clic en "Abrir en la aplicación de escritorio" nuevamente.
  
Paso 4 — Si persiste el problema:
  Contacta al administrador de TI para verificar que la política de 
  Copilot esté habilitada en el tenant de Microsoft 365.
  Como alternativa temporal, usa Copilot en Word Online (navegador) 
  desde SharePoint → el panel de Copilot está disponible en la versión web.
```

---

### Problema 2: Copilot genera contenido incorrecto, genérico o no relacionado con los datos de la auditoría ficticia

**Síntoma:** Las respuestas de Copilot son muy generales (no mencionan los datos específicos de la auditoría), repiten información de otras fuentes no relacionadas, o ignoran el contexto del sector metalmecánico indicado en el prompt.

**Causa probable:** El prompt no incluye suficiente contexto específico, Copilot no tiene acceso al documento de referencia porque no está abierto en Word al momento de la consulta, o el prompt es demasiado largo y Copilot está procesando solo parte de él.

**Solución:**
```
Paso 1 — Verificar que el archivo de referencia está abierto:
  Copilot en Word puede referenciar documentos abiertos en la misma 
  sesión. Confirma que "M2_DatosAuditoria_Ficticios.docx" está 
  abierto en una ventana de Word activa.

Paso 2 — Referenciar el documento explícitamente en el prompt:
  Añade al inicio del prompt: 
  "Basándote en los datos del documento M2_DatosAuditoria_Ficticios.docx 
  que tengo abierto, y específicamente en [menciona el hallazgo concreto]..."

Paso 3 — Dividir prompts largos:
  Si el prompt tiene más de 300 palabras, divídelo en dos prompts 
  separados: primero el contexto y los datos, luego la tarea y el formato.

Paso 4 — Usar datos directamente en el prompt:
  Si Copilot no accede al documento, copia y pega directamente los 
  datos brutos relevantes dentro del prompt (máximo 5–6 líneas de datos).
  Esto garantiza que Copilot trabaje con la información correcta.

Paso 5 — Reiniciar la conversación de Copilot:
  Haz clic en el ícono de "Nueva conversación" (✏️) en el panel de Copilot.
  Inicia el prompt nuevamente desde el principio con el contexto completo.
```

---

## Limpieza del Entorno

Al finalizar el laboratorio, realiza los siguientes pasos para dejar el entorno ordenado:

**1. Verificar que todos los archivos están guardados en SharePoint:**
```
- M2_ReporteEHS_[TuNombre].docx → guardado en SharePoint ✅
- M2_PresentacionEjecutiva_[TuNombre].pptx → guardado en SharePoint ✅
- Los archivos originales del instructor NO deben haber sido modificados.
```

**2. Cerrar las aplicaciones de Word y PowerPoint:**
```
Cierra todas las ventanas de Word y PowerPoint.
Si aparece un diálogo de guardado, confirma "Guardar" y verifica 
que la ubicación sea SharePoint (no "Este PC" ni "Escritorio").
```

**3. Compartir los archivos con el instructor (si se requiere revisión):**
```
En SharePoint:
1. Selecciona tu archivo M2_ReporteEHS_[TuNombre].docx
2. Haz clic en "Compartir" → "Copiar vínculo"
3. Asegúrate de que el vínculo sea "Solo personas de tu organización"
4. Envía el vínculo al instructor por el canal de Teams del curso.
Repite el proceso para la presentación de PowerPoint.
```

**4. Limpiar datos sensibles (verificación de privacidad):**
```
Confirma que ninguno de tus documentos contiene:
❌ Nombres reales de empleados
❌ Datos reales de la empresa
❌ Información confidencial de seguridad real
✅ Solo datos ficticios del escenario de práctica
```

**5. Cerrar sesión si usas un equipo compartido:**
```
Si el laboratorio se realizó en un equipo compartido o de sala de cómputo:
Microsoft Edge → Perfil → "Cerrar sesión"
Esto evita que otros usuarios accedan a tu cuenta de Microsoft 365.
```

---

## Resumen del Laboratorio

### Lo que Aprendiste

En este laboratorio aplicaste un flujo completo de comunicación ejecutiva en EHS usando Microsoft 365 Copilot, cubriendo cuatro competencias clave:

| Etapa | Competencia desarrollada | Herramienta principal |
|---|---|---|
| **1 — Síntesis Normativa** | Interpretar y resumir requisitos de ISO 14001, ISO 45001 y NOMs usando prompts estructurados (contexto + documento + acción + formato) | Copilot en Word |
| **2 — Conclusiones Ejecutivas** | Transformar datos brutos de auditoría en conclusiones estructuradas bajo el esquema Hallazgo + Impacto + Recomendación | Copilot en Word |
| **3 — Action Titles** | Crear títulos estratégicos que comunican el mensaje principal en lugar de solo describir el tema | Copilot en Word |
| **4 — Presentación Ejecutiva** | Estructurar una presentación de 9 diapositivas orientada a la toma de decisiones ejecutivas | Copilot en PowerPoint |

### Principios Clave para Recordar

1. **La calidad del prompt determina la calidad del resultado.** Los cuatro elementos esenciales son: contexto, documento de referencia, acción solicitada y formato de salida.

2. **Copilot acelera, el especialista valida.** Ningún resultado de Copilot debe usarse sin revisión profesional, especialmente en contextos normativos donde los errores tienen consecuencias legales.

3. **Un action title efectivo puede leerse de forma aislada y comunicar la situación crítica.** Si solo lees los títulos de una presentación y entiendes el problema, los action titles son efectivos.

4. **La estructura Hallazgo + Impacto + Recomendación** es el estándar de comunicación ejecutiva en EHS porque responde las tres preguntas que toda audiencia directiva necesita: ¿qué pasó?, ¿qué significa?, ¿qué hacemos?

5. **Los archivos deben vivir en SharePoint o OneDrive**, no en el disco local, para que Copilot pueda acceder a ellos y generar resultados contextualizados.

### Conexión con el Siguiente Módulo

Las habilidades de síntesis normativa y comunicación ejecutiva desarrolladas en este laboratorio serán la base del **Módulo 3**, donde trabajarás con datos cuantitativos de accidentabilidad en Excel. Copilot en Excel te ayudará a analizar tendencias, identificar patrones estadísticos y generar visualizaciones que complementarán el tipo de reporte ejecutivo que construiste hoy.

---

### Recursos de Referencia

| Recurso | Descripción | Enlace |
|---|---|---|
| Documentación de Copilot en Word | Guía oficial de Microsoft para usar Copilot en Word | [learn.microsoft.com/es-es/copilot/microsoft-365](https://learn.microsoft.com/es-es/copilot/microsoft-365/microsoft-365-copilot-overview) |
| Copilot en PowerPoint — Guía oficial | Cómo crear y mejorar presentaciones con Copilot | [support.microsoft.com — Copilot en PowerPoint](https://support.microsoft.com/es-es/office/crear-una-presentaci%C3%B3n-con-copilot-en-powerpoint) |
| ISO 14001:2015 — Descripción general | Requisitos del sistema de gestión ambiental | [iso.org/standard/60857.html](https://www.iso.org/standard/60857.html) |
| ISO 45001:2018 — Descripción general | Requisitos del sistema de gestión de seguridad y salud | [iso.org/standard/63787.html](https://www.iso.org/standard/63787.html) |
| NOM-001-SEMARNAT-1996 | Límites máximos permisibles en aguas residuales (México) | [DOF — NOM-001-SEMARNAT](https://www.dof.gob.mx/nota_detalle.php?codigo=4863829&fecha=06/01/1997) |
| NOM-011-STPS-2001 | Condiciones de seguridad e higiene — Ruido (México) | [STPS — NOM-011](https://www.stps.gob.mx/bp/secciones/dgsst/normatividad/normas/Nom-011.pdf) |
| Biblioteca de prompts para EHS | Comunidad Microsoft Tech Community — Copilot | [techcommunity.microsoft.com](https://techcommunity.microsoft.com/t5/microsoft-365-copilot/ct-p/Microsoft365Copilot) |

---

> **📝 Nota del Instructor:** Al finalizar el laboratorio, dedica 5–8 minutos a una revisión grupal rápida. Pide a 2–3 participantes que proyecten sus action titles y lean sus conclusiones ejecutivas en voz alta. Facilita una discusión breve sobre la diferencia entre los títulos descriptivos originales y los action titles generados. Este cierre reflexivo consolida el aprendizaje y permite identificar participantes que necesitan refuerzo antes del Módulo 3.
