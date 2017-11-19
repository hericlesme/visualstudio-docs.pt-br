---
title: "Como: instalar o Visual Studio Tools for Office Runtime redistribuível | Microsoft Docs"
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
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: "94"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8d3439a98a445761a8d357d9b4bef631da034943
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Como instalar o redistribuível de tempo de execução do Visual Studio Tools para Office
  O Visual Studio 2010 Tools para Office Runtime deve ser instalado em cada computador que executa soluções são criadas usando as ferramentas de desenvolvedor do Microsoft Office em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. O tempo de execução é instalado automaticamente quando você instala o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e o Microsoft Office. Para obter mais informações, consulte [Visual Studio Tools para Office cenários de instalação de tempo de execução](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Talvez seja necessário que você siga as instruções de instalação manual abaixo nas seguintes situações:  
  
-   Você precisa instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] em um servidor. Por exemplo, você deseja usar o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe para gerenciar soluções de nível de documento em um servidor.  
  
-   Você precisa instalar o tempo de execução em um computador que já tenha todos os outros pré-requisitos de soluções do Office instalados.  
  
    > [!NOTE]  
    >  Você deve ser um administrador no computador de desenvolvimento para instalar o .NET Framework e o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
### <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Para instalar o Visual Studio Tools for Office runtime  
  
1.  Instalar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.  
  
    -   Para baixar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consulte [Microsoft .NET Framework 4 (instalador da Web)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Para baixar o [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consulte [(instalador da Web) do Microsoft .NET Framework 4 Client Profile](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Para baixar o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Execute vstor_redist.exe para instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Você pode baixar esses arquivos de instalação do [Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Os pré-requisitos para o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] corresponde os pré-requisitos para o .NET Framework.  
  
     O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]inclui pacotes de idiomas. Se a instalação do Windows é definida para um idioma diferente do inglês, você pode exibir mensagens de tempo de execução no mesmo idioma em que você usa para Windows. Da mesma forma, se os usuários finais instalam o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e, em seguida, execute as soluções em instalações do Windows que são definidas para um idioma diferente do inglês, mensagens de tempo de execução serão exibido no mesmo idioma do Windows. Em alguns casos, talvez seja necessário pacotes de idioma adicionais. Por exemplo, talvez seja necessário pacotes de idioma adicionais se sua cópia do Windows usa mais de uma configuração de idioma, ou se você alternar para outro idioma, depois que você já tiver instalado o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Você pode encontrar os pacotes de idiomas em [Microsoft Visual Studio 2010 Tools para o pacote de idiomas do Microsoft Office System (versão 4.0 Runtime)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Introdução &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configurando um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Como: configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Como: instalar Assemblies de interoperabilidade primários do Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Gerenciando documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)  
  
  