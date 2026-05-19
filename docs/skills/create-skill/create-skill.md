# Skill: Criação de Novas Skills

## Contexto
Esta skill deve ser utilizada por agentes de IA sempre que o usuário solicitar a criação de uma nova diretriz, regra ou "skill" para o projeto. O objetivo é garantir que todas as skills sigam um padrão uniforme e sejam facilmente compreendidas pelo modelo.

## Regras de Localização e Nomenclatura
1. **Estrutura de Pastas:** Todas as novas skills **DEVEM** ser criadas em sua própria pasta dentro do diretório `/docs/skills/` (ex: `/docs/skills/minha-skill/`).
2. **Nomenclatura do Arquivo:** Dentro da pasta, o arquivo principal da skill deve ser um `.md` e possuir o **exato mesmo nome** da pasta (ex: `/docs/skills/minha-skill/minha-skill.md`). Ambos os nomes devem estar em `kebab-case`.
3. **Arquivos Auxiliares:** Caso a skill necessite de arquivos adicionais (como exemplos em JSON, scripts auxiliares ou templates), eles devem ser armazenados dentro desta mesma pasta da skill.

## Template Padrão para Novas Skills
Ao criar uma nova skill, a IA deve estruturar o documento utilizando os seguintes tópicos:

### 1. Propósito / Gatilho
Descrever em qual cenário ou para qual tipo de tarefa aquela skill deve ser lembrada ou ativada (ex: "Sempre que for criar um componente React", "Sempre que for gerar um artefato").

### 2. Regras e Diretrizes
Uma lista clara e objetiva (preferencialmente numerada ou em bullet points) com as regras que devem ser seguidas. 

### 3. Exemplos (Crucial para IAs)
IAs aprendem muito bem com exemplos. Toda skill deve conter exemplos contrastantes, se aplicável:
* **✅ Correto / Recomendado:** [Exemplo do padrão esperado]
* **❌ Incorreto / Evitar:** [Exemplo do que não fazer]

### 4. Restrições (Opcional)
Ações proibidas ou limites estritos relacionados à skill.

## Comportamento Esperado da IA ao Criar a Skill
1. Elaborar o conteúdo seguindo o template acima.
2. Criar o arquivo no caminho correto.
3. Apresentar um resumo para o usuário, permitindo que ele refine as regras se necessário.
