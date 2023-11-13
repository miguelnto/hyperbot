# HyperBot

![hyperbot repository thumbnail](hyperui.png)

**A solução moderna para o mercado digital, com praticidade e simplicidade.**


## Configuração inicial e como usar

Requisitos:

- Uma *key* para ativar o bot.
- Uma chave SDK do Mercado Pago.
- Um email que você tenha acesso, e que não esteja conectado em uma conta do Mercado Pago.

Se você tem todos esses requisitos, por favor siga os seguintes passos **na ordem:**

- Use o comando `/activate` com a key. Se você digitou corretamente, o bot alertará que a key foi ativada com sucesso.
- Use o comando `/expires` para checar quando sua key vai expirar. Esse comando pode ser usado no futuro quantas vezes você quiser.
- Use o comando `/configurar` com sua **chave SDK** (sdkkey) e **email**.
  - Se você ou um cliente tiverem problemas na tela de pagamento, então a sua **chave SDK** está incorreta ou seu **email** está inválido. Isso significa que você deve usar o comando `/deletarconfig` para deletar a configuração anterior e então usar o comando `/configurar` novamente.
  - Se você quiser receber com outra conta do Mercado Pago, você vai precisar de outra **chave SDK**, e então usar o comando `/deletarconfig` para deletar a configuração anterior  e configurar novamente com `/configurar`.
-  Use o comando `/checar` para checar se o servidor foi configurado corretamente com a **chave SDK** e o **email**.
- A configuração já foi feita e você pode começar a usar o bot!

## Começando a usar

1. Crie um canal cujo nome termine com a palavra `entregas` e outro que termine com a palavra `vendas`. Nesses canais, todas as suas vendas aprovadas ficarão registradas.

2. Crie uma categoria cujo nome termine com a palavra `carrinho`. Nessa categoria, serão criados carrinhos (canais) que os usuários irão acessar para realizar a compra.

3. Crie seu primeiro produto com o comando `/additem`, que cria um produto no estoque a partir do nome e do conteúdo. Confira mais sobre esse comando em [comandos.](#comandos-principais)

![Adicione um item](additem.png)
![Item adicionado com sucesso](additemresult.png)

4. Envie um anúncio no estilo Embed para o seu produto com o comando `/anuncio`. Vai abrir um prompt para que você configure a sua tabela.
 - O título do seu produto ao enviar deve ser exatamente igual ao nome adicionado no estoque. (Letras maiúsculas ou minúsculas não importam)
 - A quantidade disponível no estoque é obtida automaticamente!

![Prompt para tabela](tabelapreenchida.png)

![Anúncio de teste](anuncioteste.png)

5. E aqui está seu primeiro anúncio! Veja mais comandos e mais dicas para agilizar o processo de anunciar em [comandos.](#comandos-principais)

## Como obter o token de acesso (chave SDK)

O token de acesso (conhecido como chave SDK nesta documentação) é o que permite que sejam criados novas cobranças de pagamentos em seu nome, e por isso é necessário para a aplicação do HyperBot. Esse token é guardado na base de dados de forma segura o suficiente para que apenas o HyperBot tenha acesso, quando necessário. Veja abaixo como obter este token (dura em torno de 5 minutos!)

1. Você deve ter uma conta no Mercado Pago. Se você ainda não tem, faça o download do app no seu celular e prossiga com a criação da conta, que também não demora mais que 5 minutos. Não tem muita burrocracia e requer poucos passos.
2. Você deve acessar o site oficial do [Mercado Pago.](https://www.mercadopago.com.br/home) Ao entrar no site, será pedido que você faça uma verificação para confirmar a sua identidade, por questões de segurança. Prossiga com a verificação.
3. Após feito isso, você será direcionado para uma página parecida com esta:
   
![Página inicial do MercadoPago](tutorial_pt3.gif)

4. Você deve ir até "Meu negócio", e depois "Configurações", como mostrado no GIF acima.
5. Aparecerá uma tela para configurar aplicação, e você deve preencher da seguinte forma:
  - Em nome da aplicação, coloque o nome da sua loja/negócio.
  - Marque pagamentos online.
  - Marque que você está usando uma plataforma e-commerce.
  - Na opção da plataforma que será usada para integrar, selecione WooCommerce ou Outra Plataforma. Recomendo selecionar outra plataforma.
  - Abaixo da opção acima, selecione CheckoutPro.
  - Marque o botão de confirmação e também "Não sou um robô".

![Tela de configuração da aplicação](tutorial_pt5.png)

Acima está uma figura detalhando o que você deve fazer.

6. Você deve então ativar as credenciais, e informar alguns detalhes sobre o seu negócio, como segue abaixo.

![Ativar credenciais](ativarcredenciais.png)
![Ativar credenciais 2](ativarcredenciais2.png)

7. Finalmente, clique em credenciais de produção, e então copie o Access Token, que é a sua chave SDK (ou token de acesso). Agora você já tem sua chave SDK e pode seguir para a [configuração inicial.](#configuração-inicial-e-como-usar)

![Credenciais de produção](credenciais.png)
![Credenciais de produção 2](credenciais2.png)

## Comandos Principais

#### `/anuncio` - envia uma anúncio para um produto. 
*Um prompt será aberto para que sejam colocadas as informações essenciais, como nome do produto, descrição, preço e url da thumbnail da tabela. 
Para usar esse comando, por favor [leia mais informações aqui.](#dúvidas-principais)*

#### `/additem` - adiciona um item ao estoque de um produto.

*Esse é o comando principal que deve ser usado para adicionar itens na loja.*
- **nome_produto** - o nome do produto.
- **item** - informações que devem ser enviadas ao usuário quando ele comprar o produto.
- **qtd** - a quantidade de vezes que este mesmo item deve ser adicionado ao estoque. Por padrão, esse valor será 1. Evite usar valores maiores que 100.

#### `/removeproduto` - remove todos os itens do estoque de um produto pelo nome.

*Esse comando deve ser usado quando você quer deletar TOTALMENTE o estoque de um produto pelo nome.*
- **nome_produto** - o nome do produto.

#### `/removeitem` - remove um item do estoque pelo ID.

*Esse comando deve ser usado quando você quer deletar um item do estoque pelo id.*
- **id_do_item** - o id do tem.

#### `/clear` - limpa completamente a loja, deletando todos os estoques.

*Cuidado. Este comando limpa a loja completamente, excluindo TODOS os itens. A configuração do servidor não é deletada.*

#### `/listprodutos` - mostra todos os produtos disponíveis na loja.

*Esse comando mostra todos os produtos presentes na loja, com seu nome e quantidade disponível no estoque.*

#### `/entrega` - registra a entrega de um produto.

*Esse comando registra a entrega de um produto manualmente.*
**Atenção: para que funcione corretamente, no seu servidor deve existir um canal que termine com a palavra entregas. Exemplo: #hyper-entregas, #super-entregas, #entregas, etc..**

- **nome_produto** (nome do produto)
- **qtd** (a quantidade de itens de um produto que foi enviada)
- **preco** (o preço do total comprado). `Exemplo: 2,30, 3,15`
- **data** (a data da entrega do produto). Deve ser colocada no seguinte formato: "dia/mes/ano hora/minuto/segundo"
` Exemplo: 21/02/2023 13:47:15`
- *[opcional]* **avaliacao** (o número no qual sua entrega foi avaliada, deve ser um número de 0 a 5). Se esse número não for passado, a mensagem que aparecerá é "Nenhuma avaliação enviada".
- *[opcional]* **desconto** (o valor do desconto dado) Caso não passado, será igual a 0.00.

#### `/getdb` - devolve um arquivo txt do estoque.

*Esse comando envia um arquivo .txt contendo todos os itens da loja.*

#### `carregar` - carrega a loja com um arquivo txt ou csv.

Um arquivo txt ou csv deve ser enviado EXATAMENTE antes de usar esse comando.

*Cuidado: esse comando limpa a loja completamente, excluindo TODOS os itens, e então adiciona itens na loja de acordo com o conteúdo do arquivo txt ou csv.* 

**Seu arquivo deve estar no seguinte formato, onde a primeira coluna é o nome dos itens e a segunda é o item em si (o conteúdo do item):**

![Arquivo CSV do google planilhas](carregar.png)

#### `additens` - comando em manutenção.

Um arquivo txt ou csv deve ser enviado EXATAMENTE antes de usar esse comando.
*Cuidado: esse comando adiciona itens na loja de acordo com o conteúdo do arquivo txt ou csv. Nenhum item anteriormente presente na loja é excluido.* 

**Seu arquivo deve estar no mesmo formato necessário para o comando `/carregar`.**

## Comandos - Configurações

#### `/configurar` - configura o bot com a chave SDK + email.

- **sdkkey** - A chave SDK, que pode ser obtida em ....
- **email** - Um email que você tenha acesso. Não pode ser o mesmo da sua conta do Mercado Pago.

#### `/deletarconfig` - deleta a configuração da chave SDK + email.

*Esse comando deve ser usado quando você pretende reconfigurar o servidor com uma nova chave SDK e email.*

#### `/checar` - checa se o servidor está corretamente configurado com a chave SDK + email.

*Caso tudo esteja certo, o BOT enviará as informações presentes na configuração.*

## Comandos - Keys

#### `/activate` - ativa o servidor com uma key.

- **key** - A key a ser usada.

#### `/expires` - mostra a data de expiração da key atual.

## Keys

Keys são usadas para a ativação da aplicação, com o intuito de manter a organização de forma prática e permitir a distribuição do uso da aplicação. Confira a seguir informaçãoes essenciais sobre as keys:

- Você deve usar apenas uma key e **uma vez** por mês. Se você tem 2 ou mais keys, aguarde até 1 ou 2 dias antes da data de expiração da key para usar uma nova. Se você usar uma key e em seguida usar outra, isso não extenderá o prazo de expiração.
- Uma key funciona só uma vez. Se você tentar usar uma key usada, você vai receber uma mensagem de erro.
- O horário da expiração da key é de acordo com o horário de brasília. Se sua key expira em `22/12/2031`, e são `00:01` do dia `22/12/2031` no horário de brasília, sua key já expirou.
- Nenhum comando ou interação com o bot será possível se o seu servidor não estiver ativado com a key.

## Dúvidas principais 

### Comandos

**Ao usar quaisquer comandos do bot, existem algumas regras principais:**

- Para adicionar quebras de linha na **descrição** de um produto, use "\n". 
Por exemplo:
```
Esse produto contém:
Bananas
Morangos
Uvas
```
Para obter esse tipo de **descrição**, você deve escrever: 
`Esse produto contém:\nBananas\nMorangos\nUvas`.

- Uma **url para thumbnail** SEMPRE deve ser uma página que exibe apenas uma imagem. Exemplo: `https://upload.wikimedia.org/wikipedia/commons/7/74/White_domesticated_duck,_stretching.jpg`
