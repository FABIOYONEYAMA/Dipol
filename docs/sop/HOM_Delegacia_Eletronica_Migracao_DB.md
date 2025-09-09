# Sobre

Este procedimento é utilizado para reconfigurar o provedor JDBC e uma fonte de dados já existente, devido a troca do banco de dados e sua versão e a documentação oficial da IBM pode ser consultada no link abaixo

[Configurando Provedor e Fonte JDBC](https://www.ibm.com/docs/en/was/8.5.5?topic=SSEQTP_8.5.5/com.ibm.websphere.nd.multiplatform.doc/ae/tdat_tccrtprovds.htm)

Está listado todos os recursos e procedimentos realizados para esta tarefa.

# Tabela de Conteúdo
- [Sobre](#sobre)
- [Tabela de Conteúdo](#tabela-de-conteúdo)
- [Instâncias](#instâncias)
- [Procedimentos Operacionais](#procedimentos-operacionais)
  - [Validação de Acessos](#validação-de-acessos)
  - [Adicionando os drivers mssql-jdbc](#adicionando-os-drivers-mssql-jdbc)
  - [Configurando o Driver no IBM Websphere](#configurando-o-driver-no-ibm-websphere)
  - [Configurando o JAAS - J2C authentication data](#configurando-o-jaas---j2c-authentication-data)
  - [Configurando o data source PRODESP\_SSP\_DE](#configurando-o-data-source-prodesp_ssp_de)
  - [Restart do ambiente de Homologação](#restart-do-ambiente-de-homologação)


# Instâncias
Abaixo é informada as **instâncias dos ambientes** de **DESENVOLVIMENTO, HOMOLOGAÇÃO e PRODUÇÃO**.

Name            | Internal IP   | Type        | Status       |
----------------| ------------- | ----------- | -------------|
caetes-ws1      | 10.200.77.125 | DMGR & NODE | Enabled      |
caetes-ws2      | 10.200.77.126 | NODE        | Enabled      |
cupira          | 10.200.77.127 | MSsql 2014  | Discontinued |
gc5000917-sql01 | 10.153.26.3   | MSsql 2019  | Enabled      |

> Migração das databases da Delegacia Eletrônica do host cupira >> gc5000917-sql01

> Este procedimento será realizado pelo time de Administração do banco de dados


# Procedimentos Operacionais

Detalhamos todo o **procedimento na camada de aplicação e infraestrutura** que é necessário para o funcionamento correto desta modificação planejada.

## Validação de Acessos

Necessário **validar os acessos dos servidores de aplicação com o banco de dados**. Os servidores **caetes-ws1 e caetes-ws2** devem ter acesso ao servidor **gc5000917-sql01 na porta 1433.** 

As evidências dos acessos são detalhadas e imrpessas abaixo:

* Comando executados:
  * **Servidores**
    * **hostname**: caetes-ws1
      * **IP**: 10.200.77.125
    * **hostname**: caetes-ws2
      * **IP**: 10.200.77.126
```bash
echo quit |telnet 10.153.26.3 1433
```

![001_DE_migracao](/assets/img/sop/DE_migracao/001_DE_migracao.png)

## Adicionando os drivers mssql-jdbc

Para este procedimento, foi **verificado a matriz de compatibilidde**, com a finalidade de **manter o serviço funcionando corretamente.**

* [Compatibilidade Versão SQL](https://learn.microsoft.com/en-us/sql/connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix?view=sql-server-ver16#sql-version-compatibility)
* [Ciclo de vida de Suporte do Driver](https://learn.microsoft.com/en-us/sql/connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix?view=sql-server-ver16#microsoft-jdbc-driver-support-lifecycle-matrix-and-policy)


Execute o aplicativo **winSCP**, conecte nos servidores caetes-ws1 e caetes-ws2, acesse o diretório **/opt/IBM/WebSphere/AppServer/lib/ext** e adicione os drivers compatíveis com a versão do SQL em uso.

* Acessando os servidores **caetes-ws1 e caetes-ws2 via winSCP** 
  
![002_DE_migracao](/assets/img/sop/DE_migracao/002_DE_migracao.png)

* Adicionando o driver ao diretório padrão
  
![003_DE_migracao](/assets/img/sop/DE_migracao/003_DE_migracao.png)

## Configurando o Driver no IBM Websphere

Vamos acessar a console de **Administração do ambiente da Delegacia Eletrônica**, para isso acesse:

![Websphere Inquérito](/assets/img/DE/websphere_console_de_dev.png)

No **console administrativo** acesse o **Menu** >> **Resource** >> **JDBC** >> **JDBC providers** 

![004_DE_migracao](/assets/img/sop/DE_migracao/004_DE_migracao.png)

Selecione o **JDBC providers**, **MSSQL Server JDBC Driver** para editar a configuração e realizar os procedimento abaixo

![005_DE_migracao](/assets/img/sop/DE_migracao/005_DE_migracao.png)

* Edite **MSSQL Server JDBC Driver**
  * **Name:** MSSQL Server JDBC Driver 2019
  * **Class Path:** ${MICROSOFT_JDBC_DRIVER_PATH}/mssql-jdbc-7.4.1.jre8.jar
  * Clique em **Apply**
  * Clique em **Save**

![006_DE_migracao](/assets/img/sop/DE_migracao/006_DE_migracao.png)

## Configurando o JAAS - J2C authentication data

No **console administrativo** acesse o **Menu** >> **Resource** >> **JDBC** >> **Data sources** 

![007_DE_migracao](/assets/img/sop/DE_migracao/007_DE_migracao.png)

Selecione o Data source **PRODESP_SSP_DE**, conforme imagem abaixo, para editar a configuração e realizar os procedimentos abaixo

![008_DE_migracao](/assets/img/sop/DE_migracao/008_DE_migracao.png)

* **Selecione J2C authentication data**
   * Edite o **alias** caetes-ws1CellManager01/usudehml 
   * Altere o usuário e senha

![009_DE_migracao](/assets/img/sop/DE_migracao/009_DE_migracao.png)

## Configurando o data source PRODESP_SSP_DE

No **console administrativo** acesse o **Menu** >> **Resource** >> **JDBC** >> **Data sources** 

![007_DE_migracao](/assets/img/sop/DE_migracao/007_DE_migracao.png)

Selecione o Data source **PRODESP_SSP_DE**, conforme imagem abaixo, para editar a configuração e realizar os procedimentos abaixo

* Edite **PRODESP_SSP_DE**
  * **Server name: **10.153.26.3**
  *  Clique em **Apply**
  *  Clique em **Save**
  
![010_DE_migracao](/assets/img/sop/DE_migracao/010_DE_migracao.png)

## Restart do ambiente de Homologação

Efetue o restart de todo o ambiente de homologação, **DMGR, NodeAgent e JVM** utilize os scripts de restart para melhor execução.

