---
title: "Como: incluir arquivos usando um módulo | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ebefc0420eba48fdc53e68482a96a575111e536f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-include-files-by-using-a-module"></a>Como: Incluir arquivos usando um módulo
  *Módulos* (não deve ser confundido com [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) são contêineres que permitem que você implantar arquivos como páginas mestras ASPX, arquivos de texto ou imagens no SharePoint.  
  
 Você pode optar por implantar um arquivo em uma biblioteca de documentos ou como um arquivo normal (por exemplo, default.aspx) fora de uma biblioteca de documentos. Para adicionar um arquivo a uma biblioteca de documentos, especifique `Type="GhostableInLibrary"` como um atributo no **arquivo** elemento. Esta configuração instrui o SharePoint para criar um item de lista para ir com o arquivo quando ele é adicionado à biblioteca. Para implantar um arquivo fora de uma biblioteca de documentos, especifique `Type="Ghostable"` ou omita apenas o **tipo** atributo.  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>Adicionando um módulo a uma solução do SharePoint  
  
#### <a name="to-add-a-module"></a>Para adicionar um módulo  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra ou crie um projeto do SharePoint.  
  
     Para obter mais informações, consulte [projeto do SharePoint e modelos de Item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Em **Solution Explorer**, escolha o nó do projeto e, em seguida, na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é aberta.  
  
3.  Na lista de modelos do SharePoint, escolha o **módulo** modelo e, em seguida, escolha o **adicionar** botão.  
  
     Esta etapa cria um nó no projeto chamado Module1.  
  
4.  Em Module1, exclua o arquivo txt.  
  
     Txt está incluído em todos os novos módulos fins por exemplo e não é necessária. (Observe que excluir o arquivo também remove a entrada do arquivo Elements XML do módulo.)  
  
5.  Se desejar que os arquivos para implantar em uma estrutura de pasta específica no SharePoint, criar essas pastas em Module1 em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] escolhendo o nó Module1 e, em seguida, na barra de menus, escolha **projeto**, **novo Pasta**.  
  
6.  Escolha a pasta na qual você deseja adicionar o arquivo e, em seguida, na barra de menus, escolha **projeto**, **Add Existing Item**.  
  
7.  Escolha um ou mais arquivos que você deseja implantar no SharePoint e, em seguida, escolha o **adicionar** botão.  
  
     Quando você adiciona um arquivo ao projeto, uma entrada para ele é adicionada automaticamente para o arquivo do módulo Elements. Quando o projeto é implantado, os arquivos são copiados para o servidor do SharePoint, relativo ao diretório raiz do projeto, o que é especificado pelo **arquivo** do elemento **Url** atributo, como `Url="Module1/New Folder/SomeFile.doc`. Se você quiser alterar o local de implantação de um arquivo, mova-lo para outra pasta **Solution Explorer** ou alterar seu **Url** configuração.  
  
8.  Para todos os arquivos que você deseja exibir em uma biblioteca de documentos, acrescente o `Type="GhostableInLibrary"` atributo de entrada na Elements. Por exemplo,  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Implante o projeto.  
  
     Copie os arquivos para os locais especificados no SharePoint.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  