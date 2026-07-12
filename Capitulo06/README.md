Creación de un Page Básico para Registrar Incidentes de Seguridad

## 1. Metadatos del Laboratorio

| Atributo | Detalle |
| :--- | :--- |
| **Duración** | 90 minutos |
| **Complejidad** | Avanzada |
| **Audiencia** | Personal de las áreas de EHS, Seguridad Patrimonial, Ingeniería y Mantenimiento que busca digitalizar actividades de control de forma directa y sin complicaciones técnicas. |
| **Tecnologías** | Microsoft Copilot (M365 / Interfaz de Chat) y Google Colab (Notebooks de Trabajo). |
| **Enfoque** | Herramientas digitales autocontenidas, interfaces visuales sencillas e interactividad sin dependencias de bases de datos. |

---

## 2. Descripción Corta

Este laboratorio de 90 minutos capacita a los profesionales de EHS en el uso de Microsoft Copilot para generar minipáginas y utilidades interactivas en Google Colab. En lugar de construir un sistema de software complejo, los estudiantes crearán de forma secuencial 5 herramientas independientes dentro de un mismo archivo de trabajo. Cada celda del Notebook funcionará como un elemento cerrado: desde un selector visual de tipos de riesgo, hasta un generador automático de textos para reportes y un simulador directo de cálculo de prioridades, garantizando un aprendizaje libre de errores de código.

---

## 3. Objetivos del Laboratorio

Al finalizar este laboratorio, el estudiante será capaz de:
* **Ingresar y estructurar celdas de trabajo en Google Colab** de forma independiente.
* **Desplegar menús interactivos y botones visuales** mediante códigos provistos por inteligencia artificial.
* **Generar herramientas autónomas de captura y procesamiento de texto** para agilizar los reportes en planta.
* **Modificar parámetros visuales y opciones dentro de un script** para personalizar sus propias herramientas de seguridad.

---

## 4. Prerrequisitos

* Cuenta activa de Google (correo electrónico de Gmail o institucional).
* Cuenta activa de **Microsoft 365** con acceso a **Microsoft Copilot**.
* Un cuaderno en blanco abierto en Google Colab titulado `Herramientas_Digitales_EHS.ipynb`.

---

## 5. Procedimiento Paso a Paso

### Paso 1: Acceso a Google Colab y Creación de un Selector de Áreas

Comenzaremos por abrir nuestro espacio de trabajo y generar un selector visual simple. Este miniprograma solo mostrará opciones en pantalla para que el usuario elija un área de la planta y confirme su selección.

#### Guía para acceder a la plataforma:
1. Abra su navegador de internet (Google Chrome o Microsoft Edge).
2. Escriba en la barra de direcciones: `https://colab.research.google.com`
3. Seleccione la pestaña **"Archivo"** (arriba a la izquierda) y haga clic en **"Bloc de notas nuevo"**.
4. En la esquina superior izquierda, cambie el nombre del archivo por: `Herramientas_Digitales_EHS.ipynb`.

#### Generación de la Herramienta 1:
5. Abra el chat de **Microsoft Copilot** e introduzca el siguiente prompt:

```
Actúa como un Asesor de Transformación Digital para Seguridad Industrial. Necesito un código en Python autocontenido para ejecutar en Google Colab. 

El código debe crear una mini-pantalla independiente que tenga:
1. Un menú desplegable (Dropdown) con las opciones de áreas de planta: "Molienda", "Prensas", "Mantenimiento", "Embarques".
2. Un botón azul abajo que diga "Confirmar Área".
3. Que al presionar el botón, imprima un mensaje sencillo abajo diciendo: "Área seleccionada para inspección: [Área elegida]".

Dame únicamente el código limpio dentro de un bloque de texto, listo para copiar y pegar.
```

6. Copie el código otorgado por Copilot (`Ctrl+C`).
7. Vaya a Google Colab, péguelo en la primera celda y haga clic en el botón de **Play**. Pruebe el menú desplegable y presione el botón para ver el mensaje.

---

### Paso 2: Generador Digital de Tarjetas de Condición Insegura

Crearemos una segunda herramienta independiente en la siguiente celda. Esta funcionará como un formulario plano que toma una descripción y la transforma de inmediato en un formato limpio listo para ser copiado a un reporte oficial.

1. En Google Colab, haga clic en el botón **"+ Código"** en la barra superior para abrir una segunda celda vacía.
2. Introduzca el siguiente prompt en Copilot:

```
Actúa como un Facilitador de Herramientas Digitales para EHS. Necesito un código en Python totalmente independiente para una nueva celda de Google Colab.

El código debe mostrar en pantalla:
1. Un cuadro de texto largo (Textarea) para que el supervisor escriba una "Descripción del Peligro Encontrado".
2. Un botón verde que diga "Generar Reporte de Texto".
3. Al presionarse, debe tomar el texto escrito y mostrarlo abajo con un diseño limpio y formateado como este:
   "*** ALERTA DE SEGURIDAD EN PLANTA ***
   Detalle del hallazgo: [Texto del usuario]"

Dame únicamente el código listo para copiar en la segunda celda.
```

3. Copie el código de Copilot, péguelo en la **Celda 2** de su Colab y dele **Play**. Escriba una falla en el cuadro de texto y presione el botón verde.

---

### Paso 3: Calculadora Autónoma de Nivel de Criticidad

La tercera herramienta independiente servirá para que el supervisor elija la probabilidad y la gravedad de un riesgo mediante botones, y el programa calcule el resultado de forma matemática en el momento.

1. En Google Colab, haga clic en el botón **"+ Código"** para abrir la tercera celda vacía.
2. Ingrese este prompt en Copilot:

```
Actúa como un Consultor de Procesos de Seguridad Industrial. Necesito un código en Python independiente para una celda de Google Colab que funcione como calculadora de criticidad.

La herramienta debe desplegar:
1. Un menú desplegable para 'Gravedad del Daño' con valores numéricos: "1 - Menor", "2 - Moderado", "3 - Grave".
2. Un menú desplegable para 'Probabilidad' con valores numéricos: "1 - Baja", "2 - Media", "3 - Alta".
3. Un botón que diga "Calcular Nivel".
4. Al presionarse, debe multiplicar ambos números seleccionados e imprimir abajo el resultado indicando: "El factor de riesgo estimado es: [Resultado de la multiplicación]".

Dame solo el bloque de código de Python listo para usar.
```

3. Copie el bloque de código, péguelo en la **Celda 3** de su Colab y ejecútelo (`Play`). Seleccione los valores, presione el botón y valide el cálculo inmediato.

---

### Paso 4: Marcador Digital de Tiempos de Respuesta (Cronómetro de Simulacros)

Para medir la efectividad en evacuaciones o brigadas, programaremos una celda independiente que sirva como un botón de registro de tiempo instantáneo.

1. Cree una cuarta celda en su cuaderno haciendo clic en **"+ Código"**.
2. Introduzca este prompt en el chat de Copilot:

```
Actúa como un Evaluador de Brigadas de Emergencia de EHS. Necesito un código en Python autocontenido para una celda de Google Colab.

El programa debe mostrar en la pantalla un único botón rojo grande que diga "Registrar Hora de Alerta". Al hacer clic en él, debe leer la hora actual de la computadora y mostrar un mensaje abajo diciendo de forma directa: "¡Simulacro Iniciado! Hora exacta registrada: [Hora:Minutos:Segundos]".

Dame únicamente el código de Python listo para ejecutar.
```

3. Copie el código de Copilot, péguelo en la **Celda 4** de su Colab y dele **Play**. Presione el botón rojo y observe cómo captura el tiempo exacto sin fallas.

---

### Paso 5: Visor y Clasificador Visual de Estatus de Hallazgos

Como última utilidad, crearemos una celda que tome un estatus seleccionado por el usuario y le asigne un indicador visual de color (texto informativo) para simular un tablero de control manual.

1. Abra una quinta celda de código con el botón **"+ Código"**.
2. Ingrese el siguiente prompt en Copilot:

```
Actúa como un Diseñador de Soluciones Visuales para Operaciones en Planta. Necesito un código en Python independiente para Google Colab.

La herramienta debe mostrar:
1. Un menú desplegable para seleccionar el 'Estado Actual de la Acción' con las opciones: "Abierto", "En Proceso", "Cerrado".
2. Un botón que diga "Verificar Estatus".
3. Al presionarse, debe imprimir un mensaje de texto plano abajo. Si es Abierto, que diga "[ALERTA] La acción requiere atención inmediata". Si es En Proceso, que diga "[SEGUIMIENTO] Trabajo en ejecución". Si es Cerrado, que diga "[COMPLETO] Condición segura restablecida".

Dame solo el fragmento de código listo para copiar.
```

3. Copie el código, péguelo en la **Celda 5** de su Google Colab y presione **Play** para comprobar su funcionamiento autónomo.

---

### Paso 6: Reto de Aplicación Autónoma – Creación de la Herramienta de Checklist Rápido

**Instrucciones para el estudiante:** El Director de EHS solicita una nueva herramienta digital independiente para que los supervisores validen rápidamente si el personal cuenta con sus Elementos de Protección Personal (EPP) antes de iniciar el turno. 

#### El Desafío:
Vas a diseñar y construir tu propia herramienta autónoma utilizando **Microsoft Copilot**, sin necesidad de modificar los códigos anteriores.

1. **Escribe tu propio prompt en Copilot:** Abre el chat de Copilot y redacta una petición (prompt) utilizando como base los ejemplos de los pasos anteriores. Tu prompt debe pedirle a la IA un código de Python para Google Colab que cree una pantalla independiente con:
   * Un menú desplegable para elegir el EPP a revisar (opciones: "Casco", "Gafas de Seguridad", "Guantes", "Botas Dieléctricas").
   * Un segundo menú desplegable para marcar el estado (opciones: "Cumple", "No Cumple", "No Aplica").
   * Un botón que diga "Registrar EPP".
   * Que al presionar el botón, imprima abajo un texto claro con la combinación seleccionada (ej. *"Verificación: Casco -> Estado: Cumple"*).

2. **Implementa tu herramienta:** 
   * En tu cuaderno de Google Colab, haz clic en el botón **"+ Código"** para abrir una sexta celda al final del archivo.
   * Copia el código que te entregó Copilot y pégalo en esa nueva **Celda 6**.
   * Presiona el botón de **Play** y realiza una prueba seleccionando un EPP y su estado.

3. **Comprobación de éxito:** Tu reto estará cumplido cuando la Celda 6 muestre la mini-pantalla interactiva funcionando de forma totalmente autónoma y sin errores.

---

## 6. Conceptos Clave para Recordar

* **Celda Autocontenida:** Bloque de código en un Notebook que incluye todas sus librerías, variables y lógicas de forma interna, permitiendo que se ejecute con éxito sin depender de lo que haya sucedido en otras partes del documento.
* **Interfaz de Usuario Básica:** Controles visuales simples (botones, menús, textos) que permiten a cualquier operador interactuar con un programa ingresando datos directamente en la pantalla.
* **Widgets de Control:** Herramientas digitales interactivas especializadas en capturar una acción del usuario (como un clic o una selección) y transformarla en una respuesta inmediata en pantalla.

---

## 7. Resultado Esperado del Estudiante

Para validar la conclusión exitosa de este laboratorio práctico sin errores de código, el estudiante guardará y entregará:

1. **Archivo Único de Trabajo (`Herramientas_Digitales_EHS.ipynb`):**
   * El archivo de Colab completo que aloja las 5 herramientas independientes operando de manera perfecta al presionar sus respectivos botones.
   * La **Celda 1** debe mostrar los cambios del Reto Autónomo (Paso 6), incorporando de forma exitosa el segundo menú interactivo de selección de tipo de incidente.
