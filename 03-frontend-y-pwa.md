# 03 - Frontend y PWA (lo que ve el usuario)

> Objetivo: entender la capa que la gente toca -el navegador, el celu- y como
> se construye una app moderna e instalable (PWA).

---

## 1. Que es el frontend

El **frontend** es todo lo que el usuario ve y toca: la pantalla, los botones,
los colores, los formularios, las animaciones. Vive y corre en el dispositivo
del usuario (su navegador o su celu).

Se para sobre tres tecnologias, y TODA app web del mundo usa estas tres:

- **HTML**: la ESTRUCTURA. El esqueleto: "aca hay un titulo, aca un boton,
  aca una imagen." Como los ladrillos de una casa.
- **CSS**: el ESTILO. Colores, tamanos, espaciados, tipografia, animaciones.
  La pintura, la decoracion, el diseno.
- **JavaScript (JS)**: el COMPORTAMIENTO. "Cuando aprietan este boton, pasa
  esto." La electricidad y la plomeria: hace que la casa funcione.

Analogia completa: HTML es el cuerpo, CSS es la ropa y el peinado, JS es el
sistema nervioso que hace que reaccione.

---

## 2. Entendé esto: HTML/CSS/JS son la base de TODO

Aunque uses frameworks modernos (React, etc.), por debajo SIEMPRE terminan
siendo HTML, CSS y JS, porque es lo unico que el navegador entiende. Por eso
vale la pena entender lo basico de los tres aunque despues uses herramientas
que te lo simplifican. No hace falta ser experto; hace falta saber que hace
cada uno.

Dato util: tus reportes "flat HTML" (los de un solo archivo con Tailwind por
CDN y Chart.js) son exactamente esto en su forma mas pura: HTML + CSS + JS en
un archivo. Es la forma mas simple de construir algo que se ve en el navegador.

---

## 3. TypeScript: JavaScript con casco

**TypeScript (TS)** es JavaScript con "tipos": le decis a las variables que
tipo de dato son (texto, numero, etc.) y el editor te avisa de errores ANTES
de correr el codigo. Atrapa bugs tontos temprano. Casi todo proyecto serio
moderno usa TS (tus proyectos MALP y Mundial lo usan). Vale 100% la pena.

Analogia: JS es manejar sin cinturon; TS es con cinturon. Igual de rapido,
pero te salva cuando hay un choque.

---

## 4. Frameworks de frontend: por que existen React y compania

Construir apps grandes con HTML/CSS/JS "a mano" se vuelve un caos: mucho
codigo repetido, dificil de mantener. Los **frameworks/librerias** resuelven
esto dandote piezas reutilizables (**componentes**) y manejando la
complejidad por vos.

- **React**: el mas popular del mundo. Todo se arma con **componentes**
  (piezas de UI reutilizables: un boton, una tarjeta, una pantalla). Es lo
  que usan tus proyectos. Aprender React es la apuesta mas segura.
- **Vue** y **Svelte**: alternativas excelentes, algunos las encuentran mas
  faciles. Pero por ecosistema y trabajo, React lidera.
- **Next.js**: React "con esteroides" (agrega backend, rutas, optimizaciones).
  Muy usado en produccion. Lo veras cuando crezcas.

**Que es un componente (el concepto clave de React):** una pieza de interfaz
que encapsula su estructura + estilo + comportamiento y se puede reusar. En
MALP, `Monstera.tsx` es un componente: la planta que crece, la usas donde
quieras. Piezas de LEGO que armas para hacer pantallas.

---

## 5. Vite, npm/pnpm y el "build"

Cuando trabajas con React necesitas herramientas de apoyo:

- **Node.js**: permite correr JavaScript fuera del navegador (en tu compu),
  necesario para las herramientas de desarrollo.
- **npm / pnpm**: gestores de paquetes. Instalan las librerias que tu proyecto
  usa (React, etc.) y las guardan en `node_modules`. `pnpm` es una version mas
  rapida y eficiente de npm.
- **Vite**: la herramienta que levanta tu proyecto en modo desarrollo
  (`pnpm dev` -> lo ves en tu navegador al instante mientras editas) y que
  hace el **build**: empaqueta todo tu codigo React/TS en HTML/CSS/JS puro y
  optimizado, listo para publicar. Tus proyectos usan Vite.

Flujo tipico:
```bash
pnpm install   # instala las librerias (crea node_modules)
pnpm dev       # desarrollo: ves los cambios en vivo en localhost
pnpm build     # produccion: genera la version optimizada para publicar
```

---

## 6. Tailwind CSS: estilar rapido y consistente

**Tailwind** es una forma de escribir CSS con "clases utilitarias" directo en
el HTML: `class="bg-green-500 text-white p-4 rounded"` = fondo verde, texto
blanco, padding, esquinas redondeadas. En vez de escribir CSS aparte, componés
estilos con clasecitas. Es rapidisimo una vez que le agarras la mano, y
mantiene todo consistente. Tus proyectos lo usan.

Truco pro (que aplicamos en MALP): define tus colores de marca UNA vez en
`tailwind.config.js` con nombres (`malp.verde`) y usa esos nombres en todo el
proyecto. Cambias la marca entera tocando un solo archivo. Eso es DRY aplicado
al diseno.

---

## 7. Que es una PWA (Progressive Web App)

Una **PWA** es una app web que se comporta como una app nativa: se puede
**instalar** en el celu (aparece con su icono en la pantalla), funciona
**offline** (sin internet) hasta cierto punto, y puede mandar notificaciones.
Pero por dentro es una web normal.

La gran ventaja: **escribis una sola vez y sirve para todo** (Android, iPhone,
compu). No necesitas hacer una app separada para cada tienda (App Store, Play
Store) ni pagar sus comisiones. Para proyectos como MALP o Kitradep, la PWA es
la opcion mas inteligente: maximo alcance, minimo costo.

Que la hace "instalable/offline", tecnicamente:
- **Manifest** (`manifest.json`): un archivo que le dice al celu el nombre,
  icono y colores de la app, para poder instalarla.
- **Service Worker**: un script que corre en segundo plano y puede guardar
  archivos en cache para que la app abra sin internet.

La buena noticia: no tenes que escribir esto a mano. `vite-plugin-pwa` (que
tus proyectos ya usan) lo genera casi solo.

Limitacion honesta: en iPhone las PWAs tienen algunas restricciones (las
notificaciones push, por ejemplo, funcionan pero con limites). Para el 95% de
los casos, alcanza y sobra.

---

## 8. PWA vs app nativa vs web comun (cuando usar cada una)

| Queres... | Elegí |
|---|---|
| Algo que se vea en el navegador, sin instalar | **Web comun** (una URL) |
| Que se instale, funcione offline, multiplataforma, gratis | **PWA** |
| Acceso profundo al hardware del celu (camara avanzada, sensores, maximo rendimiento de juego) o estar SI o SI en las tiendas | **App nativa** (React Native / Flutter / Swift / Kotlin) |

Regla practica para vos: **empeza siempre con PWA.** Solo salta a nativa si
chocas con un limite real que la PWA no cubre. Nativa es mas cara y compleja
(dos plataformas, revisiones de tienda, etc.).

---

## 9. Accesibilidad y responsive (lo que separa amateur de pro)

- **Responsive**: que se vea bien en cualquier tamano de pantalla (celu,
  tablet, compu). Se disena **mobile-first**: primero para el celu, despues
  se agranda. La mayoria de tus usuarios entran por el telefono.
- **Accesibilidad (a11y)**: que la puedan usar personas con discapacidad
  (lectores de pantalla para ciegos, buen contraste de colores, navegable con
  teclado). No es opcional ni "extra": es parte de hacerlo bien. Pedile a la
  IA: "hace este componente accesible (contraste, etiquetas aria, navegable
  por teclado)".

---

## Hacelo vos (ejercicios)

1. Crea un archivo `hola.html`, escribi un titulo y un boton en HTML, pintalo
   con un poco de CSS, y con JS hace que el boton muestre una alerta al
   clickearlo. Todo en un archivo. Abrilo con doble click. Acabas de entender
   los 3 pilares.
2. Pedile a la IA que te explique la diferencia entre HTML, CSS y JS con una
   analogia de un auto. Compara con la de la casa que usamos aca.
3. Abri MALP (tu proyecto) y encontra: el `tailwind.config.js` (los colores),
   un componente en `src/components/`, y una pantalla en `src/screens/`.
   Reconocé las piezas de las que hablamos.
4. Instala un icono de tu PWA MALP en tu celu (entra a la URL de GitHub Pages
   y "agregar a pantalla de inicio"). Vive la magia de una PWA.

---

Ya sabes que ve el usuario. Ahora, el cerebro detras:
[capitulo 04: Backend, datos y APIs](04-backend-datos-apis.md).
