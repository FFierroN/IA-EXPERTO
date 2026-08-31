# Ruta IA - De cero a pro en IA generativa y Claude Code

> Una guia didactica, en espanol, para meterte de verdad al mundo de crear
> software con ayuda de la IA: apps, PWAs, backend, frontend, bots,
> automatizaciones, hosting y nube.
>
> Escrita por Kira (Code Puppy) para Felipe Fierro. 2026-08-31.

---

## Para quien es esto

Para vos, que ya probaste el poder de construir cosas con una IA al lado
(Kitradep, MALP, tu PWA del Mundial) y ahora queres **entender de verdad**
como funciona todo, para no depender de la magia y poder crear lo que se te
ocurra. No asume que seas ingeniero. Asume que sos curioso y que aprendes
haciendo.

## La promesa

Si segues esta ruta y construis los proyectos que propone, en unos meses vas
a poder:

- Conversar con cualquier IA generativa sabiendo que pasa por dentro.
- Dirigir a Claude Code (u otro agente) como un profesional, no como quien
  le reza a una caja negra.
- Levantar un frontend, un backend, una base de datos y publicarlos online.
- Armar un bot y automatizaciones que trabajen por vos.
- Decidir con criterio cuando pagar un servidor y cuando ir a la nube.

## Como usar esta guia

Leela **en orden** la primera vez (cada capitulo se apoya en el anterior).
Despues volve a los capitulos como referencia. Cada uno termina con una
seccion **"Hacelo vos"** con ejercicios concretos: no saltes esa parte, ahi
esta el 80% del aprendizaje.

Regla de oro: **no leas mas de un capitulo sin construir algo.** La IA se
aprende con las manos, no con los ojos.

---

## Indice del curso

| # | Capitulo | Que vas a aprender |
|---|----------|--------------------|
| 00 | [Mentalidad y como aprender](00-mentalidad-y-como-aprender.md) | Como se aprende esto sin frustrarte + el meta-truco |
| 01 | [Fundamentos de IA generativa](01-fundamentos-ia-generativa.md) | Que es un LLM, tokens, prompts, contexto, RAG, agentes |
| 02 | [Claude Code y agentes de codigo](02-claude-code-y-agentes.md) | Como dirigir un agente para que construya software real |
| 03 | [Frontend y PWA](03-frontend-y-pwa.md) | Lo que ve el usuario: HTML/CSS/JS, React, apps instalables |
| 04 | [Backend, datos y APIs](04-backend-datos-apis.md) | El cerebro: servidores, bases de datos, Python, Supabase |
| 05 | [Bots y automatizaciones](05-bots-y-automatizaciones.md) | Que la maquina trabaje por vos: bots, scraping, tareas |
| 06 | [Hosting: servidores vs nube](06-hosting-servidores-vs-nube.md) | Donde vive tu app y cuando pagar que cosa |
| 07 | [Ruta de proyectos practicos](07-ruta-de-proyectos.md) | El plan de estudio real, proyecto por proyecto |
| 08 | [Recursos curados](08-recursos.md) | Los mejores links para seguir aprendiendo |
| 09 | [Glosario](09-glosario.md) | Todos los terminos raros explicados en cristiano |

---

## El mapa mental (la foto grande)

Todo el software que vas a construir se arma con estas piezas. Metetelas en
la cabeza ahora; el resto de la guia es aprender cada una:

```
   [ USUARIO ]
       |
       v
  FRONTEND  ...... lo que se ve y se toca (navegador, celu)   -> cap. 03
       |
       | (pide datos por internet)
       v
  BACKEND / API .. la logica y las reglas del negocio          -> cap. 04
       |
       v
  BASE DE DATOS .. donde se guarda todo de forma permanente     -> cap. 04
       ^
       |
  BOTS / AUTOMAT.. procesos que corren solos y alimentan todo   -> cap. 05

  Todo esto vive en algun lado:
  HOSTING ........ VPS o nube (AWS/Azure/GCP)                    -> cap. 06

  Y vos construis todo esto dirigiendo a:
  UN AGENTE DE IA (Claude Code) .. tu multiplicador de fuerza   -> cap. 02
```

Cuando entiendas como se conectan estas cajas, dejas de sentir que el
software es magia. Es LEGO. Bloques que encajan.

---

## Una nota de Kira antes de arrancar

No tenes que memorizar nada de esto. Nadie sabe todo de memoria: los mejores
programadores googlean (o le preguntan a la IA) cien veces al dia. Lo que sí
tenes que construir es el **mapa mental**: saber que existe cada pieza, para
que sirve, y como se conectan. Con ese mapa, cualquier detalle lo buscas en
30 segundos.

La IA generativa no te reemplaza como creador; te da superpoderes. Pero los
superpoderes sin criterio son peligrosos (facturas de nube de miles de
dolares, apps inseguras, codigo que nadie entiende). Esta guia te da el
criterio, no solo los comandos.

Dale, jefe. Empeza por el capitulo 00. Nos "leemos" en cada pagina.

-- Kira
