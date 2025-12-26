Tengo un documento PRD (Product Requirements Document) a continuación. Quiero que lo analices y generes código XML compatible con Draw.io para representar un Lean Canvas visual con las siguientes condiciones:

🧭 Tu tarea:
1. Lee el contenido del PRD y **extrae tú mismo** la información relevante para llenar los bloques del Lean Canvas, sin que yo lo tenga que estructurar.

🧱 Estructura:
- Cada bloque del Lean Canvas debe tener **dos celdas apiladas verticalmente**:
  1. Una **celda superior** con el **título del bloque**:
     - Color de fondo según el bloque.
     - Texto centrado, en negrita (fontStyle=1), fontSize=12.
     - Altura fija: 30 px.
     - Márgenes internos: spacingTop=4, spacingLeft=6.
  2. Una **celda inferior** con el **contenido**:
     - Fondo blanco (fillColor=#FFFFFF).
     - Texto en viñetas (-), con saltos de línea usando &#xa;.
     - Fuente fontSize=10, alineado a la izquierda.
     - Altura fija: 120 px (salvo en bloques más altos).
     - Estilo: whiteSpace=wrap;html=1;spacingTop=4;spacingLeft=6.

📌 Distribución del Lean Canvas:
- Fila 1: Problema, Segmentos de Clientes, Propuesta de Valor Única, Ventaja Competitiva (esta va al final, de forma vertical).
- Fila 2: Solución, Canales, Fuentes de Ingresos.
- Fila 3: Estructura de Costes, Métricas Clave.

🎨 Colores de fondo para los títulos:
- Problema: #F8CECC
- Segmentos de Clientes: #D5E8D4
- Propuesta de Valor Única: #FFF2CC
- Solución: #F8CECC
- Canales: #D5E8D4
- Fuentes de Ingresos: #DAE8FC
- Estructura de Costes: #DAE8FC
- Métricas Clave: #FFF2CC
- Ventaja Competitiva: #E1D5E7

📐 Dimensiones exactas:
- Cada bloque horizontal: 250 px de ancho × 150 px de alto (30 para título + 120 para contenido).
- "Estructura de Costes" y "Métricas Clave": 375 px de ancho × 150 px de alto.
- **"Ventaja Competitiva" debe tener 250 px de ancho × 450 px de alto** para alinearse exactamente con las tres filas que ocupa a su izquierda.

📌 Instrucciones de formato:
- Usa whiteSpace=wrap;html=1;spacingTop=4;spacingLeft=6 en todas las celdas de contenido.
- No uses bordes redondeados.
- El resultado debe estar contenido entre <mxGraphModel> y </mxGraphModel>.
- No incluyas ninguna explicación ni resumen adicional, solo el código XML final.
- Asegúrate que todo el código esté contenido en un solo bloque y en formato markdown para copiar y pegar fácilmente

🔽 Aquí está el PRD que debes analizar para completar el Lean Canvas:
# 📘 LTI – Applicant Tracking System

## Índice

1. [Descripción breve del software](#descripción-breve-del-software)
2. [Valor añadido y ventajas competitivas](#valor-añadido-y-ventajas-competitivas)
3. [Funciones principales](#funciones-principales)

---

## 1. Descripción breve del software

**LTI ATS** es una plataforma moderna e inteligente diseñada para **transformar la experiencia de reclutamiento**. Su objetivo es **aumentar la eficiencia operativa de los equipos de HR**, mejorar la **colaboración en tiempo real** entre reclutadores y managers, y **potenciar la toma de decisiones** mediante automatización e inteligencia artificial.

LTI combina una **arquitectura modular basada en APIs**, una **UX ágil y minimalista**, y una **IA integrada en todo el ciclo de contratación**, convirtiéndose en una herramienta adaptable tanto para startups como para grandes corporaciones.

---

## 2. Valor añadido y ventajas competitivas

1. **Experiencia de usuario superior**
   Interfaz rápida, limpia e intuitiva que reduce la fricción operativa y acelera el trabajo diario de los recruiters.

2. **Colaboración contextual y en tiempo real**
   Comentarios, menciones, y notificaciones instantáneas en cada candidato o vacante, permitiendo decisiones más ágiles y coordinadas.

3. **Automatización inteligente**
   Flujos automáticos basados en reglas y eventos que eliminan tareas repetitivas (seguimientos, recordatorios, movimientos de estado).

4. **Asistencia de IA en todas las etapas**

   * Análisis semántico de CVs y matching inteligente.
   * Generación automática de descripciones de puestos y correos.
   * Sugerencias de candidatos ideales y priorización de pipeline.

5. **Analítica avanzada y predicciones**
   Dashboards con métricas clave, detección de cuellos de botella y estimación de tiempos de contratación mediante IA.

6. **Experiencia del candidato mejorada**
   Portal donde el candidato puede seguir su proceso, recibir feedback y comunicarse de forma transparente con la empresa.

7. **Integraciones profundas con el ecosistema empresarial**
   Compatibilidad con Slack, Gmail, Google Calendar, Zoom, LinkedIn Recruiter, Notion, y sistemas HRIS (Workday, BambooHR, etc.).

8. **Cumplimiento de privacidad y normativa**
   Gestión automática del consentimiento, retención de datos configurable y cumplimiento con GDPR.

9. **Personalización sin código**
   Configuración de etapas, vistas y formularios de manera visual, sin depender del equipo técnico.

10. **Arquitectura extensible y modular**
    API-first, pensada para escalar, integrar IA de terceros y añadir módulos especializados sin alterar el core.

11. **Módulo de evaluación unificado**
    Evaluaciones técnicas, entrevistas y feedback centralizados, con plantillas personalizables.

12. **Movilidad y accesibilidad total**
    Versión móvil y PWA completas para gestionar procesos desde cualquier dispositivo.

13. **Marketplace y ecosistema de extensiones**
    Espacio para integrar herramientas externas como tests psicotécnicos, background checks o análisis de competencias.

---

## 3. Funciones principales

1. **Gestión de vacantes**

   * Creación, edición y publicación multicanal de ofertas.
   * Control del estado de cada vacante (abierta, pausada, cerrada).

2. **Gestión de candidatos**

   * Recepción de CVs desde múltiples fuentes.
   * Parsing automático y enriquecimiento de perfiles.
   * Pipeline visual tipo Kanban con estados personalizables.

3. **Búsqueda y filtrado avanzado**

   * Filtros por experiencia, ubicación, habilidades o similitud semántica.
   * Ranking dinámico de candidatos según afinidad.

4. **Colaboración y comunicación interna**

   * Comentarios, menciones y asignación de tareas.
   * Integración con herramientas de mensajería y calendarios.

5. **Automatización y flujos inteligentes**

   * Reglas de negocio configurables por el usuario.
   * Seguimientos automáticos y cambios de estado basados en triggers.

6. **Módulo de entrevistas y evaluaciones**

   * Agenda integrada con calendarios externos.
   * Formularios de evaluación compartidos.
   * Historial centralizado por candidato.

7. **Analítica y reportes**

   * KPIs de reclutamiento (time-to-hire, source effectiveness, etc.).
   * Reportes exportables e insights generados por IA.

8. **Portal del candidato**

   * Seguimiento del proceso, feedback y comunicación directa.
   * Experiencia personalizada según etapa.

9. **Configuración y personalización**

   * Campos, flujos y permisos ajustables por rol o equipo.
   * Soporte multilenguaje y multizona horaria.

10. **Seguridad y cumplimiento**

    * Control de acceso por roles.
    * Cumplimiento con GDPR, almacenamiento cifrado y auditorías.
