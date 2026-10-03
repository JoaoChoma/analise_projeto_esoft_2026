# Lista de Exercícios --- Análise e Projeto de Software

## Objetivo

Revisar e aplicar os conceitos trabalhados até o momento:

-   Regras de Negócio;
-   Requisitos Funcionais e Não Funcionais;
-   Casos de Uso;
-   validação e completude de Casos de Uso;
-   rastreabilidade;
-   fluxos principais, alternativos e de exceção;
-   Diagrama de Sequência;
-   distribuição de responsabilidades.

Progressão:

``` text
COMPREENDER → ANALISAR → CORRIGIR → MODELAR → INTEGRAR
```

------------------------------------------------------------------------

# Parte 1 --- Discussão e compreensão dos conceitos

## Exercício 1 --- Regra de Negócio × Requisito

Explique a diferença entre uma **Regra de Negócio** e um **Requisito de
Software**.

Classifique e justifique:

a)  Todo empréstimo deve possuir prazo máximo de 30 dias.\
b)  O sistema deve permitir registrar um empréstimo.\
c)  Usuários administradores devem utilizar autenticação em dois
    fatores.\
d)  Clientes com pagamentos vencidos não podem realizar novas compras.\
e)  O sistema deve responder às consultas em até 2 segundos.

------------------------------------------------------------------------

## Exercício 2 --- Requisitos Funcionais e Não Funcionais

Considere um sistema de biblioteca. Classifique os requisitos e, quando
forem não funcionais, indique sua categoria:

-   permitir empréstimo de livros;
-   permitir consulta ao catálogo;
-   suportar 500 usuários simultâneos;
-   exigir autenticação para operações administrativas;
-   funcionar nos principais navegadores atuais;
-   apresentar resultados de pesquisa em até 2 segundos.

Depois discuta:

> Por que requisitos não funcionais não devem ser tratados como
> requisitos "menos importantes"?

------------------------------------------------------------------------

## Exercício 3 --- Por que Casos de Uso?

Um desenvolvedor afirma:

> "Se já temos os requisitos funcionais, não precisamos de Casos de
> Uso."

Explique por que essa afirmação é problemática.

> O que o Caso de Uso acrescenta à descrição de um requisito funcional?

------------------------------------------------------------------------

## Exercício 4 --- Caso de Uso não é tela

Analise:

``` text
Abrir Tela de Cliente
Clicar em Salvar
Cadastrar Cliente
Digitar CPF
Registrar Pedido
Selecionar Produto
Cancelar Pedido
```

Identifique quais são bons candidatos a **Casos de Uso** e quais parecem
ações de interface ou passos internos. Justifique.

------------------------------------------------------------------------

## Exercício 5 --- Atores

Em um sistema acadêmico existem estudantes, professores, coordenadores,
funcionários e integração com um serviço externo de autenticação.

Responda:

a)  Quais podem ser atores?\
b)  Um sistema externo pode ser ator?\
c)  Uma pessoa pode representar mais de um ator?\
d)  "Banco de Dados" deveria normalmente aparecer como ator? Por quê?

------------------------------------------------------------------------

# Parte 2 --- Identificação de Regras, Requisitos e Casos de Uso

## Exercício 6 --- Sistema de estacionamento

> Um estacionamento permite que clientes estacionem veículos. Na
> entrada, a placa e o horário são registrados. Na saída, o sistema
> calcula o valor de acordo com o período de permanência. Clientes
> conveniados recebem 20% de desconto. O atendente registra o pagamento
> e libera a saída. O sistema deve manter o histórico das operações.

Identifique:

-   regras de negócio;
-   requisitos funcionais;
-   possíveis requisitos não funcionais;
-   atores;
-   possíveis Casos de Uso.

Organize usando:

``` text
RN01, RN02...
RF01, RF02...
RNF01, RNF02...
UC01, UC02...
```

------------------------------------------------------------------------

## Exercício 7 --- Sistema acadêmico

Considere:

``` text
RN01 — A nota deve estar entre 0 e 100.
RN02 — Somente o professor responsável pela turma pode alterar notas.
RN03 — Após o fechamento do período, notas não podem ser alteradas.
RN04 — Estudantes com frequência inferior a 75% são reprovados por frequência.
```

Derive os **Requisitos Funcionais** necessários e indique quais **Casos
de Uso** seriam afetados.

------------------------------------------------------------------------

# Parte 3 --- Analisando Casos de Uso

## Exercício 8 --- Encontre os problemas

``` text
UC01 — Cadastro

Ator: Usuário

1. Abrir a tela.
2. Digitar os dados.
3. Clicar no botão.
4. Sistema verifica.
5. Sistema salva.
6. Finaliza.
```

Identifique pelo menos **seis problemas** e reescreva o Caso de Uso.

------------------------------------------------------------------------

## Exercício 9 --- Caso de Uso incompleto

``` text
UC05 — Realizar Empréstimo

Ator: Bibliotecário

1. Bibliotecário informa o aluno.
2. Sistema localiza o aluno.
3. Bibliotecário informa o livro.
4. Sistema registra o empréstimo.
```

Regras:

``` text
RN01 — Alunos com empréstimos vencidos não podem realizar novos empréstimos.
RN02 — Um aluno pode possuir no máximo 5 livros emprestados simultaneamente.
RN03 — Livros indisponíveis não podem ser emprestados.
RN04 — O prazo normal do empréstimo é de 14 dias.
```

Analise se o Caso de Uso respeita as regras, identifique o que falta e
produza uma versão corrigida.

------------------------------------------------------------------------

# Parte 4 --- Fluxos Alternativos e Exceções

## Exercício 10 --- O happy path não é suficiente

Considere:

``` text
UC — Realizar Compra

1. Cliente seleciona os produtos.
2. Cliente informa os dados de entrega.
3. Sistema calcula o valor.
4. Cliente informa os dados de pagamento.
5. Sistema processa o pagamento.
6. Sistema registra o pedido.
```

Identifique:

-   3 fluxos alternativos;
-   3 fluxos de exceção.

Para cada um, indique em qual passo ele ocorre.

------------------------------------------------------------------------

## Exercício 11 --- Fluxo alternativo ou exceção?

Classifique e justifique:

a)  Cliente escolhe PIX em vez de cartão.\
b)  Cartão é recusado.\
c)  Cliente adiciona outro produto.\
d)  Produto fica sem estoque antes da confirmação.\
e)  Cliente informa cupom de desconto.\
f)  Cupom está vencido.

Depois discuta:

> Todas essas situações precisam estar documentadas no mesmo Caso de
> Uso?

------------------------------------------------------------------------

# Parte 5 --- Testando a qualidade de um Caso de Uso

## Exercício 12 --- Revisão por checklist

Escolha um Caso de Uso da equipe e aplique:

``` text
□ Identificador
□ Nome orientado a objetivo
□ Ator principal
□ Atores secundários
□ Objetivo
□ Gatilho
□ Pré-condições
□ Pós-condições
□ Fluxo principal
□ Fluxos alternativos
□ Exceções
□ Regras relacionadas
□ Requisitos relacionados
□ Resultado esperado
```

Registre:

  Problema   Por que é um problema?   Correção proposta
  ---------- ------------------------ -------------------
                                      
                                      

------------------------------------------------------------------------

## Exercício 13 --- Teste das perguntas

Para cada passo do fluxo principal, aplique:

``` text
QUEM?
O QUÊ?
SOBRE O QUÊ?
E SE NÃO DER CERTO?
QUAL REGRA SE APLICA?
O QUE ACONTECE DEPOIS?
```

Identifique quais perguntas revelaram informações ausentes.

------------------------------------------------------------------------

# Parte 6 --- Rastreabilidade

## Exercício 14 --- Construa a cadeia

Considere:

``` text
RN07 — Descontos superiores a 15% devem ser autorizados pelo gerente.
```

Construa:

``` text
RN
 ↓
RF
 ↓
UC
 ↓
Fluxo Alternativo
 ↓
Critério de Aceitação
 ↓
Cenário de Teste
```

Todos os elementos devem permanecer coerentes com a RN07.

------------------------------------------------------------------------

## Exercício 15 --- Matriz de rastreabilidade

Utilizando o projeto da equipe:

  Regra   Requisito   Caso de Uso   Fluxo/Cenário
  ------- ----------- ------------- ---------------
  RN01    RF??        UC??          ???
  RN02    RF??        UC??          ???

Depois responda:

-   Existem regras sem requisitos?
-   Existem requisitos sem Casos de Uso?
-   Existem comportamentos sem relação aparente com requisito ou regra?
-   Isso necessariamente representa um erro?

------------------------------------------------------------------------

