# Requisitos

## Funcionalidade: Login

### História do Usuário
Como usuário,  
Quero fazer login no sistema  
Para acessar minha conta  

### Critérios de Aceitação

#### Cenários Positivos
- O usuário pode fazer login com credenciais válidas (standard_user / secret_sauce)
- O usuário é redirecionado para a página de produtos após login bem-sucedido

#### Cenários Negativos
- Uma mensagem de erro é exibida para credenciais inválidas
- Os campos de usuário e senha são obrigatórios
- Usuário bloqueado (locked_out_user) não consegue realizar login e recebe mensagem de erro

#### Casos de Borda
- O tempo de resposta do sistema é degradado ao utilizar o usuário performance_glitch_user

### API Endpoints
- POST /login

---

## Funcionalidade: Carrinho

### História do Usuário
Como usuário,  
Quero adicionar itens ao meu carrinho  
Para comprá-los posteriormente  

### Critérios de Aceitação

#### Cenários Positivos
- O usuário pode adicionar itens ao carrinho
- O usuário pode remover itens do carrinho
- Os itens permanecem no carrinho após atualização da página

#### Cenários Negativos
- O usuário não deve conseguir prosseguir para o checkout com o carrinho vazio
- O usuário não deve acessar o carrinho sem estar autenticado

#### Casos de Borda
- Múltiplos cliques em "Adicionar ao carrinho" não devem duplicar itens
- O comportamento do carrinho deve permanecer consistente após atualização durante o fluxo de checkout
- A sessão deve ser resetada após logout (o carrinho deve ser limpo)

### API Endpoints
- POST /cart
- GET /cart

---

## Funcionalidade: Checkout

### História do Usuário
Como usuário,  
Quero finalizar uma compra  
Para receber meus produtos  

### Critérios de Aceitação

#### Cenários Positivos
- O usuário pode finalizar a compra com dados válidos
- A tela de confirmação do pedido é exibida após a compra

#### Cenários Negativos
- O usuário deve estar logado para realizar o checkout
- O sistema não deve permitir finalizar compra com carrinho vazio
- Os campos obrigatórios (Nome, Sobrenome, CEP) devem ser validados

#### Casos de Borda
- Atualizar a página durante o checkout não deve duplicar o pedido
- Dados inválidos ou incompletos devem impedir a progressão

### API Endpoints
- POST /checkout