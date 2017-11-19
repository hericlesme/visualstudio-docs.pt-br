---
title: "Configurando um computador para desenvolver soluções do Office | Microsoft Docs"
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
helpviewer_keywords: Office development in Visual Studio, installing tools
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: "97"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d3e0b354375d6116a1bcc0cc2b0d69ecc2f16b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Configurando um computador para desenvolver soluções do Office
  Para criar suplementos do VSTO e personalizações para o Microsoft Office, instale uma versão com suporte do Visual Studio, o .NET Framework e o Microsoft Office.  
  
|Software|Versões com suporte|  
|--------------|------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)]**Importante:** você deve selecionar a caixa de seleção do Microsoft Office Developer Tools durante a instalação.|  
|.NET Framework|-O .NET Framework 4 ou posterior.|  
|Microsoft Office|<ul><li>Qualquer edição do pacote do Office, incluindo o Office Professional Plus para o Office 365.</li><li>Qualquer uma das aplicações autônomas seguintes:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 e Office 2010 apenas)</li><li>Outlook</li><li>PowerPoint</li><li>Projeto</li><li>Visio</li><li>Palavra</li></ul></li></ul><br /> O Visual Basic for Applications (VBA) deve ser instalado como parte do Office. **Importante:** clique para executar versões de aplicativos do Office 2010 não têm suporte.|  
  
 Para obter etapas detalhadas de instalação, consulte [como: configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Se os modelos de projeto não são exibidos ou não funcionam no Visual Studio  
 Se você instalar uma versão com suporte do Visual Studio, o .NET Framework e o Microsoft Office, mas os modelos de projeto do Office não aparecem no Visual Studio **novo projeto** caixa de diálogo, ou você recebe um erro ao tentar usar um, Verifique o seguinte:  
  
-   Certifique-se de que o Microsoft Office Developer Tools esteja instalado no computador.  
  
     O Office Developer Tools é um componente opcional do Visual Studio, mas geralmente é instalado automaticamente junto com o Visual Studio. Se você personalizar a instalação do Visual Studio especificando quais recursos a serem instalados, certifique-se de que você escolha **Microsoft Office Developer Tools** durante a instalação para instalar as ferramentas.  
  
     Para garantir que essas ferramentas são instaladas, inicie o programa de instalação do Visual Studio e escolha o **modificar** botão. Selecione o **Microsoft Office Developer Tools** caixa de seleção e, em seguida, escolha o **atualização** botão.  
  
-   Certifique-se de que você não estiver executando uma versão do Office que foi entregue por clique para executar. Consulte [como: verificar se o Outlook é um aplicativo clique para executar em um computador](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Certifique-se de que você está executando apenas uma versão do Microsoft Office.  
  
 Se você continuar tendo problemas, consulte [suporte adicional para erros em soluções do Office](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Introdução &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Como: configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Como: instalar o Visual Studio Tools for Office Runtime redistribuível](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Como: instalar Assemblies de interoperabilidade primários do Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Funcionalidades disponibilizadas pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md)  
  
  