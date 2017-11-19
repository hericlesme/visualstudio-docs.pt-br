---
title: Arquitetura de suplementos do VSTO | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
ms.assetid: 978f102f-15c6-44e4-84e8-80b161408324
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9813add14da26049e5e32b9e060a146db4ce9afb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="architecture-of-vsto-add-ins"></a>Arquitetura de suplementos do VSTO
  Suplementos do VSTO criados usando as ferramentas de desenvolvedor do Office no Visual Studio têm recursos arquitetônicos que enfatizam a estabilidade e segurança e permitem que eles trabalham em conjunto com o Microsoft Office. Este tópico descreve os seguintes aspectos de suplementos do VSTO:  
  
-   [Noções básicas sobre os suplementos do VSTO](#UnderstandingAddIns)  
  
-   [Componentes de suplementos do VSTO](#AddinComponents)  
  
-   [Como os suplementos do VSTO trabalhar com aplicativos do Microsoft Office](#HowAddinsWork)  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Para obter informações gerais sobre como criar suplementos do VSTO, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) e [Introdução Programando suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a>Noções básicas sobre os suplementos do VSTO  
 Quando você usa as ferramentas de desenvolvedor do Office no Visual Studio para criar um suplemento do VSTO, você pode criar um assembly de código gerenciado que é carregado por um aplicativo do Microsoft Office. Depois que o assembly é carregado, o suplemento do VSTO pode responder a eventos que são gerados no aplicativo (por exemplo, quando um usuário clica em um item de menu). O suplemento do VSTO também pode chamar no modelo de objeto para automatizar e estender o aplicativo e ele pode usar qualquer uma das classes no [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 O assembly se comunica com componentes COM, do aplicativo por meio do assembly de interoperabilidade primária do aplicativo. Para obter mais informações, consulte [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md) e [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 Se vários suplementos do VSTO estão instalados para um aplicativo, cada suplemento do VSTO é carregado em um domínio de aplicativo diferente. Isso significa que um VSTO suplemento que se comporta incorretamente não pode fazer com que outros suplementos do VSTO falhar. Ele também ajuda a garantir que, quando o aplicativo for fechado, todos os suplemento do VSTO assemblies são descarregados da memória. Para obter mais informações sobre domínios de aplicativo, consulte [domínios de aplicativo](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Suplementos do VSTO que você cria usando as ferramentas de desenvolvedor do Office no Visual Studio são projetados para ser utilizada somente quando o host de aplicativo do Microsoft Office é iniciado por um usuário final. Se o aplicativo for iniciado por meio de programação (por exemplo, usando automação), o suplemento do VSTO pode não funcionar conforme o esperado.  
  
##  <a name="AddinComponents"></a>Componentes de suplementos do VSTO  
 Embora o assembly do suplemento do VSTO é o principal componente, há vários outros componentes que desempenham um papel importante em como os aplicativos do Microsoft Office descobrirem e carreguem suplementos do VSTO.  
  
### <a name="registry-entries"></a>Entradas do registro  
 Aplicativos do Microsoft Office descobrir suplementos do VSTO procurando um conjunto de entradas do registro. Para obter uma lista completa das entradas do registro usadas pelos suplementos do VSTO, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Quando você cria sua solução, o Visual Studio cria todas as entradas do registro necessárias no computador de desenvolvimento para que você possa depurar e executar o suplemento do VSTO. Para obter mais informações, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
 Se você usar o ClickOnce para implantar sua solução, o programa de instalação gerado pelo processo de publicação automaticamente cria as chaves do registro no computador do usuário final. Para obter mais informações, consulte [implantar uma solução Office pelo ClickOnce usando](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### <a name="deployment-manifest-and-application-manifest"></a>O manifesto de implantação e o manifesto do aplicativo  
 Suplementos do VSTO usam manifestos de aplicativo e manifestos de implantação para identificar e carregar a versão mais atual do assembly do suplemento do VSTO. A implantação do manifesto aponta para o manifesto do aplicativo atual. O manifesto do aplicativo aponta para o assembly do suplemento do VSTO e especifica a classe de ponto de entrada para executar no assembly. Para obter mais informações, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>O Visual Studio Tools for Office Runtime  
 Para executar suplementos do VSTO que são criados usando as ferramentas de desenvolvedor do Office no Visual Studio, os computadores do usuário final devem ter o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instalado. O tempo de execução inclui componentes não gerenciados e um conjunto de assemblies gerenciados. Os componentes gerenciados carregar o assembly do suplemento do VSTO. Os módulos gerenciados fornecem o modelo de objeto que usa o código de suplemento do VSTO para automatizar e estender o aplicativo host.  
  
 Para obter mais informações, consulte [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a>Como os suplementos do VSTO trabalhar com aplicativos do Microsoft Office  
 Quando um usuário inicia um aplicativo do Microsoft Office, o aplicativo usa o manifesto de implantação e o manifesto do aplicativo para localizar e carregar a versão mais atual do assembly do suplemento do VSTO. A ilustração a seguir mostra a arquitetura básica desses suplementos do VSTO.  
  
 ![Arquitetura de suplemento do office de 2007](../vsto/media/office07addin.png "arquitetura de suplemento do Office de 2007")  
  
> [!NOTE]  
>  Em soluções do Office que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], soluções chamarão o modelo de objeto do aplicativo host por usando informações de tipo PIA são inseridas no assembly solução, em vez de chamar o PIA diretamente. Para obter mais informações, consulte [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Processo de carregamento  
 Quando um usuário inicia um aplicativo, ocorrem as seguintes etapas:  
  
1.  O aplicativo verifica o registro para entradas que identificam os suplementos do VSTO que foram criados usando as ferramentas de desenvolvedor do Office no Visual Studio.  
  
2.  Se o aplicativo encontrar essas entradas do registro, o aplicativo carrega VSTOEE.dll, que carrega VSTOLoader.dll. Eles são gerenciados DLLs que são os componentes de carregador para o Visual Studio 2010 Tools for Office Runtime. Para obter mais informações, consulte [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  VSTOLoader.dll carrega o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] e inicia a parte gerenciada do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verifica se há atualizações de manifesto e baixa os manifestos de aplicativo e implantação mais recentes.  
  
5.  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] executa uma série de verificações de segurança. Para obter mais informações, consulte [Protegendo soluções do Office](../vsto/securing-office-solutions.md).  
  
6.  Se o suplemento do VSTO é confiável para ser executado, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usa o manifesto de implantação e o manifesto do aplicativo para verificar se há atualizações do assembly. Se uma nova versão do assembly está disponível, o tempo de execução baixa a nova versão do assembly para o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] cache no computador cliente. Para obter mais informações, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
7.  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria um novo domínio de aplicativo no qual carregar o assembly do suplemento do VSTO.  
  
8.  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] carrega o assembly do suplemento do VSTO para o domínio de aplicativo.  
  
9. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> método o VSTO Add-in, se você o tiver substituído.  
  
     Opcionalmente, você pode substituir esse método para expor um objeto no seu suplemento do VSTO para outras soluções do Microsoft Office. Para obter mais informações, consulte [chamando código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método o VSTO Add-in, se você o tiver substituído.  
  
     Opcionalmente, você pode substituir esse método para estender um recurso do Microsoft Office, retornando um objeto que implementa uma interface de extensibilidade. Para obter mais informações, consulte [personalização da interface do usuário recursos por usando Interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] torna separar chamadas para o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método para cada interface de extensibilidade com suporte pelo aplicativo host. Embora a primeira chamada para o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método geralmente acontece antes da chamada para o `ThisAddIn_Startup` método, o suplemento do VSTO não deve ser feita suposições sobre quando o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método será chamado ou quantas vezes ele será chamado.  
  
11. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o `ThisAddIn_Startup` método no seu suplemento do VSTO. Esse método é o manipulador de eventos padrão para o <xref:Microsoft.Office.Tools.AddInBase.Startup> evento. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)   
 [Ferramentas do Visual Studio para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Desenvolvendo soluções do Office](../vsto/developing-office-solutions.md)   
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)  
  
  