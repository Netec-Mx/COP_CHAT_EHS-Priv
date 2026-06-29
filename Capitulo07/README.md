---LAB_START---
LAB_ID: 07-00-01
---MARKDOWN---
# Práctica 7 — Conexión de Copilot para Enviar Reportes por Email

## 1. Metadatos

| Campo | Detalle |
|---|---|
| **Duración estimada** | 90 minutos |
| **Complejidad** | Alta (Hard) |
| **Nivel Bloom** | Aplicar (Apply) |
| **Módulo** | Módulo 7 — Integración de Agentes EHS con Correo Electrónico |
| **Prerequisito inmediato** | Prácticas 5 y 6 completadas (agente EHS funcional con flujo de registro de incidentes operativo) |

---

## 2. Descripción General

En esta práctica conectarás el agente EHS construido en los módulos anteriores con el sistema de correo electrónico corporativo de Microsoft 365, automatizando la comunicación de incidentes de seguridad industrial. Utilizarás **Power Automate** para construir un flujo que reciba los datos del incidente desde **Copilot Studio**, aplique lógica condicional según la severidad del evento y envíe correos electrónicos dinámicos a los destinatarios correctos a través del conector de **Outlook**. Al finalizar, habrás implementado un pipeline completo: el agente registra el incidente → dispara el flujo → se envía el correo → el equipo EHS recibe la notificación en tiempo real.

---

## 3. Objetivos de Aprendizaje

Al completar este laboratorio serás capaz de:

- [ ] Configurar un flujo de Power Automate disparado por un agente de Copilot Studio que envíe automáticamente reportes de incidentes por correo electrónico a los destinatarios correctos.
- [ ] Diseñar plantillas de correo electrónico dinámicas en HTML que incorporen los datos capturados por el agente (fecha, área, tipo, descripción, responsable y severidad).
- [ ] Implementar lógica de enrutamiento condicional en Power Automate para diferenciar entre alertas críticas y notificaciones de incidentes menores, asignando destinatarios y niveles de urgencia distintos.
- [ ] Integrar la acción de disparo del flujo dentro del agente EHS en Copilot Studio y ejecutar pruebas end-to-end del ciclo completo de notificación.

---

## 4. Prerrequisitos

### Conocimiento Previo

| Área | Nivel Requerido |
|---|---|
| Copilot Studio — creación de temas y variables | Completado (Prácticas 5 y 6) |
| Power Automate — interfaz básica y conectores | Familiaridad básica (material previo del Módulo 7) |
| Protocolos OAuth 2.0 y Microsoft Graph API | Comprensión conceptual (Lección 7.1) |
| Formato HTML básico para correos | Básico |
| Conceptos de EHS: severidad de incidentes | Completado en módulos anteriores |

### Accesos y Configuración Previa

| Recurso | Estado Requerido |
|---|---|
| Licencia Microsoft 365 Copilot activa | ✅ Verificada por TI |
| Acceso a Copilot Studio (`copilotstudio.microsoft.com`) | ✅ Rol "Environment Maker" asignado |
| Acceso a Power Automate (`make.powerautomate.com`) | ✅ Con permisos para crear flujos |
| Cuenta de Outlook corporativa | ✅ Con permisos para enviar correos desde flujos |
| Agente EHS de Prácticas 5 y 6 publicado y funcional | ✅ Operativo en el entorno de práctica |
| Archivos de práctica cargados en SharePoint | ✅ Cargados por el instructor |

> ⚠️ **Aviso de privacidad:** Durante toda la práctica utiliza **exclusivamente datos ficticios**. Está prohibido ingresar nombres reales de empleados, correos corporativos reales de personas identificables o información confidencial de la organización en los prompts del agente o en los flujos de Power Automate.

---

## 5. Entorno de Laboratorio

### Hardware Mínimo Recomendado

| Componente | Especificación |
|---|---|
| Procesador | Intel Core i5 8ª gen. / AMD Ryzen 5 o superior |
| RAM | 8 GB mínimo (16 GB recomendado) |
| Almacenamiento libre | 10 GB |
| Pantalla | 1920×1080 mínimo (monitor secundario recomendado) |
| Conexión a Internet | 10 Mbps mínimo estable |

### Software Requerido

| Aplicación | Versión / Acceso |
|---|---|
| Microsoft Edge (navegador recomendado) | Versión estable más reciente |
| Microsoft Copilot Studio | `https://copilotstudio.microsoft.com` |
| Microsoft Power Automate | `https://make.powerautomate.com` |
| Microsoft Outlook (web o desktop) | Incluido en Microsoft 365 |
| Microsoft Teams (para verificación opcional) | Versión empresarial actualizada |

### Configuración Inicial del Entorno

Antes de comenzar los pasos del laboratorio, realiza las siguientes verificaciones:

**1. Verifica que tu agente EHS está publicado:**
```
1. Abre https://copilotstudio.microsoft.com
2. Navega a tu agente EHS (creado en Prácticas 5 y 6)
3. Confirma que el estado muestra "Publicado" en la esquina superior
4. Prueba un mensaje rápido en el panel "Probar agente" para confirmar que responde
```

**2. Verifica acceso a Power Automate:**
```
1. Abre https://make.powerautomate.com en una pestaña nueva
2. Confirma que puedes ver la pantalla de inicio con "Mis flujos"
3. Verifica que el entorno seleccionado (esquina superior derecha) 
   coincide con el entorno de práctica asignado por el instructor
```

**3. Verifica el conector de Outlook:**
```
1. En Power Automate, ve a: Datos > Conexiones
2. Busca "Office 365 Outlook"
3. Si no existe una conexión, selecciona "+ Nueva conexión" 
   y autentica con tu cuenta corporativa de práctica
4. Confirma que el estado de la conexión muestra un ícono verde (activo)
```

---

## 6. Procedimiento Paso a Paso

El laboratorio está organizado en **cuatro etapas** que deben completarse en orden:

| Etapa | Actividad | Tiempo estimado |
|---|---|---|
| **A** | Diseño del flujo de comunicación | 10 min |
| **B** | Creación del flujo en Power Automate | 30 min |
| **C** | Diseño de plantillas de correo dinámicas | 20 min |
| **D** | Conexión e integración con Copilot Studio y pruebas | 30 min |

---

### Etapa A — Diseño del Flujo de Comunicación (10 minutos)

**Objetivo:** Antes de construir cualquier componente técnico, mapear el flujo de notificación completo para tener claridad sobre qué se envía, a quién y cuándo.

#### Instrucciones

**Paso A-1: Analiza el esquema de enrutamiento de notificaciones**

Estudia la siguiente tabla de enrutamiento que usarás durante toda la práctica. Este esquema define la lógica condicional que implementarás en Power Automate:

| Severidad del Incidente | Destinatarios Principales | Destinatarios en Copia (CC) | Asunto del Correo | Tiempo Máximo de Envío |
|---|---|---|---|---|
| **CRÍTICA** (Nivel 3) | `supervisor.turno@practicaehs.com` + `gerencia.ehs@practicaehs.com` | `direccion.planta@practicaehs.com` | ⚠️ ALERTA CRÍTICA EHS — [Área] — Acción Inmediata | Inmediato (< 1 min) |
| **ALTA** (Nivel 2) | `supervisor.turno@practicaehs.com` | `coordinador.ehs@practicaehs.com` | 🔶 Incidente de Alta Severidad EHS — [Área] | Inmediato (< 1 min) |
| **MEDIA / BAJA** (Nivel 1) | `coordinador.ehs@practicaehs.com` | — | 📋 Registro de Incidente EHS — [Área] | Inmediato (< 1 min) |

> **Nota:** Todos los correos en esta práctica usan direcciones ficticias del dominio `@practicaehs.com`. Nunca uses correos corporativos reales de personas identificables.

**Paso A-2: Identifica las variables del agente que alimentarán el correo**

Confirma que tu agente EHS de las prácticas anteriores captura y almacena las siguientes variables. Anótalas, ya que las usarás en Power Automate:

```
Variables requeridas del agente EHS (confirmar en Copilot Studio):
─────────────────────────────────────────────────────────────────
• varFechaIncidente      → Fecha y hora del incidente
• varAreaAfectada        → Área o sector donde ocurrió
• varTipoIncidente       → Categoría del incidente (caída, derrame, etc.)
• varDescripcion         → Descripción detallada del evento
• varResponsable         → Nombre del responsable del área (ficticio)
• varSeveridad           → Nivel de severidad: CRITICA / ALTA / MEDIA / BAJA
• varNumeroReporte       → Número de folio del reporte (ej. EHS-2024-0047)
```

**Paso A-3: Verifica las variables en Copilot Studio**

1. En Copilot Studio, abre tu agente EHS.
2. Ve a **Variables** (en el menú lateral o dentro del tema de registro de incidentes).
3. Confirma que las variables listadas arriba existen. Si alguna tiene un nombre diferente, anota el nombre real que usarás más adelante.
4. Si `varSeveridad` no existe en tu agente, créala ahora:
   - Tipo: **Texto**
   - Valor por defecto: `MEDIA`

#### Resultado Esperado

Al finalizar la Etapa A debes tener:
- El esquema de enrutamiento claro y anotado.
- La lista de variables del agente confirmada con sus nombres exactos.
- Claridad sobre qué condición determinará el tipo de correo a enviar.

#### Verificación

✅ Puedes responder estas preguntas sin dudar:
- ¿A quién se envía un incidente de severidad CRÍTICA?
- ¿Qué variable del agente contiene el nivel de severidad?
- ¿Cuántos destinatarios diferentes puede tener el flujo según el nivel?

---

### Etapa B — Creación del Flujo en Power Automate (30 minutos)

**Objetivo:** Construir el flujo de Power Automate que recibirá los datos del incidente desde Copilot Studio, aplicará lógica condicional y preparará el envío del correo.

#### Instrucciones

**Paso B-1: Crea un nuevo flujo de nube instantáneo**

1. Abre `https://make.powerautomate.com`.
2. En el menú lateral, selecciona **Mis flujos**.
3. Haz clic en **+ Nuevo flujo** → **Flujo de nube instantáneo**.
4. En el cuadro de diálogo:
   - **Nombre del flujo:** `Flujo_Notificacion_EHS_Incidentes`
   - En "¿Cómo desencadenar este flujo?": selecciona **Cuando Copilot Studio llama a un flujo** (conector de Power Virtual Agents / Copilot Studio).
5. Haz clic en **Crear**.

> ℹ️ **Si no encuentras el desencadenador:** Busca "Power Virtual Agents" en el buscador de desencadenadores. En algunos entornos aparece como "Run a flow from Copilot Studio" o "Power Virtual Agents — When a flow is called from a bot".

**Paso B-2: Configura las entradas del desencadenador**

El desencadenador de Copilot Studio permite definir los parámetros de entrada que el agente enviará al flujo. Configura las siguientes entradas:

1. En el bloque del desencadenador, haz clic en **Agregar una entrada**.
2. Agrega **cada una** de las siguientes entradas (tipo **Texto** para todas):

```
Entrada 1:
  - Nombre de entrada: FechaIncidente
  - Descripción: Fecha y hora del incidente registrado

Entrada 2:
  - Nombre de entrada: AreaAfectada
  - Descripción: Área o sector donde ocurrió el incidente

Entrada 3:
  - Nombre de entrada: TipoIncidente
  - Descripción: Categoría del incidente (caída, derrame, etc.)

Entrada 4:
  - Nombre de entrada: Descripcion
  - Descripción: Descripción detallada del evento

Entrada 5:
  - Nombre de entrada: Responsable
  - Descripción: Nombre del responsable del área

Entrada 6:
  - Nombre de entrada: Severidad
  - Descripción: Nivel de severidad: CRITICA, ALTA, MEDIA o BAJA

Entrada 7:
  - Nombre de entrada: NumeroReporte
  - Descripción: Número de folio del reporte EHS
```

3. Guarda el flujo haciendo clic en **Guardar** (ícono de disco o botón en la barra superior).

**Paso B-3: Agrega la lógica condicional de enrutamiento**

Ahora implementarás la lógica que determinará a quién se envía el correo según la severidad:

1. Debajo del desencadenador, haz clic en **+ Nuevo paso**.
2. Busca y selecciona la acción **Condición** (Control → Condición).
3. Configura la primera condición:
   - **Valor:** haz clic en el campo y selecciona el contenido dinámico `Severidad` (del desencadenador).
   - **Operador:** `es igual a`
   - **Valor de comparación:** `CRITICA`

4. En la rama **Si sí** (incidente CRÍTICO):
   - Haz clic en **Agregar una acción** dentro de la rama "Si sí".
   - Busca y agrega la acción **Establecer variable** — pero primero necesitas inicializar variables. Sigue los pasos B-4 y B-5 antes de continuar aquí.

**Paso B-4: Inicializa las variables de destinatarios**

Antes del bloque de condición, agrega las variables que almacenarán los destinatarios:

1. Haz clic en el **signo "+"** entre el desencadenador y el bloque de condición para insertar un paso antes.
2. Agrega la acción **Inicializar variable** (Variables → Inicializar variable):
   ```
   Nombre:  DestinatarioPrincipal
   Tipo:    Cadena
   Valor:   coordinador.ehs@practicaehs.com
   ```
3. Agrega otro **Inicializar variable** inmediatamente después:
   ```
   Nombre:  DestinatarioCC
   Tipo:    Cadena
   Valor:   (dejar vacío)
   ```
4. Agrega un tercer **Inicializar variable**:
   ```
   Nombre:  NivelUrgencia
   Tipo:    Cadena
   Valor:   Normal
   ```

**Paso B-5: Configura las ramas de la condición**

Ahora regresa al bloque de **Condición** (Severidad = CRITICA):

**Rama "Si sí" (CRÍTICA):**

Agrega tres acciones **Establecer variable**:

```
Acción 1 — Establecer variable:
  Nombre:  DestinatarioPrincipal
  Valor:   supervisor.turno@practicaehs.com;gerencia.ehs@practicaehs.com

Acción 2 — Establecer variable:
  Nombre:  DestinatarioCC
  Valor:   direccion.planta@practicaehs.com

Acción 3 — Establecer variable:
  Nombre:  NivelUrgencia
  Valor:   Alta
```

**Rama "Si no" (no es CRÍTICA) — agrega una segunda condición anidada:**

1. Dentro de la rama "Si no", agrega otra **Condición**:
   - **Valor:** `Severidad` (contenido dinámico)
   - **Operador:** `es igual a`
   - **Valor:** `ALTA`

2. En la sub-rama **"Si sí"** (ALTA):
   ```
   Establecer variable DestinatarioPrincipal:
     Valor: supervisor.turno@practicaehs.com

   Establecer variable DestinatarioCC:
     Valor: coordinador.ehs@practicaehs.com

   Establecer variable NivelUrgencia:
     Valor: Alta
   ```

3. En la sub-rama **"Si no"** (MEDIA o BAJA — ya están inicializadas con los valores correctos por defecto):
   ```
   Establecer variable DestinatarioPrincipal:
     Valor: coordinador.ehs@practicaehs.com

   Establecer variable DestinatarioCC:
     Valor: (dejar vacío — no se modifica)

   Establecer variable NivelUrgencia:
     Valor: Normal
   ```

4. Guarda el flujo.

#### Resultado Esperado

El flujo debe mostrar la siguiente estructura visual en Power Automate:

```
[Desencadenador: Cuando Copilot Studio llama a un flujo]
        ↓
[Inicializar variable: DestinatarioPrincipal]
[Inicializar variable: DestinatarioCC]
[Inicializar variable: NivelUrgencia]
        ↓
[Condición: Severidad = CRITICA]
   ├── Sí → [Establecer variables para CRÍTICA]
   └── No → [Condición: Severidad = ALTA]
                ├── Sí → [Establecer variables para ALTA]
                └── No → [Establecer variables para MEDIA/BAJA]
```

#### Verificación

✅ Comprueba lo siguiente antes de continuar:
- El flujo se guarda sin errores (sin triángulos de advertencia en rojo).
- Las tres variables están inicializadas antes de los bloques condicionales.
- Cada rama de la condición tiene exactamente tres acciones "Establecer variable".

---

### Etapa C — Diseño de Plantillas de Correo Dinámicas (20 minutos)

**Objetivo:** Crear las plantillas de correo electrónico en HTML que incorporarán dinámicamente los datos del incidente y se adaptarán según el nivel de severidad.

#### Instrucciones

**Paso C-1: Agrega la acción de envío de correo al flujo**

1. Debajo de toda la lógica condicional (después del último bloque de condición), haz clic en **+ Nuevo paso**.
2. Busca y selecciona: **Office 365 Outlook → Enviar un correo electrónico (V2)**.
3. Si se solicita autenticación, usa tu cuenta corporativa de práctica.

**Paso C-2: Configura los campos del correo**

Rellena los campos de la acción de Outlook con el siguiente contenido. Usa el botón de **contenido dinámico** (rayo ⚡) para insertar variables y datos del desencadenador:

| Campo | Valor a configurar |
|---|---|
| **Para** | Variable dinámica: `DestinatarioPrincipal` |
| **CC** | Variable dinámica: `DestinatarioCC` |
| **Asunto** | Ver Paso C-3 |
| **Cuerpo** | Ver Paso C-4 |
| **Importancia** | Variable dinámica: `NivelUrgencia` |

**Paso C-3: Configura el asunto dinámico del correo**

En el campo **Asunto**, construye la siguiente expresión combinando texto fijo y contenido dinámico:

```
Haz clic en el campo "Asunto" y escribe/selecciona:

[REPORTE EHS - Nro. ] + [NumeroReporte] + [ ] | [ ] + [Severidad] + [ - ] + [AreaAfectada]

Resultado visual del asunto:
"[REPORTE EHS - Nro. EHS-2024-0047] | CRITICA - Planta Norte"
```

Para construirlo en Power Automate:
1. Escribe `[REPORTE EHS - Nro. ` (texto literal).
2. Selecciona contenido dinámico `NumeroReporte`.
3. Escribe ` ] | ` (texto literal).
4. Selecciona contenido dinámico `Severidad`.
5. Escribe ` - ` (texto literal).
6. Selecciona contenido dinámico `AreaAfectada`.

**Paso C-4: Diseña el cuerpo HTML dinámico del correo**

1. En el campo **Cuerpo**, activa el modo HTML haciendo clic en `</>` (código fuente) si está disponible, o usa el editor de texto enriquecido.
2. Copia y adapta la siguiente plantilla HTML. Para insertar los valores dinámicos, coloca el cursor donde corresponde y usa el panel de **Contenido dinámico**:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <style>
    body { font-family: Calibri, Arial, sans-serif; color: #333; margin: 0; padding: 20px; }
    .header-critica  { background-color: #C00000; color: white; padding: 15px 20px; border-radius: 4px 4px 0 0; }
    .header-alta     { background-color: #E36C09; color: white; padding: 15px 20px; border-radius: 4px 4px 0 0; }
    .header-normal   { background-color: #1F497D; color: white; padding: 15px 20px; border-radius: 4px 4px 0 0; }
    .content         { border: 1px solid #ddd; padding: 20px; border-radius: 0 0 4px 4px; }
    .field-label     { font-weight: bold; color: #555; font-size: 12px; text-transform: uppercase; margin-top: 12px; }
    .field-value     { font-size: 15px; margin-top: 2px; padding: 6px 10px; background: #f9f9f9; border-left: 3px solid #1F497D; }
    .footer          { margin-top: 20px; font-size: 11px; color: #999; border-top: 1px solid #eee; padding-top: 10px; }
    .badge-critica   { background: #C00000; color: white; padding: 3px 10px; border-radius: 12px; font-size: 12px; font-weight: bold; }
    .badge-alta      { background: #E36C09; color: white; padding: 3px 10px; border-radius: 12px; font-size: 12px; font-weight: bold; }
    .badge-normal    { background: #1F497D; color: white; padding: 3px 10px; border-radius: 12px; font-size: 12px; font-weight: bold; }
  </style>
</head>
<body>
  <div class="header-normal">
    <h2 style="margin:0;">🛡️ Sistema de Notificación EHS Automatizado</h2>
    <p style="margin:4px 0 0 0; font-size:13px;">Reporte generado automáticamente por el Agente EHS</p>
  </div>
  <div class="content">
    <p>Se ha registrado un nuevo incidente de seguridad que requiere su atención.</p>

    <div class="field-label">Número de Reporte</div>
    <div class="field-value"><strong>[NumeroReporte]</strong></div>

    <div class="field-label">Nivel de Severidad</div>
    <div class="field-value">
      <span class="badge-normal">[Severidad]</span>
    </div>

    <div class="field-label">Fecha y Hora del Incidente</div>
    <div class="field-value">[FechaIncidente]</div>

    <div class="field-label">Área Afectada</div>
    <div class="field-value">[AreaAfectada]</div>

    <div class="field-label">Tipo de Incidente</div>
    <div class="field-value">[TipoIncidente]</div>

    <div class="field-label">Descripción del Evento</div>
    <div class="field-value">[Descripcion]</div>

    <div class="field-label">Responsable del Área</div>
    <div class="field-value">[Responsable]</div>

    <hr style="margin: 20px 0; border: none; border-top: 1px solid #eee;">
    <p style="color: #C00000; font-weight: bold;">
      ⚡ Por favor, confirme la recepción de este reporte y tome las acciones correspondientes 
      según el protocolo EHS vigente.
    </p>

    <div class="footer">
      <p>Este mensaje fue generado automáticamente por el Sistema de Gestión EHS integrado 
      con Microsoft Copilot Studio y Power Automate.<br>
      No responda directamente a este correo. Para consultas, contacte al área de EHS.</p>
      <p><em>Datos ficticios generados para entorno de práctica — Lab 07-00-01</em></p>
    </div>
  </div>
</body>
</html>
```

> **Instrucción importante:** Los valores entre corchetes `[NombreVariable]` deben reemplazarse con el **contenido dinámico** correspondiente de Power Automate. No dejes texto literal entre corchetes en el flujo final. Posiciona el cursor en cada `[variable]`, bórrala y selecciona el campo dinámico del panel lateral.

**Paso C-5: Configura la opción de guardado en Enviados**

En la acción de Outlook, busca la opción avanzada:
- **¿Guardar en Enviados?** → Selecciona `Sí` / `true`

Esto garantiza que cada correo enviado por el flujo quede registrado en el buzón del agente para auditoría, siguiendo el principio de registro que vimos en la Lección 7.1.

**Paso C-6: Agrega la respuesta de salida al agente**

Después de la acción de envío de correo, agrega una acción de respuesta para que Copilot Studio sepa si el correo se envió correctamente:

1. Haz clic en **+ Nuevo paso**.
2. Busca y selecciona: **Power Virtual Agents → Devolver valor(es) al bot** (o "Respond to Copilot Studio").
3. Haz clic en **Agregar una salida** → Tipo **Texto**:
   ```
   Nombre de salida:  EstadoEnvio
   Valor:             Reporte [NumeroReporte] enviado correctamente al equipo EHS.
   ```
   (Inserta `NumeroReporte` como contenido dinámico del desencadenador.)

4. Guarda el flujo completo.

#### Resultado Esperado

La estructura completa del flujo debe ser:

```
[Desencadenador Copilot Studio — 7 entradas definidas]
        ↓
[Inicializar variable: DestinatarioPrincipal]
[Inicializar variable: DestinatarioCC]
[Inicializar variable: NivelUrgencia]
        ↓
[Condición: Severidad = CRITICA]
   ├── Sí → [3× Establecer variable]
   └── No → [Condición: Severidad = ALTA]
                ├── Sí → [3× Establecer variable]
                └── No → [3× Establecer variable]
        ↓
[Enviar correo electrónico (V2) — Outlook]
        ↓
[Devolver valor al bot: EstadoEnvio]
```

#### Verificación

✅ Antes de continuar confirma:
- El flujo se guarda sin errores ni advertencias en rojo.
- El campo "Para" usa la variable `DestinatarioPrincipal` (no un correo hardcodeado).
- El campo "Cuerpo" contiene el HTML con todos los valores dinámicos correctamente vinculados (no quedan corchetes literales).
- Existe la acción de respuesta al bot al final del flujo.

---

### Etapa D — Conexión e Integración con Copilot Studio y Pruebas End-to-End (30 minutos)

**Objetivo:** Conectar el flujo de Power Automate al agente EHS en Copilot Studio, configurar la acción de disparo y ejecutar pruebas completas del ciclo de notificación.

#### Instrucciones

**Paso D-1: Obtén el nombre del flujo para referenciarlo en Copilot Studio**

1. En Power Automate, ve a **Mis flujos**.
2. Localiza `Flujo_Notificacion_EHS_Incidentes`.
3. Verifica que el estado es **Activado** (toggle en verde). Si está desactivado, actívalo.
4. Anota el nombre exacto del flujo.

**Paso D-2: Abre el agente EHS en Copilot Studio**

1. Ve a `https://copilotstudio.microsoft.com`.
2. Abre tu agente EHS.
3. Navega al tema que gestiona el **registro de incidentes** (el tema principal construido en las Prácticas 5 y 6, típicamente llamado "Registrar Incidente" o similar).

**Paso D-3: Localiza el punto de inserción en el flujo del tema**

1. En el editor del tema, desplázate hasta el **final del flujo de conversación**, justo después del nodo donde el agente confirma al usuario que el incidente ha sido registrado.
2. Antes del nodo de cierre/fin de conversación, insertarás la llamada al flujo de Power Automate.

**Paso D-4: Agrega la acción de llamada al flujo de Power Automate**

1. Haz clic en el **nodo "+"** para agregar un nuevo nodo después de la confirmación de registro.
2. Selecciona **Llamar a una acción** → **Flujo de Power Automate**.
3. En el panel que aparece, busca y selecciona: `Flujo_Notificacion_EHS_Incidentes`.
4. Si el flujo no aparece inmediatamente, espera 30 segundos y actualiza la lista (puede tardar unos momentos en sincronizarse).

**Paso D-5: Mapea las variables del agente a las entradas del flujo**

Una vez seleccionado el flujo, Copilot Studio mostrará los campos de entrada que definiste en Power Automate. Mapea cada entrada con la variable correspondiente del agente:

| Entrada del Flujo (Power Automate) | Variable del Agente (Copilot Studio) |
|---|---|
| `FechaIncidente` | `varFechaIncidente` |
| `AreaAfectada` | `varAreaAfectada` |
| `TipoIncidente` | `varTipoIncidente` |
| `Descripcion` | `varDescripcion` |
| `Responsable` | `varResponsable` |
| `Severidad` | `varSeveridad` |
| `NumeroReporte` | `varNumeroReporte` |

Para cada campo:
1. Haz clic en el campo de entrada.
2. Selecciona la variable correspondiente del agente desde el selector de variables.

**Paso D-6: Captura y muestra la respuesta del flujo al usuario**

Después del nodo de llamada al flujo, agrega un nodo de **Mensaje** que muestre al usuario la confirmación del envío:

1. Haz clic en **"+"** después del nodo de llamada al flujo.
2. Selecciona **Enviar un mensaje**.
3. En el texto del mensaje, escribe:

```
✅ Reporte registrado y notificación enviada.

El equipo de EHS ha sido notificado automáticamente.
Estado: [EstadoEnvio]

Puedes hacer seguimiento del incidente con el número: [varNumeroReporte]
```

> Inserta `EstadoEnvio` como variable de salida del flujo (aparecerá disponible después de mapear las entradas) y `varNumeroReporte` como variable del agente.

**Paso D-7: Guarda y publica el agente**

1. Haz clic en **Guardar** en la barra superior de Copilot Studio.
2. Una vez guardado sin errores, haz clic en **Publicar**.
3. Confirma la publicación en el cuadro de diálogo.
4. Espera a que el estado cambie a **"Publicado"** (puede tardar 1-2 minutos).

**Paso D-8: Ejecuta la prueba end-to-end — Incidente CRÍTICO**

1. En Copilot Studio, abre el panel **"Probar agente"** (esquina superior derecha).
2. Inicia una conversación con el agente usando el siguiente escenario de prueba ficticio:

```
Escenario de prueba 1 — Incidente CRÍTICO:
─────────────────────────────────────────
Mensaje inicial: "Quiero registrar un incidente"

Responde a cada pregunta del agente con los siguientes datos ficticios:
• Fecha: 15/11/2024 09:42
• Área: Planta Norte - Sector Almacenamiento Q
• Tipo: Derrame de sustancia química
• Descripción: Se detectó derrame de reactivo en contenedor Q-07, 
               temperatura superior a 58°C. Área evacuada preventivamente.
• Responsable: Ing. Carlos Ficticio (Supervisor de Turno)
• Severidad: CRITICA
• Número de reporte: EHS-2024-0047 (o el que genere el agente)
```

3. Completa el flujo de conversación hasta llegar al punto donde el agente llama al flujo.
4. Observa si el agente muestra el mensaje de confirmación con el estado del envío.

**Paso D-9: Verifica la recepción del correo en Outlook**

1. Abre Outlook Web (`https://outlook.office.com`) o la aplicación de escritorio.
2. Busca en la bandeja de entrada un correo con asunto similar a:
   ```
   [REPORTE EHS - Nro. EHS-2024-0047] | CRITICA - Planta Norte - Sector Almacenamiento Q
   ```
3. Verifica que el correo:
   - Llegó a `supervisor.turno@practicaehs.com` y `gerencia.ehs@practicaehs.com` (si usas cuentas de práctica reales del instructor, verifica con él).
   - Contiene todos los campos del incidente correctamente poblados.
   - Muestra el HTML con el formato correcto (encabezado, etiquetas de campo, badge de severidad).
   - **No** contiene corchetes literales `[variable]` sin reemplazar.

4. Verifica también en la **carpeta Enviados** del buzón del flujo que el correo quedó registrado.

**Paso D-10: Ejecuta la prueba end-to-end — Incidente MEDIA severidad**

Repite el proceso con el siguiente escenario para validar la lógica condicional:

```
Escenario de prueba 2 — Incidente MEDIA severidad:
───────────────────────────────────────────────────
• Fecha: 15/11/2024 14:15
• Área: Bodega Central - Pasillo 3
• Tipo: Caída de objeto desde altura
• Descripción: Caja de 5kg cayó desde estante nivel 3. 
               Sin lesionados. Área señalizada.
• Responsable: Técnico Juan Ficticio
• Severidad: MEDIA
• Número de reporte: EHS-2024-0048
```

Verifica que:
- El correo llega únicamente a `coordinador.ehs@practicaehs.com` (sin CC).
- El asunto muestra `MEDIA` en lugar de `CRITICA`.
- La importancia del correo es "Normal" (no "Alta").

#### Resultado Esperado

Al completar la Etapa D deberías haber:
- Publicado el agente EHS con la acción de llamada al flujo configurada.
- Ejecutado exitosamente dos pruebas end-to-end con diferentes niveles de severidad.
- Recibido correos correctamente formateados en Outlook para ambos escenarios.
- Verificado que la lógica de enrutamiento diferencia correctamente los destinatarios.

#### Verificación

✅ Marca cada punto antes de continuar a la sección de validación:
- [ ] El agente muestra el mensaje de confirmación con el número de reporte tras llamar al flujo.
- [ ] El correo del incidente CRÍTICO llegó con importancia "Alta" y múltiples destinatarios.
- [ ] El correo del incidente MEDIA llegó con importancia "Normal" y un único destinatario.
- [ ] El HTML del correo se renderiza correctamente (sin código fuente visible al usuario).
- [ ] Ambos correos aparecen en la carpeta Enviados del buzón del flujo.

---

## 7. Validación y Pruebas

### Lista de Verificación Final

Completa la siguiente tabla de validación para certificar que el laboratorio está completo:

| # | Criterio de Validación | Método de Verificación | ✅ / ❌ |
|---|---|---|---|
| 1 | El flujo `Flujo_Notificacion_EHS_Incidentes` está activo en Power Automate | Power Automate → Mis flujos → Estado: Activado | |
| 2 | El flujo tiene exactamente 7 entradas definidas en el desencadenador | Abrir el flujo y contar las entradas del trigger | |
| 3 | La lógica condicional cubre los tres niveles: CRITICA, ALTA y MEDIA/BAJA | Revisar el diagrama del flujo en Power Automate | |
| 4 | La acción de Outlook usa variables dinámicas (no valores hardcodeados) | Abrir la acción de envío y verificar los campos | |
| 5 | El agente EHS está publicado con la llamada al flujo configurada | Copilot Studio → Estado: Publicado | |
| 6 | Prueba CRÍTICA: correo recibido con destinatarios correctos e importancia Alta | Verificar en Outlook | |
| 7 | Prueba MEDIA: correo recibido solo al coordinador, sin CC, importancia Normal | Verificar en Outlook | |
| 8 | El HTML del correo renderiza correctamente sin código visible | Abrir el correo recibido en Outlook | |
| 9 | La respuesta del flujo aparece en el chat del agente | Panel "Probar agente" en Copilot Studio | |
| 10 | Los correos enviados aparecen en la carpeta Enviados del buzón | Verificar en Outlook → Enviados | |

### Prueba de Historial del Flujo

Para verificar el registro de auditoría del flujo:

1. En Power Automate, ve a **Mis flujos** → `Flujo_Notificacion_EHS_Incidentes`.
2. Haz clic en el flujo para abrir su detalle.
3. En la sección **Historial de ejecución del flujo de 28 días**, verifica que:
   - Aparecen las ejecuciones de tus pruebas.
   - El estado de cada ejecución es **Correcto** (ícono verde).
   - Puedes hacer clic en cada ejecución para ver el detalle de cada paso y los valores de las variables en tiempo de ejecución.

> 💡 Si alguna ejecución muestra estado **Con errores**, haz clic en ella para ver en qué paso falló y cuál fue el mensaje de error. Esto es esencial para el troubleshooting.

---

## 8. Resolución de Problemas

### Problema 1: El flujo de Power Automate no aparece en Copilot Studio al intentar agregarlo como acción

**Síntoma:** Al hacer clic en "Llamar a una acción → Flujo de Power Automate" en Copilot Studio, el flujo `Flujo_Notificacion_EHS_Incidentes` no aparece en la lista, o aparece como no disponible/en gris.

**Causa raíz:** Este problema ocurre por una de tres razones: (a) el flujo no está **activado** en Power Automate (estado desactivado); (b) el flujo fue creado en un **entorno diferente** al que está configurado en Copilot Studio; o (c) el flujo no usa el desencadenador correcto de Copilot Studio (debe ser específicamente "Cuando Copilot Studio llama a un flujo" / "Power Virtual Agents — When a flow is called from a bot").

**Solución paso a paso:**
1. En Power Automate (`make.powerautomate.com`), verifica que el entorno seleccionado (esquina superior derecha) es **exactamente el mismo** que el entorno de tu agente en Copilot Studio.
2. Ve a **Mis flujos** y confirma que el flujo tiene el toggle en **verde (Activado)**. Si está desactivado, actívalo.
3. Abre el flujo y verifica que el primer bloque (desencadenador) es específicamente el de **Copilot Studio / Power Virtual Agents**. Si usaste un desencadenador diferente (como HTTP Request), deberás crear un nuevo flujo con el desencadenador correcto.
4. Regresa a Copilot Studio, guarda el agente y vuelve a intentar agregar la acción. Si sigue sin aparecer, cierra sesión y vuelve a iniciarla en ambas plataformas, luego espera 2-3 minutos antes de intentarlo de nuevo (la sincronización entre plataformas puede tomar tiempo).

---

### Problema 2: El correo se envía pero los campos dinámicos aparecen vacíos o como texto literal `[variable]`

**Síntoma:** El correo llega a los destinatarios correctamente, pero el cuerpo del mensaje muestra campos vacíos (sin valor) o muestra literalmente el texto `[FechaIncidente]`, `[AreaAfectada]`, etc., en lugar de los datos reales del incidente.

**Causa raíz:** Existen dos causas posibles: (a) en el diseño del cuerpo HTML en Power Automate, los valores entre corchetes se escribieron como **texto literal** en lugar de seleccionarse como **contenido dinámico** del desencadenador; o (b) las variables del agente en Copilot Studio no están correctamente mapeadas a las entradas del flujo (se enviaron vacías o con nombres incorrectos).

**Solución paso a paso:**
1. En Power Automate, abre el flujo y haz clic en la acción **Enviar un correo electrónico (V2)**.
2. Examina el campo **Cuerpo**: cada valor dinámico debe aparecer como una **etiqueta/chip de color** (naranja o azul), no como texto plano entre corchetes. Si ves texto plano, debes reemplazarlo:
   - Selecciona el texto literal (ej. `[FechaIncidente]`), bórralo.
   - Posiciona el cursor en ese punto y abre el panel de **Contenido dinámico**.
   - Selecciona el campo correspondiente del desencadenador (ej. `FechaIncidente`).
3. Si los chips dinámicos están correctamente insertados pero los valores llegan vacíos, el problema está en Copilot Studio: abre el agente, ve al nodo de llamada al flujo y verifica que cada entrada del flujo tiene asignada la variable correcta del agente (no está en blanco). Confirma que las variables del agente (`varFechaIncidente`, etc.) tienen valores asignados antes de llegar al nodo de llamada al flujo.
4. Ejecuta el flujo manualmente desde **Power Automate → Probar** con valores de prueba para verificar que el cuerpo del correo se genera correctamente de forma aislada, antes de volver a probar desde el agente.

---

## 9. Limpieza del Entorno

Una vez completado y validado el laboratorio, realiza las siguientes acciones de limpieza para mantener el entorno ordenado:

### En Power Automate

```
1. Ve a https://make.powerautomate.com → Mis flujos
2. El flujo "Flujo_Notificacion_EHS_Incidentes" DEBE PERMANECER ACTIVO
   (lo usarás en el Módulo 8)
3. Elimina cualquier flujo de prueba temporal que hayas creado durante
   la sesión (flujos con nombres como "Sin título", "Copia de...", etc.)
```

### En Copilot Studio

```
1. Confirma que el agente EHS está publicado con los cambios del Lab 07
2. Toma una captura de pantalla del diagrama del tema de "Registrar Incidente"
   mostrando el nodo de llamada al flujo (para tu portafolio de práctica)
3. NO elimines ni modifiques el agente (es el punto de partida del Módulo 8)
```

### En Outlook

```
1. Revisa tu bandeja de entrada y elimina los correos de prueba ficticios
   generados durante el laboratorio (o muévelos a una carpeta "Práctica Lab 07")
2. Verifica que no quedan correos con datos que parezcan reales o confidenciales
```

### Verificación Final de Privacidad

> 🔒 **Antes de cerrar sesión**, confirma que:
> - Ningún correo enviado durante la práctica contiene nombres reales de empleados.
> - Ningún flujo de Power Automate tiene credenciales hardcodeadas en los campos de configuración.
> - Los datos del historial de ejecuciones del flujo son ficticios (como se instruyó al inicio).

---

## 10. Resumen y Recursos Adicionales

### Resumen del Laboratorio

En este laboratorio de 90 minutos completaste la integración entre el agente EHS de Copilot Studio y el sistema de correo corporativo de Microsoft 365, aplicando los conceptos de la Lección 7.1 en un flujo funcional de producción. Los logros principales fueron:

| Etapa | Lo que construiste | Concepto aplicado de la Lección 7.1 |
|---|---|---|
| **A — Diseño** | Esquema de enrutamiento por severidad | Principio de mínimo privilegio + validación de destinatarios |
| **B — Flujo PA** | Flujo con lógica condicional de 3 niveles | Protocolo de transporte + autenticación mediante conector OAuth |
| **C — Plantillas** | HTML dinámico con datos del incidente | Formato MIME/HTML + registro en Enviados para auditoría |
| **D — Integración** | Agente conectado al flujo + pruebas E2E | Flujo completo: agente → API → correo → verificación |

### Conceptos Clave Consolidados

- **OAuth 2.0 en Power Automate:** el conector de Office 365 Outlook gestiona automáticamente la autenticación OAuth 2.0, eliminando la necesidad de gestionar tokens manualmente (como se haría con la Microsoft Graph API directamente).
- **Contenido dinámico como abstracción de API:** los campos de contenido dinámico en Power Automate son la representación visual de los datos JSON que viajan entre el agente y el flujo, equivalentes a los campos del `cuerpo_mensaje` en el ejemplo Python de la Lección 7.1.
- **Registro de auditoría:** la opción "Guardar en Enviados" + el historial de ejecuciones de Power Automate cumplen el requisito de registro de auditoría descrito en la Lección 7.1.
- **Enrutamiento inteligente:** la lógica condicional por severidad implementa el principio de "validación de destinatarios" asegurando que solo las personas correctas reciben cada tipo de alerta.

### Próximos Pasos

En el **Módulo 8** extenderás este flujo para incluir:
- Confirmaciones de recepción (el destinatario responde al correo y el agente registra la confirmación).
- Escalamiento automático si no hay respuesta en N minutos.
- Integración con Microsoft Teams para notificaciones adicionales en canales del equipo EHS.

### Recursos de Referencia

| Recurso | URL |
|---|---|
| Documentación: Llamar a un flujo desde Copilot Studio | `https://learn.microsoft.com/es-es/microsoft-copilot-studio/advanced-flow` |
| Documentación: Conector de Office 365 Outlook en Power Automate | `https://learn.microsoft.com/es-es/connectors/office365/` |
| Documentación: Contenido dinámico en Power Automate | `https://learn.microsoft.com/es-es/power-automate/use-expressions-in-conditions` |
| Documentación: Microsoft Graph API — Enviar correo | `https://learn.microsoft.com/es-es/graph/api/user-sendmail` |
| Documentación: Historial de ejecuciones en Power Automate | `https://learn.microsoft.com/es-es/power-automate/monitor-manage-processes` |
| Documentación: Seguridad en conectores de Power Platform | `https://learn.microsoft.com/es-es/power-platform/admin/wp-security` |

---

> **Nota para el instructor:** Si algún participante no pudo completar satisfactoriamente este laboratorio, proporciona el archivo de checkpoint `Lab07_Checkpoint_FlujoPowerAutomate.zip` disponible en la biblioteca de SharePoint del curso. Este archivo contiene el flujo exportado con la configuración base de la Etapa B, listo para importar en Power Automate y continuar desde la Etapa C.

---
LAB_END---
