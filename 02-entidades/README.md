# Entidades

Esta pasta concentra a documentação das entidades do domínio.

## Navegação

| Entidade | Tipo | Descrição |
|---|---|---|
| [Professor](professor.md) | Principal | Usuário administrativo que cria e gerencia turmas |
| [Aluno](aluno.md) | Principal | Participante das turmas, sem login próprio nesta fase |
| [Turma](turma.md) | Principal | Agrupamento de aulas criado por um professor |
| [HorarioTurma](horario-turma.md) | Principal | Horários recorrentes associados a uma turma |
| [ProfessorAluno](professor-aluno.md) | Relacionamento | Vínculo entre professor e aluno, com limite de turmas |
| [Inscricao](inscricao.md) | Relacionamento | Vínculo entre aluno e turma |

---

## Entidades principais

As entidades principais representam conceitos centrais do domínio.

- Professor
- Aluno
- Turma
- HorarioTurma

---

## Entidades de relacionamento

As entidades de relacionamento representam vínculos entre entidades principais.

- ProfessorAluno
- Inscricao

Essas entidades evitam que regras importantes fiquem acopladas diretamente em `Aluno` ou `Turma`.

---

## Voltar

- [Voltar para o README principal](../README.md)
