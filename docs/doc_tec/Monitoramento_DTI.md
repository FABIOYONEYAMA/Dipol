# Sobre

Seção **destinada a documentação** do sistema **Monitoramento_DTI**, com _procedimentos técnicos, desenho da arquitetura e recursos disponíveis_.

# Tabela de Conteúdo
- [Sobre](#sobre)
- [Tabela de Conteúdo](#tabela-de-conteúdo)
- [Deploy da Aplicação](#deploy-da-aplicação)
  - [Produção Monitoramento\_DTI](#produção-monitoramento_dti)
    - [Arquitetura](#arquitetura)
    - [1. Procedimentos Iniciais](#1-procedimentos-iniciais)
    - [2. Backup ssp-monitoramentoDTI](#2-backup-ssp-monitoramentodti)
    - [3. Update ssp-monitoramentoDTI](#3-update-ssp-monitoramentodti)


# Deploy da Aplicação

Demonstrar os **procedimentos necessários para executar o deploy nos ambientes das aplicações do Monitoramento_DTI.** A execução deve ser realizada conforme, **ITQ-7.5-251 - Execução e Acompanhamento de job no Control-M WLA** (Procedimento Prodesp).

Antes de iniciar o procedimento de deploy é necessário **validar o espaço em disco, consumo de memória e cpu dos servidores que receberão a nova versão da aplicação e além disso é necessário validar se a versão atual não apresenta nenhum problema** que deve ser resolvida antes da execução.
É importante **realizar backup da versão atual** caso seja necessário a **execução de um rollback.**
Abaixo é apresentado a execução para os _**ambientes de Desenvolvimento | Homologação | Produção**_

## Produção Monitoramento_DTI

### Arquitetura

A seguir é **demonstrado desenho da arquitetura** provisionada na infraestrutura On-Premise para os projetos da Polícia Civil do Estado de São Paulo do **sistema do Monitoramento_DTI.**

>**Nota:** O diagrama acima pode ser **baixado em formato SVG** clicando [aqui](assets/diagrams/legado/PROD_Monitoramento_DTI.svg). Se desejar, baixe a **[versão em XML](assets/diagrams/legado/PROD_Monitoramento_DTI.xml)** compatível com a **ferramenta [Draw.io](https://app.diagrams.net/).**

![Arquitetura Monitoramento_DTI PROD](assets/diagrams/legado/PROD_Monitoramento_DTI.png)

### 1. Procedimentos Iniciais

Antes de executar o **procedimento de deploy** certifique-se que a **aplicação está funcionando corretamente**, para isso devemos executar alguns passos. Acesse as seguintes URLS:

* Acesso intragov **http://10.200.173.25/monitoramentoDTI/index.xhtml**

![Website Monitoramento_DTI](/assets/img/Monitoramento_DTI/PROD/001.png)

Verifique a **versão da aplicação Monitoramento DTI**, para no final da execução do **deploy** validar a **nova versão**. Para isso salve em um bloco de notas a informação  **(DE | PARA)** da versão do ambiente conforme exemplo abaixo:

**CRQ000000672632** - Finalizado <br>
**Ambiente**: ***Produção*** <br>
**Aplicação**: ***Monitoramento_DTI*** <br>
**DE**    :   ***Versão 2.12.0 (19/02/2025)*** <br>
***PARA***:   ***Versão 2.13.0 (26/03/2025)*** <br>


***OBS: A versão da aplicação encontra-se no rodapé do website***

### 2. Backup ssp-monitoramentoDTI

Vamos acessar a console de **Administração do ambiente do Monitoramento_DTI**, para isso acesse:

![Websphere Inquérito](/assets/img/Monitoramento_DTI/PROD/002.png)

No **console administrativo** acesse o **Menu** ***>*** **Applications** ***>*** **Application Types** ***>*** **WebSphere Enterprise Applications**, marque o serviço **“ssp-monitoramentoDTI-ear ”** e clique em **“Export”**. Vamos exportar o arquivo ear para realizar o **backup do ear original**.

![Websphere export ear](/assets/img/Monitoramento_DTI/PROD/003.png)

Salve o arquivo em seu **HD por segurança** ***clicando no nome do arquivo** e depois clique em **“Voltar”** para continuarmos o processo

![Websphere export ear](/assets/img/Monitoramento_DTI/PROD/004.png)

**Salve o arquivo de backup da aplicação** e clique no **servidor** **caetite** no **diretório: /opt/backup**, criando uma pasta conforme este modelo: **aaaa/mm/dd_CRQxxxxxxxx**

![Websphere backup ear](/assets/img/Monitoramento_DTI/PROD/005.png)


### 3. Update ssp-monitoramentoDTI

Selecione novamente a **aplicação** e **prossiga com a atualização** clicando no botão **“Update”**.

![Websphere export ear](/assets/img/Monitoramento_DTI/PROD/003.png)

Em **Application to be updated**, verifique se o nome da aplicação está correta, **ssp-monitoramentoDTI-ear **, em **Specify the path to the replacement ear file** selecione o **arquivo de deploy** clicando em **“Selecionar arquivo”** e prossiga clicando em **“Next”**. Mantenha todas as outras marcações conforme imagem abaixo.

![Websphere deploy ear](/assets/img/Monitoramento_DTI/PROD/006.png)

Em **How do you want to install the application?** Selecione **"Fast Path - Prompt only when additional information is required."** Depois clique em **"Next."**

![Websphere deploy II ear](/assets/img/Monitoramento_DTI/PROD/007.png)

Na próxima tela **marque as mesmas opções que a imagem** e prossiga clicando em **"Next"**

![Websphere deploy III ear](/assets/img/Monitoramento_DTI/PROD/008.png)

***Atenção:*** Verificar se **todos os parâmetros se encontram conforme a imagem abaixo**, caso haja alguma divergência, **ajustar seguindo documentação**. Não havendo divergência, nesta próxima tela pode clicar diretamente em **“Next”**

![Websphere deploy IV ear](/assets/img/Monitoramento_DTI/PROD/009.png)

Prossiga clicando em **“Finish”**.

![Websphere deploy V ear](/assets/img/Monitoramento_DTI/PROD/010.png)

Após a **execução** aparecerá a seguinte mensagem:  **Application ssp-monitoramentoDTI-ear installed successfully**, clique em **save** e aguarde a aplicação iniciar.

![Websphere deploy VI ear](/assets/img/Monitoramento_DTI/PROD/011.png)