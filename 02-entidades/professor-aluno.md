# Entidade: ProfessorAluno

## Descrição

Representa o vínculo entre um professor e um aluno.

Essa entidade existe para registrar a relação administrativa entre as duas partes, sem acoplar essa responsabilidade diretamente na entidade Aluno.

Ela permite que o mesmo aluno esteja vinculado a múltiplos professores, cada um com regras próprias.

---

## Campos

| Campo              | Tipo     | Descrição                                           | Motivo                                                              |
|-------------------|----------|-----------------------------------------------------|---------------------------------------------------------------------|
| id                | UUID     | Identificador único do vínculo                      | Evita colisão e permite rastrear cada relacionamento                |
| professorId       | UUID     | Identificador do professor                          | Define qual professor participa do vínculo                          |
| alunoId           | UUID     | Identificador do aluno                              | Define qual aluno participa do vínculo                              |
| limiteTurmas      | integer  | Quantidade máxima de turmas permitidas com o professor | Permite aplicar a regra de negócio definida por professor        |
| status            | enum     | Situação do vínculo                                 | Permite ativar ou inativar a relação sem excluir dados              |
| criadoEm          | datetime | Data de criação do vínculo                          | Auditoria                                                           |
| atualizadoEm      | datetime | Data da última atualização                          | Controle de mudanças                                                |

---

## Status possíveis

| Status   | Descrição                                 |
|----------|--------------------------------------------|
| ATIVO    | Vínculo válido entre professor e aluno     |
| INATIVO  | Vínculo desativado                         |

---

## Observações

- Um professor pode possuir vários alunos vinculados
- Um aluno pode estar vinculado a vários professores
- O vínculo entre professor e aluno deve ser único
- O limite de turmas é definido no contexto de cada professor
- O limite de turmas não substitui a validação de conflito de horário
- Mesmo que um aluno tenha limite disponível com um professor, ele não pode se inscrever em turmas com choque de horário
- Essa entidade não representa a inscrição na turma
- A inscrição do aluno em uma turma deve ser tratada pela entidade `Inscricao`

---

## Regras associadas

- Não deve existir mais de um vínculo ativo para o mesmo par `professorId + alunoId`
- O professor pode criar, editar ou inativar esse vínculo
- O aluno só pode se inscrever em turmas de um professor se possuir vínculo ativo com ele
- O sistema deve validar o limite de turmas com base nessa entidade
