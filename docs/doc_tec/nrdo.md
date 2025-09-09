# Sobre

Seção **destinada a documentação** da **NRDO**, com _procedimentos técnicos, desenho da arquitetura e recursos disponíveis_.

# Tabela de Conteúdo
- [Sobre](#sobre)
- [Tabela de Conteúdo](#tabela-de-conteúdo)
- [Página de Inatividade do Sistema](#página-de-inatividade-do-sistema)
  - [Desenvolvimento: NRDO - Manutenção](#desenvolvimento-nrdo---manutenção)
  - [Homologação: NRDO - Manutenção](#homologação-nrdo---manutenção)
  - [Produção: NRDO - Manutenção](#produção-nrdo---manutenção)
- [Deploy da Aplicação](#deploy-da-aplicação)
  - [Homologação NRDO](#homologação-nrdo)
    - [Arquitetura](#arquitetura)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais)
    - [2. Backup ssp-nrdo-ear](#2-backup-ssp-nrdo-ear)
    - [3. Update ssp-nrdo-ear](#3-update-ssp-nrdo-ear)
  - [Produção Preview: Novo Registro Digital de Ocorrência](#produção-preview-novo-registro-digital-de-ocorrência)
    - [Arquitetura](#arquitetura-1)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais-1)
    - [2. Backup ssp-inquerito-preview-ear](#2-backup-ssp-inquerito-preview-ear)
    - [3. Update ssp-nrdo-preview-ear](#3-update-ssp-nrdo-preview-ear)
  - [Produção Novo Registro Digital de Ocorrência](#produção-novo-registro-digital-de-ocorrência)
    - [Arquitetura](#arquitetura-2)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais-2)
    - [2. Backup ssp-inquerito-ear](#2-backup-ssp-inquerito-ear)
    - [3. Update ssp-nrdo-ear](#3-update-ssp-nrdo-ear-1)

# Página de Inatividade do Sistema

Demonstrar os procedimentos necessários para habilitar a desabilitar a página de Manutenção e Inatividade dos Sistemas NRDO. A Execução deve ser realizada sob aprovação da Gestão de Mudanças (GMUD).

> Antes de iniciar qualquer alteração nas configurações é necessário realizar backup dos arquivos e diretórios que deverão ser alterados.

## Desenvolvimento: NRDO - Manutenção

Abaixo listamos **todas as informações necessárias** para a **execução deste procedimento**

* Artefatos para site de Manutenção: 
    * **[pcsp_files.zip](/uploads/2eacdd7274daebe7e10559f3eca44119/pcsp_files.zip)** 
* Contextos utilizados:
    * **/nrdo**
    * **/integracaoRDO**
* Diretório e arquivos configurações: 
    * **/opt/IBM/HTTPServer/conf**
    

adicionar no arquivo **http.conf**, e adicionar o conteúdo no arquivo.

```bash
## BLOQUEIO DO NRDO OFFLINE
        <Location "/nrdo">
        ProxyPass               http://10.200.9.16/pcsp.html
        ProxyPassReverse        http://10.200.9.16/pcsp.html
        </Location>
## BLOQUEIO DO integracaoRDO OFFLINE
        <Location "/integracaoRDO">
        ProxyPass               http://10.200.9.16/pcsp.html
        ProxyPassReverse        http://10.200.9.16/pcsp.html
        </Location>
```

Após **salvar as configurações** execute os **três procedimentos abaixo**:

```bash
/opt/IBM/HTTPServer/bin/apachectl configtest
/opt/IBM/HTTPServer/bin/apachectl stop
/opt/IBM/HTTPServer/bin/apachectl start
```

## Homologação: NRDO - Manutenção

## Produção: NRDO - Manutenção

# Deploy da Aplicação

Demonstrar os **procedimentos necessários para executar o deploy nos ambientes das aplicações do NRDO.** A execução deve ser realizada conforme, **ITQ-7.5-251 - Execução e Acompanhamento de job no Control-M WLA** (Procedimento Prodesp).

Antes de iniciar o procedimento de deploy é necessário **validar o espaço em disco, consumo de memória e cpu dos servidores que receberão a nova versão da aplicação e além disso é necessário validar se a versão atual não apresenta nenhum problema** que deve ser resolvida antes da execução.
É importante **realizar backup da versão atual** caso seja necessário a **execução de um rollback.**
Abaixo é apresentado a execução para os _**ambientes de Desenvolvimento | Homologação | Produção**_


## Homologação NRDO 

### Arquitetura

A seguir é demonstrado **desenho da arquitetura provisionada** na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do sistema da NRDO.

>**Nota:** O diagrama acima pode ser **baixado em formato svg** clicando [aqui](assets/diagrams/legado/HOM_NRDO.svg). Se desejar, baixe a **[versão em XML](assets/diagrams/legado/DEV_Delegacia_Eletronica.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura NRDO HOM](assets/diagrams/legado/HOM_NRDO.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.13.98/nrdo/**
* Acesso ao WebSphere **https://10.200.77.78:9043/ibm/console/logon.jsp**

![Website NRDO](/assets/img/NRDO/website_NRDO_hom.png)

<br>

Verifique a **versão da aplicação NRDO**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:


**CRQ000000678663** - Finalizado <br>
**Ambiente**: ***Homologação*** <br>
**Aplicação**: ***NRDO*** <br>
**DE**    :   ***5.9.0 (25/02/2025) *** <br>
***PARA***:   ***5.10.0 (12/05/2025) *** <br>

***OBS: A versão da aplicação encontra-se no rodapé do website***

### 2. Backup ssp-nrdo-ear

Vamos acessar a console de **Administração do ambiente da NRDO**, para isso acesse:

![Websphere Inquérito](/assets/img/NRDO/websphere_console_nrdo_hom.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-nrdo-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/NRDO/websphere_export_ear.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/NRDO/websphere_backup_ear.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **caetite** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/NRDO/backup_ear_nrdo_hom.png)

### 3. Update ssp-nrdo-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/NRDO/websphere_update_ear_hom.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-nrdo-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/NRDO/websphere_deploy_ear.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/NRDO/websphere_deployII_ear.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy II ear](/assets/img/NRDO/websphere_deployIII_hom_ear.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/NRDO/websphere_deployIV_hom_ear.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/NRDO/websphere_deployV_hom_ear.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-de-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/NRDO/websphere_deployVI_ear.png)

<br>

## Produção Preview: Novo Registro Digital de Ocorrência 

### Arquitetura

A seguir é **demonstrado desenho da arquitetura** provisionada na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do **sistema da Novo Registro Digital de Ocorrência.**

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](assets/diagrams/legado/PROD_NRDO.svg). Se desejar, baixe a **[versão em XML](assets/diagrams/legado/PROD_NRDO.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Inquérito Policial DEV](/assets/diagrams/legado/PROD_NRDO.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.173.25/nrdo-preview/**

![Website NRDO](/assets/img/NRDO/preview/001.png)

Verifique a **versão da aplicação NRDO**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:

**CRQ000000497613** - Finalizado <br>
**Ambiente**: ***Produção*** <br>
**Aplicação**: ***NRDO*** <br>
**DE**    :   ***Versão 5.9.0 (25/02/2025)*** <br>
***PARA***:   ***Versão 5.9.0 (25/02/2025)*** <br>

### 2. Backup ssp-inquerito-preview-ear

Vamos acessar a console de **administração do ambiente NRDO**, para isso acesse:

![Websphere Inquérito](/assets/img/NRDO/preview/002.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-nrdo-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/NRDO/preview/003.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/NRDO/preview/004.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **matina-ws1** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/NRDO/preview/005.png)

### 3. Update ssp-nrdo-preview-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/NRDO/preview/006.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-nrdo-preview-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/NRDO/preview/007.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/NRDO/preview/008.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy III ear](/assets/img/NRDO/preview/009.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/NRDO/preview/010.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/NRDO/preview/011.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-nrdo-preview-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/NRDO/preview/012.png)

<br>

## Produção Novo Registro Digital de Ocorrência 

### Arquitetura

A seguir é **demonstrado desenho da arquitetura** provisionada na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do **sistema da Novo Registro Digital de Ocorrência.**

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](assets/diagrams/legado/PROD_NRDO.svg). Se desejar, baixe a **[versão em XML](assets/diagrams/legado/PROD_NRDO.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Inquérito Policial DEV](/assets/diagrams/legado/PROD_NRDO.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.173.24/nrdo/**

![Website NRDO](/assets/img/NRDO/prod/001.png)

Verifique a **versão da aplicação NRDO**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:

**CRQ000000497613** - Finalizado <br>
**Ambiente**: ***Produção*** <br>
**Aplicação**: ***NRDO*** <br>
**DE**    :   ***Versão 5.9.0 (25/02/2025)*** <br>
***PARA***:   ***Versão 5.9.0 (25/02/2025)*** <br>

### 2. Backup ssp-inquerito-ear

Vamos acessar a console de **administração do ambiente NRDO**, para isso acesse:

![Websphere Inquérito](/assets/img/NRDO/prod/002.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-nrdo-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/NRDO/prod/003.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/NRDO/prod/004.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **matina-ws1** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/NRDO/prod/005.png)

### 3. Update ssp-nrdo-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/NRDO/prod/006.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-inquerito-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/NRDO/prod/007.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/NRDO/prod/008.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy III ear](/assets/img/NRDO/prod/009.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/NRDO/prod/010.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/NRDO/prod/011.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-nrdo-preview-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/NRDO/prod/012.png)

<br>