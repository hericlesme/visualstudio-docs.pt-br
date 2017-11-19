---
title: 'Como: mapear esquemas para documentos do Word dentro do Visual Studio | Microsoft Docs'
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
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdfc13415a06960ad0ec736b19eb5b2483e7f19c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Como mapear esquemas para documentos do Word dentro do Visual Studio
  **Importante** as informações definidas neste tópico sobre o Microsoft Word são apresentada exclusivamente para o benefício e o uso de pessoas e organizações que estão localizados fora dos Estados Unidos e seus territórios ou que estão usando o ou desenvolvendo programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removido uma implementação de determinada funcionalidade relacionado ao XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word não podem ser lidas ou usadas por indivíduos ou organizações nos Estados Unidos ou seus territórios que estão usando ou desenvolver programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft após 10 de janeiro de 2010 ; Esses produtos não se comportar o mesmo que produtos licenciados antes dessa data ou adquirido e licenciado para uso fora dos Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Você pode mapear um esquema XML para um documento enquanto o documento está aberto no Visual Studio. Você usar as mesmas ferramentas do Microsoft Office Word que você usa quando o documento está aberto fora do Visual Studio. O Office project cria os objetos de mesmo se você mapear o esquema para o documento antes ou depois de criar sua solução do Word.  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Para mapear um esquema XML para um documento do Word no Visual Studio  
  
1.  Abra o projeto de modelo ou documento do Word dentro do Visual Studio.  
  
2.  Clique para mover o foco para o designer no documento.  
  
3.  Na faixa de opções, clique no **desenvolvedor** guia.  
  
    > [!NOTE]  
    >  Se o **desenvolvedor** guia não estiver visível, você deve primeiro mostrá-la. Para obter mais informações, consulte [como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  No **XML** de grupo, clique em **esquema**.  
  
     O **modelos e suplementos** caixa de diálogo é aberta.  
  
5.  Clique o **esquema XML** guia.  
  
6.  Clique em **adicionar esquema**.  
  
     O **adicionar esquema** caixa de diálogo é aberta.  
  
7.  Navegue até seu arquivo de esquema, selecione-o e, em seguida, clique em **abrir**.  
  
     O **configurações do esquema** caixa de diálogo é aberta.  
  
8.  Atribuir um alias ou clique em **Okey** para adicionar o esquema sem um alias.  
  
9. Clique em **OK**.  
  
     O **estrutura XML** janela será aberta.  
  
10. Arraste elementos do **estrutura XML** janela para os locais em seu documento onde você deseja que os controles correspondentes a ser criado.  
  
## <a name="see-also"></a>Consulte também  
 [Como: mapear esquemas para planilhas dentro do Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Esquemas e dados XML em personalizações no nível do documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  