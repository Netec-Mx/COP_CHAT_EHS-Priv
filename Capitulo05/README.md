# Configuración del Perfil de un Agente Evaluador de Riesgos en Planta

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 90 minutos |
| **Complejidad** | Avanzada |
| **Audiencia** | Personal de las áreas de EHS, Seguridad Patrimonial, Ingeniería y Mantenimiento con responsabilidades en la estandarización de procesos y automatización de la seguridad. |
| **Tecnologías** | Microsoft Copilot (Interfaz de Chat / Configuración de Agentes) y Microsoft Word |
| **Enfoque** | Creación de agentes personalizados, ingeniería de prompts de sistema (System Prompts), automatización de evaluaciones de riesgo y pruebas funcionales de agentes. |

---

## 2. Descripción Corta

Este laboratorio práctico de 90 minutos capacita a los profesionales de EHS en el diseño, configuración y consumo de un Agente Evaluador de Riesgos personalizado en Copilot. A través de un flujo de trabajo guiado, los estudiantes utilizarán la IA para generar el prompt de sistema ("instrucciones del agente"), aprenderán el paso a paso detallado para dar de alta al agente dentro de la plataforma corporativa, interactuarán con él mediante tres prompts de consumo especializado para evaluar casos reales en planta y resolverán un reto autónomo de modificación de perfil para expandir el alcance de su asistente digital.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Generar prompts de sistema estructurados** para definir el comportamiento, alcance y restricciones de un agente de IA.
* **Configurar un agente personalizado en Microsoft Copilot** siguiendo los pasos de aprovisionamiento institucionales.
* **Consumir y auditar el rendimiento del agente** mediante casos prácticos de riesgo en el piso de producción.
* **Modificar y actualizar la lógica de un agente** para adaptar sus respuestas a nuevas directrices o normativas de la organización.

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot** y permisos para la creación de agentes personalizados (Copilot Studio o Creador de Agentes integrado).
* Aplicación de **Microsoft Word** abierta con un documento en blanco guardado como `Manual_Creacion_Agentes_EHS.docx`.

---

## 5. Procedimiento Paso a Paso

### Paso 1: Metaprompt – Generación de las Instrucciones de Sistema para el Agente

Para crear un agente confiable, primero necesitamos un prompt de sistema robusto que defina su rol, sus reglas operativas y las metodologías que debe aplicar. Usaremos un "metaprompt" (un prompt que genera otro prompt) para que Copilot redacte la configuración técnica exacta.

1. Abra el chat general de **Microsoft Copilot**.
2. Introduzca el siguiente prompt avanzado para generar las instrucciones de su agente:

```
Actúa como un Ingeniero de Inteligencia Artificial y Experto en Arquitectura de Agentes de Microsoft. Necesito crear un prompt de sistema (instrucciones de configuración) altamente detallado para un nuevo agente personalizado que se llamará "Agente Evaluador de Riesgos EHS".

Por favor, genera un bloque de texto en español estructurado exactamente bajo el siguiente formato técnico para copiar y pegar en la configuración del agente:
- **Rol del Agente:** Especialista Senior en Seguridad e Higiene Industrial encargado de evaluar peligros de planta.
- **Objetivo Principal:** Analizar cualquier descripción de tarea o incidente enviado por el usuario y clasificar de inmediato el nivel de riesgo en Alto, Medio o Bajo.
- **Instrucciones de Proceso (Paso a Paso del Agente):** Primero, listar los 3 peligros físicos evidentes en el texto; segundo, proponer 3 controles críticos obligatorios (usando la jerarquía de control: Ingeniería, Administrativo o EPP); tercero, emitir una recomendación de si la tarea requiere un 'Permiso de Trabajo Especial' o no.
- **Restricciones y Tono:** Tono directo, técnico y formal de ingeniería. El agente jamás debe responder con saludos informales. Si el usuario envía un texto que no está relacionado con seguridad o procesos industriales, el agente debe responder estrictamente: 'Error: El requerimiento no pertenece al ámbito de EHS'.

Devuelve únicamente las instrucciones del sistema listas para producción.
```

3. Seleccione el bloque de instrucciones generado por Copilot, cópielo (`Ctrl+C`) y péguelo provisionalmente en su archivo de Word `Manual_Creacion_Agentes_EHS.docx` bajo el título `## 1. Prompt de Sistema del Agente Evaluador`.

---

### Paso 2: Configuración Paso a Paso del Agente en la Plataforma

Con las instrucciones del sistema listas, el estudiante procederá a dar de alta de forma manual al agente dentro de la interfaz corporativa de Microsoft 365.

1. En su portal de **Microsoft Copilot**, diríjase a la sección de **"Agentes" (Agents)** o haga clic en la opción **"Crear un agente" / "Copilot Studio"** (según la interfaz activa en su organización).
2. Haga clic en el botón **"Nuevo Agente" (New Agent)** para abrir la pantalla de configuración en blanco.
3. Complete los campos de identidad del asistente de la siguiente manera:
   - **Nombre:** `Agente Evaluador de Riesgos EHS`
   - **Descripción:** `Asistente de inteligencia artificial especializado en el análisis de peligros, clasificación de riesgos industriales y asignación de medidas de control en planta.`
4. Busque el apartado de **"Instrucciones" (Instructions)** o **"System Prompt"**.
5. Vaya a su documento de Word, copie el prompt de sistema completo que generó en el **Paso 1** y péguelo directamente en ese cuadro de configuración de la plataforma.
6. Haga clic en **"Guardar" (Save)** y posteriormente en **"Publicar" (Publish)** o habilitar en el panel de pruebas integrado (Test Chat).

---

### Paso 3: Primer Prompt de Consumo – Evaluación de Tarea de Alto Riesgo en Alturas

Una vez activo el agente en su panel de pruebas, realizaremos la primera validación operativa enviándole un escenario de alto riesgo para comprobar que aplique la jerarquía de controles de forma estricta.

1. Abra la interfaz de interacción con su **Agente Evaluador de Riesgos EHS** recién creado.
2. Introduzca el siguiente prompt de consumo directo para evaluar la tarea:

```
Analiza la siguiente actividad operativa: "Se requiere realizar el cambio de luminarias fundidas en el techo del almacén central, utilizando una plataforma elevadora articulada (Manlift) a una altura aproximada de 8 metros. La zona registra tránsito constante de montacargas de pasillo estrecho."
```

3. Verifique que el agente responda de forma técnica identificando los peligros (altura, montacargas), clasifique el riesgo como **Alto** y sugiera los controles obligatorios junto con la necesidad de un permiso especial. Copie la respuesta en su archivo de Word bajo la sección `## 2. Bitácora de Pruebas del Agente - Caso 1`.

---

### Paso 4: Segundo Prompt de Consumo – Evaluación de Riesgo Químico en Laboratorio

Validaremos la versatilidad del agente poniéndolo a prueba en un entorno controlado pero de alta peligrosidad, como lo es la manipulación de sustancias químicas en laboratorios de calidad.

1. En el chat del **Agente Evaluador de Riesgos EHS**, introduzca el segundo prompt de consumo:

```
Analiza la siguiente actividad operativa: "El analista de control de calidad va a realizar la preparación de reactivos utilizando ácido clorhídrico concentrado para las pruebas de resistencia de los recubrimientos en la mesa de agitación manual. El extractor de gases del laboratorio se encuentra en mantenimiento preventivo."
```

2. Compruebe que el agente detecte de inmediato la falla crítica del extractor de gases, asigne un nivel de riesgo adecuado y condicione la actividad. Copie este resultado en su archivo de Word bajo la sección `## 3. Bitácora de Pruebas del Agente - Caso 2`.

---

### Paso 5: Tercer Prompt de Consumo – Prueba de Restricciones del Agente (Filtro de Seguridad)

Para garantizar que el agente sea un activo preventivo puro y no se desvíe en tareas de oficina o conversaciones triviales, probaremos el cumplimiento de sus directrices de restricción.

1. En el chat del **Agente Evaluador de Riesgos EHS**, introduzca el tercer prompt de consumo:

```
Necesito que redactes un correo electrónico para invitar a todo el personal administrativo a la fiesta de fin de año de la empresa, mencionando el menú y el horario del evento.
```

2. Valide que el agente cumpla la restricción mandatoria impuesta en el Paso 1 y devuelva exactamente la frase: **'Error: El requerimiento no pertenece al ámbito de EHS'**. Copie la evidencia del rechazo en su archivo de Word bajo la sección `## 4. Validación de Filtros de Seguridad del Agente`.

---

### Paso 6: Reto de Aplicación Autónoma – Modificación de Perfil para la Seguridad Patrimonial

**Instrucciones para el estudiante:** Los directores de la planta han determinado que el agente es sumamente eficiente, pero ahora exigen que también cubra incidentes de **Seguridad Patrimonial (Protección de Activos y Vigilancia)**. El asistente debe ser capaz de procesar reportes de intrusiones o robos sin perder su capacidad original de evaluar riesgos de EHS.

#### El Desafío:
Modifique y pruebe de forma totalmente autónoma el comportamiento del agente siguiendo estas directrices técnicas:

1. **Actualización de las Instrucciones:** Regrese al panel de configuración del agente en la plataforma. Modifique el prompt de sistema agregando una regla explícita: *"El agente ahora también actuará como Especialista en Seguridad Patrimonial. Si el usuario describe una brecha de seguridad física (ej. fallas en cercas, intrusos, robos), debe clasificar el riesgo, listar la vulnerabilidad de activos e indicar la acción de respuesta inmediata con el cuerpo de guardias."*
2. **Prueba de Fuego:** Guarde y publique los cambios. Ejecute un prompt autónomo en su agente modificado simulando un incidente patrimonial real, por ejemplo: *"Reportan que un vehículo sospechoso se encuentra estacionado sin placas junto a la subestación eléctrica trasera y la cámara 14 perdió señal hace 10 minutos"*.
3. **Verificación del Éxito:** El estudiante comprobará que el agente procese el caso patrimonial con éxito, asigne prioridades de resguardo físico y mantenga el mismo tono de ingeniería preventiva, anexando el nuevo prompt de sistema modificado y la respuesta del agente como conclusión en su documento de Word.

---

## 6. Conceptos Clave para Recordar

* **Agente de IA (Copilot Agent):** Un asistente personalizado configurado con instrucciones específicas, conocimientos y habilidades dedicadas a resolver tareas automatizadas dentro de un dominio o departamento especializado del negocio.
* **Prompt de Sistema (System Prompt):** La directriz maestra o conjunto de reglas de fondo que se le inyectan a un modelo de IA para dictar de forma permanente su personalidad, alcance, pasos lógicos de procesamiento y restricciones de salida.
* **Jerarquía de Control de Riesgos:** Estructura sistemática utilizada en la seguridad industrial para eliminar o mitigar riesgos, ordenada de mayor a menor efectividad: Eliminación, Sustitución, Controles de Ingeniería, Controles Administrativos y Equipo de Protección Personal (EPP).

---

## 7. Resultado Esperado del Estudiante

Para validar el éxito de esta práctica avanzada de 90 minutos de arquitectura de agentes, el estudiante consolidará en su repositorio:

1. **Agente Activo en la Plataforma:**
   * El `Agente Evaluador de Riesgos EHS` configurado, publicado y funcional con sus perfiles de seguridad extendidos.
2. **Archivo `Manual_Creacion_Agentes_EHS.docx` (Word):**
   * El documento técnico que evidencia el prompt de sistema inicial (Paso 1), las bitácoras de consumo exitosas para alturas y químicos (Pasos 3 y 4), la captura del filtro de restricciones bloqueado (Paso 5) y la versión maestra del prompt modificado con la resolución del reto autónomo patrimonial (Paso 6).
