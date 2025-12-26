# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.# 📘 Guía Maestra de Git & GitHub: De Junior a Pro

Este manual cubre desde los comandos básicos hasta situaciones de "pánico" comunes en el desarrollo colaborativo.

## 1. Configuración Inicial

Antes de empezar, tu identidad digital en los commits.

| Comando | Explicación |
|---------|-------------|
| `git config --global user.name "Tu Nombre"` | Define el nombre que aparecerá en el historial. |
| `git config --global user.email "tu@email.com"` | Define el correo (debe coincidir con el de GitHub). |

## 2. El Ciclo de Vida Diario (Workflow Básico)

La rutina sagrada: Modificar -> Preparar -> Guardar.

### 🔍 Ver el estado

Siempre, antes de cualquier cosa, mira dónde estás parado.
```bash
git status
```

**Qué hace:** Te dice qué archivos modificaste, cuáles están preparados (staged) y en qué rama estás.

### 📦 Preparar archivos (Staging)

Mueve tus cambios al "área de preparación".
```bash
git add .           # Agrega TODOS los archivos modificados
git add archivo.js  # Agrega SOLO un archivo específico (Best Practice)
```

### 💾 Guardar cambios (Commit)

Crea una "foto" permanente de tu trabajo.
```bash
git commit -m "feat: agrega lógica del temporizador pomodoro"
```

**Tip Senior:** Usa verbos en imperativo ("agrega", "corrige", "actualiza") y sé descriptivo.

## 3. Gestión de Ramas (Branching)

Nunca trabajes en main o develop directamente. Las ramas son tus espacios seguros de trabajo.

| Comando | Explicación |
|---------|-------------|
| `git branch` | Lista las ramas locales. |
| `git checkout -b nombre-rama` | Crea una rama y te mueve a ella automáticamente. |
| `git checkout nombre-rama` | Te cambia a una rama existente. |
| `git branch -d nombre-rama` | Borra una rama local (solo si ya se fusionó). |

## 4. Sincronización con el Remoto (GitHub)

Cómo hablar con el servidor.

### 📥 Traer cambios (Fetch vs Pull)

Esta es una distinción vital.

**La forma segura (Ver antes de tocar):**
```bash
git fetch origin
```

Descarga la información del remoto pero NO toca tus archivos. Ideal para ver qué han hecho otros.

**La forma directa (Traer y mezclar):**
```bash
git pull origin develop
```

Descarga los cambios de develop remoto y trata de mezclarlos en tu rama actual. Cuidado: puede causar conflictos.

### 📤 Subir cambios (Push)
```bash
git push origin nombre-rama
```

## 🚨 5. Situaciones Reales (Recetario Senior)

Aquí es donde se diferencia un tutorial básico de la vida real.

### Escenario A: "Existe una rama en el servidor y quiero trabajar en ella"

**Situación:** Un compañero creó la rama develop o feature/login y tú necesitas tenerla en tu PC tal cual está allá.
```bash
# 1. Actualiza tu lista de referencias (para que tu git sepa que la rama existe)
git fetch origin

# 2. Crea tu copia local conectada a la remota (Tracking branch)
git checkout -b develop origin/develop
```

**Explicación:** Creas una rama local llamada develop que es un clon exacto de origin/develop y quedan vinculadas.

### Escenario B: "Tengo que cambiar de rama urgente, pero mi trabajo está a medias"

**Situación:** Estás programando, nada funciona aún, y te piden revisar un bug en otra rama. No puedes hacer commit porque romperías todo.
```bash
# 1. Guarda tus cambios temporalmente en un "cajón"
git stash

# 2. Cambia de rama y haz lo que debas hacer
git checkout main
# ... trabajar ...

# 3. Vuelve a tu rama y recupera tu trabajo
git checkout mi-feature
git stash pop
```

**Explicación:** stash congela tu estado actual y deja el directorio limpio. pop devuelve los cambios y borra el stash.

### Escenario C: "Me equivoqué en el mensaje del último commit"

**Situación:** Hiciste commit pero escribiste "fix: errror" y te da vergüenza o olvidaste incluir un archivo.
```bash
# (Si olvidaste un archivo, haz git add primero)
git commit --amend -m "fix: corrección de error ortográfico en el título"
```

**Ojo:** Solo haz esto si aún no has hecho push. Si ya subiste el código, déjalo así.

### Escenario D: "He roto todo, quiero volver a como estaba el último commit"

**Situación:** Hiciste un desastre probando código y quieres descartar todos los cambios actuales (resetear el archivo).
```bash
# Peligroso: Borra todos los cambios no guardados
git checkout . 
# O en versiones nuevas de git:
git restore .
```

### Escenario E: "Actualizar mi rama con lo último de develop"

**Situación:** Llevas 3 días en tu rama feature/pomodoro y otros han actualizado develop. Necesitas esos cambios en tu rama.
```bash
# 1. Asegúrate de estar en tu rama
git checkout feature/pomodoro

# 2. Trae la info nueva
git fetch origin

# 3. Fusiona develop dentro de tu rama
git merge origin/develop
```

**Tip:** Si hay conflictos, Git te pedirá resolverlos manualmente en el editor.

## 💡 Glosario Rápido

- **Origin:** El apodo estándar para el repositorio en GitHub.
- **HEAD:** Un puntero que indica "¿Dónde estoy parado ahora mismo?".
- **Conflict:** Cuando dos personas tocaron la misma línea de código y Git no sabe con cuál quedarse.
- **Pull Request (PR):** No es un comando de Git, es una funcionalidad de GitHub para pedir que revisen y fusionen tu código.