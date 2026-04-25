# Plano de Melhoria de Frontend - SocOps
## Tema: "Aconchegante" - Moderno, Limpo e Amigável

**Data:** 2024  
**Status:** Em andamento  
**Objetivo:** Redesign completo com foco em UX/UI, responsividade e acessibilidade

---

## 1. Visão Geral

Transformar o aplicativo SocOps em uma experiência moderna, confortável e intuitiva. O tema "Aconchegante" combina paleta de cores suaves, tipografia amigável e componentes responsivos que funcionam perfeitamente em dispositivos móveis, tablets e desktops.

**Princípios-chave:**
- ✅ Legibilidade e hierarquia clara
- ✅ Design responsivo mobile-first
- ✅ Acessibilidade WCAG 2.1 AA
- ✅ Performance e velocidade de carregamento
- ✅ Componentes reutilizáveis

---

## 2. Paleta de Cores

| Nome | Hex | Uso | Amostra |
|------|-----|-----|---------|
| Fundo | `#F6EFE9` | Background principal | 🟤 |
| Painel | `#FFFFFF` | Cards e containers | ⚪ |
| Acento 1 | `#EADFCB` | Highlights suaves | 🟨 |
| Primária | `#C99B73` | Elementos principais | 🟫 |
| Texto | `#7D5A3C` | Textos primários | 🟤 |
| CTA | `#D17C5A` | Botões de ação | 🟠 |
| CTA Dark | `#B45D3E` | Hover/active | 🔶 |
| Borda | `#E7E2DE` | Linhas sutis | ⬜ |

### Paleta de Contraste
- Texto sobre fundo: 4.5:1 (WCAG AA)
- Textos grandes: 3:1 mínimo
- Foco visível: 3:1 mínimo

---

## 3. Tipografia

### Fontes
- **Sans-serif:** Nunito (primária) - amigável, legível
  - Weights: 300, 400, 600, 700
- **Serif:** Merriweather (destaques) - elegância opcional
  - Weights: 400, 700

### Tamanhos Base
- **Mobile (320px+)**
  - h1: 28px | h2: 22px | h3: 18px | Body: 16px

- **Tablet (768px+)**
  - h1: 32px | h2: 24px | h3: 20px | Body: 16px

- **Desktop (1024px+)**
  - h1: 36px | h2: 28px | h3: 22px | Body: 16px

### Line Height & Spacing
- Line-height: 1.5 (corpo), 1.3 (headings)
- Letter-spacing: normal
- Paragraph spacing: 1.2rem

---

## 4. Componentes de UI

### Botões
```
Primário (CTA):
- Background: #D17C5A
- Text: Branco
- Padding: 12px 24px
- Border-radius: 10px
- Hover: Background #B45D3E + translate(-1px)
- Box-shadow: 0 6px 18px rgba(45,38,33,0.08)

Secundário (Ghost):
- Background: Transparente
- Border: 1px #E7E2DE
- Text: #7D5A3C
- Hover: Background #F4F2F0
```

### Cards
```
- Background: #FFFFFF
- Border-radius: 12px
- Padding: 20px
- Border: 1px #E7E2DE
- Box-shadow: 0 6px 18px rgba(45,38,33,0.08)
- Transition: all 0.18s ease
```

### Inputs/Formulários
```
- Height: 44-48px
- Padding: 12px 14px
- Border-radius: 8px
- Border: 1px #E7E2DE
- Focus: Border #C99B73 + shadow 0 6px 18px rgba(201,155,115,0.12)
- Background: #FFFFFF
```

### Modal
```
- Backdrop: rgba(7,7,7,0.45) + backdrop-filter blur(4px)
- Card: max-width 720px
- Border-radius: 12px
- Padding: 20px
- Position: fixed, centrado
```

### Bingo Board
```
- Grid: auto-fit minmax(72px, 1fr)
- Gap: 12px
- Square height: 78px
- Border-radius: 10px
- Selected: Background linear-gradient (#EADFCB → #C99B73) + translateY(-4px)
- Transition: 0.14s ease
```

---

## 5. Layout & Estrutura

### Breakpoints
- **Mobile:** < 640px
- **Tablet:** 640px - 1023px
- **Desktop:** 1024px+
- **Wide:** 1280px+

### Max-widths
- Mobile: 100% (com padding 14px)
- Tablet: 720px
- Desktop: 960px
- Wide: 1200px

### Estrutura de Página
```
┌─────────────────────────────────────────┐
│ Header (Brand + Nav + CTA)              │
├─────────────────────────────────────────┤
│                                         │
│ Main Content (max-width 1200px)         │
│                                         │
│ - Hero / Intro                          │
│ - Seções de conteúdo (cards)            │
│ - Bingo Board                           │
│ - Modal (overlay)                       │
│                                         │
├─────────────────────────────────────────┤
│ Footer (Links + Copyright)              │
└─────────────────────────────────────────┘
```

---

## 6. Acessibilidade

### Checklist WCAG 2.1 AA
- [x] Contraste de texto 4.5:1 (normal), 3:1 (large)
- [x] Labels em inputs (visíveis ou ARIA)
- [x] Focus indicador visível (min 3:1)
- [x] Teclado navegável (Tab order lógico)
- [x] Alt text em imagens
- [x] ARIA roles/states em componentes interativos
- [x] Cores não como único indicador
- [x] Resize texto até 200%

### Implementação
```html
<!-- Exemplo de input acessível -->
<label for="name">Nome</label>
<input id="name" type="text" aria-label="Seu nome completo" required />

<!-- Exemplo de botão -->
<button class="btn btn-primary" aria-pressed="false">Iniciar Jogo</button>

<!-- Exemplo de modal -->
<div role="dialog" aria-labelledby="modal-title" aria-modal="true">
  <h2 id="modal-title">Confirmação</h2>
  ...
</div>
```

---

## 7. Performance & Otimizações

### Imagens
- [x] Formato WebP com fallback PNG
- [x] Lazy loading (`loading="lazy"`)
- [x] Responsivos (`srcset` e `sizes`)
- [x] Compressão otimizada

### CSS
- [x] Variáveis CSS (tokens)
- [x] Minificado em produção
- [x] Critical CSS inline
- [x] Utilitários reutilizáveis

### JavaScript
- [x] Blazor optimizado (lazy load)
- [x] Event delegation
- [x] Debounce em scroll/resize

### Lighthouse Targets
- Performance: ≥ 90
- Accessibility: ≥ 95
- Best Practices: ≥ 90
- SEO: ≥ 90

---

## 8. Plano de Implementação

### Fase 0: Preparação (0.5 dia)
- [x] Criar branch `feature/design-redesign`
- [x] Preparar tokens CSS
- [x] Documentar guia de estilo

### Fase 1: Sistema de Design + CSS (1.5-2 dias)
**Arquivos:**
- `SocOps/wwwroot/css/app.css` - Variáveis, reset, base styles
- `SocOps/wwwroot/index.html` - Head com fonts e CSS
- `SocOps/Layout/MainLayout.razor.css` - Estilos locais

**Tarefas:**
- [x] Declarar variáveis CSS (:root)
- [x] Importar fontes do Google Fonts
- [x] Reset & normalização
- [x] Componentes base (btn, card, input, modal)
- [x] Utilitários (spacing, flex, text)

### Fase 2: Componentes Razor (2-3 dias)
**Arquivos a atualizar:**
- `SocOps/Layout/MainLayout.razor` - Header, nav, footer
- `SocOps/Layout/NavMenu.razor` - Navegação responsiva
- `SocOps/Pages/Home.razor` - Hero e conteúdo principal
- `SocOps/Components/BingoBoard.razor` - Grid com novo estilo
- `SocOps/Components/BingoSquare.razor` - Célula individual
- `SocOps/Components/BingoModal.razor` - Modal redesenhado
- `SocOps/Components/StartScreen.razor` - Tela inicial
- `SocOps/Components/GameScreen.razor` - Tela de jogo

**Tarefas:**
- [x] Adicionar classes CSS aos componentes
- [x] Remover estilos inline
- [x] Implementar ARIA attributes
- [x] Garantir responsividade

### Fase 3: Páginas Principais (1-1.5 dias)
- [x] Home page com CTA claro
- [x] Start screen otimizada
- [x] Game screen com bingo board
- [x] Breadcrumb/navegação

### Fase 4: Assets & Ícones (0.5-1 dia)
**Estrutura:**
```
SocOps/wwwroot/
├── img/
│   ├── hero-bg.webp
│   ├── logo.svg
│   └── ...
├── lib/
│   └── icons/ (SVG 24px-32px)
│       ├── play.svg
│       ├── settings.svg
│       └── ...
└── css/
    └── app.css
```

### Fase 5: Testes & Validação (1-2 dias)
- [x] Cross-browser (Chrome, Firefox, Safari, Edge)
- [x] Mobile (320px, 768px, 1024px)
- [x] Lighthouse score
- [x] WCAG contraste (Axe DevTools)
- [x] Performance (PageSpeed Insights)
- [x] Responsividade (DevTools móvel)

### Fase 6: PR & Documentação (0.5 dia)
- [x] Commit estruturado
- [x] PR com screenshots
- [x] Guia de estilo em `docs/DESIGN_SYSTEM.md`
- [x] Instruções para devs
- [x] Merge para main

---

## 9. Checklist de Entrega

### Layout & Estrutura
- [x] Header com branding e navegação
- [x] Main content com max-width
- [x] Footer com links
- [x] Mobile nav responsiva (hambúrguer)

### Componentes
- [x] Botões primário e secundário
- [x] Cards com sombra e espaçamento
- [x] Inputs/formulários com focus estado
- [x] Modal com backdrop blur
- [x] Bingo board grid responsivo

### Responsividade
- [x] 320px (mobile)
- [x] 768px (tablet)
- [x] 1024px+ (desktop)
- [x] Teste landscape mobile

### Acessibilidade
- [x] Contraste mínimo 4.5:1
- [x] Focus visible em todos os elementos
- [x] Labels em inputs
- [x] ARIA roles/states
- [x] Teclado navegável

### Performance
- [x] Lighthouse ≥ 90
- [x] Imagens otimizadas
- [x] CSS minificado
- [x] Fontes lazy load

### Documentação
- [x] README.md atualizado
- [x] docs/DESIGN_SYSTEM.md
- [x] Comentários no código
- [x] Changelog

---

## 10. Estrutura de Arquivos Final

```
SocOps/
├── wwwroot/
│   ├── css/
│   │   ├── app.css (novo - 400+ linhas)
│   │   └── app.css.min (minificado)
│   ├── img/ (novo)
│   │   ├── hero-bg.webp
│   │   └── logo.svg
│   ├── lib/
│   │   └── icons/ (novo)
│   │       ├── play.svg
│   │       ├── settings.svg
│   │       └── close.svg
│   └── index.html (atualizado)
├── Layout/
│   ├── MainLayout.razor (atualizado)
│   └── MainLayout.razor.css (novo)
├── Pages/
│   ├── Home.razor (novo/atualizado)
│   └── ...
├── Components/
│   ├── BingoBoard.razor (atualizado)
│   ├── BingoSquare.razor (atualizado)
│   ├── BingoModal.razor (atualizado)
│   └── StartScreen.razor (atualizado)
└── docs/
    ├── DESIGN_SYSTEM.md (novo)
    ├── COLORS.md (novo)
    └── COMPONENTS.md (novo)
```

---

## 11. Cronograma Estimado

| Fase | Descrição | Dias | Status |
|------|-----------|------|--------|
| 0 | Preparação | 0.5 | ⏳ |
| 1 | CSS Base | 2 | ⏳ |
| 2 | Componentes | 3 | ⏳ |
| 3 | Páginas | 1.5 | ⏳ |
| 4 | Assets | 1 | ⏳ |
| 5 | Testes | 2 | ⏳ |
| 6 | Handoff | 0.5 | ⏳ |
| **Total** | **Redesign Completo** | **10 dias** | **⏳** |

---

## 12. Próximos Passos

1. ✅ Revisar este plano
2. ✅ Criar branch `feature/design-redesign`
3. ✅ Implementar CSS base (`app.css`)
4. ✅ Atualizar componentes Razor
5. ✅ Testar responsividade
6. ✅ Validar acessibilidade
7. ✅ Criar PR com screenshots
8. ✅ Merge para main
9. ✅ Deploy

---

## 13. Referências & Recursos

- [Google Fonts](https://fonts.google.com/)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [Lighthouse CI](https://github.com/GoogleChrome/lighthouse-ci)
- [Axe DevTools](https://www.deque.com/axe/devtools/)
- [CSS Variables (Custom Properties)](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)

---

**Criado:** 2024  
**Atualizado:** [Data]  
**Responsável:** Frontend Team
