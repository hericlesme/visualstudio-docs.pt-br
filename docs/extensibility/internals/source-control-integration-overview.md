---
title: Visão geral de integração de controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d75936e21729729dfeafaa041d800acbe01caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-integration-overview"></a>Visão geral de integração de controle do código-fonte
Esta seção compara as duas formas de integrar o controle de origem do Visual Studio; um controle de origem plug-in e um VSPackage que fornece uma solução de controle de origem e destaca os novos recursos de controle de origem. O Visual Studio permite manual alternando o controle de origem VSPackages e plug-ins de controle de origem, bem como com base em solução de comutação automática.  
  
## <a name="source-control-integration"></a>Integração de controle de origem  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oferece suporte a dois tipos de opções de integração de controle de origem. Todas as versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você ainda pode integrar um plug-in com base na API de plug-in de controle do código-fonte (anteriormente também conhecida como a API MSSCCI), e que fornece funcionalidade de controle de origem básico usando o Visual Studio fonte (de interface de usuário de controle INTERFACE DO USUÁRIO). Um controle de origem VSPackage, por outro lado, fornece uma integração profundo nova [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] caminho adequado para a integração de controle de origem que exige um alto nível de sofisticação e autonomia no seu modelo de controle de origem.  
  
 ![Visão geral do controle de origem](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in de controle de origem  
 Todas as versões do Visual Studio oferecem suporte a API de plug-in de controle de origem especificação versão 1.2 como um caminho de integração. Um implementador de plug-in de controle de origem grava uma DLL que implementa as funções de API de plug-in de controle de origem para a integração de controle de origem e o registro conforme descrito em [criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md). Nessa abordagem, o ambiente de desenvolvimento integrado (IDE) usa o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário para as caixas de diálogo, como check-in, check-out e glifos de controle do código-fonte, barras de ferramentas e páginas de propriedade Ferramentas/opções. Estrita aderência para a API de plug-in de controle de origem garante uma fácil integração com o Visual Studio e uma experiência sem problemas para o usuário. Isso significa que o plug-in de controle de origem deve implementar a maioria das funções e retornos de chamada detalhados na API.  
  
 Para implementar um plug-in de usando a API de plug-in de controle de origem de controle de origem, siga estas etapas:  
  
1.  Criar uma DLL que implementa as funções especificadas na [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrar a DLL, tornando as entradas do registro apropriada (descrito na [como: instalar um plug-in de controle de origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Criar um auxiliar de interface do usuário e a exibição quando solicitado pelo pacote de adaptador de controle de origem (o componente do Visual Studio que lida com a funcionalidade de controle de origem por meio de plug-ins de controle de origem)  
  
 Em resposta a um comando de controle de origem, o Visual Studio IDE apresenta uma interface de usuário padrão para as operações básicas e, em seguida, transmite as informações de controle de origem plug-in por meio de funções definidas na API de plug-in de controle de origem. Para opções avançadas, o plug-in de controle de origem pode ser chamado em para apresentar sua própria interface do usuário, por exemplo, navegando para um projeto de controle do código-fonte. Isso significa que o usuário pode ser apresentado dois estilos possivelmente diferentes da interface do usuário ao lidar com controle de origem: a interface do usuário que apresenta do Visual Studio e a interface do usuário que apresenta o plug-in de controle de origem. Isso é mais perceptível com operações de controle de origem avançadas.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Desvantagens para implementar um plug-in de controle de origem  
  
-   Recursos avançados, o usuário pode ver dois estilos diferentes de interfaces, levando a possível confusão.  
  
-   O plug-in de controle de origem é limitado ao modelo de controle de origem implicado a API de plug-in de controle de origem.  
  
-   A API de plug-in de controle de origem pode ser muito restritiva para alguns cenários de controle de origem.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantagens para implementar um plug-in de controle de origem  
  
-   O Visual Studio fornece todos os a interface do usuário para todas as operações de controle de origem básico para que o plug-in de controle de origem não tem que implementar a interface de usuário complexa.  
  
-   Devido a API estrita, o plug-in de controle de origem prontamente pode interagir com programas de controle de origem externa para fornecer a funcionalidade mais ampla; O Visual Studio, não importa muito bem como a funcionalidade de controle de origem é realizada, apenas que ela é realizada de acordo com a API de plug-in de controle de origem.  
  
-   É mais fácil de implementar um plug-in de um controle de origem VSPackage de controle de origem.  
  
## <a name="source-control-vspackage"></a>VSPackage de controle do código-fonte  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permite a integração total no Visual Studio com controle total da funcionalidade de controle de origem e uma substituição completa da interface de usuário de controle de origem fornecidos pelo Visual Studio. Um controle de origem VSPackage é registrado com o Visual Studio e fornece funcionalidade de controle de origem. Embora várias VSPackages de controle de origem pode ser registrado com o Visual Studio, apenas um deles pode ser ativo a qualquer momento. Um controle de origem VSPackage tem controle total sobre a aparência e a funcionalidade de controle de origem no Visual Studio enquanto estiver ativo. Todos os outros controle de origem VSPackages que podem ser registrados no sistema está inativo e não exibirá nenhuma interface do usuário em todos os.  
  
 Implementação de um controle de origem VSPackage requer uma estratégia "tudo ou nada". O criador de um controle de origem VSPackage deve investir uma quantidade significativa de esforço na implementação de um número de interfaces de controle de origem e novos elementos de interface do usuário (caixas de diálogo, menus e barras de ferramentas) para cobrir a funcionalidade de controle de origem inteiro. Consulte [criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md) para obter mais detalhes.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Desvantagens para implementar um VSPackage de controle do código-fonte  
  
-   O VSPackage deve implementar um número de interfaces complexas para integrar com êxito com o Visual Studio.  
  
-   O VSPackage deve fornecer todos os a interface do usuário necessário para o controle de origem; O Visual Studio não fornecem nenhuma assistência nessa área.  
  
-   Um controle de origem VSPackage está intimamente relacionado para o Visual Studio e não pode operar com programas autônomos, portanto a funcionalidade não pode ser facilmente compartilhada com uma versão externa do programa de controle de origem.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantagens para implementar um VSPackage de controle do código-fonte  
  
-   Como o VSPackage tem funcionalidade e controle total sobre o controle de origem da interface do usuário, o usuário é apresentado com uma interface uniforme para controle de origem.  
  
-   O VSPackage não está limitado a um modelo de controle de origem em particular.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de origem](../../extensibility/internals/source-control.md)   
 [Criando um controle de origem plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Novidades no controle do código-fonte](../../extensibility/internals/what-s-new-in-source-control.md)