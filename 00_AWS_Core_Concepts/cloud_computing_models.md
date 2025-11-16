## Modelos de Serviço de Nuvem: IaaS, PaaS e SaaS

Os serviços de nuvem são categorizados com base no nível de controle e responsabilidade que você tem sobre a infraestrutura. Cada modelo representa uma camada de abstração, definindo o que você gerencia versus o que o provedor de nuvem gerencia.

---

### IaaS (Infrastructure as a Service) - "Comprar o Terreno e os Materiais"

- **O que é**? Fornece os blocos de construção fundamentais da TI: servidores virtuais, armazenamento e redes. É o modelo que oferece o maior nível de flexibilidade e controle sobre sua infraestrutura.
- **Seu controle:** Você gerencia o sistema operacional, os dados e as aplicações.
- **Exemplos na AWS:** Amazon EC2 (servidores virtuais), Amazon S3 (armazenamento de objetos), Amazon VPC (redes).
- **Analogia:** A AWS te vende o terreno (rede), os tijolos (servidores virtuais) e o cimento (armazenamento). Você é o arquiteto e o construtor. Você decide o tamanho da casa, quantos quartos terá, qual sistema operacional (Linux ou Windows) vai rodar, e é sua responsabilidade instalar tudo, garantir que as paredes não caiam (manutenção do S.O.) e trancar a porta (segurança).
- **Na Prática na AWS**:
	- Você usa o Amazon EC2 para criar um servidor virtual (uma "máquina").
	- **Sua responsabilidade**: Escolher o sistema operacional, instalar o que precisa (ex: um servidor web Apache), aplicar atualizações de segurança, configurar o firewall e gerenciar tudo.
	- **Vantagem**: Controle total. Você pode configurar tudo exatamente como quiser.
	- **Desvantagem**: Mais trabalho. Você é responsável por muito mais coisas.

> **Resumo IaaS:** A AWS gerencia o data center físico e a virtualização. **Você gerencia o servidor virtual, o sistema operacional e tudo acima dele.**

---

### PaaS (Platform as a Service) - "Comprar uma Casa Pré-fabricada"

- **O que é**? O provedor gerencia o hardware e o sistema operacional. Você foca apenas em implantar e gerenciar suas aplicações.
- **Seu controle:** Você gerencia suas aplicações e dados.
- **Exemplos na AWS:** AWS Elastic Beanstalk, Amazon RDS (para bancos de dados).
- **Analogia:** Você compra uma casa pré-fabricada. A estrutura, as paredes, o telhado e as instalações já vêm prontas e são mantidas pelo fabricante (AWS). Sua única preocupação é decorar o interior (subir seu código) e usar a casa. Se o fabricante decidir melhorar o material do telhado (atualizar o S.O.), ele faz isso por você.
- **Na Prática na AWS**:
	- Você usa o AWS Elastic Beanstalk.
	- **Sua responsabilidade**: Você simplesmente faz o upload do seu código (ex: um site em Python, Java ou Node.js). O Elastic Beanstalk cuida de criar os servidores (EC2), configurar o balanceamento de carga, instalar o ambiente (Python, Java), e gerenciar o sistema operacional.
	- **Vantagem**: Muita simplicidade. Você foca apenas no seu código, e não na infraestrutura.
	- **Desvantagem**: Menos flexibilidade e controle sobre a infraestrutura subjacente.

> **Resumo PaaS:** A AWS gerencia o hardware e o sistema operacional. **Você gerencia apenas sua aplicação e seus dados.**

---

### SaaS (Software as a Service) - "Alugar um Apartamento Mobiliado"

- **O que é**? Um produto completo, pronto para uso, gerenciado pelo provedor. Na maioria dos casos, os softwares SaaS são aplicações para o usuário final.
- **Seu controle:** Você apenas utiliza o software e gerencia seus dados dentro dele.
- **Exemplos Gerais:** Gmail, Dropbox, Salesforce.
- **Exemplos na AWS:** Amazon WorkMail (e-mail), Amazon Chime (reuniões online).
- **Analogia:** Você aluga um apartamento totalmente mobiliado com serviços inclusos (água, luz, internet, limpeza). Você não se preocupa com a mobília, a manutenção do prédio ou as contas. Você apenas usa o espaço e guarda suas coisas lá.
- **Na Prática na AWS**:
	- Um bom exemplo é o Amazon WorkMail (um serviço de e-mail, concorrente do Gmail) ou o Amazon Chime (para reuniões online, concorrente do Zoom).
	- **Sua responsabilidade**: Apenas criar sua conta, configurar seus usuários e usar o serviço. Você não tem ideia de quantos servidores rodam por trás, qual sistema operacional eles usam, etc. A AWS cuida de absolutamente tudo.
	- **Vantagem**: Simplicidade máxima. É só usar.
	- **Desvantagem**: Controle quase zero. Você usa o que é oferecido, sem poder customizar a infraestrutura.

> **Resumo SaaS:** O provedor (AWS ou outro) gerencia tudo. **Você apenas consome o serviço.**

<hr>
![Diagrama de Responsabilidades IaaS, PaaS, SaaS](https://github.com/user-attachments/assets/57623a37-4509-45a2-ae17-adf13709b4de)