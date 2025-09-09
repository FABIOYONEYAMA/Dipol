## Sobre

O **reCAPTCHA** usa técnicas avançadas de **análise de risco para detectar fraudes**. Com o reCAPTCHA, v**ocê pode proteger seus sites ou aplicativos para dispositivos móveis contra spam e abuso e detectar outros tipos de atividades fraudulentas**, como preenchimento de credenciais, invasão de conta e criação automatizada de contas. *O reCAPTCHA oferece detecção aprimorada com pontuações mais detalhadas, códigos de motivo para eventos de risco, SDKs para apps para dispositivos móveis, detecção de violação ou vazamento de senha, autenticação multifator e a capacidade de ajustar seu modelo específico do site para proteger empresas corporativas.*


# Tabela de Conteúdo
- [Tabela de Conteúdo](#tabela-de-conteúdo)
  - [Faturamento](#faturamento)
  - [Chaves reCAPTCHA](#chaves-recaptcha)
  - [reCAPTCHA](#recaptcha)
    - [Desenvolvimento: dipol-analitico](#desenvolvimento-dipol-analitico)
    - [Desenvolvimento: dipol-spj](#desenvolvimento-dipol-spj)
    - [Desenvolvimento: dipol-sso](#desenvolvimento-dipol-sso)
    - [Desenvolvimento: portal-web](#desenvolvimento-portal-web)


## Faturamento

**O reCAPTCHA** oferece **três níveis de uso**: *Enterprise, Standard e Essentials*. Para saber mais sobre os recursos disponíveis nesses níveis, consulte:
[Comparar recursos entre níveis do reCAPTCHA.](https://cloud.google.com/recaptcha/docs/compare-tiers?hl=pt-br)


## Chaves reCAPTCHA

Name                           | Segurança do desafio              | Environment         | Chave                  |
------------------------------ | --------------------------------- | ------------------- | ---------------------- |
dipol-analitico                | Dificuldade mais fácil do desafio | Desenvolvimento     | [Chave reCAPTCHA](https://console.cloud.google.com/security/recaptcha/6LetbPUpAAAAAP9ABlvF5mok3OwYL7v54kcdJD_p/overview?hl=pt-br&project=dipol-sist-invest-dev) |
dipol-spj                      | Dificuldade mais fácil do desafio | Desenvolvimento     | [Chave reCAPTCHA](https://console.cloud.google.com/security/recaptcha/6LdGy48qAAAAAKJacGpQHFtO3L3uKvkkfz0GWRUz/overview?hl=pt-br&project=dipol-sist-invest-dev) |
dipol-sso                      | Dificuldade mais fácil do desafio | Desenvolvimento     | [Chave reCAPTCHA](https://console.cloud.google.com/security/recaptcha/6LeEOPMqAAAAAMX3VgmWHgoGxiqAC1GawC4-jLYw/overview?hl=pt-br&project=dipol-sist-invest-dev) |
portal-web                     | Dificuldade média                 | Desenvolvimento     | [Chave reCAPTCHA](https://console.cloud.google.com/security/recaptcha/6LcjTCUqAAAAAAmZ1-tFVofmSVv498VlPqrCRNl3/overview?hl=pt-br&project=dipol-sist-invest-dev) |

## reCAPTCHA

O Serviço será utilizado para **para proteger** os sites e aplicativos contra spam e outros tipos de atividades fraudulentas nos **ambientes de desenvolvimento, homologação e produção.**

### Desenvolvimento: dipol-analitico
1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/001.png)

2. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/002.png)

3. Na caixa de **pesquisa digite reCAPTCHA** e selecione **reCAPTCHA**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/003.png)

4. O painel de **administração do reCAPTCHA** é aberto, **mostrando as configuraçãoes atuais**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/004.png)

5. Vamos criar a **chave do reCAPTCHA** *"dipol-analítico"*, selecione o botão de **+ Criar chave**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/005.png)

6. Na tela de **criação da chave** digite as *informações conforme descritas abaixo*:
   1. **Nome de exibição:** dipol-analitico
   2. **Escolher tipo de plataforma:** site

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/010.png)

7. **Lista de domínios**, cadastre os **domínios relacionados abaixo**:
   1. analitico-dev.ipe-policiacivil.sp.gov.br
   2. localhost

> **Atenção!** - *O domínio localhost* só deve ser **cadastrado em ambientes de desenvolvimento**

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/011.png)

8. Em **tipo de desafio**, marque a opção:
   1. **Usar desafio de caixa de seleção**
      1.  **Dificuldade mais fácil do desafio**
   2.  Clique "Criar chave"

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/012.png)

9. A chave deverá ser enviada para o arquiteto responsável pela configuração do aplicativo. 

![Google Cloud - ID reCAPTCHA](/assets/img/api/reCAPTCHA/dev/013.png)

### Desenvolvimento: dipol-spj
1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/001.png)

2. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/002.png)

3. Na caixa de **pesquisa digite reCAPTCHA** e selecione **reCAPTCHA**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/003.png)

4. O painel de **administração do reCAPTCHA** é aberto, **mostrando as configuraçãoes atuais**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/004.png)

5. Vamos criar a **chave do reCAPTCHA** *"dipol-spj"*, selecione o botão de **+ Criar chave**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/005.png)

6. Na tela de **criação da chave** digite as *informações conforme descritas abaixo*:
   1. **Nome de exibição:** dipol-spj
   2. **Escolher tipo de plataforma:** site

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/014.png)

7. **Lista de domínios**, cadastre os **domínios relacionados abaixo**:
   1. spj-dev.ipe-policiacivil.sp.gov.br
   2. localhost

> **Atenção!** - *O domínio localhost* só deve ser **cadastrado em ambientes de desenvolvimento**

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/015.png)

8. Em **tipo de desafio**, marque a opção:
   1. **Usar desafio de caixa de seleção**
      1.  **Dificuldade mais fácil do desafio**
   2.  Clique "Criar chave"

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/016.png)

9. A chave deverá ser enviada para o arquiteto responsável pela configuração do aplicativo. 

![Google Cloud - ID reCAPTCHA](/assets/img/api/reCAPTCHA/dev/017.png)

### Desenvolvimento: dipol-sso
1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/001.png)

2. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/002.png)

3. Na caixa de **pesquisa digite reCAPTCHA** e selecione **reCAPTCHA**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/003.png)

4. O painel de **administração do reCAPTCHA** é aberto, **mostrando as configuraçãoes atuais**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/004.png)

5. Vamos criar a **chave do reCAPTCHA** *"dipol-sso"*, selecione o botão de **+ Criar chave**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/005.png)

6. Na tela de **criação da chave** digite as *informações conforme descritas abaixo*:
   1. **Nome de exibição:** dipol-sso
   2. **Escolher tipo de plataforma:** site

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/006.png)

7. **Lista de domínios**, cadastre os **domínios relacionados abaixo**:
   1. sso-dev.ipe-policiacivil.sp.gov.br
   2. localhost

> **Atenção!** - *O domínio localhost* só deve ser **cadastrado em ambientes de desenvolvimento**

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/007.png)

8. Em **tipo de desafio**, marque a opção:
   1. **Usar desafio de caixa de seleção**
      1.  **Dificuldade mais fácil do desafio**
   2.  Clique "Criar chave"

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/008.png)

9. A chave deverá ser enviada para o arquiteto responsável pela configuração do aplicativo. 

![Google Cloud - ID reCAPTCHA](/assets/img/api/reCAPTCHA/dev/009.png)

### Desenvolvimento: portal-web
1. Acesse a **página de login** do ***Googleloud*** em: **[Google Cloud Login](https://cloud.google.com/?hl=pt-br)**
   1. Clique em **console** para abrir a **Console do Google Cloud**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/001.png)

2. No menu de projetos selecione o projeto desejado **5000916-Dipol-Sist-Invest-Dev**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/002.png)

3. Na caixa de **pesquisa digite reCAPTCHA** e selecione **reCAPTCHA**

![Google CLOUD Login](/assets/img/api/reCAPTCHA/dev/003.png)

4. O painel de **administração do reCAPTCHA** é aberto, **mostrando as configuraçãoes atuais**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/004.png)

5. Vamos criar a **chave do reCAPTCHA** *"portal-web"*, selecione o botão de **+ Criar chave**

![Google Cloud - reCAPTCHA](/assets/img/api/reCAPTCHA/dev/005.png)

6. Na tela de **criação da chave** digite as *informações conforme descritas abaixo*:
   1. **Nome de exibição:** portal-web
   2. **Escolher tipo de plataforma:** site

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/018.png)

7. **Lista de domínios**, cadastre os **domínios relacionados abaixo**:
   1. portal-web.ipe-policiacivil.sp.gov.br
   2. localhost

> **Atenção!** - *O domínio localhost* só deve ser **cadastrado em ambientes de desenvolvimento**

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/019.png)

8. Em **tipo de desafio**, marque a opção:
   1. **Usar desafio de caixa de seleção**
      1.  **Dificuldade média (equilibrio entre segurança e nível de dificuldade)**
   2.  Clique "Criar chave"

![Google Cloud - Create Key reCAPTCHA](/assets/img/api/reCAPTCHA/dev/020.png)

9. A chave deverá ser enviada para o arquiteto responsável pela configuração do aplicativo. 

![Google Cloud - ID reCAPTCHA](/assets/img/api/reCAPTCHA/dev/021.png)
