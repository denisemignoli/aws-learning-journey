# AWS Well-Architected Framework

O AWS Well-Architected Framework é um guia criado pela AWS que ajuda os clientes a construir a infraestrutura mais segura, resiliente, eficiente e de alta performance possível para suas aplicações.

Ele não é um serviço, mas sim um conjunto de **melhores práticas**, perguntas de design e estratégias, organizado em **seis pilares**. O objetivo é permitir que você avalie sua arquitetura e a aprimore ao longo do tempo.

---

## Os 6 Pilares do Framework

### 1. Excelência Operacional (Operational Excellence)
Este pilar foca na capacidade de **executar e monitorar sistemas** para entregar valor de negócio e de melhorar continuamente os processos e procedimentos de suporte.

*   **Princípios de Design:** 
	* Executar operações como código (Infrastructure as Code)
	* Anotar a documentação
	* Fazer alterações frequentes, pequenas e reversíveis
	* Refinar os procedimentos operacionais com frequência
	* Prever falhas
	* Aprenda com todas as falhas operacionais
*   **Serviços Chave:** AWS CloudFormation, AWS Config, Amazon CloudWatch, AWS X-Ray.

### 2. Segurança (Security)
Este pilar foca em proteger informações, sistemas e ativos, enquanto entrega valor de negócio através da avaliação de riscos e da implementação de estratégias de mitigação.

*   **Princípios de Design:** 
	* Aplicar a segurança em todas as camadas
	* Habilitar a rastreabilidade
	* Implementar o princípio do menor privilégio
	* Proteger seu sistema
	* Automatizar as práticas recomendadas de segurança
*   **Serviços Chave:** AWS IAM, Amazon GuardDuty, AWS Shield, AWS KMS, AWS WAF.

### 3. Confiabilidade (Reliability)
Este pilar foca na capacidade de um sistema de se recuperar de falhas de infraestrutura ou de serviço, de adquirir dinamicamente recursos de computação para atender à demanda e de mitigar interrupções.

*   **Princípios de Design:**
	* Testar procedimentos de recuperação
	* Recuperar-se de falhas automaticamente
	* Dimensionar a escala horizontalmente para aumentar a disponibilidade agregada do sistema
	* Parar de tentar adivinhar a capacidade
	* Gerenciar alterações na automação
*   **Serviços Chave:** Amazon Route 53, Auto Scaling, Zonas de Disponibilidade (AZs), AWS Backup.

### 4. Eficiência de Performance (Performance Efficiency)
Este pilar foca no uso eficiente dos recursos de computação para atender aos requisitos do sistema e em manter essa eficiência à medida que a demanda muda e as tecnologias evoluem.

*   **Princípios de Design:**
	* Democratizar tecnologias avançadas
	* Obter alcance global em minutos
	* Usar arquitetura sem servidor;
	* Experimentar com maior frequência
	* Ter afinidade mecânica
*   **Serviços Chave:** Amazon EC2 (com tipos de instância específicos), Amazon S3 (com classes de armazenamento), AWS Lambda, Amazon RDS.

### 5. Otimização de Custos (Cost Optimization)
Este pilar foca em evitar custos desnecessários. É sobre entender e controlar onde o dinheiro está sendo gasto, selecionar o tipo e a quantidade certa de recursos e analisar os gastos ao longo do tempo.

*   **Princípios de Design:**
	* Adotar um modelo de consum
	* Medir a eficiência geral
	* Reduzir os gastos com operações do data center
	* Analisar e atribuir despesas
	* Usar serviços gerenciados
*   **Serviços Chave:** AWS Budgets, AWS Cost Explorer, Savings Plans, Instâncias Spot do EC2.

### 6. Sustentabilidade (Sustainability)
Este é o pilar mais novo e foca em minimizar os impactos ambientais da execução de cargas de trabalho na nuvem.

*   **Princípios de Design:** Entender seu impacto, estabelecer metas de sustentabilidade, maximizar a utilização de recursos e usar serviços gerenciados para minimizar o uso de hardware.
*   **Serviços Chave:** AWS Graviton (processadores eficientes em energia), Instâncias Spot, AWS Compute Optimizer.
