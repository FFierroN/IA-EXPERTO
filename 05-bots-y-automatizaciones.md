# 05 - Bots y automatizaciones (que la maquina trabaje por vos)

> Objetivo: hacer que procesos corran solos -bots que conversan, scripts que
> repiten tareas aburridas, cosas que pasan sin que aprietes un boton.

---

## 1. Que es un bot y que es una automatizacion

- **Automatizacion**: un programa que hace una tarea repetitiva por vos, sin
  intervencion humana. Ej: "todos los dias a las 8am, baja los resultados de
  los partidos y actualiza la base de datos" (eso hace el `robot/` de tu PWA
  del Mundial). O "cuando llega un mail con factura, guardala en una carpeta".
- **Bot**: un programa con el que se interactua, normalmente conversando. Ej:
  un chatbot de WhatsApp (como Kitradep), un bot de Telegram, un bot de
  Discord. Un bot suele ser una automatizacion + una interfaz de conversacion.

Los dos comparten el mismo corazon: **codigo que reacciona a algo y hace una
accion.** La diferencia es el disparador (el usuario que escribe, vs el reloj
que marca las 8am, vs el mail que llega).

---

## 2. Los disparadores (triggers): que hace arrancar un proceso

Todo bot/automatizacion arranca por un **trigger**. Los mas comunes:

- **Tiempo (schedule/cron)**: "corre cada dia/hora/minuto". El `cron` es el
  clasico en servidores; en Windows es el "Programador de tareas". Ideal para
  reportes diarios, backups, scraping periodico.
- **Webhook (evento web)**: "cuando pase X, avisame a esta URL". WhatsApp le
  pega a tu webhook cuando alguien escribe (asi funciona la Fase B de
  Kitradep). Es el trigger de los bots conversacionales.
- **Manual / a demanda**: vos corres el script cuando lo necesitas.
- **Cambio en datos**: "cuando se agregue una fila a esta tabla, hace Y"
  (Supabase y otros lo soportan).

---

## 3. Python para automatizacion (tu mejor amigo aca)

Python es el rey de la automatizacion porque es simple y tiene una libreria
para todo. Cosas que automatizas facil:

- **Leer/escribir archivos, Excel, CSV, PDF.**
- **Mandar emails** (libreria `smtplib`, como las notificaciones de Kitradep).
- **Llamar a APIs** de otros servicios (libreria `requests` o `httpx`).
- **Web scraping**: extraer datos de paginas web (ver seccion 5).
- **Tareas programadas**: correr algo cada cierto tiempo.
- **Procesar datos**: pandas para analisis tipo Excel con superpoderes.

Ejemplo mental de una automatizacion util: un script que cada manana llama a
una API del clima, y si va a llover, te manda un WhatsApp "no riegues hoy".
Trigger (cron) + API (clima) + accion (mensaje). Tres piezas, listo.

---

## 4. Como se construye un bot de chat (la anatomia)

Un bot conversacional (como Kitradep) tiene estas partes -reconocelas porque
son universales:

1. **El canal / la interfaz**: por donde habla el usuario. WhatsApp, Telegram,
   web, Discord. Cada uno tiene su forma de conectarse (API o webhook).
2. **El webhook / receptor**: el codigo que RECIBE el mensaje entrante. (En
   Kitradep, es la Fase B pendiente: `whatsapp_webhook.py`.)
3. **El cerebro / router**: decide que responder. Puede ser:
   - **Basado en reglas / menu** (arboles de decision, "escribi 1 para
     agendar"): predecible, barato, pero rigido. La Fase 1-2 de Kitradep.
   - **Basado en LLM**: conversacion natural con una IA. Flexible pero hay que
     ponerle guardrails. La Fase 3 de Kitradep.
   - **Hibrido** (lo mejor de ambos): LLM para conversar + logica estricta
     para tareas criticas como agendar. Es la arquitectura de Kitradep.
4. **La memoria**: para recordar el hilo de la conversacion (en Kitradep,
   `db.py` guarda la sesion por numero de telefono).
5. **Los guardrails**: reglas de seguridad que el bot nunca cruza (no
   diagnosticar, derivar urgencias, no filtrar datos). Sagrados.
6. **La respuesta de vuelta**: mandar el texto al canal por su API.

Si entendes estas 6 piezas, entendes cualquier bot del mundo. Kitradep las
tiene todas; te recomiendo abrir ese repo y mapear cada pieza a su archivo.

---

## 5. Web scraping: extraer datos de la web (con cuidado)

**Scraping** es leer una pagina web con un programa y sacarle datos (precios,
resultados, noticias). Librerias Python: `requests` + `BeautifulSoup` para
paginas simples; `Playwright` o `Selenium` para paginas con mucho JavaScript
(que controlan un navegador de verdad).

Advertencias serias (no las ignores):
- **Respeta los terminos de servicio** del sitio. Muchos prohiben scraping.
- **No scrapees sitios de la competencia** para robar precios/catalogo: ademas
  de poco etico, puede ser ilegal y en entornos corporativos esta prohibido.
- **Se gentil**: no bombardees un sitio con miles de pedidos por segundo; lo
  podes tirar abajo y te bloquean.
- **Preferí APIs oficiales** cuando existan. Es mas estable y legitimo. Tu
  robot del Mundial usa una API de datos deportivos (Highlightly), que es la
  forma correcta.

---

## 6. Plataformas no-code / low-code de automatizacion

No todo requiere programar de cero. Para conectar servicios entre si
(cuando pasa X en la app A, hace Y en la app B) existen plataformas visuales:

- **Zapier / Make (Integromat)**: conectas apps con clics. "Cuando llega un
  formulario, agregalo a una planilla y mandame un mail." Rapido, pero de pago
  y con limites.
- **n8n**: alternativa open source, autohospedable (la corres en tu servidor),
  mas poder y sin costo por accion. Muy querida por los que saben.
- **IFTTT**: mas simple, orientado a lo personal/hogar.

Cuando usar no-code vs codigo: si es una conexion simple entre servicios
populares y no queres mantener codigo, no-code gana. Si necesitas logica
custom, control fino, o evitar costos por volumen, codigo (Python) gana.
Muchos pros usan las dos: no-code para lo simple, codigo para lo complejo.

---

## 7. Donde corren los bots y automatizaciones

Una automatizacion necesita algo prendido para correr:

- **Tu propia compu**: gratis, pero solo corre cuando la tenes prendida. Sirve
  para tareas manuales o mientras desarrollas.
- **Un servidor / VPS 24/7**: para bots que deben estar siempre disponibles
  (como Kitradep en produccion). Ver capitulo 06.
- **Serverless / Functions**: para tareas cortas que corren y mueren (un
  webhook que responde y listo). No pagas por tener algo prendido siempre,
  solo por cada ejecucion. Ideal y barato para muchos bots. Ej: Cloudflare
  Workers (tu `worker-vivo/` del Mundial es esto), AWS Lambda, Supabase Edge
  Functions.
- **Un runner programado**: GitHub Actions puede correr un script cada cierto
  tiempo gratis (para automatizaciones livianas periodicas).

---

## Hacelo vos (ejercicios)

1. Escribi un script Python que lea un archivo de texto con nombres y te salude
   a cada uno. Primer paso de automatizar: leer + procesar + producir.
2. Usa la libreria `requests` para llamar a una API publica y gratis (busca
   "APIs publicas gratis", ej. una de chistes o del clima) e imprime la
   respuesta. Acabas de consumir una API desde codigo.
3. Abri Kitradep y mapea las 6 piezas de un bot (seccion 4) a sus archivos
   reales (`router.py`, `db.py`, `guardrails.py`, etc.). Reconocé la anatomia.
4. Pensa una tarea aburrida y repetitiva de tu vida. Escribila en tus notas
   y bosqueja: cual seria el trigger, que datos necesita, que accion hace.
   Ese es tu primer proyecto de automatizacion.

---

Ya sabes construir las partes. Ahora: donde vive todo esto y cuanto cuesta:
[capitulo 06: Hosting - servidores vs nube](06-hosting-servidores-vs-nube.md).
