---
title: "Uma ou mais propriedades no arquivo. ofs não são válidas para a classe de mensagem selecionada | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ca816a635abf929f2bfa1614f4560f434adbfd45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Uma ou mais propriedades no arquivo .ofs não são válidas para a classe de mensagem selecionada
  Esse erro aparece quando você importa uma região de formulário projetada no Outlook, mas um ou mais campos na região de formulário não são compatíveis com as classes de mensagem que você selecionar na página final do **nova região de formulário** assistente.  
  
 Por exemplo, você pode selecionar **tarefa (IPM. Tarefa)** na página final do **nova região de formulário** assistente. Se a região de formulário contém um **endereço comercial** campo, você receberá esse erro porque uma tarefa não tem um endereço de negócios. Portanto, o **endereço comercial** campo não é compatível com o IPM. Classe de mensagem de tarefa.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Na página final do **nova região de formulário** assistente, selecione a classe de mensagem que é compatível com os campos na região de formulário.  
  
-   No Designer de formulários no Outlook, remover campos que não são compatíveis com as classes de mensagem que você planeja para selecionar a página final de **nova região de formulário** assistente.  
  
## <a name="see-also"></a>Consulte também  
 [Instruções passo a passo: importando uma região do formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  