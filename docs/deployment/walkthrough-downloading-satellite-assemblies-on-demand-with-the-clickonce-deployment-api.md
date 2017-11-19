---
title: "Passo a passo: Baixando Assemblies satélite por demanda com a API de implantação do ClickOnce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: c3c3b817975304a41181b5e346a32b0b95c4258e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Instruções passo a passo: baixando assemblies satélite por demanda com a API de implantação do ClickOnce
Aplicativos de formulários do Windows podem ser configurados para várias culturas com o uso de assemblies de satélite. Um *assembly satélite* é um assembly que contém recursos de aplicativos para uma cultura diferente de cultura do padrão do aplicativo.  
  
 Conforme discutido em [Localizando os aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md), você pode incluir vários assemblies de satélite para várias culturas dentro do mesmo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação. Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] baixará todos os assemblies satélite em sua implantação para o computador cliente, embora um único cliente provavelmente exigirá assembly satélite apenas um.  
  
 Este passo a passo demonstra como marcar seus assemblies de satélite como opcional e baixar apenas o assembly precisa de um computador cliente para suas configurações de cultura atual. O procedimento a seguir usa as ferramentas disponíveis no [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Você também pode executar esta tarefa no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consulte também [passo a passo: baixando Assemblies satélite por demanda com o ClickOnce implantação API usando o Designer](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) ou [passo a passo: baixando Assemblies satélite por demanda com a API de implantação do ClickOnce Usando o Designer](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  Para fins de teste, o exemplo de código a seguir programaticamente define a cultura `ja-JP`. Consulte a seção "Próximas etapas" mais adiante neste tópico para obter informações sobre como ajustar esse código para um ambiente de produção.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você saiba como adicionar recursos localizados para seu aplicativo usando o Visual Studio. Para obter instruções detalhadas, consulte [passo a passo: Localizando Windows Forms](https://msdn.microsoft.com/en-us/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Para baixar os assemblies satélite por demanda  
  
1.  Adicione o seguinte código ao seu aplicativo para habilitar o download sob demanda de assemblies de satélite.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Gerar assemblies de satélite para seu aplicativo usando [Resgen.exe (gerador de arquivo)](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Gerar um manifesto de aplicativo ou abrir o manifesto do aplicativo existente, usando MageUI.exe. Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe (ferramenta de edição, cliente gráfico e geração de manifesto)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
4.  Clique o **arquivos** guia.  
  
5.  Clique o **reticências** botão (**...** ) e selecione o diretório que contém todos os assemblies e arquivos, incluindo os assemblies satélite geradas usando Resgen.exe de seu aplicativo. (Um assembly satélite terá um nome no formato *isoCode*\ApplicationName.resources.dll, onde *isoCode* é um identificador de idioma no formato RFC 1766.)  
  
6.  Clique em **popular** para adicionar os arquivos para a sua implantação.  
  
7.  Selecione o **opcional** caixa de seleção para cada assembly satélite.  
  
8.  Defina o campo de grupo para cada assembly satélite para o identificador de idioma ISO. Por exemplo, para um assembly satélite japonês, você deve especificar um nome de grupo de download de `ja-JP`. Isso permitirá que o código que você adicionou na etapa 1 para baixar o assembly satélite, dependendo o usuário <xref:System.Threading.Thread.CurrentUICulture%2A> configuração de propriedade.  
  
## <a name="next-steps"></a>Próximas etapas  
 Em um ambiente de produção, você provavelmente precisará remover a linha no código de exemplo que define <xref:System.Threading.Thread.CurrentUICulture%2A> para um valor específico, como cliente máquinas serão tem o valor correto definida por padrão. Quando seu aplicativo é executado em um computador cliente em japonês, por exemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` por padrão. Definir esse valor por meio de programação é uma boa maneira de testar seus assemblies satélites antes de implantar seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Localizando aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md)