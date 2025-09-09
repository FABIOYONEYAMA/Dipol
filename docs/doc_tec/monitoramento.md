## Sobre

Nesse documento é abordado tudo sobre o monitoramento dos serviços provisionados nos datacenters [IBM Cloud](https://cloud.ibm.com/), [Google Cloud](https://cloud.google.com/?hl=pt-br) e PRODESP, desde as ferramentas utilizadas até a configuração de cada serviço mantido e consumido pelos usuários da [Polícia Civil do Estado de São Paulo](https://www.policiacivil.sp.gov.br/).

Para acessar as ferramentas de monitoramento é necessário atender todos os pré-requisitos descritos abaixo:

* [VPN]() configurada, permitindo acessar os serviços da rede privada da Polícia Civil.
* [IBM Cloud Credentials](https://cloud.ibm.com/docs/account?topic=account-account-getting-started) gerenciado pela equipe PRODESP.
* [IBM Cloud CLI](https://cloud.ibm.com/docs/cli) instalado e devidamente configurado.
* [Google Cloud CLI](https://cloud.google.com/sdk/docs/install?hl=pt-br#linux) instalado e devidamente configurado.

---

## Monitoramento

Serviços de Monitoramento em execução:

- **Produção**
  - [Dynatrace SPJ | Investigação | Novo Inquérito](https://gerenciamentoapm.prodesp.sp.gov.br/e/9aaf0a6a-09f4-460b-860e-72acedadd4d4/#dashboard;gtf=-2h;gf=5355219715125557752;id=21558fd2-c172-42d0-a4cd-a80b88b1693b) - Monitora todos os serviços e aplicações das Aplicações do SPJ, Investigação e Novo Inquérito
  - [Dynatrace Legado](https://gerenciamentoapm.prodesp.sp.gov.br/e/9aaf0a6a-09f4-460b-860e-72acedadd4d4/#dashboard;gtf=-2h;gf=5355219715125557752;id=59529f08-e12d-418d-9bd8-6282abc5d52d) - Monitora todos os serviços e aplicações das Aplicações do legado.
  - [Google cloud Status](https://status.cloud.google.com/regional/americas) - Exibe em tempo real a saúde de todos os serviços na nuvem Google.
  - [Google Cloud Monitoring](https://console.cloud.google.com/monitoring;duration=PT1H?hl=pt-br&project=dipol-sist-invest-prod) - Monitora todos os componentes provisionados na nuvem
  - [Google Cloud Logging](https://console.cloud.google.com/logs/query;cursorTimestamp=2024-09-06T18:06:57.005520Z;duration=PT1H?hl=pt-br&project=dipol-sist-invest-prod) - Permite visualizar o log de todos os componentes em execução na nuvem
  - [IBM Cloud Status](https://cloud.ibm.com/status) - Exibe em tempo real a saúde de todos os serviços da nuvem IBM
  - [IBM Cloud Monitoring](https://cloud.ibm.com/observe/embedded-view/monitoring/144ca74d-fd87-4ba6-a9c4-9bd0d3caeaab) - Monitora todos os componentes provisionados na nuvem
  - [IBM Cloud Logging](https://cloud.ibm.com/observe/embedded-view/logging/85cd5aa7-802c-4786-8271-85da0861185e) - Permite visualizar o log de todos os componentes em execução na nuvem

## Subtópico

- [Dynatrace](https://gitlab.prodesp.sp.gov.br/ssp/dipol/business/dipol-ops/-/wikis/Home/Monitoramento/Dynatrace)
  - [Password Reset](https://gitlab.prodesp.sp.gov.br/ssp/dipol/business/dipol-ops/-/wikis/Home/Monitoramento/Dynatrace#password-reset)
  - [Selecionando Ambiente - Dev | Hom | Prod](https://gitlab.prodesp.sp.gov.br/ssp/dipol/business/dipol-ops/-/wikis/Home/Monitoramento/Dynatrace#selecionando-o-ambiente)