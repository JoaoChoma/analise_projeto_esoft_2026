# Lista Master Class — Diagrama de Classes UML e Organização da Arquitetura de Software


## 1. Objetivo da atividade

Desenvolver a capacidade de transformar os artefatos produzidos durante a análise em uma proposta de estrutura e organização para implementação.

```text
REGRAS DE NEGÓCIO → REQUISITOS → CASOS DE USO
→ DIAGRAMA DE SEQUÊNCIA → IDENTIFICAÇÃO DE CLASSES
→ DEFINIÇÃO DE RESPONSABILIDADES → DIAGRAMA DE CLASSES
→ ORGANIZAÇÃO DA ARQUITETURA → ESTRUTURA DE DIRETÓRIOS
→ IMPLEMENTAÇÃO
```

**Objetivo central:** compreender como as decisões de análise e projeto orientam a identificação das classes, a distribuição de responsabilidades e a organização do código-fonte.

---

# Parte 1 — Fundamentos da modelagem estrutural

## Exercício 1 — Modelagem comportamental × estrutural

Uma equipe produziu um Diagrama de Casos de Uso e um Diagrama de Sequência. Um desenvolvedor afirmou:

> "Já sabemos quais funcionalidades o sistema possui e como os objetos interagem. Portanto, não precisamos de um Diagrama de Classes."

Responda:

a) Qual é a finalidade do Diagrama de Casos de Uso?  
b) Qual é a finalidade do Diagrama de Sequência?  
c) Qual é a finalidade do Diagrama de Classes?  
d) Quais informações estruturais não são necessariamente apresentadas em um Diagrama de Sequência?  
e) Explique como os três diagramas podem se complementar.

## Exercício 2 — Identificação de classes

> Uma biblioteca possui livros, exemplares físicos, alunos e empréstimos. Um livro pode possuir vários exemplares. Um aluno pode realizar vários empréstimos, mas cada empréstimo pertence a um único aluno e está associado a um exemplar. O sistema registra a data do empréstimo, a data prevista de devolução e a data efetiva da devolução.

Identifique: (1) possíveis classes do domínio; (2) atributos; (3) operações; (4) relacionamentos.

| Classe | Atributos | Operações | Responsabilidade |
|---|---|---|---|
| | | | |
| | | | |

**Discussão:** todo substantivo encontrado na descrição deve necessariamente se transformar em classe? Justifique.

## Exercício 3 — Anatomia de uma classe UML

```text
+-------------------------------------+
|               Produto               |
+-------------------------------------+
| - id: Long                          |
| - nome: String                      |
| - preco: Decimal                    |
| - quantidade: Integer               |
+-------------------------------------+
| + calcularSubtotal(qtd): Decimal    |
| + verificarEstoque(qtd): Boolean    |
| + atualizarPreco(valor): void       |
+-------------------------------------+
```

Responda:

a) O que representam os três compartimentos?  
b) Qual é a diferença entre atributos e operações?  
c) O que significam `+` e `-`?  
d) O que representa o tipo após os dois-pontos?  
e) Por que documentar operações, e não apenas atributos?  
f) Explique a relação entre visibilidade e encapsulamento.

---

# Parte 2 — Relacionamentos entre classes

## Exercício 4 — Associação e multiplicidade

Considere um sistema acadêmico:

- Um professor pode ministrar várias turmas.
- Cada turma possui um professor responsável.
- Uma turma possui vários estudantes.
- Um estudante pode participar de várias turmas.
- Cada turma pertence a uma disciplina.
- Uma disciplina pode ser oferecida em várias turmas.

Construa um Diagrama de Classes com `Professor`, `Turma`, `Estudante` e `Disciplina`, incluindo relacionamentos e multiplicidades.

Explique o significado de `1`, `0..1`, `0..*` e `1..*` e a importância das multiplicidades para a implementação.

## Exercício 5 — Associação, agregação e composição

**Cenário A:** uma universidade possui departamentos. Um departamento pode continuar existindo mesmo que seja transferido para outra universidade.

**Cenário B:** um pedido possui itens. Cada item pertence exclusivamente àquele pedido e não possui significado independente dele.

**Cenário C:** um professor ministra disciplinas.

Responda:

a) Qual relacionamento é mais adequado em cada cenário?  
b) Diferencie associação, agregação e composição.  
c) O que ocorre com as partes de uma composição quando o objeto composto deixa de existir?  
d) Por que não usar composição apenas porque uma classe referencia outra?

Construa um pequeno Diagrama de Classes para os três cenários. Justifique com base em identidade, propriedade e ciclo de vida dos objetos.

## Exercício 6 — Herança e generalização

Considere `Pagamento`, `PagamentoPix`, `PagamentoCartao` e `PagamentoBoleto`. Todos possuem identificador, valor, data e situação, mas cada modalidade possui características próprias.

Responda:

a) Quais atributos pertencem à superclasse?  
b) Quais comportamentos podem ser compartilhados?  
c) Quais são específicos?  
d) Construa o diagrama com generalização.  
e) Diferencie herança e composição.  
f) Quando a herança pode prejudicar a evolução?

---

# Parte 3 — Responsabilidades e qualidade do projeto

## Exercício 7 — Classes anêmicas e responsabilidades

```java
public class Pedido {
    private Long id;
    private double valorTotal;
    private String status;
    // getters e setters
}
```

```java
public class PedidoService {
    public double calcularTotal(Pedido pedido) { /* ... */ }
    public void cancelarPedido(Pedido pedido) { /* ... */ }
    public void aplicarDesconto(Pedido pedido) { /* ... */ }
}
```

Responda:

a) Qual é a responsabilidade de `Pedido`?  
b) Qual é a de `PedidoService`?  
c) Quais operações podem ser comportamentos próprios do domínio `Pedido`?  
d) Por que concentrar todas as regras em uma única `Service` pode ser problemático?  
e) Proponha uma distribuição de responsabilidades e represente-a em UML.

**Importante:** nem toda regra precisa estar em uma entidade; considere serviços de domínio e de aplicação quando apropriado.

## Exercício 8 — Coesão e acoplamento

```text
SistemaManager
    cadastrarCliente()
    atualizarProduto()
    calcularFrete()
    registrarPagamento()
    emitirRelatorio()
    autenticarUsuario()
    enviarEmail()
```

Responda:

a) Qual problema de projeto a classe apresenta?  
b) Explique coesão.  
c) Explique acoplamento.  
d) Como responsabilidades mal distribuídas afetam manutenção e testes?  
e) Reorganize as operações em classes específicas.  
f) Construa um Diagrama de Classes da nova organização.

## Exercício 9 — Da sequência para as classes

```text
Cliente → TelaPedido → PedidoController → PedidoService → PedidoRepository
```

O sistema deve registrar pedidos.

Responda:

a) Quais participantes poderiam virar classes concretas?  
b) Quais responsabilidades pertencem à interface, aplicação, domínio ou infraestrutura?  
c) Quais operações podem ser identificadas a partir das mensagens?  
d) O Diagrama de Sequência permite descobrir atributos? Explique.  
e) Construa um Diagrama de Classes para o cenário.  
f) Por que nem todo participante da sequência aparece no Diagrama de Classes de domínio?

---

# Parte 4 — Arquitetura de software

## Exercício 10 — Organização em camadas

Classifique as responsabilidades em **Apresentação/Interface**, **Aplicação**, **Domínio** ou **Infraestrutura**:

1. Receber requisições HTTP.
2. Validar regras de negócio.
3. Coordenar a execução de um Caso de Uso.
4. Consultar registros no banco de dados.
5. Representar uma entidade do domínio.
6. Converter dados recebidos em objetos.
7. Persistir alterações.
8. Retornar uma resposta HTTP.

Responda:

a) Qual a finalidade de cada camada?  
b) Quais classes poderiam existir em cada uma?  
c) Diferencie camada lógica e diretório físico.  
d) A arquitetura exige quatro diretórios?  
e) Como a separação ajuda a manutenção?

## Exercício 11 — Controller, Service, Entity e Repository

Considere `ProdutoController`, `ProdutoService`, `Produto` e `ProdutoRepository`.

Responda:

a) Responsabilidade de cada classe.  
b) Quem recebe a requisição HTTP?  
c) Quem coordena o Caso de Uso?  
d) Quem representa conceitos e comportamentos do domínio?  
e) Quem oferece acesso aos dados?  
f) Por que a entidade não deveria depender do controlador HTTP?  
g) Construa um Diagrama de Classes com dependências relevantes.

**Atenção:** diferencie o contrato de repositório de sua implementação concreta na infraestrutura.

## Exercício 12 — Dependências inadequadas

```text
ProdutoController → ProdutoRepository → Banco de Dados
```

O controlador também calcula descontos, valida estoque e determina regras de preço.

Responda:

a) Quais problemas existem?  
b) Acesso direto ao repositório pelo controlador é sempre incorreto? Justifique.  
c) Como reorganizar a arquitetura?  
d) O que pertence ao domínio?  
e) O que pertence à aplicação?  
f) Construa um Diagrama de Classes da solução.

---

# Parte 5 — Organização de diretórios e documentação

## Exercício 13 — Estrutura de diretórios

Uma equipe iniciou o projeto assim:

```text
src/main/java/sistema/
├── Cliente.java
├── Produto.java
├── Pedido.java
├── ClienteController.java
├── ProdutoController.java
├── PedidoController.java
├── ClienteService.java
├── ProdutoService.java
├── PedidoService.java
├── ClienteRepository.java
├── ProdutoRepository.java
└── PedidoRepository.java
```

Responda:

a) Quais dificuldades surgem com o crescimento?  
b) Proponha organização por camadas.  
c) Proponha organização por funcionalidades/módulos.  
d) Compare as propostas.  
e) Qual facilita localizar tudo relacionado a `Registrar Pedido`?  
f) Justifique a escolha para um sistema médio.

## Exercício 14 — Organização por camadas × funcionalidades

### Estrutura A — Por camadas

```text
src/main/java/br/edu/sistema/
├── controller/
│   ├── ClienteController.java
│   └── PedidoController.java
├── service/
│   ├── ClienteService.java
│   └── PedidoService.java
├── repository/
│   ├── ClienteRepository.java
│   └── PedidoRepository.java
└── model/
    ├── Cliente.java
    └── Pedido.java
```

### Estrutura B — Por funcionalidades

```text
src/main/java/br/edu/sistema/
├── cliente/
│   ├── Cliente.java
│   ├── ClienteController.java
│   ├── ClienteService.java
│   └── ClienteRepository.java
└── pedido/
    ├── Pedido.java
    ├── PedidoController.java
    ├── PedidoService.java
    └── PedidoRepository.java
```

Responda:

a) Qual o critério de cada organização?  
b) Vantagens e desvantagens?  
c) Como afetam a compreensão da arquitetura?  
d) Diretórios garantem boa arquitetura?  
e) Como combinar módulos por funcionalidade com responsabilidades internas?

## Exercício 15 — Documentação das classes

```java
public class PedidoService {
    public void registrarPedido(Pedido pedido) { /* ... */ }
}
```

Documente nome, responsabilidade, operações públicas, parâmetros, resultados esperados, dependências, RN, RF e UC relacionados.

| Campo | Descrição |
|---|---|
| Classe | |
| Responsabilidade | |
| Operações | |
| Dependências | |
| RN relacionadas | |
| RF relacionadas | |
| UC relacionados | |

**Discussão:** qual a diferença entre documentar uma classe e documentar um Caso de Uso?

---

# Parte 6 — Integração entre análise, projeto e arquitetura

## Exercício 16 — Rastreabilidade até as classes

```text
RN01 — Um pedido não pode ser confirmado quando algum produto estiver indisponível.
RF01 — O sistema deve permitir registrar pedidos.
UC01 — Registrar Pedido.
```

Construa:

```text
RN01 → RF01 → UC01 → DIAGRAMA DE SEQUÊNCIA
→ CLASSES E OPERAÇÕES → MÓDULOS/DIRETÓRIOS
```

Responda:

a) Quais classes são necessárias?  
b) Quem verifica disponibilidade?  
c) Quem confirma o pedido?  
d) Como a RN01 aparece na sequência?  
e) Como documentar a relação entre RN01 e as classes?

## Exercício 17 — Arquitetura de um sistema de estoque

Funcionalidades: cadastrar produtos; registrar entrada e saída de mercadorias; consultar estoque; emitir relatório de movimentações.

```text
RN01 — O estoque não pode ficar negativo.
RN02 — Toda entrada deve gerar uma movimentação.
RN03 — Toda saída deve gerar uma movimentação.
RN04 — Somente usuários autorizados podem registrar movimentações.
```

Realize:

a) Identifique classes do domínio.  
b) Defina atributos e operações.  
c) Identifique associações e multiplicidades.  
d) Construa Diagrama de Classes do domínio.  
e) Identifique componentes de aplicação.  
f) Identifique infraestrutura.  
g) Proponha diretórios.  
h) Explique onde cada RN é aplicada.

---

# Parte 7 — Master Class: projeto completo

## Exercício 18 — Do Caso de Uso à arquitetura

### Sistema de Gerenciamento de Pedidos

Uma empresa deseja gerenciar clientes, produtos e pedidos. O sistema deve permitir cadastrar clientes e produtos, consultar produtos, registrar pedidos, adicionar produtos, calcular total, confirmar e cancelar pedidos e consultar histórico.

### Regras de Negócio

**RN01:** Um pedido deve estar associado a um cliente.  
**RN02:** Um pedido deve possuir pelo menos um item para ser confirmado.  
**RN03:** Produtos sem estoque suficiente não podem ser adicionados ao pedido.  
**RN04:** O total corresponde à soma dos subtotais, considerando descontos autorizados.  
**RN05:** Pedidos confirmados não podem ter seus itens alterados.  
**RN06:** Somente pedidos ainda não enviados podem ser cancelados.

### Etapa 1 — Análise

Identifique requisitos funcionais, requisitos não funcionais relevantes, atores e Casos de Uso.

### Etapa 2 — Especificação

Especifique `UC01 — Registrar Pedido` com objetivo, ator, pré-condições, pós-condições, fluxo principal, alternativas, exceções, RN e RF relacionados.

### Etapa 3 — Diagrama de Sequência

Modele o registro de pedido com `Vendedor`, `TelaPedido`, `PedidoController`, `PedidoService`, `EstoqueService` e `PedidoRepository` (ajuste participantes se necessário). Use `alt` para disponibilidade, `loop` para vários produtos e mensagens de confirmação e persistência.

### Etapa 4 — Identificação das classes

Identifique classes do domínio, aplicação, interfaces e infraestrutura.

| Classe | Responsabilidade | Atributos | Operações |
|---|---|---|---|
| | | | |
| | | | |

### Etapa 5 — Diagrama de Classes

Represente classes, atributos, operações, visibilidade, relacionamentos, multiplicidades e dependências relevantes.

### Etapa 6 — Arquitetura

Organize as responsabilidades em **Apresentação**, **Aplicação**, **Domínio** e **Infraestrutura**. Defina classes, dependências permitidas e dependências a evitar. Explique que a divisão em camadas não impõe necessariamente dependências unidirecionais entre todas elas.

### Etapa 7 — Estrutura de diretórios

Complete a proposta Java:

```text
src/main/java/br/edu/sistema/
├── cliente/
├── produto/
└── pedido/
```

Identifique classes, interfaces, serviços, controladores, repositórios e DTOs quando necessários.

### Etapa 8 — Documentação arquitetural

Produza documento com:

1. Visão geral do sistema.
2. Decisões arquiteturais e justificativas.
3. Árvore de diretórios comentada.
4. Responsabilidades das principais classes.
5. Diagramas de Classes e Sequência.
6. Rastreabilidade RN–RF–UC–classes.
7. Regras de dependência entre módulos.

---