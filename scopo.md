# mooOS (my opinion on OS)

# 1. Propósito

O **mooOS**, como indicado pelo seu acrônimo (*my opinion on Open Source*), é um **sistema de avaliações de programas de código aberto conduzido pelos usuários**. O projeto visa facilitar a escolha de bons softwares e encorajar a sua utilização através de notas e críticas construtivas da comunidade.

# 2. Requisitos Funcionais

Descrevem as funcionalidades diretas do sistema, ou seja, o que ele deve fazer.

| **ID** | **Título** | **Descrição** |
| --- | --- | --- |
| **RF01** | **Usuários** | O sistema deve permitir o cadastro, leitura, atualização e exclusão (CRUD) de usuários comuns e moderadores. |
| **RF02** | **Catálogo** | O sistema deve permitir o registo de programas de código aberto, contendo nome, descrição, link do repositório e categoria. |
| **RF03** | **Avaliação** | O sistema deve permitir que os utilizadores atribuam notas (de 1 a 5) e escrevam críticas de texto sobre os softwares. |
| **RF04** | **Descoberta** | O sistema deve exibir listas de softwares mais bem classificados, tendências ou filtrados por categorias. |
| **RF05** | **Moderação** | O sistema deve permitir que moderadores removam avaliações ofensivas ou que infrinjam as diretrizes. |
| **RF06** | **Métricas** | O sistema deve calcular automaticamente a média de notas de cada programa por período e total. |
| **RF07** | **Edição** | O sistema deve permitir que um utilizador altere ou remova a sua própria avaliação prévia. |

# 3. Requisitos Não Funcionais (RNF)

Expressam as restrições, limites e qualidades específicas que o sistema deve atender.

- **RNF01 (Software):** O sistema deve ser desenvolvido obrigatoriamente para ambiente Node.js utilizando o framework Express.
- **RNF02 (Segurança):** Apenas utilizadores autenticados podem submeter avaliações, e apenas moderadores podem gerir denúncias.

# 5. Modelagem de Casos de Uso

Abaixo, detalhamos as interações entre os atores e o sistema para garantir que os requisitos sejam implementáveis e sem ambiguidades.

### UC01: Avaliar Software

- **Ator Principal:** Utilizador Autenticado.
- **Precondição:** O utilizador deve estar logado e o software pretendido deve estar previamente registrado no catálogo.
- **Fluxo Principal:**
    1. O utilizador solicita a criação de uma avaliação na página do software.
    2. O sistema solicita os dados (Nota de 1 a 5 e comentário opcional).
    3. O utilizador insere as informações.
    4. O sistema valida se o utilizador já possui uma avaliação para aquele software.
    5. O sistema confirma a submissão, recalcula a média do programa e guarda no banco de dados.
- **Fluxo de Exceção (Avaliação Duplicada):**
    - No passo 4, se o utilizador já tiver avaliado o software, o sistema emite um erro informando que ele deve editar a avaliação existente em vez de criar uma nova.

### UC02: Moderar Avaliação 

- **Ator Principal:** Moderador.
- **Precondição:** Deve haver pelo menos uma avaliação que infrinja as diretrizes.
- **Fluxo Principal:**
    1. O moderador vê as avaliações.
    2. O moderador analisa o conteúdo e opta por remover a avaliação.
    3. O moderador finaliza a ação de moderação.
    4. O sistema altera o status da avaliação para "Removida por Moderação" e recalcula a nota média global do software correspondente.

### UC03: Fazer Login

- **Ator Principal:** Usuário Não Autenticado.
- **Precondição:** O usuário deve conseguir acessar o sistema.
- **Fluxo Principal:**
    1. O usuário, ainda não autenticado, preenche um formulário com nome de usuário e senha.
    2. O usuário insere esses dados em um outro formulário, dessa vez de login.