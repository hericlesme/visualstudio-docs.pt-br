---
title: 'Como: adicionar controles XMLNode a documentos do Word | Microsoft Docs'
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
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
ms.assetid: d583b9d4-bd13-46e3-9eb7-da18fcb7eb8c
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 73beb7b761e253abb77ef3ddcc46c534127714e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Como adicionar controles XMLNode a documentos do Word
  **Importante** as informações definidas neste tópico sobre o Microsoft Word são apresentada exclusivamente para o benefício e o uso de pessoas e organizações que estão localizados fora dos Estados Unidos e seus territórios ou que estão usando o ou desenvolvendo programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removido uma implementação de determinada funcionalidade relacionado ao XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word não podem ser lidas ou usadas por indivíduos ou organizações nos Estados Unidos ou seus territórios que estão usando ou desenvolver programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft após 10 de janeiro de 2010 ; Esses produtos não se comportar o mesmo que produtos licenciados antes dessa data ou adquirido e licenciado para uso fora dos Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Quando você mapear um elemento de esquema XML não repetição para um documento do Microsoft Office Word, o Visual Studio adiciona automaticamente um <xref:Microsoft.Office.Tools.Word.XMLNode> controle ao documento. Para obter informações sobre como mapear elementos de esquema XML de repetição, consulte [como: adicionar controles XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  O <xref:Microsoft.Office.Tools.Word.XMLNode> controle não está disponível a **caixa de ferramentas** ou **fontes de dados** janela e ele não podem ser criado por meio de programação.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Para adicionar um controle XMLNode a um documento  
  
1.  O documento no designer do Visual Studio, na faixa de opções, clique no **desenvolvedor** guia.  
  
    > [!NOTE]  
    >  Se o **desenvolvedor** guia não estiver visível, você deve primeiro mostrá-la. Para obter mais informações, consulte [como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  No **XML** de grupo, clique em **esquema**.  
  
     O **modelos e suplementos** caixa de diálogo é aberta.  
  
3.  Clique o **esquema XML** guia.  
  
4.  Clique em **adicionar esquema**.  
  
     O **adicionar esquema** caixa de diálogo é aberta.  
  
5.  Selecione um esquema XML que contém os elementos do esquema não repetitivo do **adicionar esquema** caixa de diálogo e clique em **abrir**.  
  
     O **configurações do esquema** caixa de diálogo é exibida.  
  
6.  Atribuir um alias ou clique em **Okey** para adicionar o esquema sem um alias.  
  
     O esquema é adicionado para o **adicionar esquema** caixa de diálogo.  
  
7.  No **adicionar esquema** caixa de diálogo, clique em **Okey**.  
  
8.  O **estrutura XML** é aberto o painel de tarefas.  
  
9. Clique no elemento do esquema não repetitivo no **estrutura XML** painel de tarefas para adicioná-lo ao documento.  
  
     Um <xref:Microsoft.Office.Tools.Word.XMLNode> controle é criado e adicionado ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Controle XMLNode](../vsto/xmlnode-control.md)   
 [Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  