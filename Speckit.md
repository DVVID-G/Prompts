Guía paso a paso: cómo usar Speckit
Speckit es un sistema de desarrollo guiado por especificaciones. Flujo de trabajo:
Flujo de trabajo general
1. Especificar → 2. Clarificar → 3. Planificar → 4. Tareas → 5. Analizar → 6. Implementar
Paso 1: Especificar la funcionalidad (/speckit.specify)
Qué hace: crea una especificación desde una descripción en lenguaje natural.
Cómo usarlo:
/speckit.specify Quiero agregar autenticación de usuarios con OAuth2
Proceso:
Genera un nombre corto (ej: "user-auth")
Crea una rama numerada (ej: 1-user-auth)
Crea spec.md con:
Requisitos funcionales
Criterios de éxito
Escenarios de usuario
Casos límite
Valida la calidad y crea un checklist
Resultado: specs/[número]-[nombre]/spec.md
Paso 2: Clarificar ambigüedades (/speckit.clarify)
Qué hace: identifica áreas poco claras y pregunta hasta 5 preguntas específicas.
Cómo usarlo:
/speckit.clarify
Proceso:
Analiza spec.md buscando ambigüedades
Hace preguntas una por una (máximo 5)
Integra las respuestas en spec.md
Actualiza secciones relevantes
Cuándo usarlo: después de /speckit.specify y antes de /speckit.plan.
Paso 3: Crear el plan técnico (/speckit.plan)
Qué hace: genera un plan técnico con arquitectura, stack y diseño.
Cómo usarlo:
/speckit.plan
Proceso:
Lee spec.md y la constitución del proyecto
Fase 0: investigación (research.md)
Resuelve "NEEDS CLARIFICATION"
Documenta decisiones técnicas
Fase 1: diseño y contratos
data-model.md (entidades y relaciones)
contracts/ (especificaciones API)
quickstart.md (escenarios de integración)
Actualiza el contexto del agente
Resultado: plan.md con arquitectura, stack y decisiones técnicas.
Paso 4: Generar tareas (/speckit.tasks)
Qué hace: descompone el plan en tareas ejecutables organizadas por historias de usuario.
Cómo usarlo:
/speckit.tasks
Proceso:
Lee plan.md y spec.md
Organiza tareas por historias de usuario (P1, P2, P3...)
Genera tasks.md con:
Fase 1: Setup (inicialización)
Fase 2: Fundamentos (prerequisitos)
Fase 3+: Historias de usuario en orden de prioridad
Fase final: Pulido y preocupaciones transversales
Marca tareas paralelizables con [P]
Incluye rutas de archivos específicas
Formato de tareas:
- [ ] T001 [P] [US1] Crear modelo User en src/models/user.ts- [ ] T002 [US1] Implementar UserService en src/services/user.service.ts
Paso 5: Analizar consistencia (/speckit.analyze)
Qué hace: analiza spec.md, plan.md y tasks.md para detectar inconsistencias, duplicados y brechas.
Cómo usarlo:
/speckit.analyze
Proceso:
Carga los tres artefactos
Detecta:
Duplicaciones
Ambigüedades
Subespecificaciones
Violaciones de constitución
Brechas de cobertura
Inconsistencias
Genera un reporte con severidad (CRITICAL, HIGH, MEDIUM, LOW)
Ofrece un plan de remediación (no aplica cambios automáticamente)
Cuándo usarlo: después de /speckit.tasks, antes de implementar.
Paso 6: Crear checklists (/speckit.checklist)
Qué hace: genera checklists para validar la calidad de los requisitos (no del código).
Cómo usarlo:
/speckit.checklist Crear checklist de UX/speckit.checklist Crear checklist de seguridad
Proceso:
Hace 1-3 preguntas para entender el enfoque
Lee spec.md, plan.md y tasks.md
Genera un checklist que valida:
Completitud de requisitos
Claridad y especificidad
Consistencia
Cobertura de escenarios
Casos límite
Ejemplo de items correctos:
- [ ] CHK001 ¿Están definidos los requisitos de jerarquía visual con criterios medibles? [Claridad]- [ ] CHK002 ¿Está especificado el comportamiento cuando falla la carga de imágenes? [Caso límite]
Ejemplo de items incorrectos:
❌ Verificar que el botón funciona correctamente❌ Probar que la API retorna 200
Paso 7: Implementar (/speckit.implement)
Qué hace: ejecuta las tareas de tasks.md en orden.
Cómo usarlo:
/speckit.implement
Proceso:
Verifica checklists (pregunta si están incompletos)
Lee tasks.md, plan.md y documentos de diseño
Verifica/crea archivos .ignore según el stack
Ejecuta tareas fase por fase:
Setup primero
Tests antes del código (si aplica TDD)
Desarrollo core
Integración
Pulido
Marca tareas completadas como [X] en tasks.md
Reporta progreso después de cada tarea
Comandos adicionales
/speckit.constitution
Actualiza la constitución del proyecto (principios y reglas).
Ejemplo de flujo completo
# 1. Especificar/speckit.specify Agregar sistema de notificaciones por email# 2. Clarificar (opcional pero recomendado)/speckit.clarify# 3. Planificar/speckit.plan# 4. Generar tareas/speckit.tasks# 5. Analizar/speckit.analyze# 6. Crear checklists (opcional)/speckit.checklist Crear checklist de API# 7. Implementar/speckit.implement
Estructura de archivos generada
specs/└── 1-user-auth/    ├── spec.md              # Especificación funcional    ├── plan.md              # Plan técnico    ├── tasks.md             # Tareas de implementación    ├── data-model.md        # Modelo de datos    ├── research.md          # Decisiones técnicas    ├── quickstart.md        # Guía de integración    ├── contracts/           # Especificaciones API    └── checklists/          # Checklists de calidad        ├── requirements.md        ├── ux.md        └── security.md
Consejos
Orden recomendado: specify → clarify → plan → tasks → analyze → implement
Usa clarify si hay dudas antes de planificar
Usa analyze antes de implementar para detectar problemas
Los checklists validan requisitos, no código
Las tareas deben ser específicas con rutas de archivos