# Design System - SocOps Aconchegante

Documentação completa do sistema de design para o projeto SocOps com tema "Aconchegante".

## Visão Geral

O tema "Aconchegante" (confortável, amigável) combina uma paleta de cores quentes e suaves com tipografia moderna e componentes responsivos. O objetivo é criar uma experiência de usuário clara, legível e acessível.

---

## 1. Paleta de Cores

### Cores Primárias

| Nome | Hex | RGB | Uso |
|------|-----|-----|-----|
| Fundo Principal | `#F6EFE9` | rgb(246, 239, 233) | Background geral da aplicação |
| Painel/Card | `#FFFFFF` | rgb(255, 255, 255) | Cards, inputs, modais |
| Acento Claro | `#EADFCB` | rgb(234, 223, 203) | Highlights suaves, backgrounds secundários |
| Acento Primário | `#C99B73` | rgb(201, 155, 115) | Elementos principais, acentos |
| Texto Primário | `#7D5A3C` | rgb(125, 90, 60) | Textos principais, titles |
| CTA (Call-to-Action) | `#D17C5A` | rgb(209, 124, 90) | Botões primários, links ativos |
| CTA Hover | `#B45D3E` | rgb(180, 93, 62) | Estado hover em botões |
| CTA Active | `#A24A2F` | rgb(162, 74, 47) | Estado ativo/pressionado |

### Cores Neutras

| Nome | Hex | Uso |
|------|-----|-----|
| Fundo Secundário | `#F4F2F0` | Backgrounds alternativos |
| Texto Secundário | `#6B675F` | Textos secundários |
| Texto Muted | `#9D9691` | Textos desabilitados, hints |
| Borda Leve | `#E7E2DE` | Bordas, separadores |
| Borda Média | `#D4CDCA` | Bordas mais visíveis |

### Sombras

```css
--shadow-xs: 0 2px 4px rgba(45, 38, 33, 0.04);
--shadow-sm: 0 4px 12px rgba(45, 38, 33, 0.06);
--shadow-md: 0 6px 18px rgba(45, 38, 33, 0.08);
--shadow-lg: 0 12px 32px rgba(45, 38, 33, 0.12);
```

---

## 2. Tipografia

### Famílias de Fontes

**Sans-serif (Primária):** Nunito
- Pesos: 300 (light), 400 (regular), 600 (semibold), 700 (bold)
- Uso: Corpo, labels, botões, heading
- Importação: `https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;600;700&display=swap`

**Serif (Secundária):** Merriweather
- Pesos: 400 (regular), 700 (bold)
- Uso: Destaques, citações (opcional)
- Importação: `https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700&display=swap`

### Escala de Tamanhos

#### Mobile (320px - 767px)
```
h1: 28px (font-weight: 700)
h2: 22px (font-weight: 700)
h3: 18px (font-weight: 700)
Body: 16px (font-weight: 400)
Small: 14px
```

#### Tablet (768px - 1023px)
```
h1: 32px
h2: 24px
h3: 20px
Body: 16px
```

#### Desktop (1024px+)
```
h1: 36px
h2: 28px
h3: 22px
Body: 16px
```

### Line Height & Spacing

```
Line-height:
  - Headings: 1.3
  - Body: 1.5
  - Relaxed: 1.75

Paragraph spacing: 1.2rem (20px)
Letter-spacing: normal (com títulos em -0.5px)
```

---

## 3. Componentes

### Botões

#### Primário (CTA)
```razor
<button class="btn btn-primary">Ação Principal</button>
```
- Background: `#D17C5A`
- Cor: Branco
- Padding: 10px 16px
- Border-radius: 8px
- Sombra: `var(--shadow-sm)`
- Hover: Background `#B45D3E`, Transform `translateY(-2px)`, Sombra maior
- Focus: Outline 2px solid `#D17C5A`, offset 2px

#### Secundário (Ghost)
```razor
<button class="btn btn-ghost">Ação Secundária</button>
```
- Background: Transparente
- Border: 1px `#E7E2DE`
- Cor: `#7D5A3C`
- Padding: 10px 16px
- Hover: Background `#F4F2F0`, Border `#D4CDCA`

#### Variantes de Tamanho
- Pequeno: `.btn-sm` → Padding 6px 12px, font-size 0.85rem
- Grande: `.btn-lg` → Padding 14px 28px, font-size 1rem
- Block: `.btn-block` → Width 100%

### Cards

```razor
<div class="card">
  <div class="card-header">
    <h3>Título</h3>
  </div>
  <div class="card-body">
    Conteúdo
  </div>
  <div class="card-footer">
    Footer
  </div>
</div>
```

Estilos:
- Background: `#FFFFFF`
- Border-radius: 12px
- Padding: 20px
- Border: 1px `#E7E2DE`
- Sombra: `var(--shadow-sm)`
- Hover: Sombra maior, Transform `translateY(-2px)`

### Inputs/Formulários

```razor
<div class="form-group">
  <label for="name">Nome</label>
  <input type="text" id="name" class="form-input" placeholder="Digite seu nome" />
</div>
```

Estilos:
- Width: 100%
- Padding: 12px 14px
- Border-radius: 8px
- Border: 1px `#E7E2DE`
- Focus: Border `#C99B73`, box-shadow `0 0 0 3px rgba(201, 155, 115, 0.1)`
- Font: `var(--font-sans)`, 16px

### Modal

```razor
<div class="modal-backdrop">
  <div class="modal-card">
    <div class="modal-header">
      <h2 class="modal-title">Título</h2>
      <button class="modal-close" aria-label="Fechar">&times;</button>
    </div>
    <div class="modal-body">
      Conteúdo
    </div>
    <div class="modal-footer">
      <button class="btn btn-ghost">Cancelar</button>
      <button class="btn btn-primary">Confirmar</button>
    </div>
  </div>
</div>
```

Estilos:
- Backdrop: `rgba(7, 7, 7, 0.45)` com `backdrop-filter: blur(4px)`
- Card: max-width 720px (`.small`: 480px, `.large`: 960px)
- Border-radius: 12px
- Padding: 32px
- Sombra: `var(--shadow-lg)`
- Animação: slideUp 0.18s ease

### Bingo Board

```razor
<div class="bingo-board grid-5">
  <button class="bingo-square" @onclick="SelectSquare">Item 1</button>
  <button class="bingo-square selected">Item 2</button>
  <!-- ... -->
</div>
```

Estilos:
- Grid: `repeat(5, 1fr)`
- Gap: 12px (desktop), 8px (mobile)
- Aspect-ratio: 1:1
- Height: 78px (mobile), 88px (desktop)
- Border-radius: 12px
- Background: `#F4F2F0` (normal), gradient `#EADFCB → #C99B73` (selecionado)
- Selecionado: Transform `translateY(-4px)`, Sombra maior
- Transition: 0.12s ease

---

## 4. Espaçamento

Sistema de spacing em progressão:

```css
--space-xs:  6px
--space-sm:  12px
--space-md:  20px
--space-lg:  32px
--space-xl:  48px
--space-2xl: 64px
```

### Usos Recomendados
- **xs (6px):** Gap mínimo entre elementos próximos
- **sm (12px):** Padding interno de inputs, gap entre botões pequenos
- **md (20px):** Padding de cards, margin entre seções
- **lg (32px):** Padding de página, margin entre grandes seções
- **xl (48px):** Spacing principal entre blocos
- **2xl (64px):** Espaçamento heróico, full-width sections

---

## 5. Border Radius

```css
--radius-sm:   8px   /* Inputs, botões pequenos */
--radius-md:   12px  /* Cards, modais */
--radius-lg:   16px  /* Containers grandes */
--radius-full: 9999px /* Pills, circles */
```

---

## 6. Transições

```css
--transition-fast:  0.12s ease  /* Hover rápido */
--transition-base:  0.18s ease  /* Transição padrão */
--transition-slow:  0.3s ease   /* Animações mais longas */
```

### Propriedades a Animar
- `.btn:hover` → Transform, box-shadow
- `.card:hover` → Box-shadow, transform
- `.bingo-square` → Background, transform, border-color
- `.input:focus` → Border-color, box-shadow

---

## 7. Responsividade

### Breakpoints

```css
Mobile:  < 640px
Tablet:  640px - 1023px
Desktop: 1024px+
Wide:    1280px+
```

### Grid Layout

Mobile-first approach:

```
Mobile (320px):
- Grid: auto-fit, minmax(70px, 1fr)
- Max-width: 100%
- Padding: 14px

Tablet (768px):
- Max-width: 720px
- Padding: 28px

Desktop (1024px):
- Max-width: 960px
- Padding: 32px
- Grid: repeat(5, 1fr) para bingo
```

---

## 8. Acessibilidade

### Contraste

Todos os textos atendem **WCAG 2.1 AA**:
- Texto normal: Mínimo 4.5:1
- Texto grande: Mínimo 3:1
- Elementos UI: Mínimo 3:1

### Focus Visível

```css
*:focus-visible {
  outline: 2px solid var(--cta-primary);
  outline-offset: 2px;
}
```

### Atributos ARIA

```html
<!-- Botão -->
<button aria-pressed="false">Toggle</button>

<!-- Input com label -->
<label for="name">Nome</label>
<input id="name" type="text" aria-label="Seu nome completo" />

<!-- Modal -->
<div role="dialog" aria-labelledby="modal-title" aria-modal="true">
  <h2 id="modal-title">Título</h2>
</div>

<!-- Bingo board -->
<div class="bingo-board" role="grid">
  <button role="gridcell" aria-pressed="false">Item</button>
</div>
```

### Navegação por Teclado

- Tab: Navega entre elementos focáveis
- Enter/Space: Ativa botões
- Escape: Fecha modais
- Arrow keys: Navega em grids (bingo board)

---

## 9. Utilitários CSS

### Display & Layout

```css
.flex            /* display: flex */
.flex-col        /* flex-direction: column */
.flex-center     /* Flex com align-items & justify-content center */
.flex-between    /* Flex com justify-content: space-between */

.gap-xs/sm/md/lg /* gap: var(--space-*) */
.stack           /* Flex column com gap-md */
.stack-sm/lg     /* Stack com gaps diferentes */
```

### Spacing

```css
.mb-xs/sm/md/lg  /* margin-bottom */
.mt-xs/sm/md/lg  /* margin-top */
.px-md           /* padding left & right */
.py-md           /* padding top & bottom */
```

### Texto

```css
.text-center     /* text-align: center */
.text-muted      /* color: var(--text-muted) */
.text-secondary  /* color: var(--text-secondary) */
.text-sm         /* font-size: 0.85rem */
.text-lg         /* font-size: 1.1rem */

.font-serif      /* font-family: var(--font-serif) */
.font-bold       /* font-weight: 700 */
.font-semibold   /* font-weight: 600 */

.uppercase       /* text-transform: uppercase */
.lowercase       /* text-transform: lowercase */
.capitalize      /* text-transform: capitalize */
```

### Border & Sombra

```css
.rounded         /* border-radius: var(--radius-md) */
.rounded-sm/lg   /* border-radius var */
.rounded-full    /* border-radius: 9999px */

.shadow          /* box-shadow: var(--shadow-sm) */
.shadow-md/lg    /* box-shadow var */
```

### Visibilidade

```css
.hidden          /* display: none !important */
.visible         /* display: block !important */
.invisible       /* visibility: hidden */
```

---

## 10. Exemplo de Implementação

### Página Simples

```razor
@page "/"

<div class="stack">
    <div class="text-center mb-lg">
        <h1>Bem-vindo ao SocOps</h1>
        <p class="text-muted">Um workshop interativo e divertido</p>
    </div>

    <div class="card">
        <div class="card-header">
            <h2>Como Jogar</h2>
        </div>
        <div class="card-body">
            <p>Selecione os itens do bingo e complete a linha para ganhar!</p>
        </div>
        <div class="card-footer flex-between">
            <button class="btn btn-ghost">Mais Info</button>
            <button class="btn btn-primary">Iniciar</button>
        </div>
    </div>

    <div class="bingo-board grid-5">
        @for (int i = 1; i <= 25; i++)
        {
            <button class="bingo-square">Item @i</button>
        }
    </div>
</div>
```

---

## 11. Variáveis CSS (Reference)

```css
:root {
  /* Colors */
  --bg-primary: #F6EFE9;
  --bg-secondary: #F4F2F0;
  --bg-panel: #FFFFFF;
  --accent-light: #EADFCB;
  --accent-primary: #C99B73;
  --text-primary: #7D5A3C;
  --text-secondary: #6B675F;
  --text-muted: #9D9691;
  --cta-primary: #D17C5A;
  --cta-hover: #B45D3E;
  --cta-active: #A24A2F;
  --border-light: #E7E2DE;
  --border-medium: #D4CDCA;
  --shadow-xs: 0 2px 4px rgba(45, 38, 33, 0.04);
  --shadow-sm: 0 4px 12px rgba(45, 38, 33, 0.06);
  --shadow-md: 0 6px 18px rgba(45, 38, 33, 0.08);
  --shadow-lg: 0 12px 32px rgba(45, 38, 33, 0.12);

  /* Typography */
  --font-sans: "Nunito", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  --font-serif: "Merriweather", Georgia, "Times New Roman", serif;
  --font-mono: "SF Mono", Monaco, "Cascadia Code", "Roboto Mono", Consolas, "Courier New", monospace;
  --base-font-size: 16px;
  --line-height-tight: 1.3;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.75;

  /* Spacing */
  --space-xs: 6px;
  --space-sm: 12px;
  --space-md: 20px;
  --space-lg: 32px;
  --space-xl: 48px;
  --space-2xl: 64px;

  /* Border Radius */
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-full: 9999px;

  /* Transitions */
  --transition-fast: 0.12s ease;
  --transition-base: 0.18s ease;
  --transition-slow: 0.3s ease;

  /* Z-Index */
  --z-dropdown: 100;
  --z-sticky: 500;
  --z-fixed: 1000;
  --z-modal-backdrop: 9998;
  --z-modal: 9999;
}
```

---

## 12. Checklist de Implementação

- [ ] Adicionar fonts do Google Fonts no `index.html`
- [ ] Incluir `aconchegante.css` no projeto
- [ ] Atualizar `MainLayout.razor` com nova estrutura
- [ ] Criar `MainLayout.razor.css` com estilos locais
- [ ] Atualizar componentes (BingoBoard, Cards, Modais)
- [ ] Testar responsividade (320px, 768px, 1024px)
- [ ] Validar contraste com Axe DevTools
- [ ] Testar com leitor de tela
- [ ] Validar com Lighthouse
- [ ] Documentar componentes customizados
- [ ] Criar PR com screenshots

---

**Criado:** 2024  
**Última atualização:** 2024  
**Status:** Ativo
