# Design Reverse Engineering Guide

Cómo extraer el sistema de diseño de cualquier sitio web desde el navegador y generar un `DESIGN.md` compatible con este repositorio.

## Workflow en 9 pasos

### 1. Abrir el sitio en Chrome + tomar referencia visual

```bash
# Tomar screenshot full-page como referencia visual
```

En DevTools: inspeccionar estructura general, identificar secciones clave (hero, nav, cards, footer).

### 2. Extraer CSS Custom Properties (Design Tokens)

En la consola del navegador:

```js
const s = getComputedStyle(document.documentElement);
const vars = [...s].filter(k => k.startsWith('--'));
vars.forEach(k => console.log(k, s.getPropertyValue(k).trim()));
```

Buscar prefijos del design system del sitio (`--color`, `--font`, `--spacing`, `--uds`, `--ionos`, `--chakra`, `--mantine`, etc.). Si el sitio usa Tailwind sin tokens semánticos, pasar al paso 3.

### 3. Extraer paleta de colores real

```js
const all = document.querySelectorAll('*');
const colors = {text: new Set(), bg: new Set(), border: new Set()};
all.forEach(el => {
  const c = getComputedStyle(el);
  ['color','backgroundColor','borderColor'].forEach(p => {
    const v = c[p];
    if (!v || v === 'rgba(0,0,0,0)' || v === 'transparent') return;
    const m = v.match(/rgb\((\d+),\s*(\d+),\s*(\d+)\)/);
    if (m) {
      const hex = '#' + [m[1],m[2],m[3]].map(x => parseInt(x).toString(16).padStart(2,'0')).join('');
      if (p === 'color') colors.text.add(hex);
      else if (p === 'backgroundColor') colors.bg.add(hex);
      else colors.border.add(hex);
    }
  });
});
console.log('textColors:', [...colors.text]);
console.log('bgColors:', [...colors.bg]);
console.log('borderColors:', [...colors.border]);
```

Mapear los colores extraídos a nombres semánticos del frontmatter:
- `primary` → color dominante de CTAs
- `brand-dark` → fondo del hero/nav/footer
- `ink` → color de texto body
- `canvas` → fondo blanco/default
- `hairline` → color de bordes
- `accent-*` → colores de acento secundarios

### 4. Extraer la escala tipográfica

```js
const all = document.querySelectorAll('*');
const scale = {};
all.forEach(el => {
  const c = getComputedStyle(el);
  const fs = parseFloat(c.fontSize);
  if (!fs) return;
  const key = Math.round(fs) + 'px';
  if (!scale[key]) scale[key] = {family: c.fontFamily, weight: c.fontWeight, lh: c.lineHeight, ls: c.letterSpacing, count: 0};
  scale[key].count++;
});
const sorted = Object.entries(scale)
  .map(([k,v]) => ({size:k, ...v}))
  .sort((a,b) => parseFloat(b.size) - parseFloat(a.size));
console.table(sorted);
```

Mapear los tamaños a nombres semánticos:
- `display-xl` → el más grande (hero headings)
- `display-lg/md` → section headings grandes
- `heading-lg/md/sm` → títulos de sección/card
- `subhead` → subtítulos
- `body-lg` / `body` / `body-sm` → texto de párrafo
- `caption` / `code` → texto pequeño/técnico

### 5. Extraer headings reales (con sample text)

```js
const headings = {};
document.querySelectorAll('h1,h2,h3,h4,h5,h6').forEach(el => {
  const c = getComputedStyle(el);
  const tag = el.tagName.toLowerCase();
  if (!headings[tag]) headings[tag] = {size: c.fontSize, weight: c.fontWeight, family: c.fontFamily, lh: c.lineHeight, sample: el.textContent.trim().slice(0, 50)};
});
console.table(headings);
```

### 6. Extraer sombras y border-radius

```js
const shadows = new Set(), radii = new Set();
document.querySelectorAll('*').forEach(el => {
  const c = getComputedStyle(el);
  const bs = c.boxShadow;
  if (bs && bs !== 'none') shadows.add(bs);
  const br = c.borderRadius;
  if (br && br !== '0px') radii.add(br);
});
console.log('shadows:', [...shadows]);
console.log('radii:', [...radii].sort());
```

### 7. Extraer fuentes web (@font-face)

En la pestaña **Network** de DevTools, filtrar por `font` o `woff2`. O desde consola:

```js
const fonts = [];
for (const sheet of document.styleSheets) {
  try {
    for (const rule of sheet.cssRules) {
      if (rule.cssText.includes('@font-face')) fonts.push(rule.cssText);
    }
  } catch(e) {}
}
console.log(fonts.join('\n\n'));
```

### 8. Extraer componentes clave

Para cada tipo de componente (botón primario, nav link, card, input, footer):

```js
const btn = document.querySelector('button'); // o un selector más específico
const c = getComputedStyle(btn);
console.log({
  bg: c.backgroundColor, color: c.color, radius: c.borderRadius,
  padding: c.padding, font: c.fontSize, weight: c.fontWeight,
  family: c.fontFamily, shadow: c.boxShadow
});
```

Prestar atención a:
- **Botones**: bg, color, radius, padding, hover (simular en DevTools)
- **Cards**: bg, radius, shadow, padding
- **Nav**: bg, color de links, padding, gap
- **Footer**: bg, color, columnas
- **Forms**: input radius, border, focus state

### 9. Redactar el DESIGN.md

Seguir la estructura establecida:

```yaml
---
version: alpha
name: brand-design-analysis
description: (párrafo de 2-3 oraciones que captura la esencia visual)
colors:
  primary: "#..."
  ink: "#..."
  canvas: "#..."
  ...
typography:
  display-xl: {fontFamily, fontSize, fontWeight, lineHeight, letterSpacing}
  ...
shadows:
  card: "..."
  elevated: "..."
rounded:
  pill: ...
  card: ...
  button: ...
---
```

Secciones narrativas requeridas:
1. **Overview** — descripción general de la identidad visual
2. **Colors** — explicación del uso del color
3. **Typography** — jerarquía y familia tipográfica
4. **Layout** — grillas, contenedores, max-widths
5. **Elevation & Depth** — sistema de sombras
6. **Shapes** — escala de border-radius
7. **Components** — anatomía de componentes clave
8. **Do's and Don'ts** — reglas del sistema
9. **Responsive Behavior** — breakpoints y adaptaciones
10. **Known Gaps** — qué no se capturó

## Script todo-en-uno

Copiar y pegar en la consola del navegador para extraer todo en un solo paso:

```js
(function() {
  const r = document.documentElement;
  const s = getComputedStyle(r);
  const vars = [...s].filter(k => k.startsWith('--'));
  const out = {cssVars:{}, typeScale:[], colors:{text:[], bg:[], border:[]}, shadows:[], radii:[], headings:{}};

  vars.forEach(k => out.cssVars[k] = s.getPropertyValue(k).trim());

  const all = document.querySelectorAll('*');

  // Type scale
  const scale = {};
  all.forEach(el => {
    const c = getComputedStyle(el);
    const fs = parseFloat(c.fontSize);
    if (!fs) return;
    const key = Math.round(fs) + 'px';
    if (!scale[key]) scale[key] = {family: c.fontFamily, weight: c.fontWeight, lh: c.lineHeight, ls: c.letterSpacing, count: 0};
    scale[key].count++;
  });
  out.typeScale = Object.entries(scale).map(([k,v]) => ({size:k, ...v})).sort((a,b) => parseFloat(b.size)-parseFloat(a.size));

  // Colors
  all.forEach(el => {
    const c = getComputedStyle(el);
    ['color','backgroundColor','borderColor'].forEach(p => {
      const v = c[p];
      if (!v || v === 'rgba(0, 0, 0, 0)' || v === 'transparent') return;
      const m = v.match(/rgb\((\d+),\s*(\d+),\s*(\d+)\)/);
      if (m) {
        const hex = '#' + [m[1],m[2],m[3]].map(x => parseInt(x).toString(16).padStart(2,'0')).join('');
        if (p === 'color') out.colors.text.push(hex);
        else if (p === 'backgroundColor') out.colors.bg.push(hex);
        else out.colors.border.push(hex);
      }
    });
  });
  out.colors.text = [...new Set(out.colors.text)];
  out.colors.bg = [...new Set(out.colors.bg)];
  out.colors.border = [...new Set(out.colors.border)];

  // Shadows & radii
  all.forEach(el => {
    const c = getComputedStyle(el);
    const bs = c.boxShadow;
    if (bs && bs !== 'none') out.shadows.push(bs);
    const br = c.borderRadius;
    if (br && br !== '0px') out.radii.push(br);
  });
  out.shadows = [...new Set(out.shadows)];
  out.radii = [...new Set(out.radii)].sort();

  // Headings
  document.querySelectorAll('h1,h2,h3,h4,h5,h6').forEach(el => {
    const c = getComputedStyle(el);
    const tag = el.tagName.toLowerCase();
    if (!out.headings[tag]) out.headings[tag] = {size: c.fontSize, weight: c.fontWeight, family: c.fontFamily, lh: c.lineHeight, sample: el.textContent.trim().slice(0, 50)};
  });

  console.log(JSON.stringify(out, null, 2));
})();
```

## Convenciones del frontmatter

| Campo | Descripción |
|-------|-------------|
| `primary` | Color CTA principal |
| `primary-deep` | Hover/press del primary |
| `primary-soft` | Versión más clara del primary |
| `ink` | Color de texto body |
| `ink-secondary/muted/subtle` | Escala de grises de texto |
| `canvas` | Fondo blanco/default |
| `canvas-soft` | Fondo alternativo claro |
| `brand-dark` | Color de fondo oscuro (hero, footer) |
| `hairline` | Color de bordes por defecto |
| `accent-*` | Colores de acento secundarios |
| `semantic-*` | Colores de estado (success, error, warning) |
| `on-primary` | Texto sobre primary |
| `on-brand` | Texto sobre brand-dark |
