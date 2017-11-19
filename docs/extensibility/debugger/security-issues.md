---
title: "Problemas de segurança | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8061c419f81493e56a58df8fefbe4d3362d43e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="security-issues"></a>Problemas de segurança
Para depurar um programa usando o Visual Studio, as únicas permissões necessárias são as mesmas um desenvolvedor precisa para executar o programa. Isso inclui a depuração remota para a maioria das situações (algumas situações que envolvem a outros serviços, como o serviço de informações da Internet, podem exigir um nível mais alto de permissões).  
  
 Enquanto o Visual Studio está em execução, o Gerenciador de depuração do processo (PDM) rastreia depurar processos no computador local. Remotamente, um programa chamado msvsmon.exe é iniciado pelo desenvolvedor para tratar a depuração remota e disponibilizar o PDM. (Observe que msvsmon.exe não é um serviço e deve ser iniciado manualmente para habilitar a depuração remota nesse computador). Quando o Visual Studio (ou msvsmon.exe) não está em execução, nenhum processo é rastreado para depuração.  
  
 Isso significa que um desenvolvedor pode depurar programas que início com nenhuma permissão especial. O desenvolvedor ainda pode depurar processos iniciados por outra pessoa se outra pessoa é um membro do mesmo grupo de segurança. E para habilitar a depuração remota, é necessário apenas para copiar o necessário arquivos à instância remota do computador em Iniciar msvsmon.exe (consulte [depuração remota](../../debugger/remote-debugging.md) para obter mais detalhes).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [Gerenciador de depuração do processo](../../extensibility/debugger/process-debug-manager.md)   
 [Depuração remota](../../debugger/remote-debugging.md)