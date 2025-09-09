
# Tabela de Conteúdo

- [Tabela de Conteúdo](#tabela-de-conteúdo)
  - [Painel de controle do Kubernetes](#painel-de-controle-do-kubernetes)
    - [Sobre](#sobre)
    - [Painel de Controle Kubernetes](#painel-de-controle-kubernetes)
    - [Navegando pelos Workloads](#navegando-pelos-workloads)
    - [Navegando pelos Logs dos Workloads](#navegando-pelos-logs-dos-workloads)

## Painel de controle do Kubernetes

  * Procedimentos para acesso ao painel de controle do kubernetes, que oferece uma visão geral das aplicações em execução no cluster.

### Sobre
O Painel oferece uma visão geral das aplicações em execução no seu cluster, além de permitir a cvisualização de recursos e logs individuais do Kubernetes (como Deployments, Jobs, DaemonSets, etc.). 

O Painel também fornece informações sobre o estado dos recursos do Kubernetes em seu cluster e sobre quaisquer erros que possam ter ocorrido.

### Painel de Controle Kubernetes

1. Faça login no **IBM Cloud Console**,  acesse: [IBMCloud Console](https://cloud.ibm.com/login)

![IBM Cloud Console](/assets/img/acessos-cloud/ibmcloud_console_001.png)

2. **Conecte-se** com, seu **IBMid e Password**

![IBM Cloud Console](/assets/img/acessos-cloud/ibmcloud_console_002.png)

3. **Insira o código de verificação de seis dígitos**

![IBM Cloud Console](/assets/img/acessos-cloud/ibmcloud_console_003.png)

4. O **dashboard será apresentado** após autenticação

![IBM Cloud Console](/assets/img/acessos-cloud/ibmcloud_console_004.png)

5. Acesse o **menu de navegação** do **IBM Cloud**

![IBM Cloud Navigation Menu](/assets/img/sop/acess_cloud_iks/002.png)

6. No **menu de navegação**, clique em **Container** e depois em **Clusters**

![IBM Cloud Navigation Menu](/assets/img/sop/acess_cloud_iks/003.png)

7. Selecione o Cluster do ambiente desejado, clicano no nome do cluster

![IBM Cloud Navigation Kubernetes](/assets/img/sop/acess_cloud_iks/004.png)

8. No **painel de informações do cluster**, clique no botão **Painel do Kubernetes**

![IBM Cloud Navigation Kubernetes](/assets/img/sop/acess_cloud_iks/005.png)

9. Uma nova janela será aberta com o **painel de controle do Kubernetes**

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/006.png)


### Navegando pelos Workloads

Ao acessar o Painel do cluster, você verá a página de boas vindas, esta página contém os recursos dos workloads separados pelo Menu **Workloads**

1. Na janela do **painel de controle do Kubernetes**

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/006.png)

2. Selecione o nomespace onde o projeto está instalado. 

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/007.png)

3. Selecione o tipo de **aplicabilidade** do seu **Workload**

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/008.png)

4. Ao acessar o workload desejado, será apresentado um painel de monitoração do recurso

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/009.png)

5. Há a possibilidade de expandir mais informações do workload clicando diretamente no nome do recurso.

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/010.png)

6. Detalhes do workload, como metadata, pods status, monitor de recursos e Eventos

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/011.png)

### Navegando pelos Logs dos Workloads

Ao acessar o **Painel do cluster**, você verá a **página de boas vindas**, nesta página é **possível acessar os logs dos recursos desejados**.

1. Na janela do **painel de controle do Kubernetes**

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/006.png)

2. Selecione o nomespace onde o projeto está instalado. 

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/007.png)

3. Selecione o tipo de **aplicabilidade** do seu **Workload**

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/008.png)

4. Ao acessar o workload desejado, será apresentado um painel de monitoração do recurso

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/009.png)

5. Com o painel do workload aberto, clique no menu de  opções do workload e selecione logs

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/011.png)

6. Abaixo a tela de log do workload

![IBM Cloud Console Kubernetes](/assets/img/sop/acess_cloud_iks/012.png)




