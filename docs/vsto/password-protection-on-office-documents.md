---
title: Proteção por senha em documentos do Office | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a278677b40f8da703c7f3287851c2f82fb95a21c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572706"
---
# <a name="password-protection-on-office-documents"></a>Proteção por senha em documentos do Office
  É possível definir uma senha em seus documentos do Microsoft Office Word e pastas de trabalho do Excel do Microsoft Office para que eles não podem ser abertos por alguém que não sabe a senha. Essa opção é chamada de **senha em aberto**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Você pode criar projetos no nível de documento usando documentos existentes e pastas de trabalho **senha em aberto** habilitado. O comportamento no Visual Studio é diferente para documentos do Word e Excel com **senha em aberto** habilitado.  
  
 Para obter informações sobre como habilitar **senha em aberto**, consulte a Ajuda do Word ou Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Comportamento do Excel e do Word  
 Sempre que você abrir uma pasta de trabalho do Excel no Visual Studio tem **senha em aberto** habilitado, Excel solicitará a senha. Quando você cria sua solução, receberá a senha novamente, porque o documento é aberto durante a compilação.  
  
 Na primeira vez que você abre um documento do Word no Visual Studio tem **senha em aberto** habilitado, o Word solicitará a senha. Depois de inserir a senha com êxito **senha em aberto** é removida do documento e abrir o documento não exigir uma senha. Se você deseja que o documento em sua solução exigir uma senha antes que ele pode ser aberto, você deve habilitar **senha em aberto** após sua compilação final e antes de implantar a solução.  
  
## <a name="see-also"></a>Consulte também  
 [Proteção de documento em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Gerenciamento de direitos de informação e visão geral de extensões de código gerenciado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Como: permitir que o código seja executado atrás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
  
  