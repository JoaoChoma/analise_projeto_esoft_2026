# ATIVIDADE 02: FORMALIZAR AS REGRAS DE NEGÓCIO E REQUISITOS DO PRODUTO

# Como padronizar? 

## Siga os passos e entregue em 29/08/2026 no classroom o link do Github com os documentos

# Padrão para Regras de Negócio e Requisitos

## Objetivo

Estabelecer um **padrão único de documentação** para que regras de negócio e requisitos possam ser:

- identificados;
- descritos;
- discutidos;
- validados;
- rastreados;
- transformados em tarefas;
- relacionados a casos de uso;
- relacionados a diagramas comportamentais;
- implementados;
- testados;
- evoluídos ao longo do projeto.

> O documento de requisitos não deve ser apenas uma entrega inicial.  
> Ele deve funcionar como uma **fonte de rastreabilidade para a evolução do software**.

---

# 1. Fluxo de evolução

```text
NECESSIDADE / PROBLEMA
        ↓
STAKEHOLDERS
        ↓
REGRAS DE NEGÓCIO
        ↓
REQUISITOS DE SOFTWARE
        ↓
CASOS DE USO / COMPORTAMENTO
        ↓
TAREFAS DE DESENVOLVIMENTO
        ↓
IMPLEMENTAÇÃO
        ↓
TESTES
        ↓
VALIDAÇÃO
        ↓
EVOLUÇÃO
```

A cada etapa devem existir identificadores que permitam responder:

> De onde surgiu esta funcionalidade?

e também:

> Quais partes do sistema serão afetadas se este requisito mudar?

---

# 2. Identificação padronizada

Cada artefato recebe um identificador único.

| Artefato | Prefixo | Exemplo |
|---|---|---|
| Regra de Negócio | `RN` | `RN-001` |
| Requisito Funcional | `RF` | `RF-001` |
| Requisito Não Funcional | `RNF` | `RNF-001` |
| Caso de Uso | `UC` | `UC-001` |
| História/Tarefa | `TASK` | `TASK-001` |
| Caso de Teste | `CT` | `CT-001` |
| Diagrama | `DG` | `DG-001` |

Exemplo de rastreabilidade:

```text
RN-003
   ↓
RF-007
   ↓
UC-004
   ↓
TASK-012
   ↓
CT-018
```

---

# 3. Status padronizados

Para facilitar o gerenciamento, todos os itens devem possuir status.

```text
PROPOSTO
EM ANÁLISE
APROVADO
EM DESENVOLVIMENTO
IMPLEMENTADO
VALIDADO
CANCELADO
```

Nem todos os tipos de artefatos precisam utilizar todos os estados, mas a equipe deve manter uma terminologia consistente.

---

# 4. Prioridade

Utilize uma escala simples:

| Prioridade | Significado |
|---|---|
| Crítica | Necessária para funcionamento ou conformidade |
| Alta | Importante para a entrega |
| Média | Importante, mas pode ser planejada posteriormente |
| Baixa | Melhoria ou conveniência |

Também pode ser adotado o modelo **MoSCoW**:

```text
Must Have
Should Have
Could Have
Won't Have Now
```

---

# 5. Padrão para Regra de Negócio

Uma **Regra de Negócio** descreve uma política, restrição, cálculo, condição ou decisão existente no domínio do negócio.

Ela responde principalmente:

> **Como o negócio funciona ou deve funcionar?**

---

# 6. Template — Regra de Negócio

```markdown
## RN-XXX — Nome da Regra

**Título:**  
Nome curto e representativo.

**Descrição:**  
Descrição objetiva da regra.

**Origem:**  
Pessoa, setor, documento, legislação ou processo que originou a regra.

**Stakeholders envolvidos:**  
Quem é afetado pela regra.

**Condição:**  
Quando esta regra deve ser aplicada.

**Regra:**  
O que obrigatoriamente deve ocorrer.

**Exceções:**  
Situações nas quais a regra não se aplica ou possui comportamento diferente.

**Dados envolvidos:**  
Informações necessárias para aplicar a regra.

**Prioridade:**  
Crítica | Alta | Média | Baixa

**Status:**  
Proposto | Em análise | Aprovado | Cancelado

**Requisitos relacionados:**  
RF-XXX, RF-XXX

**Observações:**  
Informações complementares.
```

---

# 7. Exemplo — Regra de Negócio

```markdown
## RN-001 — Limite de Empréstimos

**Título:**  
Limite de empréstimos simultâneos.

**Descrição:**  
Um aluno pode possuir no máximo três livros emprestados simultaneamente.

**Origem:**  
Regulamento da biblioteca.

**Stakeholders envolvidos:**  
Aluno, bibliotecário.

**Condição:**  
Aplicada sempre que um novo empréstimo for solicitado.

**Regra:**  
O empréstimo somente poderá ser realizado quando o aluno possuir menos de três empréstimos ativos.

**Exceções:**  
Professores podem possuir até cinco empréstimos ativos.

**Dados envolvidos:**  
Usuário, tipo do usuário, empréstimos ativos.

**Prioridade:**  
Alta

**Status:**  
Aprovado

**Requisitos relacionados:**  
RF-004

**Observações:**  
O limite deve ser configurável futuramente.
```

---

# 8. Teste de qualidade de uma Regra de Negócio

Antes de aprovar uma RN, verifique:

- A regra pertence ao **negócio** ou está descrevendo uma tela?
- É possível identificar sua origem?
- A condição de aplicação está clara?
- Existem exceções?
- Os dados necessários estão identificados?
- É possível verificar se a regra foi respeitada?

Evite:

```text
RN-001 — O sistema terá um botão azul para emprestar.
```

Isso não é uma regra de negócio.

Melhor:

```text
RN-001 — Um aluno pode possuir no máximo três
empréstimos ativos simultaneamente.
```

---

# 9. Padrão para Requisito Funcional

Um **Requisito Funcional** descreve um comportamento ou serviço que o software deve oferecer.

Responde:

> **O que o sistema deve fazer?**

Uma forma recomendada de escrita é:

```text
O sistema deve + VERBO + OBJETO + CONDIÇÃO
```

Exemplo:

```text
O sistema deve impedir a realização de um novo empréstimo
quando o aluno atingir o limite definido pela RN-001.
```

---

# 10. Template — Requisito Funcional

```markdown
## RF-XXX — Nome do Requisito

**Título:**  
Nome curto da funcionalidade.

**Descrição:**  
O sistema deve...

**Objetivo:**  
Qual problema ou necessidade este requisito atende?

**Stakeholders:**  
Quem necessita ou utiliza esta funcionalidade?

**Ator principal:**  
Quem inicia a interação?

**Pré-condições:**  
O que deve ser verdadeiro antes da execução?

**Entradas:**  
Dados necessários.

**Processamento esperado:**  
O que o sistema deve realizar?

**Saídas/Resultados:**  
Qual resultado deve ser produzido?

**Pós-condições:**  
Qual deve ser o estado do sistema após a execução?

**Fluxos alternativos/exceções:**  
Quais comportamentos diferentes podem ocorrer?

**Regras de negócio relacionadas:**  
RN-XXX

**Prioridade:**  
Crítica | Alta | Média | Baixa

**Status:**  
Proposto | Em análise | Aprovado | Em desenvolvimento | Implementado | Validado

**Critérios de aceite:**  
- ...
- ...
- ...

**Casos de uso relacionados:**  
UC-XXX

**Tarefas relacionadas:**  
TASK-XXX

**Casos de teste relacionados:**  
CT-XXX
```

---

# 11. Exemplo — Requisito Funcional

```markdown
## RF-004 — Registrar Empréstimo

**Título:**  
Registrar empréstimo de livro.

**Descrição:**  
O sistema deve permitir que o bibliotecário registre o empréstimo de um exemplar disponível para um usuário habilitado.

**Objetivo:**  
Controlar a retirada e devolução de exemplares da biblioteca.

**Stakeholders:**  
Aluno, professor e bibliotecário.

**Ator principal:**  
Bibliotecário.

**Pré-condições:**  
- Usuário cadastrado.
- Usuário ativo.
- Exemplar disponível.

**Entradas:**  
- Identificador do usuário.
- Identificador do exemplar.

**Processamento esperado:**  
O sistema deve verificar a situação do usuário, disponibilidade do exemplar e regras de empréstimo antes de registrar a operação.

**Saídas/Resultados:**  
Empréstimo registrado e exemplar marcado como indisponível.

**Pós-condições:**  
O empréstimo fica associado ao usuário.

**Fluxos alternativos/exceções:**  
- Usuário bloqueado.
- Limite de empréstimos atingido.
- Exemplar indisponível.

**Regras de negócio relacionadas:**  
RN-001, RN-002

**Prioridade:**  
Alta

**Status:**  
Aprovado

**Critérios de aceite:**  
- Não permitir empréstimo para usuário bloqueado.
- Não permitir empréstimo acima do limite.
- Alterar o exemplar para indisponível após confirmação.
- Registrar data do empréstimo.

**Casos de uso relacionados:**  
UC-002

**Tarefas relacionadas:**  
TASK-010, TASK-011

**Casos de teste relacionados:**  
CT-007, CT-008, CT-009
```

---

# 12. Requisitos Não Funcionais

Os **Requisitos Não Funcionais (RNF)** descrevem restrições ou atributos de qualidade do sistema.

Respondem:

> **Como o sistema deve funcionar ou quais restrições deve respeitar?**

Categorias comuns:

```text
Desempenho
Segurança
Usabilidade
Disponibilidade
Confiabilidade
Compatibilidade
Manutenibilidade
Portabilidade
Escalabilidade
Acessibilidade
```

---

# 13. Template — Requisito Não Funcional

```markdown
## RNF-XXX — Nome do Requisito

**Categoria:**  
Segurança | Desempenho | Usabilidade | ...

**Descrição:**  
O sistema deve...

**Justificativa:**  
Por que este requisito é necessário?

**Métrica/Critério mensurável:**  
Como será verificado?

**Escopo:**  
Todo o sistema ou funcionalidades específicas?

**Prioridade:**  
Crítica | Alta | Média | Baixa

**Status:**  
Proposto | Em análise | Aprovado | Implementado | Validado

**Requisitos relacionados:**  
RF-XXX

**Casos de teste relacionados:**  
CT-XXX
```

---

# 14. Evitando requisitos não verificáveis

Evite:

```text
RNF-003

O sistema deve ser rápido.
```

Problema:

> O que significa "rápido"?

Prefira:

```text
RNF-003

O sistema deve apresentar o resultado da consulta de livros
em até 2 segundos para 95% das requisições realizadas
sob a carga operacional definida para o sistema.
```

Agora existe uma condição que pode ser testada.

---

# Exemplo de rastreabilidade

Considere:

```text
RN-001
Limite de 3 empréstimos
          │
          ▼
RF-004
Registrar empréstimos
````

