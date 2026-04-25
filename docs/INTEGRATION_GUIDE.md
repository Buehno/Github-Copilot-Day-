# Guia de Integração - Tema Aconchegante

## Resumo Executivo

Este documento fornece instruções passo a passo para integrar o tema "Aconchegante" no projeto SocOps.

---

## 1. Preparação

### Pré-requisitos
- VS Code ou Visual Studio aberto no diretório do projeto
- Git configurado
- .NET 6+ instalado
- Node.js (opcional, para otimização de assets)

### Branch de Feature
```bash
git checkout -b feature/design-redesign-aconchegante
```

---

## 2. Arquivos a Criar/Atualizar

### 2.1 CSS Principal
**Arquivo:** `SocOps/wwwroot/css/aconchegante.css`
- Status: ✅ Criado
- Tamanho: ~600 linhas
- Conteúdo: Variáveis, componentes base, utilitários, responsividade

**Ação:** Copiar arquivo `aconchegante.css` para `SocOps/wwwroot/css/`

### 2.2 CSS Local do Layout
**Arquivo:** `SocOps/Layout/MainLayout.razor.css`
- Status: ✅ Criado
- Conteúdo: Estilos específicos do header, footer, content area

**Ação:** Copiar arquivo `MainLayout.razor.css` para `SocOps/Layout/`

### 2.3 Atualizar index.html
**Arquivo:** `SocOps/wwwroot/index.html`
- Adicionar links do Google Fonts
- Adicionar link para `aconchegante.css`

**Mudanças recomendadas:**
```html
<!-- No <head> -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;600;700&family=Merriweather:wght@400;700&display=swap" rel="stylesheet" />

<!-- Antes de </head> -->
<link href="css/aconchegante.css" rel="stylesheet" />
```

### 2.4 Atualizar MainLayout.razor
**Arquivo:** `SocOps/Layout/MainLayout.razor`

Estrutura esperada:
```razor
@inherits LayoutComponentBase

<div class="app-shell">
    <header class="site-header" role="banner">
        <!-- Logo + Brand -->
        <div class="site-header-brand">
            <div class="site-header-brand-logo">S</div>
            <h1>SocOps</h1>
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
            <div>© 2024 SocOps · Tema Aconchegante</div>
            <div>
                <a href="#">Acessibilidade</a> | 
                <a href="#">Contato</a>
            </div>
        </div>
    </footer>
</div>
```

---

## 3. Atualizar Componentes Existentes

### 3.1 BingoBoard.razor
Adicionar classe de grid:
```razor
<div class="bingo-board grid-5">
    @foreach (var square in Squares)
    {
        <button class="bingo-square @(square.Selected ? "selected" : "")" 
                @onclick="() => ToggleSquare(square)"
                aria-pressed="@square.Selected">
            @square.Text
        </button>
    }
</div>
```

### 3.2 StartScreen.razor
Adicionar classe de card e botão primário:
```razor
<div class="card" style="max-width: 500px; margin: 0 auto;">
    <div class="card-header">
        <h2>Bem-vindo ao SocOps</h2>
    </div>
    <div class="card-body">
        <!-- Form fields -->
        <div class="form-group">
            <label for="playerName">Seu Nome</label>
            <input id="playerName" type="text" class="form-input" />
        </div>
    </div>
    <div class="card-footer">
        <button class="btn btn-primary btn-block" @onclick="StartGame">
            Iniciar Jogo
        </button>
    </div>
</div>
```

### 3.3 GameScreen.razor
Adicionar layout com grid responsivo:
```razor
<div class="stack">
    <div class="text-center mb-md">
        <h1>Jogo em Andamento</h1>
    </div>
    
    <div class="bingo-board grid-5">
        <!-- Bingo squares aqui -->
    </div>
    
    <div class="flex-between mt-lg">
        <button class="btn btn-ghost">Menu</button>
        <span class="text-secondary">Pontuação: @Score</span>
        <button class="btn btn-primary">Conferir Bingo</button>
    </div>
</div>
```

### 3.4 Modal/BingoModal.razor
Usar classe de modal:
```razor
@if (IsOpen)
{
    <div class="modal-backdrop" @onclick="Close">
        <div class="modal-card" @onclick:stopPropagation="true">
            <div class="modal-header">
                <h2 class="modal-title">@Title</h2>
                <button class="modal-close" @onclick="Close" aria-label="Fechar">&times;</button>
            </div>
            <div class="modal-body">
                @ChildContent
            </div>
            <div class="modal-footer">
                <button class="btn btn-ghost" @onclick="Close">Cancelar</button>
                <button class="btn btn-primary" @onclick="Confirm">Confirmar</button>
            </div>
        </div>
    </div>
}
```

---

## 4. Integração Passo a Passo

### Passo 1: Copiar Arquivos CSS
```bash
# No terminal do VS Code (PowerShell/Bash)
cp docs/DESIGN_SYSTEM.md SocOps/wwwroot/css/aconchegante.css
cp docs/MainLayout.razor.css SocOps/Layout/MainLayout.razor.css
```

### Passo 2: Atualizar index.html
Abra `SocOps/wwwroot/index.html` e adicione no `<head>`:
```html
<!-- Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;600;700&family=Merriweather:wght@400;700&display=swap" rel="stylesheet" />

<!-- Aconchegante Theme -->
<link href="css/aconchegante.css" rel="stylesheet" />
```

### Passo 3: Atualizar MainLayout.razor
Abra `SocOps/Layout/MainLayout.razor` e substitua o conteúdo conforme indicado na seção 2.4.

### Passo 4: Atualizar Componentes
Para cada componente (BingoBoard, StartScreen, GameScreen, Modal):
1. Abra o arquivo `.razor`
2. Adicione as classes CSS apropriadas
3. Remova estilos inline (mova para `.razor.css`)
4. Adicione atributos ARIA se necessário

### Passo 5: Build e Teste
```bash
cd SocOps
dotnet build
dotnet run
```

Abra `http://localhost:5000` e teste:
- Layout responsivo (redimensione a janela)
- Cores aparecem corretamente
- Botões funcionam
- Bingo board responde

---

## 5. Testes de Validação

### Responsividade
- [ ] Mobile (320px): Navegação colapsável, botões acessíveis
- [ ] Tablet (768px): Layout ajustado
- [ ] Desktop (1024px): Layout completo

**Teste:**
```
DevTools (F12) → Toggle device toolbar (Ctrl+Shift+M)
Testar: 320px, 768px, 1024px
```

### Acessibilidade
- [ ] Contraste de texto (mín. 4.5:1)
- [ ] Focus visível em todos os elementos
- [ ] Labels em inputs
- [ ] Navegação por teclado (Tab, Enter, Escape)

**Ferramentas:**
- Axe DevTools (extensão Chrome)
- WAVE (webaim.org/articles/contrast)
- Lighthouse (DevTools → Lighthouse)

### Performance
- [ ] Lighthouse score ≥ 90
- [ ] Carregamento de fontes otimizado
- [ ] CSS minificado em produção

**Teste:**
```
DevTools → Lighthouse
Rodar audit: Performance, Accessibility, Best Practices
```

---

## 6. Estrutura de Arquivos Final

```
SocOps/
├── wwwroot/
│   ├── css/
│   │   ├── aconchegante.css       ← NOVO (tema principal)
│   │   ├── app.css                (mantém compatibilidade)
│   │   └── bootstrap/...
│   ├── index.html                 ← ATUALIZADO (fonts + aconchegante.css)
│   └── lib/...
├── Layout/
│   ├── MainLayout.razor           ← ATUALIZADO (novo header/footer)
│   ├── MainLayout.razor.css       ← NOVO (estilos locais)
│   └── NavMenu.razor              (pode remover ou simplificar)
├── Pages/
│   ├── Home.razor                 ← Pode usar novas classes
│   └── ...
├── Components/
│   ├── BingoBoard.razor           ← ATUALIZADO (usar .bingo-board)
│   ├── BingoSquare.razor          ← ATUALIZADO (usar .bingo-square)
│   ├── BingoModal.razor           ← ATUALIZADO (usar .modal-*)
│   ├── StartScreen.razor          ← ATUALIZADO (usar .card, .btn)
│   └── GameScreen.razor           ← ATUALIZADO (usar .stack, .btn)
└── docs/
    ├── DESIGN_SYSTEM.md           ← NOVO (referência de design)
    └── INTEGRATION_GUIDE.md       ← Este arquivo
```

---

## 7. Troubleshooting

### Problema: Fonts não carregam
**Solução:** Verificar conexão com Google Fonts, adicionar fallback fonts
```css
/* Fallback em aconchegante.css */
--font-sans: "Nunito", -apple-system, "Segoe UI", sans-serif;
```

### Problema: Cores diferentes do esperado
**Solução:** Garantir que `aconchegante.css` está depois de `bootstrap.css`
```html
<link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
<link href="css/aconchegante.css" rel="stylesheet" />
```

### Problema: Layout quebrado em mobile
**Solução:** Verificar meta viewport tag
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

### Problema: Buttons não funcionam
**Solução:** Verificar classes CSS e estrutura HTML
```razor
<!-- Correto -->
<button class="btn btn-primary">Ação</button>

<!-- Incorreto -->
<button class="btn-primary">Ação</button>
```

---

## 8. Próximos Passos

1. ✅ Integrar CSS base (`aconchegante.css`)
2. ✅ Atualizar componentes Razor
3. ✅ Testar responsividade
4. ✅ Validar acessibilidade
5. ✅ Executar testes Lighthouse
6. ✅ Criar PR com screenshots
7. ✅ Merge para main branch
8. ✅ Deploy

---

## 9. Suporte e Referências

- **CSS Variables:** https://developer.mozilla.org/en-US/docs/Web/CSS/--*
- **WCAG 2.1:** https://www.w3.org/WAI/WCAG21/quickref/
- **Lighthouse:** https://developers.google.com/web/tools/lighthouse
- **Google Fonts:** https://fonts.google.com/
- **Figma Design:** [Link para protótipo]

---

**Criado:** 2024  
**Última atualização:** 2024  
**Status:** Pronto para integração
