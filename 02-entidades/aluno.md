# Entidade: Aluno

## Descrição

Representa o aluno atendido pelo professor e participante das turmas do sistema.

Nesta fase inicial, o aluno não possui login próprio. Sua participação ocorre principalmente por meio de interações operacionais, com foco em canais como WhatsApp.

O cadastro do aluno é realizado pelo professor.

---

## Campos

| Campo        | Tipo     | Descrição                                 | Motivo                                                                    |
|--------------|----------|-------------------------------------------|---------------------------------------------------------------------------|
| id           | UUID     | Identificador único do aluno              | Evita colisão e funciona bem em sistemas distribuídos                    |
| professorId  | UUID     | Identificador do professor responsável    | Define a relação entre aluno e professor                                 |
| nome         | string   | Nome do aluno                             | Identificação básica                                                     |
| email        | string   | Email do aluno                            | Canal de contato e possível base para futuras evoluções                  |
| telefone     | string   | Número de telefone do aluno               | Principal identificador operacional no fluxo via WhatsApp                |
| status       | enum     | Situação do aluno (ATIVO, INATIVO)        | Permite desativar sem excluir                                            |
| criadoEm     | datetime | Data de criação                           | Auditoria                                                                |
| atualizadoEm | datetime | Data da última atualização                | Controle de mudanças                                                     |

---

## Observações

- O aluno não participa do módulo de autenticação nesta fase
- O telefone tende a ser o identificador mais importante no fluxo operacional
- Um professor pode ter vários alunos
- O aluno é uma entidade do domínio, mesmo sem possuir login próprio
