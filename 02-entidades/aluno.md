# Entidade: Aluno

## Descrição

Representa o aluno participante das turmas do sistema.

Nesta fase inicial, o aluno não possui login próprio. Sua participação ocorre principalmente por meio de interações operacionais, com foco em canais como WhatsApp.

O cadastro do aluno é realizado pelo professor, mas o aluno não pertence diretamente a um único professor.

---

## Campos

| Campo        | Tipo     | Descrição                          | Motivo                                                             |
|--------------|----------|------------------------------------|--------------------------------------------------------------------|
| id           | UUID     | Identificador único do aluno       | Evita colisão e funciona bem em sistemas distribuídos             |
| nome         | string   | Nome do aluno                      | Identificação básica                                              |
| email        | string   | Email do aluno                     | Canal de contato e possível evolução futura                       |
| telefone     | string   | Número de telefone do aluno        | Principal identificador operacional (WhatsApp)                    |
| status       | enum     | Situação do aluno                  | Permite desativar sem excluir                                     |
| criadoEm     | datetime | Data de criação                    | Auditoria                                                         |
| atualizadoEm | datetime | Data da última atualização         | Controle de mudanças                                              |

---

## Observações

- O aluno não participa do módulo de autenticação nesta fase
- O telefone tende a ser o identificador mais importante no fluxo operacional
- Um aluno pode estar associado a múltiplos professores
- O vínculo entre aluno e professor será tratado por uma entidade de relacionamento (ProfessorAluno)
- O aluno é uma entidade global do domínio
