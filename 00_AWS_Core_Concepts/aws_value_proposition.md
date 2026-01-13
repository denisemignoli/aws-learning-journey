Tags: #aws/dominio1 #nuvem/beneficios #cloud/economia #finanças/opex #ferramenta/tco #otimizacao/right-sizing
## O que é computação em nuvem?
Computação em nuvem é a entrega **sob demanda** de capacidade de computação, banco de dados, armazenamento, aplicativos e outros recursos de TI. Esses recursos são entregues por meio de uma plataforma de serviços de nuvem via Internet, com **pagamento conforme o uso**.

> A nuvem é composta por **computadores servidores em grandes data centers em diferentes locais ao redor do mundo**. Ao usar um serviço de nuvem, como a Amazon Web Services (AWS), você usa os computadores de propriedade da AWS.

*Características*:

- **Sob Demanda:** Recursos disponíveis em minutos com apenas alguns cliques.
- **Acesso Global:** Entregue através de uma plataforma de serviços via internet.
- **Pagamento Conforme o Uso:** Pague apenas pelo que consumir, sem custos iniciais elevados.
- **Flexibilidade:** Trate a infraestrutura como software, permitindo mudanças rápidas e de baixo custo.

## Modelo de Computação Tradicional vs. Computação em Nuvem
Para entender o valor da nuvem, é útil comparar os dois modelos:

|Característica|Modelo Tradicional (On-Premises)|Modelo de Nuvem (AWS)|
|---|---|---|
|**Modelo de Infraestrutura**|**Infraestrutura como Hardware**: Rígida, física e definida por servidores, cabos e racks.|**Infraestrutura como Software**: Flexível, virtual e definida por código e APIs.|
|**Aquisição**|Requer compra de hardware com antecedência.|Recursos são provisionados sob demanda em minutos.|
|**Custos**|**CAPEX:** Grandes investimentos iniciais em ativos físicos.|**OPEX:** Pague apenas pelo que consumir, como uma conta de luz.|
|**Escalabilidade**|Lenta e cara. Comprar novos servidores pode levar semanas.|**Elástica:** Escale para cima ou para baixo automaticamente conforme a demanda.|
|**Manutenção**|A empresa é responsável por tudo: energia, refrigeração, segurança física.|A AWS gerencia a infraestrutura subjacente. Você foca no seu aplicativo.|
|**Alcance Global**|Limitado pela localização dos seus data centers.|Implante aplicações em múltiplas regiões do mundo com poucos cliques.|

## Trocando Despesas de Capital (CAPEX) por Despesas Operacionais (OPEX)

Um dos benefícios financeiros mais significativos da nuvem é a mudança de um modelo de **CAPEX** para um de **OPEX**.

- **CAPEX (Capital Expenditure):** Refere-se ao dinheiro que uma empresa gasta para comprar, manter ou atualizar ativos físicos, como servidores, equipamentos de rede e data centers. É um **grande investimento inicial**, feito antes de saber qual será a demanda real.
    
- **OPEX (Operational Expenditure):** Refere-se às despesas do dia a dia de uma operação, como eletricidade, salários e, no caso da nuvem, o **pagamento mensal pelos serviços que você consome**.
    

Com a AWS, você para de gastar dinheiro com CAPEX (comprar servidores) e passa a gastar com OPEX (pagar uma "conta de luz" pelos recursos de computação que utiliza). Isso elimina a necessidade de grandes investimentos iniciais e permite que empresas de todos os tamanhos, incluindo startups, tenham acesso à mesma tecnologia de ponta que as grandes corporações.

### Calculando a Economia Real: Custo Total de Propriedade (TCO)

A mudança de CAPEX para OPEX resulta em uma redução significativa do **Custo Total de Propriedade (TCO)**. O TCO é uma análise financeira que ajuda a calcular a economia real de se mover para a AWS.

Para isso, a AWS oferece a **Calculadora de Custo Total de Propriedade (TCO) da AWS**, que compara o custo de executar suas aplicações em um ambiente local (on-premises) versus na nuvem AWS.

A calculadora leva em conta não apenas os custos diretos, mas também os **custos indiretos (ocultos)** da infraestrutura local, como:

- **Custos do Data Center:**
    - Eletricidade e refrigeração.
    - Segurança física (câmeras, guardas).
    - Manutenção do prédio e aluguel do espaço.
- **Custos de Hardware e Software:**
    - Compra e renovação de servidores, roteadores e switches.
    - Licenças de software e sistemas operacionais.
- **Custos de Pessoal:**
    - Salários de administradores de rede, de sistemas e de segurança para manter a infraestrutura funcionando 24/7.

Ao mover para a AWS, a maior parte desses custos é eliminada e substituída pela fatura mensal da AWS, que, devido à **economia de escala**, geralmente resulta em um TCO muito menor.

### Dimensionamento correto (Right Sizing)
O Right Sizing é o processo de revisar continuamente seus recursos de computação para garantir que eles tenham o tamanho ideal para a carga de trabalho atual.

- **Por que é importante?** No modelo OPEX, você paga pelo que provisiona. Se você usa uma instância de servidor maior do que o necessário, está desperdiçando dinheiro.

- **Como funciona**: Você analisa o desempenho (CPU, memória, rede) e ajusta o recurso para o menor tamanho possível que ainda mantenha a performance desejada.

- **Relação com a Economia**: É o passo fundamental antes de considerar outras opções de economia, como Instâncias Reservadas ou Savings Plans.