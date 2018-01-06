---
title: "Passo a passo: Baixando Assemblies satélite por demanda com a implantação do ClickOnce usando o Designer de API | Microsoft Docs"
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
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b96665bb2d9e6395d32d85344e2fe2cdabc21951
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Instruções passo a passo: baixando assemblies satélite por demanda com a API de implantação do ClickOnce usando o designer
Aplicativos de formulários do Windows podem ser configurados para várias culturas com o uso de assemblies de satélite. Um *assembly satélite* é um assembly que contém recursos de aplicativos para uma cultura diferente de cultura do padrão do aplicativo.  
  
 Conforme discutido em [Localizando os aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md), você pode incluir vários assemblies de satélite para várias culturas dentro do mesmo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação. Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] baixará todos os assemblies satélite em sua implantação para o computador cliente, embora um único cliente provavelmente exigirá assembly satélite apenas um.  
  
 Este passo a passo demonstra como marcar seus assemblies de satélite como opcional e baixar apenas o assembly precisa de um computador cliente para suas configurações de cultura atual.  
  
> [!NOTE]
>  Para fins de teste, os exemplos de código a seguir programaticamente definem a cultura `ja-JP`. Consulte a seção "Próximas etapas" mais adiante neste tópico para obter informações sobre como ajustar esse código para um ambiente de produção.  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>Marcar assemblies de satélite como opcional  
  
1.  Criar o projeto. Isso irá gerar assemblies de satélite para todas as culturas que você está localizando para.  
  
2.  Clique com botão direito no nome do projeto no Gerenciador de soluções e, em seguida, clique em **propriedades**.  
  
3.  Clique o **publicar** guia e, em seguida, clique em **arquivos de aplicativo**.  
  
4.  Selecione o **Mostrar todos os arquivos** caixa de seleção para exibir os assemblies satélite. Por padrão, todos os assemblies de satélite serão incluídos em sua implantação e ficarão visíveis na caixa de diálogo.  
  
     Um assembly satélite terá um nome no formato *isoCode*\ApplicationName.resources.dll, onde *isoCode* é um identificador de idioma no formato RFC 1766.  
  
5.  Clique em **novo...**  no **grupo de Download** lista para cada identificador de idioma. Quando solicitado a fornecer um nome de grupo de download, insira o identificador de idioma. Por exemplo, para um assembly satélite japonês, você deve especificar o nome do grupo de download `ja-JP`.  
  
6.  Fechar o **arquivos de aplicativo** caixa de diálogo.  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Para baixar os assemblies satélite por demanda em c# #
  
1.  Abra o arquivo Program.cs. Se você não vir esse arquivo no Gerenciador de soluções, selecione o seu projeto e, no **projeto** menu, clique em **Mostrar todos os arquivos**.  
  
2.  Use o código a seguir para baixar o assembly satélite e iniciar o aplicativo.  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Para baixar os assemblies satélite por demanda no Visual Basic  
  
1.  No **propriedades** janela do aplicativo, clique no **aplicativo** guia.  
  
2.  Na parte inferior da página da guia, clique em **exibir eventos do aplicativo**.  
  
3.  Adicione a seguir importa para o início do arquivo Project.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Adicione o seguinte código para o `MyApplication` classe.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## <a name="next-steps"></a>Próximas etapas  
 Em um ambiente de produção, você provavelmente precisará remover a linha nos exemplos de código que define <xref:System.Threading.Thread.CurrentUICulture%2A> para um valor específico, como cliente máquinas serão tem o valor correto definida por padrão. Quando seu aplicativo é executado em um computador cliente em japonês, por exemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` por padrão. Definir programaticamente o valor é uma boa maneira de testar seus assemblies satélites antes de implantar seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Baixando Assemblies satélite por demanda com a API de implantação do ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Localizando aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md)
