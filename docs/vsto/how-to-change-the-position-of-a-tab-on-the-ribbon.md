---
title: "Como: alterar a posição de uma guia na faixa de opções | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 5016651a6cc4f1316536c22d555a65aaba64b788
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Como alterar a posição de uma guia na faixa de opções
  Você pode alterar a ordem das guias personalizadas em uma faixa de opções usando o **guia Editor de coleção**. Você pode posicionar guias personalizadas antes ou depois de uma guia interna na faixa de opções. Uma guia interna é um que já está na faixa de opções de um aplicativo do Microsoft Office. Por exemplo, o **dados** guia é uma guia interna no Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Para alterar a ordem das guias na faixa de opções  
  
1.  Selecione o arquivo de código da faixa de opções (arquivo. vb ou. cs) no **Gerenciador de soluções**.  
  
2.  Sobre o **exibição** menu, clique em **Designer**.  
  
3.  Clique com botão direito do Designer de faixa de opções e, em seguida, clique em **propriedades**.  
  
4.  No **propriedades** janela, selecione o **guias** propriedade e, em seguida, clique no botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET para dispositivos móveis Elipse de Designer")).  
  
     O **guia Editor de coleção** é exibida.  
  
5.  No **guia Editor de coleção**, no **membros** lista, selecione a guia que você deseja mover e clique em cima ou para baixo nas setas para alterar a ordem de tabulação.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Para posicionar uma guia antes ou depois de uma guia interna na faixa de opções  
  
1.  No Designer de faixa de opções, selecione uma guia personalizada.  
  
2.  No **propriedades** janela, expanda o **ControlId** propriedade e, em seguida, verifique se o valor da **ControlIdType** está definida como **personalizado**.  
  
3.  No **propriedades** janela, expanda o **posição** propriedade.  
  
4.  Definir o **PositionType** propriedade para o valor apropriado:  
  
    -   **BeforeOfficeId** posiciona o grupo antes de uma guia interna especificada.  
  
    -   **AfterOfficeId** posiciona o grupo depois de uma guia interna especificada.  
  
5.  Definir o **OfficeId** propriedade para a ID de controle de uma guia interna.  
  
     Para obter uma lista de IDs de controle, consulte [arquivos de Ajuda do Office 2010: identificadores de controle de Interface do Office Fluent usuário](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Passo a passo: Criando uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Instruções passo a passo: criando uma guia personalizada usando o XML da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  