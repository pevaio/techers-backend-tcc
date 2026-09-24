# PEVANOTA

# 1. Propósito

O PEVANOTA é um **bloco de notas amplificado**. O projeto conta com funcionalidades adicionais em relação a um programa tradicional, mas sem exagero.

# 2. Requisitos Funcionais

Descrevem as funcionalidades diretas do sistema, ou seja, o que ele deve fazer.

| **ID** | **Título** | **Descrição** |
| --- | --- | --- |
| **RF01** | **Escrita** | O sistema deve contar com edição de texto. |
| **RF02** | **Parsing** | O sistema deve ser capaz de traduzir o Markdown. |
| **RF03** | **Salvamento** | O sistema deve salvar as notas automaticamente. |
| **RF04** | **Pastas** | O sistema deve permitir que as notas sejam armazenadas em pastas. |
| **RF05** | **Wikilinks** | O sistema deve contar com suporte a Wikilinks. |

# 3. Modelagem de Casos de Uso

Abaixo, detalhamos as interações entre os atores e o sistema para garantir que os requisitos sejam implementáveis e sem ambiguidades.

### UC01: Escrever Nota

- **Ator Principal:** Usuário.
- **Precondição:** O usuário tem acesso ao serviço.
- **Fluxo Principal:**
    1. O usuário cria e nomeia uma nota em Markdown.
    2. O usuário escreve o conteúdo da nota.
    3. O sistema traduz a nota para texto formatado em tempo real (WYSIWYG).
    4. O sistema salva a nota automaticamente.
- **Fluxo de Exceção (Nota Duplicada):**
    - No passo 1, se o usuário já tiver uma nota com o mesmo nome, o sistema exibe um erro exigindo que o nome da nota seja trocado.    
