---
title: 'Como: aplicativos do Office de destino por meio de assemblies de interoperabilidade primários'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32ff157e3986836ac13472c4a9ed8a7b01f06e04
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Como: aplicativos do Office de destino por meio de assemblies de interoperabilidade primários
  Quando você cria um novo projeto do Office, o Visual Studio adiciona automaticamente as referências para os Microsoft Office assemblies de interoperabilidade primários (PIAs) que são necessários para compilar seu projeto. Você deve adicionar referências a outros PIAs nos seguintes cenários:  
  
-   Você deseja usar os recursos de outros aplicativos do Microsoft Office em seu projeto. Por exemplo, você talvez queira usar recursos do Microsoft Office Excel em um projeto para o Microsoft Office Word.  
  
-   Você deseja automatizar aplicativos do Microsoft Office que não tem projetos dedicados no Visual Studio, como o Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Para adicionar uma referência a um assembly de interoperabilidade primária  
  
1.  Abra seu projeto do Office e selecione o nome do projeto no **Gerenciador de soluções**.  
  
2.  No menu **Projeto**, clique em **Adicionar Referência**.  
  
3.  Sobre o **Framework** , selecione o PIA desejado no **nome do componente** lista. Para obter mais informações sobre os assemblies interoperabilidade primárias para Microsoft Office disponíveis, consulte [assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md).  
  
     Se os destinos do projeto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, o **Embed Interop Types** propriedade para a referência de assembly está definida como **True** por padrão. Usando essa configuração, sua solução não requer o PIA em computadores de usuários finais. Para obter mais informações, consulte [Design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Em projetos do Office, sempre adicionar referências a PIAs do Office usando o **.NET** guia do **adicionar referência** caixa de diálogo, em vez do **COM** guia. Para obter mais informações, consulte [assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Clique em **OK**.  
  
     O nome do assembly aparece no **referências** pasta de **Gerenciador de soluções**.  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md)   
 [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Desenvolver soluções do Office](../vsto/developing-office-solutions.md)   
 [Como: assemblies de interoperabilidade primários do Office de instalação](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  