---
title: Uma ou mais propriedades no arquivo. ofs não são válidas para a classe de mensagem selecionada | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac9f5ab05ba6ed858946b5f665d850eea51c230
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Uma ou mais propriedades no arquivo .ofs não são válidas para a classe de mensagem selecionada
  Esse erro aparece quando você importa uma região de formulário projetada no Outlook, mas um ou mais campos na região de formulário não são compatíveis com as classes de mensagem que você selecionar na página final do **nova região de formulário** assistente.  
  
 Por exemplo, você pode selecionar **tarefa (IPM. Tarefa)** na página final do **nova região de formulário** assistente. Se a região de formulário contém um **endereço comercial** campo, você receberá esse erro porque uma tarefa não tem um endereço de negócios. Portanto, o **endereço comercial** campo não é compatível com o IPM. Classe de mensagem de tarefa.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Na página final do **nova região de formulário** assistente, selecione a classe de mensagem que é compatível com os campos na região de formulário.  
  
-   No Designer de formulários no Outlook, remover campos que não são compatíveis com as classes de mensagem que você planeja para selecionar a página final de **nova região de formulário** assistente.  
  
## <a name="see-also"></a>Consulte também  
 [Instruções passo a passo: importando uma região do formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  