---
title: "Nós de programa | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90ec92ad46a850c26e700e9feafa60d291f608ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="program-nodes"></a>Nós de programa
Em termos de arquitetura do depurador, um **nó programa**:  
  
-   É uma descrição simples de um programa.  
  
-   Pode identificar em si e o processo que ele está em execução no e pode ser anexado para ser desanexado do e descrevem o mecanismo de depuração (DE) que o criou, se houver.  
  
-   É representado por um [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) normalmente criado por uma porta ou DE interface. Nós de programa são adicionados a uma porta chamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando um nó do programa é adicionado a uma porta, ele é adicionado ao processo que contém o programa que representa este nó do programa.  
  
 Em algum momento depois que uma sessão de depuração é iniciada, dependendo da implementação do pacote de depuração, nós de programa são usados para criar programas correspondentes. Quando um processo é consultado para seus programas, os programas são enumerados, uma para cada nó do programa.  
  
 Antes de um programa é conectado, o IDE precisa apenas uma descrição simples do programa. Essas informações podem ser obtidas a partir do nó do programa. Depois que o programa é conectado, o IDE precisa para exibir informações mais detalhadas, como uma lista de todos os threads em execução no programa. Essas informações são obtidas do programa em si.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Processos](../../extensibility/debugger/processes.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)