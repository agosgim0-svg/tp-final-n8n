[https://airtable.com/invite/l?inviteId=invbG9OIxneRuXDcE&inviteToken=0837e76917bbe809c08ed6fef174b769741fb32c6909a2f0f7e6290313aa8d42&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts](https://airtable.com/apptO0KQw5i3cbJxV/shrq1UNk91cEC3vUO)

# 🚀 TP Final: Ecosistema de Automatización Inteligente con n8n, OpenAI y Airtable

## 📋 Descripción del Proyecto
Este proyecto implementa un pipeline automatizado de procesamiento de encuestas y atención al cliente utilizando **n8n** como motor de orquestación, modelos avanzados de lenguaje de **OpenAI** para análisis semántico/clasificación, y una base de datos relacional en **Airtable** para la persistencia de datos y control operativo.

---

## 🏗️ 1. Diagrama de Arquitectura y Flujo de Datos
El flujo de trabajo se compone de los siguientes componentes integrados:
1. **Trigger (Webhook):** Recibe las solicitudes externas de nuevas encuestas o interacciones de usuarios en tiempo real.
2. **Human-in-the-loop (HITL):** Incorpora un nodo de pausa (`Wait` configurado en modo *On Webhook Call*) que retiene el flujo de forma segura, exigiendo validación y autorización humana antes de permitir que la IA procese la información crítica.
3. **Procesamiento de IA (`gpt-4o-mini`):** Analiza el sentimiento, categoriza la respuesta y redacta una propuesta de respuesta adecuada al caso.
4. **Persistencia Relacional (Airtable):** Almacena los resultados divididos en múltiples tablas relacionadas (**Encuestas** y **Auditoría / Validaciones**).
5. **Manejo de Errores:** Cuenta con un flujo derivado (`Error Trigger`) que captura fallas y notifica vía correo electrónico ante cualquier interrupción imprevista.

---

## 🗄️ 2. Estructura de la Base de Datos (Airtable)
La solución está estructurada mediante un modelo relacional de múltiples tablas:
* **Tabla 1: Encuestas** — Almacena el nombre completo, correo del usuario, texto de la encuesta original, estado del proceso y la clasificación arrojada por la inteligencia artificial.
* **Tabla 2: Auditoría / Validaciones** — Relacionada directamente con la tabla principal, registra las trazas de control, los tiempos de espera del circuito *Human-in-the-loop* y el estado de aprobación operativa.

---

## 📊 3. Dashboard Operativo y KPIs
El monitoreo del sistema se realiza a través de una vista compartida en Airtable (`Shared View`), la cual permite visualizar:
* Tasa de conversión y procesamiento de encuestas.
* Distribución de estados (*Pendiente*, *Procesado por IA*, *Revisión Humana*).
* Métricas de control de errores y tiempos de respuesta.

---

## 🛠️ 4. Guía de Puesta en Marcha
1. Importar el archivo **`My workflow 2.json`** dentro de una instancia de n8n.
2. Configurar las credenciales activas de la API de **OpenAI** (asegurando el uso del modelo oficial `gpt-4o-mini`) y las credenciales de **Airtable**.
3. Activar el flujo y desplegar la URL del Webhook para comenzar la ingesta de datos.
