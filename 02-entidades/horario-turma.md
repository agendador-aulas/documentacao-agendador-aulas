# Entidade: HorarioTurma

## Descrição

Representa os horários em que uma turma ocorre ao longo da semana.

Uma turma pode possuir um ou vários horários.

---

## Campos

| Campo        | Tipo     | Descrição                            | Motivo                                      |
| ------------ | -------- | ------------------------------------ | ------------------------------------------- |
| id           | UUID     | Identificador único do horário       | Permite tratar cada horário individualmente |
| turmaId      | UUID     | Identificador da turma               | Define relação com a turma                  |
| diaSemana    | enum     | Dia da semana (SEGUNDA a DOMINGO)    | Padroniza e evita erros de digitação        |
| horaInicio   | string   | Horário de início (HH:mm)            | Representa recorrência semanal              |
| horaFim      | string   | Horário de término (HH:mm)           | Permite validação de duração                |
| status       | enum     | Situação do horário (ATIVO, INATIVO) | Permite desativar sem excluir               |
| criadoEm     | datetime | Data de criação                      | Auditoria                                   |
| atualizadoEm | datetime | Data da última atualização           | Controle de mudanças                        |

---

## Observações

* Um horário pertence a uma única turma
* Uma turma pode ter vários horários
* Separar horários da turma evita complexidade futura
* Permite evoluir para controle de aulas por data no futuro
