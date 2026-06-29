# Práctica 6 — Creación de un Page Básico para Registrar Incidentes de Seguridad

## Metadatos

| Campo            | Detalle                                      |
|------------------|----------------------------------------------|
| **Duración**     | 90 minutos                                   |
| **Complejidad**  | Media                                        |
| **Nivel Bloom**  | Aplicar (Apply)                              |
| **Módulo**       | 6 — Interfaces de Notebook y Scripts Interactivos para EHS |
| **Práctica**     | 06-00-01                                     |
| **Prerrequisito**| Lab 05 — Agente EHS Risk Evaluator creado    |

---

## Descripción General

En esta práctica ampliarás el agente **EHS Risk Evaluator** creado en el Módulo 5 añadiéndole una funcionalidad central: un flujo conversacional estructurado (page/topic) que guíe al usuario paso a paso en el registro de un incidente de seguridad. Siguiendo el mismo principio de trazabilidad y captura estructurada que ofrecen las interfaces de notebook —donde cada celda documenta un paso del proceso de forma reproducible y auditable—, construirás en Copilot Studio un formulario conversacional que recopile, valide y resuma los datos de incidentes de manera consistente. Al finalizar, el agente será capaz de recibir reportes de al menos dos tipos distintos de incidentes, aplicar lógica de ramificación según el tipo y presentar al usuario un resumen estructurado antes de cerrar el registro.

---

## Objetivos de Aprendizaje

Al finalizar esta práctica serás capaz de:

- [ ] Diseñar el flujo conversacional de un formulario de registro de incidentes, identificando campos obligatorios, opciones categóricas y puntos de ramificación lógica.
- [ ] Construir un topic/page en Copilot Studio con nodos de pregunta, variables de agente y opciones de selección múltiple para capturar datos de incidentes de seguridad.
- [ ] Implementar lógica condicional (branching) que adapte las preguntas del agente según el tipo de incidente reportado (accidente con lesión vs. daño material).
- [ ] Generar un nodo de confirmación que muestre al usuario un resumen estructurado del incidente registrado antes de finalizar el flujo.
- [ ] Verificar el correcto funcionamiento del flujo mediante pruebas end-to-end con al menos dos escenarios de incidente distintos.

---

## Prerrequisitos

### Conocimiento Previo

| Tema | Nivel Requerido |
|------|----------------|
| Creación y configuración de agentes en Copilot Studio (Módulo 5) | Completado |
| Concepto de topics/pages y nodos de pregunta en Copilot Studio | Básico |
| Variables de agente y almacenamiento de respuestas en Copilot Studio | Básico |
| Lógica conversacional y flujos de ramificación | Conceptual |
| Interfaces de notebook y estructuración de datos EHS (Lección 6.1) | Revisado |

### Accesos y Licencias Requeridos

| Recurso | Estado Requerido |
|---------|-----------------|
| Licencia Microsoft 365 Copilot activa | ✅ Activa |
| Acceso a Copilot Studio (`https://copilotstudio.microsoft.com`) | ✅ Con rol *Environment Maker* |
| Agente **EHS Risk Evaluator** del Módulo 5 disponible para edición | ✅ Guardado en el entorno |
| Entorno de Power Platform habilitado por el administrador | ✅ Configurado |
| Conexión a Internet estable (mínimo 10 Mbps) | ✅ Verificada |

> ⚠️ **Importante — Datos ficticios:** Durante toda la práctica utiliza exclusivamente datos ficticios o anonimizados. Está estrictamente prohibido ingresar información personal real de empleados, datos confidenciales de la empresa o información sensible de seguridad en los prompts o variables del agente.

---

## Entorno de Laboratorio

### Hardware Recomendado

| Componente | Mínimo | Recomendado |
|------------|--------|-------------|
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 | Intel Core i7 / AMD Ryzen 7 |
| RAM | 8 GB | 16 GB |
| Resolución de pantalla | 1920×1080 | Doble monitor 1920×1080 |
| Conexión a Internet | 10 Mbps | 25 Mbps o superior |

### Software Utilizado en Esta Práctica

| Aplicación | Uso en el Lab |
|------------|---------------|
| Microsoft Copilot Studio (web) | Construcción del topic/page de registro de incidentes |
| Microsoft Edge (navegador) | Acceso a Copilot Studio y pruebas del agente |
| Microsoft Teams (opcional) | Canal de publicación del agente para pruebas |

### Configuración Inicial — Verificación del Entorno

Antes de comenzar los pasos del laboratorio, realiza las siguientes verificaciones:

**1. Verificar acceso a Copilot Studio:**
```
1. Abre Microsoft Edge.
2. Navega a: https://copilotstudio.microsoft.com
3. Inicia sesión con tu cuenta corporativa de Microsoft 365.
4. Confirma que puedes ver el listado de agentes de tu entorno.
```

**2. Verificar disponibilidad del agente del Módulo 5:**
```
1. En Copilot Studio, haz clic en "Agents" (panel izquierdo).
2. Localiza el agente "EHS Risk Evaluator".
3. Confirma que su estado es "Published" o "Draft editable".
4. Si no aparece, solicita al instructor el archivo de checkpoint del Módulo 5.
```

**3. Abrir el agente para edición:**
```
1. Haz clic sobre "EHS Risk Evaluator".
2. Selecciona "Edit" o "Open in Studio".
3. Confirma que se abre el canvas de edición del agente.
```

---

## Instrucciones Paso a Paso

---

### Etapa 1 — Diseño del Formulario Conversacional (15 minutos)

**Objetivo:** Planificar en papel (o en un documento de texto) el flujo conversacional completo antes de implementarlo en Copilot Studio. Esta etapa es equivalente a la fase de diseño de un notebook: documentar el razonamiento antes de escribir código.

---

#### Paso 1.1 — Identificar los Campos del Formulario de Incidente

**Instrucciones:**

1. Abre un documento nuevo en Microsoft Word o una hoja en blanco de papel.
2. Copia y completa la siguiente tabla de campos del formulario de incidente. Estos serán los datos que el agente recopilará en la conversación:

| # | Campo | Tipo de Dato | Opciones (si aplica) | ¿Obligatorio? |
|---|-------|-------------|----------------------|---------------|
| 1 | Fecha del incidente | Fecha (texto libre) | — | Sí |
| 2 | Hora del incidente | Hora (texto libre) | — | Sí |
| 3 | Área de la planta | Selección múltiple | Producción, Almacén, Mantenimiento, Oficinas, Área exterior | Sí |
| 4 | Tipo de incidente | Selección múltiple | Accidente con lesión, Incidente sin lesión, Daño material, Casi-accidente (near miss), Derrame ambiental | Sí |
| 5 | Descripción del incidente | Texto libre | — | Sí |
| 6 | Personas involucradas | Texto libre (nombres ficticios) | — | Sí |
| 7 | ¿Hubo lesiones reportadas? | Selección: Sí / No | — | Sí (si tipo = Accidente con lesión) |
| 8 | ¿Se brindó atención médica? | Selección: Sí / No | — | Solo si campo 7 = Sí |
| 9 | ¿Hubo daños materiales? | Selección: Sí / No | — | Sí (si tipo = Daño material) |
| 10 | Monto estimado del daño (USD) | Número (texto libre) | — | Solo si campo 9 = Sí |
| 11 | Acciones inmediatas tomadas | Texto libre | — | Sí |
| 12 | ¿Hubo testigos? | Selección: Sí / No | — | Sí |
| 13 | Nombre(s) de testigo(s) | Texto libre | — | Solo si campo 12 = Sí |

3. Revisa la tabla y confirma que comprendes qué campos son condicionales (aparecen solo si se cumple una condición previa). Marca con un asterisco (*) los campos condicionales.

**Resultado esperado:** Tabla de campos completada con anotaciones de condicionalidad. Este documento servirá como referencia durante la construcción en Copilot Studio.

**Verificación:** Confirma que tienes identificados al menos 3 campos condicionales (campos 8, 10 y 13) antes de continuar.

---

#### Paso 1.2 — Diseñar el Diagrama de Flujo Conversacional

**Instrucciones:**

1. En el mismo documento, dibuja (o describe textualmente) el flujo de ramificación principal del agente. Utiliza el siguiente esquema como guía:

```
[INICIO DEL TOPIC: "Registrar Incidente"]
        │
        ▼
[Pregunta 1] ¿Cuál es la fecha del incidente?
        │
        ▼
[Pregunta 2] ¿A qué hora ocurrió?
        │
        ▼
[Pregunta 3] ¿En qué área de la planta ocurrió?
(Opciones: Producción / Almacén / Mantenimiento / Oficinas / Área exterior)
        │
        ▼
[Pregunta 4] ¿Cuál es el tipo de incidente?
(Opciones: Accidente con lesión / Incidente sin lesión /
           Daño material / Near miss / Derrame ambiental)
        │
        ├─── Si "Accidente con lesión" ──►  [Rama A]
        │                                    ¿Hubo lesiones reportadas? (Sí/No)
        │                                    Si Sí → ¿Se brindó atención médica?
        │
        ├─── Si "Daño material" ──────────►  [Rama B]
        │                                    ¿Hubo daños materiales? (Sí/No)
        │                                    Si Sí → ¿Monto estimado del daño?
        │
        └─── Otros tipos ─────────────────►  [Flujo estándar sin ramas adicionales]
        │
        ▼ (todas las ramas convergen aquí)
[Pregunta 5] Describe brevemente el incidente.
        │
        ▼
[Pregunta 6] ¿Quiénes estuvieron involucrados? (nombres ficticios)
        │
        ▼
[Pregunta 7] ¿Qué acciones inmediatas se tomaron?
        │
        ▼
[Pregunta 8] ¿Hubo testigos? (Sí/No)
        │
        ├─── Si Sí → ¿Cuáles son sus nombres?
        │
        ▼
[NODO DE CONFIRMACIÓN]
Mostrar resumen completo del incidente registrado
        │
        ▼
[FIN DEL TOPIC]
```

2. Guarda el documento de diseño. Lo consultarás durante la construcción en Copilot Studio.

**Resultado esperado:** Diagrama de flujo textual o gráfico que muestra claramente los puntos de ramificación y la secuencia de preguntas.

**Verificación:** El flujo debe tener al menos 2 ramas condicionales claramente identificadas antes de proceder a la Etapa 2.

---

### Etapa 2 — Construcción del Topic en Copilot Studio (35 minutos)

**Objetivo:** Implementar el flujo conversacional diseñado en la Etapa 1 utilizando los nodos de pregunta, variables y opciones de selección de Copilot Studio.

---

#### Paso 2.1 — Crear un Nuevo Topic en el Agente EHS

**Instrucciones:**

1. En Copilot Studio, con el agente **EHS Risk Evaluator** abierto en modo edición, localiza el panel izquierdo.
2. Haz clic en **"Topics"** en el menú de navegación izquierdo.
3. Haz clic en el botón **"+ Add a topic"** (o **"+ Nuevo topic"**).
4. Selecciona la opción **"From blank"** (Desde cero).
5. En el campo **"Name"** (Nombre del topic), escribe exactamente:
   ```
   Registrar Incidente de Seguridad
   ```
6. En la sección **"Trigger phrases"** (Frases de activación), agrega las siguientes frases una por una (presiona Enter después de cada una):
   ```
   registrar incidente
   reportar incidente
   nuevo incidente
   quiero reportar un accidente
   registrar accidente
   reporte de seguridad
   ocurrió un incidente
   ```
7. Haz clic en **"Save"** para guardar el topic con las frases de activación.

**Resultado esperado:** El topic **"Registrar Incidente de Seguridad"** aparece en la lista de topics del agente con las 7 frases de activación configuradas.

**Verificación:** En la lista de topics, confirma que el nuevo topic aparece con el ícono de topic personalizado y que al hacer clic sobre él se abre el canvas de edición vacío.

---

#### Paso 2.2 — Configurar el Nodo de Bienvenida del Formulario

**Instrucciones:**

1. En el canvas del topic **"Registrar Incidente de Seguridad"**, localiza el nodo inicial **"Trigger"** (ya creado automáticamente con las frases de activación).
2. Haz clic en el botón **"+"** debajo del nodo Trigger para agregar el primer nodo.
3. Selecciona **"Send a message"** (Enviar un mensaje).
4. En el campo de texto del nodo, escribe el siguiente mensaje de bienvenida:
   ```
   Voy a guiarte en el registro de un incidente de seguridad. 
   Por favor, responde cada pregunta con la mayor precisión posible. 
   Recuerda utilizar únicamente datos ficticios o anonimizados durante esta práctica.
   
   Comencemos con la información básica del incidente. 🔐
   ```
5. Haz clic fuera del nodo para confirmar el texto.

**Resultado esperado:** El nodo de mensaje de bienvenida está conectado al nodo Trigger y muestra el texto configurado.

**Verificación:** El canvas muestra la secuencia: [Trigger] → [Send a message: bienvenida].

---

#### Paso 2.3 — Agregar Nodos de Pregunta para Datos Básicos (Campos 1–4)

**Instrucciones:**

Repite el siguiente proceso para cada uno de los 4 primeros campos del formulario:

**Campo 1 — Fecha del incidente:**

1. Haz clic en **"+"** debajo del nodo de bienvenida.
2. Selecciona **"Ask a question"** (Hacer una pregunta).
3. En el campo de la pregunta, escribe:
   ```
   ¿Cuál es la fecha en que ocurrió el incidente? (Ejemplo: 15/07/2025)
   ```
4. En **"Identify"** (Identificar), selecciona **"User's entire response"** (Respuesta completa del usuario).
5. En **"Save response as"** (Guardar respuesta como), haz clic en **"Create new variable"** y nómbrala:
   ```
   varFechaIncidente
   ```
6. Confirma el tipo de variable como **String (texto)**.

**Campo 2 — Hora del incidente:**

1. Agrega un nuevo nodo **"Ask a question"** debajo del anterior.
2. Pregunta:
   ```
   ¿A qué hora ocurrió el incidente? (Ejemplo: 14:30)
   ```
3. Variable: `varHoraIncidente` (tipo String)

**Campo 3 — Área de la planta (selección múltiple):**

1. Agrega un nuevo nodo **"Ask a question"**.
2. Pregunta:
   ```
   ¿En qué área de la planta ocurrió el incidente?
   ```
3. En **"Identify"**, selecciona **"Multiple choice options"** (Opciones de selección múltiple).
4. Agrega las siguientes opciones haciendo clic en **"+ New option"** para cada una:
   ```
   Producción
   Almacén
   Mantenimiento
   Oficinas
   Área exterior
   ```
5. Variable: `varAreaIncidente` (tipo String)

**Campo 4 — Tipo de incidente (selección múltiple):**

1. Agrega un nuevo nodo **"Ask a question"**.
2. Pregunta:
   ```
   ¿Cuál es el tipo de incidente que deseas registrar?
   ```
3. En **"Identify"**, selecciona **"Multiple choice options"**.
4. Agrega las opciones:
   ```
   Accidente con lesión
   Incidente sin lesión
   Daño material
   Casi-accidente (near miss)
   Derrame ambiental
   ```
5. Variable: `varTipoIncidente` (tipo String)

**Resultado esperado:** El canvas muestra una cadena de 5 nodos: [Trigger] → [Bienvenida] → [Fecha] → [Hora] → [Área] → [Tipo de incidente].

**Verificación:** Haz clic en cada nodo de pregunta y confirma que la variable correspondiente aparece correctamente nombrada en el campo **"Save response as"**.

---

#### Paso 2.4 — Agregar Nodos de Pregunta para Datos Descriptivos (Campos 5–7)

**Instrucciones:**

Continúa la cadena de nodos después del nodo de **Tipo de incidente** (estos nodos se agregan después de las ramas condicionales que crearás en el Paso 3.1; por ahora, agrégalos temporalmente en secuencia directa):

**Campo 5 — Descripción del incidente:**

1. Agrega un nodo **"Ask a question"** con el texto:
   ```
   Por favor, describe brevemente cómo ocurrió el incidente. 
   Incluye el contexto, las circunstancias y cualquier detalle relevante.
   ```
2. Identifica: **"User's entire response"**
3. Variable: `varDescripcionIncidente` (tipo String)

**Campo 6 — Personas involucradas:**

1. Agrega un nodo **"Ask a question"**:
   ```
   ¿Quiénes estuvieron involucrados en el incidente? 
   (Usa nombres ficticios como: Empleado A, Operario B, Supervisor C)
   ```
2. Variable: `varPersonasInvolucradas` (tipo String)

**Campo 7 — Acciones inmediatas:**

1. Agrega un nodo **"Ask a question"**:
   ```
   ¿Qué acciones inmediatas se tomaron después del incidente? 
   (Ejemplo: evacuación, primeros auxilios, cierre del área, notificación al supervisor)
   ```
2. Variable: `varAccionesInmediatas` (tipo String)

**Campo 8 — Testigos:**

1. Agrega un nodo **"Ask a question"**:
   ```
   ¿Hubo testigos del incidente?
   ```
2. En **"Identify"**, selecciona **"Multiple choice options"**.
3. Opciones: `Sí` / `No`
4. Variable: `varHuboTestigos` (tipo String)

**Resultado esperado:** El flujo principal tiene ahora 9 nodos en secuencia (sin contar aún las ramas condicionales).

**Verificación:** Recorre visualmente el canvas de arriba a abajo y confirma que todos los nodos están conectados en secuencia sin interrupciones.

---

### Etapa 3 — Lógica de Ramificación y Scripts de Confirmación (25 minutos)

**Objetivo:** Añadir la lógica condicional que adapta el flujo según el tipo de incidente reportado, y construir el nodo de confirmación final que muestra el resumen estructurado del incidente al usuario.

---

#### Paso 3.1 — Insertar Lógica Condicional Después del Nodo "Tipo de Incidente"

**Instrucciones:**

1. En el canvas, localiza el nodo **"Tipo de incidente"** (`varTipoIncidente`).
2. Haz clic en **"+"** debajo de ese nodo.
3. Selecciona **"Add a condition"** (Agregar una condición) o **"Branching"** según la versión de Copilot Studio disponible.
4. Se creará automáticamente una estructura de condición con ramas. Configura la **Rama A** (primera condición):
   - En el campo de condición, selecciona la variable: `varTipoIncidente`
   - Operador: **"is equal to"** (es igual a)
   - Valor: `Accidente con lesión`

5. Dentro de la **Rama A** (accidente con lesión), agrega los siguientes nodos:

   **Nodo A1 — Lesiones reportadas:**
   ```
   ¿Hubo lesiones físicas reportadas como resultado del accidente?
   ```
   - Opciones: `Sí` / `No`
   - Variable: `varHuboLesiones` (tipo String)

   **Nodo A2 — Atención médica (condicional dentro de Rama A):**
   - Agrega una condición: si `varHuboLesiones` es igual a `Sí`
   - Dentro de esa sub-rama, agrega:
   ```
   ¿Se brindó atención médica al lesionado? 
   (Ejemplo: primeros auxilios en planta, traslado a clínica, hospitalización)
   ```
   - Opciones: `Sí` / `No`
   - Variable: `varAtencionMedica` (tipo String)

6. Haz clic en **"+ Add branch"** (Agregar rama) para crear la **Rama B**:
   - Condición: `varTipoIncidente` es igual a `Daño material`

7. Dentro de la **Rama B** (daño material), agrega:

   **Nodo B1 — Daños materiales:**
   ```
   ¿Puedes confirmar que hubo daños a equipos, instalaciones o materiales?
   ```
   - Opciones: `Sí` / `No`
   - Variable: `varHuboDanoMaterial` (tipo String)

   **Nodo B2 — Monto estimado (condicional dentro de Rama B):**
   - Agrega una condición: si `varHuboDanoMaterial` es igual a `Sí`
   - Dentro de esa sub-rama, agrega:
   ```
   ¿Cuál es el monto estimado del daño material en USD? 
   (Ejemplo: 500, 1200, 3500 — usa valores ficticios)
   ```
   - Identifica: **"User's entire response"**
   - Variable: `varMontoEstimado` (tipo String)

8. Asegúrate de que ambas ramas (A y B) y la rama **"All other conditions"** (todos los demás tipos de incidente) converjan en un único punto de continuación del flujo. En Copilot Studio, esto se hace conectando el nodo de salida de cada rama al mismo nodo siguiente (el nodo de descripción del incidente, Campo 5).

**Resultado esperado:** El canvas muestra una estructura en forma de diamante: el nodo de tipo de incidente se bifurca en Rama A (accidente con lesión), Rama B (daño material) y rama por defecto, y todas convergen de nuevo antes del nodo de descripción.

**Verificación:** Haz clic en cada rama y confirma que:
- La Rama A contiene los nodos `varHuboLesiones` y (condicionalmente) `varAtencionMedica`.
- La Rama B contiene los nodos `varHuboDanoMaterial` y (condicionalmente) `varMontoEstimado`.
- La rama "All other conditions" está vacía o tiene solo un mensaje de transición.

---

#### Paso 3.2 — Agregar Lógica Condicional para Testigos

**Instrucciones:**

1. Localiza el nodo **"¿Hubo testigos?"** (`varHuboTestigos`) en el canvas.
2. Haz clic en **"+"** debajo de ese nodo.
3. Selecciona **"Add a condition"**.
4. Configura la condición:
   - Variable: `varHuboTestigos`
   - Operador: **"is equal to"**
   - Valor: `Sí`
5. Dentro de la rama **"Sí"**, agrega un nodo de pregunta:
   ```
   Por favor, indica el nombre o identificación de los testigos. 
   (Usa identificadores ficticios como: Testigo 1, Operario T-02)
   ```
   - Variable: `varNombresTestigos` (tipo String)
6. En la rama **"No"**, no agregues nodos adicionales (el flujo continúa directamente al nodo de confirmación).
7. Conecta ambas ramas al nodo de confirmación que crearás en el siguiente paso.

**Resultado esperado:** El nodo de testigos tiene una bifurcación: si hay testigos, captura sus nombres; si no, continúa directamente al resumen.

**Verificación:** Confirma que la variable `varNombresTestigos` solo aparece en la rama "Sí" del nodo de testigos.

---

#### Paso 3.3 — Construir el Nodo de Confirmación y Resumen

**Instrucciones:**

1. Después de la convergencia de las ramas de testigos, agrega un nodo **"Send a message"**.
2. En el campo de texto, construye el mensaje de resumen utilizando las variables capturadas. En Copilot Studio, las variables se insertan con la sintaxis `{NombreVariable}` o usando el botón **"Insert variable"**:

   Escribe el siguiente mensaje (inserta cada variable usando el selector de variables del editor):
   ```
   ✅ RESUMEN DEL INCIDENTE REGISTRADO
   ─────────────────────────────────────
   📅 Fecha: {varFechaIncidente}
   🕐 Hora: {varHoraIncidente}
   📍 Área: {varAreaIncidente}
   ⚠️ Tipo de incidente: {varTipoIncidente}
   
   📝 Descripción:
   {varDescripcionIncidente}
   
   👥 Personas involucradas: {varPersonasInvolucradas}
   🚑 Acciones inmediatas: {varAccionesInmediatas}
   ─────────────────────────────────────
   El reporte ha sido registrado exitosamente. 
   Un supervisor EHS revisará este incidente en las próximas 24 horas.
   ```

   > **Nota técnica:** Para insertar variables en el mensaje, haz clic en el ícono **{x}** o **"Insert variable"** dentro del editor del nodo de mensaje. Busca cada variable por su nombre y selecciónala. Copilot Studio la insertará con la sintaxis correcta según la versión de la plataforma.

3. Después del nodo de resumen, agrega un último nodo **"Send a message"** con el mensaje de cierre:
   ```
   ¿Hay algo más en lo que pueda ayudarte relacionado con seguridad EHS?
   ```

4. Haz clic en **"Save"** para guardar todos los cambios del topic.

**Resultado esperado:** El canvas termina con un nodo de resumen que muestra todas las variables capturadas en formato estructurado, seguido de un mensaje de cierre.

**Verificación:** Revisa el nodo de resumen y confirma que todas las variables (`varFechaIncidente`, `varHoraIncidente`, `varAreaIncidente`, `varTipoIncidente`, `varDescripcionIncidente`, `varPersonasInvolucradas`, `varAccionesInmediatas`) aparecen referenciadas correctamente en el texto del mensaje.

---

#### Paso 3.4 — Guardar y Publicar el Agente Actualizado

**Instrucciones:**

1. En la barra superior de Copilot Studio, haz clic en **"Save"** (Guardar) para guardar el topic completo.
2. Confirma que no aparecen errores de validación en el canvas (los errores se muestran con íconos rojos sobre los nodos problemáticos).
3. Si aparecen advertencias (íconos amarillos), revisa el nodo indicado y corrige la configuración.
4. Una vez sin errores, haz clic en **"Publish"** (Publicar) en la barra superior.
5. En el diálogo de confirmación, haz clic en **"Publish"** nuevamente.
6. Espera a que aparezca el mensaje de confirmación: *"Your agent has been published successfully"* (o equivalente en español).

**Resultado esperado:** El agente **EHS Risk Evaluator** está publicado con el nuevo topic **"Registrar Incidente de Seguridad"** activo.

**Verificación:** En la lista de topics del agente, confirma que **"Registrar Incidente de Seguridad"** aparece con estado **"On"** (activo).

---

### Etapa 4 — Pruebas End-to-End del Flujo Completo (15 minutos)

**Objetivo:** Verificar el correcto funcionamiento del topic de registro de incidentes mediante pruebas con dos escenarios distintos de incidente, validando que los datos se capturan correctamente y que el resumen final es coherente.

---

#### Paso 4.1 — Prueba de Escenario 1: Accidente con Lesión

**Instrucciones:**

1. En Copilot Studio, localiza el panel de **"Test your agent"** (Probar tu agente) en el lado derecho de la pantalla. Si no está visible, haz clic en **"Test"** en la barra superior.
2. En el panel de chat de prueba, escribe la frase de activación:
   ```
   registrar incidente
   ```
3. Sigue el flujo respondiendo con los siguientes datos ficticios de prueba:

   | Pregunta del Agente | Respuesta de Prueba |
   |---------------------|---------------------|
   | Fecha del incidente | `22/07/2025` |
   | Hora del incidente | `09:15` |
   | Área de la planta | `Producción` |
   | Tipo de incidente | `Accidente con lesión` |
   | ¿Hubo lesiones físicas? | `Sí` |
   | ¿Se brindó atención médica? | `Sí` |
   | Descripción del incidente | `Empleado A sufrió una caída al resbalarse en el piso mojado cerca de la línea de ensamblaje 3. No había señalización de piso húmedo en el área.` |
   | Personas involucradas | `Empleado A (Operario), Supervisor B` |
   | Acciones inmediatas | `Se brindaron primeros auxilios, se trasladó al empleado a la clínica interna, se señalizó el área y se limpió el derrame.` |
   | ¿Hubo testigos? | `Sí` |
   | Nombres de testigos | `Testigo 1, Testigo 2` |

4. Verifica que el agente muestra el **resumen estructurado** al final con todos los datos ingresados.
5. Toma una **captura de pantalla** del resumen final del agente.

**Resultado esperado:**
```
✅ RESUMEN DEL INCIDENTE REGISTRADO
─────────────────────────────────────
📅 Fecha: 22/07/2025
🕐 Hora: 09:15
📍 Área: Producción
⚠️ Tipo de incidente: Accidente con lesión

📝 Descripción:
Empleado A sufrió una caída al resbalarse en el piso mojado...

👥 Personas involucradas: Empleado A (Operario), Supervisor B
🚑 Acciones inmediatas: Se brindaron primeros auxilios...
─────────────────────────────────────
El reporte ha sido registrado exitosamente.
Un supervisor EHS revisará este incidente en las próximas 24 horas.
```

**Verificación:**
- [ ] El agente realizó las preguntas de la Rama A (lesiones y atención médica).
- [ ] El resumen muestra todos los campos con los datos ingresados.
- [ ] No hubo interrupciones ni errores en el flujo.
- [ ] El mensaje de cierre aparece correctamente al final.

---

#### Paso 4.2 — Prueba de Escenario 2: Daño Material

**Instrucciones:**

1. En el panel de prueba, haz clic en **"Reset"** o **"New conversation"** (Nueva conversación) para reiniciar el chat.
2. Escribe la frase de activación:
   ```
   quiero reportar un accidente
   ```
3. Sigue el flujo con los siguientes datos ficticios de prueba para el segundo escenario:

   | Pregunta del Agente | Respuesta de Prueba |
   |---------------------|---------------------|
   | Fecha del incidente | `23/07/2025` |
   | Hora del incidente | `16:45` |
   | Área de la planta | `Almacén` |
   | Tipo de incidente | `Daño material` |
   | ¿Confirmas daños a equipos? | `Sí` |
   | Monto estimado del daño | `2500` |
   | Descripción del incidente | `Un montacargas colisionó con una estantería metálica en el pasillo B del almacén, causando el derrumbe parcial de la estructura y daños en 3 cajas de producto terminado.` |
   | Personas involucradas | `Operario C (conductor del montacargas), Coordinador D` |
   | Acciones inmediatas | `Se acordonó el área, se notificó a mantenimiento para evaluación estructural y se suspendió el uso del pasillo B.` |
   | ¿Hubo testigos? | `No` |

4. Verifica que el agente **no** preguntó sobre lesiones ni atención médica (esas preguntas son exclusivas de la Rama A).
5. Verifica que el agente **sí** preguntó sobre daños materiales y monto estimado (Rama B).
6. Confirma que el resumen final es coherente con los datos ingresados.
7. Toma una **captura de pantalla** del resumen final.

**Resultado esperado:** El agente ejecutó el flujo de la Rama B correctamente, capturando el monto estimado del daño, y generó un resumen estructurado sin las preguntas de lesiones.

**Verificación:**
- [ ] El agente NO preguntó sobre lesiones físicas ni atención médica en este escenario.
- [ ] El agente SÍ preguntó sobre daños materiales y monto estimado.
- [ ] El agente NO preguntó por nombres de testigos (respuesta fue "No").
- [ ] El resumen final es coherente y completo.

---

## Validación y Verificación Final

Antes de dar por completada la práctica, verifica cada uno de los siguientes criterios de aceptación:

### Lista de Verificación Final

| # | Criterio de Aceptación | Estado |
|---|------------------------|--------|
| 1 | El topic **"Registrar Incidente de Seguridad"** existe en el agente EHS Risk Evaluator y está activo (On). | ☐ |
| 2 | El topic tiene al menos 5 frases de activación configuradas. | ☐ |
| 3 | Se crearon y nombraron correctamente al menos 8 variables de agente (`varFechaIncidente`, `varHoraIncidente`, `varAreaIncidente`, `varTipoIncidente`, `varDescripcionIncidente`, `varPersonasInvolucradas`, `varAccionesInmediatas`, `varHuboTestigos`). | ☐ |
| 4 | Los campos de área y tipo de incidente utilizan nodos de selección múltiple (no texto libre). | ☐ |
| 5 | Existe lógica condicional que activa preguntas de lesiones/atención médica solo cuando el tipo es "Accidente con lesión". | ☐ |
| 6 | Existe lógica condicional que activa preguntas de daño material/monto solo cuando el tipo es "Daño material". | ☐ |
| 7 | Existe lógica condicional que pregunta por nombres de testigos solo cuando la respuesta es "Sí". | ☐ |
| 8 | El nodo de confirmación final muestra un resumen con todas las variables capturadas. | ☐ |
| 9 | La Prueba del Escenario 1 (accidente con lesión) se completó sin errores y el resumen es correcto. | ☐ |
| 10 | La Prueba del Escenario 2 (daño material) se completó sin errores y el resumen es correcto. | ☐ |
| 11 | El agente fue publicado exitosamente después de los cambios. | ☐ |
| 12 | Se tomaron capturas de pantalla de ambos resúmenes de prueba. | ☐ |

**Criterio de aprobación:** Todos los ítems deben estar marcados como completados (☐ → ✅) para considerar la práctica aprobada.

---

## Resolución de Problemas

### Problema 1 — Las variables no aparecen en el nodo de resumen o muestran texto vacío

**Síntoma:** Al ejecutar la prueba del agente, el nodo de confirmación final muestra el texto del resumen pero los valores de las variables aparecen en blanco, como `{varFechaIncidente}` sin sustituir, o el campo aparece vacío donde debería estar el dato ingresado por el usuario.

**Causa:** Este problema ocurre generalmente por una de dos razones: (a) la variable fue creada con un nombre diferente al referenciado en el nodo de mensaje (por ejemplo, la variable se llama `varFecha` pero en el mensaje se insertó `varFechaIncidente`), o (b) la variable fue declarada en el scope incorrecto y no es accesible desde el nodo de resumen (esto puede ocurrir si la variable se creó dentro de una rama condicional y se intenta usar fuera de ella).

**Solución:**
```
1. Abre el nodo de resumen y haz clic en cada referencia de variable.
2. Verifica que el nombre mostrado coincide exactamente con el nombre de la variable 
   definida en el nodo de pregunta correspondiente (incluyendo mayúsculas/minúsculas).
3. Si hay discrepancia, elimina la referencia incorrecta y usa el botón 
   "Insert variable" para seleccionar la variable correcta de la lista.
4. Para variables creadas dentro de ramas condicionales (como varAtencionMedica 
   o varMontoEstimado): verifica en las propiedades de la variable que su scope 
   esté configurado como "Global" o "Topic-level", no "Branch-level".
5. Guarda y republica el agente, luego repite la prueba.
```

---

### Problema 2 — El agente no activa el topic "Registrar Incidente de Seguridad" y responde con el topic de fallback

**Síntoma:** Al escribir frases como "registrar incidente" o "quiero reportar un accidente" en el panel de prueba, el agente responde con un mensaje genérico del tipo "No entendí tu solicitud, ¿puedes reformularla?" o activa un topic diferente (por ejemplo, el topic de evaluación de riesgos del Módulo 5) en lugar del nuevo topic de registro.

**Causa:** Este comportamiento ocurre cuando (a) las frases de activación del nuevo topic son demasiado similares a las frases de otro topic existente y Copilot Studio asigna mayor puntuación de confianza al topic anterior, o (b) el topic fue guardado pero no publicado, por lo que el agente en prueba sigue ejecutando la versión anterior publicada.

**Solución:**
```
1. VERIFICAR PUBLICACIÓN:
   - En Copilot Studio, confirma que después de guardar el topic hiciste clic 
     en "Publish" y esperaste el mensaje de confirmación de publicación exitosa.
   - En el panel de prueba, haz clic en "Reset" y luego en "Refresh" para 
     cargar la versión más reciente del agente publicado.

2. VERIFICAR FRASES DE ACTIVACIÓN:
   - Abre el topic "Registrar Incidente de Seguridad" y revisa las frases 
     de activación configuradas.
   - Asegúrate de que existen al menos 5-7 frases variadas y específicas.
   - Agrega frases adicionales más específicas si es necesario:
     "quiero registrar un incidente de seguridad"
     "reportar accidente en planta"
     "nuevo reporte EHS"

3. VERIFICAR CONFLICTOS CON OTROS TOPICS:
   - Revisa los topics del Módulo 5 y confirma que sus frases de activación 
     no incluyen "registrar" o "reportar incidente".
   - Si hay conflicto, edita las frases del topic anterior para hacerlas 
     más específicas y distintas.

4. USAR EL PANEL DE DIAGNÓSTICO:
   - En el panel de prueba, activa la opción "Track between topics" 
     (si está disponible) para ver qué topic está siendo seleccionado 
     y con qué puntuación de confianza.
```

---

## Limpieza del Entorno

Al finalizar la práctica, realiza las siguientes acciones para mantener el entorno ordenado:

**1. Guardar capturas de pantalla de evidencia:**
```
1. Confirma que tienes guardadas las capturas de pantalla de:
   - El canvas del topic "Registrar Incidente de Seguridad" con el flujo completo visible.
   - El resumen del Escenario 1 (accidente con lesión) en el panel de prueba.
   - El resumen del Escenario 2 (daño material) en el panel de prueba.
2. Guarda las capturas en tu carpeta de OneDrive del curso:
   /CursoEHS_Copilot/Modulo6/Lab06-00-01/
```

**2. Verificar el estado del agente:**
```
1. Confirma que el agente "EHS Risk Evaluator" está publicado y activo.
2. Confirma que el topic "Registrar Incidente de Seguridad" tiene estado "On".
3. NO elimines ni desactives ningún topic: el agente se usará en prácticas 
   posteriores (Módulos 7 y 8).
```

**3. Limpiar el historial del panel de prueba:**
```
1. En el panel de prueba de Copilot Studio, haz clic en "Reset" 
   para limpiar el historial de la conversación de prueba.
2. Cierra el panel de prueba.
```

**4. Cerrar sesión (si aplica):**
```
1. Si estás en un equipo compartido o de laboratorio, cierra la sesión 
   en Copilot Studio haciendo clic en tu avatar de usuario (esquina 
   superior derecha) y seleccionando "Sign out".
2. Cierra el navegador Microsoft Edge.
```

> ⚠️ **Recordatorio de privacidad:** Confirma que ningún dato real de empleados, datos confidenciales de la empresa o información sensible fue ingresado durante las pruebas. Todos los datos utilizados deben ser ficticios o anonimizados.

---

## Resumen

En esta práctica construiste una funcionalidad central del agente **EHS Risk Evaluator**: un flujo conversacional estructurado para el registro interactivo de incidentes de seguridad. Aplicando el mismo principio de trazabilidad y captura estructurada de las interfaces de notebook —donde cada celda documenta un paso del proceso de forma reproducible—, implementaste en Copilot Studio un formulario conversacional que guía al usuario paso a paso, valida la información mediante selecciones categóricas y adapta dinámicamente las preguntas según el tipo de incidente reportado.

### Conceptos Clave Aplicados

| Concepto | Aplicación en Esta Práctica |
|----------|----------------------------|
| **Interfaces de notebook** (Lección 6.1) | Analogía con la estructura de celdas secuenciales y documentación de cada paso del proceso de captura |
| **Topics/Pages en Copilot Studio** | Creación del topic "Registrar Incidente de Seguridad" como unidad modular del agente |
| **Variables de agente** | 8+ variables para almacenar los datos del incidente durante la conversación |
| **Nodos de pregunta con selección múltiple** | Campos categóricos para área y tipo de incidente, garantizando consistencia de datos |
| **Lógica de ramificación (branching)** | Flujo adaptativo según tipo de incidente (Rama A: lesión; Rama B: daño material) |
| **Nodo de confirmación/resumen** | Generación de un resumen estructurado y auditable al finalizar el registro |
| **Trazabilidad de datos** | El resumen final permite verificar que todos los campos fueron capturados correctamente |

### Habilidades Desarrolladas

Al completar esta práctica, eres capaz de:
- ✅ Diseñar flujos conversacionales estructurados para captura de datos EHS.
- ✅ Implementar variables y lógica condicional en Copilot Studio.
- ✅ Construir interfaces conversacionales que generen salidas auditables y reproducibles.
- ✅ Probar y validar flujos de agente con escenarios múltiples.

### Conexión con la Siguiente Práctica

En la **Práctica 7 (Módulo 7)**, integrarás el agente EHS Risk Evaluator con **Power Automate** para que los datos de incidentes registrados a través de este formulario conversacional sean automáticamente enviados a una lista de SharePoint, generando un registro persistente y auditable. El topic que construiste hoy será el punto de entrada de ese flujo automatizado.

---

### Recursos Adicionales

| Recurso | URL |
|---------|-----|
| Documentación oficial de Copilot Studio — Topics y Pages | https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-create-edit-topics |
| Variables en Copilot Studio | https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-variables |
| Lógica condicional y ramificación en Copilot Studio | https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-using-conditions |
| Mejores prácticas de diseño conversacional (UX) | https://learn.microsoft.com/es-es/microsoft-copilot-studio/guidance/conversational-design |
| ISO 45001:2018 — Gestión de seguridad y salud en el trabajo | https://www.iso.org/standard/63787.html |

---
