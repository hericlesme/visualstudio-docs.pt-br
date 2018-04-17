---
title: 'Como: exibir a guia Desenvolvedor na faixa de opções | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9921c10d8a886eb4051b3d5f3d8392ddc77c2da7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Como mostrar a guia Desenvolvedor na faixa de opções
  Para acessar o **desenvolvedor** guia na faixa de opções de um aplicativo do Office, você deve configurá-lo para mostrar a guia porque ele não aparece por padrão. Por exemplo, você deve mostrar guia se você deseja adicionar um <xref:Microsoft.Office.Tools.Word.GroupContentControl> para uma personalização de nível de documento para Word.  
  
> [!NOTE]  
>  Este guia se aplica ao Office 2010 ou posteriores aplicativos somente. Se você deseja mostrar este guia do 2007 Microsoft Office System, consulte a seguinte versão deste tópico [como: Mostrar a guia Desenvolvedor na faixa de opções](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Acesso não tem um **desenvolvedor** guia.  
  
### <a name="to-show-the-developer-tab"></a>Para mostrar a guia do desenvolvedor  
  
1.  Inicie qualquer um dos aplicativos do Office com suporte neste tópico. Consulte o **aplica-se a:** Observação neste tópico.  
  
2.  Sobre o **arquivo** guia, escolha o **opções** botão.  
  
     A figura a seguir mostra o **arquivo** guia e **opções** botão no Office 2010.  
  
     ![Escolher o arquivo, as opções no Outlook 2010](../vsto/media/vsto-office-file-tab.png "escolhendo o arquivo, as opções no Outlook 2010")  
  
     A figura a seguir mostra o **arquivo** guia no Office 2013.  
  
     ![Na guia do arquivo no Outlook 2013](../vsto/media/vsto-office2013-filetab.png "guia o arquivo no Outlook 2013")  
  
     A figura a seguir mostra o **opções** botão no Office 2013.  
  
     ![O botão de opções no Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "botão as opções no Outlook 2013 Preview")  
  
3.  No *ApplicationName * opções** caixa de diálogo caixa, escolha o **personalizar faixa de opções** botão.  
  
     A figura a seguir mostra o **opções** caixa de diálogo e o **personalizar faixa de opções** botão no Excel 2010. O local desse botão é semelhante em todos os outros aplicativos listados na seção "Aplica-se a" na parte superior deste tópico.  
  
     ![O botão de faixa de opções personalizar](../vsto/media/vsto-office2010-customizeribbonbutton.png "botão a faixa de opções personalizar")  
  
4.  Na lista de guias principais, selecione o **desenvolvedor** caixa de seleção.  
  
     A figura a seguir mostra o **desenvolvedor** caixa de seleção no Word 2010 e [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. O local dessa caixa de seleção é semelhante em todos os outros aplicativos listados na seção "Aplica-se a" na parte superior deste tópico.  
  
     ![A caixa de seleção de desenvolvedor na caixa de diálogo Opções do Word](../vsto/media/vsto-office2010-developercheckbox.png "desenvolvedor a caixa de seleção na caixa de diálogo Opções do Word")  
  
5.  Escolha o **Okey** para fechar o **opções** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)  
  
  