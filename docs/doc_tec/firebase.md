## Sobre

O **Firebase Cloud Messaging (FCM)** é uma **solução de mensagens entre plataformas** que permite a **entrega confiável de mensagens** sem custo.

Usando o FCM, você pode **notificar um app cliente de que novos e-mails ou outros dados estão disponíveis para sincronização.** Você pode enviar **mensagens de notificação** para promover novas interações e a retenção de usuários. 

_Para casos de uso como mensagens instantâneas, uma mensagem pode transferir um payload de até 4096 bytes para um app cliente._

# Tabela de Conteúdo

- [Tabela de Conteúdo](#tabela-de-conteúdo)
  - [Faturamento](#faturamento)
  - [Instâncias](#instâncias)
  - [Firebase](#firebase)
  - [Firebase Messaging API: Desenvolvimento](#firebase-messaging-api-desenvolvimento)
    - [Adicionando APPs](#adicionando-apps)
  - [Firebase Messaging API: Homologação](#firebase-messaging-api-homologação)
    - [Adicionando APPs](#adicionando-apps-1)
  - [Firebase Messaging API: Produção](#firebase-messaging-api-produção)
    - [Adicionando APPs](#adicionando-apps-2)

<br>

## Faturamento

**Sem custo de ativação da API**.

## Instâncias
Abaixo é informada as **instâncias dos ambientes** de **DESENVOLVIMENTO, HOMOLOGAÇÃO e PRODUÇÃO**.

Name                           | Type                         | Environment         | Region                 |
------------------------------ | ---------------------------- | ------------------- | ---------------------- |
fcm.googleapis.com             | Firebase Cloud Messaging API | Desenvolvimento     | southamerica           |
5000916-Dipol-Sist-Invest-Dev  | Firebase Console / Projects  | Desenvolvimento     | southamerica           |
fcm.googleapis.com             | Firebase Cloud Messaging API | Homologação         | southamerica           |
5000917-Dipol-Sist-Invest-Hom  | Firebase Console / Projects  | Homologação         | southamerica           |
fcm.googleapis.com             | Firebase Cloud Messaging API | Produção            | southamerica           |
5000034-Dipol-Sist-Invest-Prod | Firebase Console / Projects  | Produção            | southamerica           |


## Firebase

O Serviço será utilizado para **envio de mensagens de notificações para o aplicativo mobile** e deverá ser provisionado nos **ambientes de desenvolvimento, homologação e produção.**

## Firebase Messaging API: Desenvolvimento

1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/firebase/dev/001-firebase.png)

2. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/firebase/dev/002-firebase.png)

3. Na caixa de **pesquisa digite Firebase** e selecione **Firebase Cloud Messaging API**

![Google CLOUD Login](/assets/img/firebase/dev/003-firebase.png)

4. Na tela da **API do Firebase**, clique no botão **habilitar** após alguns segundos aparecerá o botão **Gerenciar**

![Google CLOUD Login](/assets/img/firebase/dev/004-firebase.png)

5. Tela de detalhes da **API/serviço**

![Google CLOUD Login](/assets/img/firebase/dev/005-firebase.png)

6. Após **habilitar a API**, acesse a console do **Firebase**
[Firebase Console](https://console.firebase.google.com/)

![Google CLOUD Login](/assets/img/firebase/dev/006-firebase.png)

7. Selecione o **Menu**, criar um projeto

![Google CLOUD Login](/assets/img/firebase/dev/007-firebase.png)

8. Clique em **Adicionar o Firebase ao projeto do Google Cloud**

![Google CLOUD Login](/assets/img/firebase/dev/008-firebase.png)

9. Digite o nome do projeto **5000916-Dipol-Sist-Invest-Dev** e clique em **Continuar**

![Google CLOUD Login](/assets/img/firebase/dev/009-firebase.png)

10. Confirmar o **plano Blaze** (Pagamento por utilização)

![Firebase config](/assets/img/firebase/dev/010-firebase.png)

11. Dados **sobre a contratação e plano**

![Firebase config](/assets/img/firebase/dev/011-firebase.png)

12. **Google Analytics (desabilitado não foi solicitado)**

![Firebase config](/assets/img/firebase/dev/012-firebase.png)

13. Tela de finalização de configuração

![Firebase config](/assets/img/firebase/dev/013-firebase.png)

14. **Dashboard do ambiente de desenvolvimento**

![Firebase config](/assets/img/firebase/dev/014-firebase.png)

### Adicionando APPs

1. Em **Project Overview**, vamos **adicionar** um **novo APP**. Conforme imagem abaixo:

![Firebase config](/assets/img/firebase/dev/015-firebase.png)

2. Selecione o ícone **Android** para adicionar um **novo APP**

![Firebase config](/assets/img/firebase/dev/016-firebase.png)

3. Agora vamos adicionar o Firebase para o nosso **App Android**
    * **Android package name:** br.ipemobile.app
    * **App nickname:** ipe mobile
    * **debub signing:** não alterar

![Firebase config](/assets/img/firebase/dev/017-firebase.png)

4. Faça o **download do json** para adicionar em seu **Aplicativo**

![Firebase config](/assets/img/firebase/dev/018-firebase.png)

5. Selecione o ícone de **Configurações** e acesse o **Menu Service Accounts**

![Firebase config](/assets/img/firebase/dev/019-firebase.png)

6. Em Firebase Admin SDK selecione:
    * **Admin SDK Configuration:**
        * Java
        * Generate New private key

![Firebase config](/assets/img/firebase/dev/020-firebase.png)

7. Envie para o **desenvolvedor os arquivos JSON** para incluir no **Aplicativo**

8. Selecione o ícone **IOS** para adicionar um **novo APP**

![Firebase config](/assets/img/firebase/dev/022-firebase.png)

9. Agora vamos adicionar o Firebase para o nosso **App IOS**
    * **Android package name:** br.ipemobile.app
    * **App nickname:** ipe mobile
    * **debub signing:** não alterar

![Firebase config](/assets/img/firebase/dev/023-firebase.png)

10. Faça o **download do json** para adicionar em seu **Aplicativo**

![Firebase config](/assets/img/firebase/dev/024-firebase.png)

11. Selecione o botão **next** para concluír as configurações

![Firebase config](/assets/img/firebase/dev/025-firebase.png)

12. Após a configuração do **APP IOS**, precisamos realizar as configurações de Autenticação ou **APN para os Apps Apple**, para isso vamos acessar o **Menu Project Overview** e acessar o menu **Cloud Messaging**, conforme é demonstrado na imagem abaixo:

![Firebase config](/assets/img/firebase/dev/028-firebase.png)

13. Em **Apple app Configuration** selecione o **Apple apps ipe mobile**, e em **APNs Authentication key**, clique no botão **Upload**

![Firebase config](/assets/img/firebase/dev/029-firebase.png)

14. Uma nova janela será aberta e é necessário informar os valores para upload da key
    * **APNs auth key:** [Key APP IOS](/assets/service_accout/firebase/AuthKey_RD466526WH.p8)
    * **Key ID:** RD466526WH
    * **Team ID:** C32FDC6C6Q

![Firebase config](/assets/img/firebase/dev/030-firebase.png)

15. Configuração dos **arquivos APNs** de **autenticação**

![Firebase config](/assets/img/firebase/dev/031-firebase.png)

## Firebase Messaging API: Homologação

1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/firebase/hom/001-firebase.png)

2. No menu de projetos selecione o projeto desejado **5000917-Dipol-Sist-Invest-Hom**

![Google CLOUD Login](/assets/img/firebase/hom/002-firebase.png)

3. Na caixa de **pesquisa digite Firebase** e selecione **Firebase Cloud Messaging API**

![Google CLOUD Login](/assets/img/firebase/hom/003-firebase.png)

4. Na tela da **API do Firebase**, clique no botão **habilitar** após alguns segundos aparecerá o botão **Gerenciar**

![Google CLOUD Login](/assets/img/firebase/hom/004-firebase.png)

5. Tela de detalhes da **API/serviço**

![Google CLOUD Login](/assets/img/firebase/hom/005-firebase.png)

6. Após **habilitar a API**, acesse a console do **Firebase**
[Firebase Console](https://console.firebase.google.com/)

![Google CLOUD Login](/assets/img/firebase/hom/006-firebase.png)

7. Selecione o **Menu**, criar um projeto

![Google CLOUD Login](/assets/img/firebase/hom/007-firebase.png)

8. Clique em **Adicionar o Firebase ao projeto do Google Cloud**

![Google CLOUD Login](/assets/img/firebase/hom/008-firebase.png)

9. Digite o nome do projeto **5000917-Dipol-Sist-Invest-Hom** e clique em **Continuar**

![Google CLOUD Login](/assets/img/firebase/hom/009-firebase.png)

10. Confirmar o **plano Blaze** (Pagamento por utilização)

![Firebase config](/assets/img/firebase/hom/010-firebase.png)

11. Dados **sobre a contratação e plano**

![Firebase config](/assets/img/firebase/hom/011-firebase.png)

12. **Google Analytics (desabilitado não foi solicitado)**

![Firebase config](/assets/img/firebase/hom/012-firebase.png)

13. Tela de finalização de configuração

![Firebase config](/assets/img/firebase/hom/013-firebase.png)

14. **Dashboard do ambiente de homologação**

![Firebase config](/assets/img/firebase/hom/014-firebase.png)

### Adicionando APPs

1. Em **Project Overview**, vamos **adicionar** um **novo APP**. Conforme imagem abaixo:

![Firebase config](/assets/img/firebase/hom/015-firebase.png)

2. Selecione o ícone **Android** para adicionar um **novo APP**

![Firebase config](/assets/img/firebase/hom/016-firebase.png)

3. Agora vamos adicionar o Firebase para o nosso **App Android**
    * **Android package name:** br.ipemobile.app
    * **App nickname:** ipe mobile
    * **debub signing:** não alterar

![Firebase config](/assets/img/firebase/hom/017-firebase.png)

4. Faça o **download do json** para adicionar em seu **Aplicativo**

![Firebase config](/assets/img/firebase/hom/018-firebase.png)

5. Selecione o ícone de **Configurações** e acesse o **Menu Service Accounts**

![Firebase config](/assets/img/firebase/hom/019-firebase.png)

6. Em Firebase Admin SDK selecione:
    * **Admin SDK Configuration:**
        * Java
        * Generate New private key

![Firebase config](/assets/img/firebase/hom/020-firebase.png)

7. Envie para o **desenvolvedor apenas o arquivo JSON mobilesdk_app** para incluir no **Aplicativo**
   1. > Atenção: **Não enviar a service account AdminSDK**, esta **service account** deverá ser **configurada do secret do cluster kubernetes**

8. Selecione o ícone **IOS** para adicionar um **novo APP**

![Firebase config](/assets/img/firebase/hom/021-firebase.png)

9. Agora vamos adicionar o Firebase para o nosso **App IOS**
    * **Android package name:** br.ipemobile.app
    * **App nickname:** ipe mobile
    * **debub signing:** não alterar

![Firebase config](/assets/img/firebase/hom/022-firebase.png)

10. Faça o **download do json** para adicionar em seu **Aplicativo**

![Firebase config](/assets/img/firebase/hom/023-firebase.png)

11. Selecione o botão **next** para concluír as configurações

![Firebase config](/assets/img/firebase/hom/024-firebase.png)

12. Após a configuração do **APP IOS**, precisamos realizar as configurações de Autenticação ou **APN para os Apps Apple**, para isso vamos acessar o **Menu Project Overview** e acessar o menu **Cloud Messaging**, conforme é demonstrado na imagem abaixo:

![Firebase config](/assets/img/firebase/hom/025-firebase.png)

13. Em **Apple app Configuration** selecione o **Apple apps ipe mobile**, e em **APNs Authentication key**, clique no botão **Upload**

![Firebase config](/assets/img/firebase/hom/026-firebase.png)

14. Uma nova janela será aberta e é necessário informar os valores para upload da key
    * **APNs auth key:** [Key APP IOS](/assets/service_accout/firebase/AuthKey_RD466526WH.p8)
    * **Key ID:** RD466526WH
    * **Team ID:** C32FDC6C6Q

![Firebase config](/assets/img/firebase/hom/027-firebase.png)

## Firebase Messaging API: Produção

1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/firebase/prod/001-firebase.png)

2. No menu de projetos selecione o projeto desejado **5000036-Dipol-Sist-Invest-Prod**

![Google CLOUD Login](/assets/img/firebase/prod/002-firebase.png)

3. Na caixa de **pesquisa digite Firebase** e selecione **Firebase Cloud Messaging API**

![Google CLOUD Login](/assets/img/firebase/prod/003-firebase.png)

4. Na tela da **API do Firebase**, clique no botão **habilitar** após alguns segundos aparecerá o botão **Gerenciar**

![Google CLOUD Login](/assets/img/firebase/prod/004-firebase.png)

5. Tela de detalhes da **API/serviço**

![Google CLOUD Login](/assets/img/firebase/prod/005-firebase.png)

6. Após **habilitar a API**, acesse a console do **Firebase**
[Firebase Console](https://console.firebase.google.com/)

![Google CLOUD Login](/assets/img/firebase/dev/006-firebase.png)

7. Selecione o **Menu**, criar um projeto

![Google CLOUD Login](/assets/img/firebase/prod/007-firebase.png)

8. Clique em **Adicionar o Firebase ao projeto do Google Cloud**

![Google CLOUD Login](/assets/img/firebase/prod/008-firebase.png)

9. Digite o nome do projeto **5000034-Dipol-Sist-Invest-Prod** e clique em **Continuar**

![Google CLOUD Login](/assets/img/firebase/prod/009-firebase.png)

10. Confirmar o **plano Blaze** (Pagamento por utilização)

![Firebase config](/assets/img/firebase/prod/010-firebase.png)

11. Dados **sobre a contratação e plano**

![Firebase config](/assets/img/firebase/prod/011-firebase.png)

12. **Google Analytics (desabilitado não foi solicitado)**

![Firebase config](/assets/img/firebase/prod/012-firebase.png)

13. Tela de finalização de configuração

![Firebase config](/assets/img/firebase/prod/013-firebase.png)

14. **Dashboard do ambiente de desenvolvimento**

![Firebase config](/assets/img/firebase/dev/014-firebase.png)

### Adicionando APPs

1. Em **Project Overview**, vamos **adicionar** um **novo APP**. Conforme imagem abaixo:

![Firebase config](/assets/img/firebase/prod/015-firebase.png)

2. Selecione o ícone **Android** para adicionar um **novo APP**

![Firebase config](/assets/img/firebase/prod/016-firebase.png)

3. Agora vamos adicionar o Firebase para o nosso **App Android**
    * **Android package name:** br.ipemobile.app
    * **App nickname:** ipe mobile
    * **debub signing:** não alterar

![Firebase config](/assets/img/firebase/prod/017-firebase.png)

4. Faça o **download do json** para adicionar em seu **Aplicativo**

![Firebase config](/assets/img/firebase/prod/018-firebase.png)

5. Selecione o ícone de **Configurações** e acesse o **Menu Service Accounts**

![Firebase config](/assets/img/firebase/prod/019-firebase.png)

6. Em Firebase Admin SDK selecione:
    * **Admin SDK Configuration:**
        * Java
        * Generate New private key
  
7. Envie para o **desenvolvedor apenas o arquivo JSON mobilesdk_app** para incluir no **Aplicativo**
   1. > Atenção: **Não enviar a service account AdminSDK**, esta **service account** deverá ser **configurada do secret do cluster kubernetes**

8. Selecione o ícone **IOS** para adicionar um **novo APP**

![Firebase config](/assets/img/firebase/prod/020-firebase.png)

9. Agora vamos adicionar o Firebase para o nosso **App IOS**
    * **Apple bundle ID:** br.ipemobile.app
    * **App nickname:** ipe mobile
    * **App store id:** não alterar

![Firebase config](/assets/img/firebase/prod/021-firebase.png)

10. Faça o **download do plist** para adicionar em seu **Aplicativo**

![Firebase config](/assets/img/firebase/prod/022-firebase.png)

11. Selecione o botão **next** para concluír as configurações

![Firebase config](/assets/img/firebase/prod/023-firebase.png)

12. Após a configuração do **APP IOS**, precisamos realizar as configurações de Autenticação ou **APN para os Apps Apple**, para isso vamos acessar o **Menu Project Overview** e acessar o menu **Cloud Messaging**, conforme é demonstrado na imagem abaixo:

![Firebase config](/assets/img/firebase/prod/024-firebase.png)

13. Em **Apple app Configuration** selecione o **Apple apps ipe mobile**, e em **APNs Authentication key**, clique no botão **Upload**

![Firebase config](/assets/img/firebase/prod/025-firebase.png)

14. Uma nova janela será aberta e é necessário informar os valores para upload da key
    * **APNs auth key:** [Key APP IOS](/assets/service_accout/firebase/AuthKey_RD466526WH.p8)
    * **Key ID:** RD466526WH
    * **Team ID:** C32FDC6C6Q

![Firebase config](/assets/img/firebase/prod/026-firebase.png)