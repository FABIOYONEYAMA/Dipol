## Sobre

**O RabbitMQ** é um **software de enfileiramento de mensagens** também conhecido como agente de mensagens ou gerenciador de filas. É um software onde **são definidas filas, às quais os aplicativos se conectam para transferir uma mensagem ou mensagens.**

# Tabela de Conteúdo
- [Tabela de Conteúdo](#tabela-de-conteúdo)
  - [Faturamento](#faturamento)
  - [Instâncias](#instâncias)
  - [RabbitMQ](#rabbitmq)
    - [RabbitMQ: Desenvolvimento](#rabbitmq-desenvolvimento)
      - [Configurando o Peering VPC](#configurando-o-peering-vpc)
    - [RabbitMQ: Homologação](#rabbitmq-homologação)
      - [Configurando o Peering VPC](#configurando-o-peering-vpc-1)
    - [RabbitMQ: Produção](#rabbitmq-produção)
      - [Configurando o Peering VPC](#configurando-o-peering-vpc-2)

## Faturamento

**A taxa de uso é cobrada mensalmente**, **os planos flexíveis** para todas as suas necessidades.

## Instâncias

Abaixo é informada as **instâncias dos ambientes** de **DESENVOLVIMENTO, HOMOLOGAÇÃO e PRODUÇÃO**.

Name                          | Type                | Environment     | Region             | Version     |
----------------------------- | --------------------| ----------------| ------------------ |------------ |
gc5000916-dev                 | CloudAMQP Instances | Desenvolvimento | southamerica-east1 | V 4.0.5     |
gc5000917-hom                 | CloudAMQP Instances | Homologação     | southamerica-east1 | V 4.0.5     |
gc5000034-prod                | CloudAMQP Instances | Produção        | southamerica-east1 | V 4.0.5     |
rabbitmq-5000034-private      | CloudAMQP Instances | Produção        | southamerica-east1 | V 3.13.7    |

## RabbitMQ

O Serviço será utilizado como **agente de mensagens ou gerenciador de filas** dos projetos **SPJ / Investigação**

### RabbitMQ: Desenvolvimento

1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/rabbitmq/dev/001-rabbitmq.png)

2. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/rabbitmq/dev/002-rabbitmq.png)

3. Na caixa de **pesquisa digite CloudAMQP** e selecione **CloudAMQP**

![Google CLOUD Console Source](/assets/img/rabbitmq/dev/003-rabbitmq.png)

4. Na tela da **API do Firebase**, clique no botão **habilitar** após alguns segundos aparecerá o botão **Gerenciar**

![Google CLOUD RabbitMQ](/assets/img/rabbitmq/dev/004-rabbitmq.png)

5. Console de administração do CloudAMQP

![CloudAMQP - Admin Console](/assets/img/rabbitmq/dev/005-rabbitmq.png)

6. Na tela de **Administração da CloudAMQP**, selecione o botão **Create a New Instance** para provisionar a instância de **Desenvolvimento**.

![CloudAMQP - Admin Console](/assets/img/rabbitmq/dev/006-rabbitmq.png)

7. **Em Step 1**, digite os dados abaixo:

* **Name**: gc5000916-rabbit-dev
* **Plan**: Big Bunny
* **Tag**: "deixar em branco"
  * **Clique no botão**: Select Region

![CloudAMQP - New Instance](/assets/img/rabbitmq/dev/007-rabbitmq.png)

8. **Em Step 2**, digite os dados abaixo:

* **Data Center**: Google Compute Engine
* **Type**: southamerica-east1 (São Paulo)
  * **Clique no botão**: Configure

![CloudAMQP - New Instance](/assets/img/rabbitmq/dev/008-rabbitmq.png)

9. **Em Step 3**, digite os dados abaixo:

* **Nodes**: 1
* **RabbitMQ Version**: 4.0.5
* **Dedicated VPC**: Enabled
* **Copy Instance from**: rabbitmq-5000916
* **Settings to copy**: yes
  * RabbitMQ Config
  * Enabled plugins
  * Alarm Configurations
  * Logs Integration
  * Firewall Configuration

![CloudAMQP - New Instance](/assets/img/rabbitmq/dev/009-rabbitmq.png)

#### Configurando o Peering VPC

1. Acesse o **Menu >> Networking >> VPC Peering** e configure conforme abaixo:

* **Create peering request**: 
  * **Your GCE VPC Network**: projects/dipol-sist-invest-dev/global/networks/vpc-gcp-dipol-dev
    * **Clique no botão**: Send peering request

![CloudAMQP - Configure VPC Peering](/assets/img/rabbitmq/dev/010-rabbitmq.png)

2. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/rabbitmq/dev/001-rabbitmq.png)

3. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/rabbitmq/dev/002-rabbitmq.png)

4. Na caixa de **VPC network peering** e selecione **Peering da rede VPC**

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/dev/011-rabbitmq.png)

5. Em Peering de rede VPC, clique no botão **Criar conexão Peering**

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/dev/012-rabbitmq.png)

6. Em **criar conexão de peering** digite as informações conforme imagem abaixo:

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/dev/013-rabbitmq.png)

7. Teste se é possível **fechar conexão com o rabbitMQ pelo cluster kubernetes**

* **Acesse o cluster do ambiente de desenvolvimento**
  * **Cluster**: gke-5000916-private-dev
  * **bastion**: namespace dipol-infra

![Cluster Kubernetes - Validation access](/assets/img/rabbitmq/dev/014-rabbitmq.png)

### RabbitMQ: Homologação

1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/rabbitmq/hom/001-rabbitmq.png)

2. No menu de projetos selecione o projeto desejado **5000917-Dipol-Sist-Invest-Hom**

![Google CLOUD Login](/assets/img/rabbitmq/hom/002-rabbitmq.png)

3. Na caixa de **pesquisa digite CloudAMQP** e selecione **CloudAMQP**

![Google CLOUD Console Source](/assets/img/rabbitmq/hom/003-rabbitmq.png)

4. Na tela da **API do Firebase**, clique no botão **habilitar** após alguns segundos aparecerá o botão **Gerenciar**

![Google CLOUD RabbitMQ](/assets/img/rabbitmq/hom/004-rabbitmq.png)

5. Console de administração do CloudAMQP

![CloudAMQP - Admin Console](/assets/img/rabbitmq/hom/005-rabbitmq.png)

6. Na tela de **Administração da CloudAMQP**, selecione o botão **Create a New Instance** para provisionar a instância de **Homologação**.

![CloudAMQP - Admin Console](/assets/img/rabbitmq/hom/006-rabbitmq.png)

7. **Em Step 1**, digite os dados abaixo:

* **Name**: gc5000917-hom
* **Plan**: Big Bunny x1
* **Tag**: "deixar em branco"
  * **Clique no botão**: Select Region

![CloudAMQP - New Instance](/assets/img/rabbitmq/hom/007-rabbitmq.png)

8. **Em Step 2**, digite os dados abaixo:

* **Data Center**: Google Compute Engine
* **Type**: southamerica-east1 (São Paulo)
  * **Clique no botão**: Configure

![CloudAMQP - New Instance](/assets/img/rabbitmq/dev/008-rabbitmq.png)

9. **Em Step 3**, digite os dados abaixo:

* **Nodes**: 1
* **RabbitMQ Version**: 4.0.5
* **Dedicated VPC**: Enabled
* **Copy Instance from**: rabbitmq-5000916
* **Settings to copy**: yes
  * RabbitMQ Config
  * Enabled plugins
  * Alarm Configurations
  * Logs Integration
  * Firewall Configuration

![CloudAMQP - New Instance](/assets/img/rabbitmq/hom/009-rabbitmq.png)

#### Configurando o Peering VPC

1. Acesse o **Menu >> Networking >> VPC Peering** e configure conforme abaixo:

* **Create peering request**: 
  * **Your GCE VPC Network**: projects/dipol-sist-invest-hom/global/networks/vpc-gcp-dipol-hom
    * **Clique no botão**: Send peering request

![CloudAMQP - Configure VPC Peering](/assets/img/rabbitmq/hom/010-rabbitmq.png)

2. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/rabbitmq/hom/001-rabbitmq.png)

3. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/rabbitmq/hom/002-rabbitmq.png)

4. Na caixa de **VPC network peering** e selecione **Peering da rede VPC**

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/hom/011-rabbitmq.png)

5. Em Peering de rede VPC, clique no botão **Criar conexão Peering**

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/hom/012-rabbitmq.png)

6. Em **criar conexão de peering** digite as informações conforme imagem abaixo:

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/hom/013-rabbitmq.png)

7. Teste se é possível **fechar conexão com o rabbitMQ pelo cluster kubernetes**

* **Acesse o cluster do ambiente de Homologação**
  * **Cluster**: gke-5000917-private-hom
  * **bastion**: namespace dipol-infra

![Cluster Kubernetes - Validation access](/assets/img/rabbitmq/hom/014-rabbitmq.png)

### RabbitMQ: Produção

1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/rabbitmq/prod/001-rabbitmq.png)

2. No menu de projetos selecione o projeto desejado **5000034-Dipol-Sist-Invest-Prod**

![Google CLOUD Login](/assets/img/rabbitmq/prod/002-rabbitmq.png)

3. Na caixa de **pesquisa digite CloudAMQP** e selecione **CloudAMQP**

![Google CLOUD Console Source](/assets/img/rabbitmq/prod/003-rabbitmq.png)

4. Na tela da **API do Firebase**, clique no botão **habilitar** após alguns segundos aparecerá o botão **Gerenciar**

![Google CLOUD RabbitMQ](/assets/img/rabbitmq/prod/004-rabbitmq.png)

5. Console de administração do CloudAMQP

![CloudAMQP - Admin Console](/assets/img/rabbitmq/prod/005-rabbitmq.png)

6. Na tela de **Administração da CloudAMQP**, selecione o botão **Create a New Instance** para provisionar a instância de **Produção**.

![CloudAMQP - Admin Console](/assets/img/rabbitmq/prod/006-rabbitmq.png)

7. **Em Step 1**, digite os dados abaixo:

* **Name**: gc5000034-prod
* **Plan**: Big Bunny x 3
* **Tag**: "deixar em branco"
  * **Clique no botão**: Select Region

![CloudAMQP - New Instance](/assets/img/rabbitmq/prod/007-rabbitmq.png)

8. **Em Step 2**, digite os dados abaixo:

* **Data Center**: Google Compute Engine
* **Type**: southamerica-east1 (São Paulo)
  * **Clique no botão**: Configure

![CloudAMQP - New Instance](/assets/img/rabbitmq/prod/008-rabbitmq.png)

9. **Em Step 3**, digite os dados abaixo:

* **Nodes**: 3
* **RabbitMQ Version**: 4.0.5
* **Dedicated VPC**: Enabled
* **Copy Instance from**: rabbitmq-5000034-private-prod
* **Settings to copy**: yes
  * RabbitMQ Config
  * Enabled plugins
  * Alarm Configurations
  * Logs Integration
  * Firewall Configuration

![CloudAMQP - New Instance](/assets/img/rabbitmq/prod/009-rabbitmq.png)

#### Configurando o Peering VPC

1. Acesse o **Menu >> Networking >> VPC Peering** e configure conforme abaixo:

* **Create peering request**: 
  * **Your GCE VPC Network**: projects/dipol-sist-invest-hom/global/networks/vpc-gcp-dipol-hom
    * **Clique no botão**: Send peering request

![CloudAMQP - Configure VPC Peering](/assets/img/rabbitmq/prod/010-rabbitmq.png)

2. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/rabbitmq/prod/011-rabbitmq.png)

3. No menu de projetos selecione o projeto desejado **5000034-Dipol-Sist-Invest-Prod**

![Google CLOUD Login](/assets/img/rabbitmq/prod/012-rabbitmq.png)

4. Na caixa de **VPC network peering** e selecione **Peering da rede VPC**

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/prod/013-rabbitmq.png)

5. Em Peering de rede VPC, clique no botão **Criar conexão Peering**

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/prod/014-rabbitmq.png)

6. Em **criar conexão de peering** digite as informações conforme imagem abaixo:

![Google Cloud - Configure VPC Peering](/assets/img/rabbitmq/prod/015-rabbitmq.png)

7. Teste se é possível **fechar conexão com o rabbitMQ pelo cluster kubernetes**

* **Acesse o cluster do ambiente de Homologação**
  * **Cluster**: gke-5000034-private-prod
  * **bastion**: namespace dipol-infra

![Cluster Kubernetes - Validation access](/assets/img/rabbitmq/prod/016-rabbitmq.png)