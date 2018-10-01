---
title: Editar e continuar (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 825eac4ab53e95904e85a794b665ce6f6b11f873
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463172"
---
# <a name="edit-and-continue-visual-basic"></a>Editar e Continuar (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [editar e continuar (Visual Basic)](https://docs.microsoft.com/visualstudio/debugger/edit-and-continue-visual-basic).  
  
Editar e Continuar são um recurso para depuração do [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] que permite alterar seu código durante a execução em modo de interrupção. Depois que as edições do código tiverem sido aplicadas, você poderá retomar a execução de código com as novas edições no lugar e visualizar o efeito.  
  
 Você pode usar o recurso Editar e Continuar sempre que entrar no modo de Interrupção. No modo de Interrupção, o ponteiro de instrução, uma seta amarela na janela de origem, aponta para a linha que será executada em seguida e será localizado em uma instrução executável dentro de um método ou corpo de propriedade. Você pode fazer praticamente qualquer tipo de alteração nas instruções executáveis no modo de Interrupção, e a alteração será inserida no projeto subjacente. Quando estiver no modo de Interrupção, porém, não será permitido em geral modificar instruções de declaração, como métodos públicos, campos públicos ou declarações da classe.  
  
 Quando você faz uma edição não autorizada, a alteração será marcada com um sublinhado ondulado roxo e uma tarefa será exibida na Lista de Tarefas. Você deve desfazer uma edição não autorizada se quiser continuar usando Editar e Continuar. Certas edições não autorizadas podem ser permitidas se forem feitas fora de Editar e Continuar. Se você quiser reter os resultados de uma edição não autorizada, deverá parar de depurar e reiniciar o aplicativo.  
  
 Editar e Continuar tem suporte para projetos de 64 bits voltados para o .NET Framework 4.5.1.  
  
 Editar e continuar não é suportado quando você inicia a depuração usando **anexar ao processo**. Editar e Continuar não tem suporte para código otimizado, código gerenciado misto e código nativo, ou projetos do Compact Framework (dispositivo inteligente).  
  
 Os tópicos desta seção fornecem detalhes adicionais sobre como usar esse recurso e que tipos de alterações não são permitidas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como aplicar edições no modo de interrupção com Editar e Continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explica como aplicar edições do código no modo de Interrupção.  
  
 [Edições sem suporte em Editar e Continuar do Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Descreve quais tipos de edições não podem ser executadas em Editar e Continuar do [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Editar e continuar](../debugger/edit-and-continue.md)  
 Fornece uma lista de tópicos em Editar e Continuar.



