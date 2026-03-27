# Requisitos

## Funcionalidade: Login

### História do Usuário
Como usuário,

Desejo fazer login no sistema
Para acessar minha conta

### Critérios de Aceitação

---
- O usuário pode fazer login com credenciais válidas 

# SUCESSO:
-- (aceito com standard_user de user e secret_sauce
de password)

---
- Os campos de e-mail e senha são obrigatórios 

# SUCESSO:
-- (quando NÃO tem os campos de login ou senha preenchidos: Epic sadface: Username is required; Epic sadface: Password is required)

---

### Critérios negativos

- Uma mensagem de erro é exibida para logins inválidos

# ERRO
-- NÃO foi aceito com o user: secret_sauce
 com a seguinte mensagem de erro: Epic sadface: Username and password do not match any user in this service; 
 
 NÃO foi aceito com a senha: senha-errada
 com a seguinte mensagem de erro: Epic sadface: Username and password do not match any user in this service

---
- Usuário bloqueado 
# ERRO
-- Usado com "locked_out_user", com a seguinte mensagem de erro: Epic sadface: Sorry, this user has been locked out.

---
- Os campos de e-mail e senha são obrigatórios 

# ERRO
-- quando NÃO tem os campos de login ou senha preenchidos: Epic sadface: Username is required; Epic sadface: Password is required.

---

## Funcionalidade: Carrinho

### História do Usuário
Como usuário,
Desejo adicionar itens ao meu carrinho
Para comprá-los posteriormente

### Critérios positivos

-- Resultado obtido: Dados persitidos com sucesso, logout e acesso via URL mostram carrinho com itens.

- O usuário pode adicionar itens ao carrinho

# SUCESSO:
-- Todos os itens podem ser adicionados e removidos normalmente

---

- O usuário pode remover itens

# SUCESSO:
-- Pode ser removido todos os itens normalmente

---

- O carrinho permanece após a atualização da página

# SUCESSO:
-- Sim, os itens permanecem depois de atualizar a página.

---

### Critérios negativos


- Fluxo de Checkout e Carrinho Vazio
Checkout sem itens: Tentar clicar no botão "Checkout" quando o carrinho estiver com 0 itens. 

# ERRO

-- permite avançar, o que é considerado uma falha de regra de negócio em um e-commerce real: Checkout: Your Information

--- 

- Campos de Checkout em branco: No formulário de informações (checkout-step-one.html), tentar avançar deixando "First Name", "Last Name" ou "Postal Code" vazios.
 
# ERRO: 

-- permite avançar, o que é considerado uma falha de regra de negócio em um e-commerce real 

---

- Persistência e Manipulação de Sessão
Logout com itens no carrinho: Adicionar itens ao carrinho, fazer Logout e depois Login novamente com o mesmo usuário.

Objetivo: Verificar se o carrinho é limpo ou se os itens persistem (no SauceDemo padrão, a sessão é reiniciada ao deslogar).

Acesso Direto via URL: Tentar acessar a página https://www.saucedemo.com/cart.html sem estar logado.

Resultado esperado: Redirecionamento para a página de login com mensagem de erro.

# ERRO: 
Resultado obtido: página https://www.saucedemo.com/cart.html é acessada normalmente, logout volta com itens normalmente no carrinho.

---

-- Comportamento do "Problem User" (Caso especial do site)


Resultados esperados: Com o "Problem User" (Caso especial do site), já espera-se os erros.

# ERRO: 
Resultados obtidos:

- Só dá pra remover na tela: https://www.saucedemo.com/cart.html (Carrinho)

- Imagens na tela principal são incoerentes(Cachorro Pug)

- Imagens no carrinho não aparecem (Sem imagem) 

- Dá pra adicionar no carrinho apenas os itens: 

Sauce Labs Backpack

Sauce Labs Bike Light

Sauce Labs Onesie

---

- Casos de Borda (Edge Cases)
Múltiplos cliques no "Add to cart": Clicar repetidamente no botão de adicionar antes da transição da UI.

Verificação: O contador do carrinho deve aumentar apenas uma vez por produto, já que o site não trabalha com múltiplas unidades do mesmo item (o botão muda para "Remove").

# SUCESSO:
Resultado obtido: O contador do carrinho aumenta normalmente e o botão muda para "remove"

Refresh na etapa final: Adicionar itens, ir até a página de "Overview" (checkout-step-two.html) e atualizar a página (F5).

Verificação: O sistema deve manter os dados da compra ou retornar ao carrinho com segurança, sem duplicar o pedido.

## Funcionalidade: Finalização da Compra

### História do Usuário
Como usuário,
Desejo concluir uma compra
Para receber meus produtos

### Critérios de Aceitação

-- O usuário deve estar logado

# SUCESSO:
Resultado esperado: Checkout feito apenas quando estiver logado.

Resultado obtido: resultado esperado é obtido.

---
-- O carrinho não pode estar vazio
# ERRO: 
Resultado esperado: Não conseguir finalizar a compra.

Resultado obtido: Compra prosegue com o carrinho vazio.
---
-- A confirmação do pedido deve ser exibida

# SUCESSO:
Resultado esperado: tela de confirmação do pedido aparece.

Resultado obtido: resultado esperado é obtido.

--- 

