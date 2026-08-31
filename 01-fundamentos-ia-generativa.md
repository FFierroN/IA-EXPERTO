# 01 - Fundamentos de IA generativa

> Objetivo: que entiendas que pasa por dentro cuando le hablas a una IA.
> Sin esto, todo lo demas es magia. Con esto, tenes criterio.

---

## 1. Que es la "IA generativa"

Es un tipo de inteligencia artificial que **genera contenido nuevo**: texto,
imagenes, codigo, audio, video. La diferencia con la IA "de antes" (que
clasificaba o predecia: "esto es spam", "va a llover") es que esta CREA.

El motor mas comun para texto y codigo es el **LLM** (Large Language Model,
Modelo Grande de Lenguaje). Claude, GPT, Gemini y Llama son LLMs.

---

## 2. Como funciona un LLM (la version honesta y simple)

Un LLM es, en esencia, una maquina gigante de **predecir la siguiente
palabra**. Le das un texto y calcula: "dado todo esto, cual es la palabra
mas probable que sigue?". Repite eso miles de veces y arma parrafos enteros.

Analogia: es el autocompletado de tu celular, pero entrenado con casi todo
internet y con una memoria y razonamiento muchisimo mas profundos.

Como aprendio a predecir tan bien? Lo **entrenaron** mostrandole cantidades
absurdas de texto (libros, webs, codigo) y ajustando billones de "perillas"
internas (los **parametros**) hasta que sus predicciones se volvieron
increiblemente buenas. Ese entrenamiento cuesta millones de dolares y meses;
por eso no lo haces vos, lo hacen empresas como Anthropic (Claude), OpenAI
(GPT), Google (Gemini).

**Implicancia clave #1:** el modelo no "sabe" cosas como una base de datos;
"intuye" patrones. Por eso a veces inventa con total seguridad datos falsos.
Eso se llama **alucinacion**. Regla de oro: para datos que importan (fechas,
cifras, nombres, leyes), verifica siempre. La IA es brillante razonando y
pesima siendo tu fuente de verdad factual.

**Implicancia clave #2:** el modelo tiene una **fecha de corte** de
conocimiento (cuando termino su entrenamiento). No conoce lo que paso
despues, salvo que le des esa info vos o tenga acceso a internet/herramientas.

---

## 3. Tokens: la moneda de la IA

Los LLMs no leen letras ni palabras exactas: leen **tokens**, que son
pedacitos de palabra. "planta" puede ser 1 token; "kinesiologia" pueden ser
3-4. Regla practica: en espanol, 1 token es ~0,75 palabras (mas o menos 4
caracteres).

Por que te importa:

- **Se paga por token.** Casi todas las APIs de IA cobran por tokens de
  entrada (lo que mandas) + tokens de salida (lo que responde). Textos mas
  cortos = mas barato y mas rapido.
- **Hay un limite de tokens** por conversacion, la **ventana de contexto**
  (ver abajo). Si te pasas, el modelo "se olvida" del principio.

---

## 4. El contexto: la memoria de trabajo del modelo

La **ventana de contexto** es todo lo que el modelo puede "tener en mente"
de una vez: tu pregunta actual + el historial de la conversacion +
documentos que le pegaste + sus propias respuestas. Se mide en tokens (hoy
van desde ~8.000 hasta 1.000.000+ segun el modelo).

Analogia: es el escritorio del modelo. Cabe cierta cantidad de papeles. Si
metes uno nuevo cuando ya esta lleno, se cae el mas viejo. Por eso en
conversaciones largas el modelo empieza a "olvidar" lo del principio.

Consecuencias practicas:

- **Un LLM no tiene memoria entre conversaciones distintas.** Cada chat
  nuevo arranca en blanco (salvo que la herramienta tenga memoria aparte,
  como el "kennel" que uso yo, o como Claude Code con sus archivos de
  proyecto). Lo que "recuerda" dentro de un chat es solo lo que cabe en la
  ventana.
- **Darle buen contexto es tu trabajo.** Si le pegas el codigo relevante y le
  explicas el objetivo, responde 10 veces mejor.
- **Conversaciones eternas se degradan.** Si un chat se volvio larguisimo y
  confuso, a veces conviene empezar uno nuevo con un resumen limpio.

---

## 5. Prompt, system prompt y roles

- **Prompt**: lo que le escribis (ya lo vimos en el cap 00).
- **System prompt** (prompt de sistema): instrucciones "de fondo" que definen
  como se comporta el modelo en TODA la conversacion. Ej: "Sos un asistente de
  kinesiologia que trata de usted y nunca da diagnosticos." El usuario no lo
  ve, pero manda sobre el comportamiento. (En Kitradep, esto vive en
  `prompts/kitra.txt`.)
- **Roles**: las conversaciones se estructuran en turnos con rol `system`,
  `user` (vos) y `assistant` (el modelo). Entender esto te sirve cuando
  programes con la API.

---

## 6. Temperatura y otros "diales"

Cuando usas la API podes ajustar parametros. El mas util de entender:

- **Temperature** (temperatura): cuan "creativo/aleatorio" es. Baja (0-0,3) =
  respuestas mas deterministas y precisas (ideal para codigo, datos,
  clasificacion). Alta (0,7-1) = mas variado y creativo (ideal para escribir,
  brainstorming). Para un bot que agenda citas, queres temperatura baja.

---

## 7. Las 3 formas de "darle conocimiento" a una IA

Esto es CRUCIAL y mucha gente lo confunde. Hay tres formas, de menos a mas
costosa:

### a) Prompting / In-context (meterle la info en el prompt)
Le pegas la informacion directamente en la conversacion. "Aca estan los
precios de mi tienda: [...]. Responde segun esto." Simple, inmediato, gratis
(mas alla del costo de tokens). Es lo primero que debes intentar SIEMPRE.

### b) RAG (Retrieval-Augmented Generation)
Cuando tenes MUCHA info (cientos de documentos) que no cabe en el prompt.
La idea: guardas tus documentos en una **base de datos vectorial** (usando
**embeddings**, ver abajo), y cuando el usuario pregunta algo, el sistema
busca los 3-5 fragmentos mas relevantes y SOLO esos se los pega al prompt.
Asi el modelo responde con TU informacion sin necesidad de reentrenarlo.
Es como darle a un estudiante brillante los apuntes correctos justo antes del
examen. La mayoria de los "chatbots que saben de mi empresa" son RAG.

### c) Fine-tuning (afinar el modelo)
Reentrenar (un poco) el modelo con tus propios ejemplos para cambiar su
ESTILO o comportamiento. Es caro, lento, y casi nunca es lo que necesitas.
Mito comun: "quiero que el bot sepa de mi negocio, hay que hacer
fine-tuning". NO. Para que SEPA cosas, usas prompting o RAG. Fine-tuning es
para que se COMPORTE de cierta forma muy especifica, y raramente vale la pena
para un proyecto chico.

> Regla practica: 95% de los proyectos se resuelven con prompting + RAG.
> Fine-tuning es la excepcion, no la regla.

---

## 8. Embeddings (el concepto que desbloquea RAG y busqueda)

Un **embedding** es convertir un texto en una lista de numeros (un vector)
que representa su SIGNIFICADO. Textos con significado parecido dan vectores
cercanos. "perro" y "cachorro" quedan cerca; "perro" y "taladro" quedan lejos.

Para que sirve: **busqueda semantica** (por significado, no por palabras
exactas). Buscas "como cuido mi planta con poca luz" y encuentra un documento
que dice "plantas de sombra", aunque no compartan ninguna palabra. Es el
motor detras de RAG.

No necesitas entender la matematica; necesitas saber que existe y para que
sirve.

---

## 9. Agentes: cuando la IA no solo habla, sino que ACTUA

Un LLM solo, genera texto. Un **agente** es un LLM al que le diste
**herramientas** (tools) y un objetivo, y puede decidir usarlas en un bucle:

```
Objetivo: "arregla el bug del login"
  -> el agente LEE archivos (tool)
  -> RAZONA que esta mal
  -> EDITA un archivo (tool)
  -> CORRE los tests (tool)
  -> ve el resultado, y si fallo, vuelve a intentar
  -> hasta lograr el objetivo
```

Claude Code (capitulo 02) es exactamente esto: un agente con herramientas
para leer/escribir archivos y correr comandos en tu compu. Yo, Kira, soy un
agente. La clave conceptual: **el agente decide que herramienta usar y
cuando, en un loop, hasta cumplir la meta.** Eso es lo que lo hace sentir
"inteligente" de verdad.

Conceptos relacionados que vas a escuchar:
- **Function calling / tool use**: el mecanismo por el cual el modelo pide
  usar una herramienta ("quiero llamar a la funcion enviar_email con estos
  datos").
- **MCP (Model Context Protocol)**: un estandar para conectarle herramientas
  y fuentes de datos a los agentes de forma ordenada. Lo vas a ver mucho.

---

## 10. Modelos: como elegir (y por que hay tantos)

No hay "el mejor modelo"; hay trade-offs entre tres cosas: **inteligencia**,
**velocidad** y **costo**. Cada familia (Claude, GPT, Gemini) tiene:

- Modelos **grandes/pro**: los mas inteligentes, mas caros y lentos. Para
  tareas complejas (arquitectura, razonamiento, codigo dificil).
- Modelos **chicos/flash/mini**: rapidos y baratos, un poco menos capaces.
  Para tareas simples y alto volumen (clasificar, responder FAQs, un bot de
  atencion). En Kitradep usamos `gemini-flash-latest` justamente por esto.

Regla practica: **empeza con un modelo chico/barato; solo subi a uno grande
si la calidad no alcanza.** No pagues Ferrari para ir a la esquina.

Otra decision: **API cerrada vs modelo abierto.**
- **API cerrada** (Claude, GPT, Gemini): le pagas a la empresa por uso, es
  facil, siempre esta actualizado, no manejas infraestructura. Ideal para
  empezar y para el 95% de los casos.
- **Modelo abierto** (Llama, Mistral, etc.): lo corres vos en tu servidor.
  Mas control y privacidad, sin costo por token, pero pagas el servidor
  (caro si necesita GPU) y la complejidad. Para casos con requisitos fuertes
  de privacidad o volumen enorme.

---

## 11. Privacidad y seguridad (no lo saltees)

- **Nunca mandes secretos a una IA** que no deberian salir de tu maquina:
  contrasenas, claves de API, datos personales de clientes (PII), datos
  medicos. Una vez que salen, salieron.
- **Las claves de API son como tu tarjeta de credito.** Si alguien roba tu
  `GEMINI_API_KEY`, gasta con tu plata. Van en un archivo `.env` que NUNCA
  se sube a git (por eso `.gitignore`).
- **Prompt injection**: si tu app deja que usuarios metan texto que va al
  prompt, un malicioso puede intentar "secuestrar" al modelo ("ignora tus
  instrucciones y..."). Por eso existen los **guardrails** (como en Kitradep):
  filtros deterministas que revisan antes/despues del LLM.

---

## Hacelo vos (ejercicios)

1. Anda a un "tokenizer" online (busca "tiktokenizer" o el tokenizer de
   Anthropic) y pega un parrafo tuyo. Mira cuantos tokens son. Intuicion
   ganada.
2. Pedile a una IA la MISMA pregunta creativa dos veces con temperatura
   distinta (si la herramienta te deja), o simplemente observa cuanto varian
   dos respuestas a "escribime un eslogan para una tienda de plantas".
3. Explica con TUS palabras, en `mis-notas.md`, la diferencia entre prompting,
   RAG y fine-tuning. Si no podes explicarlo, releelo. Este concepto es oro.
4. Diseña (en papel) como harias un chatbot que responde sobre los cuidados
   de 200 plantas distintas. Prompting, RAG o fine-tuning? Por que? (Pista:
   200 fichas no caben en un prompt...)

---

Ya tenes el mapa mental de la IA. Ahora, a domarla:
[capitulo 02: Claude Code y agentes de codigo](02-claude-code-y-agentes.md).
