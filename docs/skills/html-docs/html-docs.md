# Skill: Criação de Documentações HTML (html-docs)

## Contexto / Gatilho
Esta skill deve ser ativada sempre que o usuário solicitar a criação de documentações, páginas de ajuda, guias, tutoriais ou qualquer arquivo em formato HTML estruturado sob o termo "docs" ou "html-docs".

---

## 🛠️ Passo a Passo Otimizado para Execução

### Passo 1: Classificação e Nomenclatura (Taxonomia de Arquivos)
Antes de criar o arquivo físico, defina em qual categoria ele se enquadra para aplicar o prefixo e as regras de governança corretas:
*   **📂 Tópicos (`topic-<slug>.html`):** 
    *   *Propósito:* Documentar discussões iniciais, estudos de caso, decisões de design e pensamentos conceituais.
    *   *Governança:* **DEVEM** ser indexados na tabela principal de tópicos (`#table-topics`) do arquivo `/docs/index.html`.
*   **📂 Documentações Técnicas (`docs-<slug>.html`):**
    *   *Propósito:* Manuais estritamente técnicos, instruções de comandos, guias de APIs e referências de codificação.
    *   *Governança:* **NÃO** devem constar na `#table-topics`. São páginas de consulta técnica direta.
    *   *Conectividade:* Devem conter um link de navegação explícito rotulado como `"Discussão Inicial"` apontando diretamente para o arquivo `topic-*` conceitual correspondente.

---

### Passo 2: Estrutura HTML5 Semântica e Navegação Cruzada
Crie a estrutura base do documento utilizando elementos semânticos estruturais padrão:
1.  **Semântica Base:** Use tags semânticas do HTML5 (`<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`, `<aside>`) para estruturar a página em vez de abusar de `<div>`.
2.  **Hierarquia Clara:** Mantenha uma hierarquia de títulos consistente (`<h1>` única para a página, seguido de `<h2>`, `<h3>` etc.). Evite marcações redundantes e aninhamento excessivo.
3.  **🌐 Padronização de Cabeçalhos (Headers):**
    *   Tanto os arquivos `topic-*.html` quanto os `docs-*.html` **DEVEM** possuir um cabeçalho `<header>` contendo um link explícito para retornar à listagem central de documentações (`index.html`), rotulado como `"Voltar ao Hub"`, `"Voltar ao Sumário"` ou similar.
    *   Nos arquivos `docs-*.html` de documentação técnica, este link deve coexistir ao lado do link `"Discussão Inicial"` para facilitar a navegação em teia.

---

### Passo 3: Taxonomia Semântica de Atributos (`id` e `class`)
Para garantir código limpo, fácil manutenção e permitir referências exatas em prompts de IA e ferramentas externas:
*   **Estrutura de `id` para Componentes:** Todo componente principal, tabela ou seção do layout deve possuir um atributo `id` estruturado como: `<ui-element>-<contexto-local|contexto-dominio|contexto>`.
    *   *Exemplo:* Uma tabela/grid que lista tópicos deve usar `id="grid-topics"`. Um cabeçalho de hub deve usar `id="header-hub"`.
*   **Classes Semânticas de Contexto:** Adicionalmente às classes utilitárias de estilo (ex: Tailwind CSS), cada componente deve possuir uma classe personalizada idêntica ao padrão de `id` semântico acima. Isto cria contextos CSS legíveis para humanos e ideais para scrapers, testes automatizados e seletores regex.
*   **Herança Semântica para Elementos Filhos:** Todos os elementos descendentes (filhos) de um componente principal devem herdar a base do `id` ou `class` do pai como prefixo, seguido pelo seu próprio subcontexto funcional.
    *   *Fórmula:* `<prefixo-do-pai>-<subcontexto-do-filho>`
    *   *Exemplos:* Dentro do container `id="grid-topics"`, os títulos usam `id="grid-topics-headings"`, e os botões de ação usam `id="grid-topics-action-buttons"` ou `class="grid-topics-action-buttons"`.

---

### Passo 4: Estilização com Tailwind CSS (Light Premium & Densidade 50%)
Adicione a biblioteca Tailwind CSS no `<head>` (`<script src="https://cdn.tailwindcss.com"></script>`) e aplique a regra de **compressão estrita de 50%** em espaçamentos, raios de borda e tipografia para maximizar a densidade visual (Tailwind Compacto):
1.  **Design Light Premium:** Foco em cores claras e sutis de fundo (`bg-slate-50`, `bg-white`) com tipografias escuras e de alto contraste (`text-slate-800`, `text-slate-900`).
2.  **Container Padrão:** Use `max-w-7xl` como largura default do container para garantir legibilidade ideal centralizada.
3.  **Responsividade Extrema:** Otimize a exibição para telas de até 1536px, oferecendo *graceful degradation* completa para smartphones com navegação em coluna e tabelas roláveis (`overflow-x-auto`).
4.  **Tabela de Compressão de 50%:**
    *   *Espaçamento (Paddings, Margins, Gaps):*
        *   `py-16` / `py-24` &rarr; Reduzir para `py-8` / `py-12`
        *   `py-8` / `py-6` &rarr; Reduzir para `py-4` / `py-3`
        *   `px-6` / `px-4` &rarr; Reduzir para `px-3` / `px-2`
        *   `p-4` / `p-2` &rarr; Reduzir para `p-2` / `p-1`
        *   `gap-6` / `space-y-6` &rarr; Reduzir para `gap-3` / `space-y-3`
    *   *Raios de Borda (Border Radiuses):*
        *   `rounded-3xl` / `rounded-2xl` &rarr; Reduzir para `rounded-xl` / `rounded-lg`
        *   `rounded-xl` / `rounded-lg` &rarr; Reduzir para `rounded-md` / `rounded`
        *   `rounded` / `rounded-sm` &rarr; Reduzir para `rounded-sm` / `rounded-none`
    *   *Escala de Fontes:*
        *   Títulos de destaque (`text-4xl`/`text-3xl`) &rarr; Reduzir para `text-2xl`/`text-xl`
        *   Subtítulos e títulos de seção (`text-2xl`/`text-xl`) &rarr; Reduzir para `text-lg`/`text-sm`
        *   Corpo de texto (`text-base`/`text-sm`) &rarr; Reduzir para `text-sm`/`text-xs`
        *   Meta-dados, slugs e tags &rarr; Utilizar `text-[10px]` para máxima compacidade.

---

### Passo 5: Interatividade e Recursos Dinâmicos
Implemente as funcionalidades JavaScript integradas nativas:
1.  **Experiência de Cópia de Código:** Sempre implemente um botão de "Copiar" absoluto no topo direito de blocos `pre` + `code` (`top-1 right-1`) com JavaScript vanilla para transferir o conteúdo instantaneamente.
2.  **Seção de Raciocínio Decisional (Apenas para Tópicos):**
    *   *Diretrizes e Templates Estritos:* A estrutura, marcação HTML e controle de estado do modal de linha do tempo **DEVEM** seguir rigorosamente as especificações detalhadas em 
    *   *Bloco Informativo Compacto:* Adicione um bloco destacado (`bg-indigo-50/50` e borda `border-indigo-100`) com um título e um botão CTA estilizado (ex: `"Ver Raciocínio"`).
    *   *Modal Overlay Interativo:* O botão deve disparar um modal com `onclick` que exiba um painel rolável contendo a linha do tempo das decisões evolutivas usando um fundo escuro semi-transparente fixo (`fixed inset-0 bg-slate-900/60 backdrop-blur-sm`).
    *   *Carimbo de Tempo Padrão:* Cada etapa decisória no modal deve ser identificada com a data e hora formatada estritamente em `dd/mmm - HH:mm:ss` (ex: `18/Mai - 11:49:01`).
    *   *Vanilla JavaScript Puro:* Toda a lógica de abertura/fechamento do modal deve ser implementada com JavaScript nativo leve integrado à página.
    *   Caso existam, siga as instruções no template [modal-raciocinio.md](file:///home/gstv/projects/docs/skills/html-docs/modal-raciocinio.md).

---

## Exemplos de Validação

### ✅ Correto (Semântico, 50% mais Compacto, Botão de Copiar, Taxonomia de ID e Atributos)
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Diretrizes de Instalação</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-50 font-sans text-slate-800 antialiased min-h-screen flex flex-col">

  <!-- Header Compacto com Links de Navegação (ID e Class Semânticos) -->
  <header id="header-hub" class="header-hub bg-white border-b border-slate-200 py-2">
    <div id="header-hub-container" class="header-hub-container max-w-7xl mx-auto px-3 flex justify-between items-center">
      <h1 id="header-hub-title" class="header-hub-title text-sm font-bold text-slate-900">Guia de API (docs-install.html)</h1>
      <div id="header-hub-navigation" class="header-hub-navigation flex items-center space-x-2.5">
        <a id="header-hub-link-discussion" href="./topic-instalacao-framework.html" class="text-xs font-semibold text-indigo-600 hover:underline">
          &larr; Discussão Inicial
        </a>
        <span class="text-slate-300 text-[10px]">|</span>
        <a id="header-hub-link-back" href="./index.html" class="text-xs font-semibold text-slate-500 hover:text-indigo-600 transition-colors">
          Voltar ao Hub
        </a>
      </div>
    </div>
  </header>

  <!-- Main Compacto (py-4, text-xs/sm) -->
  <main id="main-content" class="main-content flex-grow max-w-7xl mx-auto px-3 py-4 w-full">
    <article id="article-guide" class="article-guide space-y-3">
      <section id="section-install" class="section-install space-y-1.5">
        <h2 id="section-install-heading" class="section-install-heading text-sm font-semibold text-slate-900">Passo 1: Instalação</h2>
        <p id="section-install-paragraph" class="text-xs text-slate-600">Execute o seguinte comando no terminal do seu projeto:</p>
        
        <!-- Bloco de Código de Alta Densidade (rounded-sm p-2 text-xs) -->
        <div id="section-install-terminal-box" class="section-install-terminal-box relative bg-slate-900 text-slate-100 rounded-sm p-2 font-mono text-xs group">
          <button id="section-install-btn-copy" onclick="copyToClipboard(this)" class="section-install-btn-copy absolute top-1 right-1 bg-slate-800 hover:bg-slate-700 text-slate-300 text-[10px] px-1.5 py-0.5 rounded-sm transition-colors">
            Copiar
          </button>
          <pre><code id="code-install">npm install @sdk/client-api</code></pre>
        </div>
      </section>
    </article>
  </main>

  <footer id="footer-page" class="footer-page bg-white border-t border-slate-200 py-3 mt-4">
    <div id="footer-page-container" class="footer-page-container max-w-7xl mx-auto px-3 text-center text-[10px] text-slate-500">
      &copy; 2026 Meu Projeto. Todos os direitos reservados.
    </div>
  </footer>

  <script>
    function copyToClipboard(button) {
      const codeElement = button.nextElementSibling.querySelector('code');
      navigator.clipboard.writeText(codeElement.textContent.trim());
      button.innerText = 'Copiado!';
      setTimeout(() => { button.innerText = 'Copiar'; }, 2000);
    }
  </script>
</body>
</html>
```

---

### ❌ Incorreto (Layout folgado, rounded gigante, sem taxonomia e sem botão de copiar)
```html
<!-- Ruim: rounded exagerado, semântica pobre, paddings largos desperdiçando tela de programador -->
<div class="bg-indigo-900 p-8 rounded-3xl m-8">
  <h1 class="text-4xl font-black mb-6">Instalação</h1>
  <p class="text-lg mb-4">Execute o comando:</p>
  <pre class="bg-black p-6 rounded-2xl">npm install @sdk/client-api</pre>
</div>
```

---

## Restrições (Não Fazer)
* **NÃO** utilize layouts pesados ou interfaces inteiramente "dark mode" a menos que expressamente solicitado.
* **NÃO** utilize classes de espaçamento largas (`p-8`, `p-6`, `gap-6`, `space-y-6`) a menos que queira especificamente um visual folgado. Dê preferência por compacidade visual.
* **NÃO** liste arquivos prefixados com `docs-` na tabela `#table-topics` do `index.html`. Apenas indexe os arquivos prefixados com `topic-`.
* **NÃO** force o usuário a selecionar manualmente o texto do código para conseguir copiar. Sempre implemente o botão funcional de cópia.
