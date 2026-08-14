Ecosistema de Automatización de Atención al Cliente con Make, Airtable y Google Gemini AI

Autora: Geovanna Larreal    
Proyecto:Trabajo Final - Automatización e Inteligencia Artificial  

---
Ecosistema de Automatización de Atención al Cliente con Make, Airtable y Gemini A. Este proyecto implementa una solución desacoplada y escalable de triage y generación de respuestas automáticas para soporte al cliente de una tienda deportiva (ficticia).

Objetivo del Proyecto

Optimizar la gestión de correos entrantes (consultas sobre talles, stock, devoluciones y envíos), reduciendo los tiempos de respuesta y liberando carga operativa mediante:
* Clasificación en tiempo real por categoría y urgencia.
* Redacción asistida por IA para generar sugerencias de respuesta
* Validación Humana (Human-in-the-Loop) para garantizar el control de calidad antes del envío final
* Manejo de Errores (Error Handlers) para alta disponibilidad del sistema

Arquitectura del Sistema

La solución está construida en dos escenarios independientes en Make, conectados a través de una base de datos centralizada en Airtable:

- Escenario 1: Ingestión e IA: Gmail (Consulta) ➔ Airtable (Registro) ➔ Gemini AI (Borrador) ➔ Alerta Operador
- Escenario 2: Despacho: Airtable (Status = 'Aprobado') ➔ Gmail (Envío al cliente) ➔ Airtable (Estado: Resuelto)

Arquitectura del Sistema

La solución está construida en dos escenarios independientes en Make, conectados a través de una base de datos centralizada en Airtable:

Escenario 1: Ingestión e IA
Gmail (Consulta) ➔ Airtable (Registro) ➔ Gemini AI (Borrador) ➔ Alerta Operador
[HUMAN-IN-THE-LOOP]: Operador revisa y aprueba el borrador en Airtable

Escenario 2: Despacho
Airtable (Status = 'Aprobado') ➔ Gmail (Envío al cliente) ➔ Airtable (Estado: Resuelto)

Stack Tecnológico
Make Orquestador del flujo y lógica del sistema
Gmail Recepción de consultas y envío de respuestas oficiales
Airtable Base de datos relacional para gestión de tickets, clientes y control HITL
Google Gemini 1.5 Flash Procesamiento de lenguaje natural, clasificación y redacción de borradores

---
Características Clave
Elección Inteligente del LLM: Implementación de Gemini 1.5 Flash por su baja latencia (0.8s) y su costo ultra eficiente ($0.00015 USD por correo procesado)
Tolerancia a Fallos (Resiliencia): Uso de directivas `Resume` en Make para reintentos y respuestas fallback en caso de caídas de API
Human-in-the-Loop (HITL): Barrera de seguridad que impide el envío automático no supervisado de correos al cliente
Dashboard Operativo: Agrupaciones y métricas en Airtable para seguimiento en tiempo real de KPIs y tasa de aprobación de la IA

---

Recursos del Repositorio
- Informe_Tecnico_Geovanna_Larreal.pdf` — Documentación técnica completa y justificación de arquitectura.
- Ecosistema_IA_Soporte.blueprint.json` — Blueprint del flujo exportado desde Make para importar directamente de los 2 escenarios.
- Arquitectura.png` — Diagrama visual detallado del flujo.
- Base de Datos en Airtable (Modo Lectura)](https://airtable.com/invite/l?inviteId=invrR8RaXgAXRvXe6&inviteToken=9fe2fa5106e23ebea4351364c53fd06116515ed471b185f93c92ecfc3fcfb30a&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts)
- Capturas de pantalla de todos los escenarios incluyendo los correos electronicos recibidos
- Cuadro comparativo de modelos de IA.

---

