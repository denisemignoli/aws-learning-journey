Status: #developing

Tags:  #aws/dominio3 #aws/computacao #nuvem/iaas #financas/spot #storage/ebs #infra/elasticidade

---

# Amazon EC2: Elastic Compute Cloud

O Amazon EC2 (Elastic Compute Cloud) é um serviço web que fornece capacidade computacional segura e redimensionável na nuvem. Ele foi projetado para facilitar a computação em escala de web para os desenvolvedores. Em termos simples, o EC2 permite que você **alugue servidores virtuais (chamados de instâncias)** para executar suas aplicações.

O EC2 é um serviço **IaaS (Infrastructure as a Service)**, o que significa que você tem controle total sobre o sistema operacional e a configuração da sua instância.

## Índice

1. [Visão Geral: Configurando uma Instância EC2](#1-opções-de-dimensionamento-e-configuração-do-ec2)
2. [Conceitos Fundamentais do EC2](#2-conceitos-fundamentais-do-ec2)
    - [AMI (Amazon Machine Image)](#ami-amazon-machine-image)
    - [Tipos de Instância (Instance Types)](#tipos-de-inst%C3%A2ncia-instance-types)
3. [Modelos de Compra de Instâncias (Pricing Models)](#3-modelos-de-compra-de-inst%C3%A2ncias-pricing-models)
    - [On-Demand (Sob Demanda)](#on-demand-sob-demanda)
    - [Savings Plans (Planos de Economia)](#savings-plans-planos-de-economia)
    - [Reserved Instances (Instâncias Reservadas)](#reserved-instances-inst%C3%A2ncias-reservadas)
    - [Spot Instances (Instâncias Spot)](#spot-instances-inst%C3%A2ncias-spot)
    - [Dedicated Hosts (Hosts Dedicados)](#dedicated-hosts-hosts-dedicados)
4. [Armazenamento para Instâncias EC2](#4-armazenamento-para-inst%C3%A2ncias-ec2)
    - [EBS (Elastic Block Store)](#ebs-elastic-block-store)
    - [EFS (Elastic File System)](#efs-elastic-file-system)
    - [Instance Store](#instance-store)
5. [Escalabilidade e Disponibilidade](#5-escalabilidade-e-disponibilidade)
    - [Auto Scaling Groups](#auto-scaling-groups)
    - [Elastic Load Balancing (ELB)](#elastic-load-balancing-elb)

## 1.  Opções de Dimensionamento e Configuração do EC2

Ao criar uma instância EC2, você precisa definir uma série de opções que determinam o tamanho, a performance e o comportamento do seu servidor virtual. As principais decisões são:

- **Sistema Operacional (OS):**
    - Qual sistema sua aplicação usará? As opções incluem **Linux**, **Windows** ou **macOS**.
    - _Isso é definido pela **AMI (Amazon Machine Image)**_.
- **Poder de Computação e Cores (CPU):**
    
    - Quanta capacidade de processamento é necessária?
    - _Isso é definido pelo **Tipo de Instância (Instance Type)**_.
- **Memória de Acesso Aleatório (RAM):**
    
    - Quanta memória sua aplicação precisa para rodar eficientemente?
    - _Isso também é definido pelo **Tipo de Instância (Instance Type)**_.
- **Espaço de Armazenamento (Storage):**
    
    - **Armazenamento de Rede (Network-attached):** Armazenamento persistente e flexível.
        - **EBS (Elastic Block Store):** Para um único EC2.
        - **EFS (Elastic File System):** Para múltiplos EC2s.
    - **Armazenamento de Hardware (Hardware):** Armazenamento local, fisicamente conectado à máquina host para performance máxima, mas não persistente.
        - **EC2 Instance Store**.
- **Placa de Rede (Network Card):**
    
    - Qual a velocidade da rede?
    - A instância precisa de um **Endereço de IP Público** para ser acessada pela internet?
- **Regras de Firewall (Firewall Rules):**
    
    - Quais portas e protocolos de rede serão permitidos?
    - _Isso é controlado pelo **Security Group**_.
- **Script de Inicialização (Bootstrap Script):**
    
    - Você precisa executar comandos ou instalar softwares automaticamente na primeira vez que a instância é iniciada?
    - _Isso é feito usando o campo **EC2 User Data**_.

## 2. Conceitos Fundamentais do EC2

### AMI (Amazon Machine Image)

- **O que é?** Uma AMI é um **template** que contém a configuração de software (sistema operacional, servidor de aplicação e aplicações) necessária para iniciar sua instância. É como uma "imagem de disco" ou um "molde" para suas instâncias.
- **O que ela define?**
    - O Sistema Operacional (ex: Linux, Windows Server).
    - O software pré-instalado.
    - A configuração de armazenamento inicial.
- **Tipos de AMI:** Você pode usar AMIs fornecidas pela AWS, AMIs da comunidade, AMIs do AWS Marketplace (com software comercial) ou **criar suas próprias AMIs personalizadas** a partir de uma instância que você já configurou.

### Tipos de Instância (Instance Types)

- **O que são?** Os tipos de instância são combinações variadas de CPU, memória, armazenamento e capacidade de rede. Cada tipo de instância pertence a uma "família" otimizada para um caso de uso específico.
- **Como entender o nome?** Um nome como `t2.micro` pode ser quebrado em:
    - `t`: Família da instância (neste caso, "burstable", de uso geral).
    - `2`: Geração da instância.
    - `micro`: Tamanho da instância dentro da família.
- **Principais Famílias (Nível Cloud Practitioner):**
    - **Uso Geral (Famílias T e M):** Bom equilíbrio entre computação, memória e rede. Ideal para servidores web, pequenos bancos de dados e ambientes de desenvolvimento.
    - **Otimizada para Computação (Família C):** Possui CPUs de alta performance. Ideal para processamento em lote, servidores de jogos e computação de alto desempenho (HPC).
    - **Otimizada para Memória (Famílias R e X):** Grande quantidade de RAM. Ideal para bancos de dados em memória, processamento de Big Data e aplicações que precisam carregar grandes datasets na memória.

## 3. Modelos de Compra de Instâncias (Pricing Models)

Entender os modelos de compra é crucial para o pilar de **Otimização de Custos**.

|Modelo de Compra|Caso de Uso Ideal|Características Principais|
|---|---|---|
|**On-Demand**|Cargas de trabalho de curto prazo, imprevisíveis e que não podem ser interrompidas.|Pague por segundo, sem compromisso. Mais flexível, porém mais caro.|
|**Savings Plans**|Cargas de trabalho com uso consistente e previsível.|Comprometa-se a gastar um valor (em $/hora) por 1 ou 3 anos para receber um grande desconto. Flexível entre famílias de instâncias e regiões.|
|**Reserved Instances**|Cargas de trabalho com estado estável e previsível (ex: um banco de dados que roda 24/7).|Comprometa-se com um tipo de instância e região específicos por 1 ou 3 anos para obter o maior desconto. Menos flexível que Savings Plans.|
|**Spot Instances**|Cargas de trabalho tolerantes a falhas, sem estado e que podem ser interrompidas.|Use a capacidade computacional não utilizada da AWS com até 90% de desconto. A AWS pode retomar a instância a qualquer momento com um aviso de 2 minutos.|
|**Dedicated Hosts**|Cenários com requisitos de conformidade rigorosos ou licenças de software "traga sua própria licença" (BYOL).|Você aluga um servidor físico inteiro para seu uso exclusivo. É o modelo mais caro.|

## 4. Armazenamento para Instâncias EC2

O armazenamento de uma instância pode ser de dois tipos principais: **persistente** (os dados sobrevivem se a instância for desligada) ou **efêmero** (os dados são perdidos).

### EBS (Elastic Block Store)

- **O que é?** Um "HD externo de rede" que você anexa à sua instância EC2.
- **Persistência:** Os dados em um volume EBS **são persistentes**. Eles sobrevivem independentemente do ciclo de vida da instância. Você pode desanexar um volume EBS de uma instância e anexá-lo a outra.
- **Característica:** Um volume EBS só pode ser anexado a **uma única instância EC2 por vez** na mesma Zona de Disponibilidade.
- **Snapshots:** Você pode criar "cópias de segurança" de seus volumes EBS, chamadas **Snapshots**, que são armazenadas de forma barata no Amazon S3.

### EFS (Elastic File System)

- **O que é?** Um sistema de arquivos de rede totalmente gerenciado, baseado em NFS (Network File System).
- **Persistência:** Os dados no EFS são persistentes.
- **Característica:** Um sistema de arquivos EFS pode ser montado e acessado por **múltiplas instâncias EC2 simultaneamente**, inclusive em diferentes Zonas de Disponibilidade. É ideal para compartilhamento de arquivos entre servidores.

### Instance Store

- **O que é?** Um armazenamento de bloco localizado fisicamente no mesmo servidor host da sua instância EC2.
- **Persistência:** Os dados no Instance Store são **efêmeros (não persistentes)**. Se a instância for **parada (stopped), hibernada ou terminada**, todos os dados são perdidos.
- **Característica:** Oferece performance de I/O (leitura/escrita) extremamente alta, pois está fisicamente acoplado à máquina. Ideal para cache, buffers ou dados temporários.

## 5. Escalabilidade e Disponibilidade

### Auto Scaling Groups (ASG)

- **O que é?** Um serviço que ajusta automaticamente o número de instâncias EC2 em um grupo para atender à demanda atual.
- **Componentes:**
    - **Launch Template/Configuration:** Define o "molde" da instância a ser lançada (AMI, tipo de instância, etc.).
    - **Configuração do Grupo:** Define o número mínimo, máximo e desejado de instâncias.
    - **Políticas de Escalonamento:** Regras que definem quando adicionar ou remover instâncias (ex: "se a CPU média for > 70%, adicione uma instância").
- **Benefícios:** Garante **elasticidade** (economia de custos) e **alta disponibilidade** (se uma instância falhar, o ASG a substitui automaticamente).

### Elastic Load Balancing (ELB)

- **O que é?** Um serviço que distribui automaticamente o tráfego de entrada de aplicações por várias instâncias EC2 (ou outros destinos).
- **Função:**
    - **Alta Disponibilidade:** Se uma instância falhar, o ELB para de enviar tráfego para ela e o redireciona para as instâncias saudáveis.
    - **Escalabilidade:** Atua como um ponto de entrada único para o tráfego, que é então distribuído para o seu grupo de instâncias (geralmente um Auto Scaling Group).
- **Como funciona:** O ELB realiza "verificações de saúde" (Health Checks) para monitorar o estado das instâncias e garantir que o tráfego seja enviado apenas para as que estão operando corretamente.

