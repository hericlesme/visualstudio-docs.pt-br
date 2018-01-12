---
title: 'Como: personalizar uma guia interna | Microsoft Docs'
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
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 251c1cf70ab1d528f65d558208f0f2d43e10388a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-built-in-tab"></a>Como personalizar uma guia interna
  Você pode adicionar grupos e controles a uma guia interna. Uma guia interna é um que já está na faixa de opções de um aplicativo do Microsoft Office. Por exemplo, o **dados** guia é uma guia interna no Excel. Quando você cria um grupo personalizado, ele é exibido por último na guia, mas você pode mover o grupo em qualquer lugar na guia.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Você pode adicionar grupos a uma guia interna, mas você não pode remover grupos internos de uma guia interna.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Para adicionar grupos a uma guia interna  
  
1.  Clique no arquivo de código da faixa de opções no **Solution Explorer**e, em seguida, clique em **Designer de exibição**.  
  
    > [!NOTE]  
    >  Se o arquivo de código da faixa de opções não aparecer na **Solution Explorer**, você deve adicionar um **item da faixa de opções** ao seu projeto. Consulte [como: personalizar a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Clique em qualquer guia no designer de faixa de opções e, em seguida, clique em **propriedades**.  
  
3.  No **propriedades** janela, expanda o **ControlId** propriedade e, em seguida, defina o **ControlIdType** propriedade **Office**.  
  
4.  Definir o **OfficeId** propriedade para o *identificação de controle* da guia interna que você deseja personalizar.  
  
     A ID do controle é o nome que identifica exclusivamente a guias, grupos e controles que são inseridos nos aplicativos do Microsoft Office.  
  
     Para obter uma lista de IDs de controle, consulte [arquivos de Ajuda do Office 2010: identificadores de controle de Interface do Office Fluent usuário](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Do **controles de faixa de opções do Office** guia do **caixa de ferramentas**, arraste a guia de grupos.  
  
    > [!NOTE]  
    >  Grupos internos não aparecem no designer. Portanto, a única maneira de determinar se você estiver trabalhando com uma guia interna é examinar o **ControlId** propriedade da guia.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Para posicionar os grupos em uma guia interna  
  
1.  No Designer de faixa de opções, selecione um grupo personalizado.  
  
2.  No **propriedades** janela, expanda o **posição** propriedade.  
  
3.  Definir o **PositionType** propriedade para o valor apropriado:  
  
    -   **BeforeOfficeId** posiciona o grupo antes de um grupo interno especificado.  
  
    -   **AfterOfficeId** posiciona o grupo depois de um grupo interno especificado.  
  
4.  Definir o **OfficeId** propriedade para a ID de controle de um grupo interno.  
  
     Para obter uma lista de IDs de controle, consulte [arquivos de Ajuda do Office 2010: identificadores de controle de Interface do Office Fluent usuário](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Passo a passo: Criando uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Passo a passo: Criando uma guia usando o XML da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Como: personalizar a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Como: alterar a posição de uma guia na faixa de opções](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Como: adicionar controles à exibição Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Como mostrar erros de interface do usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  