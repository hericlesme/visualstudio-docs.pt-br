---
title: 'Como: destinar a Interface de usuário multilíngue do Office | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 54b305311b686f527a79092280fbc33c3974247e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Como destinar a Interface de Usuário Multilíngue do Office
  A Interface de usuário multilíngue (MUI) é um recurso do Microsoft Office que permite que o usuário final para alterar o idioma da interface do usuário (IU). Por exemplo, um usuário final trabalhando com uma interface do usuário em inglês pode alterar o idioma da interface do usuário para espanhol.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se seu aplicativo será usado por pessoas que usam vários idiomas do Office, você pode adicionar código para alterar automaticamente o idioma de suas cadeias de caracteres da interface do usuário para corresponder ao idioma que está sendo usado pelo Office no computador do usuário (se o usuário tem os recursos corretos instalados).  
  
### <a name="to-check-the-current-office-ui-setting"></a>Para verificar a configuração atual da interface do usuário do Office  
  
1.  Use o <xref:System.Threading.Thread.CurrentUICulture%2A> propriedade do thread atual. Defina o idioma de suas cadeias de caracteres da interface do usuário para corresponder ao idioma que está sendo usado pela versão do Office em execução no computador do usuário.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: destinar aplicativos do Office por meio de Assemblies de interoperabilidade primários](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Vinculação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md)  
  
  