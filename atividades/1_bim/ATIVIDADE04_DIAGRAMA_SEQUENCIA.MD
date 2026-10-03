# Parte 7 --- Introdução ao Diagrama de Sequência

## Exercício 16 --- Caso de Uso × Diagrama de Sequência

Explique:

``` text
Caso de Uso:
Como o ator alcança seu objetivo utilizando o sistema?

Diagrama de Sequência:
Como os participantes colaboram ao longo do tempo
para realizar determinado cenário?
```

> Por que um Diagrama de Sequência não substitui um Caso de Uso?

------------------------------------------------------------------------

## Exercício 17 --- Identificando participantes

> Um cliente solicita uma transferência bancária. A interface envia a
> solicitação para o sistema. O sistema verifica a conta de origem,
> consulta o saldo, valida a transferência, registra a movimentação e
> informa o resultado ao cliente.

Identifique participantes considerando:

``` text
ATOR
INTERFACE / BOUNDARY
CONTROLE / APLICAÇÃO
DOMÍNIO
PERSISTÊNCIA
```

Justifique a responsabilidade de cada participante.

------------------------------------------------------------------------

# Parte 8 --- Construção de Diagramas de Sequência

## Exercício 18 --- Da especificação para a sequência

``` text
UC03 — Reservar Sala

Ator: Professor

1. Professor solicita uma reserva.
2. Sistema solicita data e horário.
3. Professor informa data e horário.
4. Sistema verifica disponibilidade.
5. Sistema apresenta a sala disponível.
6. Professor confirma.
7. Sistema registra a reserva.
8. Sistema informa a confirmação.
```

Construa um Diagrama de Sequência contendo pelo menos:

``` text
Professor
TelaReserva
ReservaController
ReservaService
ReservaRepository
```

------------------------------------------------------------------------

## Exercício 19 --- Adicione uma decisão

Acrescente:

``` text
RN05 — Uma sala não pode possuir duas reservas para períodos conflitantes.
```

Modifique o Diagrama usando `alt` para:

``` text
[sala disponível]
[sala indisponível]
```

Explique como a RN05 aparece no comportamento.

------------------------------------------------------------------------

## Exercício 20 --- Adicione uma repetição

Considere um pedido com vários produtos.

Represente:

``` text
loop [para cada produto]
    verificar disponibilidade
    adicionar item
    calcular subtotal
```

Explique por que `loop` é mais adequado que repetir manualmente as
mensagens.

------------------------------------------------------------------------

# Parte 9 --- Encontrando problemas no projeto

## Exercício 21 --- Quem deveria fazer isso?

Considere:

``` text
TelaPedido
   ↓
validarCliente()
verificarEstoque()
calcularDesconto()
calcularTotal()
salvarPedido()
enviarEmail()
```

Discuta:

1.  Qual é o problema?
2.  Quais responsabilidades estão concentradas indevidamente?
3.  Como distribuí-las entre Interface, Controller/Aplicação, Domínio e
    Infraestrutura?

Depois desenhe uma solução melhor.

------------------------------------------------------------------------

## Exercício 22 --- Mensagens sem origem

Um Diagrama de Sequência contém:

``` text
PedidoService → ClienteService:
bloquearCliente()
```

Porém, nenhuma Regra de Negócio, requisito ou passo do Caso de Uso
menciona bloqueio.

Discuta:

1.  o diagrama está errado;
2.  o requisito está incompleto;
3.  uma Regra de Negócio não foi documentada;
4.  trata-se de uma decisão interna legítima de projeto.

Explique como decidir entre as possibilidades.

------------------------------------------------------------------------

# Parte 10 --- Exercício Integrador

## Exercício 23 --- Do problema ao Diagrama de Sequência

> Uma clínica permite que pacientes agendem consultas. O paciente
> escolhe uma especialidade, profissional, data e horário. Um
> profissional não pode possuir duas consultas no mesmo horário.
> Consultas somente podem ser agendadas em horários disponíveis. O
> paciente pode cancelar uma consulta até 24 horas antes do horário
> agendado. O sistema deve registrar todas as consultas e cancelamentos.

Realize:

1.  Identifique as Regras de Negócio.
2.  Especifique os Requisitos Funcionais.
3.  Proponha Requisitos Não Funcionais relevantes.
4.  Identifique os atores.
5.  Identifique os Casos de Uso.
6.  Escolha `Agendar Consulta`.
7.  Especifique:
    -   objetivo;
    -   ator;
    -   pré-condições;
    -   pós-condições;
    -   fluxo principal;
    -   fluxos alternativos;
    -   exceções.
8.  Relacione `RN ↔ RF/RNF ↔ UC`.
9.  Aplique o checklist.
10. Corrija os problemas.
11. Identifique os participantes do fluxo principal.
12. Construa o Diagrama de Sequência.
13. Utilize `alt` para horário disponível/indisponível.
14. Explique a responsabilidade de cada participante.

------------------------------------------------------------------------

# Parte 11 --- Desafio com o projeto da equipe

## Exercício 24 --- Da análise ao projeto

Utilizando **o projeto real da equipe**, escolha um Caso de Uso
importante e produza:

``` text
REGRA DE NEGÓCIO
        ↓
REQUISITO
        ↓
CASO DE USO
        ↓
FLUXO PRINCIPAL
   ↙           ↘
ALTERNATIVO   EXCEÇÃO
        ↓
CHECKLIST / REVISÃO
        ↓
CASO DE USO CORRIGIDO
        ↓
DIAGRAMA DE SEQUÊNCIA
        ↓
RESPONSABILIDADES
```

A equipe deverá justificar **cada elemento do Diagrama de Sequência a
partir da análise realizada anteriormente**.

------------------------------------------------------------------------

# Questão final para discussão

> O Diagrama de Sequência apenas representa graficamente o Caso de Uso
> ou também ajuda a descobrir problemas e decisões de projeto que ainda
> não estavam explícitas?

Apresente pelo menos **dois exemplos encontrados durante os
exercícios**.

------------------------------------------------------------------------
