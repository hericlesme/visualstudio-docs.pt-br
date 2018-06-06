---
title: Soluções VBA e do Office no Visual Studio comparadas
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 81e55c2861da33d656ad9a5584e6ff5916afb232
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768047"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Soluções VBA e do Office no Visual Studio comparadas
  Microsoft Visual Basic for Applications (VBA) usa o código não gerenciado é integrado com aplicativos do Office. Projetos do Microsoft Office criados usando o Visual Studio permitem aproveitar as ferramentas de design do Visual Studio e .NET Framework.  
  
 Para obter informações sobre os tipos de soluções do Office que você pode criar usando o Visual Studio, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Comparação  
 A tabela a seguir fornece uma comparação básica entre soluções VBA e soluções do Office no Visual Studio.  
  
|Soluções VBA|Soluções do Office no Visual Studio|  
|-------------------|---------------------------------------|  
|Usa o código que está conectado ao e persistente com um documento específico.|Usa o código que é armazenado separadamente do documento (para personalizações de nível de documento), ou em um assembly que é carregado pelo aplicativo (para VSTO VSTO Add-ins).|  
|Funciona com as APIs de VBA e modelos de objeto do Office.|Fornece acesso a modelos de objeto do Office e o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] APIs.|  
|Projetado para a gravação da macro e uma experiência simplificada de desenvolvedor.|Projetado para segurança, manutenção mais fácil de código e a capacidade de usar o ambiente de desenvolvimento integrado completo do Visual Studio (IDE).|  
|Funciona bem para soluções que se beneficiam de uma integração com aplicativos do Office.|Funciona bem para soluções que se beneficiam de todos os recursos do Visual Studio e o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Tem limitações para a empresa, especialmente nas áreas de segurança e implantação.|Projetado para uso na empresa.|  
  
 Algumas coisas são ainda mais fácil de fazer rapidamente usando VBA. Especificamente, você talvez queira continuar usando o VBA para:  
  
-   Funções de planilha personalizada.  
  
-   Gravação da macro.  
  
## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combinar soluções VBA e soluções do Office criadas usando o Visual Studio  
 Você pode chamar código VBA de soluções do Office criadas usando o Visual Studio, e você também pode chamar código em soluções do Office criadas usando o Visual Studio por meio do VBA. A técnica específica difere dependendo se sua solução do Office é um suplemento do VSTO ou uma personalização no nível do documento. Para obter mais informações, consulte [chamar o código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) e [combinar VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral sobre o desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Chamar o código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Combinar VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Proteger as soluções do Office](../vsto/securing-office-solutions.md)   
 [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  