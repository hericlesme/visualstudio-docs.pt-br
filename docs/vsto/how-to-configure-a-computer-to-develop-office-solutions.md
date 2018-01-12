---
title: "Como: configurar um computador para desenvolver soluções do Office | Microsoft Docs"
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
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a6f920bbc6ce2767728a08172243969b688f3ee9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Como configurar um computador para desenvolver soluções do Office
  Para configurar um computador de desenvolvimento para que você pode usar as ferramentas de desenvolvedor do Microsoft Office no Visual Studio, siga as instruções neste tópico. Você deve ter privilégios administrativos no computador de desenvolvimento para executar essas etapas.  
  
### <a name="to-configure-the-development-computer"></a>Para configurar o computador de desenvolvimento  
  
1.  Instale uma versão do Visual Studio que inclui o Office developer tools. O Office developer tools é instalado por padrão. Se você personalizar a instalação do Visual Studio, selecionando quais recursos a serem instalados, verifique se **Microsoft Office Developer Tools** é selecionada durante a instalação. Para obter mais informações sobre as versões do Visual Studio que incluem o Office developer tools, consulte [Configurando um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Instale uma versão do Office que é compatível com as ferramentas de desenvolvedor do Office no Visual Studio. Para obter mais informações, consulte [Configurando um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Certifique-se de que você também instale os PIAs para a versão do Office que você instalar. Por padrão, os PIAs são instalados com o Office. Se você modificar a instalação do Office, verifique se o **suporte à programação do .NET** está selecionado para os aplicativos que você deseja como destino.  
  
3.  Se você tiver uma versão em inglês do Visual Studio, mas usa configurações diferentes do inglês do Windows, você pode instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pacote de idiomas para ver [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mensagens no mesmo idioma do Windows. Versões do Visual Studio instala automaticamente o pacote de idiomas. O pacote de idiomas está disponível na [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Consulte também  
 [O que há de novo no desenvolvimento do Office](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Guia de Introdução &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Como: instalar o Visual Studio Tools for Office Runtime redistribuível](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Como instalar assemblies de interoperabilidade primários do Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  