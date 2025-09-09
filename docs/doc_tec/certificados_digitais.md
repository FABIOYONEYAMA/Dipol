
# Sobre

Esta Seção é **destinada a documentação** de **Certificados Digitiais** utilizados pelos sistemas **DIPOL**, os _procedimentos técnicos, auxiliam na atualização do certificado desejado_

# Tabela de Conteúdo

- [Certificado Digital Assinatura](#)
- [Certificado Digital CemiSSP](#certificado-digital-cemissp)
- [Certificado Digital Detecta](#certificado-digital-detecta)
- [Certificado Digital Google Recaptcha](#certificado-digital-google-recaptcha)
<br>
<br>
<br>

# Certificado Digital CemiSSP

### Sobre

**Atualização manual é necessária** e o **certificado** tem **prazo de 1 ano**, sendo **rotacionado 30 dias antes ou menos** da **data fim** do **certificado**

### CEMI Serviços

**O CEMI** é uma plataforma centralizada com o **objetivo de impedir que aparelhos de telefonia móvel roubados, furtados ou extraviados sejam utilizados indevidamente nas redes das operadoras brasileiras**. O **sistema é gerenciado pela Associação Brasileira de Recursos em Telecomunicações (ABR Telecom)**.

### Objetivo

Carregar **Chaves no repositorio do Java do Broker** (senha padrão: ******). Esta senha é solicitada **quando vamos carregar a chave para o cacerts**

Para **baixar o certificado digital** acesse: [cemissp](https://cemissp.com.br/cemiseguranca/) e baixe o **cer** diretamente do navegado

### Servidores relacionados

Os **servidores listados** abaixo devem ser adicionados o **certificado digital do CEMISSP**

|**Host**       |     **IP**        | 
--------------- | ----------------- |
|**ubata-app1** | **10.200.78.145** |

### Adicionando as variáveis do ambiente

Adicione as variáveis abaixo para agilizar o procedimento 

    export PATH_KEYTOOL="/opt/mqm/java/jre64/jre/bin/keytool"
    export STORE_PASSWORD="*******"
    export PATH_KEYSTORE="/opt/IBM/iib-10.0.0.15/common/jdk/jre/lib/security/cacerts"
    export ALIAS_CERT="sspcemi"
    export PATH_FILE=/var/mqsi/certificates/cemissp.cer

#### listar chaves
    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD

#### listar chaves especificas
    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD |grep $ALIAS_CERT

#### Deletar chaves sspcemi
    $PATH_KEYTOOL -delete -noprompt -alias $ALIAS_CERT -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD

#### listar chaves para verificar se as chaves foram excluídas
    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD |grep $ALIAS_CERT

#### Inserir novas Chaves
    $PATH_KEYTOOL -import -alias $ALIAS_CERT -file $PATH_FILE -storetype JKS -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD

#### listar se chaves foram inseridas
    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD |grep $ALIAS_CERT
  
#### stop EG
    mqsistopmsgflow IIB_SSP01_01 -e INTEGRA_TJ_TELECOM

#### start EG
    mqsistartmsgflow IIB_SSP01_01 -e INTEGRA_TJ_TELECOM

<br>
<br>

# Certificado Digital Detecta

### Sobre

**Atualização manual é necessária** e o **certificado** tem **prazo de 1 ano**, sendo **rotacionado 30 dias antes ou menos** da **data fim** do **certificado**


### Detecta Integração

O **Projeto Detecta** é um serviço da **segurança pública do Governo de São Paulo**, que utiliza tecnologia de **análise de dados e inteligência artificial** para monitorar e combater crimes de forma eficaz. 

### Objetivo

Carregar **Chaves no repositorio do Java do Broker** (senha padrão: **changeit**). Esta senha é solicitada **quando vamos carregar a chave para o cacerts**

Para **baixar o certificado digital** acesse: [Detecta Integração](https://servicos.detecta.sp.gov.br/) e baixe o **cer** diretamente do navegado

### Servidores relacionados

Os **servidores listados** abaixo devem ser adicionados o **certificado digital do detecta**

|**Host**       |     **IP**        | 
--------------- | ----------------- |
|**ubata-app1** | **10.200.78.145** |
|**ubata-app2** | **10.200.78.146** |

### Adicionando as variáveis do ambiente
Adicione as variáveis abaixo para agilizar o procedimento 

    export PATH_KEYTOOL="/opt/mqm/java/jre64/jre/bin/keytool"
    export STORE_PASSWORD="changeit"
    export PATH_KEYSTORE="/opt/IBM/iib-10.0.0.15/common/jdk/jre/lib/security/cacerts"
    export ALIAS_CERT="detecta"
    export PATH_FILE=/var/mqsi/certificates/detecta.cer

#### listar chaves

    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD

#### listar chaves especificas

    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD |grep $ALIAS_CERT

#### Deletar chaves detecta serviços

    $PATH_KEYTOOL -delete -noprompt -alias $ALIAS_CERT -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD

#### listar chaves para verificar se as chaves foram excluídas

    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD |grep $ALIAS_CERT

#### Inserir novas Chaves

    $PATH_KEYTOOL -import -alias $ALIAS_CERT -file $PATH_FILE -storetype JKS -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD

#### listar se chaves foram inseridas

    $PATH_KEYTOOL -list -keystore $PATH_KEYSTORE -storepass $STORE_PASSWORD |grep $ALIAS_CERT
  
#### stop EG

    mqsistopmsgflow IIB_SSP01_01 -e INTEGRA_TJ
    mqsistopmsgflow IIB_SSP02_01 -e INTEGRA_TJ

#### start EG

    mqsistartmsgflow IIB_SSP01_01 -e INTEGRA_TJ
    mqsistartmsgflow IIB_SSP02_01 -e INTEGRA_TJ


### Certificado Digital Google Recaptcha

**A reCAPTCHA** usa um **mecanismo** avançado de **análise de riscos e desafios adaptativos** para evitar que softwares maliciosos se envolvam em **atividades abusivas em seu site**. Enquanto isso, usuários legítimos poderão fazer login, fazer compras, visualizar páginas ou criar contas e usuários falsos serão bloqueados.

### 1. Backup
O primeiro procedimento a ser realizado é o **backup do certificado atual**, caso seja necessário podemos **voltar o arquivo novamente para a aplicação.**

**No diretório:**
    
    /opt/certificados

**Copie o arquivo original** para o **diretório de backup.**

    cp /opt/certificados/google_2022.cer /opt/certificados/backup/

![Google Recaptcha Inquérito](/assets/img/certificado-digitais/certificado_google_recaptcha.png)


### 2. Download Certificado

Acesse o website do google recaptcha em: https://www.google.com/recaptcha/, clique no **cadeado** do navegador e selecione **"A conexão é segura"**

![Download Cert Google](/assets/img/certificado-digitais/google_cert_download_web.png)

Em **"A Conexão é Segura"** selecione o icone do certificado para visualizar e baixar

![Download Cert Google Crt](/assets/img/certificado-digitais/google_cert_download_crt.png)

Na caixa de visualização do certificado, selecione o Menu **Detalhes**  e em **Hierarquia de  Certificados** deixe selecionado opção **GTS1 Root R1** e clique no botão, **Exportar o certificado selecionado**

![Download Cert Google Crt Detalhes](/assets/img/certificado-digitais/google_cert_download_crt_detalhes.png)

**Salve o arquivo** no diretório **/opt/certificados** conforme detalhe abaixo:

    cp google_2022.cer /opt/certificados/

Abra a Console do **IBM Websphere** para realizar a instalação do **certificado digital** google recaptcha

![Websphere Inquérito](/assets/img/certificado-digitais/websphere_console_inq.png)

No **console administrativo** acesse o **Menu** ***>*** **Security** ***>*** **SSL certificate and key management**.

![Websphere Inquérito Security](/assets/img/certificado-digitais/websphere_security.png)

Em **SSL certificate and key management**, vamos selecionar o link **key stores and certificates** que se encontra do lado direito da Console em **Related Items**

![Websphere Inquérito Key Store](/assets/img/certificado-digitais/websphere_keystore_and_certificates.png)

Vamos encontrar acessar na lista o nome do recurso **CellDefaultTruststore** para verificar a lista de certificados instalados

![Websphere Inquérito Cell truststore](/assets/img/certificado-digitais/websphere_cell_trutstore.png)

Clique em **Signer Certificate** conforme imagem abaixo:

![Websphere Inquérito Signer Certificates](/assets/img/certificado-digitais/websphere_signer_certificates.png)

Vamos Adicionar o novo **Certificado**:<br>
**Campo Alias**: ***google_recaptcha*** <br>
**File Name**: ***/opt/certificados/google_2022.cer***<br>
**Data Type**: ***Base64-encoded ASCII data*** <br>
Clique em **Apply** e posteriormente em **OK**

![Websphere Inquérito New Google Cert](/assets/img/certificado-digitais/websphere_new_google_cert.png)

Após o procedimento clique em **save**, para guardar as informações e **depois execute o ripplestart**. **Executando o procedimento** que pode ser ***acessado aqui:*** [RippleStart]()

<br>
<br>