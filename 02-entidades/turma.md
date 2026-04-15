# Entidade: Turma

## Descrição

Representa um grupo de alunos organizado por um professor em um conjunto de aulas.

A turma define a estrutura onde os alunos se inscrevem e participam das aulas.

---

## Campos

| Campo              | Tipo     | Descrição                                | Motivo                                                                 |
|--------------------|----------|------------------------------------------|------------------------------------------------------------------------|
| id                 | UUID     | Identificador único da turma             | Evita colisão e funciona bem em sistemas distribuídos                 |
| professorId        | UUID     | Identificador do professor responsável   | Define o dono da turma                                                |
| nome               | string   | Nome da turma                            | Identificação da turma                                                |
| descricao          | string   | Descrição da turma                       | Informações adicionais para alunos                                    |
| capacidadeMaxima   | integer  | Quantidade máxima de alunos              | Controle de lotação                                                   |
| status             | enum     | Situação da turma                        | Permite ativar ou desativar a turma                                   |
| criadoEm           | datetime | Data de criação                          | Auditoria                                                             |
| atualizadoEm       | datetime | Data da última atualização               | Controle de mudanças                                                  |

---

## Status possíveis

| Status   | Descrição                                      |
|----------|------------------------------------------------|
| ATIVA    | Turma disponível para novas inscrições          |
| INATIVA  | Turma não aceita novas inscrições               |

---

## Relacionamentos

- Uma turma pertence a um professor
- Uma turma possui vários horários (`HorarioTurma`)
- Uma turma possui várias inscrições (`Inscricao`)

---

## Observações

- A turma não armazena diretamente a lista de alunos
- A relação entre aluno e turma é feita pela entidade `Inscricao`
- Isso permite maior flexibilidade e controle sobre o vínculo

---

## Regras associadas

- Não deve permitir mais inscrições que a `capacidadeMaxima`
- Turmas inativas não aceitam novas inscrições
- O professor pode editar a turma a qualquer momento
- O professor pode remover alunos da turma (via `Inscricao`)
