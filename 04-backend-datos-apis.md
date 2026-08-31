# 04 - Backend, datos y APIs (el cerebro)

> Objetivo: entender lo que pasa "del lado del servidor": la logica, la base
> de datos, y como el frontend habla con todo eso.

---

## 1. Que es el backend (y por que existe)

El **backend** es la parte de la app que el usuario NO ve: corre en un
servidor (una computadora prendida en algun lado), guarda los datos, aplica
las reglas del negocio, y protege lo importante.

Por que no hacer todo en el frontend? Porque el frontend vive en el
dispositivo del usuario y **no es confiable ni seguro**. Ejemplos:

- Si los precios o las reglas de puntos vivieran solo en el frontend, un
  usuario listo podria cambiarlos desde su navegador y darse 1 millon de
  puntos. El backend, que el no controla, es quien decide de verdad.
- Las claves secretas (de la base de datos, de servicios pagos) NO pueden
  estar en el frontend porque cualquiera las veria. Viven en el backend.

Regla mental: **el frontend propone, el backend dispone.** Todo lo que
importa (dinero, seguridad, verdad) se valida en el backend.

---

## 2. Que es una API (el concepto que conecta todo)

Una **API** (Application Programming Interface) es la forma en que dos
programas se hablan. En la web, es como el frontend le pide cosas al backend.

Analogia del restaurante (la mejor que hay):
- Vos (frontend) sos el cliente en la mesa.
- La **carta** es la API: te dice que podes pedir.
- El **mozo** lleva tu pedido a la cocina y te trae el plato.
- La **cocina** (backend + base de datos) prepara todo, pero vos no entras.

Vos no gritas a la cocina; usas al mozo con un pedido en el formato que
espera ("una pizza margarita"). Igual el frontend: le pide al backend "dame
las plantas del usuario 5" y recibe los datos, sin saber ni importarle como
la cocina los busco.

Terminos que vas a escuchar:
- **Endpoint**: cada "cosa que se puede pedir" de una API. Una URL como
  `/api/plantas` o `/api/usuarios/5`.
- **Request** (pedido) y **Response** (respuesta).
- **Metodos HTTP**: el TIPO de pedido. `GET` (dame datos), `POST` (crea algo),
  `PUT/PATCH` (actualiza), `DELETE` (borra). Son los verbos del mozo.
- **JSON**: el formato de texto en que viajan los datos (listas y pares
  clave-valor). Es el "idioma" universal de las APIs.
- **REST**: el estilo mas comun de disenar APIs (endpoints + metodos HTTP).

---

## 3. Bases de datos: donde vive la informacion para siempre

Una **base de datos** (DB) es donde se guardan los datos de forma permanente:
usuarios, plantas, puntos, mensajes. Si apagas y prendes el servidor, los
datos siguen ahi (a diferencia de la memoria, que se borra).

Dos grandes familias:

### a) Relacionales / SQL (las mas comunes)
Guardan datos en **tablas** con filas y columnas, como planillas de Excel
conectadas entre si. Ejemplos: **PostgreSQL** (el rey open source), MySQL,
SQLite. Se consultan con el lenguaje **SQL** ("dame todos los usuarios con
mas de 500 puntos"). Ideales cuando tus datos tienen estructura y relaciones
claras (un usuario TIENE muchas plantas, una planta TIENE muchos cuidados).
Es lo que usan tus proyectos (Supabase es Postgres; Kitradep usa SQLite).

### b) No relacionales / NoSQL
Guardan datos con estructura mas flexible (documentos tipo JSON). Ejemplos:
MongoDB, Firestore. Utiles cuando los datos no tienen forma fija. Para la
mayoria de tus proyectos, SQL es la eleccion correcta y mas solida.

**SQLite vs Postgres, cuando cada uno:**
- **SQLite**: una base de datos que es UN solo archivo. Cero configuracion,
  perfecta para apps chicas, prototipos, o un bot (como Kitradep). Su limite:
  no aguanta bien mucha escritura simultanea de muchos usuarios.
- **PostgreSQL**: una base "de verdad" que corre como servicio, aguanta muchos
  usuarios a la vez. Para cuando creces. Supabase te da Postgres sin que
  tengas que administrarlo.

---

## 4. El modelo de datos: pensar antes de construir

Antes de programar, se disena el **modelo de datos**: que tablas hay y como se
relacionan. Es el plano de la casa. En MALP lo hicimos en
`docs/04-modelo-de-datos.md` (10 tablas). Ejemplo simple:

```
usuarios      (id, nombre, email)
plantas       (id, usuario_id, apodo, especie, foto)   <- usuario_id conecta
cuidados      (id, planta_id, tipo, fecha)             <- planta_id conecta
```

La clave: las tablas se conectan por **ids** (una planta "pertenece a" un
usuario via `usuario_id`). Esto se llama **relaciones**. Disenar bien esto al
principio te ahorra dolores enormes despues. Pedile a la IA que te ayude:
"diseña el modelo de datos para una app de X, con las tablas y relaciones".

---

## 5. Python: tu navaja suiza para backend, bots y datos

**Python** es un lenguaje de programacion famoso por ser legible y facil de
aprender ("lee casi como ingles"). Es LA eleccion para:

- **Backend** (con frameworks como FastAPI o Django).
- **Automatizaciones y scripts** (capitulo 05).
- **Datos, analisis, IA/machine learning** (es el idioma dominante de la IA).

Por que Python y no JS para el backend? Podes usar cualquiera. JS/TS
(con Node) te deja usar UN lenguaje en front y back. Python brilla en datos,
IA y automatizacion, y es mas amable para aprender. Muchos usan JS en el front
y Python en el back sin problema. Para vos: **aprende Python si vas a tocar
datos, bots o IA; es una inversion segura.**

Sabor de Python (mira que legible es):
```python
plantas = ["Monstera", "Potos", "Cactus"]
for planta in plantas:
    print(f"Cuidar mi {planta} hoy")
```

Herramientas del mundo Python que veras:
- **pip** / **uv**: instalan librerias (uv es la version moderna y rapida).
- **Entorno virtual** (`venv`): una "burbuja" aislada de librerias por
  proyecto, para que no se pisen entre si. SIEMPRE se usa uno por proyecto.
- **FastAPI**: framework moderno y rapidisimo para hacer APIs/backend en
  Python. Facil de aprender, muy usado. Excelente primera opcion.
- **requirements.txt**: la lista de librerias que tu proyecto necesita.

---

## 6. BaaS: Supabase y Firebase (el atajo inteligente)

Aca esta la joya para vos. Hacer un backend "a mano" (servidor + base de datos
+ login + seguridad) es mucho trabajo. Un **BaaS** (Backend as a Service) te
da todo eso ya hecho, listo para usar desde tu frontend:

- **Supabase** (el que elegimos para MALP): te da una base de datos Postgres,
  sistema de login (**Auth**), almacenamiento de archivos (**Storage**, para
  fotos), y una API automatica sobre tus tablas. Open source, generoso plan
  gratis. Ideal para tus proyectos.
- **Firebase** (de Google): similar, muy popular, base NoSQL. Tambien
  excelente.

Por que es un atajo genial: para MALP, en vez de programar un backend entero,
creas las tablas en Supabase y tu frontend React les habla casi directo. Meses
de trabajo -> dias.

**Concepto de seguridad clave en Supabase: RLS (Row Level Security).** Como el
frontend habla casi directo con la base, necesitas reglas que digan "cada
usuario solo puede ver/editar SUS filas". Sin RLS bien puesto, un usuario
podria leer datos de otro. Es EL punto de seguridad a cuidar con un BaaS.
Y las operaciones sensibles (acreditar puntos, aprobar reclamos) se hacen por
**Edge Functions / RPC** (mini-backend en Supabase), no confiando en el
cliente. Esto esta en las notas de MALP.

---

## 7. Autenticacion vs autorizacion (no los confundas)

- **Autenticacion** (authn): verificar QUIEN sos. El login. "Sos Felipe?
  Contrasena correcta, adelante."
- **Autorizacion** (authz): verificar QUE podes hacer. "Felipe es admin?
  Entonces puede aprobar reclamos. Camila no, es clienta."

Un BaaS como Supabase te da la autenticacion casi gratis. La autorizacion
(roles: cliente vs admin) la defines vos con RLS y logica. En MALP, el "rol
admin" que valida misiones es autorizacion.

---

## 8. Como decidir tu arquitectura de backend

| Situacion | Recomendacion |
|---|---|
| App chica/mediana, queres velocidad, no queres administrar servidores | **BaaS (Supabase)** - tu default |
| Necesitas logica de servidor muy custom o pesada | **Backend propio** (FastAPI en Python o Node) |
| Un bot o automatizacion simple con algo de datos | **Python + SQLite** (como Kitradep) |
| Tareas puntuales que corren y mueren (sin servidor prendido siempre) | **Serverless / Functions** (ver cap 06) |

Regla de oro: **no construyas mas backend del que necesitas.** Empeza con un
BaaS. Solo hace backend propio cuando choques con un limite real.

---

## Hacelo vos (ejercicios)

1. Explica con tus palabras, en `mis-notas.md`, la analogia del restaurante
   para una API. Si podes explicarla, la entendiste.
2. Abri Supabase (crea una cuenta gratis), crea un proyecto y una tabla
   `plantas` con unas columnas. Mira como te da una API automatica. Magia.
3. Escribi tu primer script Python: una lista de tus plantas y un `for` que
   imprima "regar {planta}". Correlo. Bienvenido a Python.
4. Diseña en papel el modelo de datos (tablas + relaciones) de una app de
   lista de tareas: usuarios, tareas. Que columnas? Como se conectan?
5. Investiga (pregunta a la IA): "que es RLS en Supabase y por que es
   importante para la seguridad?" Resumilo en tus notas.

---

Ya entendes front y back. Ahora, que la maquina trabaje sola:
[capitulo 05: Bots y automatizaciones](05-bots-y-automatizaciones.md).
