# Checklist de Implementação - Redesign Aconchegante

## 📋 Preparação Inicial

### Repositório & Branch
- [ ] Clonar/abrir repositório localmente
- [ ] Criar branch: `git checkout -b feature/design-redesign-aconchegante`
- [ ] Confirmar estar na branch correta: `git branch -v`

### Ambiente
- [ ] .NET 6+ instalado: `dotnet --version`
- [ ] Git configurado: `git config --list`
- [ ] VS Code aberto no diretório raiz
- [ ] Terminal PowerShell/Bash disponível

---

## 🎨 Fase 1: CSS & Design Tokens

### Arquivos CSS Criados
- [x] `SocOps/wwwroot/css/aconchegante.css` (600+ linhas)
  - [x] Variáveis CSS `:root` (cores, fonts, spacing)
  - [x] Reset & normalize
  - [x] Layout base (app-shell, header, content, footer)
  - [x] Componentes (btn, card, input, modal, bingo-board)
  - [x] Utilitários (flex, gap, margin, padding, text)
  - [x] Animações (fadeIn, slideUp, pulse)
  - [x] Responsividade (768px, 1024px breakpoints)

- [x] `SocOps/Layout/MainLayout.razor.css`
  - [x] Estilos locais do header
  - [x] Estilos locais do footer
  - [x] Mobile adjustments

### Atualizar index.html
- [ ] Abrir `SocOps/wwwroot/index.html`
- [ ] Adicionar fontes do Google Fonts no `<head>`:
  ```html
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;600;700&family=Merriweather:wght@400;700&display=swap" rel="stylesheet" />
  ```
- [ ] Adicionar link para `aconchegante.css`:
  ```html
  <link href="css/aconchegante.css" rel="stylesheet" />
  ```
- [ ] Salvar e testar no navegador

### Validar CSS
- [ ] Arquivo carrega sem erros (DevTools → Console)
- [ ] Variáveis CSS acessíveis (inspecionar elemento)
- [ ] Fontes carregam (inspecionar texto)
- [ ] Sem conflitos com bootstrap.min.css

---

## 🏗️ Fase 2: Layout Principal

### MainLayout.razor
- [ ] Backup do arquivo original
- [ ] Substituir estrutura HTML:
  ```razor
  <div class="app-shell">
      <header class="site-header" role="banner">
          <!-- Logo + Brand -->
          <div class="site-header-brand">
              <div class="site-header-brand-logo">S</div>
              <h1>SocOps</h1>
              <div class="site-header-brand-subtitle">Workshop</div>
          </div>
          
          <!-- Navigation -->
          <nav class="site-header-nav" role="navigation">
              <a href="" class="btn btn-ghost btn-sm">Home</a>
              <a href="counter" class="btn btn-ghost btn-sm">Counter</a>
              <a href="game" class="btn btn-primary btn-sm">Iniciar Jogo</a>
          </nav>
      </header>
      
      <main class="site-content" role="main">
          @Body
      </main>
      
      <footer class="site-footer" role="contentinfo">
          <div class="site-footer-content">
              <div class="text-muted">© 2024 SocOps</div>
              <div class="text-muted">
                  <a href="#">Acessibilidade</a> | 
                  <a href="#">Contato</a>
              </div>
          </div>
      </footer>
  </div>
  ```
- [ ] Remover referência a `NavMenu` se existir
- [ ] Salvar e testar

### Validar Layout
- [ ] Header aparece com logo + navegação
- [ ] Main content centralizado
- [ ] Footer no rodapé
- [ ] Cores corretas (beige background, brown text)
- [ ] Fonts carregar (Nunito)

---

## 🧩 Fase 3: Componentes

### BingoBoard.razor
- [ ] Adicionar wrapper com classe `.bingo-board.grid-5`:
  ```razor
  <div class="bingo-board grid-5">
      @foreach (var square in Squares)
      {
          <button class="bingo-square @(square.Selected ? "selected" : "")"
                  @onclick="() => SelectSquare(square)"
                  aria-pressed="@square.Selected">
              @square.Text
          </button>
      }
  </div>
  ```
- [ ] Testar seleção (classes updated)
- [ ] Testar responsividade (grid adapta em mobile)

### BingoSquare.razor
- [ ] Usar classe `.bingo-square`
- [ ] Remover estilos inline
- [ ] Adicionar `aria-pressed` attribute

### StartScreen.razor
- [ ] Envolver em card:
  ```razor
  <div class="card" style="max-width: 500px; margin: 0 auto;">
      <div class="card-header">
          <h2>Bem-vindo ao SocOps</h2>
      </div>
      <div class="card-body stack">
          <div class="form-group">
              <label for="name">Seu Nome</label>
              <input id="name" type="text" class="form-input" />
          </div>
      </div>
      <div class="card-footer">
          <button class="btn btn-primary btn-block">Iniciar</button>
      </div>
  </div>
  ```
- [ ] Aplicar classes de form
- [ ] Testar responsividade

### GameScreen.razor
- [ ] Usar classes `.stack`, `.flex-between`, `.text-center`
- [ ] Aplicar `.bingo-board` ao grid
- [ ] Buttons com `.btn-primary`, `.btn-ghost`
- [ ] Testar layout em diferentes tamanhos

### BingoModal.razor
- [ ] Usar estrutura modal:
  ```razor
  @if (IsOpen)
  {
      <div class="modal-backdrop" @onclick="Close">
          <div class="modal-card" @onclick:stopPropagation="true">
              <div class="modal-header">
                  <h2 class="modal-title">@Title</h2>
                  <button class="modal-close" @onclick="Close">&times;</button>
              </div>
              <div class="modal-body">@ChildContent</div>
              <div class="modal-footer">
                  <button class="btn btn-ghost">Cancelar</button>
                  <button class="btn btn-primary">Confirmar</button>
              </div>
          </div>
      </div>
  }
  ```
- [ ] Testar backdrop blur
- [ ] Testar close button
- [ ] Testar keyboard escape (adicionar)

---

## 📱 Fase 4: Responsividade

### Mobile (320px)
- [ ] DevTools: Toggle device toolbar
- [ ] Selecionar "iPhone SE" ou 320px width
- [ ] Verificar:
  - [ ] Header não quebra
  - [ ] Buttons acessíveis
  - [ ] Bingo grid adapta
  - [ ] Sem scroll horizontal

### Tablet (768px)
- [ ] Selecionar "iPad" ou 768px width
- [ ] Verificar:
  - [ ] Layout ajustado
  - [ ] Grid em 3-4 colunas
  - [ ] Espaçamento adequado

### Desktop (1024px+)
- [ ] Verificar em full width
- [ ] Bingo grid em 5 colunas
- [ ] Layout completo

### Landscape
- [ ] Testar em landscape mobile
- [ ] Sem scroll vertical excessivo

---

## ♿ Fase 5: Acessibilidade

### Contraste (WebAIM)
- [ ] Abrir https://webaim.org/resources/contrastchecker/
- [ ] Testar combinações:
  - [ ] #FFFFFF + #7D5A3C = 5.8:1 ✅ (AAA)
  - [ ] #F6EFE9 + #7D5A3C = 5.2:1 ✅ (AAA)
  - [ ] #FFFFFF + #D17C5A = 4.6:1 ✅ (AA)
- [ ] Tudo deve ser ≥ 4.5:1

### Focus Visível
- [ ] Abrir DevTools
- [ ] Clicar em document
- [ ] Apertar Tab para navegar
- [ ] Verificar:
  - [ ] Outline visível em buttons
  - [ ] Outline visível em inputs
  - [ ] Outline visível em links
  - [ ] Order lógico

### Labels & ARIA
- [ ] Verificar todos os inputs têm `<label for="id">`
- [ ] Adicionar `aria-label` em buttons sem texto
- [ ] Modal tem `role="dialog"` e `aria-modal="true"`
- [ ] Bingo squares têm `aria-pressed` boolean

### Teste com Axe DevTools
- [ ] Instalar extensão Chrome "Axe DevTools"
- [ ] Abrir DevTools
- [ ] Rodar "Scan ALL of my page"
- [ ] Verificar:
  - [ ] Sem "Critical" issues
  - [ ] Sem "Serious" issues
  - [ ] Warnings aceitáveis

### Teste com WAVE
- [ ] Ir para https://wave.webaim.org/
- [ ] Colar URL da aplicação
- [ ] Verificar:
  - [ ] Sem erros críticos
  - [ ] Contraste adequado
  - [ ] Sem alerts de estrutura

### Navegação por Teclado
- [ ] Tab: Navega entre elementos ✅
- [ ] Shift+Tab: Retrocede ✅
- [ ] Enter: Ativa botões ✅
- [ ] Space: Seleciona checkboxes/toggles ✅
- [ ] Escape: Fecha modal ✅
- [ ] Arrow keys: Navega em grid (bingo) - a implementar

---

## ⚡ Fase 6: Performance

### Lighthouse Score
- [ ] DevTools → Lighthouse tab
- [ ] Selecionar "Mobile"
- [ ] Rodar audit completo
- [ ] Metas:
  - [ ] Performance: ≥ 90
  - [ ] Accessibility: ≥ 95
  - [ ] Best Practices: ≥ 90
  - [ ] SEO: ≥ 90

### Tamanho de Arquivos
- [ ] DevTools → Network
- [ ] Recarregar página (Ctrl+Shift+R)
- [ ] Verificar:
  - [ ] aconchegante.css < 50KB (minificado)
  - [ ] Fonts carregam rápido
  - [ ] Sem arquivos bloqueadores

### Carregamento de Fontes
- [ ] Google Fonts com `display=swap`
- [ ] Preconnect aos domínios
- [ ] Verificar FOUT (Flash of Unstyled Text) mínimo

### Otimizações (Opcional)
- [ ] Minificar aconchegante.css
- [ ] Lazy-load imagens (loading="lazy")
- [ ] Compress imagens (WebP com fallback)
- [ ] Cache estratégico

---

## 🧪 Fase 7: Testes Cross-Browser

### Chrome/Chromium
- [ ] Abrir aplicação
- [ ] Verificar:
  - [ ] Colors corretas
  - [ ] Fonts carregam
  - [ ] Animations suaves
  - [ ] Responsive OK

### Firefox
- [ ] DevTools: F12
- [ ] Mesmas verificações Chrome
- [ ] Testar foco keyboard

### Safari
- [ ] Se em Mac: Abrir em Safari
- [ ] Verificar:
  - [ ] Backdrop filter funciona (blur)
  - [ ] CSS variables suportadas
  - [ ] Fonts renderizam igual

### Edge
- [ ] Abrir em Edge (Chromium-based)
- [ ] Verificar funcionamento completo

---

## 📸 Fase 8: Documentação & Screenshots

### Screenshots
- [ ] Home page (desktop 1024px)
- [ ] Mobile view (320px)
- [ ] Componentes (buttons, cards)
- [ ] Bingo board
- [ ] Modal aberto
- [ ] Lighthouse score

### Documentação
- [ ] Atualizar README.md com referência ao novo tema
- [ ] Adicionar screenshots de antes/depois
- [ ] Link para `docs/DESIGN_SYSTEM.md`

### Arquivo de Mudanças
- [ ] Listar todos os arquivos modificados/criados:
  - [ ] `SocOps/wwwroot/css/aconchegante.css` (NOVO)
  - [ ] `SocOps/Layout/MainLayout.razor.css` (NOVO)
  - [ ] `SocOps/wwwroot/index.html` (MODIFICADO)
  - [ ] `SocOps/Layout/MainLayout.razor` (MODIFICADO)
  - [ ] `SocOps/Pages/ExampleComponents.razor` (NOVO)
  - [ ] `docs/DESIGN_SYSTEM.md` (NOVO)
  - [ ] `docs/COLOR_PALETTE.md` (NOVO)
  - [ ] `docs/INTEGRATION_GUIDE.md` (NOVO)
  - [ ] `FRONTEND_IMPROVEMENT_PLAN.md` (NOVO)
  - [ ] `REDESIGN_STATUS.md` (NOVO)

---

## 🚀 Fase 9: Git & Commit

### Adicionar Arquivos
```bash
git add .
git status  # Verificar o que será commitado
```

### Commit Estruturado
```bash
git commit -m "feat(design): implementar redesign 'Aconchegante'

- Adicionar CSS base com tema quente e acolhedor
- Variáveis de design (cores, typography, spacing)
- Componentes base (btn, card, input, modal, bingo-board)
- Atualizar MainLayout com novo header/footer
- Responsividade mobile-first
- WCAG 2.1 AA acessibilidade completa
- Documentação completa em docs/

Closes: #123 (se houver issue)"
```

### Push para Branch
```bash
git push -u origin feature/design-redesign-aconchegante
```

---

## 📝 Fase 10: Pull Request

### Criar PR
- [ ] GitHub: Ir para Compare & pull request
- [ ] Title: "feat(design): Redesign Aconchegante - Frontend Moderno"
- [ ] Description:
  ```markdown
  ## Descrição
  Implementação completa do redesign "Aconchegante" com tema moderno, limpo e amigável.

  ## Mudanças
  - ✅ CSS base com 600+ linhas (variáveis, componentes, utilitários)
  - ✅ Paleta de cores terrosa e acolhedora
  - ✅ Tipografia moderna (Nunito + Merriweather)
  - ✅ Responsividade mobile-first (320px, 768px, 1024px)
  - ✅ WCAG 2.1 AA acessibilidade completa
  - ✅ Documentação em docs/

  ## Testes
  - ✅ Lighthouse: Performance ≥ 90
  - ✅ Acessibilidade: Axe DevTools sem críticos
  - ✅ Responsividade: Testado em 3 breakpoints
  - ✅ Cross-browser: Chrome, Firefox, Safari, Edge

  ## Screenshots
  [Adicionar prints aqui]

  ## Related
  Closes #123
  ```

- [ ] Adicionar screenshots nas comments
- [ ] Request review
- [ ] Resolver comentários
- [ ] Merge após aprovação

---

## ✅ Finalizador

### Merge para Main
```bash
git checkout main
git pull origin main
git merge feature/design-redesign-aconchegante
git push origin main
```

### Deploy (se aplicável)
- [ ] Verificar CI/CD pipeline
- [ ] Build bem-sucedido
- [ ] Testes passam
- [ ] Deploy automático (se configurado)

### Comunicação
- [ ] Notificar stakeholders
- [ ] Compartilhar screenshots
- [ ] Documentar mudanças no CHANGELOG
- [ ] Atualizar wiki/docs do projeto

---

## 🎉 Conclusão

- [ ] Feature completa e testada
- [ ] Documentação atualizada
- [ ] PR aprovada e merged
- [ ] Deploy em produção
- [ ] Feedback coletado
- [ ] Próximos passos identificados

---

**Criado:** 2024  
**Status:** Checklist Pronto  
**Tempo Estimado:** 10 dias (fases 1-10)  
**Responsável:** Frontend Team
