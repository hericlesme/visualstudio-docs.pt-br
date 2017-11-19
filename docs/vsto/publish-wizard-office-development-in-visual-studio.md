---
title: Publicar o Assistente (desenvolvimento do Office no Visual Studio) | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8eeb0a002e2d62b9066165a99ce474cf7a01a88f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Assistente de Publicação (desenvolvimento do Office no Visual Studio)
  Use o **Assistente de publicação** para copiar arquivos de solução para um local especificado, crie os arquivos de manifesto e crie um programa de instalação.  
  
 Para acessar esse assistente, no **criar** menu, escolha **publicar** *SolutionName*. Você também pode acessar o **Assistente de publicação** de **Gerenciador de soluções**. Abra o menu de atalho para o nó do projeto e escolha **publicar**.  
  
 As seções a seguir descreve uma página do assistente.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>Onde você deseja publicar o aplicativo?  
 **Especifique o local para publicar este aplicativo**  
 Necessário. O local de publicação é o diretório onde o **Assistente de publicação** copia os arquivos de solução, como os manifestos, assemblies, certificados temporários e outros arquivos da compilação. Você deve ter acesso de gravação a esse diretório.  
  
 Digite o local como um caminho de disco, compartilhamento de arquivos, site FTP ou URL do site ou clique o **procurar** botão para procurar o local. O caminho pode ser nos seguintes formatos:  
  
-   Um caminho relativo ou absoluto no formato padrão do Windows, como C:\Deploy\MyApplication ou \MyApplication.  
  
-   Um caminho de convenção de nomenclatura Universal (UNC), como \\\ServerName\MyApplication\\.  
  
-   Uma URL de um site, como http://www.microsoft.com/MyApplication.  
  
 Por padrão, o local de publicação é *http://localhost/projectname/* se tiver instalado o IIS ou o diretório Publish se você fizer não tem o IIS instalado.  
  
> [!NOTE]  
>  Existem considerações mais se o computador de destino está executando o Windows Vista. Você deve ser um administrador no computador Windows Vista para usar a opção de local de publicação. Além disso, o local padrão é sempre o *publicar\\*  diretório, independentemente se você tiver o IIS instalado.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>O que é o caminho de instalação padrão em computadores de usuário final?  
 O caminho de instalação é opcional. Se preferir, você pode definir o caminho de instalação mais tarde. Para obter detalhes, consulte [como: alterar o caminho de instalação de uma solução do Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 O caminho de instalação é o diretório do qual o usuário final instalará a personalização. Também é o caminho que a solução usará para verificar as atualizações. O **Assistente de publicação** não implanta a solução para esse local, a menos que o caminho é o mesmo que você digitou no **especificar o local para publicar este aplicativo** caixa na página anterior.  
  
 **De um site da Web**  
 Especifique a URL que os usuários finais seguirá para instalar a solução.  
  
 **De um compartilhamento de arquivo ou caminho UNC**  
 Especifique o caminho UNC que os usuários finais seguirá para instalar a solução.  
  
 **De um CD-ROM ou DVD-ROM**  
 Essa opção não exige um caminho de instalação.  
  
 O Visual Studio não gravar o CD ou DVD. Você deve copiar a saída para um CD ou DVD manualmente.  
  
## <a name="see-also"></a>Consulte também  
 [Implantando uma solução do Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Publicar página, Designer de projeto &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)  
  
  