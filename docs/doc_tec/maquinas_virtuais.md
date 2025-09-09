# Sobre

**Documentação** das **instalações e configurações** de todas as maquinas virtuais no **IBM Cloud** e **Google Cloud** para os ambientes de **desenvolvimento, homologação e produção**

# Tabela de Conteúdo
<!-- no toc -->
- [Sobre](#sobre)
- [Tabela de Conteúdo](#tabela-de-conteúdo)
    - [GC05009160005](#gc05009160005)
  - [PostFix](#postfix)
    - [Recursos das Instâncias](#recursos-das-instâncias)
    - [GC05009160023: Desenvolvimento](#gc05009160023-desenvolvimento)
    - [GC05009160025: Homologação](#gc05009160025-homologação)


### GC05009160005

**Instância** para utilização **análise de Áudio, análise de Vídeo e generative IA,** utilizado pelo **time de Oitivas** e criado *na data de 15/jan/2024*, para o **ambiente de desenvovlimento.** Abaixo é descrito todo o procedimento para criação e validação da Máquina Virtual. 

#### 1. Recursos das Instâncias

Detalhamento da **Instância** provisionada

Name              | Machine Type | Architecture | VCPU        |GPU's            | Memory     | SubNetwork                | Internal IP     | Ambiente            |
----------------- | -------------| ------------ | ----------- |-----------------| ---------- | ------------------------- | -----------     | ------------------- |
**GC05009160005** | **custom**   | **x86/64**   | **12 vCPU** |**2 x NVIDIA T4**| **32 GB**  | **vpc-gcp-dipol-k8s-dev** | **10.153.8.18** | **Desenvolvimento** |

#### 2. Seleção de Projeto
No **Console do Google Cloud**, selecione o **projeto desejado**:

![Gcloud Panel Project](/assets/img/maquinas-virtuais/dev/GC05009160005/google_cloud_select_project.png)

#### 3. Compute Engine 

No **menu Gcloud**, selecione **Compute Engine** e depois **VM Instances**.

![Gcloud Compute Engine Instances](/assets/img/maquinas-virtuais/dev/GC05009160005/google_cloud_menu_compute_engine_instances.png)

#### 4. Create Instances 

Na tela **VM Instances** podemos verificar todas as **VM  provisionadas** e seus **status de atividade**, clique no botão **CREATE INSTANCES** para criar a nova VM como desejado.

![Gcloud Create instances](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_create_instances.png)

#### 5. Create Instances: Name / Regions

Siga os **padrões** conforme **informação** abaixo:

Name              | Region                 | Zone                       |
----------------- | -----------------------| -------------------------- |
**GC05009160005** | **southamerica-east1** | **southamerica-east1-c**   | 

![Gcloud Create Instances config](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_create_instances_configure.png)

#### 6. Create Instances: Machine Type

Determine a configuração de máquina conforme solicitado:

Series  | Machine Type    |
------- | --------------- |
**E2**  | **2 vCPU, 4GB** |

![Gcloud Configure Machine](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_create_instances_configure_2.png)

#### 7. Create Instances: Boot disk

No tópico **Boot disk**, clique no botão **CHANGE** e selecione **Sistema Operacional**, **Versão** e **Tamanho de Disco**, conforme desejado. 

Operation System  | Version             | Architecture | Disk Size    |
----------------- | ------------------- | ------------ | ------------ |
**UBUNTU**        | **Ubuntu 22.04LTS** | **x86/64**   | **100GB**    |

![Gcloud Configure Machine Boot Disk](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_create_instances_configure_3.png)

#### 8. Create Instances: API access

Em **Identity and API access**, selecione **Compute Engine default service account** e marque **Allow full access to all Cloud APIs**, assim como demonstrado na imagem:

![Gcloud Configure Machine API Access](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_create_instances_configure_4.png)

#### 9. Create Instances: Network

Por fim, em **Advanced options | Network**, percorra até **Network interfaces** e em **Network interface is permanent** selecione a **subrede que a VM pertencerá**, verifique antes de **configurar**, para que seja selecionado a **subrede correta.** Em **External IP address** marque como **None** se não for necessário acesso externo.

![Gcloud Configure Machine Network](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_create_instances_configure_5.png)

#### 10. Instances Details

Percorra para o fim do formulário de criação de VM e clique em **CRIAR**. O **painel do google cloud** retornará para a **lista de instâncias** e quando sua instância estiver pronto **aparecerá conforme imagem abaixo:**

![Gcloud List Instances](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_create_instances_configure_6.png)

#### 11. Access Instances 

Acesse a **máquina remota** e execute os **comandos abaixo**:
```bash
gcloud compute instances list --sort-by NAME
gcloud compute ssh --zone "southamerica-east1-c" "gc05009160005" --project "dipol-sist-invest-dev" --internal-ip
```
![Gcloud SSH Instances](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_access_instances.png)

#### 12. Add Disk: hdd001

Adicionado disco **hdd001** para armazenamento de dados

![ADD Disk hdd001](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_add_disk_hdd001.png)

#### 13. Install GPU Drivers

* Procedimentos para instalação:
  * Seguindo a documentação Oficial conforme a Google Cloud sugere:
    * [GCP Instalar os drivers da GPU](https://cloud.google.com/compute/docs/gpus/install-drivers-gpu?hl=pt-br)
    * [CUDA Toolkit 12.3 Update 2 Downloads](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local)

![Install GPU Drivers](/assets/img/maquinas-virtuais/dev/GC05009160005/GC05009160005_install_gpu_drivers.png)

<br>

## PostFix

**Agente** de  **transfêrencia e recebimento** que **roteia as mensagens enviadas** pelo **cliente** via **protocolo SMTP** (Simple Mail Transfer Protocol).
**Instância** criada e configurada para o **ambiente de desenvolvimento**, **ambiente de Homologação** e **ambiente de Produção **, abaixo é descrito todo o procedimento para criação e validação das Máquinas Virtuais.

### Recursos das Instâncias

Detalhamento da **Instância** provisionada

Name              | Machine Type | Architecture | VCPU         |GPU's            | Memory    | SubNetwork                | Internal IP      | Ambiente            |
----------------- | -------------| ------------ | ------------ |-----------------| --------- | ------------------------- | -----------      | ------------------- |
**GC05009160023** | **e2-medium**| **x86/64**   | **1-2 vCPU** |   **N/A**       | **4 GB**  | **vpc-gcp-dipol-k8s-dev** | **10.153.8.18**  | **Desenvolvimento** |
**gc50009170025** | **e2-medium**| **x86/64**   | **1-2 vCPU** |   **N/A**       | **4 GB**  | **vpc-gcp-dipol-k8s-hom** | **10.153.9.13**  | **Homologação**     |
**gc50009170026** | **e2-medium**| **x86/64**   | **1-2 vCPU** |   **N/A**       | **4 GB**  | **vpc-gcp-dipol-k8s-prod** | **10.153.9.13** | **Produção**        |

### GC05009160023: Desenvolvimento

Instância **provisionada e configurada** na data de **set. 30, 2022, 2:58:28 PM UTC-03:00**

#### 1. Seleção de Projeto
No **Console do Google Cloud**, selecione o **projeto desejado**:

![Gcloud Panel Project](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_select_project.png)

#### 2. Compute Engine 

No **menu Gcloud**, selecione **Compute Engine** e depois **VM Instances**.

![Gcloud Compute Engine Instances](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_menu_compute_engine_instances.png)

#### 3. Create Instances 

Na tela **VM Instances** podemos verificar todas as **VM  provisionadas** e seus **status de atividade**, clique no botão **CREATE INSTANCES** para criar a nova VM como desejado.

![Gcloud Create instances](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_create_instances.png)

#### 4. Create Instances: Name / Regions

Siga os **padrões** conforme **informação** abaixo:

Name              | Region                 | Zone                       |
----------------- | -----------------------| -------------------------- |
**GC05009160023** | **southamerica-east1** | **southamerica-east1-a**   | 

![Gcloud Create Instances config](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_create_instances_configure.png)

#### 5. Create Instances: Machine Type

Determine a configuração de máquina conforme solicitado:

Series  | Machine Type    |
------- | --------------- |
**E2**  | **2 vCPU, 4GB** |

![Gcloud Configure Machine](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_machine_configuration.png)

#### 6. Create Instances: Boot disk

No tópico **Boot disk**, clique no botão **CHANGE** e selecione **Sistema Operacional**, **Versão** e **Tamanho de Disco**, conforme desejado. 

Operation System  | Version             | Architecture | Disk Size    |
----------------- | ------------------- | ------------ | ------------ |
**UBUNTU**        | **Ubuntu 22.04LTS** | **x86/64**   | **20GB**     |

![Gcloud Configure Machine Boot Disk](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_machine_configuration_boot_disk.png)

#### 7. Create Instances: API access

Em **Identity and API access**, selecione **Compute Engine default service account** e marque **Allow full access to all Cloud APIs**, assim como demonstrado na imagem:

![Gcloud Configure Machine API Access](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_machine_api_access.png)

#### 8. Create Instances: Network

Por fim, em **Advanced options | Network**, percorra até **Network interfaces** e em **Network interface is permanent** selecione a **subrede que a VM pertencerá**, verifique antes de **configurar**, para que seja selecionado a **subrede correta.** Em **External IP address** marque como **None** se não for necessário acesso externo.

![Gcloud Configure Machine Network](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_machine_network_configure.png)

#### 9. Instances Details

Percorra para o fim do formulário de criação de VM e clique em **CRIAR**. O **painel do google cloud** retornará para a **lista de instâncias** e quando sua instância estiver pronto **aparecerá conforme imagem abaixo:**

![Gcloud List Instances](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_instances.png)

#### 10. Access Instances 

Acesse a **máquina remota** e execute os **comandos abaixo**:

        gcloud compute instances list
        gcloud config set compute/zone southamerica-east1-a
        gcloud compute ssh gc05009160023

![Gcloud SSH Instances](/assets/img/maquinas-virtuais/dev/gc05009160023/google_cloud_ssh_instances.png)

#### 11. Install Postfix 

Instale os **pacotes do postfix** e **demais pacotes** necessários, digite:

        sudo apt-get install -y postfix libsasl2-modules mailutils

![Gcloud Install postfix](/assets/img/maquinas-virtuais/dev/gc05009160023/install_postfix.png)

#### 12. Configure Postfix 

**Alterando as configurações do Postfix** no **main.cf**, acesse: 

        vim /etc/postfix/main.cf

![PostFix edit main](/assets/img/maquinas-virtuais/dev/gc05009160023/postfix_edit_main.png)

**Altere para os dados** abaixo, conforme imagem:

        mydestination = $myhostname, mail-dev.ipe-policiacivil.sp.gov.br, gc05009160023.southamerica-east1-a.c.dipol-sist-invest-dev.internal, localhost.southamerica-east1-a.c.dipol-sist-invest-dev.internal, , localhost, ipe-policiacivil.sp.gov.br
        mailbox_command = procmail -a "$EXTENSION"
        mailbox_size_limit = 0
        recipient_delimiter = +
        inet_interfaces = all
        inet_protocols = all
        smtp_sasl_auth_enable = yes
        smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
        smtp_sasl_security_options = noanonymous
        smtp_sasl_tls_security_options = noanonymous
        smtp_tls_security_level = encrypt
        header_size_limit = 4096000
        relayhost = [smtp.sendgrid.net]:587
        mynetworks = 127.0.0.1/32, 10.153.8.0/24, 10.88.0.0/14
        relay_domains =


![PostFix edit main II](/assets/img/maquinas-virtuais/dev/gc05009160023/postfix_edit_main_II.png)

#### 13. Configure Postfix: Permissions

 **Adicione as permissões** e **credenciais** conforme descrição abaixo:

        cat > /etc/postfix/sasl_passwd<<EOF
        [smtp.sendgrid.net]:587 apikey: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
        EOF
        chmod 600 /etc/postfix/sasl_passwd
        postmap /etc/postfix/sasl_passwd
        systemctl enable postfix
        systemctl restart postfix

#### 14. Validation Postfix  

Execute **teste para validação** digite:

        echo "Sendgrid and postfix" | mail -r no-reply@ipe-policiacivil.sp.gov.br -s "teste - sendgrid" tborges@magnasistemas.com.br, alisboa@magnasistemas.com.br

<br>

### GC05009160025: Homologação

Instância **provisionada e configurada** na data de **set. 30, 2022, 4:11:09 PM UTC-03:00**

#### 1. Seleção de Projeto
 No **Console do Google Cloud**, selecione o **projeto desejado**:

![Gcloud Panel Project](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_select_project.png)

#### 2. Compute Engine
No **menu Gcloud**, selecione **Compute Engine** e depois **VM Instances**.

![Gcloud Compute Engine Instances](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_menu_compute_engine_instances.png)

#### 3. Create Instances 
Na tela **VM Instances** podemos verificar todas as **VM  provisionadas** e seus **status de atividade**, clique no botão **CREATE INSTANCES** para criar a nova VM como desejado.

![Gcloud Create instances](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_create_instances.png)

#### 4. Create Instances: Name / Regions
Siga os **padrões** conforme **informação** abaixo:

Name              | Region                 | Zone                       |
----------------- | -----------------------| -------------------------- |
**GC50009170025** | **southamerica-east1** | **southamerica-east1-a**   | 


![Gcloud Create Instances config](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_create_instances_configure.png)

#### 5. Create Instances: Machine Type
Determine a configuração de máquina conforme solicitado:

Series  | Machine Type    |
------- | --------------- |
**E2**  | **2 vCPU, 4GB** |

![Gcloud Configure Machine](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_machine_configuration.png)

#### 7. Create Instances: Boot disk
No tópico **Boot disk**, clique no botão **CHANGE** e selecione **Sistema Operacional**, **Versão** e **Tamanho de Disco**, conforme desejado. 

Operation System  | Version             | Architecture | Disk Size    |
----------------- | ------------------- | ------------ | ------------ |
**UBUNTU**        | **Ubuntu 18.04LTS** | **x86/64**   | **20GB**     |

![Gcloud Configure Machine Boot Disk](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_machine_configuration_boot_disk.png)

#### 8. Create Instances: API access
Em **Identity and API access**, selecione **Compute Engine default service account** e marque **Allow full access to all Cloud APIs**, assim como demonstrado na imagem:

![Gcloud Configure Machine API Access](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_machine_api_access.png)

#### 9. Create Instances: Network 
Por fim, em **Advanced options | Network**, percorra até **Network interfaces** e em **Network interface is permanent** selecione a **subrede que a VM pertencerá**, verifique antes de **configurar**, para que seja selecionado a **subrede correta.** Em **External IP address** marque como **None** se não for necessário acesso externo.

![Gcloud Configure Machine Network](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_machine_network_configure.png)

#### 10. Instance Details
Percorra para o fim do formulário de criação de VM e clique em **CRIAR**. O **painel do google cloud** retornará para a **lista de instâncias** e quando sua instância estiver pronto **aparecerá conforme imagem abaixo:**

![Gcloud List Instances](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_instances.png)

#### 11. Access Instances
Acesse a **máquina remota** e execute os **comandos abaixo**:

        gcloud compute instances list
        gcloud config set compute/zone southamerica-east1-a
        gcloud compute ssh gc50009170025

![Gcloud SSH Instances](/assets/img/maquinas-virtuais/hom/gc50009170025/google_cloud_ssh_instances.png)

#### 12. Install Postfix
Instale os **pacotes do postfix** e **demais pacotes** necessários, digite:

        sudo apt-get install -y postfix libsasl2-modules mailutils

![Gcloud Install postfix](/assets/img/maquinas-virtuais/hom/gc50009170025/install_postfix.png)

#### 13. Configure Postfix 
**Alterando as configurações do Postfix** no **main.cf**, acesse: 

        vim /etc/postfix/main.cf

![PostFix edit main](/assets/img/maquinas-virtuais/hom/gc50009170025/postfix_edit_main.png)

**Altere para os dados** abaixo, conforme imagem:

        mydestination = $myhostname, mail-hom.ipe-policiacivil.sp.gov.br, gc50009170025.southamerica-east1-a.c.dipol-sist-invest-hom.internal, localhost.southamerica-east1-a.c.dipol-sist-invest-hom.internal, localhost, ipe-policiacivil.sp.gov.br
        smtp_sasl_auth_enable = yes
        smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
        smtp_sasl_security_options = noanonymous
        smtp_sasl_tls_security_options = noanonymous
        smtp_tls_security_level = encrypt
        header_size_limit = 4096000
        relayhost = [smtp.sendgrid.net]:587
        mynetworks = 127.0.0.1/32, 10.153.9.0/24, 10.164.0.0/14
        relay_domains =

![PostFix edit main II](/assets/img/maquinas-virtuais/hom/gc50009170025/postfix_edit_main_II.png)

#### 14. Configure Postfix: Permissions
**Adicione as permissões** e **credenciais** conforme descrição abaixo:

        cat > /etc/postfix/sasl_passwd<<EOF
        [smtp.sendgrid.net]:587 apikey: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
        EOF
        chmod 600 /etc/postfix/sasl_passwd
        postmap /etc/postfix/sasl_passwd
        systemctl enable postfix
        systemctl restart postfix

#### 15. Validation Postfix
Execute **teste para validação** digite:

        echo "Sendgrid and postfix" | mail -r no-reply@ipe-policiacivil.sp.gov.br -s "teste - sendgrid" tborges@magnasistemas.com.br, alisboa@magnasistemas.com.br

<br>