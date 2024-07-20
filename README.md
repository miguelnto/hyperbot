<div align="center">

# HyperBot

**A solução moderna para o mercado digital, com praticidade e simplicidade.**

![hyperbot repository thumbnail](hyperui.png)

[![produto-hyperstore](https://img.shields.io/badge/produto%20hyperstore-%232B2F33.svg?style=for-the-badge&logoColor=white)](https://discord.gg/M7FURN5R88)
![discord-bot](https://img.shields.io/badge/discord%20bot-%235865F2.svg?style=for-the-badge&logo=discord&logoColor=white)

</div>

---

## Sumário

- [Configuração inicial](#configuração-inicial)
- [Começando a usar](#começando-a-usar)
- [Como obter a chave SDK (ou token de acesso)](#como-obter-o-token-de-acesso-chave-sdk)
- [Comandos principais](#comandos-principais)
- [Comandos - Configurações](#comandos---configurações)
- [Comandos - Keys](#comandos---keys)
- [Keys](#keys)
- [Dúvidas principais](#dúvidas-principais)
- [Contato](#contato)


## Configuração inicial

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

Sempre que um comprador faz uso do BOT através do botão da compra, um novo canal (que apenas o vendedor e o comprador podem ver) deve ser criado para que o comprador prossiga com a compra. Para isso, um categoria com o nome `carrinho` deve ser criada. Além disso, deve ser criado um canal criado `entregas`, e outro chamado `vendas`. No canal `entregas`, serão registrados logs de vendas feitas, sem informações sobre o comprador, e no canal `vendas`, haverá logs com informações sobre o comprador.
**Resumindo, seu servidor precisa ter:**

- **Um canal com o nome `#entregas`**
- **Uma categoria com o nome `#carrinho`**
- **Opcionalmente, um canal com o nome `#vendas`**


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

## Comandos principais

### ⚙️ /anuncios

Envia um painel para que você gerencie seus anúncios.
Esse comando não possui parâmetros, pois ele já envia um painel interativo, assim como o abaixo:

![hyperbot_anuncios](hyperbot-exemplo.png)

---

### ⚙️ /criar_anuncio - `nome`, `descricao`, `imgurl`

*Cria um anúncio para sua loja.*

- `nome` - O nome (ou título) do anúncio.
- `descricao` - A descrição do anúncio.
- `imgurl` - A URL da thumbnail do anúncio.

---

### ⚙️ /listar_itens - `anuncio_id`

*Esse comando envia um arquivo .csv contendo todos os itens de um anúncio.*

Em cada linha, existem 3 informações: ID do item, nome do item, e o conteúdo do item, nesta ordem. 

- `anuncio_id` - O ID de um anúncio no seu servidor. Este ID pode ser obtido no painel do comando `/anuncios`.

--- 

### ⚙️ /enviar_anuncio - `anuncio_id`, `preco`, `cargo`

*Esse comando envia um anúncio no canal em que ele foi usado.*
Perceba que o preço do anúncio é um parâmetro passado **no momento do envio.** Isso significa que os vendedores são livres para mudar os preços de seus anúncios. Além disso, todos os compradores **irão receber um cargo** ao fazer a compra de um anúncio, a depender do parâmetro `cargo`. Caso você não queira que um comprador receba um cargo extra, você pode colocar um **cargo padrão** para membros no parâmetro `cargo`. 

- `anuncio_id` - O ID de um anúncio no seu servidor. Este ID pode ser obtido no painel do comando `/anuncios`.
- `preco` - O preço atrelado ao anúncio. Pode ser escrito nos seguintes formatos: `9,70`, `9.70`.
- `cargo` - O cargo que será dado ao comprador quando a comprar for aprovada.

---

### ⚙️ /atualizar_anuncio - `nome`, `descricao`, `imgurl`, `anuncio_id`

Esse comando atualiza todas as informações no anúncio, dado o ID de um anúncio. Este ID pode ser obtido no painel do comando `/anuncios`.

- `nome` - O novo nome do anúncio.
- `descricao` - A nova descrição do anúncio.
- `imgurl` - A nova URL da thumbnail do anúncio.
- `anuncio_id` - O ID do anúncio a ser mudado.

---

## Comandos - Configurações

### ⚙️ `/configurar` - `sdkkey`, `email`

Configura o bot com a chave SDK + Email.

- `sdkkey` - A chave SDK, que pode ser obtida em [como obter a chave SDK (ou token de acesso).](#como-obter-o-token-de-acesso-chave-sdk)
- `email` - Um email que você tenha acesso. Pode ser o mesmo da sua conta do Mercado Pago.

### ⚙️ `/deletar_config`

*Deleta a configuração da chave SDK + Email. Esse comando deve ser usado quando você pretende reconfigurar o servidor com uma nova chave SDK e email.* Esse comando não possui parâmetros.

### ⚙️ `/checar`

*Checa se o servidor está corretamente configurado com a chave SDK + Email. Caso tudo esteja certo, o BOT enviará as informações presentes na configuração.* Esse comando não possui parâmetros.

## Comandos - Keys

### ⚙️ `/activate`

Ativa o servidor com uma key.

- `key` - A key a ser usada.

### ⚙️ `/expires`

Mostra a data de expiração da key atual. Esse comando não possui parâmetros.

## Keys

> [!IMPORTANT]
> Keys são usadas para a ativação da aplicação. Confira a seguir informações essenciais sobre as keys:
- Você deve usar apenas uma key e **uma vez** por mês. Se você tem 2 ou mais keys, aguarde até 1 dia antes da data de expiração da key para usar uma nova. Se você usar uma key e em seguida usar outra, isso não extenderá o prazo de expiração.
- Uma key funciona só uma vez. Se você tentar usar uma key usada, você vai receber uma mensagem alertando que a key não pôde ser usada para ativar o BOT.
- Nenhum comando ou interação com o bot será possível se o BOT não estiver ativado com a key.

## Dúvidas principais 

### Sobre comandos

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

## Contato

🚀 **Esse BOT foi desenvolvido com carinho por Miguel, desenvolvedor full stack.**

Todos os links de contato estão abaixo. Vem trocar uma ideia comigo! 🖖

- **Email: miguelup01@outlook.com**
- **Servidor: [HyperStore](https://discord.gg/M7FURN5R88)**
- **Discord: miguelnto**
