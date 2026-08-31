# 09 - Glosario (todos los terminos raros en cristiano)

> Diccionario de bolsillo. Cuando un capitulo (o la IA) use una palabra que no
> conoces, busca aca. En orden alfabetico.

---

**Agente (IA)**: un LLM al que le diste herramientas y un objetivo, y que
actua en un bucle (leer, razonar, hacer, revisar) hasta cumplirlo. Claude Code
y Kira son agentes.

**Alucinacion**: cuando un LLM inventa informacion falsa con total seguridad.
Por eso siempre se verifican los datos importantes.

**API**: la forma en que dos programas se hablan. En la web, como el frontend
le pide datos al backend. (Analogia: la carta y el mozo de un restaurante.)

**Autenticacion (authn)**: verificar QUIEN sos (el login).

**Autorizacion (authz)**: verificar QUE podes hacer (permisos, roles).

**Backend**: la parte de la app que el usuario no ve; corre en un servidor,
guarda datos, aplica reglas y protege lo importante.

**BaaS (Backend as a Service)**: servicio que te da backend + base de datos +
login + storage ya hechos. Ej: Supabase, Firebase.

**Base de datos (DB)**: donde se guardan los datos de forma permanente. SQL
(tablas, ej. Postgres) o NoSQL (documentos, ej. MongoDB).

**Build**: el proceso de empaquetar y optimizar tu codigo (React/TS) en
HTML/CSS/JS puro listo para publicar.

**Cache**: guardar algo temporalmente para no tener que buscarlo de nuevo (mas
rapido). Un service worker usa cache para que una PWA abra offline.

**CDN (Content Delivery Network)**: red de servidores repartidos por el mundo
que sirve tus archivos desde el mas cercano al usuario. Mas velocidad.

**Cloud / Nube**: servidores de terceros (AWS, Azure, GCP) que alquilas por
uso. Poder y escala enormes, con riesgo de costos si no controlas.

**Commit**: un checkpoint guardado en git, una "foto" de tu proyecto a la que
podes volver.

**Componente**: una pieza reutilizable de interfaz en frameworks como React
(un boton, una tarjeta, una pantalla). LEGO de UI.

**Contenedor**: una "caja" (Docker) que empaqueta tu app con todo lo que
necesita para correr igual en cualquier lado.

**Contexto (ventana de)**: todo lo que un LLM puede "tener en mente" de una
vez (tu pregunta + historial + documentos). Se mide en tokens.

**Cron**: un programador de tareas que corre algo cada cierto tiempo (cada
dia, cada hora). En Windows, el "Programador de tareas".

**CSS**: el lenguaje del ESTILO de una pagina web (colores, tamanos, diseno).

**Deploy / Despliegue**: publicar tu app para que otros la usen.

**DNS**: el sistema que traduce un nombre de dominio (kitradep.cl) a la IP de
un servidor.

**Docker**: herramienta para empaquetar apps en contenedores portables.
Resuelve el "en mi maquina funcionaba".

**Dominio**: el nombre de tu sitio (ej. kitradep.cl). Se compra por ~USD
12/ano.

**DRY (Don't Repeat Yourself)**: principio: no repitas logica ni datos;
hacelo una vez y reusalo.

**Embedding**: convertir un texto en numeros (vector) que representan su
significado. Base de la busqueda semantica y RAG.

**Endpoint**: cada "cosa que se puede pedir" de una API; una URL como
/api/plantas.

**Entorno virtual (venv)**: burbuja aislada de librerias por proyecto Python,
para que no se pisen entre si.

**Fine-tuning**: reentrenar un poco un LLM con tus ejemplos para cambiar su
estilo/comportamiento. Caro y raro; casi siempre no lo necesitas.

**Framework**: un conjunto de herramientas y estructura que te facilita
construir (ej. React para frontend, FastAPI para backend).

**Frontend**: todo lo que el usuario ve y toca; corre en su navegador o celu.

**Git**: sistema para versionar tu codigo; te deja guardar checkpoints y
volver atras.

**GitHub**: donde viven tus repos git en la nube. Respaldo + portafolio.

**Guardrails**: reglas de seguridad que un bot/IA nunca cruza (ej. no
diagnosticar, derivar urgencias). Suelen ser filtros deterministas.

**HTML**: el lenguaje de la ESTRUCTURA de una pagina web (el esqueleto).

**HTTP / HTTPS**: el protocolo con que viaja la info en la web. HTTPS es la
version segura (encriptada, el candadito). Hoy es obligatorio.

**IaaS / PaaS / SaaS / BaaS**: niveles de "cuanto te dan hecho" en la nube:
Infraestructura / Plataforma / Software / Backend como servicio.

**IP**: la direccion numerica de un servidor en internet.

**JSON**: formato de texto para intercambiar datos (listas y pares
clave-valor). El "idioma" de las APIs.

**JavaScript (JS)**: el lenguaje del COMPORTAMIENTO en la web; hace que las
paginas reaccionen. Tambien corre en servidores con Node.

**KISS (Keep It Simple)**: principio: la solucion mas simple que funcione,
gana.

**Libreria**: codigo ya hecho por otros que usas en tu proyecto (ej. React,
requests).

**LLM (Large Language Model)**: modelo de IA que predice texto; el motor
detras de Claude, GPT, Gemini.

**localStorage**: almacenamiento simple dentro del navegador; guarda datos en
el dispositivo del usuario (sin backend).

**MCP (Model Context Protocol)**: estandar para conectarle herramientas y
datos a los agentes de IA de forma ordenada.

**Modelo de datos**: el plano de que tablas hay y como se relacionan en tu
base de datos.

**Node.js**: permite correr JavaScript fuera del navegador (en tu compu/
servidor). Necesario para las herramientas de frontend.

**npm / pnpm**: gestores de paquetes de JavaScript; instalan librerias.

**NoSQL**: bases de datos no relacionales (documentos flexibles), ej. MongoDB.

**Parametros**: las "perillas" internas de un LLM que se ajustan al entrenar
(billones de ellas).

**PaaS (Platform as a Service)**: subis tu codigo y ellos manejan el
servidor. Ej: Railway, Render.

**pip / uv**: instaladores de librerias de Python (uv es el moderno y rapido).

**Prompt**: lo que le escribis a una IA.

**Prompt injection**: ataque donde un usuario mete texto para secuestrar las
instrucciones de un LLM. Se mitiga con guardrails.

**PWA (Progressive Web App)**: app web instalable que funciona offline y se
comporta como nativa, pero es una web. Una sola para todas las plataformas.

**Python**: lenguaje simple y potente, rey del backend, automatizacion, datos
e IA.

**RAG (Retrieval-Augmented Generation)**: darle a un LLM tus documentos
buscando los fragmentos relevantes y pegandolos al prompt. Para que "sepa" de
lo tuyo sin reentrenarlo.

**React**: la libreria de frontend mas popular; todo se arma con componentes.

**Repositorio (repo)**: la carpeta de tu proyecto versionada con git.

**Request / Response**: pedido y respuesta entre frontend y backend (o
cualquier API).

**Responsive**: diseno que se ve bien en cualquier tamano de pantalla.

**REST**: el estilo mas comun de disenar APIs (endpoints + metodos HTTP).

**RLS (Row Level Security)**: reglas en la base de datos que aseguran que cada
usuario solo ve/edita SUS filas. Clave con Supabase.

**Runtime**: el programa que ejecuta tu codigo (Node para JS, el interprete
para Python).

**Scraping**: extraer datos de paginas web con un programa. Con cuidado legal
y etico.

**Serverless / Functions**: tu codigo corre solo cuando se lo llama y no pagas
por tenerlo prendido. Ideal para webhooks. Ej: Cloudflare Workers, AWS Lambda.

**Service Worker**: script que corre en segundo plano en el navegador; permite
offline y notificaciones en una PWA.

**SQL**: lenguaje para consultar bases de datos relacionales.

**SQLite**: base de datos que es un solo archivo; cero configuracion, ideal
para apps chicas y bots.

**SSL / TLS**: la tecnologia que encripta el trafico (el "S" de HTTPS).

**Supabase**: BaaS open source: Postgres + Auth + Storage + API automatica.

**System prompt**: instrucciones de fondo que definen el comportamiento de un
LLM en toda la conversacion.

**Tailwind CSS**: forma de escribir estilos con clases utilitarias directo en
el HTML. Rapido y consistente.

**Temperatura**: dial que controla cuan creativo/aleatorio es un LLM. Baja =
preciso; alta = creativo.

**Token**: pedacito de palabra que los LLMs procesan. Se paga y se mide en
tokens.

**Tool use / Function calling**: mecanismo por el cual un LLM pide usar una
herramienta externa.

**TypeScript (TS)**: JavaScript con tipos; atrapa errores antes de correr.

**Vite**: herramienta que levanta tu proyecto React en desarrollo y hace el
build para produccion.

**VPS (Virtual Private Server)**: una computadora virtual entera para vos, con
precio fijo. El equilibrio control/costo para empezar.

**Webhook**: una URL que recibe un aviso cuando pasa un evento (ej. WhatsApp
te avisa cuando alguien escribe). Trigger de los bots.

**YAGNI (You Aren't Gonna Need It)**: principio: no construyas cosas "por si
acaso"; solo lo que necesitas hoy.

---

Y con esto cerramos el curso. Volve a este glosario siempre que lo necesites,
y agregale los terminos nuevos que vayas encontrando. Un glosario que crece es
senal de que vos crecas.

Suerte, jefe. El resto es construir. -- Kira
