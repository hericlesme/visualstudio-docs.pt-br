---
title: Nós de programa | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: caff608b85dc8fc563ace8f5d582dba1cba427c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472932"
---
# <a name="program-nodes"></a>Nós de programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [nós de programa](https://docs.microsoft.com/visualstudio/extensibility/debugger/program-nodes).  
  
Em termos de arquitetura do depurador, uma **nó do programa**:  
  
-   É uma descrição simples de um programa.  
  
-   Pode identificar em si e o processo que ele está em execução no e pode ser anexado para ser desanexado do e descrever o mecanismo de depuração (DES) que o criou, se houver.  
  
-   É representado por um [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface, geralmente criado por uma porta ou DE. Nós de programa são adicionados a uma porta chamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando um nó do programa é adicionado a uma porta, ele é adicionado ao processo que contém o programa que representa este nó do programa.  
  
 Em algum momento depois que uma sessão de depuração é iniciada, dependendo da implementação do pacote de depuração, nós de programa são usados para criar programas correspondentes. Quando um processo é consultado para seus programas, os programas são enumerados, uma para cada nó do programa.  
  
 Antes de um programa estiver anexado a, o IDE precisa de apenas uma descrição simples do programa. Essas informações podem ser obtidas a partir do nó do programa. Depois que o programa é anexado ao, o IDE precisa exibir informações mais detalhadas, como uma lista de todos os threads em execução no programa. Essas informações são obtidas do programa em si.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Processos](../../extensibility/debugger/processes.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

