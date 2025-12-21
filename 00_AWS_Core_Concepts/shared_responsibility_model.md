# O Modelo de responsabilidade compartilhada da AWS

O Modelo de responsabilidade compartilhada é um dos conceitos mais importantes de segurança na AWS. Ele define claramente quais tarefas de segurança são de responsabilidade da **AWS** e quais são de responsabilidade do **cliente**.

A frase-chave para lembrar é:
- A **AWS** é responsável pela segurança **DA** nuvem.
- O **Cliente** é responsável pela segurança **NA** nuvem.

---

## A Analogia: O prédio de apartamentos

Pense em usar a AWS como morar em um prédio de apartamentos de alta segurança:

- **Responsabilidade da AWS (A Construtora/Administradora do Prédio):**
  - A construtora é responsável pela **fundação do prédio**, pela segurança do perímetro (muros, portões), pelo controle de acesso às áreas comuns (hall de entrada, elevadores) e pela infraestrutura básica (eletricidade, encanamento). Eles garantem que o prédio seja estruturalmente seguro e que ninguém não autorizado entre nas áreas comuns.

- **Sua Responsabilidade (O morador do apartamento):**
  - Você é responsável por tudo **dentro do seu apartamento**. Você deve **trancar a sua porta**, não deixar a janela aberta, não dar sua chave para estranhos e decidir quem pode ou não entrar no seu espaço privado. A administradora do prédio não tem responsabilidade se você deixar sua porta destrancada e alguém entrar.

---

## Responsabilidades da AWS (Segurança DA nuvem)

A AWS gerencia e protege a infraestrutura física que sustenta toda a nuvem. Isso inclui:

- **Hardware Físico:** Servidores, equipamentos de rede e cabos nos data centers.
- **Software Fundamental:** O hipervisor que cria as máquinas virtuais e o software de rede.
- **Infraestrutura Global:** A segurança física dos Data Centers, Zonas de Disponibilidade e Regiões.

Em suma, a AWS garante que a "casa" que eles te alugam (a infraestrutura) seja segura, resiliente e disponível.

---

## Suas responsabilidades (Segurança NA nuvem)

Sua responsabilidade depende muito dos serviços que você usa, mas geralmente inclui:

- **Gerenciamento de acesso e identidade:**
  - Criar e gerenciar usuários, grupos e permissões no **IAM**.
  - Aplicar o princípio do menor privilégio.
  - Proteger a conta raiz com **MFA (Autenticação Multifator)**.

- **Dados do cliente:**
  - Você é responsável pelos seus próprios dados.
  - Decidir se vai usar **criptografia** para proteger os dados em repouso (no disco) e em trânsito (na rede).

- **Configuração da aplicação e do sistema operacional:**
  - Instalar patches de segurança no sistema operacional das suas instâncias EC2.
  - Configurar corretamente os **Security Groups** (o firewall da sua instância) e as **Network ACLs** (o firewall da sua rede).
  - Garantir que sua aplicação não tenha vulnerabilidades de código.

---

## Como a responsabilidade muda com IaaS, PaaS e SaaS

A linha que divide a responsabilidade não é fixa. Ela muda dependendo do modelo de serviço que você escolhe:

- **IaaS (ex: EC2):** Você tem a maior responsabilidade. Você gerencia o SO, os patches, as bibliotecas e tudo acima. (Você constrói a maior parte da "casa").
- **PaaS (ex: RDS, Elastic Beanstalk):** A AWS gerencia mais coisas para você, como o SO e os patches do banco de dados. Sua responsabilidade diminui, focando apenas na sua aplicação e nos seus dados. (A "casa" já vem pré-fabricada).
- **SaaS (ex: Amazon Chime):** Você tem a menor responsabilidade. A AWS gerencia tudo, e você apenas usa o software. (Você só usa o "apartamento mobiliado").

### Diagrama de responsabilidades

<p align="center">
  <img src="https://github.com/user-attachments/assets/e90388c2-2241-42c1-96eb-3c42c37354d1" alt="Diagrama de Responsabilidade Compartilhada" width="700"/>
</p>

<p align="center">
  <em>Fonte: <a href="https://aws.amazon.com/pt/compliance/shared-responsibility-model/">Modelo de responsabilidade compartilhada da AWS</a></em>
</p>
