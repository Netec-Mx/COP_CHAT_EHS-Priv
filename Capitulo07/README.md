# Conexión de Copilot para Enviar Reportes por Email

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 90 minutos |
| **Complejidad** | Intermedia |
| **Audiencia** | Personal de las áreas de EHS, Seguridad Patrimonial, Ingeniería y Mantenimiento que requiera optimizar sus tiempos de comunicación, envío de alertas y reportes a la alta gerencia. |
| **Tecnologías** | Microsoft Copilot (M365 / Interfaz de Chat con integraciones) y Microsoft Outlook. |
| **Enfoque** | Comunicación corporativa en crisis, automatización de minutas, redacción ejecutiva de alertas y gestión de bandejas por lenguaje natural. |

---

## 2. Descripción Corta

Este laboratorio de 90 minutos enseña a los profesionales de operaciones a potenciar su productividad utilizando Microsoft Copilot como un puente automatizado de comunicación por correo electrónico. A través de un flujo estructurado de 5 pasos, los participantes aprenderán a redactar de forma instantánea correos de notificación de incidentes críticos, transformar apuntes desordenados de planta en minutas ejecutivas listas para enviar, programar plantillas de seguimiento de auditorías y auditar correos largos de EHS. El taller cierra con un reto autónomo para estructurar un correo de crisis ante un comité directivo.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Redactar notificaciones e informes de incidentes en tiempo récord** con la estructura corporativa adecuada para alta gerencia.
* **Convertir notas de campo informales en correos formales** de seguimiento de compromisos (Minutas CAPA).
* **Utilizar Copilot en Outlook** para resumir hilos largos de correos y extraer tareas críticas de seguridad pendientes.
* **Diseñar plantillas de comunicación preventiva** adaptadas a diferentes niveles de la organización (operarios vs. directores).

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot** y **Microsoft Outlook**.
* Aplicación de **Microsoft Word** abierta con un documento en blanco guardado como `Bitacora_Automatizacion_Correos.docx` (para respaldar los prompts y resultados).

---

## 5. Procedimiento Paso a Paso

### Paso 1: Generación Flash de Notificación de Incidente Crítico (Alerta Roja)

Cuando ocurre un incidente de EHS o Seguridad Patrimonial, la velocidad de notificación es vital, pero debe mantener un tono corporativo exacto para evitar el pánico y activar los protocolos correctos.

1. Abra el chat de **Microsoft Copilot** (si su organización cuenta con Copilot con protección de datos comerciales o Copilot para M365, asegúrese de iniciar sesión).
2. Introduzca el siguiente prompt avanzado de redacción urgente:

```
Actúa como un Director de Comunicaciones de EHS y Gestión de Crisis. Necesito redactar un correo electrónico urgente para enviar a todo el Comité de Operaciones y Gerencia de Planta.

El correo debe notificar la siguiente situación real ocurrida hace 15 minutos:
"Se presentó un amago de incendio en el tablero eléctrico principal del pasillo B debido a un sobrecalentamiento. El equipo de brigadistas actuó de inmediato con extintores de CO2, controlando la situación por completo. No hay heridos, pero la línea de empaque 2 se encuentra detenida temporalmente por seguridad mientras Mantenimiento evalúa los daños."

Estructura el correo con:
1. Un asunto directo y de alta prioridad (usa etiquetas como [ALERTA DE SEGURIDAD]).
2. Un saludo formal.
3. El cuerpo del mensaje dividido en tres viñetas claras: Qué pasó, Estatus actual de la planta y Medidas tomadas.
4. Un cierre donde indiques que se enviará un informe técnico detallado al final del turno.

Usa un tono institucional, claro, asertivo y de control.
```

3. Copie el correo generado por Copilot, abra **Microsoft Outlook**, pegue el contenido en un nuevo correo y verifique cómo la estructura permite una lectura analítica en menos de 10 segundos. Respalde el texto en su archivo de Word.

---

### Paso 2: Transformación de Notas de Campo a Minuta Ejecutiva de Compromisos

Después de un recorrido de seguridad en el piso de producción, los supervisores suelen quedarse con anotaciones rápidas. Utilizaremos Copilot para procesar esos apuntes informales y estructurar un correo formal de asignación de tareas.

1. Introduzca el siguiente prompt en el chat de Copilot:

```
Actúa como un Facilitador de Procesos EHS y Gestión de Proyectos. Tengo las siguientes anotaciones informales que tomé en mi libreta durante la auditoría de hoy:
"Revisión patio: Juan de mantenimiento se compromete a cambiar las 3 luminarias fundidas antes del viernes. En el área de molienda el piso está resbaloso por aceite, hablé con Carlos de operaciones y dice que mandará limpiar hoy mismo antes de las 4 pm. Falta señalética en la salida de emergencia de prensas, anoté a ingeniería para que lo resuelva la otra semana."

Necesito que transformes estas notas en un correo formal de seguimiento dirigido a los involucrados con copia al Gerente de Planta.
Estructúralo en una tabla limpia dentro del correo que contenga: Acción Obligatoria | Responsable | Fecha Límite.
Agrega un párrafo inicial amable pero firme recordando que el cumplimiento de estas acciones previene multas normativas.

Dame el contenido listo para copiar y enviar.
```

2. Copie la respuesta y valide la conversión de lenguaje informal a una matriz corporativa de responsabilidades. Copie la evidencia a su documento de Word.

---

### Paso 3: Resumen Inteligente de Hilos de Correo y Extracción de Pendientes

Muchas veces, los profesionales de planta regresan de sus días de descanso y encuentran cadenas kilométricas de correos sobre un problema de seguridad. Simularemos cómo usar Copilot para resumir y obtener acciones directas.

1. Introduzca el siguiente prompt en el chat de Copilot simulando un hilo de conversación de Outlook:

```
Actúa como un Asistente Ejecutivo de Operaciones Industriales. Necesito que analices el siguiente historial de correos cruzados entre el equipo y extraigas los puntos clave:

"[Correo 1 - Lunes] Auditor: Detectamos que la alarma contra incendios del almacén sur no suena en las pruebas. [Correo 2 - Martes] Proveedor: Fuimos a revisar y es una falla en la tarjeta principal, la pieza tarda 3 días en llegar. [Correo 3 - Miércoles] Gerente de EHS: No podemos operar el almacén sur sin sistema de alerta. Propongo guardias físicos haciendo rondines cada hora con megáfono portatil en lo que llega la pieza. [Correo 4 - Jueves] Jefe de Seguridad Patrimonial: De acuerdo, ya asigné a dos guardias del turno nocturno para cubrir esa zona a partir de hoy."

Entrégame un resumen ejecutivo de este hilo en español bajo tres puntos:
1. ¿Cuál es el problema raíz?
2. ¿Cuál fue la solución provisional acordada y quién la ejecuta?
3. ¿Cuál es la acción definitiva pendiente por monitorear?

Sé extremadamente breve, entregando solo las respuestas directas.
```

2. Evalúe la capacidad de síntesis de la IA para ahorrar tiempo de lectura en la bandeja de entrada. Guarde el resultado en su bitácora.

---

### Paso 4: Redacción de Comunicado Masivo de Concientización Operativa

El equipo de seguridad debe enviar constantemente campañas de prevención. En este paso, programaremos a Copilot para que redacte un mensaje masivo dirigido a todo el personal técnico de la planta, utilizando analogías sencillas y un tono cercano.

1. Introduzca el siguiente prompt en el chat de Copilot:

```
Actúa como un Coordinador de Cultura de Seguridad Laboral. Necesito redactar un correo institucional pero muy empático y cercano, dirigido a todo el personal operativo de los tres turnos de la planta.

El objetivo del correo es recordar la obligatoriedad del uso correcto de los lentes de seguridad en el piso de producción, debido a un ligero incremento en reportes de partículas en los ojos durante la última semana.
Usa una analogía simple (por ejemplo, cómo los lentes son el parabrisas de su propia visión). 

El correo debe incluir:
- Un asunto llamativo pero respetuoso.
- 3 reglas de oro para el cuidado de sus lentes (limpieza, guardado y reporte de daños).
- Un cierre motivacional que recuerde que en casa los esperan sanos y salvos.

Evita palabras excesivamente técnicas; busca conectar con el trabajador.
```

2. Copie el texto generado y observe cómo cambia el estilo de comunicación de Copilot al pasar de un correo directivo (Paso 1) a uno enfocado en el factor humano de la planta.

---

### Paso 5: Reto de Aplicación Autónoma – Diseño del Prompt de Respuesta Automática en Crisis Patrimonial

**Instrucciones para el estudiante:** Se ha reportado una falla general en el sistema de barreras vehiculares de la entrada principal de la planta (se quedaron abiertas y no responden al control digital), comprometiendo el control de accesos patrimoniales. Como encargado de la seguridad, debes enviar un correo de alerta inmediata al equipo de guardias y supervisores de turno para activar el protocolo de contingencia manual.

#### El Desafío:
Consolidando lo aprendido sobre comunicación estructurada y automatización de correos a través de la IA, vas a diseñar tu propio prompt desde cero en Copilot:

1. **Diseño del Prompt Autónomo:** Redacte una instrucción en Copilot solicitándole un correo que notifique la falla de las barreras vehiculares perimetrales.
2. **Requisitos de su Prompt:** Debe exigirle a la IA que el correo incluya:
   * Un asunto que marque claramente [CONTINGENCIA PATRIMONIAL].
   * La orden explícita de activar el "Protocolo de Cierre Manual" (colocación de cadenas, candados físicos y registro obligatorio a mano de cada placa de vehículo).
   * La asignación de la revisión técnica urgente al equipo de Mantenimiento de Sistemas.
3. **Validación del Éxito:** Ejecute su prompt en Copilot, copie el correo institucional que este le devuelva y péguelo en la sección final de su archivo de Word como evidencia de que sabe dirigir a la IA para resolver crisis de comunicación operativa en la empresa.

---

## 6. Conceptos Clave para Recordar

* **Comunicación Asertiva en Crisis:** Capacidad de estructurar mensajes de alta prioridad informando un incidente con total transparencia, pero delimitando las acciones de control de forma inmediata para mantener el orden institucional.
* **Minuta de Compromisos Operativos:** Formato condensado de comunicación que traduce conversaciones u observaciones en un plan de acción directo con responsables y fechas fatales asignadas.
* **Tono y Estilo de Redacción:** Adaptación del vocabulario y la estructura del mensaje según la audiencia final (directores, proveedores o personal de operaciones) para garantizar que el mensaje logre el impacto buscado.

---

## 7. Resultado Esperado del Estudiante

Para validar la correcta conclusión de esta práctica avanzada de automatización de flujos de comunicación, el estudiante guardará en su repositorio:

1. **Archivo `Bitacora_Automatizacion_Correos.docx` (Word):**
   * El documento técnico completo que resguarda el correo de Alerta Roja (Paso 1), la tabla de responsabilidades generada desde apuntes de campo (Paso 2), el resumen ejecutivo del caso de las alarmas (Paso 3) y el comunicado masivo de concientización (Paso 4).
   * La sección final de la bitácora debe contener el prompt diseñado de forma autónoma y la respuesta del correo de contingencia patrimonial para las barreras vehiculares (Paso 5).
