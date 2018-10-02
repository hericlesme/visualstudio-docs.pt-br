---
title: Suporte do Assistente para projetos aninhados | Microsoft Docs
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
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4621627faae761bfe63b7fd056427a3771d21582
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474562"
---
# <a name="wizard-support-for-nested-projects"></a>Suporte do assistente para projetos aninhados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [suporte do Assistente para projetos aninhados](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-support-for-nested-projects).  
  
O IDE executa dois assistentes que o projeto pai para projetos aninhados pode implementar: o **novo projeto** assistente e o **Add Item** assistente.  
  
 Se um usuário inicia o **novo projeto** do assistente selecionando **Add Project** e clicando em **novo projeto** no menu arquivo ou selecionando **adicionar** e o botão direito do mouse **novo projeto** no Gerenciador de soluções, o IDE executa o **AddProject** comando e a implementação do projeto pai o **AddProject**comando retorna um arquivo de projeto de modelo ou um arquivo do assistente (. vsz) que tem um conjunto de parâmetros de contexto.  
  
 Da mesma forma, a implementação do projeto pai da **AddItem** assistentes retorna um arquivo. vsz que tem um conjunto diferente de parâmetros de contexto.  
  
 Para obter mais informações sobre assistentes, consulte [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parâmetros de contexto](../../extensibility/internals/context-parameters.md) e [registrar modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Aninhar projetos](../../extensibility/internals/nesting-projects.md)

