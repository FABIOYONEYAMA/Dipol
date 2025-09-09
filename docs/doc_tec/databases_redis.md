## Sobre

**Banco de dados de key-value** totalmente **gerenciado para desempenho em tempo real**. O **Redis** é o banco de **dados in-memory.** Ele fornece soluções em nuvem e locais **para armazenamento em cache, pesquisa vetorial e bancos de dados NoSQL que se encaixam perfeitamente em qualquer pilha de tecnologia,** tornando simples para os clientes digitais criar, dimensionar e implantar os aplicativos rápidos em que nosso mundo é executado.

# Tabela de Conteúdo
- [Tabela de Conteúdo](#tabela-de-conteúdo)
- [Faturamento](#faturamento)
  - [Instâncias](#instâncias)
  - [Databases Redis](#databases-redis)
    - [Database Redis Datascience: Desenvolvimento](#database-redis-datascience-desenvolvimento)
      - [Service Account](#service-account)
      - [IBMCloud Monitoring](#ibmcloud-monitoring)
      - [Conectando na Instância:](#conectando-na-instância)
    - [Database Redis SPJ e Inv: Desenvolvimento](#database-redis-spj-e-inv-desenvolvimento)
      - [Service Account](#service-account-1)
      - [IBMCloud Monitoring](#ibmcloud-monitoring-1)
      - [Conectando na Instância:](#conectando-na-instância-1)
    - [Database Redis SPJ e Inv: Homologação](#database-redis-spj-e-inv-homologação)
      - [Service Account](#service-account-2)
    - [Database Redis Datascience: Produção](#database-redis-datascience-produção)
      - [Service Account](#service-account-3)
    - [Database Redis SPJ e Inv: Produção](#database-redis-spj-e-inv-produção)

# Faturamento

**A taxa de uso é cobrada mensalmente**, **os planos flexíveis** para todas as suas necessidades.

## Instâncias

Abaixo é informada as **instâncias dos ambientes** de **DESENVOLVIMENTO, HOMOLOGAÇÃO e PRODUÇÃO**.

Name                             | Type                | Environment     | Region             |
-------------------------------- | --------------------| ----------------| ------------------ |
ib0500007-datascience-redis-dev  | IBM Cloud Databases | Desenvolvimento | Sao Paulo (br-sao) |
ib0500007-datascience-redis-prod | IBM Cloud Databases | Desenvolvimento | Sao Paulo (br-sao) |
ib0500007-spj-redis-dev          | IBM Cloud Databases | Desenvolvimento | Sao Paulo (br-sao) |
ib0500007-spj-redis-hom          | IBM Cloud Databases | Homologação     | Sao Paulo (br-sao) |
ib0500007-spj-redis-prod         | IBM Cloud Databases | Produção        | Sao Paulo (br-sao) |


## Databases Redis

O serviço será utilizado como uma solução para armazenamento em cache, para diversos projetos e sistemas. As instâncias são separadas por sistema, com a finalidade de melhor performace dos projetos DIPOL.

### Database Redis Datascience: Desenvolvimento

1. Acesse a **página de login** do ***IBM Cloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**. A **autenticação** é realizada por **duplo fator.**
   
![IBM CLOUD Login](/assets/img/redis/dev/001_redis.png)

2. Clique no **menu de navegação** para abrir a **o painel de seleção**

![IBM CLOUD Menu](/assets/img/redis/dev/002_redis.png)

3. Selecione o **Menu Databases** >> **Resources** 

![IBM CLOUD Menu](/assets/img/redis/dev/003_redis.png)

4. No menu de recursos da database, clique no botão **Create**, para criar a instância desejada

![IBM CLOUD Databases](/assets/img/redis/dev/004_redis.png)

5. Escolha o serviço desejado, **Databases for Redis**

![IBM CLOUD Databases](/assets/img/redis/dev/005_redis.png)

6. **Adicione as informações abaixo:** (Parte 1)
   1. **Platform**: IBM Cloud
   2. **Service Name**: ib0500007-datascience-redis-dev
   3. **Resource Group**: gr-0500007-dev
   4. **Location**: Sao Paulo (br-sao)
   5. **Tags**: dev | datascience

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/006_redis.png)

7. **Adicione as informações abaixo:** (Parte 2)
   1. **Select your hosting model**: Shared
   2. **Resource Allocation**: Small
   3. **Disk**: 1GB

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/007_redis.png)

8. **Adicione as informações abaixo:** (parte 3)
   1. **Database Version**: 7.2 
   2. Endpoint: Both public & private network

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/008_redis.png)

9. Clique em **create e aguarde até finalizar**

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/009_redis.png)

10. Após **provisionamento o status da instância** ficará conforme imagem abaixo

![IBM CLOUD Databases Status ](/assets/img/redis/dev/010_redis.png)

#### Service Account

1. Acesse a instância, clicando no me da Instância:

![IBM CLOUD Databases instances ](/assets/img/redis/dev/010_redis.png)

2. Selecione **Service Account** >> **New Credential**

![IBM CLOUD Databases Service Account](/assets/img/redis/dev/011_redis.png)

3. Em **Create credential**, digite:
   1. **Name:** credential-admin-datascience-redis-dev
   2. **Add**

![IBM CLOUD Databases Service Account](/assets/img/redis/dev/012_redis.png)

4. Detalhes da **Service Account** criada.

![IBM CLOUD Databases Service Account](/assets/img/redis/dev/013_redis.png)


#### IBMCloud Monitoring

1. Para acesso ao IBM Cloud Monitoring na instância, é necessário acessar o Menu Monitoring a primeira vez para que seja configurado o monitoramento para a instância conforme imagem abaixo:
   1. **Acesse**: ib0500007-datascience-redis-dev
   2. **Navegue Menu**: Monitoring
   3. **Dashboard**: [ib0500007-datascience-redis-dev](https://br-sao.monitoring.cloud.ibm.com/#/dashboard-template/ibm_databases_for_redis?skip-welcome=true&scope=ibm_location%20%3D%20%22br-sao%22%20and%20ibm_service_instance%20%3D%20%22a66d5bf0-c0e4-44ea-a832-c56e180ddc79%22&last=3600)

![IBM CLOUD Databases Monitoring](/assets/img/redis/dev/014_redis.png)


2. Painel de **Monitoramento ib0500007-datascience-redis-dev**

![IBM CLOUD Databases Monitoring](/assets/img/redis/dev/015_redis.png)


#### Conectando na Instância:

1. Para se **conectar a essa instância redis**, **é necessário o ciente de linha de comanda REDLI**, o **redli é um cliente da linha de comando de software livre do Redis**. Ele é independente, imita os argumentos da linha de comandos de redis-cli e inclui suporte para as conexões TLS/SSL do Redis.
   1. **Para obter o cliente de linha de comando acesse: [REDLI cli](https://github.com/IBM-Cloud/redli/releases)**

2. **Inicie o acesso ao redis, execute os comandos no terminal conforme imagem abaixo:**

![IBM CLOUD Databases redli](/assets/img/redis/dev/016_redis.png)

### Database Redis SPJ e Inv: Desenvolvimento

1. Acesse a **página de login** do ***IBM Cloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**. A **autenticação** é realizada por **duplo fator.**
   
![IBM CLOUD Login](/assets/img/redis/dev/001_redis.png)

2. Clique no **menu de navegação** para abrir a **o painel de seleção**

![IBM CLOUD Menu](/assets/img/redis/dev/002_redis.png)

3. Selecione o **Menu Databases** >> **Resources** 

![IBM CLOUD Menu](/assets/img/redis/dev/003_redis.png)

4. No menu de recursos da database, clique no botão **Create**, para criar a instância desejada

![IBM CLOUD Databases](/assets/img/redis/dev/004_redis.png)

5. Escolha o serviço desejado, **Databases for Redis**

![IBM CLOUD Databases](/assets/img/redis/dev/005_redis.png)

6. **Adicione as informações abaixo:** (Parte 1)
   1. **Platform**: IBM Cloud
   2. **Service Name**: ib0500007-redis-dev-v7
   3. **Resource Group**: gr-0500007-dev
   4. **Location**: Sao Paulo (br-sao)
   5. **Tags**: dev | SPJ | INV | V7

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/017_redis.png)

7. **Adicione as informações abaixo:** (Parte 2)
   1. **Select your hosting model**: Shared
   2. **Resource Allocation**: Small
   3. **Disk**: 1GB

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/018_redis.png)

8. **Adicione as informações abaixo:** (parte 3)
   1. **Database Version**: 7.2 
   2. Endpoint: Both public & private network

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/019_redis.png)

9. Clique em **create e aguarde até finalizar**

![IBM CLOUD Databases Provisioning ](/assets/img/redis/dev/009_redis.png)

10. Após **provisionamento o status da instância** ficará conforme imagem abaixo

![IBM CLOUD Databases Status ](/assets/img/redis/dev/020_redis.png)

#### Service Account

1. Acesse a instância, clicando no me da Instância:

![IBM CLOUD Databases Status ](/assets/img/redis/dev/021_redis.png)

2. Selecione **Service Account** >> **New Credential**

![IBM CLOUD Databases Service Account](/assets/img/redis/dev/022_redis.png)

3. Em **Create credential**, digite:
   1. **Control by secrets manager:** disable
   2. **Name:** credential-admin-ib0500007-redis-dev
   3. **Add**

![IBM CLOUD Databases Service Account](/assets/img/redis/dev/023_redis.png)

4. Detalhes da **Service Account** criada.

![IBM CLOUD Databases Service Account](/assets/img/redis/dev/013_redis.png)

#### IBMCloud Monitoring

1. Para acesso ao IBM Cloud Monitoring na instância, é necessário acessar o Menu Monitoring a primeira vez para que seja configurado o monitoramento para a instância conforme imagem abaixo:
   1. **Acesse**: ib0500007-redis-dev-v7
   2. **Navegue Menu**: Monitoring
   3. **Dashboard**: [ib0500007-redis-dev-v7](https://br-sao.monitoring.cloud.ibm.com/#/dashboard-template/ibm_databases_for_redis?skip-welcome=true&scope=ibm_location%20%3D%20%22br-sao%22%20and%20ibm_service_instance%20%3D%20%2294578e36-10b8-44b0-8853-8b1d9a1cd04f%22&last=3600)

![IBM CLOUD Databases Monitoring](/assets/img/redis/dev/025_redis.png)


2. Painel de **Monitoramento ib0500007-datascience-redis-dev**

![IBM CLOUD Databases Monitoring](/assets/img/redis/dev/026_redis.png)

#### Conectando na Instância:

1. Para se **conectar a essa instância redis**, **é necessário o ciente de linha de comanda REDLI**, o **redli é um cliente da linha de comando de software livre do Redis**. Ele é independente, imita os argumentos da linha de comandos de redis-cli e inclui suporte para as conexões TLS/SSL do Redis.
   1. **Para obter o cliente de linha de comando acesse: [REDLI cli](https://github.com/IBM-Cloud/redli/releases)**

2. **Inicie o acesso ao redis, execute os comandos no terminal conforme imagem abaixo:**

![IBM CLOUD Databases redli](/assets/img/redis/dev/027_redis.png)

### Database Redis SPJ e Inv: Homologação

1. Acesse a **página de login** do ***IBM Cloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**. A **autenticação** é realizada por **duplo fator.**
   
![IBM CLOUD Login](/assets/img/redis/hom/001_redis.png)

2. Clique no **menu de navegação** para abrir a **o painel de seleção**

![IBM CLOUD Menu](/assets/img/redis/hom/002_redis.png)

3. Selecione o **Menu Databases** >> **Resources** 

![IBM CLOUD Menu](/assets/img/redis/hom/003_redis.png)

4. No menu de recursos da database, clique no botão **Create**, para criar a instância desejada

![IBM CLOUD Databases](/assets/img/redis/hom/004_redis.png)

5. Escolha o serviço desejado, **Databases for Redis**

![IBM CLOUD Databases](/assets/img/redis/hom/005_redis.png)

6. **Adicione as informações abaixo:** (Parte 1)
   1. **Platform**: IBM Cloud
   2. **Service Name**: ib0500007-redis-hom-v7
   3. **Resource Group**: gr-0500007-hom
   4. **Location**: Sao Paulo (br-sao)
   5. **Tags**: hom | SPJ | INV | V7

![IBM CLOUD Databases Provisioning ](/assets/img/redis/hom/006_redis.png)

7. **Adicione as informações abaixo:** (Parte 2)
   1. **Select your hosting model**: Shared
   2. **Resource Allocation**: Small
   3. **Disk**: 12GB

![IBM CLOUD Databases Provisioning ](/assets/img/redis/hom/007_redis.png)

8. **Adicione as informações abaixo:** (parte 3)
   1. **Database Version**: 7.2 
   2. Endpoint: Both public & private network

![IBM CLOUD Databases Provisioning ](/assets/img/redis/hom/008_redis.png)

9. Clique em **create e aguarde até finalizar**

![IBM CLOUD Databases Provisioning ](/assets/img/redis/hom/009_redis.png)

10. Após **provisionamento o status da instância** ficará conforme imagem abaixo

![IBM CLOUD Databases Status ](/assets/img/redis/hom/010_redis.png)

#### Service Account

1. Acesse a instância, clicando no me da Instância:

![IBM CLOUD Databases Status ](/assets/img/redis/hom/011_redis.png)

2. Selecione **Service Account** >> **New Credential**

![IBM CLOUD Databases Service Account](/assets/img/redis/hom/012_redis.png)

3. Em **Create credential**, digite:
   1. **Control by secrets manager:** disable
   2. **Name:** credential-admin-ib0500007-redis-hom
   3. **Add**

![IBM CLOUD Databases Service Account](/assets/img/redis/hom/013_redis.png)

4. Detalhes da **Service Account** criada.

![IBM CLOUD Databases Service Account](/assets/img/redis/hom/014_redis.png)

### Database Redis Datascience: Produção

1. Acesse a **página de login** do ***IBM Cloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**. A **autenticação** é realizada por **duplo fator.**
   
![IBM CLOUD Login](/assets/img/redis/dev/001_redis.png)

2. Clique no **menu de navegação** para abrir a **o painel de seleção**

![IBM CLOUD Menu](/assets/img/redis/dev/002_redis.png)

3. Selecione o **Menu Databases** >> **Resources** 

![IBM CLOUD Menu](/assets/img/redis/dev/003_redis.png)

4. No menu de recursos da database, clique no botão **Create**, para criar a instância desejada

![IBM CLOUD Databases](/assets/img/redis/dev/004_redis.png)

5. Escolha o serviço desejado, **Databases for Redis**

![IBM CLOUD Databases](/assets/img/redis/dev/005_redis.png)

6. **Adicione as informações abaixo:** (Parte 1)
   1. **Platform**: IBM Cloud
   2. **Service Name**: ib0500007-datascience-redis-prod
   3. **Resource Group**: gr-0500007-prod
   4. **Location**: Sao Paulo (br-sao)
   5. **Tags**: prod | Datascience | V7

![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/101_redis.png)

7. **Adicione as informações abaixo:** (Parte 2)
   1. **Select your hosting model**: Isolated
   2. **Resource Allocation**: XS 4x16
   3. **Disk**: 100GB

![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/102_redis.png)

8. **Adicione as informações abaixo:** (parte 3)
   1. **Database Version**: 7.2 
   2. Endpoint: Both public & private network
![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/103_redis.png)

9. Clique em **create e aguarde até finalizar**

![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/104_redis.png)

10. Após **provisionamento o status da instância** ficará conforme imagem abaixo

![IBM CLOUD Databases Status ](/assets/img/redis/prod/105_redis.png)

#### Service Account

1. Acesse a instância, clicando no me da Instância:

![IBM CLOUD Databases Status ](/assets/img/redis/prod/108_redis.png)

2. Selecione **Service Account** >> **New Credential**

![IBM CLOUD Databases Service Account](/assets/img/redis/prod/109_redis.png)

3. Em **Create credential**, digite:
   1. **Control by secrets manager:** disable
   2. **Name:** credential-admin-ib0500007-redis-prod
   3. **Add**

![IBM CLOUD Databases Service Account](/assets/img/redis/prod/106_redis.png)

4. Detalhes da **Service Account** criada.

![IBM CLOUD Databases Service Account](/assets/img/redis/prod/107_redis.png)


### Database Redis SPJ e Inv: Produção

1. Acesse a **página de login** do ***IBM Cloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**. A **autenticação** é realizada por **duplo fator.**
   
![IBM CLOUD Login](/assets/img/redis/prod/001_redis.png)

2. Clique no **menu de navegação** para abrir a **o painel de seleção**

![IBM CLOUD Menu](/assets/img/redis/prod/002_redis.png)

3. Selecione o **Menu Databases** >> **Resources** 

![IBM CLOUD Menu](/assets/img/redis/prod/003_redis.png)

4. No menu de recursos da database, clique no botão **Create**, para criar a instância desejada

![IBM CLOUD Databases](/assets/img/redis/prod/004_redis.png)

5. Escolha o serviço desejado, **Databases for Redis**

![IBM CLOUD Databases](/assets/img/redis/prod/005_redis.png)

6. **Adicione as informações abaixo:** (Parte 1)
   1. **Platform**: IBM Cloud
   2. **Service Name**: ib0500007-spj-redis-prod
   3. **Resource Group**: gr-0500007-prod
   4. **Location**: Sao Paulo (br-sao)
   5. **Tags**: prod | spj | inv | v7 

![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/006_redis.png)

7. **Adicione as informações abaixo:** (Parte 2)
   1. **Select your hosting model**: Custom
   2. **Resource Allocation**: 6x56
   3. **Disk**: 300GB

![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/007_redis.png)

8. **Adicione as informações abaixo:** (parte 3)
   1. **Database Version**: 7.2 
   2. Endpoint: Both public & private network
![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/008_redis.png)

9. Clique em **create e aguarde até finalizar**

![IBM CLOUD Databases Provisioning ](/assets/img/redis/prod/009_redis.png)

10. Após **provisionamento o status da instância** ficará conforme imagem abaixo

![IBM CLOUD Databases Status ](/assets/img/redis/prod/010_redis.png)
