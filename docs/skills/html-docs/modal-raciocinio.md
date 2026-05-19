# Skill Auxiliar: Modal de Raciocínio Decisional (modal-raciocinio.md)

Este documento define as diretrizes estritas, a marcação de código HTML e os scripts de controle para implementar a **Seção de Raciocínio Decisional e o Modal de Linha do Tempo** nos arquivos de tópicos (`topic-*.html`).

---

## 1. Gatilho de Ativação
Esta skill auxiliar deve ser consultada sempre que for necessário criar ou editar um documento do tipo Tópico (`topic-*.html`) para registrar a cronologia evolutiva de decisões e diálogos com o usuário.

---

## 2. Padrão de Estruturação HTML (Strict Layout)

### A. O Bloco Informativo de Gatilho
Na seção principal da página (geralmente no final do artigo), insira o container de chamada:
```html
<section class="bg-indigo-50/50 border border-indigo-100 rounded p-3 space-y-2">
  <div class="flex items-center space-x-1.5 text-indigo-900 font-bold text-xs">
    <svg class="w-4 h-4 text-indigo-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
    <span>Cronologia do Raciocínio Decisional</span>
  </div>
  <p class="text-xs text-slate-600 leading-relaxed">
    [Breve texto explicativo resumindo que a construção do sistema foi evolutiva e iterativa]
  </p>
  <div class="pt-1.5">
    <button onclick="openModal()" class="inline-flex items-center space-x-1 px-3 py-1.5 bg-indigo-600 hover:bg-indigo-700 active:bg-indigo-800 text-white font-bold text-xs rounded transition-colors shadow-sm tracking-wide">
      <span>Ver Raciocínio</span>
      <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M9 5l7 7-7 7" />
      </svg>
    </button>
  </div>
</section>
```

### B. A Estrutura do Modal Overlay
O modal deve ser adicionado ao final do `<body>`, fora da tag `<main>`, para evitar problemas de posicionamento relativo e z-index:
```html
<div id="modal-timeline" class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/60 backdrop-blur-sm hidden" onclick="closeModalOnOutsideClick(event)">
  <div class="bg-white rounded border border-slate-200 shadow-2xl max-w-2xl w-full p-4 mx-3 max-h-[85vh] flex flex-col" onclick="event.stopPropagation()">
    
    <!-- Cabeçalho do Modal -->
    <div class="flex items-center justify-between border-b border-slate-200 pb-2 mb-3">
      <div class="flex items-center space-x-1.5">
        <span class="w-2.5 h-2.5 rounded-full bg-indigo-600 animate-ping"></span>
        <h3 class="text-sm font-bold text-slate-900">Registro Temporal de Decisões</h3>
      </div>
      <button onclick="closeModal()" class="text-slate-400 hover:text-slate-600 font-bold text-xs p-1 rounded hover:bg-slate-100 transition-colors">
        Fechar
      </button>
    </div>

    <!-- Linha do Tempo (Scrollable) -->
    <div class="overflow-y-auto space-y-3 pr-1 text-xs select-none">
      <!-- Os itens da timeline entram aqui -->
    </div>

    <!-- Rodapé do Modal -->
    <div class="border-t border-slate-200 pt-2.5 mt-3 flex justify-end">
      <button onclick="closeModal()" class="px-3 py-1 bg-slate-900 hover:bg-slate-800 text-white font-bold text-xs rounded transition-colors">
        Fechar Visualização
      </button>
    </div>

  </div>
</div>
```

---

## 3. Design dos Nós da Linha do Tempo
Cada nó de decisão no modal deve possuir a seguinte estrutura:

```html
<div class="relative pl-5 border-l-2 border-indigo-200">
  <!-- Marcador circular -->
  <div class="absolute -left-[6px] top-1.5 w-2.5 h-2.5 rounded-full bg-indigo-600 border border-white"></div>
  
  <!-- Timestamp estrito em dd/mmm - HH:mm:ss -->
  <span class="font-bold font-mono text-[10px] text-indigo-600">18/Mai - 11:49:01</span>
  
  <!-- Título da Etapa -->
  <h4 class="font-bold text-slate-900 mt-0.5">[Título Sucinto do Passo]</h4>
  
  <!-- Descrição Sucinta (Gatilho + Solução) -->
  <p class="text-[11px] text-slate-500 mt-0.5 leading-relaxed">
    <strong>Gatilho:</strong> [Gatilho/Input do Usuário que motivou o passo]<br>
    <strong>Solução:</strong> [Diretriz técnica decidida ou alteração de código realizada]
  </p>
</div>
```

> [!NOTE]
> O **último nó** da linha do tempo pode utilizar um marcador circular com cor diferenciada (ex: `bg-emerald-500`) ou um ping para explicitar visualmente a conclusão do raciocínio.

---

## 4. Gerenciamento de Estado via JavaScript (Vanilla JS)
Insira as seguintes funções de controle de estado no script do documento para garantir o correto funcionamento e usabilidade do modal:

```javascript
// Abre o modal de cronologia e congela o scroll da página ao fundo
function openModal() {
  const modal = document.getElementById('modal-timeline');
  modal.classList.remove('hidden');
  document.body.style.overflow = 'hidden'; 
}

// Fecha o modal e restaura o comportamento de scroll normal
function closeModal() {
  const modal = document.getElementById('modal-timeline');
  modal.classList.add('hidden');
  document.body.style.overflow = ''; 
}

// Fecha o modal ao clicar fora da caixa do modal (no overlay)
function closeModalOnOutsideClick(event) {
  if (event.target === document.getElementById('modal-timeline')) {
    closeModal();
  }
}
```
