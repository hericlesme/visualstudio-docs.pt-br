---
title: "Aplicativo de configurações em várias conexões de projeto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a5d66bf7670d5ba9b6423461bdb5e5482819592f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicativo de configurações em várias conexões de projeto
Um plug-in de controle de origem criados usando o código-fonte controle plug-in API 1.2, pode usar uma operação em lote para executar a mesma operação de controle de origem em vários contextos de conexão ou de vários projetos. Lotes podem ser usados para eliminar a redundância, caixas de diálogo da experiência do usuário por projeto.  
  
 Se um usuário seleciona vários itens que pertencem a mais de uma conexão em um plug-in de controle de origem criado usando o 1.1 de API de plug-in de origem, (por exemplo, dois projetos para Web em máquinas diferentes de compartilhamento de arquivos) e verifica-los, o usuário verá a mesma caixa de diálogo repetidamente. Isso acontecerá mesmo se o usuário clica o **aplicar a todos os** caixa na caixa de diálogo de seleção porque o IDE redefine seu estado para cada contexto de conexão.  
  
## <a name="new-capability-flag"></a>Novo sinalizador de recurso  
 `SccBeginBatch`Função define o `SCC_CAP_BATCH` sinalizador para indicar que uma operação em lote está em andamento  
  
## <a name="new-functions"></a>Novas funções  
 As novas funções a seguir oferece suporte à operação de lote:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 O `SCCBeginBatch` função inicia um grupo de operações de controle de origem. `SccEndBatch`Fecha o grupo. Os grupos não podem ser aninhados.  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na Versão 1.2 da API do plug-in de controle de código-fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)