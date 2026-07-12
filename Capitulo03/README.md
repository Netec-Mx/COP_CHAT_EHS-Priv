# Análisis de Indicadores de Accidentabilidad y Visualización de Datos EHS con Microsoft 365 Copilot en Excel

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 90 minutos |
| **Complejidad** | Intermedia |
| **Audiencia** | Personal de las áreas de EHS, Seguridad Patrimonial, Ingeniería y Mantenimiento con responsabilidades de supervisión, auditoría y análisis estadístico. |
| **Tecnologías** | Microsoft Copilot (M365 / Interfaz de Chat), Microsoft Excel y Microsoft Word |
| **Enfoque** | Procesamiento de grandes volúmenes de datos operativos, analítica de datos de seguridad, cálculo de fórmulas normativas internacionales (OSHA), identificación de causa raíz y visualización gráfica automatizada. |

---

## 2. Descripción Corta

Este laboratorio avanzado de 90 minutos capacita a los profesionales de EHS en el uso de Microsoft Copilot para transformar registros históricos de accidentes en inteligencia preventiva de alto impacto. Mediante un flujo de trabajo práctico de copiado y pegado directo, los estudiantes estructurarán una base de datos de siniestralidad en Excel, utilizarán la IA para calcular de forma matemática índices estandarizados de frecuencia y severidad bajo criterios OSHA, y ordenarán a Copilot procesar las tendencias para generar gráficos conceptuales e interpretaciones críticas de causa raíz destinadas a la prevención de pérdidas.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Consolidar registros masivos de siniestralidad** en formatos tabulares limpios y estructurados dentro de hojas de cálculo.
* **Calcular e interpretar indicadores de accidentabilidad internacionales** (Índice de Frecuencia e Índice de Severidad OSHA) mediante procesamiento analítico guiado por IA.
* **Descubrir patrones y correlaciones ocultas** en los datos operativos (turnos de mayor riesgo, maquinaria crítica, tipos de lesión).
* **Generar representaciones gráficas y diagramas visuales de tendencias** directamente desde la interfaz de Copilot para su uso en reportes.
* **Diseñar planes de acción correctiva inmediatos** basados en hallazgos cuantitativos y metodologías de causa raíz.

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot** (habilitado para análisis y visualización gráfica).
* Aplicación de **Microsoft Excel** abierta y lista para producción.
* Aplicación de **Microsoft Word** abierta con un documento en blanco guardado como `Analisis_Estadistico_Siniestralidad.docx`.

---

## 5. Procedimiento Paso a Paso

### Paso 1: Importación de la Base de Datos Histórica de Siniestralidad

El primer paso para realizar un análisis de tendencias confiable es contar con un registro histórico estructurado. Copilot procesará un escenario con múltiples incidentes simulados y los entregará en un formato listo para Excel.

1. Abra el chat de **Microsoft Copilot**.
2. Introduzca el siguiente prompt avanzado para generar la matriz de datos históricos:

```
Actúa como un Analista de Datos de EHS e Ingeniero Estadístico. Necesito poblar un registro histórico de accidentes e incidentes de nuestra planta de manufactura correspondiente al último semestre.

Genera una tabla de datos formal y limpia (omite formatos CSV planos con comas). Devuelve la información estructurada en formato de tabla visual de Markdown (usando barras verticales | y guiones) para que al seleccionarla, copiarla y pegarla directamente en Excel, cada dato se posicione de forma automática en su celda correspondiente.

La tabla debe contener exactamente las siguientes columnas:
ID_Incidente | Mes | Turno | Área_Planta | Tipo_Lesión | Días_Perdidos | Maquinaria_Involucrada

Pobla la matriz simulando exactamente 6 registros detallados que presenten patrones industriales realistas (por ejemplo, accidentes repetitivos en turnos nocturnos o áreas específicas como molienda, prensado o mantenimiento):
1. INC-001 | Enero | Nocturno | Molienda | Atrapamiento leve | 12 | Molino de Bolas A
2. INC-002 | Febrero | Diurno | Prensas | Contusión en mano | 4 | Prensa Hidráulica 2
3. INC-003 | Marzo | Nocturno | Molienda | Esguince por caída | 8 | Pasillo Técnico
4. INC-004 | Abril | Mixto | Mantenimiento | Quemadura térmica | 15 | Taller de Soldadura
5. INC-005 | Mayo | Nocturno | Molienda | Atrapamiento de dedos | 22 | Molino de Bolas A
6. INC-006 | Junio | Diurno | Calidad | Corte menor | 0 | Mesa de Inspección

Entrégame únicamente la tabla estructurada, sin introducciones ni saludos conversacionales.
```

3. Seleccione la tabla visual generada por Copilot arrastrando el cursor sobre todas sus celdas y cópiela (`Ctrl+C`).
4. Abra **Microsoft Excel**, seleccione la celda A1 de una hoja en blanco y pegue directamente (`Ctrl+V`). Verifique la correcta distribución de las columnas. Nombre a esta pestaña `Registro_Historico` y guarde el archivo como `Analisis_Estadistico_EHS.xlsx`.

---

### Paso 2: Cálculo Matemático de Indicadores Internacionales (OSHA)

El análisis estadístico normativo exige calcular las tasas estandarizadas para poder comparar el desempeño de la planta con los niveles aceptables de la industria. Utilizaremos a Copilot para procesar los cálculos globales basados en los datos del Paso 1.

1. Introduzca el siguiente prompt en el chat de Copilot para automatizar la aplicación de las fórmulas analíticas:

```
Actúa como un Auditor Senior de EHS experto en Normativa OSHA. Basado en los 6 registros de incidentes del Paso 1, necesito que realices el procesamiento matemático de las métricas de accidentabilidad de la planta. 

Para los cálculos, asume que la planta tiene un promedio de 150 trabajadores y que en el semestre acumulado laboraron un total exacto de 180,000 Horas-Hombre (HHT).

Devuelve una tabla formal en formato Markdown para copiar directamente en Excel que muestre los siguientes indicadores calculados con sus respectivas fórmulas estándar OSHA:
1. **Total de Días Perdidos:** La sumatoria exacta de los días perdidos en el semestre.
2. **Índice de Frecuencia (IF) OSHA (Fórmula: [Número de Accidentes x 200,000] / Horas Hombre Trabajadas):** Calcula el valor exacto para nuestros 6 accidentes y explica brevemente qué significa el resultado.
3. **Índice de Severidad (IS) OSHA (Fórmula: [Número de Días Perdidos x 200,000] / Horas Hombre Trabajadas):** Calcula el valor exacto basado en la sumatoria de días perdidos y detalla el nivel de gravedad de la planta.

Entrega únicamente la tabla con las fórmulas y los resultados finales calculados, lista para producción.
```

2. Copie la tabla analítica devuelta por Copilot (`Ctrl+C`).
3. Vaya a su archivo de Excel `Analisis_Estadistico_EHS.xlsx`, cree una segunda hoja llamada `Indicadores_OSHA`, seleccione la celda A1 y pegue los resultados (`Ctrl+V`).

---

### Paso 3: Análisis de Causa Raíz y Aislamiento de Tendencias Críticas

Con los datos y los índices calculados, el especialista en EHS debe utilizar la inteligencia artificial para analizar el volumen total de información e identificar el "foco rojo" o causa raíz de la siniestralidad semestral de la fábrica.

1. Introduzca el siguiente prompt en el chat de Copilot para extraer las tendencias críticas:

```
Actúa como un Especialista en Investigación de Accidentes y Metodología Lean Six Sigma. Analiza de manera integral los datos del registro histórico (Paso 1) y los indicadores OSHA (Paso 2).

Escribe un reporte de diagnóstico técnico en español estructurado bajo los siguientes encabezados formales:
1. **Identificación de la Tendencia Crítica Operativa:** Identifica cuál es el área de la planta, el turno específico y la maquinaria que concentra el mayor porcentaje de incidentes y días perdidos de forma alarmante.
2. **Análisis de Causa Raíz Hipotético (Los 5 Porqués):** Desarrolla una secuencia lógica de '5 Porqués' simulada que explique por qué están ocurriendo atrapamientos específicamente en el 'Turno Nocturno' en el 'Molino de Bolas A' (vincula factores como fatiga, falta de iluminación o bypass de guardas de seguridad).
3. **Plan de Acción de Mitigación Inmediato:** Propone 3 acciones concretas de ingeniería y control administrativo para erradicar este patrón antes del próximo mes.

Genera las conclusiones con un lenguaje de ingeniería preventiva de alto nivel, listo para exportar a Word.
```

2. Copie el análisis técnico generado por Copilot y péguelo en su documento de Word `Analisis_Estadistico_Siniestralidad.docx` bajo el título `## 1. Informe Ejecutivo de Tendencias de Siniestralidad y Causa Raíz`.

---

### Paso 4: Generación Visual del Gráfico de Rendimiento desde Copilot

Para que los supervisores y comités de seguridad entiendan la gravedad de las tendencias sin leer el reporte completo, ordenaremos a Copilot que genere una representación gráfica o diagrama visual que ilustre la distribución del riesgo detectado.

1. Introduzca el siguiente prompt en el chat de Copilot para activar su motor de visualización de datos:

```
Actúa como un Diseñador de Visualización de Datos de EHS. Basado en el registro de accidentes del primer semestre, necesito que generes una representación gráfica clara y directa dentro del chat.

Por favor, genera y entrégame:
1. **Un Gráfico de Barras Textual/Conceptual:** Diseña una gráfica utilizando caracteres y barras visuales (ejemplo: [██████████] 50%) que muestre la distribución del 'Número de Incidentes por Área de la Planta', contrastando Molienda (3 accidentes), Prensas (1 accidente), Mantenimiento (1 accidente) y Calidad (1 accidente).
2. **Estructura del Gráfico Recomendado para Excel:** Explica de forma breve y concisa qué tipo de gráfico nativo de Excel debería usar el usuario para cruzar de forma óptima el 'Mes del año' contra los 'Días Perdidos', detallando qué variable colocar en el eje X y cuál en el eje Y para que la gerencia vea la evolución cronológica de la gravedad.

Evita códigos de programación. Entrega la gráfica visual de barras de texto de forma directa y limpia.
```

2. Copie el gráfico de barras textual y las recomendaciones visuales generadas por Copilot.
3. Pegue este recurso en su archivo de Word bajo el título `## 2. Panel Gráfico de Distribución del Riesgo de Planta`.

---

### Paso 5: Reto de Aplicación Autónoma – Simulación de Alerta por Brote de Incidentes Ergonómicos

**Instrucciones para el estudiante:** Durante las últimas dos semanas del mes de julio, el servicio médico de la planta reportó un incremento inusual de **7 trabajadores del área de empaque manual** que acudieron por dolores lumbares e inflamación en muñecas (lesiones ergonómicas acumulativas). Ninguno ha generado días perdidos aún (estatus de incidentes menores), pero el analista de EHS sabe que si no se interviene, se transformará en incapacidades severas en el próximo mes.

#### El Desafío:
Aplicando de forma integral la metodología analítica del laboratorio y sin asistencia de plantillas previas, diseñe un prompt autónomo en Copilot para resolver esta contingencia operativa:

1. **Estructura de la Solicitud Autónoma:** Ordene a Copilot que asuma el rol de un Ergónomo Industrial y Consultor de Salud Ocupacional.
2. **Análisis Cuantitativo y Plan Preventivo:** Indique a la IA que procese la situación del brote ergonómico en empaque manual y proponga:
   - El diseño conceptual de una **Lista de Verificación Ergonómica** rápida de 4 puntos clave que el supervisor de empaque deba aplicar en las estaciones de trabajo de inmediato.
   - La definición técnica de un indicador preventivo que anticipe estas lesiones antes de que se conviertan en días perdidos.
   - Una propuesta de "Pausas Activas Dirigidas" específica para movimientos repetitivos de manufactura.
3. **Prueba de Verificación:** El estudiante revisará que el entregable resultante entregado por Copilot proporcione soluciones enfocadas en la prevención ergonómica de piso (rediseño de alturas de mesas, rotación de puestos cada 2 horas), demostrando que sabe dirigir la IA para contener riesgos de salud ocupacional antes de que impacten las estadísticas OSHA de la empresa.

---

## 6. Conceptos Clave para Recordar

* **Índice de Frecuencia OSHA:** Métrica internacional estandarizada que representa el número de accidentes con baja médica que ocurren por cada 200,000 horas-hombre trabajadas por el total del personal.
* **Índice de Severidad OSHA:** Indicador que mide la gravedad de los accidentes ocurridos, representando el total de días de trabajo perdidos debido a incapacidades por cada 200,000 horas-hombre laborales.
* **Metodología de los 5 Porqués:** Técnica sistemática de preguntas utilizada en la fase de análisis de problemas para buscar las relaciones de causa-efecto que generan un incidente específico, permitiendo llegar a la raíz del fallo.

---

## 7. Resultado Esperado del Estudiante

Para validar la correcta conclusión de esta práctica avanzada de 90 minutos de analítica de seguridad, el estudiante consolidará y presentará:

1. **Archivo `Analisis_Estadistico_EHS.xlsx` (Excel):**
   * Pestaña `Registro_Historico` con la matriz semestral de los 6 incidentes críticos importados en el Paso 1.
   * Pestaña `Indicadores_OSHA` con las fórmulas normativas y tasas calculadas por la IA en el Paso 2.
2. **Archivo `Analisis_Estadistico_Siniestralidad.docx` (Word):**
   * El informe maestro que contiene la investigación de causa raíz (Paso 3), el panel gráfico y diagramación textual de distribución del riesgo (Paso 4) y la resolución completa del Plan de Intervención Ergonómica desarrollado en el Reto Autónomo (Paso 5).
