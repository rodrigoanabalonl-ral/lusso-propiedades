# Lusso Propiedades — Documento del proyecto (sitio web)

> **Punto de partida** para retomar el sitio web de Lusso Propiedades: qué existe, dónde está, cómo funciona, qué decisiones se tomaron y qué falta.
> Última actualización: 13-11-2026

---

## 1. Resumen

| | |
|---|---|
| **Cliente** | Lusso Propiedades: corredora de propiedades en Chile |
| **Responsable comercial** | Mariel Cañellas, corredora de propiedades |
| **Estado** | Demo v1 publicada (sitio estático de una página) |
| **Sitio en línea** | https://rodrigoanabalonl-ral.github.io/lusso-propiedades/ |
| **Repositorio** | https://github.com/rodrigoanabalonl-ral/lusso-propiedades (público, rama `main`) |
| **Copia local** | `G:\Mi unidad\Programas\Lusso\index.html` |
| **Fuente del contenido** | Instagram [@lusso.propiedades](https://www.instagram.com/lusso.propiedades/) |

---

## 2. Datos del negocio (sacados del Instagram)

- **Rubro (bio):** Gestión de venta y arriendo · Asesoría patrimonial inmobiliaria · Posesión efectiva · Administración de inmuebles · 📍 Chile · Asesoría personalizada.
- **Teléfono / WhatsApp:** +56 9 9870 1674 *(una publicación dice 1684; usamos 1674 porque aparece en la mayoría. **Confirmar**)*.
- **Email:** solo aparece `DGI.MCGESTION@GMAIL.COM` en una publicación antigua, así que **no se puso en el sitio. Confirmar uno vigente**.
- **Identidad visual del logo:** edificios en azul marino con acento dorado, "LUSSO" en tipografía con serifa, "PROPIEDADES · BIENES RAÍCES" en dorado, ícono de llave.
- **Zonas donde opera:** Región Metropolitana (La Florida, Alto Macul, Puente Alto, Santiago Centro, Las Condes, Estación Central), Valparaíso (Los Andes, San Esteban), Ñuble (Cobquecura), Los Ríos (Valdivia, La Unión) y Los Lagos (Puerto Varas).
- **Mensaje de marca (del reel de arriendo):** *"Tú disfruta de la tranquilidad, nosotros nos ocupamos del resto."* Busca al arrendatario ideal, evalúa a los postulantes y administra (pagos de arriendo, cuentas y gestiones).

---

## 3. Stack y estructura técnica

- **Un solo archivo `index.html`**: HTML + CSS + JavaScript puro (vanilla), sin frameworks ni build.
- **Fuentes:** Google Fonts: *Cormorant Garamond* (títulos) y *Montserrat* (texto).
- **Imágenes:** **fotos de referencia de Unsplash** cargadas por URL (no son las fotos reales de las propiedades).
- **Hosting:** GitHub Pages en modo *Deploy from a branch*, rama `main`, carpeta `/ (root)`. Lleva un `.nojekyll` para que GitHub no procese el HTML.
- **Contacto:** no hay backend. El formulario arma un mensaje y abre **WhatsApp** (`wa.me/56998701674`) con el texto listo.

### Archivos del repositorio
```
index.html     → sitio completo
README.md      → descripción corta + enlace
PROYECTO.md    → este documento
.nojekyll      → desactiva Jekyll en GitHub Pages
```

### Paleta (variables CSS en `:root`)
| Variable | Color | Uso |
|---|---|---|
| `--navy` | `#14213d` | Color principal |
| `--navy-3` | `#0c1528` | Fondos oscuros, footer |
| `--gold` | `#c6a052` | Acentos, botones |
| `--gold-2` | `#e2c27f` | Dorado claro |
| `--cream` | `#f8f5ef` | Fondos de secciones claras |

### Secciones de la página (en orden)
1. **Nav fija**: logo SVG + menú; en móvil pasa a menú hamburguesa.
2. **Hero** (`#inicio`): titular, botones y **buscador** (operación / tipo / zona) que filtra el listado.
3. **Barra de cifras**: contadores animados (13 propiedades, 5 regiones, 4 servicios, 24/7).
4. **Propiedades** (`#propiedades`): grilla con filtros (*Todas / Venta / Arriendo / Terrenos*) y **modal de detalle** con botón de WhatsApp que menciona la propiedad.
5. **Servicios** (`#servicios`): las 4 líneas de la bio.
6. **Propietarios** (`#propietarios`): proceso en 4 pasos y llamado a publicar.
7. **Operaciones cerradas** (`#exito`): 4 casos vendidos o arrendados.
8. **Nosotros** (`#nosotros`): texto, valores y tarjeta con la cita de Mariel Cañellas.
9. **Contacto** (`#contacto`): datos y formulario que envía a WhatsApp.
10. **Footer** y **botón flotante de WhatsApp**.

---

## 4. Cómo editar las propiedades

Todas las propiedades están en el arreglo **`PROPIEDADES`**, dentro del `<script>` al final de `index.html`. Para agregar, quitar o cambiar un aviso **solo se edita ese arreglo**. El HTML de las tarjetas se genera solo.

```js
{ id:'chancoyan',            // único, sin espacios
  op:'venta',                // 'venta' | 'arriendo' | 'mixto' (venta o arriendo)
  tipo:'terreno',            // 'departamento' | 'casa' | 'terreno' | 'oficina'
  zona:'sur',                // 'rm' | 'sur' | 'otras'  (usado por el buscador)
  titulo:'Terreno en condominio privado',
  ubicacion:'Chancoyán Alto, Valdivia',
  precio:'$55.000.000',      // texto libre: '5.500 UF', 'Consultar', etc.
  precioNota:'conversable',  // opcional (texto chico sobre el precio)
  dorm:3, banos:2, sup:'5.000 m²',   // opcionales
  img:'fotos/chancoyan.jpg', // hoy usa U('id-unsplash'); cambiar por la foto real
  desc:'Descripción corta…',
  items:['Rol propio','Luz y agua','…'] }  // viñetas del modal
```

Las **operaciones cerradas** (sección `#exito`) están escritas directo en el HTML, no en el arreglo.

### Propiedades cargadas hoy (13)
| ID | Operación | Tipo | Ubicación | Precio |
|---|---|---|---|---|
| cayumapu | Venta | Terreno 13.000 m² | Cayumapu, Valdivia | Consultar |
| chancoyan | Venta | Terreno 5.000 m² | Chancoyán Alto, Valdivia | $55.000.000 |
| launion | Venta | Predio | La Unión, Los Ríos | $32.000.000/ha |
| altavista | Venta | Depto 3D/2B | Alto Macul, La Florida | 5.500 UF |
| altomacul2 | Venta | Depto 2D/2B | Alto Macul, La Florida | 5.100 UF |
| puentealto | Venta | Casa 3D/2B | Puente Alto | $142.000.000 |
| laflorida-arr | Arriendo | Depto 3D/2B | La Florida | $700.000 |
| valdovinos | Arriendo | Depto 1D 39 m² | Metro Carlos Valdovinos | Consultar |
| portugal564 | Venta/Arriendo | Depto 1D | Av. Portugal 564, Stgo. | 1.800 UF / $300.000 |
| myway | Venta/Arriendo | Depto 2D/2B | Av. Portugal 520, Stgo. | 3.000 UF / $500.000 |
| oficinas | Venta | 2 oficinas 44 m² | Los Militares, Las Condes | 3.500 UF |
| sanesteban | Venta | Terreno 11.719 m² | San Esteban, V Región | 2 UF/m² |
| cobquecura | Venta | Terreno | Cobquecura, Ñuble | $25.000.000 |

**Operaciones cerradas mostradas:** casa en Alto Macul (vendida), parcela en Río Chico Alto, Puerto Varas (vendida), casa de campo en Los Andes (vendida) y depto en Las Condes, Metro Manquehue (arrendado).

---

## 5. Cómo publicar cambios

1. Editar `index.html` (en local o directo en GitHub con el ícono del lápiz).
2. Subirlo a la rama `main` (commit + push, o *Commit changes* en la web).
3. GitHub Pages republica solo en **1 a 2 minutos**. Si no se ve el cambio, recargar con `Ctrl+F5`.

Para probar en local basta con abrir `index.html` con doble clic. Las fotos y fuentes necesitan internet.

> La app de Claude ya está instalada en el repositorio, así que Claude puede hacer commit y push directamente.

---

## 6. Decisiones tomadas

- **Sitio de una sola página y archivo único**: rápido de revisar, sin dependencias y gratis en GitHub Pages.
- **Contacto por WhatsApp en vez de email/backend**: es el canal que usa el cliente en Instagram y no requiere servidor.
- **Fotos de Unsplash como referencia**: las de Instagram vienen de URLs firmadas que caducan, así que no sirven para enlazarlas. El footer avisa *"Fotografías referenciales"*.
- **Repo público**: es lo que exige GitHub Pages en el plan gratuito.
- **Logo recreado en SVG** (símbolo de edificios + texto) en vez del logo original, que no se tenía en buena resolución.

---

## 7. Pendientes / próximos pasos

### Antes de mostrar al cliente
- [ ] **Fotos reales** de cada propiedad: dejarlas en `fotos/` y cambiar `img` en el arreglo.
- [ ] **Logo oficial** en alta resolución (PNG transparente o SVG) para reemplazar el SVG recreado.
- [ ] **Confirmar teléfono** (1674 vs 1684) y un **email** de contacto vigente.
- [ ] **Validar con Mariel qué avisos siguen vigentes.** Varios son de 2024 (San Esteban, oficinas Las Condes, Av. Portugal).
- [ ] Revisar los textos de *Nosotros* y *Servicios* (los redacté yo a partir de la bio y deben aprobarse).
- [ ] Foto de Mariel para la tarjeta de *Nosotros* (hoy muestra las iniciales "MC").

### Mejoras siguientes
- [ ] **Dominio propio** (ej. `lussopropiedades.cl`) apuntado a GitHub Pages: *Settings → Pages → Custom domain*.
- [ ] **SEO**: etiquetas Open Graph (vista previa al compartir por WhatsApp), favicon, `sitemap.xml` y Google Search Console.
- [ ] **Analítica** (Google Analytics o similar) y Meta Pixel si van a hacer publicidad.
- [ ] Página individual por propiedad (URL propia para compartir cada aviso).
- [ ] Galería de varias fotos por propiedad en el modal.
- [ ] Mover las propiedades a un archivo `propiedades.json` o a un panel simple (Google Sheets / Supabase) para que el cliente las actualice sin tocar código.
- [ ] Formulario con respaldo por email (Formspree, Web3Forms o similar) además de WhatsApp.
- [ ] Mapa con la ubicación aproximada de cada propiedad.

---

## 8. Cómo retomar con Claude

Pegar algo así al empezar una conversación nueva:

> *"Estoy retomando el sitio de Lusso Propiedades. El repo es `rodrigoanabalonl-ral/lusso-propiedades` y está publicado en GitHub Pages. Lee `PROYECTO.md` y luego ayúdame con: …"*
