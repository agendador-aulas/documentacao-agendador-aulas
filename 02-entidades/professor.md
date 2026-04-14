# Entidade: Professor

## Descrição

Representa o professor dentro do sistema como entidade persistida.
É o responsável por criar e gerenciar turmas.

---

## Campos

| Campo        | Tipo     | Descrição                          | Motivo                                                |
| ------------ | -------- | ---------------------------------- | ----------------------------------------------------- |
| id           | UUID     | Identificador único do professor   | Evita colisão e funciona bem em sistemas distribuídos |
| nome         | string   | Nome do professor                  | Identificação básica                                  |
| email        | string   | Email utilizado para login         | Credencial principal, deve ser único                  |
| senhaHash    | string   | Senha armazenada de forma segura   | Nunca armazenar senha em texto puro                   |
| telefone     | string   | Telefone do professor              | Permite futuras integrações (ex: WhatsApp)            |
| status       | enum     | Situação da conta (ATIVO, INATIVO) | Permite desativar sem excluir                         |
| criadoEm     | datetime | Data de criação                    | Auditoria                                             |
| atualizadoEm | datetime | Data da última atualização         | Controle de mudanças                                  |

---

## Segurança da senha

O campo `senhaHash` não armazena a senha original do usuário.

A senha é processada utilizando um algoritmo de hash seguro (ex: bcrypt), que:

* transforma a senha em um valor irreversível
* adiciona um salt automaticamente
* dificulta ataques de força bruta

### Fluxo de registro

* a senha enviada pelo usuário é transformada em hash
* apenas o hash é armazenado no sistema

### Fluxo de login

* a senha informada é comparada com o hash armazenado
* não há necessidade de descriptografar a senha

### Observações

* a senha nunca deve ser armazenada ou trafegada em texto puro após o processamento
* o hash nunca deve ser exposto em respostas da API


## Observações

* O professor aparece como:

  * ator (interação com sistema)
  * entidade (dados persistidos)
* O email deve ser único no sistema
* A senha deve sempre ser armazenada como hash
