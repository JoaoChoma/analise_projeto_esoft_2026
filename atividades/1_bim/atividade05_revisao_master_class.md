# Lista 05 --- Análise e projeto de Software

# Exercício 1 

Uma empresa desenvolve seus sistemas sem um processo definido. Cada
desenvolvedor conversa diretamente com o cliente, interpreta as
necessidades e implementa as funcionalidades da maneira que considera
mais adequada. Não existe documentação dos requisitos e poucas
funcionalidades possuem testes. Quando um desenvolvedor deixa a equipe,
parte do conhecimento sobre o sistema também é perdida.

Responda:

**a)** Quais problemas podem surgir devido a essa forma de
desenvolvimento?

**b)** Explique o que é um **processo de desenvolvimento de software**.

**c)** Cite e explique pelo menos **quatro atividades** que poderiam
fazer parte do processo adotado pela empresa.

**d)** Explique como essas atividades poderiam reduzir os problemas
apresentados no enunciado.

------------------------------------------------------------------------

# Exercício 2

Considere um sistema de locação de veículos.

Classifique cada afirmação como:

-   Regra de Negócio (RN);
-   Requisito Funcional (RF);
-   Requisito Não Funcional (RNF).

Justifique sua classificação.

**a)** Clientes com habilitação vencida não podem alugar veículos.

**b)** O sistema deve permitir que o atendente registre uma locação.

**c)** Uma locação deve possuir período mínimo de uma diária.

**d)** O sistema deve apresentar os veículos disponíveis em até 3
segundos.

**e)** O sistema deve permitir registrar a devolução de um veículo.

**f)** Clientes menores de 21 anos não podem alugar veículos da
categoria premium.

**g)** O sistema deve exigir autenticação dos funcionários.

Depois responda:

> Qual é a principal diferença entre uma Regra de Negócio e um Requisito
> de Software?

------------------------------------------------------------------------

# Exercício 3

Considere o seguinte sistema:

> Uma academia permite que alunos agendem aulas coletivas. Cada aula
> possui um limite máximo de participantes. Um aluno não pode realizar
> duas reservas para aulas que ocorram no mesmo horário. Alunos com
> mensalidade vencida não podem realizar novos agendamentos. O sistema
> deve permitir que o aluno consulte as aulas disponíveis, realize uma
> reserva e cancele uma reserva. A consulta das aulas disponíveis deve
> apresentar o resultado em até dois segundos.

A partir da descrição:

**a)** Identifique as **Regras de Negócio** e numere-as como `RN01`,
`RN02` etc.

**b)** Identifique os **Requisitos Funcionais** e numere-os como `RF01`,
`RF02` etc.

**c)** Identifique os **Requisitos Não Funcionais**, classifique seu
tipo e justifique.

**d)** Explique como uma Regra de Negócio pode influenciar um ou mais
Requisitos Funcionais.

------------------------------------------------------------------------

# Exercício 4

Considere um sistema de biblioteca com as seguintes funcionalidades:

> Bibliotecários registram empréstimos e devoluções. Alunos consultam
> livros disponíveis e seu histórico de empréstimos. O coordenador da
> biblioteca pode cadastrar novos livros e bloquear usuários. O sistema
> também consulta um serviço externo de autenticação para validar o
> acesso dos usuários.

Responda:

**a)** Identifique os possíveis atores.

**b)** Identifique os principais Casos de Uso.

**c)** Relacione cada ator aos Casos de Uso com os quais interage.

**d)** O serviço externo de autenticação pode ser considerado um ator?
Justifique.

**e)** Explique por que itens como **"clicar no botão Emprestar"**,
**"abrir a tela de livros"** e **"digitar matrícula"** normalmente não
devem ser modelados como Casos de Uso.

------------------------------------------------------------------------

# Exercício 5

Considere:

``` text
UC01 — Fazer Reserva

Ator: Cliente

1. Cliente abre a tela.
2. Cliente escolhe.
3. Sistema verifica.
4. Cliente confirma.
5. Sistema salva.
6. Sistema finaliza.
```

Responda:

**a)** Identifique pelo menos **cinco problemas** nessa especificação.

**b)** Explique por que expressões como "sistema verifica", "sistema
salva" e "sistema finaliza" podem prejudicar a compreensão.

**c)** Quais elementos importantes de uma especificação de Caso de Uso
estão ausentes?

**d)** Reescreva o fluxo principal tornando as ações mais claras.

------------------------------------------------------------------------

# Exercício 6

Considere um sistema de hotel.

Regras de Negócio:

``` text
RN01 — Uma reserva somente pode ser realizada para um quarto disponível.

RN02 — A data de saída deve ser posterior à data de entrada.

RN03 — Um cliente não pode possuir duas reservas para o mesmo período.

RN04 — Reservas podem ser canceladas sem cobrança até 24 horas antes do check-in.
```

Requisito:

``` text
RF01 — O sistema deve permitir que o atendente registre reservas.
```

Elabore a especificação do:

``` text
UC01 — Registrar Reserva
```

A especificação deve conter:

-   objetivo;
-   ator principal;
-   pré-condições;
-   pós-condições;
-   fluxo principal;
-   pelo menos um fluxo alternativo;
-   pelo menos um fluxo de exceção;
-   Regras de Negócio relacionadas;
-   Requisitos relacionados.

Ao final, explique:

> Como podemos verificar se o Caso de Uso está coerente com as Regras de
> Negócio?

------------------------------------------------------------------------

# Exercício 7

Considere um sistema de restaurante:

> O atendente pode registrar pedidos e cancelar pedidos. O cozinheiro
> pode consultar os pedidos que precisam ser preparados e marcar um
> pedido como pronto. O caixa pode registrar o pagamento. O gerente pode
> consultar relatórios de vendas.

**a)** Identifique os atores.

**b)** Identifique os Casos de Uso.

**c)** Construa o **Diagrama de Casos de Uso**, representando as
associações entre atores e funcionalidades.

**d)** Explique o que representa a fronteira do sistema.

**e)** Explique a diferença entre:

``` text
ATOR
```

e:

``` text
CASO DE USO
```

**f)** O Diagrama de Casos de Uso mostra a ordem em que as operações
acontecem? Justifique.

------------------------------------------------------------------------

# Exercício 8

Considere o seguinte cenário:

``` text
UC02 — Consultar Produto

1. Vendedor informa o código do produto.
2. Sistema recebe o código.
3. Sistema consulta o produto.
4. Sistema obtém os dados do produto.
5. Sistema apresenta os dados ao vendedor.
```

Considere os participantes:

``` text
Vendedor
TelaProduto
ProdutoController
ProdutoService
ProdutoRepository
```

**a)** Construa um **Diagrama de Sequência** para o cenário.

**b)** Indique qual participante deveria receber inicialmente a
interação do ator.

**c)** Qual participante poderia ser responsável por coordenar a
operação?

**d)** Qual participante seria responsável pela consulta/persistência
dos dados?

**e)** Explique por que a ordem vertical das mensagens é importante em
um Diagrama de Sequência.

------------------------------------------------------------------------

# Exercício 9

Considere o Caso de Uso:

``` text
UC03 — Realizar Saque
```

Fluxo:

``` text
1. Cliente informa o valor do saque.
2. Sistema consulta o saldo da conta.
3. Sistema verifica se existe saldo suficiente.
4. Se houver saldo, o sistema realiza o débito.
5. Sistema registra a movimentação.
6. Sistema informa que o saque foi realizado.

Caso o saldo seja insuficiente:
7. Sistema informa que a operação não pode ser realizada.
```

Considere os participantes:

``` text
Cliente
TelaSaque
SaqueController
ContaService
MovimentacaoRepository
```

Construa um **Diagrama de Sequência** contendo:

-   ator;
-   participantes;
-   mensagens;
-   consulta/validação do saldo;
-   fragmento `alt`;
-   condição `[saldo suficiente]`;
-   condição `[saldo insuficiente]`;
-   registro da movimentação;
-   retorno do resultado ao cliente.

Depois explique:

> Qual é a finalidade do fragmento `alt` em um Diagrama de Sequência?

------------------------------------------------------------------------

# Exercício 10

Considere o seguinte problema:

> Uma clínica permite que pacientes agendem consultas. O paciente
> escolhe um médico, uma data e um horário. Um médico não pode possuir
> duas consultas no mesmo horário. Somente horários disponíveis podem
> ser agendados. O sistema deve permitir que o atendente registre
> consultas e cancelamentos. O paciente pode consultar suas consultas
> agendadas. A consulta dos horários disponíveis deve ser realizada em
> até dois segundos.

Realize as seguintes atividades:

## Parte A --- Regras e Requisitos

**a)** Identifique as Regras de Negócio.

**b)** Identifique os Requisitos Funcionais.

**c)** Identifique o Requisito Não Funcional e classifique-o.

## Parte B --- Caso de Uso

Para:

``` text
UC — Agendar Consulta
```

defina:

-   ator principal;
-   objetivo;
-   pré-condições;
-   fluxo principal;
-   pelo menos um fluxo alternativo ou de exceção;
-   pós-condição.

## Parte C --- Diagrama de Casos de Uso

Construa um Diagrama de Casos de Uso contendo os atores e
funcionalidades identificados.

## Parte D --- Diagrama de Sequência

Considere:

``` text
Atendente
TelaAgendamento
AgendamentoController
AgendaService
ConsultaRepository
```

Construa o Diagrama de Sequência para **Agendar Consulta**.

Utilize um fragmento `alt` para representar:

``` text
[horário disponível]

[horário indisponível]
```

## Parte E --- Integração dos conceitos

Explique a diferença de finalidade entre os seguintes artefatos:

``` text
REGRA DE NEGÓCIO
        ↓
REQUISITO
        ↓
CASO DE USO
        ↓
DIAGRAMA DE CASOS DE USO
        ↓
DIAGRAMA DE SEQUÊNCIA
```

Na resposta, explique **qual pergunta cada artefato ajuda a responder
durante a análise e o projeto do software**.