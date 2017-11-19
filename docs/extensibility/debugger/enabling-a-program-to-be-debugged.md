---
title: Habilitar um programa a ser depurado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1c38c110e9499936a24c33432180adf18209bf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="enabling-a-program-to-be-debugged"></a>Habilitar um programa a ser depurado
Antes do mecanismo de depuração (DE) pode depurar um programa, você deve primeiro iniciar DE ou anexá-lo para um programa existente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Obter uma porta](../../extensibility/debugger/getting-a-port.md)  
 Discute como obter uma porta como a primeira etapa para habilitar um programa a ser depurado.  
  
 [Registrar o programa](../../extensibility/debugger/registering-the-program.md)  
 Explica a próxima etapa para habilitar um programa a ser depurado: registrá-lo com a porta. Depois de registrado, o programa pode ser depurado pelo processo de anexação ou a depuração just-in-time (JIT).  
  
 [Anexar ao programa](../../extensibility/debugger/attaching-to-the-program.md)  
 Explica a próxima etapa: anexar o depurador para o programa.  
  
 [Com base no lançamento anexando](../../extensibility/debugger/launch-based-attachment.md)  
 Descreve o anexo com base em Iniciar para um programa, o que é automático após a inicialização, o SDM.  
  
 [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)  
 Percorre os eventos necessários durante a criação de um mecanismo de depuração (DE) e anexá-lo a um programa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define um mecanismo de depuração (DE) e descreve os serviços implementados por meio DE interfaces e como elas podem causar o depurador para fazer a transição entre os modos operacionais diferentes.