## Sobre

**IBM Cloud® Databases for MySQL** é um **serviço de banco de dados em nuvem** sem servidor e totalmente gerenciado. Ele oferece os seguintes benefícios:
* **Manutenção automatizada:** Não é necessária nenhuma administração manual de software, infraestrutura, rede ou sistema operacional.
* **Alta disponibilidade:** Implementado em vários data centers com failover automático.
* **Escalabilidade**: Escalonamento independente de disco, RAM e vCPU com escalonamento automático e faturamento por hora.
* **Replicação semissíncrona:** Garante que os dados estejam disponíveis em vários locais para alta disponibilidade, acrescentando uma camada extra de segurança e confiabilidade dos dados.
* **Segurança:** Escolha entre ambientes multilocatários ou isolados, dependendo de suas necessidades de segurança.

# Tabela de Conteúdo
- [Tabela de Conteúdo](#tabela-de-conteúdo)
- [Faturamento](#faturamento)
  - [Instâncias](#instâncias)
  - [Databases MySQL](#databases-mysql)
    - [Database MySQL GPI: Desenvolvimento](#database-mysql-gpi-desenvolvimento)
      - [Service Account](#service-account)

# Faturamento

**A taxa de uso é cobrada mensalmente**, **os planos flexíveis** para todas as suas necessidades.

## Instâncias

Abaixo é informada as **instâncias dos ambientes** de **DESENVOLVIMENTO, HOMOLOGAÇÃO e PRODUÇÃO**.

Name                             | Type                | Environment     | Region             |
-------------------------------- | --------------------| ----------------| ------------------ |

## Databases MySQL

O serviço será utilizado como uma solução de banco de dados relacional (RDBMS) de código aberto, que vai armazenar e gerenciar dados, para o projeto dos sistemas GPI (Gestão Policial Integrada).

### Database MySQL GPI: Desenvolvimento

1. Acesse a **página de login** do ***IBM Cloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**. A **autenticação** é realizada por **duplo fator.**
   
![IBM CLOUD Login](/assets/img/databases_mysql/dev/001_mysql.png)

2. Clique no **menu de navegação** para abrir a **o painel de seleção**

![IBM CLOUD Menu](/assets/img/databases_mysql/dev/002_mysql.png)

3. Selecione o **Menu Databases** >> **Resources** 

![IBM CLOUD Menu](/assets/img/databases_mysql/dev/003_mysql.png)

4. No menu de recursos da database, clique no botão **Create**, para criar a instância desejada

![IBM CLOUD Databases](/assets/img/databases_mysql/dev/004_mysql.png)

5. Escolha o serviço desejado, **Databases for MySQL**

![IBM CLOUD Databases](/assets/img/databases_mysql/dev/005_mysql.png)

6. **Adicione as informações abaixo:** (Parte 1)
   1. **Platform**: IBM Cloud
   2. **Service Name**: ib0500007-gpi-mysql-dev
   3. **Resource Group**: gr-0500007-dev
   4. **Location**: Sao Paulo (br-sao)
   5. **Tags**: dev | gpi

![IBM CLOUD Databases Provisioning ](/assets/img/databases_mysql/dev/006_mysql.png)

7. **Adicione as informações abaixo:** (Parte 2)
   1. **Select your hosting model**: Shared
   2. **Resource Allocation**: Small
   3. **Disk**: 100GB

![IBM CLOUD Databases Provisioning ](/assets/img/databases_mysql/dev/007_mysql.png)

8. **Adicione as informações abaixo:** (parte 3)
   1. **Database Version**: 8.0 
   2. Endpoint: Both public & private network

![IBM CLOUD Databases Provisioning ](/assets/img/databases_mysql/dev/008_mysql.png)

9. Clique em **create e aguarde até finalizar**

![IBM CLOUD Databases Provisioning ](/assets/img/databases_mysql/dev/009_mysql.png)

10. Após **provisionamento o status da instância** ficará conforme imagem abaixo

![IBM CLOUD Databases Status ](/assets/img/databases_mysql/dev/010_mysql.png)

#### Service Account

1. Acesse a instância, clicando no me da Instância:

![IBM CLOUD Databases instances ](/assets/img/databases_mysql/dev/010_mysql.png)

2. Selecione **Service Account** >> **New Credential**

![IBM CLOUD Databases Service Account](/assets/img/databases_mysql/dev/011_mysql.png)

3. Em **Create credential**, digite:
   1. **Name:** credential-admin-gpi-mysql-dev
   2. **Add**


![IBM CLOUD Databases Service Account](/assets/img/databases_mysql/dev/012_mysql.png)

4. Detalhes da **Service Account** criada.

![IBM CLOUD Databases Service Account](/assets/img/databases_mysql/dev/013_mysql.png)
