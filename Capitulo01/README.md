# Creación de instrucciones precisas para la elaboración y revisión de documentos y políticas, permitiendo que la IA actúe como un redactor técnico capaz de estructurar manuales operativos y procedimientos de seguridad alineados con los estándares de la empresa.

---

## 1. Metadatos

| Atributo | Detalle |
|---|---|
| **Duración estimada** | 60 minutos |
| **Complejidad** | Fácil |
| **Nivel Bloom** | Aplicar (*Apply*) |
| **Módulo** | Módulo 1 — Introducción a Copilot y Redacción Técnica EHS |
| **Laboratorio ID** | 01-00-01 |
| **Modalidad** | Individual, guiado por instructor |

---

## 2. Descripción General

En este laboratorio los participantes darán sus primeros pasos prácticos con Microsoft 365 Copilot en el contexto de EHS y Seguridad Patrimonial. Comenzarán revisando los principios de privacidad de datos que rigen el uso corporativo de Copilot —incluyendo el modelo de herencia de permisos y la obligación de anonimizar información sensible— para luego aplicar técnicas de *prompt engineering* estructurado dentro de Microsoft Word. A través de tres ejercicios progresivos, los participantes generarán un procedimiento de trabajo seguro en altura, lo refinarán mediante técnicas avanzadas de prompting y, finalmente, revisarán una política de seguridad patrimonial preexistente utilizando Copilot como asistente de auditoría documental. Todos los documentos producidos se guardarán en SharePoint para ser reutilizados en prácticas posteriores del curso.

---

## 3. Objetivos de Aprendizaje

Al finalizar este laboratorio, el participante será capaz de:

- [ ] **Identificar** los principios de privacidad de datos de Microsoft 365 Copilot (aislamiento del *tenant*, herencia de permisos, no reutilización de datos) y aplicarlos mediante el uso de datos ficticios y anonimizados durante toda la práctica.
- [ ] **Construir** prompts estructurados con los cinco componentes clave —contexto, rol, tarea, formato y restricciones— para generar documentos técnicos EHS de calidad profesional.
- [ ] **Utilizar** Copilot en Microsoft Word para generar y estructurar un procedimiento de seguridad para trabajo en altura, aplicando al menos dos iteraciones de refinamiento del prompt.
- [ ] **Aplicar** Copilot como revisor técnico para identificar brechas e inconsistencias en una política de seguridad patrimonial preexistente y generar sugerencias de mejora documentadas.
- [ ] **Guardar** los documentos producidos en la biblioteca de SharePoint del curso, asegurando su disponibilidad para laboratorios posteriores.

---

## 4. Prerrequisitos

### Conocimientos Previos

| Área | Nivel requerido |
|---|---|
| Uso general de Microsoft Word | Básico (crear, editar y guardar documentos) |
| Navegación en Microsoft 365 (OneDrive / SharePoint) | Básico (acceder a bibliotecas de documentos) |
| Conceptos de EHS (procedimientos de seguridad, políticas corporativas) | Básico (comprensión general del dominio) |
| Lectura del material de la Lección 1.1 | **Obligatorio** — revisar antes de iniciar este laboratorio |

### Accesos y Licencias Requeridos

| Recurso | Estado requerido |
|---|---|
| Cuenta corporativa de Microsoft 365 | ✅ Activa y con sesión iniciada |
| Licencia Microsoft 365 Copilot | ✅ Habilitada y verificada (panel de Copilot visible en Word) |
| Acceso a la biblioteca de SharePoint del curso | ✅ Confirmado por el instructor antes del inicio |
| Archivo de práctica `POL-SEG-PATRIMONIAL-v1.docx` | ✅ Cargado en SharePoint por el instructor |

> ⚠️ **Nota crítica:** Si el panel de Copilot no aparece en Word, detén la práctica e informa al instructor antes de continuar. Sin la licencia activa, ningún ejercicio de este laboratorio puede ejecutarse.

---

## 5. Entorno del Laboratorio

### Hardware Recomendado

| Componente | Especificación mínima |
|---|---|
| Procesador | Intel Core i5 8ª gen. / AMD Ryzen 5 o superior |
| Memoria RAM | 8 GB (recomendado: 16 GB) |
| Resolución de pantalla | 1920 × 1080 |
| Conexión a Internet | 10 Mbps estable |
| Almacenamiento libre | 10 GB en disco |

### Software Requerido

| Aplicación | Versión / Acceso |
|---|---|
| Microsoft Word | Microsoft 365 Apps for Enterprise (canal actual) |
| Microsoft 365 Copilot | Integrado en Word — panel lateral activo |
| Microsoft SharePoint Online | Acceso vía navegador o integración en Word |
| Microsoft Edge | Versión estable más reciente (recomendado) |

### Configuración Inicial del Entorno

Antes de comenzar los ejercicios, completa los siguientes pasos de configuración. Estos pasos no cuentan dentro del tiempo de los ejercicios.

**Paso de configuración 1 — Verificar sesión de Microsoft 365:**

1. Abre **Microsoft Edge**.
2. Navega a `https://www.office.com`.
3. Confirma que la sesión está iniciada con tu cuenta corporativa (el avatar o iniciales deben aparecer en la esquina superior derecha).

**Paso de configuración 2 — Acceder a la biblioteca de SharePoint del curso:**

1. En la barra de direcciones de Edge, navega a la URL de SharePoint proporcionada por el instructor. La URL tendrá el formato:
   ```
   https://<tenant>.sharepoint.com/sites/CursoEHS-Copilot/Documentos compartidos/
   ```
2. Verifica que puedes ver los siguientes archivos en la carpeta `Lab01`:
   - `POL-SEG-PATRIMONIAL-v1.docx` (política preexistente para el Ejercicio 3)
   - `REFERENCIA-NORMAS-EHS.docx` (documento de referencia normativa)
3. Si no ves estos archivos, informa al instructor de inmediato.

**Paso de configuración 3 — Abrir Word y verificar Copilot:**

1. Abre **Microsoft Word** desde el menú de aplicaciones de Microsoft 365 (`https://www.office.com` → ícono de Word).
2. Crea un documento en blanco **directamente en OneDrive** (no en el disco local):
   - Selecciona **Nuevo** → **Documento en blanco**.
   - Word debe guardarlo automáticamente en OneDrive. Verifica que la barra de título muestre el nombre del archivo con la ruta de OneDrive.
3. Confirma que el botón o panel de **Copilot** es visible:
   - En la cinta de opciones (*ribbon*), busca el ícono de Copilot (generalmente en la pestaña **Inicio** o **Vista**).
   - Alternativamente, busca el panel lateral de Copilot en el lado derecho de la ventana de Word.

> 💡 **Recordatorio de privacidad (de la Lección 1.1):** Durante toda esta práctica utilizarás **exclusivamente datos ficticios**. Está prohibido ingresar nombres reales de empleados, datos personales identificables o información confidencial real de la empresa en ningún prompt de Copilot.

---

## 6. Pasos del Laboratorio

---

### Ejercicio 1: Generación de un Procedimiento de Seguridad con un Prompt Básico

**Objetivo del ejercicio:** Experimentar con un prompt simple para comprender las capacidades y limitaciones de Copilot cuando las instrucciones no están suficientemente estructuradas. Este ejercicio sirve como línea base para comparar con el Ejercicio 2.

**Tiempo estimado:** 15 minutos

---

#### Instrucciones

**1.1 — Preparar el documento de trabajo:**

1. En el documento en blanco que creaste durante la configuración, escribe el siguiente título en la primera línea:
   ```
   BORRADOR - Procedimiento Trabajo en Altura - Versión 1 (Prompt Básico)
   ```
2. Aplica el estilo **Título 1** a esta línea (pestaña **Inicio** → grupo **Estilos** → **Título 1**).
3. Guarda el archivo con el nombre:
   ```
   Lab01_EJ1_TrabajoenAltura_PromptBasico.docx
   ```
   Asegúrate de guardarlo en tu **OneDrive** o en la biblioteca de SharePoint del curso (carpeta `Lab01/Mis Documentos`).

**1.2 — Abrir el panel de Copilot en Word:**

1. Haz clic en el ícono de **Copilot** en la cinta de opciones. El panel lateral de Copilot se abrirá en el lado derecho de la pantalla.
2. Confirma que el panel muestra un campo de texto para ingresar prompts y el mensaje de bienvenida de Copilot.

**1.3 — Ingresar el prompt básico:**

1. En el campo de texto del panel de Copilot, escribe el siguiente prompt **exactamente como se muestra**:

   ```
   Escribe un procedimiento de seguridad para trabajo en altura.
   ```

2. Presiona **Enter** o haz clic en el botón de enviar.
3. Espera a que Copilot genere la respuesta. Este proceso puede tomar entre 10 y 30 segundos.

**1.4 — Insertar el contenido generado en el documento:**

1. Revisa el texto generado por Copilot en el panel lateral.
2. Haz clic en el botón **Insertar** (o el equivalente que aparezca en la interfaz de Copilot) para añadir el contenido al documento de Word.
3. Guarda el documento con **Ctrl + S**.

**1.5 — Analizar y anotar las limitaciones observadas:**

1. Lee el documento generado con atención crítica.
2. Al final del documento, agrega una sección con el título **"Observaciones del Ejercicio 1"** y responde las siguientes preguntas en formato de lista:
   - ¿El procedimiento incluye referencias a normas específicas (OSHA, NOM, ISO)?
   - ¿Tiene una estructura de secciones claramente definida (objetivo, alcance, responsabilidades, pasos, EPP)?
   - ¿Menciona el tipo de industria o contexto específico?
   - ¿El nivel de detalle técnico es suficiente para uso real en planta?
3. Guarda el documento nuevamente.

---

**Resultado esperado del Ejercicio 1:**

Copilot generará un procedimiento genérico de trabajo en altura con información básica pero sin estructura formal definida, sin referencias normativas específicas y sin adaptación al contexto industrial. Este resultado limitado es **intencional y esperado**: sirve para demostrar la importancia del prompt engineering que se aplicará en el Ejercicio 2.

**Verificación del Ejercicio 1:**

- [ ] El archivo `Lab01_EJ1_TrabajoenAltura_PromptBasico.docx` existe en OneDrive/SharePoint.
- [ ] El documento contiene el texto generado por Copilot a partir del prompt básico.
- [ ] La sección "Observaciones del Ejercicio 1" está completa con al menos 4 respuestas anotadas.
- [ ] El participante puede identificar verbalmente al menos 2 limitaciones del prompt básico.

---

### Ejercicio 2: Refinamiento del Procedimiento Mediante Prompt Engineering Avanzado

**Objetivo del ejercicio:** Aplicar la anatomía completa de un prompt efectivo (contexto, rol, tarea, formato y restricciones) para generar un procedimiento de trabajo en altura de calidad profesional, comparándolo con el resultado del Ejercicio 1.

**Tiempo estimado:** 20 minutos

---

#### La Anatomía de un Prompt Efectivo para EHS

Antes de escribir el prompt avanzado, revisa la siguiente tabla con los cinco componentes que debe incluir un prompt estructurado para documentos técnicos EHS:

| Componente | Descripción | Ejemplo aplicado |
|---|---|---|
| **Contexto** | Describe el entorno, la industria y las condiciones relevantes | "Planta de manufactura automotriz con trabajo en estructuras metálicas a más de 1.8 metros de altura" |
| **Rol** | Define el papel que debe asumir Copilot | "Actúa como un redactor técnico especializado en EHS con experiencia en normas OSHA y NOM-009" |
| **Tarea** | Especifica claramente qué debe producir | "Redacta un Procedimiento de Trabajo Seguro (PTS) completo" |
| **Formato** | Indica la estructura, extensión y estilo del documento | "Organizado en secciones numeradas: Objetivo, Alcance, Definiciones, Responsabilidades, Equipo de Protección Personal, Procedimiento paso a paso, Restricciones y Referencias normativas" |
| **Restricciones** | Establece límites, exclusiones y requisitos obligatorios | "Usa datos ficticios. No incluyas nombres reales. El documento debe ser aplicable a México y cumplir con NOM-009-STPS-2011" |

---

#### Instrucciones

**2.1 — Crear un nuevo documento de trabajo:**

1. Abre un **nuevo documento en blanco** en Word (desde OneDrive).
2. Escribe el título:
   ```
   PTS-001 - Procedimiento de Trabajo Seguro en Altura - Versión 2 (Prompt Avanzado)
   ```
3. Guarda el archivo como:
   ```
   Lab01_EJ2_TrabajoenAltura_PromptAvanzado.docx
   ```
   en la carpeta `Lab01/Mis Documentos` de SharePoint/OneDrive.

**2.2 — Construir y aplicar el prompt avanzado (Iteración 1):**

1. Abre el panel de **Copilot** en Word.
2. Ingresa el siguiente prompt estructurado. Puedes copiarlo y adaptarlo:

   ```
   Actúa como un redactor técnico especializado en EHS (Environment, Health & Safety) 
   con experiencia en normativa mexicana de seguridad industrial.

   Contexto: Una planta de manufactura automotriz ficticia llamada "AutoSegura S.A. de C.V." 
   necesita un Procedimiento de Trabajo Seguro (PTS) para actividades de mantenimiento 
   en estructuras metálicas a alturas superiores a 1.8 metros.

   Tarea: Redacta el PTS completo con lenguaje técnico formal, apropiado para ser 
   utilizado por supervisores de seguridad y operadores de mantenimiento.

   Formato requerido — El documento debe incluir las siguientes secciones numeradas:
   1. Objetivo
   2. Alcance
   3. Definiciones clave
   4. Responsabilidades (Supervisor EHS, Trabajador, Jefe de área)
   5. Equipo de Protección Personal (EPP) requerido
   6. Procedimiento paso a paso (mínimo 10 pasos detallados)
   7. Condiciones que suspenden el trabajo
   8. Restricciones y prohibiciones
   9. Referencias normativas

   Restricciones obligatorias:
   - Usa únicamente datos ficticios (empresa, nombres de cargos genéricos, sin personas reales).
   - El procedimiento debe hacer referencia a la norma mexicana NOM-009-STPS-2011 
     (Trabajo en altura — Condiciones de seguridad).
   - Incluye al menos una referencia adicional a estándares internacionales (OSHA 1926.502 
     o equivalente).
   - El tono debe ser imperativo y técnico, adecuado para un documento normativo interno.
   - Extensión aproximada: 600-800 palabras.
   ```

3. Presiona **Enter** y espera la respuesta de Copilot.
4. Haz clic en **Insertar** para añadir el contenido al documento.
5. Guarda el documento con **Ctrl + S**.

**2.3 — Evaluar el resultado de la Iteración 1:**

1. Lee el documento generado y evalúa si cumple con todos los componentes del prompt.
2. Identifica al menos **dos aspectos** que podrían mejorarse. Ejemplos comunes:
   - Las definiciones son demasiado genéricas.
   - Los pasos del procedimiento no mencionan el uso de arnés de seguridad específicamente.
   - Las referencias normativas están incompletas.

**2.4 — Aplicar el prompt de refinamiento (Iteración 2):**

1. En el panel de Copilot, ingresa un prompt de refinamiento basado en las mejoras identificadas. Usa el siguiente modelo como guía, adaptándolo según tus observaciones reales:

   ```
   El procedimiento generado necesita mejoras específicas. Por favor, modifica 
   el documento con los siguientes cambios:

   1. En la sección "Definiciones clave", agrega definiciones técnicas precisas para: 
      "punto de anclaje certificado", "línea de vida", "factor de caída" y "zona de peligro".

   2. En la sección "Procedimiento paso a paso", asegúrate de que los pasos 3, 4 y 5 
      describan explícitamente el proceso de inspección y colocación del arnés de 
      seguridad tipo cuerpo completo, incluyendo los puntos de verificación obligatorios.

   3. En la sección "Referencias normativas", agrega la referencia completa a la 
      NOM-009-STPS-2011 con su título oficial y el organismo emisor (STPS México).

   Mantén el resto del documento sin cambios. Usa únicamente datos ficticios.
   ```

2. Presiona **Enter** y espera la respuesta.
3. Revisa los cambios sugeridos por Copilot.
4. Aplica los cambios al documento (usa el botón **Insertar** o copia manualmente las secciones mejoradas).
5. Guarda el documento.

**2.5 — Comparar los resultados con el Ejercicio 1:**

1. Abre en paralelo el documento `Lab01_EJ1_TrabajoenAltura_PromptBasico.docx` (del Ejercicio 1).
2. Compara ambos documentos lado a lado (puedes usar la función **Vista → Ver en paralelo** de Word, o usar un segundo monitor si está disponible).
3. Al final del documento del Ejercicio 2, agrega una sección titulada **"Análisis Comparativo EJ1 vs EJ2"** y completa la siguiente tabla:

   | Criterio de evaluación | Ejercicio 1 (Prompt básico) | Ejercicio 2 (Prompt avanzado) |
   |---|---|---|
   | Estructura de secciones definida | ¿Sí / No / Parcial? | ¿Sí / No / Parcial? |
   | Referencias normativas específicas | ¿Sí / No / Parcial? | ¿Sí / No / Parcial? |
   | Definiciones técnicas incluidas | ¿Sí / No / Parcial? | ¿Sí / No / Parcial? |
   | Pasos de procedimiento detallados (≥10) | ¿Sí / No / Parcial? | ¿Sí / No / Parcial? |
   | Adaptado al contexto industrial | ¿Sí / No / Parcial? | ¿Sí / No / Parcial? |
   | Uso de datos ficticios | ¿Sí / No / Parcial? | ¿Sí / No / Parcial? |

4. Guarda el documento final.

---

**Resultado esperado del Ejercicio 2:**

El documento generado mediante el prompt avanzado debe mostrar una mejora cualitativa significativa respecto al Ejercicio 1: estructura formal por secciones numeradas, referencias a NOM-009-STPS-2011 y OSHA, definiciones técnicas precisas, pasos de procedimiento detallados y tono imperativo apropiado para un PTS profesional. La tabla comparativa debe evidenciar la diferencia entre ambos enfoques.

**Verificación del Ejercicio 2:**

- [ ] El archivo `Lab01_EJ2_TrabajoenAltura_PromptAvanzado.docx` existe en OneDrive/SharePoint.
- [ ] El documento contiene las 9 secciones especificadas en el prompt.
- [ ] Se realizaron al menos 2 iteraciones de refinamiento (el documento refleja cambios de la Iteración 2).
- [ ] La sección "Análisis Comparativo EJ1 vs EJ2" está completa con la tabla llena.
- [ ] El documento no contiene datos personales reales ni información confidencial de ninguna empresa real.

---

### Ejercicio 3: Revisión y Mejora de una Política de Seguridad Patrimonial con Copilot

**Objetivo del ejercicio:** Utilizar Copilot como asistente de auditoría documental para revisar una política de seguridad patrimonial preexistente, identificar brechas e inconsistencias, y generar un documento de mejoras estructurado.

**Tiempo estimado:** 20 minutos

---

#### Contexto del Ejercicio

En este ejercicio trabajarás con el archivo `POL-SEG-PATRIMONIAL-v1.docx`, una política ficticia de seguridad patrimonial preparada por el instructor que contiene intencionalmente algunas brechas y áreas de mejora. Tu tarea es usar Copilot para auditar este documento y generar recomendaciones formales.

> 📋 **Sobre el archivo de práctica:** Este documento es completamente ficticio y fue diseñado para fines didácticos. Representa la política de seguridad patrimonial de una empresa ficticia llamada "Grupo Industrial Ficticio S.A." No contiene información real de ninguna organización.

---

#### Instrucciones

**3.1 — Abrir el archivo de política preexistente desde SharePoint:**

1. En Microsoft Edge, navega a la biblioteca de SharePoint del curso.
2. Localiza el archivo `POL-SEG-PATRIMONIAL-v1.docx` en la carpeta `Lab01`.
3. Haz clic en el archivo para abrirlo directamente en **Microsoft Word Online** o en la aplicación de escritorio de Word (ambas opciones son válidas).

   > ⚠️ **Importante:** Abre el archivo directamente desde SharePoint, NO lo descargues al disco local. Copilot solo funciona con archivos almacenados en la nube (OneDrive/SharePoint).

4. Una vez abierto, haz clic en **Editar** si el archivo se abre en modo de solo lectura.
5. Guarda una copia de trabajo con el nombre:
   ```
   Lab01_EJ3_PolSegPatrimonial_Revisada.docx
   ```
   en la carpeta `Lab01/Mis Documentos` de SharePoint.

**3.2 — Leer el documento y hacer anotaciones preliminares:**

1. Lee el documento completo (aproximadamente 2-3 minutos).
2. Mientras lees, toma nota mental o en papel de:
   - Secciones que parecen incompletas o vagas.
   - Ausencia de referencias a normas o marcos legales.
   - Responsabilidades que no están claramente asignadas.
   - Procedimientos de respuesta a incidentes que no están definidos.

**3.3 — Usar Copilot para auditar el documento (Prompt de Revisión):**

1. Abre el panel de **Copilot** en Word.
2. Ingresa el siguiente prompt de auditoría:

   ```
   Actúa como un auditor experto en sistemas de gestión de seguridad patrimonial 
   y seguridad corporativa, con conocimiento en normas ISO 31000 (Gestión de Riesgos) 
   y mejores prácticas internacionales de seguridad física.

   Contexto: El documento actualmente abierto es una política de seguridad patrimonial 
   de una empresa industrial ficticia. Necesito que lo revises de forma crítica.

   Tarea: Analiza el documento completo e identifica:
   1. Brechas o secciones faltantes que debería tener una política de seguridad 
      patrimonial completa.
   2. Inconsistencias internas (contradicciones entre secciones o afirmaciones 
      que se contradicen entre sí).
   3. Áreas donde el lenguaje es vago o ambiguo y debería ser más preciso.
   4. Referencias normativas o marcos legales que deberían incluirse pero están ausentes.
   5. Roles y responsabilidades que no están claramente definidos.

   Formato de respuesta requerido:
   Presenta los hallazgos en una tabla con tres columnas:
   - Columna 1: "Sección / Área del documento"
   - Columna 2: "Tipo de hallazgo" (Brecha / Inconsistencia / Ambigüedad / Normativa faltante / Rol indefinido)
   - Columna 3: "Descripción del hallazgo y recomendación de mejora"

   Incluye al menos 5 hallazgos específicos. Usa un tono formal y técnico.
   ```

3. Presiona **Enter** y espera la respuesta de Copilot.
4. Revisa la tabla de hallazgos generada. Si algún hallazgo no es claro, puedes pedir a Copilot que lo amplíe con un prompt de seguimiento como:

   ```
   Por favor, amplía el hallazgo número [X] con un ejemplo concreto de cómo 
   debería redactarse la sección mejorada.
   ```

5. Inserta la tabla de hallazgos en el documento de trabajo.

**3.4 — Generar el documento de mejoras (Prompt de Reescritura):**

1. Elige **uno** de los hallazgos identificados en el paso anterior (preferiblemente el más relevante o el que el instructor indique).
2. Ingresa el siguiente prompt de reescritura, adaptándolo al hallazgo elegido:

   ```
   Basándote en el hallazgo identificado sobre [describe brevemente el hallazgo elegido], 
   redacta la sección mejorada para la política de seguridad patrimonial.

   Requisitos:
   - La sección debe estar escrita en lenguaje técnico formal, apropiado para una 
     política corporativa.
   - Debe incluir: propósito de la sección, responsable(s) asignado(s), 
     procedimiento o directriz específica, y criterio de cumplimiento.
   - Incorpora una referencia al marco normativo aplicable (ISO 31000 o equivalente).
   - Usa únicamente datos ficticios (empresa ficticia: "Grupo Industrial Ficticio S.A.").
   - Extensión aproximada: 150-250 palabras para la sección.
   ```

3. Inserta la sección mejorada en el documento, marcándola claramente con el encabezado:
   ```
   [SECCIÓN MEJORADA - Generada con Copilot - Pendiente de revisión humana]
   ```

**3.5 — Agregar nota de revisión humana obligatoria:**

1. Al final del documento, agrega una sección titulada **"Notas de Revisión y Validación"** con el siguiente contenido (puedes adaptarlo):

   ```
   AVISO IMPORTANTE:
   Este documento ha sido revisado y parcialmente generado con asistencia de 
   Microsoft 365 Copilot como herramienta de apoyo. De acuerdo con los principios 
   de uso responsable de IA en entornos corporativos (Lección 1.1), TODO el contenido 
   generado por Copilot debe ser revisado, validado y aprobado por el profesional 
   de EHS responsable antes de su implementación oficial.

   Fecha de revisión asistida por IA: [fecha actual]
   Revisor humano responsable: [Nombre del cargo — NO incluir nombre real]
   Estado del documento: BORRADOR — Pendiente de validación
   ```

2. Guarda el documento final con **Ctrl + S**.

---

**Resultado esperado del Ejercicio 3:**

El documento `Lab01_EJ3_PolSegPatrimonial_Revisada.docx` debe contener: (a) el texto original de la política, (b) una tabla de al menos 5 hallazgos de auditoría generados por Copilot, (c) al menos una sección reescrita y mejorada con la marca de revisión pendiente, y (d) la nota de validación humana al final. Este documento demuestra el flujo completo de uso responsable de Copilot como herramienta de apoyo —no de reemplazo— del criterio profesional.

**Verificación del Ejercicio 3:**

- [ ] El archivo `Lab01_EJ3_PolSegPatrimonial_Revisada.docx` existe en la carpeta `Lab01/Mis Documentos` de SharePoint.
- [ ] El documento contiene la tabla de hallazgos con al menos 5 entradas.
- [ ] Al menos una sección mejorada está incluida con la marca `[SECCIÓN MEJORADA - Generada con Copilot - Pendiente de revisión humana]`.
- [ ] La sección "Notas de Revisión y Validación" está presente al final del documento.
- [ ] El documento no contiene datos personales reales ni información confidencial de empresas reales.

---

## 7. Validación y Pruebas Finales

Al concluir los tres ejercicios, realiza las siguientes verificaciones finales para confirmar que el laboratorio se completó satisfactoriamente:

### Lista de Verificación Final del Laboratorio

| # | Criterio de validación | Estado |
|---|---|---|
| 1 | `Lab01_EJ1_TrabajoenAltura_PromptBasico.docx` guardado en SharePoint/OneDrive | ☐ |
| 2 | `Lab01_EJ2_TrabajoenAltura_PromptAvanzado.docx` guardado en SharePoint/OneDrive | ☐ |
| 3 | `Lab01_EJ3_PolSegPatrimonial_Revisada.docx` guardado en SharePoint/OneDrive | ☐ |
| 4 | El documento del EJ2 contiene las 9 secciones del PTS especificadas en el prompt | ☐ |
| 5 | La tabla comparativa EJ1 vs EJ2 está completa en el documento del EJ2 | ☐ |
| 6 | La tabla de hallazgos del EJ3 contiene al menos 5 hallazgos | ☐ |
| 7 | Ningún documento contiene datos personales reales o información confidencial real | ☐ |
| 8 | El participante puede explicar la diferencia entre prompt básico y prompt estructurado | ☐ |
| 9 | El participante puede identificar los 5 componentes de un prompt efectivo | ☐ |
| 10 | El participante comprende por qué la revisión humana es obligatoria tras el uso de Copilot | ☐ |

### Pregunta de Reflexión Final

Antes de cerrar el laboratorio, responde brevemente (2-3 oraciones) en el chat del instructor o en el documento que el instructor indique:

> **¿Cómo aplicarías el principio de "herencia de permisos" de Microsoft 365 Copilot para proteger la confidencialidad de un informe de investigación de accidente que contiene datos médicos de un trabajador lesionado?**

Esta pregunta conecta directamente con los conceptos de privacidad de la Lección 1.1 y no tiene una única respuesta correcta: se evalúa el razonamiento aplicado.

---

## 8. Solución de Problemas

### Problema 1: El panel de Copilot no aparece en Microsoft Word

**Síntomas:**
- El ícono de Copilot no está visible en la cinta de opciones (*ribbon*) de Word.
- Al buscar "Copilot" en la búsqueda de comandos de Word, no aparece ninguna opción.
- El panel lateral de Copilot no se puede abrir.

**Causa probable:**
La licencia de Microsoft 365 Copilot no está asignada a la cuenta del usuario, o Copilot no ha sido habilitado para las aplicaciones de Microsoft 365 por el administrador de TI. También puede ocurrir si la versión de Word instalada no corresponde al canal actual de Microsoft 365 Apps for Enterprise.

**Solución:**
1. Verifica que la sesión de Microsoft 365 está iniciada con la cuenta corporativa correcta (no con una cuenta personal de Microsoft).
2. Cierra Word completamente y vuelve a abrirlo.
3. Navega a `https://www.office.com` → haz clic en tu avatar (esquina superior derecha) → **Ver cuenta** → verifica que la licencia de Copilot aparece en la lista de suscripciones activas.
4. Si la licencia no aparece, informa al instructor inmediatamente. El instructor deberá escalar al administrador de TI para verificar la asignación de licencia en el portal de administración de Microsoft 365 (`https://admin.microsoft.com`).
5. Como solución temporal, el participante puede usar **Copilot en Word Online** (versión web) accediendo desde `https://www.office.com` → Word → Nuevo documento. La funcionalidad de Copilot en la versión web es equivalente para los propósitos de este laboratorio.

---

### Problema 2: Copilot genera contenido con datos que parecen reales o sensibles

**Síntomas:**
- Copilot incluye en su respuesta nombres de personas, empresas o lugares que podrían ser reales (no ficticios).
- El contenido generado hace referencia a incidentes, accidentes o situaciones que parecen corresponder a eventos reales.
- El participante no está seguro de si el contenido generado proviene de información real almacenada en el *tenant* organizacional.

**Causa probable:**
Microsoft 365 Copilot tiene acceso a los documentos y datos almacenados en el *tenant* de la organización a los que el usuario tiene permisos (principio de herencia de permisos, Lección 1.1). Si en la biblioteca de SharePoint del curso existen documentos con información real (por error del instructor o del participante), Copilot puede incorporar ese contenido en sus respuestas. Alternativamente, el modelo de lenguaje puede generar nombres o datos que suenan reales pero son completamente ficticios (alucinaciones del modelo).

**Solución:**
1. **Detén inmediatamente** el uso de Copilot y no insertes el contenido sospechoso en ningún documento.
2. Informa al instructor de la situación describiendo el prompt utilizado y el contenido generado.
3. El instructor verificará si los archivos de la biblioteca de SharePoint del curso contienen información real que debería haber sido anonimizada o eliminada.
4. Si el contenido parece ser una alucinación del modelo (dato ficticio que suena real), el instructor confirmará que no corresponde a ninguna persona u organización real. En ese caso, puedes continuar usando el contenido pero debes agregar una nota explícita en el documento: `[Contenido ficticio generado por IA — verificado por instructor]`.
5. Como medida preventiva, añade siempre la restricción `"Usa únicamente datos completamente ficticios e inventados. No uses nombres de personas, empresas o lugares reales."` en todos tus prompts durante el curso.

---

## 9. Limpieza del Entorno

Al finalizar el laboratorio, realiza los siguientes pasos de limpieza para mantener el entorno organizado:

**9.1 — Verificar ubicación de archivos:**
1. Confirma que los tres archivos de trabajo están guardados en la carpeta correcta de SharePoint: `Lab01/Mis Documentos/[Tu nombre o ID de participante]/`.
2. Verifica que **no** quedaron copias locales de los archivos en el escritorio o en la carpeta de Descargas del equipo. Si existen, elimínalas (los archivos oficiales deben estar en la nube).

**9.2 — Cerrar documentos:**
1. Cierra todos los documentos de Word abiertos durante el laboratorio.
2. Asegúrate de que el guardado automático esté activo y que los cambios finales se sincronizaron con OneDrive/SharePoint (el ícono de nube en la barra de estado de Word debe mostrar "Guardado en la nube").

**9.3 — No eliminar archivos:**
> ⚠️ **Importante:** NO elimines ninguno de los tres archivos producidos en este laboratorio. Serán utilizados como referencia en laboratorios posteriores del curso, especialmente en los Módulos 2 y 4.

**9.4 — Cerrar sesiones si aplica:**
1. Si estás en un equipo compartido o de laboratorio, cierra la sesión de Microsoft 365 en el navegador Edge (`https://www.office.com` → Avatar → **Cerrar sesión**).
2. Cierra Microsoft Word completamente.

---

## 10. Resumen y Recursos Adicionales

### Resumen del Laboratorio

En este laboratorio aplicaste los conceptos fundamentales de la Lección 1.1 en un contexto práctico real de EHS. Los puntos clave que debes haber consolidado son:

| Concepto | Lo que practicaste |
|---|---|
| **Privacidad de datos y uso responsable** | Uso exclusivo de datos ficticios; comprensión de la herencia de permisos; obligatoriedad de revisión humana |
| **Anatomía del prompt efectivo** | Aplicación de los 5 componentes: contexto, rol, tarea, formato y restricciones |
| **Iteración de prompts** | Refinamiento progresivo del PTS mediante 2 iteraciones (EJ2) |
| **Copilot como auditor documental** | Generación de tabla de hallazgos y secciones mejoradas a partir de política preexistente (EJ3) |
| **Gestión documental en SharePoint** | Guardado correcto de documentos en la nube para uso en prácticas posteriores |

### Conexión con el Siguiente Laboratorio

Los documentos generados en este laboratorio —especialmente el PTS de trabajo en altura (EJ2) y la política de seguridad patrimonial revisada (EJ3)— serán utilizados como punto de partida en el **Laboratorio 01-00-02**, donde aprenderás a integrar referencias normativas específicas, generar plantillas reutilizables de documentos EHS y usar Copilot para comparar versiones de políticas con estándares como NOM, OSHA e ISO 45001.

### Recursos Adicionales

Los siguientes recursos complementan los temas trabajados en este laboratorio:

- **Documentación oficial de Microsoft Copilot para Microsoft 365 — Privacidad y seguridad:**
  `https://learn.microsoft.com/es-es/copilot/microsoft-365/microsoft-365-copilot-privacy`

- **Guía de prompting efectivo para Microsoft Copilot (Microsoft Learn):**
  `https://learn.microsoft.com/es-es/copilot/microsoft-365/prompting-tips-and-tricks`

- **NOM-009-STPS-2011 — Condiciones de seguridad para realizar trabajos en altura (STPS México):**
  `https://www.dof.gob.mx/nota_detalle.php?codigo=5213352&fecha=06/05/2011`

- **Centro de confianza de Microsoft — Protección de datos y privacidad:**
  `https://www.microsoft.com/es-es/trust-center/privacy`

- **OSHA Standard 1926.502 — Fall Protection Systems Criteria and Practices:**
  `https://www.osha.gov/laws-regs/regulations/standardnumber/1926/1926.502`

---

> 💬 **Nota final del instructor:** Recuerda a los participantes que el valor de Copilot no radica en reemplazar el criterio del profesional de seguridad, sino en acelerar el trabajo documentario y ampliar la capacidad de análisis. La validación humana experta siempre es el último paso —y el más importante— en cualquier flujo de trabajo que involucre IA generativa en contextos de EHS.

---
