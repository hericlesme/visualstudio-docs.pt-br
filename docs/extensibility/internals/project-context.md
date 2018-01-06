---
title: Contexto do projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 99f073e7f27fc98c1c751ae8153adfeea0018e2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="project-context"></a>Contexto do projeto
Quando o usuário adiciona ou funciona com projetos e itens de projeto, o IDE usa a noção de contexto do projeto para determinar como as várias operações devem ser executadas.  
  
 Normalmente, os arquivos são os objetos de projeto padrão que o usuário cria explicitamente, selecionando o **novo projeto** comando ou torna disponível, selecionando o **Abrir projeto** comando o  **Arquivo** menu. Nesses casos, os arquivos são criados e abertos no contexto de um projeto e o tipo de projeto define o contexto de edição do documento.  
  
 Alguns projetos fornecem um contexto muito avançado. Por exemplo, o projeto gerencia um namespace no escopo do projeto, através de programação ou uma conexão de banco de dados no escopo do projeto para associação de dados. O usuário pode abrir com frequência conexões de banco de dados ou arquivos diretamente por meio de um objeto de projeto específico, como um item de projeto exibido no Gerenciador de soluções.  
  
 Em outras ocasiões, o contexto de um item de projeto não for especificado explicitamente. Por exemplo, o contexto de um item não está disponível quando o usuário abre um arquivo, selecionando o **abrir arquivo existente** comando o **arquivo** menu, quando o depurador opera em um arquivo ou quando o usuário clica o **Localizar em arquivos** do **localizar e substituir** caixa de diálogo. Para lidar com essas situações, as chamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para gerenciar o processo de localização do projeto melhor para abrir um documento.  
  
## <a name="see-also"></a>Consulte também  
 [Prioridade do projeto](../../extensibility/internals/project-priority.md)   
 [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)