# Práctica 8 — Simulación de un Flujo Interconectado EHS-Operaciones para Auditorías

## Metadatos del Laboratorio

| Atributo | Detalle |
|---|---|
| **Duración estimada** | 90 minutos |
| **Complejidad** | Alta (Hard) |
| **Nivel Bloom** | Aplicar (Apply) |
| **Módulo** | 8 — Integración Multi-Agente y Flujos Interconectados |
| **Práctica** | 8 (Laboratorio de consolidación final del curso) |

---

## Descripción General

Este laboratorio es el **punto de consolidación final del curso**: todos los componentes construidos en los módulos anteriores convergen en un único flujo de trabajo coherente que simula una auditoría de seguridad en planta. Los participantes diseñarán e implementarán la comunicación entre dos agentes de Copilot Studio (el agente EHS ya existente y un nuevo agente de Operaciones), orquestarán el intercambio de datos mediante Power Automate y generarán automáticamente un reporte integrado con Microsoft Word + Copilot.

El flujo completo sigue el patrón de **orquestación centralizada** estudiado en la Lección 8.1: el agente EHS detecta y clasifica hallazgos de auditoría, Power Automate actúa como orquestador que enriquece los datos con contexto operativo y los entrega al agente de Operaciones, y el ciclo se cierra cuando Operaciones confirma las acciones correctivas y Copilot en Word genera el reporte final integrado.

> ⚠️ **Aviso importante sobre privacidad:** Durante toda esta práctica, utilice **exclusivamente datos ficticios o anonimizados**. Está estrictamente prohibido ingresar información personal real de empleados, datos confidenciales de la empresa o información sensible de seguridad en los prompts de Copilot o en los agentes de Copilot Studio.

---

## Objetivos de Aprendizaje

Al finalizar este laboratorio, el participante será capaz de:

- [ ] Diseñar e implementar un modelo de comunicación entre dos agentes de Copilot Studio (EHS y Operaciones) que simule un flujo real de auditoría en planta, aplicando los patrones de orquestación y pub/sub estudiados en la Lección 8.1.
- [ ] Configurar un agente de Operaciones en Copilot Studio que reciba, procese y responda a los hallazgos generados por el agente EHS, incluyendo enriquecimiento bidireccional de datos con contexto operativo (turno activo, supervisor, estado del equipo).
- [ ] Implementar en Power Automate el flujo de orquestación inter-agentes que gestiona el ciclo completo: registro de hallazgo → análisis → notificación → respuesta operativa → confirmación de cierre.
- [ ] Ejecutar una simulación completa de auditoría con al menos 3 hallazgos de distinta criticidad y generar automáticamente con Copilot en Word un reporte integrado que consolide hallazgos EHS, respuestas operativas y estado de cierre.

---

## Prerequisitos

### Conocimientos Previos

| Requisito | Descripción |
|---|---|
| Módulos 1–7 completados | Todas las prácticas anteriores deben estar finalizadas satisfactoriamente |
| Agente EHS Risk Evaluator funcional | El agente debe tener la página de registro de incidentes y la integración de correo operativas |
| Comprensión de modelos inter-agente | Haber revisado el material de la Lección 8.1 (pub/sub, request/response, orquestación centralizada) |
| Flujos de Power Automate previos | Familiaridad con la creación y edición de flujos desde módulos anteriores |

### Accesos y Licencias Requeridos

| Recurso | Estado requerido |
|---|---|
| Licencia Microsoft 365 Copilot activa | ✅ Verificada antes del laboratorio |
| Acceso a Copilot Studio | ✅ Rol "Environment Maker" asignado |
| Acceso a Power Automate | ✅ Entorno de Power Platform habilitado |
| Microsoft Word con Copilot habilitado | ✅ Archivo guardado en OneDrive/SharePoint |
| SharePoint Online — Biblioteca de práctica | ✅ Configurada por el instructor con archivos de práctica |
| Microsoft Outlook | ✅ Cuenta corporativa activa (datos ficticios) |

> 🔑 **Recordatorio crítico:** Copilot en Word, Excel y PowerPoint **solo funciona con archivos almacenados en OneDrive o SharePoint**. No guarde archivos en el disco local durante esta práctica.

---

## Entorno del Laboratorio

### Hardware Mínimo Recomendado

| Componente | Especificación mínima | Recomendado |
|---|---|---|
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 | Intel Core i7 / Ryzen 7 |
| RAM | 8 GB | 16 GB (múltiples pestañas abiertas) |
| Pantalla | 1920×1080 | Monitor secundario para comparar agentes |
| Conexión | 10 Mbps estable | 25 Mbps o superior |
| Almacenamiento libre | 10 GB | 15 GB |

### Software y Servicios Utilizados

| Aplicación | URL / Acceso | Rol en el laboratorio |
|---|---|---|
| Microsoft Copilot Studio | https://copilotstudio.microsoft.com | Creación del agente de Operaciones |
| Microsoft Power Automate | https://make.powerautomate.com | Orquestación del flujo inter-agentes |
| Microsoft SharePoint Online | Biblioteca del curso (URL provista por instructor) | Repositorio compartido de datos |
| Microsoft Word + Copilot | Aplicación de escritorio / OneDrive | Reporte integrado final |
| Microsoft Outlook | Aplicación de escritorio / Web | Notificaciones del flujo |
| Microsoft Teams | Aplicación de escritorio / Web | Canal de notificaciones (opcional) |

### Configuración Inicial del Entorno

Antes de comenzar los pasos del laboratorio, ejecute las siguientes verificaciones:

**1. Verificar acceso a Copilot Studio y el agente EHS existente:**

```
1. Abra https://copilotstudio.microsoft.com en Microsoft Edge.
2. Confirme que puede ver el agente "EHS Risk Evaluator" creado en módulos anteriores.
3. Verifique que el agente está en estado "Publicado" (Published).
```

**2. Verificar la biblioteca de SharePoint de práctica:**

```
1. Navegue a la biblioteca de SharePoint del curso (URL provista por el instructor).
2. Confirme que existen las siguientes carpetas:
   - /Hallazgos_Auditoria/
   - /Datos_Operaciones/
   - /Reportes_Integrados/
3. Si alguna carpeta no existe, créela antes de continuar.
```

**3. Preparar el archivo de datos operativos ficticios:**

Cree en SharePoint (`/Datos_Operaciones/`) un archivo llamado `contexto_operativo_ficticio.json` con el siguiente contenido de referencia (datos completamente ficticios):

```json
{
  "turnos": [
    {
      "id_turno": "T-001",
      "nombre": "Turno Matutino",
      "horario": "06:00 - 14:00",
      "supervisor_ficticio": "Ing. Carlos Mendoza (FICTICIO)",
      "areas_responsables": ["Línea A", "Almacén 1", "Taller de Mantenimiento"]
    },
    {
      "id_turno": "T-002",
      "nombre": "Turno Vespertino",
      "horario": "14:00 - 22:00",
      "supervisor_ficticio": "Ing. Laura Vásquez (FICTICIO)",
      "areas_responsables": ["Línea B", "Almacén 2", "Área de Carga"]
    }
  ],
  "equipos_criticos": [
    {
      "id_equipo": "EQ-101",
      "nombre": "Compresor Principal",
      "area": "Sala de Máquinas",
      "estado": "Operativo",
      "ultima_revision": "2025-06-01"
    },
    {
      "id_equipo": "EQ-205",
      "nombre": "Válvula de Presión V-205",
      "area": "Línea A",
      "estado": "Requiere inspección",
      "ultima_revision": "2025-04-15"
    }
  ]
}
```

---

## Pasos del Laboratorio

### Etapa 1: Diseño del Flujo Interconectado EHS-Operaciones

**Objetivo de la etapa:** Mapear visualmente el flujo completo de comunicación entre los agentes antes de implementarlo, asegurando que todos los participantes comprenden la arquitectura de orquestación que se construirá.

---

#### Paso 1.1 — Diagramar el Flujo de Comunicación Inter-Agentes

**Objetivo:** Crear un mapa del flujo completo que servirá como guía de implementación durante todo el laboratorio.

**Instrucciones:**

1. Abra un documento nuevo en **Microsoft Word** y guárdelo en SharePoint (`/Reportes_Integrados/`) con el nombre `Diseño_Flujo_EHS_Operaciones_[SusIniciales].docx`.

2. Inserte el siguiente diagrama de texto que representa la arquitectura de orquestación que implementará:

```
╔══════════════════════════════════════════════════════════════════╗
║          FLUJO INTERCONECTADO EHS-OPERACIONES (Diseño)          ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  [Auditor EHS]                                                   ║
║       │                                                          ║
║       ▼ (Registra hallazgo en agente)                           ║
║  [Agente EHS Risk Evaluator]                                     ║
║       │  Clasifica: CRÍTICO / ALTO / MEDIO                       ║
║       ▼                                                          ║
║  [Power Automate — ORQUESTADOR]                                  ║
║       │  Enriquece con: turno activo, supervisor,                ║
║       │  estado del equipo involucrado                           ║
║       ├──────────────────────────────────────────────┐           ║
║       ▼                                              ▼           ║
║  [Agente de Operaciones]                    [Notificación        ║
║       │  Recibe hallazgo enriquecido         Outlook al          ║
║       │  Asigna responsable                  supervisor]         ║
║       │  Propone acción correctiva                               ║
║       ▼                                                          ║
║  [Confirmación de Cierre → SharePoint]                           ║
║       │                                                          ║
║       ▼                                                          ║
║  [Copilot en Word — Reporte Integrado Final]                     ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

3. Debajo del diagrama, agregue una tabla con los **3 hallazgos ficticios** que simulará durante el laboratorio:

| # | Hallazgo (Ficticio) | Área | Criticidad | Equipo Involucrado |
|---|---|---|---|---|
| H-001 | Ausencia de señalización en zona de mezcla química | Almacén 1 | ALTO | N/A |
| H-002 | Válvula de presión V-205 sin revisión periódica | Línea A | CRÍTICO | EQ-205 |
| H-003 | EPP incompleto en operador de turno vespertino | Área de Carga | MEDIO | N/A |

4. Guarde el documento. Este archivo será la referencia durante todo el laboratorio.

**Resultado esperado:** Documento Word guardado en SharePoint con el diagrama de flujo y la tabla de hallazgos ficticios.

**Verificación:** El archivo aparece en la biblioteca SharePoint en la carpeta `/Reportes_Integrados/` y es accesible desde el navegador.

---

### Etapa 2: Creación del Agente de Operaciones en Copilot Studio

**Objetivo de la etapa:** Configurar un segundo agente especializado en gestión de hallazgos operativos que pueda recibir datos del agente EHS, asignar responsables y proponer acciones correctivas.

---

#### Paso 2.1 — Crear el Nuevo Agente de Operaciones

**Objetivo:** Crear y configurar el agente "Operaciones Safety Responder" en Copilot Studio.

**Instrucciones:**

1. Navegue a **https://copilotstudio.microsoft.com** y haga clic en **"Crear"** (Create) en el panel lateral izquierdo.

2. Seleccione **"Nuevo agente"** (New agent). Cuando se le solicite el nombre, ingrese:
   ```
   Nombre del agente: Operaciones Safety Responder
   ```

3. En el campo de descripción, ingrese:
   ```
   Agente especializado en la gestión operativa de hallazgos de seguridad detectados 
   durante auditorías EHS en planta. Recibe hallazgos clasificados, asigna responsables 
   de turno, propone acciones correctivas y registra el cierre de cada hallazgo. 
   Opera con datos ficticios de práctica.
   ```

4. Haga clic en **"Crear"** para generar el agente base.

5. Una vez creado, navegue a la sección **"Instrucciones"** (Instructions / System Prompt) del agente. Reemplace las instrucciones predeterminadas con el siguiente texto:

```
Eres el Agente de Operaciones Safety Responder de la Planta Industrial Ficticia "Planta Demo EHS".

TU ROL:
- Recibes hallazgos de seguridad clasificados por el agente EHS Risk Evaluator.
- Asignas un responsable operativo basándote en el turno activo y el área del hallazgo.
- Propones acciones correctivas específicas y realistas para cada hallazgo.
- Registras el estado de cierre de cada acción correctiva.
- Comunicas de forma clara y directa, usando terminología de operaciones industriales.

REGLAS IMPORTANTES:
- Todos los datos que manejas son FICTICIOS y de práctica. Nunca solicites ni proceses datos reales de empleados.
- Cuando recibas un hallazgo CRÍTICO, siempre propones una acción inmediata (plazo máximo 4 horas) y una acción correctiva de largo plazo.
- Para hallazgos ALTOS, el plazo de acción inmediata es 24 horas.
- Para hallazgos MEDIOS, el plazo es 72 horas.
- Siempre confirmas la recepción del hallazgo con un número de ticket ficticio en formato: OPS-YYYY-NNN

CONTEXTO OPERATIVO DISPONIBLE:
- Turno Matutino (06:00-14:00): Supervisor ficticio Ing. Carlos Mendoza
- Turno Vespertino (14:00-22:00): Supervisor ficticio Ing. Laura Vásquez
- Turno Nocturno (22:00-06:00): Supervisor ficticio Ing. Roberto Sánchez

FORMATO DE RESPUESTA:
Cuando recibas un hallazgo, responde siempre con esta estructura:
1. TICKET ASIGNADO: [número ficticio]
2. HALLAZGO RECIBIDO: [resumen del hallazgo]
3. CRITICIDAD: [nivel]
4. RESPONSABLE ASIGNADO: [supervisor del turno activo]
5. ACCIÓN INMEDIATA: [descripción + plazo]
6. ACCIÓN CORRECTIVA: [descripción + plazo]
7. ESTADO: PENDIENTE DE CIERRE
```

6. Haga clic en **"Guardar"** para preservar la configuración del agente.

**Resultado esperado:** El agente "Operaciones Safety Responder" aparece en la lista de agentes de Copilot Studio con estado "Guardado" y las instrucciones configuradas.

**Verificación:** Haga clic en **"Probar"** (Test) en el panel derecho e ingrese el siguiente mensaje de prueba:
```
Hallazgo H-001: Ausencia de señalización en zona de mezcla química. Área: Almacén 1. Criticidad: ALTO. Turno activo: Matutino.
```
El agente debe responder con un ticket ficticio (ej. OPS-2025-001), asignar al supervisor ficticio del turno matutino y proponer acciones con plazos de 24 horas.

---

#### Paso 2.2 — Configurar el Tema de Recepción de Hallazgos

**Objetivo:** Crear un tema (topic) específico en el agente de Operaciones que estructure la recepción y procesamiento de hallazgos provenientes del agente EHS.

**Instrucciones:**

1. En el agente "Operaciones Safety Responder", navegue a la sección **"Temas"** (Topics) en el menú lateral.

2. Haga clic en **"Agregar tema"** → **"Desde cero"** (Add topic → From blank).

3. Configure el tema con los siguientes datos:
   ```
   Nombre del tema: Recepción de Hallazgo EHS
   Frases de activación (Trigger phrases):
   - "hallazgo recibido"
   - "nuevo hallazgo EHS"
   - "auditoría detectó"
   - "registrar hallazgo operaciones"
   - "hallazgo crítico"
   - "hallazgo alto"
   - "hallazgo medio"
   ```

4. En el canvas del tema, agregue los siguientes nodos en secuencia:

   **Nodo 1 — Mensaje de confirmación:**
   ```
   Tipo: Enviar un mensaje
   Texto: "✅ Hallazgo recibido por el área de Operaciones. Procesando asignación de responsable y acciones correctivas..."
   ```

   **Nodo 2 — Preguntar por datos del hallazgo (si no vienen del flujo automático):**
   ```
   Tipo: Hacer una pregunta
   Pregunta: "Por favor confirma el ID del hallazgo para el registro:"
   Guardar respuesta en variable: varIDHallazgo
   ```

   **Nodo 3 — Mensaje de cierre del tema:**
   ```
   Tipo: Enviar un mensaje
   Texto: "Hallazgo {varIDHallazgo} registrado en el sistema de Operaciones. El responsable de turno ha sido notificado. Ticket asignado automáticamente."
   ```

5. Haga clic en **"Guardar"** el tema.

**Resultado esperado:** El tema "Recepción de Hallazgo EHS" aparece en la lista de temas del agente con estado activo.

**Verificación:** En el panel de prueba, escriba "nuevo hallazgo EHS" y verifique que el agente activa el tema correcto y solicita el ID del hallazgo.

---

#### Paso 2.3 — Obtener el Endpoint del Agente de Operaciones

**Objetivo:** Obtener la URL del endpoint del agente de Operaciones para configurar la comunicación desde Power Automate.

**Instrucciones:**

1. Con el agente "Operaciones Safety Responder" abierto, haga clic en **"Publicar"** (Publish) en la esquina superior derecha.

2. Confirme la publicación cuando se le solicite. Espere a que el estado cambie a **"Publicado"**.

3. Navegue a **"Configuración"** (Settings) → **"Canales"** (Channels) → **"API de Bot Framework"** o **"Direct Line"**.

4. Copie y guarde en un bloc de notas la siguiente información (la necesitará en la Etapa 3):
   ```
   URL del endpoint / Token endpoint: [copiar aquí]
   ID del Bot: [copiar aquí]
   ```

   > 📝 **Nota:** Si el entorno no muestra Direct Line, navegue a **"Configuración"** → **"Seguridad"** → **"Secreto de Direct Line"** y genere un nuevo secreto. Guarde este secreto de forma segura.

5. Anote también el **Environment ID** de Power Platform (visible en la URL del navegador cuando está en Copilot Studio):
   ```
   URL ejemplo: https://copilotstudio.microsoft.com/environments/[ENVIRONMENT-ID]/bots/[BOT-ID]
   Environment ID: [copiar aquí]
   ```

**Resultado esperado:** Tiene registrados el endpoint, el ID del bot y el secreto de Direct Line del agente de Operaciones.

**Verificación:** El agente aparece como "Publicado" en el dashboard de Copilot Studio.

---

### Etapa 3: Implementación del Flujo de Comunicación Inter-Agentes en Power Automate

**Objetivo de la etapa:** Crear el flujo orquestador en Power Automate que conecta el agente EHS con el agente de Operaciones, enriquece los datos con contexto operativo y gestiona las notificaciones.

---

#### Paso 3.1 — Crear el Flujo Orquestador Principal

**Objetivo:** Construir el flujo de Power Automate que actúa como orquestador centralizado del ciclo EHS-Operaciones, implementando el modelo de orquestación centralizada de la Lección 8.1.

**Instrucciones:**

1. Navegue a **https://make.powerautomate.com** y asegúrese de estar en el entorno correcto de Power Platform.

2. Haga clic en **"Crear"** → **"Flujo de nube automatizado"** (Automated cloud flow).

3. Nombre el flujo:
   ```
   Nombre: Orquestador_EHS_Operaciones_Auditoria
   ```

4. Para el **desencadenador** (trigger), seleccione:
   ```
   Conector: SharePoint
   Disparador: "Cuando se crea un elemento" (When an item is created)
   Sitio: [URL de la biblioteca SharePoint del curso]
   Lista: Hallazgos_Auditoria
   ```
   > 📝 **Nota:** Si la lista "Hallazgos_Auditoria" no existe aún en SharePoint, deberá crearla en el siguiente paso antes de continuar.

5. **Crear la lista de SharePoint** (si no existe): Abra SharePoint en otra pestaña, navegue a la biblioteca del curso y cree una nueva lista llamada `Hallazgos_Auditoria` con las siguientes columnas:

   | Nombre de columna | Tipo |
   |---|---|
   | ID_Hallazgo | Línea de texto única |
   | Descripcion | Varias líneas de texto |
   | Area | Línea de texto única |
   | Criticidad | Opción (CRÍTICO, ALTO, MEDIO) |
   | Equipo_Involucrado | Línea de texto única |
   | Turno_Activo | Línea de texto única |
   | Estado | Opción (PENDIENTE, EN PROCESO, CERRADO) |
   | Ticket_Operaciones | Línea de texto única |

6. Regrese a Power Automate. Después del desencadenador de SharePoint, agregue los siguientes pasos en orden:

**Paso A — Condición: Determinar turno activo por hora:**
```
Tipo de acción: Condición (Condition)
Condición: formatDateTime(utcNow(), 'HH') >= 6 AND formatDateTime(utcNow(), 'HH') < 14
Rama SI (True): Establecer variable "supervisor_turno" = "Ing. Carlos Mendoza (FICTICIO) - Turno Matutino"
Rama NO (False): Establecer variable "supervisor_turno" = "Ing. Laura Vásquez (FICTICIO) - Turno Vespertino"
```

> Para implementar esto correctamente, primero agregue una acción **"Inicializar variable"** antes de la condición:
> ```
> Nombre: supervisor_turno
> Tipo: String
> Valor inicial: ""
> ```

**Paso B — Obtener datos del equipo involucrado (enriquecimiento de datos):**
```
Tipo de acción: Condición (Condition)
Condición: triggerBody()?['Equipo_Involucrado'] is not empty
Rama SI (True): 
  - Agregar acción: "Obtener elemento" de SharePoint
  - Lista: Equipos_Criticos (o leer del JSON de contexto operativo)
  - Guardar resultado en variable: datos_equipo
```

**Paso C — Componer el payload enriquecido:**
```
Tipo de acción: Redactar / Componer (Compose)
Nombre: payload_enriquecido
Entradas (Expression):
{
  "id_hallazgo": "@{triggerBody()?['ID_Hallazgo']}",
  "descripcion": "@{triggerBody()?['Descripcion']}",
  "area": "@{triggerBody()?['Area']}",
  "criticidad": "@{triggerBody()?['Criticidad']}",
  "equipo_involucrado": "@{triggerBody()?['Equipo_Involucrado']}",
  "turno_activo": "@{triggerBody()?['Turno_Activo']}",
  "supervisor_responsable": "@{variables('supervisor_turno')}",
  "timestamp_deteccion": "@{utcNow()}",
  "origen": "Agente EHS Risk Evaluator",
  "estado_inicial": "PENDIENTE"
}
```

7. Guarde el flujo haciendo clic en **"Guardar"** en la parte superior.

**Resultado esperado:** El flujo aparece guardado en Power Automate con el desencadenador de SharePoint configurado y los primeros pasos de enriquecimiento de datos.

**Verificación:** El flujo aparece en el listado de "Mis flujos" con estado "Activado" (On).

---

#### Paso 3.2 — Agregar la Notificación a Operaciones y el Registro en SharePoint

**Objetivo:** Completar el flujo orquestador agregando la notificación por correo al supervisor de turno y el registro del ticket de Operaciones en SharePoint.

**Instrucciones:**

1. Abra el flujo `Orquestador_EHS_Operaciones_Auditoria` para editarlo.

2. Después del paso "Componer payload enriquecido", agregue los siguientes pasos:

**Paso D — Enviar notificación por correo (Outlook):**
```
Tipo de acción: Office 365 Outlook — Enviar un correo electrónico (V2)
Para: [correo ficticio de práctica del participante, ej. su propio correo]
Asunto: [HALLAZGO @{triggerBody()?['Criticidad']}] @{triggerBody()?['ID_Hallazgo']} — Acción requerida en @{triggerBody()?['Area']}
Cuerpo:
Estimado/a @{variables('supervisor_turno')},

Se ha registrado el siguiente hallazgo de seguridad que requiere atención operativa:

📋 ID Hallazgo: @{triggerBody()?['ID_Hallazgo']}
📍 Área: @{triggerBody()?['Area']}
⚠️ Criticidad: @{triggerBody()?['Criticidad']}
📝 Descripción: @{triggerBody()?['Descripcion']}
🔧 Equipo involucrado: @{triggerBody()?['Equipo_Involucrado']}
🕐 Turno activo: @{triggerBody()?['Turno_Activo']}

Por favor, acceda al Agente de Operaciones Safety Responder para registrar las acciones correctivas.

Este es un correo generado automáticamente por el sistema de gestión EHS (datos ficticios de práctica).
```

**Paso E — Generar número de ticket de Operaciones:**
```
Tipo de acción: Redactar / Componer (Compose)
Nombre: ticket_operaciones
Entradas: concat('OPS-2025-', rand(100, 999))
```

**Paso F — Actualizar el elemento en SharePoint con el ticket asignado:**
```
Tipo de acción: SharePoint — Actualizar elemento (Update item)
Sitio: [URL de la biblioteca SharePoint del curso]
Lista: Hallazgos_Auditoria
ID: triggerBody()?['ID']
Ticket_Operaciones: outputs('ticket_operaciones')
Estado: EN PROCESO
```

**Paso G — Guardar el payload completo en SharePoint para el reporte final:**
```
Tipo de acción: SharePoint — Crear elemento (Create item)
Sitio: [URL de la biblioteca SharePoint del curso]
Lista: Crear una nueva lista llamada "Registro_Flujo_Auditoria" con columnas:
  - ID_Hallazgo (Texto)
  - Payload_Completo (Texto multilínea)
  - Ticket_Operaciones (Texto)
  - Timestamp (Fecha y hora)
  - Estado_Final (Texto)

Valores:
  ID_Hallazgo: triggerBody()?['ID_Hallazgo']
  Payload_Completo: string(outputs('payload_enriquecido'))
  Ticket_Operaciones: outputs('ticket_operaciones')
  Timestamp: utcNow()
  Estado_Final: "EN PROCESO"
```

3. Haga clic en **"Guardar"** el flujo completo.

**Resultado esperado:** El flujo orquestador completo está guardado con todos los pasos: enriquecimiento de datos, notificación por correo y registro en SharePoint.

**Verificación:** Revise el diagrama del flujo en Power Automate. Debe mostrar al menos 7 pasos/acciones conectadas secuencialmente desde el desencadenador hasta el registro final.

---

#### Paso 3.3 — Crear el Flujo de Confirmación de Cierre

**Objetivo:** Implementar el mecanismo de cierre del ciclo, donde Operaciones confirma que las acciones correctivas han sido ejecutadas.

**Instrucciones:**

1. En Power Automate, cree un **segundo flujo** de tipo "Flujo de nube instantáneo" (Instant cloud flow):
   ```
   Nombre: Cierre_Hallazgo_Operaciones
   Desencadenador: Desencadenar manualmente un flujo (Manually trigger a flow)
   ```

2. Configure las **entradas del desencadenador manual**:
   ```
   Entrada 1:
     Tipo: Texto
     Nombre: ID_Hallazgo
     Descripción: ID del hallazgo a cerrar (ej. H-001)
   
   Entrada 2:
     Tipo: Texto
     Nombre: Ticket_Operaciones
     Descripción: Número de ticket asignado (ej. OPS-2025-123)
   
   Entrada 3:
     Tipo: Texto
     Nombre: Descripcion_Accion_Correctiva
     Descripción: Descripción de la acción correctiva ejecutada
   
   Entrada 4:
     Tipo: Texto
     Nombre: Responsable_Cierre
     Descripción: Nombre ficticio del responsable que ejecutó la acción
   ```

3. Después del desencadenador, agregue los siguientes pasos:

**Paso A — Obtener el elemento de hallazgo en SharePoint:**
```
Tipo: SharePoint — Obtener elementos (Get items)
Lista: Hallazgos_Auditoria
Filtro: ID_Hallazgo eq '@{triggerBody()?['text']}'
```

**Paso B — Actualizar el estado a CERRADO:**
```
Tipo: SharePoint — Actualizar elemento
Lista: Hallazgos_Auditoria
Estado: CERRADO
```

**Paso C — Actualizar el registro en Registro_Flujo_Auditoria:**
```
Tipo: SharePoint — Actualizar elemento
Lista: Registro_Flujo_Auditoria
Estado_Final: "CERRADO"
Agregar columna nueva: Accion_Correctiva_Ejecutada = triggerBody()?['text_3']
Agregar columna nueva: Responsable_Cierre = triggerBody()?['text_4']
Agregar columna nueva: Timestamp_Cierre = utcNow()
```

**Paso D — Enviar correo de confirmación de cierre:**
```
Tipo: Office 365 Outlook — Enviar un correo electrónico (V2)
Para: [su correo de práctica]
Asunto: ✅ CERRADO — Hallazgo @{triggerBody()?['text']} | Ticket @{triggerBody()?['text_2']}
Cuerpo:
El hallazgo @{triggerBody()?['text']} ha sido cerrado satisfactoriamente.

Acción correctiva ejecutada: @{triggerBody()?['text_3']}
Responsable: @{triggerBody()?['text_4']}
Fecha de cierre: @{utcNow()}

Este registro ha sido actualizado en el sistema EHS para su inclusión en el reporte de auditoría.
(Datos ficticios de práctica)
```

4. Guarde el flujo `Cierre_Hallazgo_Operaciones`.

**Resultado esperado:** Dos flujos activos en Power Automate: `Orquestador_EHS_Operaciones_Auditoria` y `Cierre_Hallazgo_Operaciones`.

**Verificación:** Ambos flujos aparecen en "Mis flujos" con estado "Activado" y sin errores de configuración.

---

### Etapa 4: Simulación Completa y Generación del Reporte Integrado

**Objetivo de la etapa:** Ejecutar la simulación completa de auditoría con los 3 hallazgos ficticios, verificar el funcionamiento end-to-end del flujo y generar el reporte integrado final con Copilot en Word.

---

#### Paso 4.1 — Ejecutar la Simulación con los 3 Hallazgos Ficticios

**Objetivo:** Registrar los 3 hallazgos ficticios en la lista de SharePoint para activar el flujo orquestador y verificar que el ciclo completo funciona.

**Instrucciones:**

1. Navegue a la lista `Hallazgos_Auditoria` en SharePoint.

2. Haga clic en **"Nuevo"** (New) y registre el **Hallazgo H-001**:
   ```
   ID_Hallazgo: H-001
   Descripcion: Ausencia de señalización de riesgo en zona de mezcla de productos químicos. 
                No se observan carteles de peligro ni indicaciones de EPP requerido.
   Area: Almacén 1
   Criticidad: ALTO
   Equipo_Involucrado: (dejar vacío)
   Turno_Activo: Matutino
   Estado: PENDIENTE
   Ticket_Operaciones: (dejar vacío — se llenará automáticamente)
   ```

3. Guarde el elemento. **Espere 30-60 segundos** para que Power Automate procese el flujo.

4. Verifique en Power Automate (sección "Historial de ejecuciones" del flujo `Orquestador_EHS_Operaciones_Auditoria`) que el flujo se ejecutó correctamente. Cada paso debe mostrar un ícono verde ✅.

5. Revise su bandeja de entrada de Outlook para confirmar que llegó el correo de notificación del hallazgo H-001.

6. Repita los pasos 2-5 para el **Hallazgo H-002**:
   ```
   ID_Hallazgo: H-002
   Descripcion: Válvula de presión V-205 sin revisión periódica documentada. 
                Última revisión registrada: 15/04/2025. Supera el período máximo de 60 días.
   Area: Línea A
   Criticidad: CRÍTICO
   Equipo_Involucrado: EQ-205 — Válvula de Presión V-205
   Turno_Activo: Matutino
   Estado: PENDIENTE
   ```

7. Repita para el **Hallazgo H-003**:
   ```
   ID_Hallazgo: H-003
   Descripcion: Operador identificado como "Operador Demo 03 (FICTICIO)" trabajando sin 
                casco de seguridad en área de carga. EPP incompleto observado durante ronda de supervisión.
   Area: Área de Carga
   Criticidad: MEDIO
   Equipo_Involucrado: (dejar vacío)
   Turno_Activo: Vespertino
   Estado: PENDIENTE
   ```

8. Después de registrar los 3 hallazgos, confirme que:
   - Los 3 elementos en SharePoint tienen el campo `Ticket_Operaciones` llenado automáticamente (ej. OPS-2025-XXX).
   - Los 3 elementos tienen el estado actualizado a "EN PROCESO".
   - Recibió 3 correos de notificación en Outlook.

**Resultado esperado:** Los 3 hallazgos ficticios están registrados en SharePoint con tickets asignados, estados actualizados y correos de notificación enviados.

**Verificación:** En Power Automate → Historial de ejecuciones del flujo `Orquestador_EHS_Operaciones_Auditoria`, deben aparecer 3 ejecuciones exitosas (íconos verdes).

---

#### Paso 4.2 — Interactuar con el Agente de Operaciones para Procesar Hallazgos

**Objetivo:** Simular la interacción del supervisor de turno con el agente de Operaciones para procesar cada hallazgo y proponer acciones correctivas.

**Instrucciones:**

1. Abra el agente "Operaciones Safety Responder" en Copilot Studio y acceda al panel de **prueba** (Test).

2. Para el **Hallazgo H-002 (CRÍTICO)**, ingrese el siguiente mensaje en el panel de prueba:
   ```
   Hallazgo H-002 recibido. Criticidad: CRÍTICO. Área: Línea A. 
   Descripción: Válvula de presión V-205 sin revisión periódica. Equipo: EQ-205. 
   Turno activo: Matutino. Supervisor: Ing. Carlos Mendoza (FICTICIO).
   Ticket asignado: OPS-2025-[número generado]. 
   Por favor, proponer acciones correctivas.
   ```

3. Copie y guarde la respuesta completa del agente (ticket, responsable, acciones propuestas).

4. Repita para **H-001** y **H-003** con mensajes similares adaptados a cada hallazgo.

5. Para simular el **cierre de los hallazgos**, ejecute manualmente el flujo `Cierre_Hallazgo_Operaciones` desde Power Automate para cada hallazgo:
   - Haga clic en el flujo → **"Ejecutar"** (Run)
   - Complete las entradas con datos ficticios:
     ```
     Para H-001:
       ID_Hallazgo: H-001
       Ticket_Operaciones: OPS-2025-[número]
       Descripcion_Accion_Correctiva: Se instalaron señales de peligro y carteles de EPP requerido en zona de mezcla. Verificado por supervisor de turno.
       Responsable_Cierre: Operador Demo 01 (FICTICIO)
     
     Para H-002:
       ID_Hallazgo: H-002
       Ticket_Operaciones: OPS-2025-[número]
       Descripcion_Accion_Correctiva: Se realizó inspección y revisión de válvula V-205. Equipo certificado. Se programó revisión periódica en calendario de mantenimiento.
       Responsable_Cierre: Técnico Demo 02 (FICTICIO)
     
     Para H-003:
       ID_Hallazgo: H-003
       Ticket_Operaciones: OPS-2025-[número]
       Descripcion_Accion_Correctiva: Se proporcionó EPP completo al operador y se registró en bitácora de seguridad. Capacitación de refuerzo programada.
       Responsable_Cierre: Supervisor Demo 03 (FICTICIO)
     ```

6. Verifique que los 3 elementos en SharePoint (`Hallazgos_Auditoria` y `Registro_Flujo_Auditoria`) tienen el estado actualizado a **"CERRADO"** y que recibió los correos de confirmación de cierre.

**Resultado esperado:** Los 3 hallazgos ficticios están cerrados en SharePoint, con acciones correctivas registradas y correos de confirmación enviados.

**Verificación:** En la lista `Registro_Flujo_Auditoria` de SharePoint, los 3 registros muestran `Estado_Final = CERRADO` y tienen los campos `Accion_Correctiva_Ejecutada`, `Responsable_Cierre` y `Timestamp_Cierre` completos.

---

#### Paso 4.3 — Generar el Reporte Integrado Final con Copilot en Word

**Objetivo:** Utilizar Copilot en Word para generar automáticamente el reporte integrado de auditoría que consolide todos los hallazgos, respuestas operativas y estados de cierre.

**Instrucciones:**

1. Abra el documento `Diseño_Flujo_EHS_Operaciones_[SusIniciales].docx` que creó en el Paso 1.1 (guardado en SharePoint).

   > ⚠️ **Recordatorio:** El archivo debe estar en OneDrive o SharePoint para que Copilot funcione. No trabaje con copias locales.

2. Al final del documento, haga clic en una línea en blanco y luego haga clic en el ícono de **Copilot** en la barra de herramientas de Word (o presione `Alt + I` para abrir el panel de Copilot).

3. Ingrese el siguiente prompt en Copilot:

   ```
   Genera un reporte ejecutivo de auditoría de seguridad en planta con el siguiente 
   contenido estructurado:

   TÍTULO: Reporte de Auditoría de Seguridad — Simulación EHS-Operaciones
   FECHA: [fecha de hoy]
   PLANTA: Planta Demo EHS (datos ficticios de práctica)
   
   SECCIÓN 1 — RESUMEN EJECUTIVO:
   Escribe un párrafo de resumen que indique que se realizó una auditoría de seguridad 
   en la que se detectaron 3 hallazgos (1 crítico, 1 alto, 1 medio), todos cerrados 
   satisfactoriamente mediante el flujo automatizado EHS-Operaciones.
   
   SECCIÓN 2 — HALLAZGOS DETECTADOS:
   Crea una tabla con los siguientes 3 hallazgos ficticios:
   - H-001: Ausencia de señalización en Almacén 1 | Criticidad: ALTO | Área: Almacén 1
   - H-002: Válvula V-205 sin revisión en Línea A | Criticidad: CRÍTICO | Área: Línea A
   - H-003: EPP incompleto en Área de Carga | Criticidad: MEDIO | Área: Área de Carga
   
   SECCIÓN 3 — RESPUESTAS OPERATIVAS Y ACCIONES CORRECTIVAS:
   Para cada hallazgo, describe la acción correctiva ejecutada y el responsable ficticio.
   H-001: Instalación de señales y carteles EPP | Responsable: Operador Demo 01 (FICTICIO)
   H-002: Inspección y certificación de válvula V-205 | Responsable: Técnico Demo 02 (FICTICIO)
   H-003: Provisión de EPP y capacitación programada | Responsable: Supervisor Demo 03 (FICTICIO)
   
   SECCIÓN 4 — ESTADO DE CIERRE:
   Tabla de estado final de cada hallazgo con columnas: ID, Ticket Operaciones, Estado, 
   Fecha de Cierre. Todos los hallazgos deben mostrar estado CERRADO.
   
   SECCIÓN 5 — CONCLUSIONES Y RECOMENDACIONES:
   3 conclusiones sobre la efectividad del flujo automatizado EHS-Operaciones y 
   2 recomendaciones para mejorar el proceso en futuras auditorías.
   
   Usa un tono formal y profesional apropiado para un reporte ejecutivo de EHS industrial.
   Recuerda que todos los datos son ficticios y de práctica.
   ```

4. Haga clic en **"Generar"** y espere a que Copilot produzca el contenido.

5. Revise el contenido generado. Si alguna sección necesita ajustes, use el botón **"Regenerar"** o edite directamente el texto.

6. Una vez satisfecho con el reporte, haga clic en **"Conservar"** (Keep) para insertar el contenido en el documento.

7. Agregue manualmente al inicio del documento una **portada** con:
   ```
   REPORTE INTEGRADO DE AUDITORÍA
   Simulación Flujo EHS-Operaciones
   Módulo 8 — Laboratorio Final
   Fecha: [fecha actual]
   Elaborado por: [Su nombre ficticio o iniciales]
   DOCUMENTO DE PRÁCTICA — DATOS FICTICIOS
   ```

8. Guarde el documento final en SharePoint (`/Reportes_Integrados/`) con el nombre:
   ```
   Reporte_Integrado_Auditoria_Final_[SusIniciales].docx
   ```

**Resultado esperado:** Documento Word completo guardado en SharePoint con las 5 secciones del reporte integrado generadas por Copilot, incluyendo tablas de hallazgos, acciones correctivas y estado de cierre.

**Verificación:** El documento tiene al menos 3 páginas, contiene las 5 secciones indicadas, y está guardado correctamente en la carpeta `/Reportes_Integrados/` de SharePoint.

---

## Validación y Pruebas del Laboratorio

Antes de declarar el laboratorio completado, realice las siguientes verificaciones finales:

### Lista de Verificación Final

| # | Elemento a verificar | Criterio de éxito | ✅/❌ |
|---|---|---|---|
| 1 | Agente "Operaciones Safety Responder" | Publicado en Copilot Studio, responde correctamente a hallazgos de prueba | |
| 2 | Tema "Recepción de Hallazgo EHS" | Activo y funcional en el agente de Operaciones | |
| 3 | Flujo `Orquestador_EHS_Operaciones_Auditoria` | 3 ejecuciones exitosas en historial de Power Automate | |
| 4 | Flujo `Cierre_Hallazgo_Operaciones` | 3 ejecuciones exitosas, correos de confirmación recibidos | |
| 5 | Lista SharePoint `Hallazgos_Auditoria` | 3 elementos con estado CERRADO y tickets asignados | |
| 6 | Lista SharePoint `Registro_Flujo_Auditoria` | 3 registros con acciones correctivas y timestamps de cierre | |
| 7 | Correos de notificación | 3 correos de alerta + 3 correos de cierre recibidos en Outlook | |
| 8 | Reporte integrado en Word | Documento guardado en SharePoint con 5 secciones completas | |
| 9 | Privacidad de datos | Ningún dato real de empleados o información confidencial utilizada | |

### Prueba de Extremo a Extremo (End-to-End)

Para validar el flujo completo, ejecute una prueba final con un **cuarto hallazgo adicional** (opcional, si el tiempo lo permite):

```
ID_Hallazgo: H-004
Descripcion: Extintor de incendios vencido detectado en sala de control. 
             Fecha de vencimiento: 01/03/2025. Requiere reemplazo inmediato.
Area: Sala de Control
Criticidad: CRÍTICO
Equipo_Involucrado: (dejar vacío)
Turno_Activo: Nocturno
Estado: PENDIENTE
```

Verifique que el flujo completo se ejecuta en menos de **2 minutos** desde el registro en SharePoint hasta la recepción del correo de notificación.

---

## Solución de Problemas

### Problema 1: El flujo de Power Automate falla en el paso de SharePoint con error "Item not found" o "List does not exist"

**Síntomas:**
- El flujo `Orquestador_EHS_Operaciones_Auditoria` muestra un paso en rojo ❌ en el historial de ejecuciones.
- El error indica que no puede encontrar la lista `Hallazgos_Auditoria` o que el elemento no existe.
- Los elementos de SharePoint no se actualizan con el ticket de Operaciones.

**Causa probable:**
El conector de SharePoint en Power Automate está apuntando a una URL o nombre de lista incorrectos. Esto ocurre frecuentemente cuando la lista fue creada con un nombre ligeramente diferente (espacios, mayúsculas) o cuando el flujo fue configurado antes de que la lista existiera en SharePoint.

**Solución:**
1. Abra el flujo en modo edición en Power Automate.
2. Haga clic en el paso de SharePoint que falla.
3. Verifique que la **URL del sitio** coincide exactamente con la URL de la biblioteca SharePoint del curso (copie y pegue desde el navegador).
4. Verifique que el **nombre de la lista** coincide exactamente con `Hallazgos_Auditoria` (sensible a mayúsculas y espacios).
5. Si es necesario, elimine el paso y vuelva a configurarlo seleccionando la lista desde el desplegable (no escribiendo manualmente).
6. Guarde y ejecute una prueba manual del flujo con el botón "Probar" (Test) → "Manualmente" para confirmar que el paso funciona antes de registrar nuevos hallazgos.

---

### Problema 2: Copilot en Word no genera contenido o muestra el mensaje "Copilot no está disponible para este archivo"

**Síntomas:**
- Al hacer clic en el ícono de Copilot en Word, no aparece el panel o aparece con un mensaje de error.
- El botón de Copilot está deshabilitado (gris) en la barra de herramientas.
- Al ingresar el prompt, Copilot devuelve el mensaje "No puedo ayudarte con este archivo" o similar.

**Causa probable:**
El archivo de Word está guardado **localmente** en el disco duro del equipo, no en OneDrive o SharePoint. Copilot en las aplicaciones de Microsoft 365 (Word, Excel, PowerPoint) **solo funciona con archivos almacenados en la nube**. También puede ocurrir si la licencia de Copilot no está correctamente asignada al usuario, o si el archivo fue abierto desde una copia local descargada.

**Solución:**
1. Verifique la barra de título de Word: si muestra una ruta local como `C:\Users\...\` en lugar de una URL de SharePoint o OneDrive, el archivo está en local.
2. Haga clic en **Archivo** → **Guardar como** → **SharePoint** o **OneDrive** y navegue a la carpeta `/Reportes_Integrados/` de la biblioteca del curso.
3. Guarde el archivo en la nube y ciérrelo.
4. Vuelva a abrirlo **desde SharePoint** (navegue a la biblioteca en el navegador y haga clic en el archivo → Abrir en la aplicación de escritorio).
5. Espere 10-15 segundos para que la sincronización se complete y el botón de Copilot se active.
6. Si el problema persiste, verifique con el administrador de TI que la licencia de Copilot for Microsoft 365 está activa para su cuenta en el portal de administración de Microsoft 365.

---

## Limpieza del Entorno

Una vez completado y validado el laboratorio, realice las siguientes acciones de limpieza para mantener el entorno ordenado:

### Acciones de Limpieza

1. **Copilot Studio — Agente de Operaciones:**
   - El agente "Operaciones Safety Responder" puede mantenerse publicado para referencia futura del curso.
   - Si el instructor indica que debe eliminarse: navegue al agente → **Configuración** → **Eliminar agente** (confirme la eliminación).

2. **Power Automate — Flujos creados:**
   - Desactive (no elimine) los flujos para conservar el historial de ejecuciones como evidencia del laboratorio:
     - `Orquestador_EHS_Operaciones_Auditoria`: clic en el flujo → **Desactivar** (Turn off).
     - `Cierre_Hallazgo_Operaciones`: clic en el flujo → **Desactivar**.

3. **SharePoint — Datos de práctica:**
   - Las listas `Hallazgos_Auditoria` y `Registro_Flujo_Auditoria` pueden conservarse como evidencia del laboratorio.
   - Si el instructor indica limpieza completa, elimine los elementos de prueba (no las listas completas) para que otros participantes puedan usar el mismo entorno.

4. **Documentos en SharePoint:**
   - Conserve los siguientes archivos en sus carpetas correspondientes como evidencia de completación:
     - `/Reportes_Integrados/Diseño_Flujo_EHS_Operaciones_[SusIniciales].docx`
     - `/Reportes_Integrados/Reporte_Integrado_Auditoria_Final_[SusIniciales].docx`

5. **Correos en Outlook:**
   - Mueva los 6 correos generados durante el laboratorio (3 de notificación + 3 de cierre) a una carpeta llamada `Lab_08_EHS_Operaciones` en su Outlook para mantener la bandeja ordenada.

---

## Resumen del Laboratorio

### Lo que Construyó en Este Laboratorio

En este laboratorio de consolidación final, implementó un **flujo interconectado EHS-Operaciones** completo que integra todos los componentes del curso:

| Componente | Tecnología | Lo que implementó |
|---|---|---|
| Agente EHS | Copilot Studio (existente) | Punto de origen de los hallazgos de auditoría |
| Agente de Operaciones | Copilot Studio (nuevo) | Recepción, asignación y cierre de hallazgos |
| Orquestador | Power Automate | Enriquecimiento de datos y coordinación del flujo |
| Notificaciones | Outlook | Alertas automáticas al supervisor de turno |
| Repositorio compartido | SharePoint Online | Registro de hallazgos, tickets y cierres |
| Reporte integrado | Word + Copilot | Consolidación ejecutiva del ciclo de auditoría |

### Conceptos de la Lección 8.1 Aplicados

- ✅ **Modelo de orquestación centralizada:** Power Automate actuó como orquestador que dirigió el flujo completo entre el agente EHS y el agente de Operaciones, tal como se describió en la Lección 8.1.
- ✅ **Enriquecimiento de datos:** El payload que viajó entre agentes incluyó no solo el dato bruto del hallazgo, sino también contexto operativo (turno activo, supervisor responsable, estado del equipo), implementando el principio de enriquecimiento semántico.
- ✅ **Comunicación bidireccional:** El flujo no fue unidireccional (EHS → Operaciones) sino que incluyó el mecanismo de confirmación de cierre (Operaciones → registro compartido → reporte final), demostrando el modelo request/response para el ciclo de cierre.
- ✅ **Trazabilidad completa:** Cada hallazgo quedó registrado con timestamp, responsable y estado en SharePoint, proporcionando el nivel de auditoría que el modelo de orquestación centralizada garantiza.

### Recursos Adicionales

- [Documentación de Copilot Studio — Crear y publicar agentes](https://learn.microsoft.com/es-es/microsoft-copilot-studio/authoring-create-edit-topics)
- [Power Automate — Conectores de SharePoint](https://learn.microsoft.com/es-es/connectors/sharepointonline/)
- [Patrones de integración empresarial — Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/patterns/messaging/)
- [Microsoft Copilot en Word — Guía de prompts efectivos](https://support.microsoft.com/es-es/topic/bienvenido-a-copilot-en-word-2135e85f-a467-463b-b2f0-c51a46d625d1)
- [Arquitecturas de agentes de IA en Microsoft Azure](https://learn.microsoft.com/es-es/azure/architecture/ai-ml/guide/agentic-ai-patterns)
- [NOM-030-STPS-2009: Servicios preventivos de seguridad y salud en el trabajo](https://www.dof.gob.mx/nota_detalle.php?codigo=5120760&fecha=22/12/2009)

---

> 🎓 **¡Felicitaciones!** Ha completado el laboratorio de consolidación final del curso. El flujo interconectado EHS-Operaciones que implementó representa un modelo real y escalable de gestión de seguridad industrial asistida por IA, con todos los principios de privacidad, trazabilidad y cumplimiento normativo que caracterizan un uso responsable de Microsoft 365 Copilot en entornos corporativos.
