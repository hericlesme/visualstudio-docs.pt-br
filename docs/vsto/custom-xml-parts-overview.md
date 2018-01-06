---
title: "Visão geral das partes XML personalizadas | Microsoft Docs"
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
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 735660c3af1c0a8792a35981788b70f4a79d55b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-xml-parts-overview"></a>Visão geral da personalização das partes XML
  Você pode inserir dados XML em documentos para alguns aplicativos do Microsoft Office. Quando você inserir dados XML em um documento, os dados são denominados uma *parte XML personalizada*.  
  
 Você pode criar e modificar partes XML personalizadas em um documento usando um suplemento do VSTO ou solução no Visual Studio no nível do documento. Você não precisa iniciar o aplicativo do Microsoft Office para criar e modificar partes XML personalizadas.  
  
 **Aplica-se a:** as informações neste tópico se aplicam a projetos no nível de documento e a projetos de suplemento do VSTO para Excel, PowerPoint e Word. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  O Visual Studio também permite que você para objetos de dados do cache em personalizações no nível do documento. Esse recurso é diferente de partes XML personalizadas, embora haja algumas semelhanças. Para obter mais informações, consulte [dados armazenados em cache em personalizações no nível do documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understanding-custom-xml-parts"></a>Noções básicas sobre partes XML personalizadas  
 Partes XML personalizadas foram introduzidos no sistema Microsoft Office 2007, juntamente com os formatos XML abertos. Esses formatos incluem novos formatos de arquivo baseado em XML para o Excel, PowerPoint e Word (como. docx,. pptx e. xlsx). Documentos nesses formatos consistem em arquivos XML (também chamado *partes XML*) que são organizados em pastas em um arquivo ZIP. A maioria das partes XML são partes internas que ajudam a definir a estrutura e o estado do documento. No entanto, os documentos também podem conter partes XML personalizadas, o que pode ser usado para armazenar dados XML arbitrário nos documentos.  
  
 Os formatos de arquivo XML permitem que aplicativos trabalhar com documentos de maneiras que não são possíveis com os mais antigos formatos de arquivo binário (como. doc,. ppt e. xls). Qualquer aplicativo que pode ler arquivos ZIP pode examinar e modificar o conteúdo dos documentos, mesmo se o Microsoft Office não estiver instalado.  
  
 Para obter mais informações sobre a estrutura de Open XML e partes XML personalizadas, consulte os seguintes artigos:  
  
-   [Apresentando os formatos de arquivo do Office (2007) Open XML](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Como: manipular documentos nos formatos XML abertos](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Passo a passo: Formato de XML Word 2007](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Formatos de criação de documentos do Word 2007 usando Open XML](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Word, Excel e PowerPoint também permitem usar partes XML personalizadas em documentos que são salvos nos formatos de arquivo binário. No entanto, se um documento é salvo em um formato binário, você não pode adicionar ou modificar partes XML personalizadas sem iniciar o aplicativo do Microsoft Office.  
  
## <a name="creating-and-modifying-custom-xml-parts"></a>Criando e modificando partes XML personalizadas  
 Você pode criar ou modificar partes XML personalizadas quando o documento está aberto no aplicativo do Office, ou quando o documento é fechado, mesmo se o Microsoft Office não estiver instalado.  
  
### <a name="modifying-xml-parts-while-the-office-application-is-running"></a>Modificando a partes XML enquanto o aplicativo do Office está em execução  
 Você pode trabalhar com partes XML personalizadas usando uma personalização no nível do documento ou um suplemento do VSTO. Se você estiver usando uma personalização no nível do documento, você normalmente trabalhará com partes XML personalizadas que estão no documento de personalizado. Se você estiver usando um suplemento do VSTO, você pode criar ou modificar partes XML personalizadas em qualquer documento que está aberto no aplicativo.  
  
 Para criar uma parte XML personalizada usando o Visual Studio, adicione um novo <xref:Microsoft.Office.Core.CustomXMLPart> para o <xref:Microsoft.Office.Core.CustomXMLParts> coleção no documento. Para mais informações, consulte os seguintes tópicos:  
  
-   [Como adicionar partes XML personalizadas no nível do documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Como adicionar partes XML personalizadas aos documentos usando suplementos VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modifying-xml-parts-without-starting-the-office-application"></a>Modificando a partes XML sem iniciar o aplicativo do Office  
 Você pode adicionar ou modificar uma parte XML personalizada sem iniciar o Excel, PowerPoint ou Word. Isso é útil se você quiser trabalhar com dados XML em um documento em um computador que não tenha instalados, como um servidor de aplicativos do Microsoft Office.  
  
 Para adicionar uma parte XML personalizada sem iniciar o Microsoft Office, use classes do SDK de XML aberta. Essas classes são projetadas para fornecer acesso ao conteúdo de Open XML que é específico para documentos do Office. Por exemplo, para adicionar uma parte XML personalizada a uma pasta de trabalho do Excel, você usa o [AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a) método de um [WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) objeto. Para obter mais informações, consulte [Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## <a name="binding-custom-xml-parts-to-word-content-controls"></a>Partes XML personalizadas de associação para controles de conteúdo do Word  
 Você pode vincular controles de conteúdo em uma solução de palavras para os elementos em uma parte XML personalizada. Quando um controle de conteúdo é associado a uma parte XML personalizada, os dados na parte XML personalizada são exibidos na interface do usuário (IU) do controle de conteúdo. Se um usuário editar texto no controle, o elemento XML correspondente é atualizado automaticamente. Da mesma forma, se os valores de elemento nas partes XML personalizadas são alterados, os controles de conteúdo que estão associados aos elementos XML exibem os novos dados. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Consulte também  
 [Esquemas XML e dados em personalizações no nível do documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Como: adicionar partes XML a personalizações no nível do documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Como: adicionar partes XML personalizadas aos documentos usando suplementos VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Controles de conteúdo](../vsto/content-controls.md)   
 [Instruções passo a passo: associando controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  