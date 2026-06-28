# Plano de Testes — Alimenta Aí!

## Introdução

Este documento descreve os casos de teste elaborados para o sistema **Alimenta Aí!**, uma plataforma web voltada à redução do desperdício alimentar e combate à insegurança alimentar (ODS 2 — Fome Zero).

Os testes cobrem os casos de uso identificados no diagrama elaborado no TP2, verificando o comportamento esperado da aplicação em diferentes cenários.

---

## Casos de Uso Cobertos

| ID | Caso de Uso |
|----|-------------|
| UC01 | Cadastro de Usuário |
| UC02 | Autenticação de Usuário (Login) |
| UC03 | Cadastro de Doação |
| UC04 | Listagem de Doações |
| UC05 | Solicitação de Doação |
| UC06 | Controle de Status da Doação |

---

## CT01 — Cadastro de Usuário

**Caso de Uso:** UC01  
**Objetivo:** Verificar se o sistema permite o cadastro de novos usuários com dados válidos.

### CT01.1 — Cadastro com dados válidos (doador)
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Usuário não possui conta cadastrada |
| **Entradas** | Nome: "Maria Silva", E-mail: "maria@email.com", Senha: "123456", Tipo: "Doador" |
| **Passos** | 1. Acessar a tela inicial → 2. Clicar em "Cadastrar" → 3. Preencher os dados → 4. Clicar em "Criar conta" |
| **Resultado esperado** | Conta criada, usuário redirecionado para a tela principal com saudação |
| **Resultado obtido** | ✅ Passou |

### CT01.2 — Cadastro com e-mail já existente
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Usuário "maria@email.com" já cadastrado |
| **Entradas** | E-mail: "maria@email.com" (duplicado) |
| **Passos** | 1. Tentar cadastrar com o mesmo e-mail |
| **Resultado esperado** | Mensagem de erro: "Este e-mail já está cadastrado." |
| **Resultado obtido** | ✅ Passou |

### CT01.3 — Cadastro com senha abaixo do mínimo
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Nenhuma |
| **Entradas** | Senha: "123" (3 caracteres) |
| **Passos** | 1. Preencher formulário com senha curta → 2. Clicar em "Criar conta" |
| **Resultado esperado** | Formulário não enviado; campo de senha destacado com erro |
| **Resultado obtido** | ✅ Passou |

---

## CT02 — Autenticação de Usuário (Login)

**Caso de Uso:** UC02  
**Objetivo:** Verificar o comportamento do sistema no login.

### CT02.1 — Login com credenciais corretas
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Conta "maria@email.com" cadastrada |
| **Entradas** | E-mail: "maria@email.com", Senha: "123456" |
| **Passos** | 1. Acessar aba "Entrar" → 2. Preencher credenciais → 3. Clicar em "Entrar" |
| **Resultado esperado** | Login realizado, usuário vê a tela principal com seu nome exibido |
| **Resultado obtido** | ✅ Passou |

### CT02.2 — Login com senha incorreta
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Conta "maria@email.com" cadastrada |
| **Entradas** | E-mail: "maria@email.com", Senha: "senhaerrada" |
| **Passos** | 1. Preencher credenciais erradas → 2. Clicar em "Entrar" |
| **Resultado esperado** | Mensagem de erro: "E-mail ou senha incorretos." |
| **Resultado obtido** | ✅ Passou |

### CT02.3 — Login com e-mail não cadastrado
| Campo | Valor |
|-------|-------|
| **Pré-condição** | E-mail não existe no sistema |
| **Entradas** | E-mail: "naoexiste@email.com", Senha: "qualquer" |
| **Passos** | 1. Tentar login com e-mail inexistente |
| **Resultado esperado** | Mensagem de erro: "E-mail ou senha incorretos." |
| **Resultado obtido** | ✅ Passou |

---

## CT03 — Cadastro de Doação

**Caso de Uso:** UC03  
**Objetivo:** Verificar o cadastro de alimentos disponíveis para doação.

### CT03.1 — Cadastro com campos obrigatórios preenchidos
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Usuário logado como Doador |
| **Entradas** | Nome: "Arroz integral 5kg", Local: "Rua das Flores, 100" |
| **Passos** | 1. Ir em "Nova Doação" → 2. Preencher nome e local → 3. Clicar em "Cadastrar doação" |
| **Resultado esperado** | Doação cadastrada e exibida no feed com status "Disponível" |
| **Resultado obtido** | ✅ Passou |

### CT03.2 — Tentativa sem preencher campo obrigatório
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Usuário logado |
| **Entradas** | Nome preenchido, Local em branco |
| **Passos** | 1. Preencher apenas o nome → 2. Clicar em "Cadastrar doação" |
| **Resultado esperado** | Formulário não enviado; campo obrigatório destacado |
| **Resultado obtido** | ✅ Passou |

### CT03.3 — Cadastro com todos os campos preenchidos
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Usuário logado |
| **Entradas** | Todos os campos (nome, quantidade, validade, descrição, local) |
| **Passos** | 1. Preencher todos os campos → 2. Confirmar |
| **Resultado esperado** | Doação salva com todos os dados visíveis no card |
| **Resultado obtido** | ✅ Passou |

---

## CT04 — Listagem de Doações

**Caso de Uso:** UC04  
**Objetivo:** Verificar a exibição correta das doações disponíveis.

### CT04.1 — Exibição de doações disponíveis no feed
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Existem doações cadastradas por outros usuários |
| **Entradas** | — |
| **Passos** | 1. Fazer login → 2. Acessar aba "Início" |
| **Resultado esperado** | Cards de doações disponíveis exibidos, excluindo as próprias doações do usuário |
| **Resultado obtido** | ✅ Passou |

### CT04.2 — Exibição de mensagem quando não há doações disponíveis
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Nenhuma doação cadastrada por outros usuários |
| **Entradas** | — |
| **Passos** | 1. Acessar feed sem doações disponíveis |
| **Resultado esperado** | Mensagem "Nenhuma doação disponível" exibida |
| **Resultado obtido** | ✅ Passou |

### CT04.3 — Exibição dos contadores de estatísticas
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Existem doações em diferentes status |
| **Entradas** | — |
| **Passos** | 1. Acessar tela inicial após doações cadastradas |
| **Resultado esperado** | Cards de estatísticas mostram totais corretos (cadastradas, disponíveis, entregues) |
| **Resultado obtido** | ✅ Passou |

---

## CT05 — Solicitação de Doação

**Caso de Uso:** UC05  
**Objetivo:** Verificar o processo de solicitação de uma doação.

### CT05.1 — Solicitação bem-sucedida
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Doação disponível cadastrada por outro usuário |
| **Entradas** | — |
| **Passos** | 1. Acessar feed → 2. Clicar em "Solicitar" na doação desejada |
| **Resultado esperado** | Confirmação exibida; doação passa para status "Reservado"; doação aparece em "Minhas Solicitações" |
| **Resultado obtido** | ✅ Passou |

### CT05.2 — Tentativa de solicitar a própria doação
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Usuário logado com doação própria cadastrada |
| **Entradas** | — |
| **Passos** | 1. Tentar solicitar doação cadastrada pelo próprio usuário |
| **Resultado esperado** | Mensagem de erro: "Você não pode solicitar sua própria doação." |
| **Resultado obtido** | ✅ Passou |

### CT05.3 — Tentativa de solicitar doação já reservada
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Doação com status "Reservado" |
| **Entradas** | — |
| **Passos** | 1. Tentar solicitar doação já reservada |
| **Resultado esperado** | Mensagem: "Esta doação não está mais disponível." |
| **Resultado obtido** | ✅ Passou |

---

## CT06 — Controle de Status

**Caso de Uso:** UC06  
**Objetivo:** Verificar a alteração de status das doações pelo doador.

### CT06.1 — Alterar status de "Disponível" para "Reservado"
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Doação com status "Disponível" pertencente ao usuário logado |
| **Entradas** | Novo status: "Reservado" |
| **Passos** | 1. Ir em "Minhas Doações" → 2. Clicar em "Alterar status" → 3. Selecionar "Reservado" → 4. Clicar em "Salvar" |
| **Resultado esperado** | Status atualizado; badge do card alterado para "Reservado" |
| **Resultado obtido** | ✅ Passou |

### CT06.2 — Alterar status para "Entregue"
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Doação com status "Reservado" |
| **Entradas** | Novo status: "Entregue" |
| **Passos** | 1. Abrir modal de status → 2. Selecionar "Entregue" → 3. Confirmar |
| **Resultado esperado** | Status atualizado; badge azul "Entregue" exibido; contagem de "Entregues" incrementada |
| **Resultado obtido** | ✅ Passou |

### CT06.3 — Cancelar alteração de status
| Campo | Valor |
|-------|-------|
| **Pré-condição** | Modal de status aberto |
| **Entradas** | — |
| **Passos** | 1. Abrir modal → 2. Clicar em "Cancelar" |
| **Resultado esperado** | Modal fechado sem alteração no status |
| **Resultado obtido** | ✅ Passou |

---

## Resumo dos Resultados

| Caso de Uso | Total de TCs | Passou | Falhou |
|-------------|:------------:|:------:|:------:|
| UC01 — Cadastro de Usuário | 3 | 3 | 0 |
| UC02 — Login | 3 | 3 | 0 |
| UC03 — Cadastro de Doação | 3 | 3 | 0 |
| UC04 — Listagem | 3 | 3 | 0 |
| UC05 — Solicitação | 3 | 3 | 0 |
| UC06 — Controle de Status | 3 | 3 | 0 |
| **Total** | **18** | **18** | **0** |

Todos os 18 casos de teste foram executados manualmente e passaram conforme esperado.
