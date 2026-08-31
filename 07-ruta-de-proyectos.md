# 07 - Ruta de proyectos practicos (el plan de estudio real)

> Objetivo: darte un camino concreto, proyecto por proyecto, de principiante a
> pro. Porque se aprende HACIENDO. Este es el corazon del curso.

---

## Como funciona esta ruta

Son 8 proyectos en dificultad creciente. Cada uno introduce conceptos nuevos
sobre lo anterior. No los saltees: cada uno te prepara para el siguiente.

Para cada proyecto: (1) construilo con la IA al lado, (2) entende cada pieza,
(3) subilo a GitHub, (4) escribí en `mis-notas.md` que aprendiste. Al
terminar los 8, no vas a "saber programar" de memoria: vas a saber
CONSTRUIR, que es lo que importa.

Tiempo estimado total: 3-6 meses a ritmo tranquilo (45 min/dia). Sin apuro.

---

## Nivel 1 - Fundamentos

### Proyecto 1: Tu pagina personal (1 archivo)
**Que:** una pagina `index.html` con tu nombre, una foto, tus proyectos y tus
links. Un solo archivo con HTML + CSS + un poco de JS.
**Aprendes:** los 3 pilares del frontend, como se ve el codigo, editar y
recargar.
**Conceptos nuevos:** HTML, CSS, JS basico.
**Publicalo:** GitHub Pages. Tu primera cosa online y tuya.
**Extra pro:** hacela responsive (que se vea bien en el celu).

### Proyecto 2: Calculadora o conversor con logica
**Que:** una mini-app en el navegador: conversor de monedas (CLP/USD),
calculadora de propinas, o un contador. Con JavaScript de verdad.
**Aprendes:** variables, funciones, eventos (clicks), manipular la pagina con
JS. El "comportamiento".
**Conceptos nuevos:** logica de programacion, eventos, estado simple.
**Publicalo:** GitHub Pages.

---

## Nivel 2 - Interactividad y datos

### Proyecto 3: App de tareas (To-Do) en React
**Que:** la app clasica: agregar tareas, marcarlas como hechas, borrarlas.
Pero en React, no HTML plano.
**Aprendes:** componentes, estado (state), listas, el porque de los
frameworks. Este es tu salto a "app moderna".
**Conceptos nuevos:** React, componentes, estado, Vite, npm/pnpm, TypeScript.
**Guardala en el navegador:** usa `localStorage` para que las tareas
sobrevivan al recargar (todavia sin backend).
**Publicalo:** Cloudflare Pages o GitHub Pages.

### Proyecto 4: App que consume una API publica
**Que:** una app que trae datos de internet: el clima de tu ciudad, un
buscador de peliculas, cotizacion del dolar, o fotos de perros. Muestra los
datos lindos.
**Aprendes:** como el frontend pide datos a una API, manejar la espera
(loading) y los errores. EL concepto que conecta front con el mundo.
**Conceptos nuevos:** fetch/HTTP, JSON, async (esperar respuestas), APIs REST.
**Extra pro:** un buscador con filtros. Como tu Plantoteca de MALP.

---

## Nivel 3 - Full stack (front + back + datos reales)

### Proyecto 5: App con login y base de datos (Supabase)
**Que:** una app donde el usuario se registra, entra, y guarda cosas SUYAS
(su lista de libros, sus gastos, su coleccion de algo). Datos reales que
persisten en la nube y son privados de cada usuario.
**Aprendes:** el modelo full stack completo, autenticacion, base de datos,
seguridad (RLS). Este proyecto te vuelve peligroso (en el buen sentido).
**Conceptos nuevos:** Supabase (Auth + Postgres + RLS), modelo de datos,
autenticacion vs autorizacion, TanStack Query.
**Este es el proyecto clave del curso.** Es, basicamente, MALP simplificado.
De hecho: **podrias retomar MALP aca** (ver su `GUIA_PARA_RETOMAR.md`).
**Publicalo:** front en Pages + datos en Supabase. Full stack real, gratis.

---

## Nivel 4 - IA, bots y automatizacion

### Proyecto 6: Tu primer script de automatizacion (Python)
**Que:** un script Python que haga algo util por vos: renombrar archivos en
masa, generar un reporte desde un CSV, mandarte un email con algo, o bajar
datos de una API y guardarlos.
**Aprendes:** Python, correr scripts, entornos virtuales, leer/escribir
archivos, llamar APIs desde codigo.
**Conceptos nuevos:** Python, uv/pip, venv, librerias (`requests`), triggers.
**Extra pro:** programalo para que corra solo cada dia (Programador de tareas
de Windows o GitHub Actions).

### Proyecto 7: Un chatbot con IA (LLM)
**Que:** un bot que conversa usando un LLM real (Gemini/Claude via API). Puede
ser de terminal primero, despues web. Con una personalidad y un tema (asesor
de plantas, tutor de ingles, lo que quieras).
**Aprendes:** llamar a la API de un LLM, system prompts, manejar contexto/
memoria, guardrails basicos. La IA generativa aplicada de verdad.
**Conceptos nuevos:** API de LLM, system prompt, temperatura, tokens en la
practica, memoria de conversacion.
**Este es Kitradep simplificado.** Podrias estudiar ese repo como referencia
de lujo (arquitectura hibrida, guardrails, backend intercambiable).
**Extra pro:** agregale RAG - que responda basandose en TUS documentos.

### Proyecto 8: Bot conectado a un canal real + desplegado 24/7
**Que:** llevar el bot del proyecto 7 a WhatsApp o Telegram, y desplegarlo en
un VPS para que este siempre disponible.
**Aprendes:** webhooks, desplegar en un servidor real, HTTPS, mantener algo
prendido, monitoreo. El ciclo completo hasta produccion.
**Conceptos nuevos:** webhook, VPS, Docker, Caddy/SSL, monitoreo, deploy.
**Este es literalmente la Fase B-G de Kitradep.** Su `GUIA_PARA_RETOMAR.md` es
tu instructivo paso a paso. **Podrias terminar Kitradep como proyecto 8.**

---

## Despues de los 8: como se ve "ser pro"

No hay un diploma. Sos "pro" cuando:

- Podes tomar una idea y descomponerla mentalmente en front / back / datos /
  hosting sin ayuda.
- Elegis las herramientas con criterio (no la de moda: la adecuada).
- Diriges a la IA con precision y validas lo que produce.
- Cuando algo se rompe, sabes por donde empezar a buscar.
- Publicas cosas que otros usan de verdad.

De ahi en adelante, se profundiza eligiendo una direccion:
- **Frontend avanzado**: animaciones, performance, Next.js, diseno.
- **Backend/datos**: APIs complejas, optimizar bases de datos, arquitectura.
- **IA/ML**: RAG avanzado, agentes complejos, evaluacion de modelos.
- **DevOps/nube**: escalar de verdad, AWS/Azure, CI/CD, seguridad.
- **Producto**: juntar todo para lanzar cosas que la gente pague/use.

Elegí lo que te divierta. La pasion sostiene el aprendizaje largo.

---

## Habitos que te hacen pro (mantenelos todo el curso)

1. **Commiteá seguido** con mensajes claros. Git es tu red.
2. **Escribi lo que aprendes** en `mis-notas.md`. Ensena a tu yo futuro.
3. **Leé codigo de otros** (tus propios repos viejos, proyectos open source).
4. **Preguntale a la IA el "por que", no solo el "como".**
5. **Terminá lo que empezas.** Un proyecto terminado ensena mas que diez a
   medias. (Por eso dejamos MALP y Kitradep con guias para terminarlos!)
6. **Compartí lo que haces.** Feedback = crecimiento acelerado.

---

## Hacelo vos

1. Elegí el proyecto 1 y arrancalo HOY. No manana. Hoy.
2. Crea un tablero simple (papel, Notion, lo que sea) con los 8 proyectos y
   marcá tu avance. Ver el progreso motiva.
3. Agenda 45 min fijos, 5 dias a la semana. La consistencia gana.

---

Para seguir aprendiendo mas alla de la ruta:
[capitulo 08: Recursos curados](08-recursos.md).
