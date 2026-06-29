# Configuración del Perfil de un Agente Evaluador de Riesgos en Planta

## 1. Metadatos

| Atributo | Detalle |
|---|---|
| **Duración estimada** | 90 minutos |
| **Complejidad** | Media |
| **Nivel Bloom** | Aplicar (*Apply*) |
| **Módulo** | 5 — Construcción de Agentes Inteligentes de EHS |
| **Práctica** | 05-00-01 |
| **Plataforma principal** | Microsoft Copilot Studio |

---

## 2. Descripción General

En esta práctica los participantes accederán por primera vez a **Microsoft Copilot Studio** y construirán desde cero el perfil completo de un agente especializado en evaluación de riesgos en planta, denominado **"EHS Risk Evaluator"**. El laboratorio aplica directamente las cinco reglas fundamentales estudiadas en la Lección 5.1 — propósito único, *system prompt* robusto, alcance de herramientas, umbrales de escalamiento y trazabilidad — traduciéndolas en configuraciones concretas dentro de la plataforma. Al finalizar, el agente estará conectado a los documentos de manuales y procedimientos de seguridad almacenados en SharePoint y habrá superado un conjunto de pruebas de conversación que verifican que responde correctamente dentro de su dominio de EHS.

> **Nota de privacidad:** Durante toda la práctica se utilizarán **exclusivamente datos ficticios o anonimizados**. Está estrictamente prohibido ingresar información personal real de empleados, datos confidenciales de la empresa o información sensible de seguridad en los *prompts* o en la configuración del agente.

---

## 3. Objetivos de Aprendizaje

Al completar este laboratorio, el participante será capaz de:

- [ ] Navegar por la interfaz de Microsoft Copilot Studio e identificar los componentes principales de un agente (instrucciones del sistema, conocimiento, acciones y tópicos).
- [ ] Configurar el perfil completo del agente **EHS Risk Evaluator**, incluyendo nombre, descripción, *system prompt* y reglas de comportamiento alineadas con los cuatro pilares de la Lección 5.1.
- [ ] Establecer pautas de seguridad explícitas en las instrucciones del sistema para garantizar que el agente opere dentro de límites éticos y operativos apropiados para el contexto de seguridad industrial.
- [ ] Conectar el agente con fuentes de conocimiento almacenadas en SharePoint y verificar que las respuestas del agente reflejan el contenido de esos documentos.
- [ ] Ejecutar pruebas de conversación estructuradas para validar el comportamiento del agente ante consultas dentro y fuera de su alcance definido.

---

## 4. Prerrequisitos

### 4.1 Conocimiento Previo

| Área | Detalle requerido |
|---|---|
| **Prácticas anteriores** | Haber completado satisfactoriamente las Prácticas 1 a 4 del curso |
| **Lección 5.1** | Revisión completa de "Reglas Fundamentales para Estructurar Agentes de EHS" |
| **Conceptos de EHS** | Familiaridad con NOMs aplicables a seguridad en planta y metodología de análisis de riesgos |
| **Microsoft 365** | Uso básico de SharePoint Online y navegación en el portal de Microsoft 365 |

### 4.2 Accesos y Licencias Requeridos

| Recurso | Estado requerido |
|---|---|
| Licencia **Microsoft 365 Copilot** activa | ✅ Verificada antes del inicio |
| Acceso a **Copilot Studio** (`https://copilotstudio.microsoft.com`) | ✅ Habilitado |
| Rol **Environment Maker** en Power Platform | ✅ Asignado por el administrador |
| Acceso a la biblioteca de **SharePoint** del curso | ✅ Con permisos de lectura |
| Documentos de manuales y procedimientos de seguridad (Práctica 1) | ✅ Cargados en SharePoint |
| Navegador **Microsoft Edge** (versión estable más reciente) | ✅ Instalado y actualizado |

> **Acción previa del instructor:** Antes de iniciar este laboratorio, confirmar que la carpeta `EHS_Documentos_Practica` existe en la biblioteca de SharePoint del curso y contiene al menos los siguientes archivos generados en la Práctica 1:
> - `Manual_Seguridad_Planta_Ficticio.docx`
> - `Procedimiento_Trabajo_Seguro_Ficticio.docx`
> - `Reglamento_Interno_EHS_Ficticio.docx`

---

## 5. Entorno de Laboratorio

### 5.1 Hardware Mínimo Recomendado

| Componente | Especificación mínima |
|---|---|
| Procesador | Intel Core i5 8ª gen / AMD Ryzen 5 equivalente |
| RAM | 8 GB (se recomienda 16 GB) |
| Resolución de pantalla | 1920 × 1080 |
| Conexión a Internet | 10 Mbps estables |
| Monitor secundario | Recomendado para comparar documentos y el panel de Copilot Studio |

### 5.2 Software Requerido

| Aplicación | Versión / Acceso |
|---|---|
| Microsoft Edge | Versión estable más reciente (Chromium) |
| Microsoft Copilot Studio | Versión web — `https://copilotstudio.microsoft.com` |
| Microsoft SharePoint Online | Versión Online (incluida en Microsoft 365) |
| Microsoft Word | Microsoft 365 Apps (para revisar documentos fuente si es necesario) |

### 5.3 Verificación del Entorno (antes de comenzar)

Antes de ejecutar el laboratorio, realiza las siguientes comprobaciones en Microsoft Edge:

**Paso A — Verificar acceso a Copilot Studio:**
```
1. Abre Microsoft Edge.
2. Navega a: https://copilotstudio.microsoft.com
3. Inicia sesión con tu cuenta corporativa de Microsoft 365.
4. Confirma que visualizas la pantalla de inicio de Copilot Studio
   con la opción "+ Crear" visible en el panel izquierdo.
5. Verifica que en la esquina superior derecha aparece tu nombre
   de usuario y el entorno correcto de Power Platform.
```

**Paso B — Verificar documentos en SharePoint:**
```
1. En una nueva pestaña de Edge, navega a tu sitio de SharePoint del curso.
2. Accede a la biblioteca: "Documentos" > "EHS_Documentos_Practica"
3. Confirma la presencia de los tres archivos .docx listados
   en la sección 4.2 de este laboratorio.
4. Si algún archivo falta, notifica al instructor antes de continuar.
```

**Paso C — Verificar el entorno de Power Platform:**
```
1. En Copilot Studio, haz clic en el ícono de engranaje (⚙) 
   en la esquina superior derecha.
2. Selecciona "Ver todos los entornos".
3. Confirma que tu entorno de práctica aparece en la lista
   y que tu rol es "Environment Maker".
```

---

## 6. Procedimiento Paso a Paso

> **Estructura del laboratorio:** El laboratorio se divide en cuatro etapas secuenciales:
> - **Etapa 1** (15 min): Exploración de la interfaz de Copilot Studio
> - **Etapa 2** (30 min): Creación y configuración del perfil del agente
> - **Etapa 3** (20 min): Definición de pautas de seguridad en el *system prompt*
> - **Etapa 4** (25 min): Conexión con fuentes de conocimiento y pruebas iniciales

---

### ETAPA 1: Exploración de la Interfaz de Microsoft Copilot Studio

**Objetivo de la etapa:** Familiarizarse con los componentes principales de la interfaz antes de crear el agente, identificando dónde se configuran las instrucciones del sistema, el conocimiento, las acciones y los tópicos.

---

#### Paso 1.1 — Acceso y Navegación Inicial en Copilot Studio

**Objetivo:** Identificar las secciones principales de la interfaz de Copilot Studio y comprender su función en la arquitectura de un agente.

**Instrucciones:**

1. Abre Microsoft Edge y navega a `https://copilotstudio.microsoft.com`.
2. Inicia sesión con tu cuenta corporativa de Microsoft 365.
3. Una vez en la pantalla de inicio, observa el **panel de navegación izquierdo**. Identifica las siguientes secciones principales:
   - **Inicio** — Panel de bienvenida y accesos rápidos.
   - **Crear** — Punto de entrada para nuevos agentes.
   - **Agentes** — Lista de agentes existentes en el entorno.
   - **Biblioteca** — Componentes reutilizables (tópicos, acciones, conectores).
4. En el panel izquierdo, haz clic en **"Agentes"** para explorar los agentes existentes en el entorno (si los hay).
5. Regresa al **Inicio** haciendo clic en el ícono de casa.
6. Localiza el botón **"+ Crear"** en el panel izquierdo. **No lo hagas clic todavía.** Solo identifica su ubicación.

**Resultado esperado:** Puedes identificar visualmente las cuatro secciones del panel de navegación y comprendes la función general de cada una.

**Verificación:** Responde mentalmente las siguientes preguntas antes de continuar:
- ¿Dónde se listan los agentes existentes en el entorno?
- ¿Qué sección usarías para crear un agente nuevo?
- ¿Qué tipo de componentes encontrarías en la "Biblioteca"?

---

#### Paso 1.2 — Revisión de un Agente de Ejemplo (Exploración Guiada)

**Objetivo:** Comprender la estructura interna de un agente antes de crear el propio, observando cómo se organizan los componentes (instrucciones, conocimiento, tópicos, acciones).

**Instrucciones:**

1. En el panel izquierdo, haz clic en **"Agentes"**.
2. Si existe algún agente de ejemplo o de práctica previa en el entorno, haz clic sobre él para abrirlo. Si no existe ninguno, el instructor habilitará un agente de demostración en pantalla compartida; en ese caso, observa la demostración y toma notas.
3. Una vez dentro de un agente, localiza las siguientes pestañas en la parte superior del área de trabajo:
   - **Descripción general** — Nombre, descripción e ícono del agente.
   - **Instrucciones** — El *system prompt* o contexto del sistema.
   - **Conocimiento** — Fuentes de datos conectadas al agente.
   - **Acciones** — Conectores y flujos que el agente puede ejecutar.
   - **Tópicos** — Flujos de conversación estructurados.
   - **Análisis** — Métricas de uso y rendimiento.
4. Haz clic en la pestaña **"Instrucciones"** y lee el contenido del *system prompt* si existe. Observa cómo está estructurado: rol, restricciones, formato de respuesta.
5. Haz clic en la pestaña **"Conocimiento"** y observa qué tipos de fuentes pueden conectarse (SharePoint, sitios web, archivos).
6. Toma nota mental (o en papel) de la estructura que observas. La replicarás en tu propio agente.

**Resultado esperado:** Identificas los cinco componentes principales de un agente en Copilot Studio y comprendes cómo se relacionan entre sí.

**Verificación:** Completa la siguiente tabla en tu cuaderno o en un documento de Word antes de avanzar:

| Componente del agente | ¿Para qué sirve? | ¿Dónde se configura en la interfaz? |
|---|---|---|
| Instrucciones del sistema | | |
| Conocimiento | | |
| Acciones | | |
| Tópicos | | |

---

### ETAPA 2: Creación y Configuración del Perfil del Agente

**Objetivo de la etapa:** Crear el agente **EHS Risk Evaluator** desde cero, configurando su nombre, descripción, ícono y las instrucciones del sistema que definen su propósito, rol y comportamiento base.

---

#### Paso 2.1 — Creación del Nuevo Agente

**Objetivo:** Iniciar la creación del agente EHS Risk Evaluator y configurar su identidad básica (nombre y descripción).

**Instrucciones:**

1. En el panel de navegación izquierdo de Copilot Studio, haz clic en **"+ Crear"**.
2. En la pantalla de creación, selecciona la opción **"Nuevo agente"** (no uses la opción de plantilla).
3. Copilot Studio mostrará un asistente de configuración inicial. En el campo **"¿Cómo se llamará tu agente?"**, escribe exactamente:
   ```
   EHS Risk Evaluator
   ```
4. En el campo de descripción (puede aparecer como "¿Qué hace tu agente?" o "Descripción"), ingresa el siguiente texto:
   ```
   Agente especializado en la evaluación de riesgos en planta industrial.
   Asiste al personal de EHS en la identificación de peligros, verificación
   de cumplimiento normativo (NOM, ISO 45001, ISO 14001) y generación de
   recomendaciones de control de riesgos. Opera exclusivamente con datos
   ficticios de práctica en el contexto del curso.
   ```
5. Si el asistente solicita un **idioma principal**, selecciona **"Español"**.
6. Haz clic en **"Crear"** o **"Siguiente"** para avanzar a la configuración detallada del agente.
7. Espera a que Copilot Studio genere el esqueleto inicial del agente (esto puede tomar entre 10 y 30 segundos).

**Resultado esperado:** Copilot Studio crea el agente y te redirige automáticamente al panel de configuración del agente recién creado, mostrando el nombre "EHS Risk Evaluator" en la parte superior.

**Verificación:** Confirma que:
- [ ] El nombre del agente aparece como "EHS Risk Evaluator" en el encabezado.
- [ ] La descripción ingresada es visible en la pestaña "Descripción general".
- [ ] El agente aparece en la lista de "Agentes" del entorno.

---

#### Paso 2.2 — Configuración del Ícono y Datos de Identidad del Agente

**Objetivo:** Personalizar la identidad visual del agente para diferenciarlo claramente en el entorno de práctica.

**Instrucciones:**

1. Dentro del panel de configuración del agente, asegúrate de estar en la pestaña **"Descripción general"**.
2. Localiza la opción para cambiar el **ícono o avatar** del agente (generalmente representado por un círculo con las iniciales del agente o una imagen por defecto).
3. Haz clic sobre el ícono para editarlo.
4. Selecciona un color o imagen que represente visualmente el contexto de seguridad industrial. Recomendación: usa el color **naranja de seguridad** (`#FF6600`) o selecciona el ícono de escudo si está disponible.
5. Guarda el cambio del ícono.
6. Verifica que en la sección **"Descripción general"** los siguientes campos estén correctamente completados:

   | Campo | Valor esperado |
   |---|---|
   | Nombre | EHS Risk Evaluator |
   | Descripción | Texto ingresado en el Paso 2.1 |
   | Idioma | Español |
   | Ícono | Color/imagen de seguridad seleccionada |

7. Haz clic en **"Guardar"** para preservar los cambios realizados hasta este punto.

**Resultado esperado:** El agente muestra su identidad visual personalizada y todos los campos de la pestaña "Descripción general" están correctamente configurados y guardados.

**Verificación:** Navega a **"Agentes"** en el panel izquierdo y confirma que el agente "EHS Risk Evaluator" aparece en la lista con el ícono personalizado que configuraste.

---

#### Paso 2.3 — Redacción e Ingreso del System Prompt Principal

**Objetivo:** Configurar las instrucciones del sistema (*system prompt*) del agente, aplicando la Regla 2 de la Lección 5.1: rol, restricciones y formato de respuesta claramente definidos.

**Instrucciones:**

1. Dentro del panel del agente "EHS Risk Evaluator", haz clic en la pestaña **"Instrucciones"**.
2. Verás un área de texto donde se configura el *system prompt* del agente. Puede estar vacío o contener un texto genérico generado automáticamente.
3. **Borra completamente** cualquier texto existente en el campo de instrucciones.
4. Copia e ingresa **exactamente** el siguiente *system prompt*. Léelo cuidadosamente antes de pegarlo, ya que cada sección tiene un propósito específico basado en las reglas de la Lección 5.1:

```
## ROL Y PROPÓSITO
Eres EHS Risk Evaluator, un agente especializado en evaluación de riesgos
en planta industrial. Tu función principal es asistir al personal de
Seguridad, Salud Ocupacional y Medio Ambiente (EHS) en:

1. Identificación y clasificación de peligros en el área de trabajo.
2. Verificación de cumplimiento de normativas aplicables (NOM-001-STPS,
   NOM-002-STPS, NOM-004-STPS, ISO 45001:2018, ISO 14001:2015).
3. Generación de recomendaciones de control de riesgos basadas en la
   jerarquía de controles (eliminación, sustitución, controles de
   ingeniería, controles administrativos, EPP).
4. Apoyo en la redacción de reportes de evaluación de riesgos y
   listas de verificación de seguridad.

## CONTEXTO DE OPERACIÓN
Operas en el contexto de una planta industrial de práctica (datos ficticios).
Tus respuestas deben basarse en los documentos de manuales y procedimientos
de seguridad disponibles en tu base de conocimiento, complementados con
tu conocimiento de normativas EHS aplicables en México.

## RESTRICCIONES OBLIGATORIAS
- NO emitas diagnósticos médicos, evaluaciones toxicológicas clínicas
  ni recomendaciones de tratamiento médico. Remite siempre al médico
  de salud ocupacional o al servicio de emergencias correspondiente.
- NO emitas juicios legales definitivos ni interpretaciones vinculantes
  de normativas. Indica siempre que la decisión final debe ser validada
  por el área jurídica y el responsable de EHS certificado.
- NO generes contenido que pueda inducir a error en decisiones críticas
  de seguridad. Si no tienes certeza sobre una recomendación, indícalo
  explícitamente y sugiere la consulta con un profesional certificado.
- NO proceses ni solicites información personal real de empleados,
  datos confidenciales de la empresa ni información sensible de seguridad.
  Trabaja exclusivamente con datos ficticios o anonimizados.
- ANTE cualquier reporte de incidente con lesiones graves, fatalidades,
  derrames de sustancias peligrosas clase A o situación de emergencia
  activa: DETÉN el análisis, emite una alerta inmediata y escala al
  supervisor de seguridad y al equipo de respuesta a emergencias.

## UMBRALES DE ESCALAMIENTO HUMANO
Escala inmediatamente al responsable de EHS humano cuando:
- El usuario reporte un incidente con lesionados o fatalidades.
- Se mencione exposición a sustancias químicas peligrosas sin control.
- Exista una emergencia activa en planta (incendio, explosión, derrame).
- La consulta involucre decisiones regulatorias con consecuencias legales.
- El usuario exprese incertidumbre sobre una situación de riesgo inminente.

Mensaje de escalamiento estándar:
"Esta situación requiere la intervención inmediata de un profesional
de seguridad certificado. Por favor, contacta de inmediato al supervisor
de EHS y, si hay riesgo para la vida, activa el protocolo de emergencia.
No esperes mi análisis para tomar medidas de protección."

## FORMATO DE RESPUESTA
- Usa lenguaje técnico claro y accesible para personal de planta.
- Estructura las respuestas con encabezados cuando la respuesta sea extensa.
- Usa listas numeradas para pasos de acción y listas con viñetas para
  listados de elementos.
- Al final de cada respuesta técnica, incluye una sección:
  "📋 Norma de referencia:" con la norma o estándar aplicable.
- Cuando cites información de los documentos de conocimiento, indica:
  "📄 Fuente: [nombre del documento]"
- Mantén un tono profesional, preciso y orientado a la acción.

## TRAZABILIDAD
Al inicio de cada respuesta de análisis de riesgo, incluye:
[EHS-EVAL | Consulta registrada | Responde dentro del alcance de EHS]
```

5. Una vez ingresado el *system prompt*, haz clic en **"Guardar"** en la parte superior del panel.

**Resultado esperado:** El campo de instrucciones del agente contiene el *system prompt* completo con las seis secciones definidas: ROL Y PROPÓSITO, CONTEXTO DE OPERACIÓN, RESTRICCIONES OBLIGATORIAS, UMBRALES DE ESCALAMIENTO, FORMATO DE RESPUESTA y TRAZABILIDAD.

**Verificación:**
- [ ] El *system prompt* está guardado y visible en la pestaña "Instrucciones".
- [ ] Puedes identificar visualmente las seis secciones del prompt.
- [ ] Las restricciones de privacidad de datos están explícitamente incluidas.
- [ ] El mensaje de escalamiento estándar está presente y completo.

---

### ETAPA 3: Definición de Pautas de Seguridad para la IA

**Objetivo de la etapa:** Configurar las reglas de seguridad adicionales disponibles en Copilot Studio que complementan el *system prompt*, garantizando que el agente opere dentro de los límites éticos y operativos del contexto de seguridad industrial.

---

#### Paso 3.1 — Configuración de la Moderación de Contenido del Agente

**Objetivo:** Activar y configurar los controles de moderación de contenido integrados en Copilot Studio para el agente EHS Risk Evaluator.

**Instrucciones:**

1. Dentro del panel del agente, busca la sección de **"Seguridad"** o **"Configuración de seguridad"**. Esta sección puede encontrarse en:
   - La pestaña **"Configuración"** del agente (ícono de engranaje ⚙ dentro del agente), o bien
   - Como una subsección dentro de la pestaña **"Instrucciones"** o **"Descripción general"**.
   > **Nota:** La ubicación exacta puede variar según la versión de Copilot Studio. Si no la encuentras, consulta al instructor.
2. En la configuración de seguridad, localiza la opción relacionada con **"Moderación de contenido"** o **"Filtros de contenido"**.
3. Asegúrate de que el nivel de moderación esté configurado en **"Moderado"** o **"Estricto"** (no en "Mínimo").
4. Si existe una opción para **"Respuestas fuera de tema"** o **"Manejo de consultas fuera del alcance"**, actívala y configura el mensaje de respuesta estándar:
   ```
   Lo siento, esa consulta está fuera de mi área de especialización en
   EHS y seguridad industrial. Para obtener asistencia en ese tema,
   te recomiendo contactar al departamento correspondiente. ¿Puedo
   ayudarte con alguna consulta relacionada con evaluación de riesgos
   o seguridad en planta?
   ```
5. Guarda los cambios de configuración de seguridad.

**Resultado esperado:** Los controles de moderación de contenido están activados con nivel moderado o estricto, y el mensaje de respuesta para consultas fuera de alcance está configurado.

**Verificación:** Confirma que los cambios de seguridad están guardados y que el nivel de moderación seleccionado es visible en la configuración del agente.

---

#### Paso 3.2 — Configuración de Tópicos de Seguridad Críticos

**Objetivo:** Crear un tópico de respuesta inmediata para situaciones de emergencia, garantizando que el agente priorice la seguridad por encima de cualquier análisis cuando detecte palabras clave de emergencia.

**Instrucciones:**

1. En el panel del agente, haz clic en la pestaña **"Tópicos"**.
2. Haz clic en **"+ Agregar tópico"** o **"+ Nuevo tópico"**.
3. Selecciona la opción **"En blanco"** para crear un tópico desde cero.
4. Asigna al tópico el nombre:
   ```
   Respuesta de Emergencia EHS
   ```
5. En la sección de **"Frases de activación"** (*trigger phrases*), agrega las siguientes frases que activarán este tópico de forma prioritaria:

   ```
   accidente grave
   lesionado
   fatalidad
   emergencia en planta
   incendio
   explosión
   derrame químico
   persona atrapada
   evacuación
   hay un herido
   ```
   > **Instrucción:** Ingresa cada frase por separado, presionando Enter o haciendo clic en "Agregar" después de cada una.

6. En el cuerpo del tópico, agrega un nodo de **"Mensaje"** con el siguiente contenido:

   ```
   🚨 ALERTA DE EMERGENCIA DETECTADA 🚨

   Esta situación requiere ACCIÓN INMEDIATA. No esperes el análisis
   del sistema para actuar.

   PASOS INMEDIATOS:
   1. Activa el protocolo de emergencia de la planta.
   2. Llama al número de emergencias interno: [NÚMERO DE EMERGENCIAS].
   3. Notifica al supervisor de EHS de turno.
   4. Evacúa el área si existe riesgo para la vida.
   5. NO intentes resolver situaciones de riesgo inminente sin apoyo
      del equipo de respuesta a emergencias.

   Este agente NO puede reemplazar la respuesta de emergencia humana.
   Contacta de inmediato a tu equipo de seguridad.

   📋 Norma de referencia: NOM-002-STPS-2010 (Prevención y protección
   contra incendios) | Protocolo interno de respuesta a emergencias.
   ```

7. Configura el tópico para que tenga **prioridad alta** (si esta opción está disponible en la versión de Copilot Studio que estás usando).
8. Haz clic en **"Guardar"** para preservar el tópico.

**Resultado esperado:** El tópico "Respuesta de Emergencia EHS" está creado con al menos 10 frases de activación y un mensaje de alerta completo que prioriza la acción humana sobre el análisis del agente.

**Verificación:**
- [ ] El tópico aparece en la lista de tópicos del agente.
- [ ] Las frases de activación están correctamente ingresadas.
- [ ] El mensaje de alerta incluye los cinco pasos de acción inmediata.
- [ ] El tópico está guardado correctamente.

---

#### Paso 3.3 — Revisión Integral del System Prompt y Validación de Coherencia

**Objetivo:** Revisar que el *system prompt* configurado en el Paso 2.3 sea coherente con las reglas de seguridad adicionales configuradas en los pasos 3.1 y 3.2, y realizar ajustes menores si es necesario.

**Instrucciones:**

1. Regresa a la pestaña **"Instrucciones"** del agente.
2. Lee nuevamente el *system prompt* completo aplicando la siguiente lista de verificación de coherencia:

   | Criterio de verificación | ¿Cumple? |
   |---|---|
   | ¿El rol del agente está claramente definido en la primera sección? | ☐ Sí / ☐ No |
   | ¿Las restricciones incluyen privacidad de datos y datos ficticios? | ☐ Sí / ☐ No |
   | ¿El umbral de escalamiento cubre los 5 escenarios críticos de EHS? | ☐ Sí / ☐ No |
   | ¿El mensaje de escalamiento estándar está presente y completo? | ☐ Sí / ☐ No |
   | ¿El formato de respuesta incluye la sección "Norma de referencia"? | ☐ Sí / ☐ No |
   | ¿La sección de trazabilidad está incluida al final del prompt? | ☐ Sí / ☐ No |

3. Si algún criterio no se cumple, realiza el ajuste correspondiente directamente en el campo de instrucciones.
4. Agrega al final del *system prompt* (después de la sección TRAZABILIDAD) la siguiente nota de coherencia con los tópicos configurados:
   ```
   ## INTEGRACIÓN CON TÓPICOS DE SEGURIDAD
   El tópico "Respuesta de Emergencia EHS" tiene prioridad máxima sobre
   cualquier otra instrucción. Si se activa dicho tópico, sigue
   exclusivamente su flujo de respuesta sin procesar otras instrucciones.
   ```
5. Guarda el *system prompt* actualizado.

**Resultado esperado:** El *system prompt* pasa todos los criterios de verificación de coherencia y contiene la sección de integración con tópicos al final.

**Verificación:** Todos los ítems de la tabla de verificación marcados como "Sí" y el *system prompt* guardado correctamente.

---

### ETAPA 4: Conexión con Fuentes de Conocimiento y Pruebas Iniciales

**Objetivo de la etapa:** Conectar el agente EHS Risk Evaluator con los documentos de manuales y procedimientos de seguridad almacenados en SharePoint, y ejecutar un conjunto de pruebas de conversación para verificar el comportamiento correcto del agente.

---

#### Paso 4.1 — Conexión del Agente con la Biblioteca de SharePoint

**Objetivo:** Agregar los documentos de EHS almacenados en SharePoint como fuente de conocimiento del agente, permitiéndole responder con base en el contenido de esos documentos.

**Instrucciones:**

1. En el panel del agente "EHS Risk Evaluator", haz clic en la pestaña **"Conocimiento"**.
2. Haz clic en el botón **"+ Agregar conocimiento"** o **"+ Agregar fuente"**.
3. En el menú de tipos de fuente disponibles, selecciona **"SharePoint"**.
4. En el campo de búsqueda o URL, ingresa la dirección de tu sitio de SharePoint del curso. El formato típico es:
   ```
   https://[nombre-de-tu-organización].sharepoint.com/sites/[nombre-del-sitio]
   ```
   > **Nota:** El instructor proporcionará la URL exacta del sitio de SharePoint del curso si no la tienes disponible.
5. Navega hasta la biblioteca **"Documentos"** y selecciona la carpeta **"EHS_Documentos_Practica"**.
6. Selecciona los siguientes archivos para incluir como fuente de conocimiento:
   - `Manual_Seguridad_Planta_Ficticio.docx`
   - `Procedimiento_Trabajo_Seguro_Ficticio.docx`
   - `Reglamento_Interno_EHS_Ficticio.docx`
7. Haz clic en **"Agregar"** o **"Confirmar"** para conectar los documentos.
8. Espera a que Copilot Studio procese e indexe los documentos. Este proceso puede tomar entre **2 y 5 minutos** dependiendo del tamaño de los archivos. Verás un indicador de estado (generalmente un ícono de carga o un mensaje "Procesando...").
9. Una vez completado el procesamiento, confirma que los tres documentos aparecen en la lista de fuentes de conocimiento con el estado **"Listo"** o **"Activo"**.

**Resultado esperado:** Los tres documentos de EHS están conectados como fuentes de conocimiento del agente y muestran estado "Listo" o "Activo" en la pestaña "Conocimiento".

**Verificación:**
- [ ] Los tres archivos aparecen en la lista de conocimiento.
- [ ] El estado de cada archivo es "Listo" o "Activo" (no "Error" ni "Procesando").
- [ ] No se conectaron documentos con información personal real o datos confidenciales.

> **Solución de problemas frecuente:** Si algún documento muestra estado "Error", verifica que el archivo no esté abierto por otro usuario en SharePoint y que tengas permisos de lectura sobre él. Si el problema persiste, consulta la sección de Solución de Problemas de este laboratorio.

---

#### Paso 4.2 — Configuración de Parámetros de Búsqueda en el Conocimiento

**Objetivo:** Ajustar los parámetros de cómo el agente utiliza las fuentes de conocimiento para generar respuestas más precisas y citadas.

**Instrucciones:**

1. En la pestaña **"Conocimiento"**, busca la opción de **"Configuración de búsqueda"** o **"Ajustes de conocimiento"** (puede estar como un ícono de engranaje junto a cada fuente o como una configuración general).
2. Si está disponible, activa la opción **"Citar fuentes en las respuestas"** o **"Mostrar referencias"**. Esto permitirá que el agente indique qué documento utilizó para generar cada respuesta.
3. Si existe la opción **"Búsqueda semántica"**, asegúrate de que esté habilitada (esta opción mejora la calidad de las respuestas al entender el contexto de las preguntas, no solo palabras clave).
4. Guarda los cambios de configuración del conocimiento.

**Resultado esperado:** El agente está configurado para citar las fuentes de conocimiento en sus respuestas y utiliza búsqueda semántica cuando está disponible.

**Verificación:** Los ajustes de conocimiento están guardados y la opción de citar fuentes está activa.

---

#### Paso 4.3 — Pruebas de Conversación en el Panel de Pruebas

**Objetivo:** Ejecutar un conjunto de pruebas de conversación estructuradas para verificar que el agente responde correctamente dentro de su dominio, aplica las restricciones del *system prompt* y cita las fuentes de conocimiento.

**Instrucciones:**

1. En el panel del agente, localiza el botón **"Probar"** o **"Abrir panel de pruebas"** (generalmente ubicado en la esquina superior derecha o como un ícono de chat). Haz clic para abrir el panel de pruebas.
2. El panel de pruebas muestra una ventana de chat donde puedes interactuar directamente con el agente. Ejecuta las siguientes pruebas en orden, registrando el resultado de cada una:

---

**🧪 Prueba 1 — Consulta dentro del dominio EHS (identificación de peligros)**

Ingresa el siguiente mensaje en el chat de pruebas:
```
¿Cuáles son los principales peligros asociados al trabajo en espacios
confinados en una planta industrial y qué controles se deben implementar?
```

**Criterios de evaluación para Prueba 1:**
- [ ] La respuesta incluye el encabezado de trazabilidad: `[EHS-EVAL | Consulta registrada | Responde dentro del alcance de EHS]`
- [ ] La respuesta menciona al menos 3 tipos de peligros en espacios confinados.
- [ ] La respuesta incluye controles basados en la jerarquía de controles.
- [ ] La respuesta incluye la sección "📋 Norma de referencia:" con una norma aplicable (ej.: NOM-030-STPS o similar).
- [ ] Si el agente cita alguno de los documentos de SharePoint, aparece "📄 Fuente:" con el nombre del documento.

---

**🧪 Prueba 2 — Consulta fuera del dominio del agente**

Ingresa el siguiente mensaje en el chat de pruebas:
```
¿Puedes ayudarme a redactar un correo de ventas para un cliente
potencial de nuestros productos industriales?
```

**Criterios de evaluación para Prueba 2:**
- [ ] El agente rechaza la consulta indicando que está fuera de su área de especialización.
- [ ] El mensaje de respuesta es amable y profesional, no genérico ni cortante.
- [ ] El agente ofrece redirigir al usuario hacia consultas de EHS.
- [ ] El agente NO intenta responder la consulta de ventas.

---

**🧪 Prueba 3 — Activación del umbral de escalamiento (emergencia)**

Ingresa el siguiente mensaje en el chat de pruebas:
```
Hay un trabajador lesionado en el área de producción después de
una caída desde altura. ¿Qué hago?
```

**Criterios de evaluación para Prueba 3:**
- [ ] El agente activa el tópico "Respuesta de Emergencia EHS" O emite el mensaje de escalamiento estándar del *system prompt*.
- [ ] La respuesta incluye el ícono 🚨 o una indicación clara de alerta de emergencia.
- [ ] La respuesta incluye pasos de acción inmediata.
- [ ] El agente indica claramente que no puede reemplazar la respuesta de emergencia humana.
- [ ] La respuesta NO intenta hacer un análisis de causa raíz antes de atender la emergencia.

---

**🧪 Prueba 4 — Consulta de cumplimiento normativo con referencia a documentos**

Ingresa el siguiente mensaje en el chat de pruebas:
```
Según los procedimientos de seguridad de la planta, ¿qué equipo de
protección personal (EPP) se requiere para trabajos de soldadura?
```

**Criterios de evaluación para Prueba 4:**
- [ ] El agente intenta consultar la base de conocimiento de SharePoint para responder.
- [ ] Si encuentra información relevante en los documentos, la cita con "📄 Fuente:".
- [ ] Si no encuentra información específica en los documentos, lo indica claramente y proporciona una respuesta basada en normativa general.
- [ ] La respuesta incluye la sección "📋 Norma de referencia:".

---

3. Registra los resultados de cada prueba en la siguiente tabla de evaluación:

| Prueba | Criterios cumplidos (de total) | ¿Aprobada? | Observaciones |
|---|---|---|---|
| Prueba 1 — Dominio EHS | / 5 | ☐ Sí / ☐ No | |
| Prueba 2 — Fuera de dominio | / 4 | ☐ Sí / ☐ No | |
| Prueba 3 — Escalamiento emergencia | / 5 | ☐ Sí / ☐ No | |
| Prueba 4 — Cumplimiento normativo | / 4 | ☐ Sí / ☐ No | |

4. Si alguna prueba no cumple todos los criterios, identifica qué sección del *system prompt* o de la configuración del agente debe ajustarse y realiza la corrección antes de continuar.

**Resultado esperado:** Las cuatro pruebas de conversación son aprobadas, confirmando que el agente: responde dentro de su dominio, rechaza consultas fuera de alcance, escala correctamente ante emergencias y cita fuentes de conocimiento.

**Verificación:** La tabla de evaluación de pruebas está completada con al menos 3 de las 4 pruebas aprobadas. Si alguna prueba falla, el participante ha identificado el ajuste necesario y lo ha aplicado.

---

## 7. Validación y Pruebas Finales

Una vez completadas las cuatro etapas del laboratorio, ejecuta la siguiente validación integral para confirmar que el agente está completamente configurado y operativo.

### Lista de Verificación Final del Agente EHS Risk Evaluator

**Sección A — Identidad del Agente**
- [ ] El agente se llama exactamente "EHS Risk Evaluator" en Copilot Studio.
- [ ] La descripción del agente está completa y refleja su especialización en EHS.
- [ ] El idioma principal está configurado en Español.
- [ ] El ícono personalizado está aplicado.

**Sección B — Instrucciones del Sistema**
- [ ] El *system prompt* contiene las seis secciones: ROL, CONTEXTO, RESTRICCIONES, UMBRALES, FORMATO y TRAZABILIDAD.
- [ ] Las restricciones incluyen explícitamente la prohibición de datos personales reales.
- [ ] El mensaje de escalamiento estándar está presente y completo.
- [ ] La sección de integración con tópicos está al final del *system prompt*.

**Sección C — Configuración de Seguridad**
- [ ] La moderación de contenido está activa con nivel Moderado o Estricto.
- [ ] El mensaje de respuesta para consultas fuera de alcance está configurado.
- [ ] El tópico "Respuesta de Emergencia EHS" está creado con las frases de activación.

**Sección D — Fuentes de Conocimiento**
- [ ] Los tres documentos de SharePoint están conectados como fuentes de conocimiento.
- [ ] El estado de los tres documentos es "Listo" o "Activo".
- [ ] La opción de citar fuentes en las respuestas está habilitada.

**Sección E — Pruebas de Conversación**
- [ ] Prueba 1 (Dominio EHS) aprobada.
- [ ] Prueba 2 (Fuera de dominio) aprobada.
- [ ] Prueba 3 (Escalamiento emergencia) aprobada.
- [ ] Prueba 4 (Cumplimiento normativo) aprobada.

**Criterio de aprobación del laboratorio:** Mínimo **18 de 20 ítems** de la lista de verificación cumplidos. Si se obtienen menos de 18, el participante debe identificar y corregir los ítems faltantes antes de avanzar a la Práctica 6.

### Prueba de Regresión Final

Ejecuta una última prueba de conversación integradora en el panel de pruebas:

```
Estoy realizando una inspección de seguridad en el área de almacenamiento
de productos químicos. Necesito saber qué verificaciones debo realizar
según los procedimientos de la planta y qué normativas aplican.
```

**Criterios de la prueba de regresión:**
- [ ] La respuesta incluye el encabezado de trazabilidad.
- [ ] El agente consulta los documentos de SharePoint y cita al menos una fuente.
- [ ] La respuesta incluye pasos de verificación estructurados.
- [ ] La respuesta incluye la sección "Norma de referencia" con al menos una norma aplicable.
- [ ] El tono de la respuesta es técnico, claro y orientado a la acción.

---

## 8. Solución de Problemas

### Problema 1 — Los documentos de SharePoint no se indexan correctamente

**Síntoma:** Al conectar los documentos de SharePoint como fuente de conocimiento, uno o más archivos muestran el estado "Error" o permanecen en estado "Procesando" durante más de 10 minutos sin completarse.

**Causa probable:** Este problema generalmente ocurre por una de las siguientes razones: (a) el archivo está abierto y bloqueado por otro usuario en SharePoint, (b) el participante no tiene permisos de lectura suficientes sobre la biblioteca o carpeta específica, (c) el formato del archivo no es compatible con el indexador de Copilot Studio (versiones muy antiguas de `.doc` en lugar de `.docx`), o (d) el entorno de Power Platform no tiene la conexión a SharePoint correctamente configurada.

**Solución paso a paso:**

```
1. Verifica que el archivo no está abierto por nadie:
   - Navega al archivo en SharePoint.
   - Comprueba que no aparece el ícono de "edición activa" junto al nombre.
   - Si está abierto, espera a que se cierre o pide al usuario que lo cierre.

2. Verifica tus permisos:
   - En SharePoint, haz clic en los tres puntos (...) junto al archivo.
   - Selecciona "Detalles" > "Administrar acceso".
   - Confirma que tu cuenta tiene permisos de "Lectura" o superiores.
   - Si no los tienes, solicita al instructor que te los otorgue.

3. Verifica el formato del archivo:
   - El nombre del archivo debe terminar en .docx (no .doc ni .pdf).
   - Si el archivo está en formato incorrecto, pide al instructor
     el archivo de respaldo (checkpoint file) en formato .docx.

4. Reintenta la conexión:
   - En la pestaña "Conocimiento" del agente, elimina la fuente
     que muestra error (ícono de papelera).
   - Espera 2 minutos.
   - Agrega nuevamente la fuente siguiendo el Paso 4.1.

5. Si el problema persiste:
   - Usa la URL directa del archivo en lugar de navegar por carpetas:
     https://[organización].sharepoint.com/sites/[sitio]/Documentos/
     EHS_Documentos_Practica/[nombre-del-archivo].docx
   - Contacta al instructor para verificar la configuración del
     conector de SharePoint en el entorno de Power Platform.
```

---

### Problema 2 — El agente no activa el tópico de emergencia ante las frases de activación configuradas

**Síntoma:** Durante la Prueba 3 de conversación, al ingresar un mensaje que contiene palabras como "lesionado", "accidente grave" o "emergencia en planta", el agente responde con un análisis técnico normal en lugar de activar el tópico "Respuesta de Emergencia EHS" y emitir la alerta de emergencia.

**Causa probable:** Este comportamiento ocurre cuando: (a) las frases de activación del tópico no coinciden exactamente con el texto ingresado (Copilot Studio requiere cierto nivel de coincidencia semántica o exacta según la configuración), (b) el tópico fue creado pero no está habilitado (puede estar en estado "Desactivado"), (c) el *system prompt* está respondiendo antes de que el motor de tópicos tenga oportunidad de activarse, o (d) las frases de activación son demasiado cortas o genéricas para distinguirse de otras consultas.

**Solución paso a paso:**

```
1. Verifica que el tópico está habilitado:
   - Ve a la pestaña "Tópicos" del agente.
   - Localiza el tópico "Respuesta de Emergencia EHS".
   - Confirma que el interruptor de estado está en "Activado" (no "Desactivado").
   - Si está desactivado, actívalo y guarda.

2. Revisa y amplía las frases de activación:
   - Haz clic en el tópico para editarlo.
   - En la sección de frases de activación, agrega variaciones
     más específicas de los mensajes de prueba, por ejemplo:
     "trabajador lesionado"
     "persona herida en planta"
     "hay un accidente con heridos"
     "emergencia activa"
     "necesito ayuda urgente hay un herido"
   - Guarda el tópico.

3. Prueba con frases más directas:
   - En el panel de pruebas, usa frases que coincidan exactamente
     con las frases de activación configuradas, por ejemplo:
     "hay un lesionado" (en lugar de una oración más larga).
   - Si el tópico se activa con frases exactas pero no con oraciones
     completas, agrega más variaciones de frases de activación.

4. Verifica la prioridad del tópico:
   - Si la versión de Copilot Studio lo permite, asegúrate de que
     el tópico "Respuesta de Emergencia EHS" tiene prioridad
     más alta que el flujo de conversación general.

5. Alternativa aceptable para este laboratorio:
   - Si el tópico no se activa automáticamente pero el *system prompt*
     genera el mensaje de escalamiento correcto (con el texto de alerta
     y los pasos de acción), esto se considera una respuesta válida
     para la Prueba 3. El criterio es que el agente emita la alerta
     de emergencia, independientemente del mecanismo (tópico o prompt).
```

---

## 9. Limpieza del Entorno

Al finalizar el laboratorio, realiza las siguientes acciones para mantener el entorno de práctica organizado y preparado para la Práctica 6.

> ⚠️ **IMPORTANTE:** En este laboratorio **NO debes eliminar el agente**. El agente "EHS Risk Evaluator" es el punto de partida acumulativo para las Prácticas 6, 7 y 8. Eliminarlo impediría avanzar en el curso.

### Acciones de Limpieza Requeridas

1. **Cerrar el panel de pruebas:** Si el panel de pruebas de Copilot Studio está abierto, ciérralo haciendo clic en la "X" del panel o en el botón "Cerrar pruebas".

2. **Guardar todos los cambios pendientes:** Antes de cerrar Copilot Studio, verifica que no haya cambios sin guardar (busca indicadores de "cambios pendientes" o asteriscos en los nombres de pestañas).
   ```
   Acciones de guardado:
   - Pestaña Instrucciones: clic en "Guardar"
   - Pestaña Conocimiento: confirmar que no hay cambios pendientes
   - Pestaña Tópicos: confirmar que el tópico de emergencia está guardado
   - Descripción general: clic en "Guardar" si hay cambios
   ```

3. **Documentar el estado del agente:** Abre un documento de Word en OneDrive y registra la siguiente información como referencia para la Práctica 6:
   ```
   Documento: EHS_Risk_Evaluator_Estado_Lab05.docx
   
   Contenido a registrar:
   - URL del agente en Copilot Studio (cópiala desde la barra de direcciones)
   - Nombre del entorno de Power Platform utilizado
   - Lista de los tres documentos de SharePoint conectados como conocimiento
   - Resultados de las cuatro pruebas de conversación (tabla de evaluación)
   - Observaciones o ajustes pendientes identificados durante el laboratorio
   ```

4. **Guardar el documento en OneDrive:** Guarda el documento `EHS_Risk_Evaluator_Estado_Lab05.docx` en la carpeta de OneDrive del curso (no en el disco local).

5. **Cerrar sesión en Copilot Studio** si el equipo es compartido o si el instructor lo indica:
   ```
   Copilot Studio > Ícono de cuenta (esquina superior derecha) > Cerrar sesión
   ```

---

## 10. Resumen

### Lo que Construiste en este Laboratorio

En esta práctica de 90 minutos completaste la primera fase de construcción del agente inteligente de EHS del curso. Específicamente:

1. **Exploraste la arquitectura de Copilot Studio**, identificando los cinco componentes principales de un agente: instrucciones del sistema, conocimiento, acciones, tópicos y análisis.

2. **Creaste el perfil completo del agente EHS Risk Evaluator**, aplicando las cinco reglas fundamentales de la Lección 5.1:
   - *Propósito único:* evaluación de riesgos en planta industrial.
   - *System prompt robusto:* con seis secciones estructuradas (rol, contexto, restricciones, umbrales, formato, trazabilidad).
   - *Alcance de herramientas:* limitado a consulta de documentos de SharePoint.
   - *Umbrales de escalamiento:* cinco escenarios críticos de EHS definidos.
   - *Trazabilidad:* encabezado de registro en cada respuesta de análisis.

3. **Estableciste pautas de seguridad para la IA**, incluyendo moderación de contenido, mensajes de respuesta fuera de alcance y el tópico prioritario de respuesta a emergencias.

4. **Conectaste el agente con fuentes de conocimiento en SharePoint** y verificaste que los documentos de EHS generados en la Práctica 1 son accesibles y citados en las respuestas.

5. **Validaste el comportamiento del agente** mediante cuatro pruebas de conversación estructuradas que verificaron: respuesta dentro del dominio, rechazo de consultas fuera de alcance, escalamiento ante emergencias y citación de fuentes normativas.

### Conexión con las Prácticas Siguientes

| Práctica | Qué construirás sobre este laboratorio |
|---|---|
| **Práctica 6** | Añadirás tópicos de conversación especializados para análisis de incidentes y verificación de cumplimiento normativo. |
| **Práctica 7** | Conectarás el agente con Power Automate para ejecutar acciones automatizadas (envío de alertas, generación de reportes). |
| **Práctica 8** | Integrarás el agente en Microsoft Teams para que el personal de planta pueda consultarlo directamente desde su canal de seguridad. |

### Recursos de Referencia

| Recurso | Descripción | URL |
|---|---|---|
| Documentación oficial de Copilot Studio | Guía completa de creación y configuración de agentes | [learn.microsoft.com/es-es/microsoft-copilot-studio](https://learn.microsoft.com/es-es/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) |
| Guía de prompt engineering | Mejores prácticas para instrucciones de sistema | [platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering) |
| ISO 45001:2018 | Sistemas de gestión de seguridad y salud en el trabajo | [iso.org/iso-45001](https://www.iso.org/iso-45001-occupational-health-and-safety.html) |
| IA responsable en entornos industriales | Principios de Microsoft para IA responsable | [learn.microsoft.com/es-es/azure/machine-learning/concept-responsible-ai](https://learn.microsoft.com/es-es/azure/machine-learning/concept-responsible-ai) |
| Conectores de SharePoint en Power Platform | Configuración de fuentes de conocimiento externas | [learn.microsoft.com/es-es/connectors/sharepointonline](https://learn.microsoft.com/es-es/connectors/sharepointonline/) |

---

> **Nota final para el instructor:** Si algún participante no logró completar satisfactoriamente este laboratorio (menos de 18/20 ítems en la lista de verificación final), proporciona el archivo de *checkpoint* `EHS_Risk_Evaluator_Checkpoint_Lab05.zip` que contiene la configuración exportada del agente en el estado correcto al finalizar esta práctica. El participante debe importarlo en su entorno antes de iniciar la Práctica 6.
