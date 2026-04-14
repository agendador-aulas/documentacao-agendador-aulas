# Entidade: Turma

## Descrição

Representa uma turma criada por um professor.
Uma turma define um agrupamento de aulas com capacidade e configuração própria.

---

## Campos

| Campo            | Tipo     | Descrição                          | Motivo                                           |
| ---------------- | -------- | ---------------------------------- | ------------------------------------------------ |
| id               | UUID     | Identificador único da turma       | Evita colisão                                    |
| professorId      | UUID     | Identificador do professor dono    | Define relação entre professor e turma           |
| nome             | string   | Nome da turma                      | Identificação rápida                             |
| descricao        | string   | Descrição da turma                 | Contexto adicional (tipo de treino, nível, etc.) |
| capacidadeMaxima | integer  | Número máximo de alunos            | Regra central de negócio                         |
| status           | enum     | Situação da turma (ATIVA, INATIVA) | Permite desativar sem excluir                    |
| criadoEm         | datetime | Data de criação                    | Auditoria                                        |
| atualizadoEm     | datetime | Data da última atualização         | Controle de mudanças                             |

---

## Observações

* Uma turma pertence a um único professor
* Um professor pode ter várias turmas
* A capacidade máxima deve ser maior que zero
