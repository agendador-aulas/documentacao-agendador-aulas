# Entidade: Inscricao

## Descrição

Representa o vínculo entre um aluno e uma turma.

A inscrição define que um aluno está participando de uma turma específica, respeitando as regras de negócio como capacidade, conflito de horário e limite por professor.

Essa entidade é fundamental para o funcionamento do sistema, pois permite controlar a participação dos alunos nas turmas.

---

## Campos

| Campo        | Tipo     | Descrição                                 | Motivo                                                                 |
|--------------|----------|-------------------------------------------|------------------------------------------------------------------------|
| id           | UUID     | Identificador único da inscrição          | Evita colisão e permite rastrear cada vínculo                          |
| alunoId      | UUID     | Identificador do aluno                    | Define qual aluno está inscrito                                       |
| turmaId      | UUID     | Identificador da turma                    | Define em qual turma o aluno está inscrito                            |
| status       | enum     | Situação da inscrição                     | Permite controlar o ciclo de vida da inscrição                        |
| criadoEm     | datetime | Data de criação da inscrição              | Auditoria e controle de entrada                                       |
| atualizadoEm | datetime | Data da última atualização                | Controle de mudanças                                                  |

---

## Status possíveis

| Status     | Descrição                                      |
|------------|-----------------------------------------------|
| ATIVA      | Inscrição válida e em andamento                |
| CANCELADA  | Inscrição cancelada pelo professor ou sistema  |
| REMOVIDA   | Aluno removido da turma pelo professor         |

---

## Observações

- Uma inscrição sempre relaciona um único aluno a uma única turma
- Um aluno pode possuir várias inscrições
- Uma turma pode possuir várias inscrições
- Não deve existir mais de uma inscrição ativa para o mesmo aluno na mesma turma
- A inscrição deve respeitar as regras de negócio:

  - não permitir inscrição em turma cheia
  - não permitir inscrição com conflito de horário
  - não permitir inscrição de aluno inativo
  - respeitar o limite de turmas definido por professor

- A inscrição pode ser criada:

  - pelo próprio aluno (via WhatsApp)
  - pelo professor (manual)

- Essa entidade permite evoluções futuras como:

  - histórico de participação
  - controle de presença
  - cancelamentos
  - listas de espera
