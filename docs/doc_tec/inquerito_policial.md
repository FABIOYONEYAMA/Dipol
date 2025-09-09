# Sobre

Seção **destinada a documentação** da **Inquérito Policial Eletrônico**, com _procedimentos técnicos, desenho da arquitetura e recursos disponíveis_.

# Tabela de Conteúdo

- [Sobre](#sobre)
- [Tabela de Conteúdo](#tabela-de-conteúdo)
- [Deploy da Aplicação](#deploy-da-aplicação)
  - [Desenvolvimento Inquérito Policial Eletrônico](#desenvolvimento-inquérito-policial-eletrônico)
    - [Arquitetura](#arquitetura)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais)
    - [2. Backup ssp-inquerito-ear](#2-backup-ssp-inquerito-ear)
    - [3. Update ssp-inquerito-ear](#3-update-ssp-inquerito-ear)
  - [Homologação Inquérito Policial Eletrônico](#homologação-inquérito-policial-eletrônico)
    - [Arquitetura](#arquitetura-1)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais-1)
    - [2. Backup ssp-inquerito-ear](#2-backup-ssp-inquerito-ear-1)
    - [3. Update ssp-inquerito-ear](#3-update-ssp-inquerito-ear-1)


# Deploy da Aplicação

Demonstrar os **procedimentos necessários para executar o deploy nos ambientes da aplicação do Inquérito policial Eletrônico.** A execução deve ser realizada conforme, **ITQ-7.5-251 - Execução e Acompanhamento de job no Control-M WLA** (Procedimento Prodesp).

Antes de iniciar o procedimento de deploy é necessário **validar o espaço em disco, consumo de memória e cpu dos servidores que receberão a nova versão da aplicação e além disso é necessário validar se a versão atual não apresenta nenhum problema** que deve ser resolvida antes da execução.
É importante **realizar backup da versão atual** caso seja necessário a **execução de um rollback.**
Abaixo é apresentado a execução para os _**ambientes de Desenvolvimento | Homologação | Produção**_


## Desenvolvimento Inquérito Policial Eletrônico 

### Arquitetura

A seguir é **demonstrado desenho da arquitetura** provisionada na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do **sistema da Inquérito Policial Eletrônico.**

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](assets/diagrams/legado/DEV_Inquerito_Policial.svg). Se desejar, baixe a **[versão em XML](assets/diagrams/legado/DEV_Inquerito_Policial.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Inquérito Policial DEV](/assets/diagrams/legado/DEV_Inquerito_Policial.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.9.16/inquerito**
* Acesso intragov **http://dev-rdo.policiacivil.sp.gov.br/inquerito/** 

![Website Inquérito](/assets/img/IPE/dev/001.png)

Verifique a **versão da aplicação Inquérito**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:

**CRQ000000497613** - Finalizado <br>
**Ambiente**: ***Produção*** <br>
**Aplicação**: ***Inquérito Policial*** <br>
**DE**    :   ***Versão v2.25   (12/04/2021)*** <br>
***PARA***:   ***Versão 2.27.84 (19/02/2025)*** <br>

### 2. Backup ssp-inquerito-ear

Vamos acessar a console de **administração do ambiente Inquérito**, para isso acesse:

![Websphere Inquérito](/assets/img/IPE/dev/002.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-inquerito-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/IPE/dev/003.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/IPE/dev/004.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **matina-ws1** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/IPE/dev/005.png)

### 3. Update ssp-inquerito-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/IPE/dev/006.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-inquerito-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/IPE/dev/007.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/IPE/dev/008.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy III ear](/assets/img/IPE/dev/009.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/IPE/dev/010.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/IPE/hom/websphere_deployV_ear.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-inquerito-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/IPE/hom/websphere_deployVI_ear.png)


## Homologação Inquérito Policial Eletrônico 

### Arquitetura

A seguir é **demonstrado desenho da arquitetura** provisionada na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do **sistema da Inquérito Policial Eletrônico.**

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](/assets/diagrams/legado/HOM_Inquerito_Policial.svg). Se desejar, baixe a **[versão em XML](/assets/diagrams/legado/HOM_Inquerito_Policial.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Inquérito Policial DEV](/assets/diagrams/legado/HOM_Inquerito_Policial.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.13.98/inquerito/**
* Acesso internet **não há** 

![Website Inquérito](/assets/img/IPE/hom/website_inquerito_hom.png)

Verifique a **versão da aplicação Inquérito**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:

**CRQ000000497613** - Finalizado <br>
**Ambiente**: ***Produção*** <br>
**Aplicação**: ***Inquérito Policial*** <br>
**DE**    :   ***Versão v2.25 12/04/2021*** <br>
***PARA***:   ***Versão v2.26 16/08/2022*** <br>

***OBS: A versão da aplicação encontra-se no rodapé do website***

### 2. Backup ssp-inquerito-ear

Vamos acessar a console de **administração do ambiente Inquérito**, para isso acesse:

![Websphere Inquérito](/assets/img/IPE/hom/websphere_console_inq_hom.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-inquerito-ear”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/IPE/hom/websphere_export_ear.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/IPE/hom/websphere_backup_ear.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **matina-ws1** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/IPE/hom/backup_ear_INQ_hom.png)

### 3. Update ssp-inquerito-ear

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere update ear](/assets/img/IPE/hom/websphere_update_ear.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-inquerito-ear**, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/IPE/hom/websphere_deploy_ear.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/IPE/hom/websphere_deployII_ear.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy III ear](/assets/img/IPE/hom/websphere_deployIII_ear.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/IPE/hom/websphere_deployIV_hom_ear.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/IPE/hom/websphere_deployV_ear.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-inquerito-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/IPE/hom/websphere_deployVI_ear.png)