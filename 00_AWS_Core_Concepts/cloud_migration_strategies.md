# Estratégias de Migração para a Nuvem

Migrar uma infraestrutura existente para a nuvem é um processo complexo. Para ajudar as organizações a planejar e executar essa jornada, a AWS propõe dois frameworks conceituais principais: as Estratégias de Migração (os "6 R's") e o Cloud Adoption Framework (CAF).

---

## As 6 Estratégias de Migração (Os "6 R's")

Quando uma empresa decide migrar uma aplicação para a nuvem, ela geralmente escolhe uma das seis estratégias a seguir. A escolha depende da complexidade da aplicação, do custo e do objetivo de negócio.

1.  **Rehost (Lift-and-Shift / Realocar):**
    *   **O que é?** Mover a aplicação do ambiente local para a nuvem com o mínimo de modificações. É como pegar um servidor físico e recriá-lo como uma instância EC2.
    *   **Vantagem:** É a estratégia mais rápida e simples para começar.
    *   **Exemplo:** Mover um servidor de aplicação legado para uma instância EC2 sem alterar o código.

2.  **Replatform (Lift-and-Tinker-and-Shift / Remodelar):**
    *   **O que é?** Mover a aplicação para a nuvem fazendo algumas otimizações para aproveitar os benefícios da nuvem, mas sem mudar a arquitetura central.
    *   **Vantagem:** Oferece melhorias de performance e custo com um esforço moderado.
    *   **Exemplo:** Migrar um banco de dados que rodava em um servidor local para o **Amazon RDS**, um serviço de banco de dados gerenciado (PaaS).

3.  **Refactor / Re-architect (Refatorar / Rearquitetar):**
    *   **O que é?** Reimaginar e reescrever a aplicação do zero, usando tecnologias nativas da nuvem. É a estratégia que gera mais valor, mas também a mais complexa e demorada.
    *   **Vantagem:** A aplicação se torna altamente escalável, resiliente e eficiente.
    *   **Exemplo:** Quebrar uma aplicação monolítica antiga em vários microsserviços usando **AWS Lambda** e **Amazon DynamoDB**.

4.  **Repurchase (Recomprar):**
    *   **O que é?** Descartar uma aplicação legada e mover para um produto de software pronto, geralmente um SaaS.
    *   **Vantagem:** Elimina a necessidade de gerenciar e manter uma aplicação customizada.
    *   **Exemplo:** Trocar um sistema de CRM (Customer Relationship Management) interno por uma assinatura do **Salesforce**.

5.  **Retire (Aposentar):**
    *   **O que é?** Simplesmente desligar e desativar aplicações que não são mais necessárias ou que se tornaram redundantes.
    *   **Vantagem:** Economia de custos imediata ao eliminar recursos que não geram valor.
    *   **Exemplo:** Identificar durante o processo de migração que dois sistemas faziam a mesma coisa e aposentar um deles.

6.  **Retain (Reter):**
    *   **O que é?** Manter a aplicação no ambiente local (on-premises) por enquanto. Isso pode acontecer por razões de custo, regulamentação ou porque a aplicação ainda não está pronta para ser migrada.
    *   **Vantagem:** Evita o custo e o risco de migrar sistemas que não trarão benefício imediato na nuvem.
    *   **Exemplo:** Manter um sistema de mainframe muito antigo e crítico funcionando no data center local.

---

## AWS Cloud Adoption Framework (CAF)

Enquanto os "6 R's" focam na migração de *aplicações individuais*, o **AWS CAF** foca na migração da *organização como um todo*. Ele ajuda a empresa a identificar e aprimorar as habilidades e processos necessários para uma adoção bem-sucedida da nuvem.

O CAF organiza suas diretrizes em **seis perspectivas (perspectives)**:

#### Perspectivas de Negócio:
1.  **Negócios (Business):** Garante que a TI esteja alinhada com os objetivos de negócio. (Envolve gestores de negócio, finanças, etc.)
2.  **Pessoas (People):** Foca na gestão de pessoas e mudanças, treinamento e comunicação. (Envolve RH, treinamento, etc.)
3.  **Governança (Governance):** Garante que as habilidades e processos de TI governem as operações na nuvem. (Envolve CIO, gerentes de programa, etc.)

#### Perspectivas Técnicas:
4.  **Plataforma (Platform):** Foca em construir a arquitetura de nuvem, implementando novas soluções e migrando cargas de trabalho. (Envolve CTO, arquitetos de nuvem, etc.)
5.  **Segurança (Security):** Garante que a organização atenda aos seus objetivos de segurança, confidencialidade e integridade. (Envolve CISO, engenheiros de segurança, etc.)
6.  **Operações (Operations):** Foca em como operar, monitorar e otimizar a infraestrutura na nuvem. (Envolve gerentes de operações de TI, etc.)
