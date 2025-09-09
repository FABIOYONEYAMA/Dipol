# Sobre

Seção **destinada a documentação** da **Delegacia Eletrônica**, com _procedimentos técnicos, desenho da arquitetura e recursos disponíveis_.

# Tabela de Conteúdo

- [Sobre](#sobre)
- [Tabela de Conteúdo](#tabela-de-conteúdo)
- [Deploy da Aplicação](#deploy-da-aplicação)
  - [Desenvolvimento Delegacia Eletrônica](#desenvolvimento-delegacia-eletrônica)
    - [Arquitetura](#arquitetura)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais)
    - [2. Backup ssp-de-ear](#2-backup-ssp-de-ear)
    - [3. Update ssp-de-ear](#3-update-ssp-de-ear)
  - [Homologação Delegacia Eletrônica](#homologação-delegacia-eletrônica)
    - [Arquitetura](#arquitetura-1)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais-1)
    - [2. Backup ssp-de-ear](#2-backup-ssp-de-ear-1)
    - [3. Update ssp-de-ear](#3-update-ssp-de-ear-1)
  - [Produção Delegacia Eletrônica](#produção-delegacia-eletrônica)
    - [Arquitetura](#arquitetura-2)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais-2)
    - [2. Backup ssp-de-ear](#2-backup-ssp-de-ear-2)
    - [3. Update ssp-de-ear](#3-update-ssp-de-ear-2)


# Deploy da Aplicação

Demonstrar os **procedimentos necessários para executar o deploy nos ambientes das aplicações do Delegacia Eletrônica.** A execução deve ser realizada conforme, **ITQ-7.5-251 - Execução e Acompanhamento de job no Control-M WLA** (Procedimento Prodesp).

Antes de iniciar o procedimento de deploy é necessário **validar o espaço em disco, consumo de memória e cpu dos servidores que receberão a nova versão da aplicação e além disso é necessário validar se a versão atual não apresenta nenhum problema** que deve ser resolvida antes da execução.
É importante **realizar backup da versão atual** caso seja necessário a **execução de um rollback.**
Abaixo é apresentado a execução para os _**ambientes de Desenvolvimento | Homologação | Produção**_


## Desenvolvimento Delegacia Eletrônica 

### Arquitetura

A seguir é **demonstrado desenho da arquitetura** provisionada na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do **sistema da Delegacia Eletrônica.**

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](assets/diagrams/legado/DEV_Delegacia_Eletronica.svg). Se desejar, baixe a **[versão em XML](assets/diagrams/legado/DEV_Delegacia_Eletronica.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Delegacia Eletrônica DEV](assets/diagrams/legado/DEV_Delegacia_Eletronica.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.85.135/ssp-de-cidadao/home**
* Acesso intragov **http://10.200.85.135/ssp-de-retaguarda/** 

![Website DE](/assets/img/DE/website_DE_dev.png)

Verifique a **versão da aplicação Delegacia ELetrônica**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:

**CRQ000000497613** - Finalizado <br>
**Ambiente**: ***Desenvolvimento*** <br>
**Aplicação**: ***Delegacia Eletrônica*** <br>
**DE**    :   ***Versão v3.04 01/01/2022*** <br>
***PARA***:   ***Versão v3.05 03/01/2023*** <br>

***OBS: A versão da aplicação encontra-se no rodapé do website***

### 2. Backup ssp-de-ear

Vamos acessar a console de **Administração do ambiente da Delegacia Eletrônica**, para isso acesse:

![Websphere Inquérito](/assets/img/DE/websphere_console_de_dev.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-de-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/DE/websphere_export_ear.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/DE/websphere_backup_ear.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **caetite** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/DE/backup_ear_de_dev.png)

### 3. Update ssp-de-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/DE/websphere_export_ear.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-de-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/DE/websphere_deploy_ear.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/DE/websphere_deployII_ear.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy III ear](/assets/img/DE/websphere_deployIII_ear.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/DE/websphere_deployIV_dev_ear.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/DE/websphere_deployV_ear.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-de-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/DE/websphere_deployVI_ear.png)

<br>

## Homologação Delegacia Eletrônica 

### Arquitetura

A seguir é demonstrado **desenho da arquitetura provisionada** na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do sistema da Delegacia Eletrônica.

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](assets/diagrams/legado/HOM_Delegacia_Eletronica.svg). Se desejar, **baixe a [versão em XML](assets/diagrams/legado/HOM_Delegacia_Eletronica.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Delegacia Eletrônica HOM](assets/diagrams/legado/HOM_Delegacia_Eletronica.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.77.124/ssp-de-cidadao/home**
* Acesso intragov **http://10.200.77.124/ssp-de-retaguarda/** 
* Acesso ao WebSphere **https://10.200.77.125:9043/ibm/console/logon.jsp**

![Website DE](/assets/img/DE/website_DE_hom.png)

Para uma melhor **validação ou monitoração** do funcionamento da aplicação, **utilize os validadores em HTML** [Cockpit DE Cidadão](/assets/cockpit/HOM_DE_CIDADAO.html) e [Cockpit DE Retaguarda](/assets/cockpit/HOM_DE_RETAGUARDA.html)

<br>

Verifique a **versão da aplicação Delegacia ELetrônica**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:


**CRQ000000497613** - Finalizado <br>
**Ambiente**: ***Homologação*** <br>
**Aplicação**: ***Delegacia Eletrônica*** <br>
**DE**    :   ***Versão v3.04 01/01/2022*** <br>
***PARA***:   ***Versão v3.05 03/01/2023*** <br>

***OBS: A versão da aplicação encontra-se no rodapé do website***

### 2. Backup ssp-de-ear

Vamos acessar a console de **Administração do ambiente da Delegacia Eletrônica**, para isso acesse:

![Websphere Inquérito](/assets/img/DE/websphere_console_de_dev.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-de-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/DE/websphere_export_ear.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/DE/websphere_backup_ear.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **caetite** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/DE/backup_ear_de_dev.png)

### 3. Update ssp-de-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/DE/websphere_export_ear.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-de-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/DE/websphere_deploy_ear.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/DE/websphere_deployII_ear.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy II ear](/assets/img/DE/websphere_deployIII_hom_ear.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/DE/websphere_deployIV_hom_ear.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/DE/websphere_deployV_hom_ear.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-de-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/DE/websphere_deployVI_ear.png)

<br>

## Produção Delegacia Eletrônica

### Arquitetura

A seguir é demonstrado **desenho da arquitetura provisionada** na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do sistema da Delegacia Eletrônica.

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](assets/diagrams/legado/PROD_Delegacia_Eletronica.svg). Se desejar, **baixe a [versão em XML](assets/diagrams/legado/PROD_Delegacia_Eletronica.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Delegacia Eletrônica PROD](assets/diagrams/legado/PROD_Delegacia_Eletronica.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso internet **https://www.delegaciaeletronica.policiacivil.sp.gov.br/ssp-de-cidadao/**
* Acesso intragov **http://10.200.68.94/ssp-de-retaguarda/** 

![Website DE](/assets/img/DE/website_DE_prod.png)

Verifique a **versão da aplicação Delegacia ELetrônica**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:

**CRQ000000497613** - Finalizado <br>
**Ambiente**: ***Produção*** <br>
**Aplicação**: ***Delegacia Eletrônica*** <br>
**DE**    :   ***Versão v3.04 01/01/2022*** <br>
***PARA***:   ***Versão v3.05 03/01/2023*** <br>

***OBS: A versão da aplicação encontra-se no rodapé do website***

### 2. Backup ssp-de-ear

Vamos acessar a console de **Administração do ambiente da Delegacia Eletrônica**, para isso acesse:

![Websphere Inquérito](/assets/img/DE/websphere_console_de_prod.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-de-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/DE/websphere_export_ear.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/DE/websphere_backup_ear.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **moreno-ws1** no **diretório: /opt/Versoes_Anteriores**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/DE/backup_ear_de_prod.png)

### 3. Update ssp-de-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/DE/websphere_export_ear.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-de-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/DE/websphere_deploy_ear.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/DE/websphere_deployII_ear.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy III ear](/assets/img/DE/websphere_deployIII_ear_prod.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/DE/websphere_deployIV_dev_ear_prod.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/DE/websphere_deployV_ear.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-de-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/DE/websphere_deployVI_ear.png)
