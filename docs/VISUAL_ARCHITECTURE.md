# 🎨 Arquitetura Visual do Tema Aconchegante

Documentação da estrutura visual e componentes do redesign.

---

## 📐 Layout Principal

```
┌───────────────────────────────────────────────────────────┐
│ HEADER - site-header                                       │
│ ┌─────────────────────────────────────────────────────┐   │
│ │ [Logo] SocOps                [Home] [Counter] [Go] │   │
│ └─────────────────────────────────────────────────────┘   │
└───────────────────────────────────────────────────────────┘

┌───────────────────────────────────────────────────────────┐
│ CONTENT - site-content (max-width: 1200px)               │
│                                                            │
│  Main content area                                        │
│  - Pages                                                  │
│  - Components                                             │
│  - Cards                                                  │
│  - Bingo Board                                            │
│                                                            │
└───────────────────────────────────────────────────────────┘

┌───────────────────────────────────────────────────────────┐
│ FOOTER - site-footer                                      │
│ © 2024 SocOps | Acessibilidade | Contato                 │
└───────────────────────────────────────────────────────────┘
```

---

## 🧩 Componentes Base

### 1. Buttons

#### Primário (CTA)
```
┌──────────────────────┐
│  Ação Principal  →   │  ← Hover: Move up 2px
└──────────────────────┘
Color: #D17C5A (Rust)
Hover: #B45D3E (Dark Rust)
```

**Classes:**
```html
<button class="btn btn-primary">Primário</button>
<button class="btn btn-primary btn-sm">Pequeno</button>
<button class="btn btn-primary btn-lg">Grande</button>
<button class="btn btn-primary btn-block">100% Width</button>
```

#### Secundário (Ghost)
```
┌──────────────────────┐
│  Secundário          │  ← Outline apenas
└──────────────────────┘
Border: #E7E2DE (Light)
Text: #7D5A3C
Hover: Fill com #F4F2F0
```

**Classes:**
```html
<button class="btn btn-ghost">Secundário</button>
<button class="btn btn-ghost btn-sm">Pequeno</button>
```

---

### 2. Cards

```
┌─ card ──────────────────────────┐
│                                  │
│ ┌─ card-header ────────────────┐ │
│ │  Título                      │ │
│ └──────────────────────────────┘ │
│                                  │
│ ┌─ card-body ──────────────────┐ │
│ │  Conteúdo principal          │ │
│ │  - Texto                     │ │
│ │  - Elementos                 │ │
│ └──────────────────────────────┘ │
│                                  │
│ ┌─ card-footer ────────────────┐ │
│ │ [Action 1]              [Go] │ │
│ └──────────────────────────────┘ │
│                                  │
└─────────────────────────────────┘
```

**CSS:**
```css
.card {
  background: #FFFFFF;
  border-radius: 12px;
  padding: 20px;
  border: 1px #E7E2DE;
  box-shadow: 0 4px 12px rgba(45,38,33,0.06);
}

.card-header {
  border-bottom: 1px #E7E2DE;
  margin-bottom: 20px;
}
```

---

### 3. Forms & Inputs

```
Nome Completo                    ← Label
┌──────────────────────────────────┐
│ Digite seu nome...               │ ← Input
└──────────────────────────────────┘
Focus: Border #C99B73 + Shadow
```

**HTML:**
```html
<div class="form-group">
  <label for="name">Nome Completo</label>
  <input id="name" type="text" placeholder="Digite..." />
</div>
```

---

### 4. Bingo Board

```
5x5 Grid responsivo:

┌─────────┬─────────┬─────────┬─────────┬─────────┐
│         │         │         │         │         │
│  Item   │ Item    │ Item    │ Item    │ Item    │
│    1    │   2     │   3     │   4     │   5     │
│         │         │         │         │         │
├─────────┼─────────┼─────────┼─────────┼─────────┤
│         │ ╔═════╗ │         │         │         │
│  Item   │ ║ SEL ║ │ Item    │ Item    │ Item    │
│    6    │ ║  7  ║ │   8     │   9     │   10    │
│         │ ╚═════╝ │         │         │         │
├─────────┼─────────┼─────────┼─────────┼─────────┤
│         │         │         │         │         │
│ ...     │ ...     │ ...     │ ...     │ ...     │
│         │         │         │         │         │
└─────────┴─────────┴─────────┴─────────┴─────────┘

Selected:
- Background: Gradiente #EADFCB → #C99B73
- Text: Branco
- Transform: Y -4px (float)
- Sombra: Maior
```

**HTML:**
```html
<div class="bingo-board grid-5">
  <button class="bingo-square">Item 1</button>
  <button class="bingo-square selected">Item 2</button>
  <!-- 23 mais -->
</div>
```

---

### 5. Modal

```
                    ┌─────────────────────────────────────┐
                    │ ╔═════════════════════════════════╗ │
                    │ ║ Título Modal                   ✕ ║
                    │ ╠═════════════════════════════════╣ │
                    │ ║                                   ║
                    │ ║  Conteúdo principal              ║
                    │ ║                                   ║
                    │ ╠═════════════════════════════════╣ │
                    │ ║ [Cancelar]            [Confirmar] ║
                    │ ╚═════════════════════════════════╝ │
                    └─────────────────────────────────────┘

Backdrop: Escuro + Blur
Modal Max-width: 720px (small: 480px, large: 960px)
```

**HTML:**
```html
<div class="modal-backdrop">
  <div class="modal-card">
    <div class="modal-header">
      <h2 class="modal-title">Título</h2>
      <button class="modal-close">&times;</button>
    </div>
    <div class="modal-body">Conteúdo</div>
    <div class="modal-footer">
      <button class="btn btn-ghost">Cancelar</button>
      <button class="btn btn-primary">Confirmar</button>
    </div>
  </div>
</div>
```

---

## 🎨 Paleta Visual

### Warm Color Harmony

```
Fundo Principal          Acento Claro           Acento Primário
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│                  │   │                  │   │                  │
│   #F6EFE9        │   │   #EADFCB        │   │   #C99B73        │
│  WARM BEIGE      │   │  LIGHT CREAM     │   │  WARM BROWN      │
│                  │   │                  │   │                  │
└──────────────────┘   └──────────────────┘   └──────────────────┘

Texto Primário         CTA Primário           CTA Hover
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│████████████████  │   │                  │   │                  │
│  #7D5A3C         │   │   #D17C5A        │   │   #B45D3E        │
│  DARK BROWN      │   │  WARM RUST       │   │  DEEP RUST       │
│████████████████  │   │                  │   │                  │
└──────────────────┘   └──────────────────┘   └──────────────────┘
```

---

## 📊 Tipografia

### Hierarquia de Tamanhos

```
Desktop (1024px+):
H1: 36px ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
H2: 28px ━━━━━━━━━━━━━━━━━━━━━━━
H3: 22px ━━━━━━━━━━━━━━━━
Body: 16px ━━━━━━━━━
Small: 14px ━━━━

Font: Nunito (sans) para body
Font: Merriweather (serif) para destaques
Line-height: 1.5 (corpo), 1.3 (headings)
```

---

## 📱 Breakpoints & Responsividade

### Mobile (320px)
```
[☰] SocOps      ← Hambúrguer pode estar aqui

[Content]
[Full width com padding 14px]
```

### Tablet (768px)
```
[Logo] SocOps    [Home] [Counter] [Go]

[Content]
[720px max-width]
```

### Desktop (1024px+)
```
[Logo] SocOps    [Home] [Counter] [Go]

[Content]
[960px max-width]

Bingo Board: 5 colunas grid
```

---

## ✨ Animações

### Transitions

```
Fast (0.12s):    Hover effects, state changes
Base (0.18s):    Component animations, modals
Slow (0.3s):     Page transitions
```

### Keyframes

```
fadeIn:    Opacity 0 → 1
slideUp:   Y +20px, Opacity 0 → Normal
pulse:     Opacity 1 ⇄ 0.5 (loop)
```

---

## 🔍 Utilitários - Quick Reference

### Display & Flex
```html
.flex              <!-- display: flex -->
.flex-col          <!-- flex-direction: column -->
.flex-center       <!-- align & justify center -->
.flex-between      <!-- space-between -->
.gap-sm/md/lg      <!-- gap -->
.stack             <!-- flex-col + gap-md -->
```

### Spacing
```html
.mb-xs/sm/md/lg    <!-- margin-bottom -->
.mt-xs/sm/md/lg    <!-- margin-top -->
.px-md             <!-- padding left+right -->
.py-md             <!-- padding top+bottom -->
```

### Text
```html
.text-center       <!-- text-align: center -->
.text-muted        <!-- color: #9D9691 -->
.text-secondary    <!-- color: #6B675F -->
.text-sm           <!-- font-size: 0.85rem -->
.text-lg           <!-- font-size: 1.1rem -->
.uppercase         <!-- text-transform -->
.font-bold         <!-- font-weight: 700 -->
```

### Visual
```html
.rounded           <!-- border-radius: 12px -->
.shadow            <!-- box-shadow: sm -->
.shadow-md/lg      <!-- box-shadow levels -->
.hidden            <!-- display: none -->
```

---

## 🎯 Estados Visuais

### Button States

```
Normal:     #D17C5A background
Hover:      #B45D3E background + Y -2px
Active:     #A24A2F background
Focus:      Outline 2px #D17C5A
Disabled:   Opacity 0.6
```

### Input States

```
Normal:     Border #E7E2DE
Focus:      Border #C99B73 + shadow
Invalid:    Border #E83E3E (se implementar)
Disabled:   Opacity 0.6, cursor not-allowed
```

### Square Estados

```
Normal:     Background #F4F2F0, Border #E7E2DE
Hover:      Background #E9E3DB
Selected:   Gradient + Y -4px + sombra
Disabled:   Opacity 0.5
```

---

## 📏 Espaçamento Grid

```
Espaçamento Consistente:

6px   (xs)  ─ Gaps mínimos
12px  (sm)  ─ Padding inputs, gaps pequenos
20px  (md)  ─ Padding cards, margin seções
32px  (lg)  ─ Padding página, margin grandes
48px  (xl)  ─ Spacing principal
64px  (2xl) ─ Heróico
```

---

## 🔐 Acessibilidade Visual

```
Contraste:      ✅ 4.5:1 (WCAG AA)
Focus:          ✅ 2px outline
Colors:         ✅ Não como único indicador
Text Resize:    ✅ Até 200%
Motion:         ✅ Respeita prefers-reduced-motion
```

---

## 📦 Arquivo de Referência

Localização no projeto:
```
SocOps/wwwroot/css/aconchegante.css
└─ :root (variáveis)
   ├─ Colors
   ├─ Typography
   ├─ Spacing
   ├─ Border Radius
   └─ Transitions
```

---

**Criado:** 2024  
**Versão:** 1.0  
**Status:** Visual Reference Completa
