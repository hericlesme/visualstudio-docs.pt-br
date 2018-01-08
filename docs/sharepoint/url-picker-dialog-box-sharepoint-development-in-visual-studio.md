---
title: "Caixa de diálogo Seletor de URL (desenvolvimento do SharePoint no Visual Studio) | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c475b44b15b206464e2a910cc410964906706bd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Caixa de diálogo Seletor de URL (desenvolvimento do SharePoint no Visual Studio)
  Na caixa de diálogo Seletor de URL, você pode escolher arquivos, como arquivos de página mestra ou arquivos de imagem que estão localizados em seu projeto ou no servidor local que está executando o SharePoint.  
  
 Essa caixa de diálogo aparece quando você tem a opção de escolher um arquivo para definir uma propriedade. Você pode abrir essa caixa de diálogo, escolhendo o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) ao lado de várias propriedades no **propriedades** janela. Botão de reticências também aparece como uma IntelliSense prompt quando você atribui valores a determinados atributos no **fonte** visualização do designer.  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Pastas de projeto**  
 Exibe uma lista das pastas definida no projeto ou em um servidor local que está executando o SharePoint. Escolha o botão de expansão para mostrar as subpastas.  
  
 Expanda o **projeto** nó para escolher os arquivos em seu projeto. Apareçam como selecionável na caixa de diálogo, arquivos em seu projeto devem atender aos seguintes critérios:  
  
-   O arquivo deve estar contido em uma pasta mapeada.  
  
-   O arquivo deve ser adicionado ao pacote de solução.  
  
-   O arquivo não pode ser localizado em outro projeto.  
  
 Se você quiser fazer referência a arquivos que não atendem a esses critérios, você precisa digitar o caminho do arquivo manualmente.  
  
 Expanda o **Server** nó para escolher os arquivos que estão localizados no servidor local que está executando o SharePoint. Para aparecer como selecionável na caixa de diálogo, esses arquivos devem atender aos seguintes critérios:  
  
-   O arquivo deve estar localizado em uma das seguintes pastas mapeadas: **imagens**, **Layouts**, ou **ControlTemplates**.  
  
-   O arquivo não pode ser localizado no banco de dados de conteúdo do SharePoint.  
  
 Se você quiser fazer referência a arquivos que não atendem a esses critérios, você precisa digitar o caminho do arquivo manualmente.  
  
 **Conteúdo da pasta**  
 Exibe uma lista de arquivos na pasta selecionada. Escolha um arquivo e, em seguida, escolha o **Okey** botão para fechar a caixa de diálogo e enviar a seleção para o processo que o chamou.  
  
 **Arquivos do tipo**  
 Permite que você escolha em uma lista de arquivos que são apropriados para a tarefa que você está executando.  
  
## <a name="see-also"></a>Consulte também  
 [Criando páginas de aplicativo do SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Criando Web Parts do SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
  