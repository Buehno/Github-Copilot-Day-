# ⚡ Quick Start - Redesign Aconchegante

Guia rápido (5 minutos) para começar a usar o novo tema.

---

## 📖 Leitura Rápida

1. **O que foi feito?** → Leia `SUMMARY.md` (2 min)
2. **Como implementar?** → Leia `docs/INTEGRATION_GUIDE.md` (3 min)
3. **Validar tudo?** → Siga `IMPLEMENTATION_CHECKLIST.md` (10 dias)

---

## 🚀 3 Passos Rápidos

### Passo 1: Copiar CSS
Os arquivos CSS já foram criados:
```
✅ SocOps/wwwroot/css/aconchegante.css (600+ linhas)
✅ SocOps/Layout/MainLayout.razor.css
```

### Passo 2: Atualizar index.html
Abra `SocOps/wwwroot/index.html` e adicione no `<head>`:

```html
<!-- Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;600;700&family=Merriweather:wght@400;700&display=swap" rel="stylesheet" />

<!-- Tema Aconchegante -->
<link href="css/aconchegante.css" rel="stylesheet" />
```

### Passo 3: Testar
```bash
cd SocOps
dotnet run
# Abrir http://localhost:5000
```

---

## 🎨 Cores Principais

```
🟤 Fundo:          #F6EFE9
⚪ Painel:         #FFFFFF
🟨 Acento Claro:   #EADFCB
🟫 Acento Prim:    #C99B73
🟤 Texto Prim:     #7D5A3C
🟠 CTA:            #D17C5A (Botões)
```

---

## 💻 Usar Classes CSS

### Botões
```html
<button class="btn btn-primary">Ação</button>
<button class="btn btn-ghost">Secundário</button>
<button class="btn btn-primary btn-sm">Pequeno</button>
```

### Cards
```html
<div class="card">
  <div class="card-header"><h3>Título</h3></div>
  <div class="card-body">Conteúdo</div>
  <div class="card-footer">Footer</div>
</div>
```

### Formulários
```html
<div class="form-group">
  <label for="name">Nome</label>
  <input id="name" type="text" />
</div>
```

### Bingo Board
```html
<div class="bingo-board grid-5">
  <button class="bingo-square">Item 1</button>
  <button class="bingo-square selected">Selected</button>
  <!-- ... -->
</div>
```

### Utilitários
```html
<!-- Spacing -->
<div class="mb-md">Margin bottom</div>
<div class="mt-lg">Margin top</div>

<!-- Flexbox -->
<div class="flex gap-md">Flex com gap</div>
<div class="flex-between">Space between</div>
<div class="flex-center">Centered</div>

<!-- Texto -->
<p class="text-center">Centralizado</p>
<p class="text-muted">Texto muted</p>
<p class="text-sm">Pequeno</p>
```

---

## 📱 Responsividade

O tema já é **mobile-first**. Testa em:

- **320px** (mobile)
- **768px** (tablet)
- **1024px+** (desktop)

DevTools → F12 → Toggle device toolbar (Ctrl+Shift+M)

---

## ✅ Validação Rápida

Abrir DevTools (F12) e verificar:

1. **Console:** Sem erros
2. **Network:** CSS carrega
3. **Fonts:** Nunito aparece
4. **Colors:** Beige background
5. **Buttons:** Funcionam com cor certa

---

## 📚 Documentação Completa

Consulte quando necessário:

| Arquivo | Assunto |
|---------|---------|
| `SUMMARY.md` | Visão geral |
| `docs/DESIGN_SYSTEM.md` | Especificação técnica |
| `docs/COLOR_PALETTE.md` | Cores + Acessibilidade |
| `docs/INTEGRATION_GUIDE.md` | Integração componentes |
| `IMPLEMENTATION_CHECKLIST.md` | Checklist 10 fases |
| `SocOps/Pages/ExampleComponents.razor` | Demo visual |

---

## 🎯 Próximo

1. ✅ Ler este Quick Start (5 min)
2. ➡️ Seguir `docs/INTEGRATION_GUIDE.md` (passo a passo)
3. ➡️ Validar com `IMPLEMENTATION_CHECKLIST.md`
4. ➡️ Criar PR e mergear

---

## 💡 Dicas Rápidas

- **Esqueça de uma classe?** → Consulte `docs/DESIGN_SYSTEM.md` seção "Utilitários"
- **Quer mudar uma cor?** → Editar `:root` em `aconchegante.css`
- **Modal não aparece?** → Adicionar `.modal-backdrop` + `.modal-card`
- **Responsividade quebrada?** → Testar com DevTools device toolbar
- **Fonte não carrega?** → Verificar se Google Fonts link está em `index.html`

---

**Tempo Total:** 5 minutos ⏱️  
**Status:** Pronto para usar! 🚀

Siga para `docs/INTEGRATION_GUIDE.md` para próximos passos.
