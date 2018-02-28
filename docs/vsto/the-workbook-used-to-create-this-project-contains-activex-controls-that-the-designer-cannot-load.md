---
title: "A pasta de trabalho usada para criar este projeto contém controles ActiveX que não é possível carregar o designer | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 0f50342fd82826aec8cf0d9694454afdc2db4080
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>A pasta de trabalho usada para criar este projeto contém controles ActiveX que o designer não pode carregar
  Este erro aparece quando você adiciona um controle a um documento do Word ou uma planilha do Excel programaticamente, salve o documento ou a pasta de trabalho e, em seguida, crie uma nova solução de nível de documento com base no documento ou pasta de trabalho.  
  
 Informações que descrevem o tipo gerenciado do controle não é salvo junto com o documento ou a pasta de trabalho. Quando você cria uma nova solução com base no documento ou pasta de trabalho, o Visual Studio não tem informações suficientes para carregar o controle no designer de item de host.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Abra o documento ou pasta de trabalho.  
  
2.  Remova os controles que foram adicionados em tempo de execução. Você pode fazer isso selecionando-os no documento ou pasta de trabalho e pressionando a tecla DELETE.  
  
3.  Crie uma solução de nível de documento com base no documento ou pasta de trabalho.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Adicionando controles a documentos do Office no tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  