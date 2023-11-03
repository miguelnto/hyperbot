# HyperBot

## Configuração inicial e como usar

Requisitos:

- Uma *key* para ativar o bot.
- Uma chave SDK do Mercado Pago.
- Um email que você tenha acesso, e que não esteja conectado em uma conta do Mercado Pago.

Se você tem todos esses requisitos, por favor siga os seguintes passos **na ordem:**

- Use o comando `/activate` com a key. Se você digitou corretamente, o bot alertará que a key foi ativada com sucesso.
- Use o comando `/expires` para checar quando sua key vai expirar. Esse comando pode ser usado no futuro quantas vezes você quiser.
- Use o comando `/configurar` com sua **chave SDK** (sdkkey) e **email**.
.. Se você ou um cliente tiverem problemas na tela de pagamento, então a sua **chave SDK** está incorreta ou seu **email** está inválido. Isso significa que você deve usar o comando `/deletarconfig` para deletar a configuração anterior e então usar o comando `/configurar` novamente.
.. Se você quiser receber com outra conta do Mercado Pago, você vai precisar de outra **chave SDK**, e então usar o comando `/deletarconfig` para deletar a configuração anterior  e configurar novamente com`/configurar`.
-  Use o comando `/checar` para checar se o servidor foi configurado corretamente com a **chave SDK** e o **email**.
- A configuração já foi feita e você pode começar a usar o bot!

## Comandos Principais

#### `/enviar` - envia uma tabela para um produto. 
*Um prompt será aberto para que sejam colocadas as informações essenciais, como nome do produto, descrição, preço e url da thumbnail da tabela. 
Para usar esse comando, por favor leia mais informações [aqui.](#dúvidas-principais)*

#### `/additem` - adiciona um item ao estoque de um produto.
*Esse comando deve ser usado quando você quer criar um novo produto ou adicionar um item para um produto já existente. Você deve passar para o comando as seguintes informações:*
- **nome_produto** (nome do produto), 
- **item** (informações que devem ser enviadas ao usuário quando ele comprar o produto),
- *[opcional]* **qtd** (a quantidade de vezes que esta mesma combinação de produto e item devem ser adicionadas ao estoque). Por padrão, esse valor será 1. Não use um valor maior que 10. Mais informações [aqui.](#dúvidas-principais)

#### `/removeproduto` - remove todos os itens do estoque de um produto.

*Esse comando deve ser usado quando você quer deletar TOTALMENTE o estoque de um produto. A única coisa a ser passada é o **nome_produto** (nome do produto).*

#### `/info` - mostra todas as informações de um produto.

*Esse comando mostra o nome do produto e a quantidade de itens restante no estoque. A única coisa a ser passada é o **nome_produto** (nome do produto).*

#### `/listproduto` - mostra todos os produtos disponíveis na loja.

*Esse comando mostra o nome e a quantidade de itens no estoque de todos os produtos presentes na loja. Nada precisa ser passado.*

#### `/feedback` - comando em manutenção.

#### `/entrega` - registra a entrega de um produto.

*Esse comando registra a entrega de um produto manualmente. 
**Atenção: para que funcione corretamente, no seu servidor deve existir um canal que termine com a palavra entregas. Exemplo: #hyper-entregas, #super-entregas, #entregas, etc..*** 
*Você deve passar para o comando as seguintes informações:*

- **nome_produto** (nome do produto)
- **qtd** (a quantidade de itens de um produto que foi enviada)
- **preco** (o preço do total comprado). `Exemplo: 2.10, 3.15, etc...`
- **data** (a data da entrega do produto). Deve ser colocada no seguinte formato: "dia/mes/ano hora/minuto/segundo"
` Exemplo: 21/02/2023 13:47:15`
- *[opcional]* **avaliacao** (o número no qual sua entrega foi avaliada, deve ser um número de 0 a 5). Se esse número não for passado, a mensagem que aparecerá é "Nenhuma avaliação enviada".
- *[opcional]* **desconto** (o valor do desconto dado) Caso não passado, será igual a 0.00.

#### `/getdb` - devolve um arquivo txt da database.

*Esse comando envia um arquivo .txt contendo todos os itens do estoque. Nada precisa ser passado.*

#### `/avaliar` - comando em manutenção.
#### `/removebyid` - comando em manutenção.
#### `/carregar` - comando em manutenção.

## Dúvidas principais 

### Comandos
Ao usar quaisquer comandos do bot, existem algumas regras principais:

- O **preço** de um produto SEMPRE deve ser escrito com um ponto e nunca usando vírgula. `Exemplo: 2.15 ao invés de 2,15 para representar R$2,15.`
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
- Em qualquer comando, não é recomendável usar um valor maior que 50 para o parâmetro *qtd*. Se você quer que algum produto tenha um estoque "infinito", é recomendado usar o comando `/additem` com *qtd* igual a 50 quantas vezes forem necessário. Enquanto está sendo executado, não rode nenhum outro comando, e ao terminar, espere 5 segundos e rode novamente.
### Keys
Por favor confira as informações relevantes sobre as keys abaixo:
- Se você tem **2 ou mais** keys, por favor **NÃO** use o comando `/activate` várias vezes seguidas. Esse comando deve ser usado apenas **UMA VEZ** por mês, um ou dois dias antes de sua key expirar, usando uma nova key. *Detalhe: Não tem problema em esperar sua key expirar para usar o comando `/activate` novamente.*
- Nenhum comando ou interação com o bot será possível se o bot não estiver ativado com a key. Se você quiser que o bot continue funcionando sem problemas, sempre ative seu server com uma nova key um dia antes da key expirar.
- As keys só funcionam uma vez. Se você tentar usar uma key usada, você vai receber uma mensagem de erro.
- O horário da expiração da key é de acordo com o horário de brasília. Se sua key expira em `22/12/2031`, e são `00:01` do dia `22/12/2031` no horário de brasília, sua key já expirou.
