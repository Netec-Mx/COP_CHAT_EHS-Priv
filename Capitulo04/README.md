# Taller de Consolidación — Análisis Predictivo y Reporte Integral de Seguridad Patrimonial

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 90 minutos |
| **Complejidad** | Intermedia |
| **Audiencia** | Personal de las áreas de EHS, Seguridad Patrimonial, Ingeniería y Mantenimiento responsables de la gestión de riesgos, auditorías internas y protección de activos organizacionales. |
| **Tecnologías** | Microsoft Copilot (M365 / Interfaz de Chat), Microsoft Excel y Microsoft Word |
| **Enfoque** | Auditoría preventiva, análisis de vulnerabilidades, seguridad patrimonial estratégica, modelos de prevención de pérdidas e integración de informes ejecutivos maestros. |

---

## 2. Descripción Corta

Los participantes aprenderán a utilizar Microsoft Copilot como una herramienta analítica predictiva para identificar patrones de vulnerabilidad en la cadena de custodia y los perímetros físicos de la organización. Mediante un flujo operativo práctico, los estudiantes estructurarán una base de datos de hallazgos de auditoría en Excel, utilizarán la IA para correlacionar factores de riesgo y generarán un Reporte Maestro de Hallazgos y Acciones Preventivas en Word, consolidando su competencia en la mitigación estratégica de pérdidas.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Estructurar matrices de vulnerabilidad patrimonial** en hojas de cálculo utilizando metodologías cuantitativas aceleradas por IA.
* **Identificar tendencias predictivas e intrusiones potenciales** mediante el análisis cruzado de datos históricos de seguridad física.
* **Redactar e institucionalizar planes de acción correctiva y preventiva (CAPA)** con un lenguaje directivo de alta prioridad.
* **Consolidar un Informe Maestro de Auditoría Preventiva** listo para ser presentado ante comités de dirección y auditoría corporativa.

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot**.
* Aplicación de **Microsoft Excel** abierta y lista para trabajar.
* Aplicación de **Microsoft Word** abierta con un documento en blanco guardado como `Informe_Maestro_Auditoria_Preventiva.docx`.

---

## 5. Procedimiento Paso a Paso

### Paso 1: Estructuración de la Matriz de Hallazgos de Auditoría Física

Para anticipar las brechas de seguridad antes de que ocurra una pérdida material, el equipo de Seguridad Patrimonial debe consolidar las vulnerabilidades detectadas durante los recorridos perimetrales en una matriz de datos cuantitativa.

1. Abra el chat de **Microsoft Copilot**.
2. Introduzca el siguiente prompt avanzado para generar la base de datos de auditoría:

```
Actúa como un Auditor Líder de Seguridad Patrimonial y Especialista en Prevención de Pérdidas. Necesito estructurar una matriz de hallazgos sobre las vulnerabilidades físicas detectadas en nuestra instalación industrial durante el último mes.

Genera una tabla formal y limpia (no uses formato CSV plano con comas). Devuelve la información estructurada en formato de tabla visual de Markdown (usando barras verticales | y guiones) para que al seleccionarla, copiarla y pegarla directamente en Excel, cada dato se posicione de forma automática en su celda correspondiente.

La tabla debe contener exactamente las siguientes 6 columnas:
ID_Hallazgo | Componente_Seguridad | Zona_Planta | Vulnerabilidad_Detectada | Nivel_Riesgo (Alto / Medio / Bajo) | Impacto_Potencial

Pobla la matriz con exactamente 5 registros que representen fallos industriales típicos y realistas:
1. AUD-001 | Control de Acceso | Puerta Embarques | Lector biométrico presenta fallas intermitentes | Alto | Ingreso no autorizado de personal externo
2. AUD-002 | Seguridad Perimetral | Cerca Norte | Vegetación obstruye la línea de vista de cámaras | Medio | Puntos ciegos aprovechables para intrusión
3. AUD-003 | Iluminación | Patio de Maniobras | 3 luminarias fundidas en zona de estacionamiento | Alto | Asaltos o vandalismo amparados por la obscuridad
4. AUD-004 | Monitoreo | Centro de Control (CCTV) | Monitor principal de videovigilancia parpadea | Medio | Retraso en la detección temprana de alertas
5. AUD-005 | Custodia de Activos | Almacén de Producto | Candado de la jaula de alto valor sin llave maestra | Bajo | Retraso operativo en aperturas de emergencia

Entrégame únicamente la tabla estructurada, sin introducciones ni saludos conversacionales.
```

3. Seleccione la tabla visual devuelta por Copilot arrastrando el cursor sobre todas sus celdas y cópiela (`Ctrl+C`).
4. Abra **Microsoft Excel**, seleccione la celda A1 de la primera hoja y pegue directamente (`Ctrl+V`). Verifique que los datos se distribuyan de forma inmediata en las columnas independientes. Nombre a esta pestaña `Hallazgos_Auditoria` y guarde el archivo como `Matriz_Riesgos_Patrimoniales.xlsx`.

---

### Paso 2: Análisis Predictivo y Modelado de Escenarios de Riesgo

El verdadero valor de la analítica en seguridad patrimonial radica en pasar de un enfoque reactivo a uno predictivo. Utilizaremos a Copilot para procesar los datos cruzados del paso anterior e identificar qué combinaciones de fallos incrementan la probabilidad de un incidente mayor.

1. Introduzca el siguiente prompt analítico en la interfaz de Copilot:

```
Actúa como un Consultor de Inteligencia y Seguridad Patrimonial Corporativa. Analiza la matriz de vulnerabilidades del paso anterior. Necesito que identifiques tendencias predictivas cruzando los datos para modelar el peor escenario posible.

Por favor, devuélveme un reporte de análisis predictivo estructurado en español bajo los siguientes encabezados:
1. **Correlación de Riesgos (Foco de Alerta Máxima):** Explica cómo la combinación de la vulnerabilidad AUD-002 (puntos ciegos por vegetación en cerca norte) junto con la AUD-003 (falta de iluminación en patios) crea un escenario idóneo para una intrusión nocturna exitosa.
2. **Pronóstico de Pérdidas Estimado:** Describe el impacto financiero y de continuidad operativa si se materializa un robo de mercancía en la zona de embarques debido a la falla del biométrico (AUD-001).
3. **Indicador Clave Predictivo Recomendado:** Propón una métrica o indicador preventivo (ejemplo: Índice de Mantenimiento a Sistemas de Seguridad) que permita medir la salud de los dispositivos antes de que fallen por completo.

Genera el análisis de forma directa, rigurosa y con un enfoque crítico empresarial, listo para copiar a Word.
```

2. Copie el análisis técnico generado por Copilot (`Ctrl+C`).
3. Vaya a su archivo de Excel `Matriz_Riesgos_Patrimoniales.xlsx`, cree una segunda pestaña llamada `Analisis_Predictivo`, seleccione la celda A1 y pegue el texto completo (`Ctrl+V`) para centralizar la información.

---

### Paso 3: Consolidación del Tablero de Indicadores del Plan Preventivo

Para presentar los resultados ante el comité directivo sin obligarlos a leer los registros individuales, utilizaremos a Copilot para procesar y consolidar las métricas de la auditoría en un cuadro de mando directo.

1. Ingrese el siguiente prompt en la interfaz de Copilot para generar la tabla consolidada:

```
Actúa como un Especialista en Cuadros de Mando de Seguridad Operativa. Basado en los 5 hallazgos de la auditoría física del Paso 1, necesito que proceses la información y generes una tabla resumen consolidada para el Tablero Directivo.

Devuelve el resultado en formato de tabla visual de Markdown (usando barras verticales | y guiones) para poder seleccionarla, copiarla y pegarla directamente en Excel:

La tabla condensada debe mostrar exactamente:
- Métrica de Control | Valor Calculado | Prioridad de Atención Recomendada
- Total de Vulnerabilidades Detectadas | 5 | Revisión global del estatus de la planta.
- Hallazgos clasificados en Riesgo Alto | 2 | Atención mandatoria e inmediata en las próximas 24 horas.
- Hallazgos clasificados en Riesgo Medio | 2 | Programar corrección en el plan de mantenimiento semanal.
- Hallazgos clasificados en Riesgo Bajo | 1 | Monitoreo y resolución rutinaria.
- Eficacia Actual de Barreras Físicas | 60.0% | Alerta al comité; 2 de las 5 barreras principales presentan fallas críticas.

Entrégame únicamente la tabla estructurada con los números consolidados, omitiendo cualquier texto conversacional.
```

2. Seleccione la tabla resumida devuelta por Copilot en el chat y cópiela (`Ctrl+C`).
3. Regrese a su archivo de Excel `Matriz_Riesgos_Patrimoniales.xlsx`, cree una tercera pestaña llamada `Tablero_Direccion`, seleccione la celda A1 y pegue los datos (`Ctrl+V`).

---

### Paso 4: Redacción del Informe Integral de Hallazgos y Acciones Correctivas (CAPA)

Para que la auditoría se transforme en un activo preventivo formal para la organización, se debe estructurar un plan de acciones correctivas y preventivas (CAPA, por sus siglas en inglés) que asigne responsables y tiempos de ejecución claros.

1. Introduzca el siguiente prompt en el chat de Copilot para automatizar la redacción institucional:

```
Actúa como un Director de Cumplimiento Normativo y Auditoría de Seguridad. Necesito formalizar el plan de mitigación para los dos hallazgos catalogados como de "Riesgo Alto" en el Paso 1 (AUD-001 Lector biométrico y AUD-003 Iluminación de patios).

Por favor, genera un documento de plan institucional estructurado con los siguientes apartados:
1. **Título del Documento:** Plan de Acción Correctiva y Preventiva (CAPA) - Seguridad Patrimonial 2026.
2. **Acciones Inmediatas de Contención (Para las próximas 24 horas):** Detalla medidas provisionales (ejemplo: colocar un guardia físico fijo en la puerta de embarques y patrullajes continuos con linternas de alta potencia en el patio).
3. **Acciones de Corrección Definitiva (Ingeniería y Presupuesto):** Define los pasos técnicos para el reemplazo total del biométrico por un sistema de proximidad autónomo y la migración de luminarias fundidas a tecnología LED solar autosustentable.
4. **Gobierno y Seguimiento:** Redacta un párrafo administrativo que establezca auditorías semanales de verificación hasta que ambos hallazgos queden cerrados al 100%.

Utiliza un lenguaje formal, institucional, restrictivo y corporativo.
```

2. Copie el texto completo del plan CAPA generado por la IA.
3. Abra su documento de Word `Informe_Maestro_Auditoria_Preventiva.docx`. Estructure el reporte institucional pegando el contenido en el siguiente orden:
   - Cree el título `## 1. Tablero Ejecutivo de Control de Auditoría` y pegue la tabla de indicadores consolidados que generó en el Paso 3.
   - Cree el título `## 2. Análisis Técnico de Tendencias Predictivas` y pegue el texto analítico generado en el Paso 2.
   - Cree el título `## 3. Plan de Acción Correctiva y Preventiva (CAPA)` y pegue el texto formal generado en este Paso 4.

---

### Paso 5: Reto de Aplicación Autónoma – Auditoría Predictiva en la Cadena de Suministro contra el Contrabando

**Instrucciones para el estudiante:** La organización busca certificar sus operaciones bajo el estándar internacional **BASC (Business Alliance for Secure Commerce)** para asegurar sus exportaciones de recubrimientos. Durante la pre-auditoría en el patio de carga, se detectó que los transportistas externos esperan hasta 4 horas para cargar los contenedores sin supervisión en una zona que carece de cámaras perimetrales y donde el registro de sellos de seguridad de los contenedores se realiza de manera manual en una libreta de papel.

#### El Desafío:
Consolidando todas las capacidades de análisis normativo, enfoque predictivo y gestión de riesgos adquiridas a lo largo de este curso, diseñe e implemente un prompt totalmente autónomo en Copilot para resolver esta brecha de seguridad internacional:

1. **Estructura del Requerimiento Autónomo:** Ordene a Copilot que asuma el rol de un Auditor Internacional Certificado en Seguridad de la Cadena de Suministro y Gestión de Riesgos BASC.
2. **Análisis Técnico y Contención del Riesgo:** Exija en su instrucción que la IA procese la vulnerabilidad del patio de carga y entregue:
   - Una evaluación del **Riesgo Predictivo** (ejemplo: vulnerabilidad ante contaminación de carga, introducción de sustancias ilícitas o contrabando debido a la falta de CCTV y registros manuales vulnerables).
   - El diseño de un **Procedimiento Automatizado de Registro de Sellos** mediante el uso de herramientas digitales estándar de oficina que reemplace la libreta de papel.
   - Una política estricta de tiempo de permanencia y escolta obligatoria para operadores externos dentro de las instalaciones.
3. **Prueba de Verificación:** El estudiante revisará que la respuesta generada por Copilot entregue soluciones profesionales alineadas con normativas internacionales de exportación segura, evitando respuestas genéricas y demostrando que es capaz de dirigir a la inteligencia artificial para construir activos preventivos de alto nivel normativo para la empresa.

---

## 6. Conceptos Clave para Recordar

* **Análisis Predictivo en Seguridad:** Metodología analítica que utiliza datos históricos, correlación de variables y patrones de comportamiento para anticipar dónde y cuándo es más probable que ocurra una brecha de seguridad o pérdida material, permitiendo una intervención oportuna.
* **Plan CAPA (Corrective and Preventive Action):** Sistema conceptual y administrativo de gestión industrial enfocado en investigar, resolver y mitigar desviaciones o fallas normativas, asegurando que se elimine la causa raíz para evitar su recurrencia.
* **Seguridad de la Cadena de Suministro:** Conjunto de medidas de protección física y tecnológica orientadas a salvaguardar las mercancías desde su fabricación y almacenamiento hasta su transporte e ingreso a aduanas internacionales, previniendo actividades delictivas.

---

## 7. Resultado Esperado del Estudiante

Para validar la correcta conclusión de esta práctica avanzada de 90 minutos y la aprobación del taller final del programa, el estudiante consolidará en su repositorio:

1. **Archivo `Matriz_Riesgos_Patrimoniales.xlsx` (Excel):**
   * Pestaña `Hallazgos_Auditoria` con los 5 registros estructurados en el Paso 1.
   * Pestaña `Analisis_Predictivo` que resguarda las tendencias identificadas en el Paso 2.
   * Pestaña `Tablero_Direccion` con el cuadro condensado de indicadores ejecutivos del Paso 3.
2. **Archivo `Informe_Maestro_Auditoria_Preventiva.docx` (Word):**
   * El informe maestro integral unificado con el Tablero de control corporativo, el Análisis Predictivo, el plan institucional CAPA para riesgos altos (Paso 4) y la resolución completa de la estrategia de exportación segura BASC desarrollada de forma independiente en el Reto Autónomo (Paso 5).
