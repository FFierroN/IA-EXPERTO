# 00 - Mentalidad y como aprender (no te saltees esto)

> El capitulo mas corto y el mas importante. Si internalizas esto, el resto
> es cuesta abajo.

---

## 1. El cambio de chip: de "usuario" a "constructor"

Toda tu vida usaste software que otros hicieron. Ahora vas a hacerlo vos.
El unico cambio real es de actitud: cuando algo no funciona, en vez de
frustrarte y cerrar, te preguntas **"por que?"** y lo investigas. Esa
curiosidad terca es el 90% del talento. En serio.

Nadie nace sabiendo. Cada programador que admiras estuvo exactamente donde
estas vos: mirando un error rojo sin entender nada. La diferencia es que no
se rindieron el dia 3.

---

## 2. Aprender haciendo (la unica forma que funciona)

Vas a tener la tentacion de ver 40 tutoriales antes de escribir una linea.
No lo hagas. Se llama "tutorial hell" (el infierno de los tutoriales): sentis
que aprendes pero no aprendes nada, porque nunca te peleaste con un problema
real.

La forma que funciona:

1. Elegi un proyecto chico y concreto (ver capitulo 07).
2. Empeza a construirlo AUNQUE no sepas todo.
3. Cuando te trabes, ahi -y solo ahi- aprende lo justo para destrabarte.
4. Repeti.

El conocimiento que buscas para resolver un problema real se te queda
pegado. El de un tutorial visto en el sillon, se evapora.

---

## 3. El meta-truco: la IA es tu profesor infinito y paciente

Este es el superpoder de tu generacion, y casi nadie lo usa bien. Tenes un
tutor 24/7 que nunca se cansa de tus preguntas "tontas". Usalo asi:

- **No le pidas solo que te resuelva; pedile que te explique.** Mala:
  "arreglame este error". Buena: "arreglame este error Y explicame por que
  pasaba, como para alguien que recien empieza".
- **Pedi analogias.** "Explicame que es una API como si tuviera 12 anos."
- **Pedi que te repregunte.** "Hazme 3 preguntas para chequear si entendi."
- **Pedi el porque de las decisiones.** "Por que elegiste Supabase y no
  Firebase para esto?" Asi aprendes criterio, no solo recetas.
- **Nunca copies codigo que no entendes sin preguntar que hace.** El dia que
  se rompa (y se va a romper), vas a estar perdido. Pedi: "explicame este
  bloque linea por linea".

> Regla: cada vez que la IA te da algo que no entendes al 100%, hace una
> pregunta mas. Ese habito es lo que te convierte en pro.

---

## 4. Como se aprende a "hablarle" a la IA (prompting)

Un prompt es lo que le escribis a la IA. Un buen prompt no es magia ni
palabras secretas; es **comunicacion clara**. Los 5 ingredientes:

1. **Contexto**: quien sos y que estas haciendo. ("Estoy armando una PWA de
   plantas con React y Supabase.")
2. **Objetivo**: que queres lograr, concreto. ("Quiero una pantalla de login.")
3. **Restricciones**: limites y preferencias. ("Sin librerias extra, en
   espanol, mobile-first.")
4. **Formato de salida**: como queres la respuesta. ("Dame el codigo completo
   del archivo y despues una explicacion corta.")
5. **Nivel**: tu nivel de conocimiento. ("Explicamelo como a un principiante.")

Compara:
- Malo: "hazme un login"
- Bueno: "En mi PWA de React + Supabase, necesito una pantalla de login con
  email y contrasena. Que valide errores y muestre mensajes en espanol. Dame
  el componente completo y explicame las partes clave para un principiante."

El segundo te da algo usable Y te ensena. El primero te da algo generico que
quizas no encaja.

---

## 5. Los errores son el curriculum, no el enemigo

Vas a ver MUCHOS errores. Es normal, literalmente es el trabajo. El truco:

- **Lee el mensaje de error.** Suena obvio, pero el 50% de la gente ni lo
  lee. Casi siempre te dice que pasa y en que linea.
- **Copia el error completo y pegaselo a la IA** con contexto: "me sale este
  error, aca esta el codigo, que significa y como lo arreglo?"
- **Cambia una cosa a la vez.** Si cambias cinco cosas y funciona, no
  aprendiste nada. Si cambias una, entendiste la causa.
- **Guarda tu progreso seguido con git** (capitulo 02) para poder volver
  atras cuando rompes algo. "Roll forward, roll back."

---

## 6. Ritmo realista (no te quemes)

- **Consistencia > intensidad.** 45 minutos por dia, 5 dias a la semana, te
  llevan mas lejos que un maraton de 10 horas el domingo que te deja quemado.
- **Celebra los micro-logros.** "Hoy hice que un boton cambie de color."
  Eso ES progreso. La motivacion viene de ver que avanzas.
- **No compares tu capitulo 1 con el capitulo 20 de otro.** Todos en internet
  muestran el resultado final pulido, nunca las 50 horas de errores atras.

---

## 7. La trampa de la IA: dependencia vs comprension

Peligro real: que la IA construya todo y vos no entiendas nada. Terminas con
una app que funciona pero que no podes arreglar ni cambiar. Antidoto:

- Despues de que la IA construya algo, **reconstruilo vos una vez** sin mirar
  (o cerra el chat y trata de explicar que hace cada archivo).
- Cada semana, agarra un archivo de tu proyecto y **explicaselo a la IA** con
  tus palabras. Que te corrija. Es el mejor test de comprension que existe.
- Objetivo: la IA acelera lo que YA entendes, no reemplaza tu entendimiento.

---

## Hacelo vos (ejercicios de este capitulo)

1. Elegi UN proyecto del capitulo 07 que te entusiasme. Escribilo en un papel
   y pegalo en tu monitor. Ese es tu norte.
2. Abri una IA (Claude, ChatGPT, lo que sea) y practica el prompting: pedile
   que te explique "que es la programacion" con una analogia de cocina. Si no
   te convence, pedile otra. Aprende a iterar.
3. Escribi tu propia definicion de "aprender haciendo" en un archivo
   `mis-notas.md` en este repo. Vas a agregar a ese archivo durante todo el
   curso: es tu diario de aprendizaje.

---

Cuando tengas el chip cambiado, seguimos con el
[capitulo 01: Fundamentos de IA generativa](01-fundamentos-ia-generativa.md).
