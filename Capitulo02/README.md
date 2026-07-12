# Comunicación Ejecutiva en EHS — Conclusiones, Action Titles y Presentaciones con Copilot

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 60 minutos |
| **Complejidad** | Intermedia |
| **Audiencia** | Personal de las áreas de EHS, Seguridad Patrimonial, Ingeniería y Mantenimiento que requieran reportar incidentes o avances a gerencias y direcciones. |
| **Tecnologías** | Microsoft Copilot (M365 / Interfaz de Chat), Microsoft PowerPoint y Microsoft Word |
| **Enfoque** | Comunicación ejecutiva, síntesis de datos, diseño de presentaciones corporativas mediante exportación nativa de IA y generación de recursos visuales en el chat. |

---

## 2. Descripción Corta

Este laboratorio práctico de 60 minutos capacita a los profesionales de EHS en las técnicas de comunicación ejecutiva necesarias para presentar ante comités de dirección. Los estudiantes aprenderán a transformar hallazgos operativos en conclusiones estratégicas y "action titles". Además, utilizarán Microsoft Copilot para generar de forma directa imágenes fotorrealistas de seguridad y estructurar un archivo de presentación completo utilizando la función nativa de exportación automática a PowerPoint que ofrece la herramienta.

---

## 3. Objetivos del Laboratorio

AL finalizar este laboratorio, el estudiante será capaz de:
* **Redactar "Action Titles" (Títulos de Acción)** que resuman la conclusión principal de una diapositiva o reporte de inmediato.
* **Generar recursos visuales de seguridad fotorrealistas** mediante instrucciones directas en el chat de Copilot.
* **Automatizar la creación de diapositivas en PowerPoint** utilizando la función nativa de exportación de archivos de la IA.
* **Sintetizar incidentes complejos de seguridad** en formatos ejecutivos de alta dirección (Estructura de Tres Pilares).

---

## 4. Prerrequisitos

* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot** con capacidades de creación de archivos y generación de imágenes.
* Aplicación de **Microsoft Word** abierta con un documento en blanco guardado como `Reporte_Ejecutivo_Direccion.docx`.

---

## 5. Procedimiento Paso a Paso

### Paso 1: Síntesis de Datos y Redacción de "Action Titles"

Un reporte directivo jamás debe usar títulos pasivos como "Estadísticas de incidentes". Debe usar *Action Titles* que informen e impacten de inmediato (ej. "Inversión en LOTO reduce 40% los incidentes en el primer trimestre").

1. Abra el chat de **Microsoft Copilot**.
2. Introduzca el siguiente prompt para procesar un caso operativo y transformarlo en conclusiones ejecutivas:

```
Actúa como un Consultor de Comunicación Corporativa y EHS para Directores Generales. Tengo los siguientes datos crudos de la planta: "En los últimos 6 meses tuvimos 8 conatos de incendio en el área de soldadura debido a chispas que cayeron en cartones acumulados. Se implementó una política de 'Área Limpia de Flamables' en un radio de 5 metros y los incidentes bajaron a cero en las últimas 4 semanas. Requerimos un presupuesto de $5,000 USD para instalar mamparas fijas de protección."

Por favor, transforma estos datos operativos en un resumen ejecutivo estructurado de la siguiente manera:
1. **Action Title (Título de Acción):** Un encabezado impactante de máximo 12 palabras que resuma el logro y la necesidad presupuestal.
2. **Conclusión de Negocio (3 Líneas):** Explica el beneficio financiero y de continuidad de operaciones al haber controlado el riesgo de incendio.
3. **Petición Directiva (The Ask):** Redacta de forma diplomática pero firme la solicitud de los recursos para las mamparas fijas.

Usa un tono corporativo, ejecutivo, directo y enfocado en la prevención de pérdidas.
```

3. Copie el resultado entregado por Copilot y péguelo en su documento de Word `Reporte_Ejecutivo_Direccion.docx` bajo el título `## 1. Resumen Ejecutivo de Mitigación de Riesgos`.

---

### Paso 2: Generación Directa del Recurso Visual (Imagen de Portada Corporativa)

Una presentación directiva de EHS requiere un impacto visual sobrio y profesional que refleje la seriedad de la disciplina de seguridad.

1. En la misma interfaz de chat de Copilot, introduzca el siguiente prompt especializado para indicarle que cree la imagen directamente:

```
Genera una imagen que sea una fotografía corporativa e industrial de alta calidad para la portada de un reporte ejecutivo de EHS. En la escena se debe observar en primer plano un casco industrial de color blanco limpio, unos lentes de protección transparentes y unos guantes de seguridad técnica reposando de forma ordenada sobre una mesa de juntas de madera oscura en una oficina de planta. Al fondo, a través de un gran ventanal de vidrio, se deben apreciar las luces y estructuras limpias de una planta de producción moderna. Estética corporativa, iluminación profesional, ambiente seguro, fotorrealista, formato horizontal 16:9. No incluyas ningún tipo de texto, letras ni logotipos dentro de la imagen.
```

2. Copilot procesará la instrucción y creará la imagen directamente en la pantalla de chat. Seleccione la opción que mejor represente la seriedad corporativa, haga clic en el botón de descarga y guárdela en su computadora como `Portada_EHS_Ejecutiva.png`.
3. Inserte esta imagen en su archivo de Word como parte de los anexos visuales del reporte.

---

### Paso 3: Estructuración y Exportación Nativa a PowerPoint

Para eliminar el armado manual de láminas, aprovecharemos la capacidad de Copilot de generar el archivo de presentación de forma automática y directa a través de sus comandos de exportación integrados de Microsoft 365.

1. Introduzca el siguiente prompt en el chat de Copilot para que construya la presentación:

```
Actúa como un Diseñador de Presentaciones Corporativas. Necesito que crees una presentación de PowerPoint lista para descargar sobre 'Estrategia de Seguridad Patrimonial e Indicadores Críticos 2026'. 

Estructura la presentación con las siguientes 3 diapositivas exactas utilizando plantillas corporativas limpias:
- **Diapositiva 1 (Portada):** Título: "Estrategia de Seguridad Patrimonial 2026" | Subtítulo: "Reporte de Cumplimiento Normativo y Mitigación de Pérdidas"
- **Diapositiva 2 (Hallazgos):** Título: "Action Title: Monitoreo Digital Redujo 35% Intrusiones en Perímetro" | Contenido en viñetas: Implementación de analítica de video en cámaras perimetrales; Reducción del tiempo de respuesta interna a 45 segundos; Cero pérdidas materiales reportadas en el último trimestre.
- **Diapositiva 3 (Conclusión):** Título: "Action Title: Próximo Paso Requiere Certificación BASC" | Contenido en viñetas: Auditoría externa programada para agosto 2026; Asegura el cumplimiento de la cadena de suministro internacional; Mitiga riesgos de sanciones aduanales y contrabando.

Procesa la información y utiliza tu función nativa para generar y exportar este contenido directamente a un archivo de PowerPoint (.pptx).
```

2. Una vez que Copilot termine de procesar la solicitud, le mostrará el archivo generado o el botón nativo de **"Exportar a PowerPoint" / "Abrir en PowerPoint"** en la misma ventana de chat.
3. Haga clic en la opción de exportación, descargue el archivo generado por la IA en su computadora y ábralo para comprobar que las diapositivas se crearon con sus títulos y viñetas ejecutivas exactas de forma automática. Guarde el archivo como `Presentacion_Seguridad_Patrimonial.pptx`.

---

### Paso 4: Reto de Aplicación Autónoma – Creación de la Lámina de Cierre Financiero

**Instrucciones para el estudiante:** El Director de Finanzas asistirá a la reunión de EHS y exige ver una lámina dedicada exclusivamente al impacto económico de la prevención. El dato duro es el siguiente: *Al renovar los sistemas de ventilación y extractores de polvo en el piso de la planta, se redujeron las bajas médicas por problemas respiratorios en un 80%, lo que le ahorró a la empresa $14,000 USD en pago de horas extras de reemplazo y primas de seguro de riesgo de trabajo.*

#### El Desafío:
Consolidando las habilidades adquiridas de comunicación ejecutiva y exportación automática, genere una solución de forma totalmente independiente:

1. **Estructura del Requerimiento Autónomo:** Redacte un nuevo prompt en Copilot donde le ordene asumir el rol de un Especialista en Finanzas de la Salud Ocupacional.
2. **Generación Directa del Entregable:** Pídale a la IA que tome el dato del ahorro de los $14,000 USD, lo sintetice bajo un *Action Title* contundente enfocado en el beneficio económico de la salud industrial, y genere directamente el archivo o la actualización para agregar esta lámina al reporte ejecutivo de PowerPoint.
3. **Criterio de Éxito:** El estudiante comprobará que el resultado final entregado por Copilot ordene los datos financieros en viñetas limpias de alta dirección listas para su descarga, demostrando la capacidad de usar la IA para exportar reportes ejecutivos automatizados sin diseñar nada a mano.

---

## 6. Conceptos Clave para Recordar

* **Action Titles (Títulos de Acción):** Técnica de comunicación corporativa que reemplaza los encabezados genéricos por frases que declaran explícitamente el resultado clave o la conclusión de la hoja o diapositiva, acelerando la toma de decisiones.
* **Exportación Nativa de IA:** Capacidad integrada de los asistentes modernos para empaquetar, formatear y descargar información procesada directamente en archivos compatibles con la suite de oficina (Word, Excel, PowerPoint) sin intervención del usuario.
* **Estructura de Tres Pilares:** Método de síntesis ejecutiva que organiza cualquier reporte de incidente en tres bloques obligatorios: Qué pasó (Hecho), Qué impacto tiene (Consecuencia/Costo) y Qué se va a hacer (Acción Correctiva).

---

## 7. Resultado Esperado del Estudiante

Para validar la correcta conclusión de esta práctica de comunicación ejecutiva de 60 minutos, el estudiante guardará y entregará:

1. **Archivo `Reporte_Ejecutivo_Direccion.docx` (Word):**
   * El documento oficial con la síntesis de datos, el Action Title y la petición formal del presupuesto del Paso 1, complementado con la imagen de portada descargada en el Paso 2.
2. **Archivo `Presentacion_Seguridad_Patrimonial.pptx` (PowerPoint):**
   * La presentación ejecutiva generada y exportada automáticamente por la función nativa de Copilot (Paso 3), que incluye los títulos de acción estratégicos y la lámina de impacto financiero desarrollada de manera autónoma en el Paso 4.
