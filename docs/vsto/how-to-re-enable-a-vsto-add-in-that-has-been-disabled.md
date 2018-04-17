---
title: 'Como: habilitar novamente um suplemento do VSTO que tenha sido desabilitado | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25344d23e0c9f1d6d237d008b0f6b18372490d04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Como habilitar novamente um suplemento do VSTO que tenha sido desabilitado
  Aplicativos do Microsoft Office podem desabilitar suplementos do VSTO que se comportam de forma inesperada. Se um aplicativo não carregar o suplemento do VSTO quando você tentar depurá-lo, o aplicativo pode ter desabilitado rígido ou software desabilitado o suplemento do VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Suplementos do VSTO de disco rígido-desabilitado  
 Desabilitar o disco rígido pode ocorrer quando um suplemento do VSTO faz com que o aplicativo seja encerrado inesperadamente. Também pode ocorrer no computador de desenvolvimento se você parar o depurador enquanto o <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos no seu suplemento do VSTO está em execução.  
  
#### <a name="to-re-enable-a-vsto-add-in"></a>Para habilitar novamente um suplemento do VSTO  
  
1.  No aplicativo, clique no **arquivo** guia.  
  
2.  Clique o *ApplicationName* **opções** botão.  
  
3.  No painel de categorias, clique em **suplementos**.  
  
4.  No painel de detalhes, verifique se o suplemento do VSTO aparece no **suplementos de aplicativo desabilitados** lista.  
  
     O **nome** coluna especifica o nome do assembly e o **local** coluna especifica o caminho completo do manifesto do aplicativo.  
  
5.  No **gerenciar** , clique em **itens**e, em seguida, clique em **vá**.  
  
6.  Selecione o suplemento do VSTO e clique em **habilitar**.  
  
7.  Clique em **Fechar**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Suplementos do VSTO soft-desabilitado  
 Desabilitar o software pode ocorrer quando um suplemento do VSTO produz um erro que não faz com que o aplicativo fechar inesperadamente. Por exemplo, um aplicativo flexível pode desabilitar um suplemento do VSTO se ele lança uma exceção não tratada durante a <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos está em execução.  
  
> [!NOTE]  
>  Quando você reabilitar um suplemento do VSTO do soft-desabilitado, o aplicativo imediatamente tenta carregar o suplemento do VSTO. Se o problema que causou inicialmente o aplicativo para desabilitar o software de suplemento do VSTO não foi corrigido, o aplicativo flexível desabilitará o suplemento do VSTO novamente.  
  
#### <a name="to-re-enable-an-vsto-add-in"></a>Para habilitar novamente um suplemento do VSTO  
  
1.  No aplicativo, clique no **arquivo** guia.  
  
2.  Clique o *ApplicationName* **opções** botão.  
  
3.  No painel de categorias, clique em **suplementos**.  
  
4.  No painel de detalhes, verifique se o suplemento do VSTO aparece no **suplementos de aplicativo inativos** lista.  
  
     O **nome** coluna especifica o nome do assembly e o **local** coluna especifica o caminho completo do manifesto do aplicativo.  
  
5.  No **gerenciar** , clique em **suplementos COM**e, em seguida, clique em **vá**.  
  
6.  No **suplementos COM** caixa de diálogo, selecione a caixa de seleção ao lado de desabilitado VSTO suplemento.  
  
7.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Depurando projetos do Office](../vsto/debugging-office-projects.md)   
 [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md)  
  
  