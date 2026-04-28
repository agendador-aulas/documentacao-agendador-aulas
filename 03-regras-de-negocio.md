# Regras de Negócio

## 1. Regras do Aluno

- O aluno deve possuir email
- O telefone deve ser único no sistema
- Um aluno pode estar vinculado a múltiplos professores
- Um aluno inativo não pode se inscrever em turmas

---

## 2. Regras do vínculo ProfessorAluno

- Deve existir um vínculo ativo entre professor e aluno para permitir inscrição
- O vínculo deve ser único por professor e aluno
- O professor define o limite de turmas que o aluno pode participar
- O vínculo pode ser inativado sem exclusão

---

## 3. Regras da Turma

- A turma deve possuir uma capacidade máxima maior que zero
- Não deve permitir inscrições acima da capacidade
- Turmas inativas não aceitam novas inscrições
- O professor pode editar a turma a qualquer momento

---

## 4. Regras da Inscrição

- Não deve existir mais de uma inscrição ativa para o mesmo aluno na mesma turma
- O aluno deve estar ativo
- O vínculo ProfessorAluno deve estar ativo
- A turma deve estar ativa
- A turma deve possuir vaga disponível
- Deve respeitar o limite de turmas definido pelo professor
- Deve validar conflito de horário antes de confirmar a inscrição

---

## 5. Regras de Conflito de Horário

- Um aluno não pode possuir duas turmas com horários conflitantes
- O conflito deve considerar todas as turmas do aluno, independentemente do professor
- A validação deve considerar dia da semana e horário

---

## 6. Regras em Aberto

- Definir se inscrição precisa de aprovação do professor
- Definir comportamento de cancelamento de inscrição
- Definir controle de presença em aula
