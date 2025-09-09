## Sobre

**Projeto** responsável por **provisionar todos os manuais técnicos** referente a **instalação e configuração** dos serviços de **Watsonx.AI Studio e Watsonx.AI Runtime**.

# Tabela de Conteúdo

- [Tabela de Conteúdo](#tabela-de-conteúdo)
  - [Watson.AI](#watsonai)
  - [Recursos da nuvem](#recursos-da-nuvem)
  - [Faturamento](#faturamento)
  - [Instâncias](#instâncias)
  - [Ambiente de Homologação](#ambiente-de-homologação)
    - [WATSON\_STUDIO-HOM](#watson_studio-hom)
      - [Criar API KEY](#criar-api-key)
      - [Criação dos projetos](#criação-dos-projetos)
    - [WATSON\_RUNTIME-HOM](#watson_runtime-hom)
  - [Ambiente de Producão](#ambiente-de-producão)
    - [WATSON\_STUDIO-PROD](#watson_studio-prod)
      - [Criar API KEY](#criar-api-key-1)
      - [Criação dos projetos](#criação-dos-projetos-1)
    - [WATSON\_RUNTIME-PROD](#watson_runtime-prod)
   
<br>

## Watson.AI

O **IBM® watsonx.ai** é um **estúdio de nível empresarial para desenvolver serviços de IA** e implementá-los nas aplicações de sua escolha. Conta com uma **coleção de APIs, ferramentas, modelos e tempos de execução** necessários para colocar em prática suas ideias e necessidades

## Recursos da nuvem

* Acelere o desenvolvimento de IA com a AutoAI
Com a **AutoAI**, iniciantes podem construir modelos sem codificação e os cientistas de dados especialistas podem acelerar a experimentação no desenvolvimento de IA. A AutoAI automatiza a preparação de dados, o desenvolvimento de modelos, a engenharia de recursos e a otimização de hiperparâmetro.

* Otimize decisões
O **Decision Optimization** simplifica a seleção e a implementação de modelos prescritivos. Escreva código em Python ou OPL ou em expressões de linguagem natural com o Assistente de Modelagem inteligente. Investigue e compare soluções para vários cenários com painéis.

* Desenvolva modelos visualmente
Com a tela gráfica do **IBM SPSS Modeler**, crie um fluxo de etapas para preparar dados e construir modelos preditivos. Arraste e solte a partir de mais de 100 nós de preparação de dados, de visualização de dados, de análise estatística, de modelagem preditiva e de analítica de texto.

* Treinamento de modelo federado
Com o **Aprendizado Federado**, treine um modelo em um conjunto de origens de dados ao mesmo tempo que mantém a segurança de dados. Cada parte participante da federação treina o modelo de aprendizado de máquina comum sem mover ou compartilhar dados. Os resultados do treinamento são fundidos em um modelo mais preciso.

## Faturamento

**A compra do **Watsonx.AI, será** incluída em sua declaração de faturamento consolidada mensal**. Seu investimento se **baseia em seu compromisso de compra em nuvem**.

## Instâncias
Abaixo é informada as **instâncias dos ambientes** de **DESENVOLVIMENTO, HOMOLOGAÇÃO e PRODUÇÃO**.

Name                | Type                  | Version      | Environment         | Region                 |
------------------- | --------------------- | ------------ | ------------------- | ---------------------- |
WATSON_STUDIO-HOM   | Watsonx.AI Studio     |  N/A         | Homologação         | Frankfurt (eu-de)      |
WATSON_RUNTIME_HOM  | Watson.AI Runtime     |  N/A         | Homologação         | Frankfurt (eu-de)      | 
WATSON_STUDIO-PROD  | Watsonx.AI Studio     |  N/A         | Produção            | Frankfurt (eu-de)      |
WATSON_RUNTIME_PROD | Watson.AI Runtime     |  N/A         | Produção            | Frankfurt (eu-de)      |

## Ambiente de Homologação

**Instâncias** provisionadas no **ambiente de Homologação** com o nome de implementação **WATSON_STUDIO-HOM** e **WATSON_RUNTIME-HOM**. 

### WATSON_STUDIO-HOM

1. Acesse a **página de login** do ***IBMCloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**

![IBM CLOUD Login](/assets/img/abertura-chamado-cloud/001_abrt_chamado.png)

2. Digite seu **usário** e **senha** ***IBMid***

![IBM CLOUD IBMid](/assets/img/abertura-chamado-cloud/002_abrt_chamado.png)

3. Na console do **IBM Cloud**, acesse o menu **Catálogo** na barra de menus do console

![IBM CLOUD IBMid](/assets/img/watson-ai/hom/001-watson_ai.png)

4. Na caixa de pesquisa e catálogo  digite e selecione conforme imagem:
    * watsonx.ai

![IBM CLOUD catalog](/assets/img/watson-ai/hom/002-watson_ai.png)

5. Configure a **Localização e o Plano**
    * **Selecionar uma localização:** Frankfurt (eu-de)
    * **Selecionar um plano de precificação:** Profissional

![IBM CLOUD provisioning](/assets/img/watson-ai/hom/003-watson_ai.png)

6. Configure **seu recurso**
    * **Nome do Serviço:** WATSON_STUDIO-HOM
    * **Selecione o Grupo de Recurso:** gr-0500007-hom
    * **Tags:** hom
    * **Li e concordo com os contratos de licença a seguir:** FLAG
    * **Criar:** Confirmar

![IBM CLOUD provisioning](/assets/img/watson-ai/hom/004-watson_ai.png)

#### Criar API KEY

1. Acesso gerenciamento IAM
![IBM CLOUD manage_iam](/assets/img/watson-ai/hom/008-watson_ai.png)

3. Acessar Menu de Gerenciamento de Acesso ao IAM
![IBM CLOUD manage_iam](/assets/img/watson-ai/hom/009-watson_ai.png)

4. Criar ID de Serviço
![IBM CLOUD manage_iam](/assets/img/watson-ai/hom/010-watson_ai.png)

5. Configuração de ID de Serviço (Chaves de API)
![IBM CLOUD manage_iam](/assets/img/watson-ai/hom/011-watson_ai.png)

#### Criação dos projetos

1. Acesso ao Watson Studio para criação dos projetos

![IBM CLOUD projetcts](/assets/img/watson-ai/hom/012-watson_ai.png)

2. Acesso ao Painel do Watsonx.AI Studio

![IBM CLOUD projetcts](/assets/img/watson-ai/hom/013-watson_ai.png)

3. Acesse o Menu Crie um projeto

![IBM CLOUD projetcts](/assets/img/watson-ai/hom/014-watson_ai.png)

4. Crie o projeto - Projeto Integracao-Documentos
![IBM CLOUD projetcts](/assets/img/watson-ai/hom/015-watson_ai.png)

5. Vincular o Watsonx.AI Runtime
![IBM CLOUD projetcts](/assets/img/watson-ai/prod/013-watson_ai.png)

6. Adicione a Chave de serviço no controle de acesso
![IBM CLOUD projetcts](/assets/img/watson-ai/prod/014-watson_ai.png)

### WATSON_RUNTIME-HOM

1. Acesse a **página de login** do ***IBMCloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**

![IBM CLOUD Login](/assets/img/abertura-chamado-cloud/001_abrt_chamado.png)

2. Digite seu **usário** e **senha** ***IBMid***

![IBM CLOUD IBMid](/assets/img/abertura-chamado-cloud/002_abrt_chamado.png)

3. Na console do **IBM Cloud**, acesse o menu **Catálogo** na barra de menus do console

![IBM CLOUD IBMid](/assets/img/watson-ai/hom/001-watson_ai.png)

4. Na caixa de pesquisa e catálogo  digite e selecione conforme imagem:
    * watsonx.ai Runtime

![IBM CLOUD IBMid](/assets/img/watson-ai/hom/005-watson_ai.png)

5. Configure a **Localização e o Plano**
    * **Selecionar uma localização:** Frankfurt (eu-de)
    * **Selecionar um plano de precificação:** Profissional

![IBM CLOUD IBMid](/assets/img/watson-ai/hom/006-watson_ai.png)

6. Configure **seu recurso**
    * **Nome do Serviço:** WATSON_RUNTIME-HOM
    * **Selecione o Grupo de Recurso:** gr-0500007-hom
    * **Tags:** hom
    * **Li e concordo com os contratos de licença a seguir:** FLAG
    * **Criar:** Confirmar
    * **Service endpoints:** Both

![IBM CLOUD provisioning](/assets/img/watson-ai/hom/007-watson_ai.png)

## Ambiente de Producão

**Instâncias** provisionadas no **ambiente de Produção** com o nome de implementação **WATSON_STUDIO-PROD** e **WATSON_RUNTIME-PROD**

### WATSON_STUDIO-PROD

1. Acesse a **página de login** do ***IBMCloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**

![IBM CLOUD Login](/assets/img/abertura-chamado-cloud/001_abrt_chamado.png)

2. Digite seu **usário** e **senha** ***IBMid***

![IBM CLOUD IBMid](/assets/img/abertura-chamado-cloud/002_abrt_chamado.png)

3. Na console do **IBM Cloud**, acesse o menu **Catálogo** na barra de menus do console

![IBM CLOUD IBMid](/assets/img/watson-ai/prod/001-watson_ai.png)

4. Na caixa de pesquisa e catálogo  digite e selecione conforme imagem:
    * watsonx.ai

![IBM CLOUD catalog](/assets/img/watson-ai/prod/002-watson_ai.png)

5. Configure a **Localização e o Plano**
    * **Selecionar uma localização:** Frankfurt (eu-de)
    * **Selecionar um plano de precificação:** Profissional

![IBM CLOUD provisioning](/assets/img/watson-ai/prod/003-watson_ai.png)

6. Configure **seu recurso**
    * **Nome do Serviço:** WATSON_STUDIO-PROD
    * **Selecione o Grupo de Recurso:** gr-0500007-prod
    * **Tags:** prod
    * **Li e concordo com os contratos de licença a seguir:** FLAG
    * **Criar:** Confirmar

![IBM CLOUD provisioning](/assets/img/watson-ai/prod/004-watson_ai.png)

#### Criar API KEY

1. Acesso gerenciamento IAM
![IBM CLOUD manage_iam](/assets/img/watson-ai/prod/020-watson_ai.png)

3. Acessar Menu de Gerenciamento de Acesso ao IAM
![IBM CLOUD manage_iam](/assets/img/watson-ai/prod/021-watson_ai.png)

4. Criar ID de Serviço
![IBM CLOUD manage_iam](/assets/img/watson-ai/prod/022-watson_ai.png)

5. Configuração de ID de Serviço
![IBM CLOUD manage_iam](/assets/img/watson-ai/prod/023-watson_ai.png)

#### Criação dos projetos

1. Acesso ao Watson Studio para criação dos projetos

![IBM CLOUD projetcts](/assets/img/watson-ai/prod/009-watson_ai.png)

2. Acesso ao Painel do Watsonx.AI Studio

![IBM CLOUD projetcts](/assets/img/watson-ai/prod/010-watson_ai.png)

3. Acesse o Menu Crie um projeto

![IBM CLOUD projetcts](/assets/img/watson-ai/prod/011-watson_ai.png)

4. Crie o projeto - Projeto Integracao-Documentos
![IBM CLOUD projetcts](/assets/img/watson-ai/prod/012-watson_ai.png)

5. Vincular o Watsonx.AI Runtime
![IBM CLOUD projetcts](/assets/img/watson-ai/prod/013-watson_ai.png)

6. Adicione a Chave de serviço no controle de acesso
![IBM CLOUD projetcts](/assets/img/watson-ai/prod/019-watson_ai.png)

### WATSON_RUNTIME-PROD

**Instância** provisionado no **ambiente de Produção** com o nome de implementação **WATSON_STUDIO-PROD** e **WATSON_RUNTIME-PROD**

1. Acesse a **página de login** do ***IBMCloud*** em: **[IBM Cloud Login](https://cloud.ibm.com/login)**

![IBM CLOUD Login](/assets/img/abertura-chamado-cloud/001_abrt_chamado.png)

2. Digite seu **usário** e **senha** ***IBMid***

![IBM CLOUD IBMid](/assets/img/abertura-chamado-cloud/002_abrt_chamado.png)

3. Na console do **IBM Cloud**, acesse o menu **Catálogo** na barra de menus do console

![IBM CLOUD IBMid](/assets/img/watson-ai/prod/001-watson_ai.png)

4. Na caixa de pesquisa e catálogo  digite e selecione conforme imagem:
    * watsonx.ai

![IBM CLOUD IBMid](/assets/img/watson-ai/prod/005-watson_ai.png)

5. Configure a **Localização e o Plano**
    * **Selecionar uma localização:** Frankfurt (eu-de)
    * **Selecionar um plano de precificação:** Profissional

![IBM CLOUD IBMid](/assets/img/watson-ai/prod/006-watson_ai.png)

6. Configure **seu recurso**
    * **Nome do Serviço:** WATSON_STUDIO-PROD
    * **Selecione o Grupo de Recurso:** gr-0500007-prod
    * **Tags:** prod
    * **Li e concordo com os contratos de licença a seguir:** FLAG
    * **Criar:** Confirmar
    * **Service endpoints:** Both

![IBM CLOUD provisioning](/assets/img/watson-ai/prod/007-watson_ai.png)
![IBM CLOUD provisioning](/assets/img/watson-ai/prod/008-watson_ai.png)

