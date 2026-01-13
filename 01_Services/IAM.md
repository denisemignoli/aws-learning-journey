Tags: #iam #aws/dominio2 #aws/seguranca #escopo/global #principio/menor-privilegio
# AWS IAM: Identity and Access Management
O IAM é o serviço que permite gerenciar o acesso aos serviços e recursos da AWS de forma segura. Com ele podemos criar e gerenciar usuários, grupos e usar permissões para permitir ou negar o acesso a recursos.

> [!IMPORTANT] O IAM é um **serviço global**, o que significa que usuários, grupos, funções e políticas são criados globalmente e não em uma região específica.

## Índice
1. [Componentes Principais: Usuários, Grupos e Funções](#1-componentes-principais-usuários-grupos-e-funções)
2. [Políticas e Permissões](#2-políticas-e-permissões)
   - [Estrutura de uma Policy](#estrutura-de-uma-policy)
   - [Princípio do Menor Privilégio](#princípio-do-menor-privilégio)
3. [Formas de Acesso e Autenticação](#3-formas-de-acesso-e-autenticação)
    - [AWS Management Console](#1-aws-management-console)
      - [Política de Senhas](#política-de-senhas-iam-password-policy)
      - [Autenticação Multifator (MFA)](#autenticação-multifator-mfa)
    - [AWS Command Line Interface (CLI)](#2-aws-command-line-interface-cli)
      - [AWS CloudShell](#aws-cloudshell)
    - [AWS Software Development Kits (SDKs)](#3-aws-software-development-kits-sdks)

4. [Ferramentas de Auditoria e Análise do IAM](#4-ferramentas-de-auditoria-e-análise-do-iam)
5. [Melhores Práticas de Segurança do IAM](#5-melhores-práticas-de-segurança-do-iam)

## 1. Componentes Principais: Usuários, Grupos e Funções
O IAM opera com base em "identidades". As principais são:
- **Usuário Raiz (Root User)**:
  - É a identidade criada quando você abre sua conta AWS.
  - Possui acesso total e irrestrito a todos os serviços e recursos.
  - NÃO DEVE ser usado para tarefas diárias. Sua principal função é para o gerenciamento da conta e da cobrança.
- **Usuários IAM (Users)**:
  - Representam uma pessoa ou uma aplicação que precisa interagir com a AWS.
  - Por padrão, um novo usuário IAM é criado sem nenhuma permissão.
- **Grupos IAM (Groups)**:
  - São coleções de usuários. A principal função de um grupo é simplificar o gerenciamento de permissões para um conjunto de usuários.
  - Você anexa uma política de permissão a um grupo, e todos os usuários nesse grupo herdam essas permissões.
  - **Importante**: Grupos só podem conter usuários, não outros grupos. Um usuário pode pertencer a múltiplos grupos. Um usuário não é obrigado a pertencer a um grupo.
- **Funções IAM (Roles)**:
  - São uma forma de delegar permissões para entidades confiáveis, sem a necessidade de compartilhar credenciais de longo prazo (chaves de acesso).
  - Uma função é assumida temporariamente por uma identidade (um usuário, uma aplicação ou um serviço da AWS) para obter permissões.
  - Exemplo de uso: Permitir que uma instância EC2 acesse um bucket S3 sem precisar armazenar chaves de acesso no código da aplicação.
  - Common roles:
    - **EC2 Instance Roles**: Conceder permissões temporárias àquela instância EC2.
    - **Lambda Function Roles**: Conceder à sua função Lambda as permissões necessárias para interagir com outros serviços da AWS (por exemplo, escrever logs no CloudWatch ou ler de uma tabela DynamoDB).
    - **Roles for CloudFormation**: Conceder ao CloudFormation as permissões necessárias para criar, modificar ou deletar os recursos da AWS que estão definidos no seu template. Se o seu template precisa criar uma instância EC2 e um bucket S3, a role do CloudFormation precisa ter permissão para fazer isso.

## 2. Políticas e Permissões
As permissões são atribuídas a usuários ou grupos através de documentos JSON chamados **Policies**.
- <u>O que é uma Policy?</u> É um documento que define explicitamente as permissões. Ele especifica o Efeito (Permitir/Negar), a Ação (qual operação, ex: s3:GetObject), o Recurso (em qual recurso, ex: um bucket S3 específico) e, opcionalmente, as Condições.
### Estrutura de uma Policy
Este documento JSON contém uma ou mais declarações (Statement). Cada declaração inclui:

  - **Effect**: Define se o acesso será permitido (Allow) ou negado (Deny).
  - **Action**: Lista de ações específicas que a política permite ou nega (ex: s3:GetObject).
  - **Resource**: Lista de recursos específicos (identificados por ARNs) aos quais as ações se aplicam.

    ```json
    {
    "Version": "2012-10-17",
    "Id": "S3-Account-Permissions",
    "Statement": [
      {
        "Sid": "1",
        "Effect": "Allow",
        "Principal": {
          "AWS": ["arn:aws:iam::123456789012:root"]
        },
        "Action": [
          "s3:GetObject",
          "s3:PutObject"
        ],
        "Resource": ["arn:aws:s3:::mybucket/*"]
      }
    ]
    }
    ```

### Princípio do Menor Privilégio
  - Esta é a prática de segurança mais importante no IAM.
  - Sempre conceda apenas as permissões mínimas necessárias para que uma identidade (usuário, função) possa realizar sua tarefa, e nada mais.


## 3. Formas de Acesso e Autenticação

Existem três maneiras principais de interagir com os serviços da AWS. Cada uma é adequada para diferentes casos de uso.

| Forma de Acesso                  | Proteção / Credencial     | Uso Principal                                   |
|----------------------------------|---------------------------|-------------------------------------------------|
| AWS Management Console           | Senha + MFA               | Tarefas manuais e visualização rápida           |
| AWS Command Line Interface (CLI) | Access Keys (ID e Secret) | Automação e scripts via terminal                |
| AWS Software Developer Kit (SDK) | Access Keys (ID e Secret) | Integração direta dentro do código da aplicação |


### **AWS Management Console**

-   **O que é:** Uma interface gráfica baseada na web, ideal para visualizar recursos, gerenciar configurações e realizar tarefas de forma manual e intuitiva.
-   **Autenticação:** Via usuário e senha, com a recomendação de uma camada extra de segurança através do MFA (Autenticação Multifator).

    > #### Política de Senhas (IAM Password Policy)
    > Permite definir regras de complexidade para as senhas (comprimento mínimo, tipos de caracteres, expiração, etc.) para evitar senhas fracas. Definir uma política forte é uma melhor prática de segurança fundamental.
    >
    > #### Autenticação Multifator (MFA)
    > Adiciona uma segunda camada de verificação, tornando o acesso muito mais seguro. Mesmo que uma senha seja comprometida, o acesso não é concedido sem o segundo fator.

    > - **Regra de Ouro:** Habilite o MFA para o **Usuário Raiz (Root User)** e para todos os usuários com privilégios administrativos.
    > 
    > - **Tipos de MFA:** A AWS suporta vários tipos de dispositivos MFA para atender a diferentes necessidades de segurança e conveniência. Os principais são:

    >> - **Dispositivo MFA Virtual (Virtual MFA Device)**:
    <u>O que é</u>: Um aplicativo de software que gera códigos de acesso de uso único baseados em tempo (TOTP). É a opção mais comum e flexível.
    <u>Como funciona</u>: Você instala um aplicativo em seu smartphone ou computador (como Google Authenticator, Microsoft Authenticator ou Authy).
    <u>Ideal para</u>: A maioria dos usuários, pois não requer hardware adicional.
    >>
    >> - **Chave de Segurança U2F (Universal 2nd Factor)**:
    <u>O que é</u>: Um dispositivo de hardware físico que você conecta à porta USB do seu computador.
    <u>Como funciona</u>: Quando solicitado, você toca na chave para aprovar o login. Ele se comunica usando o padrão FIDO U2F.
    <u>Exemplo</u>: Chaves da marca YubiKey.
    Ideal para: Usuários que buscam uma segurança física mais robusta e uma experiência de login mais rápida (sem digitar códigos).
    >>
    >> - **Token de Hardware (Hardware Key Fob MFA Device)**:
    <u>O que é</u>: Um pequeno dispositivo de hardware, semelhante a um chaveiro, que gera um código numérico de uso único.
    <u>Como funciona</u>: Você pressiona um botão no dispositivo, e ele exibe um código de 6 dígitos em sua tela para você digitar no login.
    <u>Exemplo</u>: Tokens da marca Gemalto.
    Ideal para: Ambientes corporativos com requisitos de segurança rigorosos, onde a empresa fornece e gerencia os dispositivos de hardware para os funcionários.


### **AWS Command Line Interface (CLI)**

-   **O que é:** Uma ferramenta de linha de comando que permite controlar e automatizar serviços da AWS diretamente do seu terminal. É ideal para administradores de sistemas e para criar scripts de automação.
-   **Autenticação:** Via Chaves de Acesso (Access Keys), que são um par de Access Key ID e Secret Access Key geradas no IAM.

> #### AWS CloudShell
> Para usar a CLI, normalmente você precisa instalá-la em seu computador e configurar as Access Keys. No entanto, a AWS oferece uma maneira mais fácil e rápida de obter acesso a um terminal pré-configurado: o AWS CloudShell.
> - O que é? O CloudShell é um terminal baseado em navegador, acessível diretamente do Console da AWS com um único clique.
> - Como funciona? Ele já vem com a AWS CLI, o SDK e outras ferramentas essenciais pré-instaladas e, o mais importante, já está autenticado com as credenciais do usuário que está logado no console.
> - Vantagens: Zero configuração. Não precisa instalar nada, nem gerenciar Access Keys localmente.
> - Segurança: Usa as credenciais temporárias da sua sessão do console, o que é mais seguro do que armazenar chaves de longo prazo.
> - Consistência: O ambiente é o mesmo para todos os usuários da conta.
Em resumo, o CloudShell é a forma mais rápida e segura de executar comandos da CLI diretamente do seu navegador.

### **AWS Software Development Kits (SDKs)**

-   **O que é:** Um conjunto de bibliotecas e ferramentas para diversas linguagens de programação (Python, Java, JavaScript, etc.). Os SDKs permitem que os desenvolvedores integrem e controlem os serviços da AWS diretamente de dentro do código de suas aplicações.
- **Autenticação**: Também utiliza Chaves de Acesso (Access Keys). No entanto, a melhor prática para aplicações rodando na AWS (ex: em uma instância EC2) é usar Funções IAM (IAM Roles), que fornecem credenciais temporárias e mais seguras, eliminando a necessidade de armazenar chaves de acesso no código.

## 4. Ferramentas de Auditoria e Análise do IAM
Para ajudar a gerenciar e auditar a segurança da sua conta, o IAM fornece duas ferramentas de análise importantes:
1. **IAM Credentials Report (Relatório de Credenciais do IAM)**
- O que é? Um relatório em nível de conta (account-level) que lista todos os usuários IAM da sua conta e o status de suas diversas credenciais.
- Quais informações ele contém?
  - Se as senhas estão ativas.
  - Quando as senhas foram usadas pela última vez.
  - Se as Access Keys (chaves de acesso) estão ativas.
  - Quando as Access Keys foram usadas pela última vez.
- Se o MFA (Autenticação Multifator) está ativado para o usuário.
2. **IAM Access Advisor (Consultor de Acesso do IAM)**
- O que é? Um recurso em nível de usuário, grupo ou role (user-level/identity-level) que mostra os serviços permitidos para aquela identidade e, mais importante, quando esses serviços foram acessados pela última vez.
- Qual problema ele resolve? Ajuda a aplicar o Princípio do Menor Privilégio.

## 5. Melhores Práticas de Segurança do IAM
1. **Proteja sua Conta Raiz**: Nunca use o usuário raiz para tarefas diárias. Ative o MFA para ele e guarde as credenciais em um local seguro.
2. **Use Usuários IAM Individuais**: Não compartilhe credenciais. Crie usuários IAM individuais para cada pessoa que precisa de acesso.
3. **Use Grupos para Gerenciar Permissões**: Em vez de anexar políticas a usuários individuais, anexe-as a grupos e adicione os usuários aos grupos.
4. **Aplique o Menor Privilégio**: Sempre comece com o mínimo de permissões e adicione mais conforme a necessidade.
5. **Use Funções (Roles) para Aplicações e Serviços**: Prefira usar Funções IAM para dar permissões a instâncias EC2 e outros serviços, em vez de usar chaves de acesso.
6. **Habilite o MFA**: Ative a Autenticação Multifator para todos os usuários, especialmente para os mais privilegiados.
7. **Rotacione as Credenciais**: Troque senhas e chaves de acesso regularmente.

<hr>


<details>
<summary><strong>Passo a Passo: Criando um Usuário e Grupo no Console (Clique para expandir)</strong></summary>

1.  **Navegue até o IAM:** No console da AWS, vá para o serviço **IAM**.

2.  **Criar Usuário (Create User):**
    *   **Nome de Usuário (User name):** Dê um nome ao usuário (ex: `denisemig`).
    *   **Acesso ao Console (Provide user access to the AWS Management Console):** Marque esta opção.
    *   **Senha (Console password):** Escolha "Autogenerated password" (senha autogerada) ou "Custom password" (senha customizada).
    *   **Opcional:** Marque a opção para que o usuário precise criar uma nova senha no primeiro login.

3.  **Definir Permissões (Set permissions):**
    *   Escolha a opção **"Adicionar usuário ao grupo" (Add user to group)**.
    *   Clique em **"Criar grupo" (Create group)**.

4.  **Criar Grupo (Create group):**
    *   **Nome do Grupo (User group name):** Dê um nome ao grupo (ex: `Developers`).
    *   **Políticas de Permissão (Permission policies):** Pesquise e selecione as políticas necessárias. Por exemplo, para um desenvolvedor que precisa de acesso de leitura à maioria dos serviços, você pode anexar a política gerenciada pela AWS chamada **`ReadOnlyAccess`**.
    *   Clique em **"Criar grupo de usuários" (Create user group)**.

5.  **Revisar e Criar:**
    *   De volta à tela de criação do usuário, o novo grupo `Developers` estará selecionado.
    *   Avance para a tela de revisão.
    *   Clique em **"Criar usuário" (Create user)**.

**Resultado:** Você criou um usuário, um grupo, anexou uma política de permissões ao grupo e adicionou o usuário a esse grupo. O usuário `denisemig` agora tem as permissões de `ReadOnlyAccess`.

</details>

