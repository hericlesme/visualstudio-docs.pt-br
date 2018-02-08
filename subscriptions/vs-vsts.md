---
title: VSTS para assinantes do Visual Studio | Microsoft Docs
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Understand how you can use Visual Studio Team Services (VSTS) as a Visual Studio subscriber.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: d3287740daded32afa9b93e109a76b1804e82a75
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-team-services-vsts-benefit-in-visual-studio-subscriptions"></a>Benefício VSTS (Visual Studio Team Services) nas assinaturas do Visual Studio

## <a name="overview"></a>Visão geral 
Para repositórios Git gratuitos, ferramentas de planejamento Agile e compilações hospedadas para qualquer idioma. É o complemento perfeito para seu IDE. 
- Crie o ambiente de desenvolvimento perfeito para sua equipe. 
- Mantenha-se conectado desde a ideia até o lançamento. 
- Melhore a qualidade do código e detecte os erros precocemente.
- Automatize e simplifique suas implantações do Azure
- Aumente a produtividade com recursos avançados. 

## <a name="eligibility"></a>Qualificação
| Nível de Assinatura/Programa                                                  | Benefício               | Renovável?                                                         |
|-------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------|
| Visual Studio Enterprise Standard                                             | Acesso avançado       |  Sim                                                               |
| Visual Studio Enterprise anual                                               | Acesso avançado       |  Sim                                                               |
| Visual Studio Enterprise mensal                                              | Acesso avançado       |  Sim                                                               |
| Visual Studio Professional Standard                                           | Acesso básico          |  Sim                                                               |
| Visual Studio Professional anual                                             | Acesso básico          |  Sim                                                               | 
| Visual Studio Professional mensal                                            | Acesso básico          |  Sim                                                               |
| Visual Studio Test Pro                                                        | Acesso avançado       |  Sim                                                               |
| Plataformas MSDN                                                                | Acesso avançado       |  Sim                                                               |
| Visual Studio Dev Essentials                                                  | Participante           |  Sim                                                               |
| Visual Studio Enterprise – NFR<sup>1</sup>                                               | Acesso avançado       |  Sim                                                               |
| Visual Studio Enterprise - FTE                                                | Acesso avançado       |  Sim                                                               |
| Visual Studio Enterprise ‒ Microsoft Partner Network                          | Acesso avançado       |  Sim                                                               |
| Visual Studio Professional – Microsoft Partner Network                        | Acesso básico          |  Sim                                                               |
| Visual Studio Enterprise – Imagine (Standard)                                 | Acesso básico          |  Sim                                                               |
| Visual Studio Enterprise – Imagine (Premium)                                  | Acesso básico          |  Sim                                                               |
| Visual Studio Enterprise – BizSpark                                           | Acesso avançado       |  Sim                                                               |
| Microsoft Certified Trainer ‒ Software e Serviços                             | Acesso básico          |  Sim                                                               |
| Microsoft Certified Trainer ‒ Desenvolvedor de Software e Serviços                   | Acesso avançado       |  Sim                                                               |

<sup>1</sup>  *Inclui: NFR (Proibida a revenda), MVP (Microsoft Valued Partner), RD (Diretor de Região), VSIP (Visual Studio Industry Partner)*  

Não tem certeza de qual assinatura você está usando?  Conecte-se a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) para ver todas as assinaturas atribuídas a seu endereço de email. Se não vir todas as suas assinaturas, talvez você tenha uma ou mais atribuídas a outro endereço de email.  Você precisará entrar com esse endereço de email para ver as assinaturas. 

Quando você entrar no VSTS usando a mesma identidade usada para ativar sua assinatura do Visual Studio, ela será reconhecida automaticamente. Isso funciona para a identidade principal usada ao fazer logon no Portal do Assinante e para qualquer identidade alternativa que esteja configurada para a sua assinatura do Visual Studio. O VSTS é compatível tanto com contas da Microsoft (como @outlook.com) quanto com contas corporativas ou de estudante (que usam um Azure Active Directory gerenciado pela organização). Você pode usar suas identidades principais e alternativas no VSTS e adicionar qualquer número de contas do VSTS como membros.

Para usar o VSTS, você precisará de uma conta. Você pode entrar com uma conta existente ou criar uma nova.  Para criar uma nova conta:
1.  Entre em [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).
2.  Localize o bloco Visual Studio Team Services na seção Ferramentas e clique no link "Introdução" na parte inferior do bloco do benefício.   

Estes recursos do VSTS estão incluídos nas seguintes assinaturas: 
- Visual Studio Enterprise: [Básico](https://www.visualstudio.com/team-services/compare-features/), [Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web), [Gerenciamento de Pacotes](https://marketplace.visualstudio.com/items?itemName=ms.feed)
- Visual Studio Professional: [Básico](https://www.visualstudio.com/team-services/compare-features/)
- Plataformas MSDN: [Básico](https://www.visualstudio.com/team-services/compare-features/), [Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)
- Visual Studio Test Professional: [Básico](https://www.visualstudio.com/team-services/compare-features/), [Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)

3.  Insira um nome para o site do projeto do VSTS.  

4.  Escolha se deseja usar o **Git** ou o **TFVC (Controle de Versão do Team Foundation)** para gerenciar o projeto.  Essa é uma escolha permanente para cada projeto de equipe que você criar, mas é possível usar os projetos de equipe TFVC e Git na mesma coleção de projetos de equipe.  Não sabe qual deseja usar? 
    - Git: o Git é um sistema de controle de versão descentralizado. Cada desenvolvedor tem uma cópia do repositório inteiro de origem em seu computador de desenvolvimento. Os desenvolvedores podem confirmar cada conjunto de alterações em seu computador de desenvolvimento e executar operações de controle de versão, como histórico e comparação, sem uma conexão de rede.  [Saiba mais](https://www.visualstudio.com/docs/git/gitquickstart) sobre o Git.
    - O TFVC (Controle de Versão do Team Foundation) é um sistema de controle de versão centralizado. Normalmente, os membros da equipe tem apenas uma versão de cada arquivo em seus computadores de desenvolvimento. Os dados históricos são mantidos somente no servidor. As ramificações são baseadas em caminho e criadas no servidor. [Saiba mais](https://www.visualstudio.com/docs/tfvc/overview) sobre o Controle de Versão do Team Foundation.

 
5.  Clique em **Alterar detalhes** para personalizar as opções de nome do projeto, de como organizar seu trabalho (Agile, Scrum, CMMI), de onde hospedar seus projetos e de como compartilhar seu trabalho com outras pessoas.  Clique em "Continuar".

# <a name="create-your-vsts-account"></a>Criar sua conta do VSTS

6.  Levará um tempo para criar sua conta e, em seguida, você verá a página do VSTS do seu primeiro projeto, usando o nome especificado.  Agora você está pronto para começar a usar o Visual Studio Team Services!

Você também receberá um email confirmando que a sua conta foi criada com êxito.  Ele também listará a URL da conta e os endereços de email de conexão e preferencial.  

![Email de boas-vinda do benefício VSTS](_img\vs-vsts\vs-vsts-welcome.png)


## <a name="faq"></a>Perguntas Frequentes
### <a name="q--what-is-the-difference-between-free-basic-access-and-advanced-access"></a>P: Qual é a diferença entre o acesso Gratuito, Básico e Avançado?
R: Os recursos disponíveis variam de acordo com o nível de acesso.  Encontre informações detalhadas sobre os [níveis de acesso](/vsts/security/access-levels). 

### <a name="q--how-do-i-add-users-to-my-vsts-account-or-team-project"></a>P: Como posso adicionar usuários à minha conta do conta ou projeto de equipe do VSTS?
R: Saiba como [gerenciar usuários e acesso](/vsts/accounts/add-account-users-from-user-hub) no VSTS.

## <a name="support-resources"></a>Recursos de suporte
-  Para obter assistência com vendas, assinaturas, contas e cobrança para Assinaturas do Visual Studio, entre em contato com o [Suporte a Assinaturas](https://www.visualstudio.com/subscriptions/support/) do Visual Studio.
-  Tem alguma pergunta sobre o IDE do Visual Studio, o Visual Studio Team Services ou outros produtos ou serviços do Visual Studio?  Acesse o [Suporte do Visual Studio](https://www.visualstudio.com/support/). 
-  Para obter a documentação completa do Visual Studio Team Services, visite /vsts/.
Para usar o VSTS, você precisará criar uma conta ou a ser adicionado como membro na conta de outra pessoa. Criar uma conta do VSTS é gratuito e você pode criar várias contas do VSTS. 

[Como se inscrever no VSTS](/vsts/accounts/index)
