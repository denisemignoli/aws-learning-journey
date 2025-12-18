A Infraestrutura global da AWS foi projetada e construída para oferecer um ambiente de computação em nuvem flexível, confiável, dimensionável e seguro com desempenho  de rede global de alta qualidade.

A AWS fornece um amplo conjunto de serviços, como computação, opções de armazenamento, redes e bancos de dados, entregues como um utilitário sob demanda que estará disponível em segundos, com preço de pagamento conforme o uso. Todos esses serviços residem na infraestrutura global da AWS.

## Data centers da AWS
Os data centers são a base da infraestrutura da AWS. 
Os data centers da AWS são construídos em clusters em várias Regiões globais.
Os data centers geralmente têm características como:  
- Um local onde os dados físicos reais residem e o processamento de dados ocorre
- Um único data center normalmente abriga de 50.000 a 80.000 servidores
- Ficar online
	- Todos os data centers ficam online
	- Nenhum data center fica inativo (ou não está sendo usado)

Além disso, os data centers contêm equipamentos de rede personalizados da AWS, como:
- Hardware originário de vários fabricantes originais do projeto (Original Design Manufacturer, ODM)
- Conjunto de protocolos de rede personalizados da Amazon

## Zonas de Disponibilidade da AWS
- Cada Zona de disponibilidade é:
	- Composta por um ou mais data centers
	- Projetada para isolamento de falhas
	- Interconectada com outras Zonas de Disponibilidade por meio de links privados de alta velocidade
- Algumas Zonas de Disponibilidade têm até seis data centers, entretanto, nenhum data center pode fazer parte de duas Zonas de Disponibilidade.
- Você é responsável por escolher as Zonas de Disponibilidade em que os sistemas serão armazenados. Os sistemas podem estar em várias Zonas de Disponibilidade.
- A AWS recomenda replicar entre Zonas de Disponibilidade para fins de resiliência.

## Regiões da AWS
- Uma Região da AWS é uma área geográfica.
- Cada Região é composta por duas ou mais Zonas de Disponibilidade
- A AWS tem 24 regiões ao redor do mundo (dado de 2020)
- Você habilita e controla a replicação de dados entre Regiões
- A comunicação entre as Regiões usa a estrutura de conexões de rede da infraestrutura  da AWS
- As Regiões são isoladas umas das outras para obter tolerância a falhas e estabilidade.
- Os recursos em uma Região não são replicados automaticamente para outras Regiões.

Em agosto de 2020, a infraestrutura global da AWS incluía 24 Regiões e 77 Zonas de Disponibilidade. A AWS expande constantemente sua infraestrutura global adicionando mais Regiões. Ao expandir a infraestrutura, a AWS ajuda os clientes a obter menor latência e taxa de transferência mais alta, bem como a garantir que os dados residam apenas nos locais desejados.

## Pontos de presença
Um ponto de presença é o local em que os usuários finais acessam os serviços da AWS por meio do serviço Amazon CloudFrontou Amazon Route 53.

A AWS oferece uma rede global de 216 locais de pontos de presença (PoP).
- Composta por 205 locais de borda e 11 caches de borda regionais
- Juntamente com o Amazon CloudFront, uma rede de entrega de conteúdo (CDN) distribui conteúdo aos usuários finais com latência reduzida.
- Caches de borda regionais usados para conteúdo com acesso infrequente.

