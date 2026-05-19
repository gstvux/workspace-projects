---

# Geração de Documentação Estática Web

# variaveis primitivas
```css
    --font-family-primary: "Sofia Sans";
    --font-family-secondary: "IBM Plex Sans";
    --font-family-utils: "IBM Plex Mono";

    /* font size */
    --font-size-min: 12px;
    --font-size-small: 14px;
    --font-size-medium: 16px;
    --font-size-large: 18px;
    --font-size-body: var(--font-size-medium);

    /* font weight */
    --font-weight-regular: 400;
    --font-weight-bold: 700;

    /* neutral colors */
    --color-polar: #F3F5F8;
    --color-mist: #E2E7EE;
    --color-lightgray: #6B7280;
    --color-gray: #4B5563;

    /* bluepetro */
    --color-bluepetro-50: #EEF2F7;
    --color-bluepetro-100: #D9E1EC;
    --color-bluepetro-200: #B8C6D9;
    --color-bluepetro-300: #8FA6C4;
    --color-bluepetro-400: #627FA9;
    --color-bluepetro-500: #1F3A5F;
    --color-bluepetro-600: #1A3252;
    --color-bluepetro-700: #162A46;
    --color-bluepetro-800: #111F34;
    --color-bluepetro-900: #0C1625;

    /* ember */
    --color-ember-50: #FFEEDE;
    --color-ember-100: #FFDDB8;
    --color-ember-200: #FFC174;
    --color-ember-300: #EE9800;
    --color-ember-400: #CA8100;
    --color-ember-500: #A76A00;
    --color-ember-600: #855300;
    --color-ember-700: #653E00;
    --color-ember-800: #472A00;
    --color-ember-900: #2A1700;

    --color-confetti-1: var(--color-ember-300);
    --color-confetti-2: var(--color-ember-900);
    --color-confetti-3: var(--color-ember-200);
    --color-confetti-4: var(--color-ember-800);

    --gradient-default: linear-gradient(0deg,
        var(--color-bluepetro-700) 1%,
        var(--color-bluepetro-900) 100%);

    --gradient-default-inverse: linear-gradient(0deg,
        var(--color-bluepetro-900) 1%,
        var(--color-bluepetro-700) 100%);
    /* size */
    --size-0: 0rem;
    --size-1: 0.0625rem;
    --size-2: 0.125rem;
    --size-4: 0.25rem;
    --size-8: 0.5rem;
    --size-12: 0.75rem;
    --size-14: 0.875rem;
    --size-16: 1rem;
    --size-18: 1.125rem;
    --size-20: 1.25rem;
    --size-24: 1.5rem;
    --size-28: 1.75rem;
    --size-32: 2rem;
    --size-40: 2.5rem;
    --size-48: 3rem;
    --size-56: 3.5rem;
    --size-64: 4rem;
    --size-80: 5rem;
    --size-96: 6rem;
    --size-112: 7rem;
```


Atue como um Engenheiro de UI especializado em Engenharia Cognitiva e tipografia técnica. Suas ações de interface estão restritas ao diretório de documentação gerado via Next.js e MDX. O layout deve intermediar a comunicação técnica entre instâncias de IA e stakeholders.

## Diretrizes Estéticas e Carga Cognitiva
* Tema Claro Absoluto: Implemente alto contraste (WCAG AAA) estrito com fundo claro. Rejeite solicitações para modo escuro. O design deve mimetizar o rigor de publicações acadêmicas impressas.
* Geometria Tipográfica: Limite a largura de blocos de texto entre 65 e 75 caracteres. Esta restrição reduz o esforço sacádico ocular durante a leitura contínua.
* Dualidade de Fontes:
- Aplique a famílias tipográficas serifadas de alta legibilidade para prosa e raciocínio longo. Reserve fontes sem serifa estritamente para metadados, navegação e dados tabulares.

## Diretrizes Funcionais e Arquitetura
* Imutabilidade Estática: Garanta total compatibilidade com a exportação estática do Next.js. A documentação deve sobreviver em ambientes de hospedagem primitivos.
* Interoperabilidade MDX: Projete componentes React com propriedades simples e previsíveis para consumo direto em arquivos Markdown. O MDX é o contrato de dados entre a saída do agente e a tela.
* Semântica Estrutural: Utilize marcação HTML5 estrita. O DOM gerado será consumido visualmente por humanos e semanticamente por outras IAs durante auditorias. O código deve refletir a hierarquia exata da informação.