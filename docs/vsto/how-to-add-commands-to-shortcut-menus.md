---
title: 'Como: adicionar comandos a Menus de atalho | Microsoft Docs'
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
- Office menus, creating
- Office development in Visual Studio, context menus
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa5578a25b6bb877f241b9a5c8b7ccd876e7b773
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Como adicionar comandos a menus de atalho
  Este tópico demonstra como adicionar comandos ao menu de atalho em um aplicativo do Office usando um suplemento do VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Para adicionar comandos a menus de atalho do Office  
  
1.  Adicionar um **XML da faixa de opções** item a um nível de documento ou de um projeto de suplemento do VSTO. Para obter mais informações, consulte [como: obter iniciado Personalizando a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md). No  
  
2.  **Gerenciador de soluções**, selecione **ThisAddin.cs** ou **ThisAddIn**.  
  
3.  Na barra de menus, escolha **Exibir**, **Código**.  
  
     O **ThisAddin** arquivo de classe é aberto no Editor de códigos.  
  
4.  Adicione o seguinte código para o **ThisAddin** classe. Esse código substitui o método CreateRibbonExtensibilityObject e retorna a classe de XML da faixa de opções para o aplicativo do Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  Em **Solution Explorer**, selecione o arquivo XML da faixa de opções. Por padrão, o arquivo XML da faixa de opções é denominado Ribbon1.  
  
6.  Na barra de menus, escolha **Exibir**, **Código**.  
  
     O arquivo de xml da faixa de opções é aberto no Editor de códigos.  
  
7.  No Editor de códigos, adicione o XML que descreve o menu de atalho e o controle que você deseja adicionar no menu de atalho.  
  
     O exemplo a seguir adiciona um botão, um menu e um controle de galeria no menu de atalho para um documento do word. A ID de controle de neste menu de atalho é ContextMenuText. Para obter uma lista de controle de atalho do Office 2010 IDs, consulte [arquivos de Ajuda do Office 2010: identificadores de controle de Interface do Office Fluent usuário](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  Em **Solution Explorer**, escolha **MyRibbon.cs** ou **MyRibbon.vb**.  
  
9. Adicionar a um método de retorno de chamada para o `Ribbon1` classe para cada controle que você deseja manipular.  
  
     Os seguintes identificadores de método de retorno de chamada de **meu botão** botão. Esse código adiciona uma cadeia de caracteres para o documento ativo no local atual do cursor.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Passo a passo: Criando Menus de atalho para indicadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Personalizando Menus de contexto no Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  