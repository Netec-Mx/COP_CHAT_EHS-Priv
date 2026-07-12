# Creación de instrucciones precisas para la elaboración y revisión de documentos y políticas, permitiendo que la IA actúe como un redactor técnico capaz de estructurar manuales operativos y procedimientos de seguridad alineados con los estándares de la empresa.

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 60 minutos |
| **Complejidad** | Básica - Inicial |
| **Audiencia** | Personal de las áreas de EHS (Seguridad, Salud y Medio Ambiente), Seguridad Patrimonial, Ingeniería, Mantenimiento y Energía, tanto en roles operativos como de supervisión y análisis. |
| **Tecnologías** | Microsoft Copilot (M365 / Interfaz de Chat) y Microsoft Word |
| **Enfoque** | Redacción técnica especializada, estructuración de procedimientos operativos estándar (SOPs), estandarización de políticas de seguridad y cumplimiento normativo e institucional. |

---

## 2. Descripción Corta

Este laboratorio práctico de 60 minutos introduce a los profesionales de seguridad y medio ambiente en el uso de Microsoft Copilot como un redactor técnico de alta precisión. A través de una metodología secuencial, los participantes aprenderán a formular instrucciones avanzadas (prompts) para que la IA actúe bajo roles expertos y genere de forma inmediata una política de contratistas, una matriz de análisis de riesgo de trabajo y un procedimiento para trabajos en alturas. Los resultados se transferirán directamente a Word mediante copiado y pegado para estructurar el inicio de su manual maestro de seguridad.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Configurar perfiles de IA (roles técnicos)** especializados en ingeniería de seguridad e higiene industrial para la generación de contenido crítico.
* **Redactar e implementar directrices normativas** claras y restrictivas aplicables a proveedores y contratistas externos.
* **Estructurar un Procedimiento Operativo Estándar (SOP)** bajo un formato industrial estandarizado sin omitir medidas críticas de prevención.
* **Evaluar y auditar documentación de EHS** utilizando la IA como un revisor normativo neutral.

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot**.
* Aplicación de **Microsoft Word** abierta con un documento en blanco guardado como `Manual_Maestro_EHS_Seguridad.docx`.

---

## 5. Procedimiento Paso a Paso

### Paso 1: Generación de la Política de Seguridad para Contratistas Externos

El control de los proveedores de servicios externos en las instalaciones es uno de los eslabones más débiles en la seguridad patrimonial y de EHS. El supervisor de seguridad necesita emitir una política estricta de cumplimiento inmediato antes de otorgar cualquier acceso físico a la planta.

1. Abra el chat general de **Microsoft Copilot**.
2. Introduzca el siguiente prompt avanzado para configurar el rol técnico y generar la política:

```
Actúa como un Director de Seguridad Patrimonial y Especialista Corporativo en EHS. Necesito redactar una política formal en español titulada "Política de Control, Acceso y Seguridad para Contratistas Externos" para nuestra planta industrial.

Por favor, genera un texto formal, imperativo y de corte administrativo legal que incluya los siguientes apartados numerados:
1. **Objetivo de la Política:** Regular el ingreso y comportamiento del personal externo para mitigar riesgos de accidentes y brechas de seguridad física.
2. **Requisitos Obligatorios de Entrada (Seguridad Patrimonial):** Detalla la obligatoriedad de presentar identificación oficial, registro ante la seguridad social, lista de herramientas y equipo de cómputo a ingresar, y el uso visible de un gafete de contratista en todo momento.
3. **Equipo de Protección Personal (EPP) Mínimo Obligatorio (EHS):** Define que ningún contratista puede pisar el área operativa sin botas de casquillo de acero, lentes de seguridad, chaleco de alta visibilidad con reflejante y casco industrial.
4. **Consecuencias por Incumplimiento:** Explica con un lenguaje administrativo severo la suspensión inmediata del trabajo y el veto definitivo de la empresa contratista en caso de violar las reglas de seguridad.

Genera el documento de forma directa y estructurada, lista para uso institucional, sin introducciones conversacionales.
```

3. Seleccione el bloque de texto formal devuelto por Copilot y cópielo (`Ctrl+C`).
4. Vaya a su documento de Word `Manual_Maestro_EHS_Seguridad.docx`, cree el título `## Sección 1: Políticas Corporativas de Control` y pegue el texto (`Ctrl+V`). Revise que el tono sea estrictamente profesional y normativo.

---

### Paso 2: Construcción de una Matriz de Análisis de Riesgo de Trabajo (ART) en Formato Tabla

Antes de iniciar cualquier labor de mantenimiento correctivo en el piso de producción, el departamento de EHS exige la elaboración de un Análisis de Riesgo de Trabajo (ART) para desglosar la actividad y prever peligros.

1. En la misma ventana de chat de Copilot, introduzca el siguiente prompt para estructurar la matriz preventiva:

```
Actúa como un Ingeniero de Seguridad Industrial Experto. Necesito estructurar la matriz de un Análisis de Riesgo de Trabajo (ART) preliminar para la tarea específica de: "Mantenimiento preventivo en el motor principal de la banda transportadora de materia prima".

Genera el resultado en formato de tabla visual de Markdown (usando barras verticales | y guiones) para que al seleccionarla, copiarla y pegarla directamente en Microsoft Word, se transforme de inmediato en una tabla con bordes y celdas individuales.

La tabla debe contener exactamente las siguientes columnas:
Secuencia de Pasos de la Tarea | Peligros Potenciales Identificados | Riesgos Asociados | Medidas Preventivas y de Control Obligatorias

Desglosa la actividad en exactamente 3 pasos secuenciales:
1. Bloqueo de energía y etiquetado (LOTO) en el tablero principal.
2. Desmontaje de la guarda de seguridad y carcasas de protección.
3. Manipulación interna de componentes mecánicos y lubricación.

Entrégame únicamente la tabla estructurada, sin saludos ni notas aclaratorias.
```

2. Seleccione la tabla visual devuelta por Copilot arrastrando el cursor sobre todas sus filas y celdas, y cópiela (`Ctrl+C`).
3. Vuelva a su archivo de Word `Manual_Maestro_EHS_Seguridad.docx`, cree un subtítulo llamado `### 1.1 Análisis de Riesgo de Trabajo (ART) - Banda Transportadora` y pegue la tabla directamente (`Ctrl+V`). Verifique que Word la reconozca como una tabla real de celdas y ajuste el diseño si es necesario.

---

### Paso 3: Elaboración de un Procedimiento Operativo Estándar (SOP) para Trabajos en Alturas

El trabajo en alturas constituye una de las actividades de alto riesgo más críticas en cualquier entorno industrial. El analista de EHS debe redactar el procedimiento paso a paso para la liberación del permiso de trabajo seguro.

1. Introduzca el siguiente prompt en la interfaz de Copilot para automatizar la redacción técnica del procedimiento:

```
Actúa como un Auditor de Seguridad e Higiene Industrial certificado bajo estándares internacionales. Necesito redactar un Procedimiento Operativo Estándar (SOP) en español para la ejecución segura de "Trabajos en Alturas (Cualquier labor realizada a más de 1.80 metros sobre el nivel del suelo)".

Por favor, genera un documento técnico y estructurado con el siguiente orden formal:
1. **Código del Documento:** EHS-SOP-005 | **Versión:** 1.0
2. **Responsabilidades:** Define claramente el rol del "Supervisor de EHS" (quien autoriza y audita en sitio) y del "Operador/Ejecutor" (quien inspecciona su equipo y ejecuta la labor).
3. **Inspección Previa del Equipo de Caídas:** Redacta una lista de verificación detallada de los puntos críticos a revisar en el arnés de cuerpo completo (herrajes en D, costuras, indicadores de impacto) y en la línea de vida antes de ponérselos.
4. **Condiciones de Suspensión Inmediata:** Describe bajo qué factores ambientales u operativos (como presencia de lluvia, ráfagas de viento superiores a 30 km/h o falta de un punto de anclaje certificado) la labor se cancela de forma mandatoria.

Usa un lenguaje técnico, directo, preciso y de ingeniería preventiva, omitiendo introducciones amigables.
```

2. Copie el texto completo del procedimiento de alturas generado por la IA (`Ctrl+C`).
3. Incorpórelo en su documento de Word bajo el título `## Sección 2: Procedimientos Operativos Estándar (SOP) de Alto Riesgo`.

---

### Paso 4: Reto de Aplicación Autónoma – Auditoría Normativa de un Procedimiento Deficiente

**Instrucciones para el estudiante:** En las auditorías de planta, es común encontrarse con documentos viejos o mal redactados que ponen en riesgo la operación. A continuación se le presenta un extracto de un procedimiento de seguridad real que fue redactado de manera deficiente:

> *"Para limpiar el derrame de químicos en el pasillo de almacén, el operador debe agarrar rápido el trapeador, echarle agua y limpiar para que nadie se resbale. Si huele muy feo el químico, que abra las ventanas de atrás y use un cubrebocas de tela normal de los que tengan ahí a la mano."*

#### El Desafío:
Aplicando sus conocimientos en EHS y su destreza técnica con la IA, diseñe un prompt autónomo en Copilot para auditar y corregir este texto deficiente:

1. **Estructura de la Instrucción Autónoma:** Ordena a Copilot que actúe como un Especialista en Respuesta a Emergencias Químicas y Materiales Peligrosos (HAZMAT).
2. **Instrucciones de Auditoría:** Pídale a la IA que analice el extracto anterior, identifique los 3 errores críticos de seguridad que contiene (por ejemplo, la falta de identificación del químico, el uso de equipo de protección inadecuado y la disposición incorrecta del residuo) y que reescriba ese procedimiento de forma técnica, profesional y segura utilizando el estándar correcto para el manejo de derrames químicos menores en plantas.
3. **Prueba de Verificación:** El estudiante comprobará que el nuevo texto generado por Copilot reemplace el lenguaje informal ("trapeador", "cubrebocas de tela") por términos técnicos de la industria ("kit de control de derrames", "materiales absorbentes inertes", "respirador para vapores químicos") y garantice la seguridad del personal de mantenimiento.

---

## 6. Conceptos Clave para Recordar

* **EHS (Environment, Health and Safety):** Disciplina empresarial y técnica que estudia e implementa aspectos prácticos de la protección ambiental, la seguridad en el trabajo y la salud ocupacional.
* **SOP (Standard Operating Procedure):** Un conjunto de instrucciones paso a paso recopiladas por una organización para ayudar a los trabajadores a realizar operaciones complejas de rutina de manera segura y eficiente.
* **LOTO (Lockout/Tagout):** Procedimiento de seguridad industrial utilizado para garantizar que las máquinas peligrosas se apaguen correctamente y no se vuelvan a encender antes de que se completen los trabajos de mantenimiento o reparación.

---

## 7. Resultado Esperado del Estudiante

Para validar el éxito y la aprobación de esta práctica de 60 minutos, el estudiante deberá consolidar en su repositorio corporativo:

1. **Archivo `Manual_Maestro_EHS_Seguridad.docx` (Word):**
   * El documento oficial estructurado con la Política de Contratistas Externos del Paso 1.
   * La tabla visual del Análisis de Riesgo de Trabajo (ART) importada limpiamente en el Paso 2.
   * El Procedimiento Operativo Estándar (SOP) para Trabajos en Alturas integrado en el Paso 3.
2. **Evidencia del Reto Autónomo:**
   * La corrección técnica y normativa del procedimiento para derrames de químicos del Paso 4 añadida al final del archivo de Word como anexo de control, demostrando la capacidad de usar la IA para auditar la seguridad de la empresa.
