# 06 - Hosting: servidores vs nube (donde vive tu app y cuanto cuesta)

> Objetivo: que decidas CON CRITERIO donde publicar tus proyectos, y que nunca
> te llegue una factura de nube de miles de dolares por sorpresa.

---

## 1. Que es "hosting" y por que lo necesitas

Tu app, tu bot, tu base de datos: todo eso es codigo y datos que necesitan
correr en una **computadora prendida y conectada a internet 24/7** para que
la gente los use. Tu compu personal no sirve (la apagas, se corta el wifi, no
tiene una direccion publica estable). El **hosting** es alquilar esa
computadora-siempre-prendida.

Hay muchos niveles de "cuanto te dan hecho". De menos a mas gestionado:

```
Vos administras TODO  <---------------------------------->  Te dan TODO hecho
  Servidor dedicado     VPS      Nube (IaaS)   PaaS      Serverless   BaaS
     (raro)          (Hetzner) (AWS EC2)   (Railway)  (Lambda)  (Supabase)
```

Cuanto mas a la derecha, menos te preocupas por la infraestructura pero menos
control tenes (y a veces mas caro por unidad). La habilidad pro es elegir el
punto justo para cada proyecto.

---

## 2. El menu de opciones (que es cada cosa)

### Hosting estatico (para frontends / sitios / PWAs)
Si tu app es frontend puro (HTML/CSS/JS o React ya "buildeado"), no necesitas
un servidor con logica: solo algo que sirva archivos. Es **gratis** y
facilisimo:
- **GitHub Pages**: gratis, publica desde tu repo. Lo usan MALP y tu Mundial.
- **Cloudflare Pages / Netlify / Vercel**: gratis, aun mas potentes (manejan
  bien las rutas de las apps, deploys automaticos, dominios). Vercel es la
  casa de Next.js.

Para el frontend de casi cualquier proyecto tuyo: **empeza aca, cuesta $0.**

### VPS (Virtual Private Server)
Una computadora virtual entera para vos, en un datacenter. Vos instalas y
configuras todo (el sistema, la base de datos, tu app). Precio fijo y
predecible (~USD 4-6/mes por uno chico). Ejemplos: **Hetzner** (el mejor
precio/rendimiento, lo recomendamos para Kitradep), DigitalOcean, Vultr,
Linode, AWS Lightsail (el VPS "facil" de AWS).

Es el equilibrio clasico: control total como un servidor propio, sin el costo
de uno dedicado. Ideal cuando tenes carga predecible y no queres sorpresas de
facturacion.

### Nube "cruda" / IaaS (AWS, Azure, GCP)
Los gigantes: **AWS** (Amazon), **Azure** (Microsoft), **GCP** (Google). Te
dan CIENTOS de servicios: servidores que escalan solos, bases de datos
gestionadas, CDNs, colas, funciones serverless, IA, etc. Poder casi infinito.
Contracara: **complejidad alta** y **modelo de pago por uso** que puede
descontrolarse. Es la eleccion de empresas y de apps que necesitan escalar de
verdad, no de un proyecto personal que arranca.

### PaaS (Platform as a Service)
Un punto medio comodo: subis tu codigo y ellos se encargan del servidor.
Ejemplos: **Railway**, **Render**, **Fly.io**, Heroku. Mas caros que un VPS
crudo pero te ahorran administrar el servidor. Geniales para lanzar un backend
rapido sin pelear con Linux.

### Serverless / Functions
No pagas por un servidor prendido; pagas por cada ejecucion. Tu codigo
"despierta", corre, responde y "duerme". Ideal para webhooks y tareas cortas.
Ejemplos: **Cloudflare Workers** (tu `worker-vivo/`), AWS Lambda, Supabase
Edge Functions. Muy barato para bots y APIs de bajo/medio trafico.

### BaaS (Backend as a Service)
Ya lo vimos en el cap 04: Supabase, Firebase. Te dan backend + base + auth +
storage sin administrar nada. Tu default para apps con datos.

---

## 3. LA DECISION: servidor propio/VPS vs nube (AWS/Azure)

Esto no es una decision de codigo, es de infraestructura. Aca esta el criterio
destilado:

- Un **VPS** ofrece el mejor equilibrio entre costo y control: instalas y
  configuras como si fuera tu servidor, sin el costo de uno dedicado. Es la
  opcion tipica cuando tenes **carga predecible** y queres **evitar sorpresas
  de facturacion**.
- La diferencia real con la nube aparece cuando la carga **cambia mucho**: la
  nube te deja agregar/quitar recursos segun la demanda (escalar), un VPS
  depende de una sola maquina.
- **AWS** es potentisima y escala como nada, pero su pago por uso es riesgoso
  si no monitoreas: facturas de miles de dolares por picos inesperados son
  reales y comunes. Ademas es compleja: a veces necesitas un especialista.
- Entre **AWS y Azure**: **AWS Lightsail** es mas simple y economico para un
  VPS basico; **Azure** conviene para cargas Windows o si ya estas en el
  ecosistema Microsoft (Active Directory, Microsoft 365, etc.).

### Tabla de decision rapida

| Escenario | Recomendacion |
|---|---|
| Frontend / PWA / sitio estatico | **Hosting estatico gratis** (GitHub/Cloudflare Pages) |
| App con datos, queres velocidad y cero admin | **BaaS (Supabase)** |
| Proyecto personal, MVP, trafico bajo/predecible, bot 24/7 | **VPS** (Hetzner ~USD 5/mes): barato, control, sin sorpresas |
| Backend rapido sin administrar servidor | **PaaS** (Railway/Render) |
| Webhooks, tareas cortas, bajo trafico | **Serverless** (Cloudflare Workers, Lambda) |
| Necesitas escalar rapido, picos impredecibles, servicios gestionados avanzados | **Nube (AWS/Azure/GCP)** |
| Empresa ya metida en ecosistema Microsoft | **Azure** |
| Empresa desde cero que quiere el ecosistema mas grande | **AWS** |

### Regla de oro para vos
**Empeza siempre por lo mas simple y barato (gratis o VPS). Subi a la nube
compleja SOLO cuando un problema real de escala te lo exija.** El 99% de los
proyectos personales viven felices y baratos sin tocar AWS. Nadie fue
despedido por empezar simple; mucha gente sufrio facturas por empezar
complejo "por si escala".

---

## 4. Como NO recibir una factura de terror (esto es serio)

El mayor peligro de la nube por uso (AWS/Azure/GCP) es el gasto descontrolado.
Reglas para dormir tranquilo:

- **Configura alertas de presupuesto** (billing alerts) desde el dia 1. "Si
  el gasto pasa de USD 10, avisame." Todas las nubes lo permiten. HACELO
  ANTES de nada.
- **Entende el modelo de precios** de cada servicio antes de encenderlo. Lo
  que parece gratis a veces cobra por transferencia de datos de salida
  (egress), que es el costo oculto clasico.
- **Apaga lo que no uses.** Un servidor olvidado prendido factura todo el mes.
- **Cuidado con el auto-scaling sin techo.** Si tu app escala sola sin limite
  y recibe un pico (o un ataque), la factura escala con ella. Pone limites.
- **Usa la capa gratuita (free tier)** para aprender, pero leé sus limites:
  muchos sustos vienen de pasarse del free tier sin darse cuenta.
- **Para aprender AWS/Azure, usa una cuenta separada** con limite de tarjeta
  bajo o tarjeta prepaga. Nunca tu tarjeta principal sin tope.

> En un VPS esto no pasa: pagas lo mismo todos los meses, uses mucho o poco.
> Por eso, para tranquilidad mental, el VPS es imbatible al empezar.

---

## 5. Dominios y HTTPS (los ultimos detalles)

- **Dominio**: el nombre de tu sitio (`kitradep.cl`). Se compra por ~USD
  10-15/ano en registradores como Namecheap, Cloudflare, o NIC Chile para
  `.cl`. Opcional al empezar: podes usar el subdominio gratis que te da el
  host (`tuapp.pages.dev`, `usuario.github.io/app`).
- **DNS**: el sistema que conecta tu dominio con la IP de tu servidor. Se
  configura con "registros" (un registro `A` apunta a una IP).
- **HTTPS / SSL**: el candadito de seguridad, encripta el trafico. HOY ES
  OBLIGATORIO (los navegadores marcan como "no seguro" lo que no lo tiene, y
  cosas como los webhooks de WhatsApp lo exigen). La buena noticia: es GRATIS
  y casi automatico. **Caddy** (que usa Kitradep) o Let's Encrypt sacan el
  certificado solos. Los hosting estaticos (Pages/Vercel) te lo dan sin que
  hagas nada.

---

## 6. Un flujo de despliegue tipico (para que lo veas completo)

Asi se ve publicar un proyecto full, juntando todo:

```
1. Frontend (React/PWA)  -> build -> GitHub Pages / Cloudflare Pages (gratis)
2. Base de datos + auth  -> Supabase (plan gratis o ~USD 25/mes al crecer)
3. Bot / backend 24/7    -> VPS Hetzner con Docker (~USD 5/mes) + Caddy (SSL)
4. Tareas cortas/webhooks-> Cloudflare Workers / Edge Functions (casi gratis)
5. Dominio               -> ~USD 12/ano (opcional)
6. Monitoreo             -> UptimeRobot pega a /health (gratis)
7. Backups               -> cron que sube a Backblaze B2 (centavos)
```

Costo total realista de un proyecto personal en produccion: **USD 0 a 10 al
mes.** Asi de accesible es hoy. Ese es el plan que dejamos escrito para
Kitradep, no por casualidad.

---

## 7. Docker: el concepto que hace todo esto portable

Vas a escuchar **Docker** por todos lados. Es una forma de empaquetar tu app
con TODO lo que necesita para correr (el sistema, las librerias, la version
exacta de Python, etc.) en una "caja" llamada **contenedor**. Esa caja corre
igual en tu compu, en un VPS o en la nube. Resuelve el clasico "en mi maquina
funcionaba".

No necesitas dominarlo para empezar, pero saber que existe y que sirve para
"empaquetar y desplegar sin sorpresas" te ubica. Kitradep ya trae su
`Dockerfile` y `docker-compose.yml` justamente para desplegarse limpio en
cualquier VPS con un comando (`docker compose up -d`).

---

## Hacelo vos (ejercicios)

1. Publica algo estatico gratis: sube un `index.html` simple a GitHub Pages o
   Cloudflare Pages y compartite el link a vos mismo. Tu primera cosa online.
2. Entra a la calculadora de precios de Hetzner y de AWS EC2. Compara el
   costo de un servidor chico. Sentí la diferencia de modelos (fijo vs por
   uso).
3. En tus notas, decidí (con la tabla de la seccion 3) donde alojarias: (a)
   una PWA sin backend, (b) un bot de WhatsApp 24/7, (c) un script que corre
   1 vez al dia. Justifica cada uno.
4. Investiga: "que es egress / transferencia de datos de salida y por que
   sorprende en las facturas de nube". Anotalo. Es el costo oculto #1.

---

Ya tenes todas las piezas y donde ponerlas. Ahora, el plan para armar tu
expertise de verdad: [capitulo 07: Ruta de proyectos](07-ruta-de-proyectos.md).
