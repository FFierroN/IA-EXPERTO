# 02 - Claude Code y agentes de codigo

> Objetivo: que dirijas a un agente de IA como un profesional. Este es tu
> multiplicador de fuerza: la diferencia entre construir 1 cosa al mes y 10.

---

## 1. Que es Claude Code (y que es un agente de codigo)

Claude Code es un **agente de IA que vive en tu terminal** y puede leer y
escribir archivos de tu proyecto, correr comandos, buscar en el codigo, y
razonar sobre todo eso en un bucle hasta cumplir un objetivo. Es de Anthropic
(los que hacen Claude). Hay primos: Cursor, GitHub Copilot Workspace, Aider,
y Code Puppy (donde vivo yo, Kira).

La diferencia con un chat comun (pegar codigo, copiar respuesta): el agente
**actua sobre tu proyecto real**. No te dice "crea un archivo asi"; lo crea.
No te dice "corre este test"; lo corre y lee el resultado.

Modelo mental correcto: **es un desarrollador junior brillante, rapidisimo y
sin ego, pero que necesita que vos seas el arquitecto/director.** Hace lo que
le pedis increiblemente bien; decidir QUE pedir y validar que este bien, es
tu trabajo.

---

## 2. El flujo de trabajo profesional con un agente

No le tires "hazme una app de plantas" y reces. Trabaja asi:

### Paso 1 - Planificar antes de construir
Pedile primero un PLAN, no codigo: "Quiero una PWA de fidelizacion de
plantas. Antes de escribir codigo, proponeme la arquitectura, el stack y las
fases. No escribas codigo todavia." Lees, discutis, ajustan. Recien despues
construyen. (Esto es exactamente como armamos MALP y Kitradep.)

### Paso 2 - Construir en pasos chicos
"Ahora hagamos SOLO la pantalla de login." Un pedazo a la vez. Pasos chicos =
mas facil de revisar, de testear y de arreglar si algo sale mal.

### Paso 3 - Revisar lo que hizo
Lee el codigo (aunque no entiendas todo, mira el ritmo). Pregunta lo que no
entiendas: "explicame que hace este archivo". No aceptes cajas negras.

### Paso 4 - Probar
Corre la app / los tests. Si funciona, sigues. Si no, le pegas el error.

### Paso 5 - Guardar con git (checkpoint)
Cuando un pedazo funciona, **commit**. Es tu punto de retorno. Si el proximo
paso rompe todo, volves atras sin drama.

### Paso 6 - Repetir
Siguiente pedazo. Y asi.

> El secreto de la gente que construye rapido con IA no es que escribe prompts
> magicos: es que trabaja en LOOPS chicos de plan -> construir -> probar ->
> commit. Confiabilidad sobre velocidad ciega.

---

## 3. Git: tu red de seguridad (aprende esto SI o SI)

Git es un sistema para guardar versiones de tu proyecto. Es lo que te deja
"viajar en el tiempo": volver a como estaba ayer, o antes de romper algo. Con
un agente de IA es INDISPENSABLE, porque a veces hace cambios grandes.

Los 6 comandos que cubren el 95% de tu vida:

```bash
git init                      # empezar a versionar un proyecto (una vez)
git status                    # que cambio desde el ultimo guardado?
git add .                     # marcar todos los cambios para guardar
git commit -m "mensaje claro" # guardar un checkpoint con una descripcion
git log --oneline             # ver el historial de checkpoints
git push                      # subir los checkpoints a GitHub (la nube)
```

Y los salvavidas:

```bash
git diff                      # ver EXACTAMENTE que cambio
git checkout -- archivo.txt   # descartar cambios de un archivo (volver)
git revert <commit>           # deshacer un commit ya hecho (seguro)
```

Filosofia (la misma que uso yo): **commiteá seguido, con mensajes claros.**
Cada commit es una foto a la que podes volver. "Roll forward, roll back."

**GitHub** es donde viven tus repos en la nube (gratis para lo tuyo). Te da:
respaldo, historial accesible desde cualquier lado, y es tu portafolio
publico. Tus proyectos (malp, Kitradep) ya viven ahi en `github.com/FFierroN`.

Reglas de oro de git:
- **Nunca subas secretos.** El `.env` va en `.gitignore` SIEMPRE.
- **Commits chicos y frecuentes** > un commit gigante al final.
- **Mensajes que digan QUE y por que**, no "cambios" ni "fix".

---

## 4. Como escribir prompts para un agente de codigo

Ademas de los 5 ingredientes del cap 00, para codigo agrega:

- **Da contexto del proyecto**: "es una PWA React + Supabase, mobile-first,
  en espanol". El agente que ya trabajo en tu repo lo sabe, pero recordarselo
  ayuda.
- **Se especifico con el alcance**: "SOLO la pantalla de login, no toques
  nada mas". Evitas que se entusiasme y cambie medio proyecto.
- **Pedi que respete lo que existe**: "reusa los componentes y estilos que ya
  hay, no dupliques". (Esto es DRY, ver abajo.)
- **Pedi tests**: "agrega un test que verifique que el login rechaza
  contrasenas vacias".
- **Pedi explicacion al final**: "cuando termines, resumime que cambiaste y
  por que".

Ejemplo de prompt pro:
> "En mi PWA (React + TS + Tailwind + Supabase), agrega logout. Reusa el
> cliente de Supabase que ya esta en `src/lib/supabase.ts`. Que el boton este
> en la pantalla de Perfil, mande al login al cerrar sesion, y muestre un
> estado de 'cargando'. No toques otras pantallas. Al final explicame los
> cambios."

---

## 5. Buenas practicas de codigo que te haran ver pro

Aunque la IA escriba, VOS diriges. Estos principios (que a mi me obsesionan)
hacen la diferencia entre un proyecto que crece sano y uno que se pudre:

- **DRY** (Don't Repeat Yourself): no copies-pegues logica. Si algo se repite,
  se hace una sola vez y se reusa. (En MALP, los colores viven solo en
  `tailwind.config.js`; nadie escribe el hex dos veces.)
- **YAGNI** (You Aren't Gonna Need It): no construyas cosas "por si acaso".
  Construi lo que necesitas HOY. El 80% de las features imaginadas nunca se
  usan.
- **KISS** (Keep It Simple): la solucion mas simple que funcione, gana.
  Complejidad = bugs futuros.
- **Nombres claros**: `calcularPuntosMision()` es mejor que `calc()`. El
  codigo se lee 10 veces mas de lo que se escribe.
- **Archivos chicos y enfocados**: si un archivo pasa de ~500 lineas, capaz
  conviene partirlo (sin partir porque si).
- **Una responsabilidad por pieza**: cada archivo/funcion hace UNA cosa bien.

Podes pedirle a la IA que respete todo esto: "seguí principios DRY y KISS,
nombres claros, y archivos chicos". Y podes pedirle que audite: "revisa este
archivo y decime si viola DRY o si algo esta sobre-complicado".

---

## 6. Los limites del agente (para no frustrarte)

- **Alucina.** Puede inventar una funcion de una libreria que no existe.
  Siempre probá lo que produce.
- **No conoce tu intencion, solo tus palabras.** Si el resultado no es lo que
  querias, casi siempre es que el prompt fue ambiguo. Reformula.
- **Se pierde en proyectos gigantes.** Por eso le das contexto y trabajas en
  pedazos.
- **No tiene tu criterio de negocio.** No sabe que "los precios FONASA son
  sensibles" salvo que se lo digas. Vos sos el dueno del "por que".
- **Puede romper cosas que funcionaban.** Por eso: git, pasos chicos, tests.

El agente es un acelerador brutal, pero **vos sos el piloto.** Nunca aceptes
un cambio grande sin entender que hace.

---

## 7. Como configurar tu entorno (setup real)

Para trabajar con un agente de codigo en tu propia maquina vas a necesitar:

1. **Un editor de codigo**: VSCode es el estandar, gratis, con todo.
2. **Git**: para versionar (ya lo tenes de tus proyectos).
3. **Un runtime segun el lenguaje**:
   - **Node.js** (con npm o pnpm) para frontend / JavaScript / TypeScript.
   - **Python** (con `uv` o pip) para backend, bots, automatizaciones.
4. **Una terminal**: donde corres comandos (PowerShell en Windows sirve).
5. **El agente**: Claude Code, Cursor, o el que elijas. Muchos se instalan
   como extension de VSCode o como comando de terminal.
6. **Cuentas**: GitHub (repos), y las APIs que uses (Anthropic, Supabase,
   etc.), cada una con su clave guardada en `.env`.

No instales todo de golpe. Instala lo que el proyecto que estas haciendo
necesita, cuando lo necesita.

---

## Hacelo vos (ejercicios)

1. Crea un repo nuevo, hace 3 commits chicos (crear un README, agregar una
   linea, corregir un typo) y mira el historial con `git log --oneline`.
   Sentí el ritmo de commitear.
2. Practica un `git revert`: hace un cambio "malo" a proposito, commiteá, y
   despues revertilo. Ahora sabes que siempre podes volver.
3. Toma un archivo de tu PWA del Mundial (MIPROYECTO) y pedile a una IA:
   "explicame que hace este archivo, para un principiante". Comprension sobre
   codigo real.
4. Escribi en `mis-notas.md` tu propio "flujo de 6 pasos" para trabajar con
   un agente, con tus palabras.

---

Ya sabes dirigir al constructor. Ahora, que construir. Empecemos por lo que
ve el usuario: [capitulo 03: Frontend y PWA](03-frontend-y-pwa.md).
