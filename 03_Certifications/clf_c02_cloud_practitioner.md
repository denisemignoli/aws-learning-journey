# 🚀 Plano de estudos: CLF-C02

Este documento serve como meu guia mestre para a certificação CLF-C02. Ele é baseado no [guia oficial do exame](https://d1.awsstatic.com/onedam/marketing-channels/website/aws/pt_BR/certification/approved/pdfs/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf).


## 🎯 Domínios do exame e pesos

O exame é dividido em quatro domínios, cada um com um peso diferente na pontuação final. Meu progresso em cada domínio será rastreado aqui.

- [ ] **Domínio 1: Conceitos da Nuvem (24%)**
- [ ] **Domínio 2: Segurança e Conformidade (30%)**
- [ ] **Domínio 3: Tecnologia e Serviços da Nuvem (34%)**
- [ ] **Domínio 4: Cobrança, Preços e Suporte (12%)**

---

## ✅ Checklist

### Domínio 1: Conceitos da Nuvem (24%)
- [x] **1.1: Definir os benefícios da nuvem AWS.**
  - [x] [Proposta de valor da AWS](../00_AWS_Core_Concepts/aws_value_proposition.md). 
  - [x] [Benefícios da infraestrutura global (alcance, velocidade)](../00_AWS_Core_Concepts/cloud_benefits.md). 
  - [x] [Vantagens da alta disponibilidade, elasticidade e agilidade](../00_AWS_Core_Concepts/cloud_benefits.md).
  - [x] [Modelos de serviço de nuvem (IaaS, PaaS, SaaS)](../00_AWS_Core_Concepts/cloud_computing_models.md).
- [ ] **1.2: Identificar os princípios de design da nuvem AWS.**
  - [x] Conhecimento do [AWS Well-Architected Framework](../00_AWS_Core_Concepts/well_architected_framework.md).
  - [ ] Compreensão e identificação dos 6 pilares do Framework.
- [ ] **1.3: Compreender os benefícios e as estratégias de migração.**
  - [x] [Estratégias de adoção da nuvem (os "6 R's")](../00_AWS_Core_Concepts/cloud_migration_strategies.md).
  - [ ] Conhecimento do AWS Cloud Adoption Framework (CAF).
- [ ] **1.4: Compreender os conceitos dos aspectos econômicos da nuvem.**
  - [ ] Custos fixos vs. variáveis (CAPEX vs. OPEX).
  - [ ] Conceito de dimensionamento correto (*right sizing*).
  - [ ] Benefícios da automação e economia de custos.

### Domínio 2: Segurança e Conformidade (30%)
- [ ] **2.1: Compreender o modelo de responsabilidade compartilhada.**
  - [ ] [Shared Responsibility Model](../00_AWS_Core_Concepts/shared_responsibility_model.md).
  - [ ] Descrever as responsabilidades do cliente e da AWS.
- [ ] **2.2: Compreender os conceitos de segurança, governança e conformidade.**
  - [ ] Onde encontrar informações de conformidade (AWS Artifact).
  - [ ] Criptografia em trânsito e em repouso.
  - [ ] Serviços de auditoria e governança (CloudTrail, Config).
- [ ] **2.3: Identificar os recursos de gerenciamento de acesso da AWS.**
  - [ ] Conhecimento profundo de [IAM](../01_Services/IAM/README).
  - [ ] Importância de proteger a conta raiz (MFA).
  - [ ] Princípio de menor privilégio.
- [ ] **2.4: Identificar os componentes e os recursos de segurança.**
  - [ ] Serviços de segurança (AWS Shield, WAF, Inspector, GuardDuty).
  - [ ] AWS Trusted Advisor.

### Domínio 3: Tecnologia e Serviços da Nuvem (34%)
- [ ] **3.1: Definir métodos de implantação e operação na nuvem.**
  - [ ] Acesso programático (CLI, SDKs) vs. Console.
  - [ ] Infraestrutura como Código (IaC) - CloudFormation.
  - [x] [Modelos de implantação de nuvem (Cloud, Hybrid, On-Premises)](../00_AWS_Core_Concepts/cloud_deployment_models.md)
- [ ] **3.2: Definir a infraestrutura global da AWS.**
  - [x] [Relação entre regiões, zonas de disponibilidade (AZs) e locais da borda](../00_AWS_Core_Concepts/infrastructure_overview.md).
- [ ] **3.3: Identificar os serviços computacionais da AWS.**
  - [ ] Conhecimento de [EC2](../01_Services/EC2/README) e seus casos de uso.
  - [ ] Opções de contêineres (ECS, EKS).
  - [ ] Computação sem servidor (Lambda).
- [ ] **3.4: Identificar os serviços de banco de dados da AWS.**
  - [ ] Bancos de dados relacionais (RDS, Aurora) vs. NoSQL (DynamoDB).
- [ ] **3.5: Identificar os serviços de rede da AWS.**
  - [ ] Componentes da VPC (sub-redes, gateways).
  - [ ] Grupos de segurança vs. ACLs de rede.
  - [ ] Amazon Route 53.
- [ ] **3.6: Identificar os serviços de armazenamento da AWS.**
  - [ ] Conhecimento de [S3](../01_Services/S3/README) e suas classes de armazenamento.
  - [ ] Armazenamento em bloco (EBS) vs. Arquivo (EFS).
- [ ] **3.7 & 3.8: Identificar outros serviços importantes.**
  - [ ] Integração de aplicações (SQS, SNS).
  - [ ] Ferramentas de desenvolvedor (CodePipeline, CodeBuild).
  - [ ] Analytics, IA/ML, etc.

### Domínio 4: Cobrança, Preços e Suporte (12%)
- [ ] **4.1: Comparar os modelos de preços da AWS.**
  - [ ] Opções de compra de computação (Sob demanda, Reservada, Spot).
  - [ ] Savings Plans.
- [ ] **4.2: Compreender os recursos de gerenciamento de cobrança.**
  - [ ] AWS Budgets, Cost Explorer.
  - [ ] Cobrança consolidada com AWS Organizations.
  - [ ] Tags de alocação de custos.
- [ ] **4.3: Identificar os recursos técnicos e as opções de suporte.**
  - [ ] Planos do AWS Support.
  - [ ] AWS Trusted Advisor.
  - [ ] Whitepapers, blogs e documentação.
