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
- [Contato](#contato)


## Configuração inicial

Requisitos:

- Uma *key* para ativar o bot.
- Uma chave SDK do Mercado Pago.
- Um email que você tenha acesso, e que não esteja conectado em uma conta do Mercado Pago.

Se você tem todos esses requisitos, por favor siga os seguintes passos **na ordem:**

**1. Configure a key:**
  - Convide o BOT para seu servidor usando o link de convite.
  - Use o comando `/activate` junto com sua key para ativar o BOT. Se você digitou corretamente, o BOT alertará que a key foi ativada com sucesso.
  > Exemplo: `/activate "7Z8V-LIFO-2W5T"`
  -  Use o comando `/expires` para checar quando sua key vai expirar. Esse comando pode ser usado a qualquer momento para te deixar informado.

**2. Configure a chave SDK.**
  - Use o comando `/configurar` com sua **chave SDK** e **Email**.
  - Se você ou um cliente tiverem problemas na tela de pagamento, então a sua **chave SDK** não é válida. Certifique-se de que você a digitou corretamente. Isso significa que você deve usar o comando `/deletarconfig` para deletar a configuração anterior e então usar o comando `/configurar` novamente.
  - Se você quiser receber com outra conta do Mercado Pago, você vai precisar de outra **chave SDK**, e então usar o comando `/deletarconfig` para deletar a configuração anterior e configurar novamente com `/configurar`.
  -  Use o comando `/checar` para checar as informações atualizadas de **chave SDK** e **Email**.
  - A configuração já foi feita e você pode começar a usar o bot!

## Começando a usar

Existe um pouco mais de configuração **no servidor** que deve ser feita por parte do vendedor (dono do servidor). Antes vamos falar um pouco sobre como o BOT funciona na prática.
Sempre que um comprador faz uso do BOT através clicando no botão de compra do anúncio, um novo canal (que apenas o vendedor e o comprador podem ver) será criado para que o comprador prossiga com a compra. Para isso, um categoria com o nome `carrinho` deve ser criada. Não coloque emojis ou caracteres adicionais, o nome da categoria deve ser apenas `carrinho`. Nesta categoria, estarão listados os pedidos em aberto como canais. Configure a categoria `carrinho` para que **apenas você, o vendedor, pode ter acesso de visibilidade aos canais desta categoria.** Não se preocupe, o BOT dará permissões de visibilidade apenas para o vendedor assim que ele clicar no botão da compra! Além disso, deve ser criado um canal criado `entregas`, e outro chamado `vendas`. No canal `entregas`, serão registrados logs de vendas feitas, sem informações sobre o comprador, e no canal `vendas`, haverá logs com informações sobre o comprador. É interessante que os membros do seu servidor tenham permissão para ver o canal `entregas`, mas não o canal `vendas`, apesar de que isso fica ao critério do vendendor (dono do servidor).

**Resumindo, seu servidor precisa ter:**

- **Um canal com o nome `entregas`** (Preferencialmente, com visibilidade pública, para todos os membros)
- **Uma categoria com o nome `carrinho`** (Com visibilidade privada para você, o vendedor)
- **Um canal com o nome `vendas`** (Preferencialmente, com visibilidade privada para você, o vendedor)


## Como obter o token de acesso (chave SDK)

O token de acesso (conhecido como chave SDK nesta documentação) é o que permite que sejam criados novas cobranças de pagamentos em seu nome, e por isso é necessário para a aplicação do HyperBot. Esse token é guardado na base de dados de forma segura o suficiente para que apenas **você, o vendedor**, e o **HyperBot** tenham acesso, quando necessário. Veja abaixo como obter este token (dura em torno de 5 minutos!)

> Tenha em mente que nossa equipe pode acompanhar você para ajudar-lhe a obter esta chave SDK, via ticket (canal de texto) ou ticket de voz (canal de voz). Você pode abrir um ticket no canal `abrir-ticket` sempre que desejar.

Por favor leia os passos abaixo com atenção. Repita do início caso necessário.

1. Você deve ter uma conta no Mercado Pago. Se você ainda não tem, faça o download do app no seu celular e prossiga com a criação da conta, que não demora muito mais que 5 minutos. Exige pouca burrocracia e requer poucos passos. Note que esta aplicação (HyperBot) não tem nenhum tipo de afiliação com o Mercado Pago, apenas fazendo uso do serviço.
2. Agora, você deve acessar o site oficial do [Mercado Pago.](https://www.mercadopago.com.br/home) Ao entrar no site, será pedido que você faça uma verificação para confirmar a sua identidade, por questões de segurança. Prossiga com a verificação.
3. Após feito isso, você será direcionado para uma página parecida com esta:
   
![Página inicial do MercadoPago](tutorial_pt3.gif)

4. Você deve ir até "Meu negócio", e depois "Configurações", como mostrado no GIF acima.
5. Aparecerá uma tela para configurar aplicação, e você deve preencher da seguinte forma:
  - Em nome da aplicação, coloque o nome da sua loja ou negócio.
  - Marque pagamentos online.
  - Marque que você está usando uma plataforma e-commerce.
  - Na opção da plataforma que será usada para integrar, selecione Outra Plataforma.
  - Abaixo da opção acima, selecione CheckoutPro.
  - Marque o botão de confirmação e também "Não sou um robô".
  - Abaixo está uma figura detalhando o que você deve fazer.

![Tela de configuração da aplicação](tutorial_pt5.png)

6. Você deve então ativar as credenciais, e informar alguns detalhes sobre o seu negócio, como segue abaixo.

![Ativar credenciais](ativarcredenciais.png)
![Ativar credenciais 2](ativarcredenciais2.png)

7. Finalmente, clique em credenciais de produção, e então copie o Access Token, que é a sua chave SDK (ou token de acesso). Agora você já tem sua chave SDK e pode seguir para a [configuração inicial.](#configuração-inicial-e-como-usar). Confira o passo a passo de forma visual abaixo.

![Credenciais de produção](credenciais.png)
![Credenciais de produção 2](credenciais2.png)

## Comandos principais

#### ⚙️ /anuncios

Envia um painel para que você gerencie seus anúncios.
Esse comando não possui parâmetros, pois ele já envia um painel interativo, assim como o abaixo:

![hyperbot_anuncios](hyperbot-exemplo.png)

---

#### ⚙️ /criar_anuncio - `nome`, `descricao`, `imgurl`

*Cria um anúncio para sua loja.*

- `nome` - O nome (ou título) do anúncio.
- `descricao` - A descrição do anúncio.
- `imgurl` - A URL da thumbnail do anúncio.

---

#### ⚙️ /listar_itens - `anuncio_id`

*Esse comando envia um arquivo .csv contendo todos os itens de um anúncio.*

Em cada linha, existem 3 informações: ID do item, nome do item, e o conteúdo do item, nesta ordem. 

- `anuncio_id` - O ID de um anúncio no seu servidor. Este ID pode ser obtido no painel do comando `/anuncios`.

--- 

#### ⚙️ /enviar_anuncio - `anuncio_id`, `preco`, `cargo`

*Esse comando envia um anúncio no canal em que ele foi usado.*
Perceba que o preço do anúncio é um parâmetro passado **no momento do envio.** Isso significa que os vendedores são livres para mudar os preços de seus anúncios. Além disso, todos os compradores **irão receber um cargo** ao fazer a compra de um anúncio, a depender do parâmetro `cargo`. Caso você não queira que um comprador receba um cargo extra, você pode colocar um **cargo padrão** para membros no parâmetro `cargo`. 

- `anuncio_id` - O ID de um anúncio no seu servidor. Este ID pode ser obtido no painel do comando `/anuncios`.
- `preco` - O preço atrelado ao anúncio. Pode ser escrito nos seguintes formatos: `9,70`, `9.70`.
- `cargo` - O cargo que será dado ao comprador quando a comprar for aprovada.

---

#### ⚙️ /atualizar_anuncio - `nome`, `descricao`, `imgurl`, `anuncio_id`

Esse comando atualiza todas as informações no anúncio, dado o ID de um anúncio. Este ID pode ser obtido no painel do comando `/anuncios`.

- `nome` - O novo nome do anúncio.
- `descricao` - A nova descrição do anúncio.
- `imgurl` - A nova URL da thumbnail do anúncio.
- `anuncio_id` - O ID do anúncio a ser mudado.

---

## Comandos - Configurações

#### ⚙️ `/configurar` - `sdkkey`, `email`

Configura o bot com a chave SDK + Email.

- `sdkkey` - A chave SDK, que pode ser obtida em [como obter a chave SDK (ou token de acesso).](#como-obter-o-token-de-acesso-chave-sdk)
- `email` - Um email que você tenha acesso. Pode ser o mesmo da sua conta do Mercado Pago.

#### ⚙️ `/deletar_config`

*Deleta a configuração da chave SDK + Email. Esse comando deve ser usado quando você pretende reconfigurar o servidor com uma nova chave SDK e email.* Esse comando não possui parâmetros.

#### ⚙️ `/checar`

*Checa se o servidor está corretamente configurado com a chave SDK + Email. Caso tudo esteja certo, o BOT enviará as informações presentes na configuração.* Esse comando não possui parâmetros.

## Comandos - Keys

#### ⚙️ `/activate`

Ativa o servidor com uma key.

- `key` - A key a ser usada.

#### ⚙️ `/expires`

Mostra a data de expiração da key atual. Esse comando não possui parâmetros.

## Keys

> [!IMPORTANT]
> Keys são usadas para a ativação da aplicação. Confira a seguir informações essenciais sobre as keys:
- Você deve usar apenas uma key e **uma vez** por mês. Se você tem 2 ou mais keys, aguarde até 1 dia antes da data de expiração da key para usar uma nova. Se você usar uma key e em seguida usar outra, isso não extenderá o prazo de expiração.
- Uma key funciona só uma vez. Se você tentar usar uma key usada, você vai receber uma mensagem alertando que a key não pôde ser usada para ativar o BOT.
- Nenhum comando ou interação com o bot será possível se o BOT não estiver ativado com a key.

---

## Como adquirir

**Você pode adquirir este BOT oficialmente no nosso [canal oficial do Discord.](https://discord.gg/M7FURN5R88) Você também encontrará o histórico de atualizações e poderá entrar em contato com o suporte.**

[![produto-hyperstore](https://img.shields.io/badge/adquirir%20produto-%232B2F33.svg?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/M7FURN5R88)
![suporte-e-garantia](https://img.shields.io/badge/%E2%9C%94%20garantia%20e%20%20suporte-%23107C10.svg?style=for-the-badge&logoColor=white)

## Contato

**Nos links abaixo, você pode entrar em contato comigo ou fazer parte do servidor oficial deste BOT:**

- **Servidor: [HyperStore](https://discord.gg/M7FURN5R88)**
- **Discord: miguelnto**
