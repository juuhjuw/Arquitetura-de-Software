# Análise de Estilos Arquiteturais

## 1. Cliente-servidor

### Conceito e definição

O estilo arquitetural cliente-servidor organiza o sistema em dois papéis principais: **cliente** e **servidor**. O cliente é responsável por fazer solicitações de serviços ou recursos, enquanto o servidor recebe essas solicitações, realiza o processamento necessário e retorna uma resposta.

Na prática, o cliente pode ser uma aplicação web, um aplicativo de celular ou outro sistema, enquanto o servidor concentra serviços, regras de negócio e, às vezes, o acesso ao banco de dados. A comunicação normalmente ocorre por meio de uma rede utilizando protocolos como HTTP ou HTTPS.

Um exemplo simples é um site de compras. O navegador do usuário atua como cliente e envia uma solicitação ao servidor. O servidor processa a requisição, consulta os dados necessários e devolve uma resposta para o navegador.

### Casos de uso comuns

O modelo cliente-servidor é bastante utilizado em sistemas que precisam centralizar dados e serviços.

**Primeiro exemplo — WhatsApp:**
Quando uma pessoa envia uma mensagem pelo WhatsApp, o celular funciona como cliente e envia a mensagem para os servidores do WhatsApp. O servidor recebe e processa a mensagem para que ela possa chegar ao celular da outra pessoa.

**Segundo exemplo — Netflix:**
Quando uma pessoa escolhe um filme ou série para assistir, o celular, computador ou televisão funciona como cliente e solicita o conteúdo aos servidores da Netflix. Os servidores enviam os dados necessários para que o vídeo possa ser reproduzido no dispositivo.

### Principais vantagens

* **Centralização:** os dados e serviços podem ser concentrados nos servidores, facilitando o gerenciamento.
* **Segurança:** é possível controlar o acesso aos recursos diretamente no servidor.
* **Manutenção facilitada:** alterações nas regras de negócio podem ser realizadas no servidor sem necessariamente modificar todos os clientes.
* **Compartilhamento de recursos:** diversos clientes podem utilizar os mesmos serviços e dados.
* **Escalabilidade:** servidores podem ser ampliados ou distribuídos para atender a um número maior de usuários.

### Principais desvantagens

* **Dependência do servidor:** se o servidor estiver indisponível, os clientes podem perder o acesso aos serviços.
* **Possibilidade de gargalo:** um servidor sobrecarregado pode prejudicar o desempenho de todos os clientes.
* **Dependência da rede:** problemas de conexão podem impedir ou dificultar a comunicação entre cliente e servidor.
* **Custo de infraestrutura:** servidores precisam ser configurados, monitorados e mantidos.
* **Ponto central de falha:** quando a arquitetura depende de um único servidor, uma falha nele pode afetar todo o sistema.

---

## 2. Publicador/assinante (Pub-Sub)

### Conceito e definição

O estilo arquitetural **Publicador/assinante (Pub-Sub)** é baseado na troca de mensagens entre componentes por meio de **tópicos ou canais**. Nesse modelo, o publicador envia uma mensagem para um determinado tópico, sem precisar conhecer diretamente quem irá recebê-la.

Os assinantes demonstram interesse em determinados tópicos e recebem as mensagens publicadas neles. Um componente intermediário, chamado de **broker**, pode ser responsável por receber, organizar e encaminhar as mensagens aos assinantes.

Essa separação permite que publicadores e assinantes funcionem de maneira independente. O publicador não precisa saber quantos assinantes existem ou quais são eles.

### Casos de uso comuns

O modelo Pub-Sub é recomendado principalmente para sistemas que precisam distribuir eventos ou informações para vários componentes de forma desacoplada.

**Primeiro exemplo — YouTube:**
Quando um canal publica um novo vídeo, os usuários que estão inscritos nele podem receber uma notificação. O canal funciona como publicador, enquanto os usuários inscritos são os assinantes que recebem a informação.

**Segundo exemplo — Aplicativos de entrega:**
Quando o status de um pedido muda, como de "em preparação" para "saiu para entrega", essa informação pode ser publicada para diferentes partes do sistema. O aplicativo do cliente pode atualizar o status e o sistema de notificações pode enviar um aviso ao usuário.

### Principais vantagens

* **Baixo acoplamento:** publicadores e assinantes não precisam conhecer diretamente uns aos outros.
* **Escalabilidade:** novos assinantes podem ser adicionados sem alterar o publicador.
* **Flexibilidade:** uma mesma mensagem pode ser recebida por vários consumidores.
* **Comunicação assíncrona:** os componentes podem trocar informações sem que o publicador precise aguardar diretamente o processamento de cada assinante.
* **Facilidade de integração:** diferentes serviços e aplicações podem utilizar o mesmo sistema de mensagens para trocar eventos.

### Principais desvantagens

* **Maior complexidade:** a presença de um broker e de comunicação por mensagens pode tornar o sistema mais difícil de entender e administrar.
* **Dependência do sistema de mensagens:** problemas no broker podem afetar a comunicação entre os componentes.
* **Dificuldade de depuração:** pode ser mais difícil acompanhar o caminho de uma mensagem quando existem muitos publicadores e assinantes.
* **Gerenciamento de mensagens:** é necessário lidar com questões como mensagens duplicadas, mensagens perdidas e ordem de processamento.
* **Monitoramento mais complexo:** sistemas com muitos tópicos e consumidores exigem ferramentas de monitoramento e controle.
