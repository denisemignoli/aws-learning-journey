## Modelos de Implantação de Nuvem

Os modelos de implantação definem **onde** sua infraestrutura e suas aplicações irão residir. Existem três modelos principais, cada um com suas próprias características e casos de uso.

### Tabela Comparativa Rápida

| Característica | Nuvem Pública (All-in) | Nuvem Híbrida (Hybrid) | Nuvem Privada (On-Premises) |
| :--- | :--- | :--- | :--- |
| **Localização** | No provedor de nuvem (AWS) | Parte na AWS, parte no seu data center | Apenas no seu data center |
| **Propriedade** | Do provedor de nuvem | Compartilhada | Da sua empresa |
| **Escalabilidade** | Praticamente infinita, elástica | Alta (usando a parte da nuvem) | Limitada ao hardware comprado |
| **Custo** | Operacional (OPEX) | Misto (OPEX + CAPEX) | Principalmente de Capital (CAPEX) |
| **Controle** | Menor (sobre o hardware) | Alto (na parte local) | Total |
| **Ideal para** | Novas aplicações, startups, agilidade | Empresas com dados sensíveis ou investimentos legados | Governo, finanças, alta regulamentação |
| **Exemplo**|Uma startup que cria um novo aplicativo mobile e hospeda todo o seu backend (banco de dados, APIs, autenticação) na AWS.| Um banco que mantém os dados principais de seus clientes em seus servidores locais (on-premises), mas usa a AWS para executar análises de risco complexas sobre esses dados ou para hospedar seu site institucional. | Uma agência governamental de inteligência que precisa manter todos os seus dados em uma rede fisicamente isolada e controlada por ela.  

### Modelos de Serviço vs. Modelos de Implantação

É crucial entender que esses dois conceitos não são excludentes; eles são **eixos ortogonais**. Você pode ter qualquer modelo de serviço em (quase) qualquer modelo de implantação.

A tabela abaixo ilustra essa relação com exemplos práticos:

| | IaaS (Infraestrutura) | PaaS (Plataforma) | SaaS (Software) |
| :--- | :--- | :--- | :--- |
| **Nuvem Pública** | **Amazon EC2:** Você aluga VMs da AWS. | **AWS Elastic Beanstalk:** Você sobe seu código na plataforma da AWS. | **Gmail, Salesforce:** Você usa um software pronto que roda na nuvem de terceiros. |
| **Nuvem Híbrida** | Sua aplicação no EC2 (IaaS público) acessa um banco de dados no seu escritório (IaaS privado). | Sua aplicação no Elastic Beanstalk (PaaS público) se conecta a um sistema legado no seu data center. | Você usa o Salesforce (SaaS público), mas ele se integra com um sistema de RH que roda na sua empresa. |
| **Nuvem Privada** | Sua empresa usa VMware ou OpenStack para oferecer "VMs sob demanda" aos seus próprios desenvolvedores. | Sua empresa instala uma plataforma como Red Hat OpenShift nos seus próprios servidores para facilitar o deploy. | Sua empresa instala e gerencia uma versão auto-hospedada de um software, como o Mattermost (alternativa ao Slack). |

