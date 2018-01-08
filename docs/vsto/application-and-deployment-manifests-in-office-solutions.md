---
title: "Manifestos de aplicativo e implantação em soluções do Office | Microsoft Docs"
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
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 83bf3b48d562e5acf24fedd27954c10505454b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifestos de aplicativo e implantação em soluções do Office
  Um manifesto de aplicativo é um arquivo XML que fornece informações que são usadas por uma solução do Office para localizar e atualizar seus assemblies. Um manifesto de aplicativo pode ser usado com um manifesto de implantação, que é um arquivo XML armazenado no servidor que fornece as informações necessárias para localizar a versão mais atual do manifesto de aplicativo e assemblies.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Estrutura de manifesto para soluções do Office  
 Para soluções do Microsoft Office criadas usando as ferramentas de desenvolvimento do Office no Visual Studio, todos os manifestos são baseados no esquema padrão do ClickOnce. Quando você implantar as soluções do Office, os manifestos de aplicativo para o nível de documento e projetos de suplemento do VSTO estão localizados no cache do ClickOnce. Os manifestos de implantação não são copiados para o computador cliente.  
  
 Para obter informações sobre o conteúdo do aplicativo e manifestos de implantação para projetos do Office, consulte [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md) e [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="creating-application-and-deployment-manifests"></a>Manifestos de criação de aplicativo e implantação  
 Manifestos de aplicativo são criados automaticamente como parte do processo de compilação. Sempre que você criar um projeto no nível do documento, o local do manifesto de implantação é inserido no documento como uma propriedade de documento personalizadas. Para suplementos do VSTO, o local do manifesto de implantação é armazenado no registro.  
  
 Para obter mais informações sobre o **Assistente de publicação**, consulte [implantar uma solução Office pelo ClickOnce usando](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Para obter mais informações sobre como manifestos de trabalhar com soluções do Office, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto do aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Manifesto de implantação do ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  