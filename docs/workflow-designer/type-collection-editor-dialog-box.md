---
title: "Caixa de diálogo Editor de coleção do tipo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8e4b794a623c3a0218e44773da6bdb6c76612816
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="type-collection-editor-dialog-box"></a>Digite a caixa de diálogo Editor de Coleção
O **Editor de coleção do tipo** caixa de diálogo é usada para adicionar tipos conhecidos para o **enviar** e **Receive** atividades. Essa caixa de diálogo também é usada para adicionar argumentos de tipo genérico para o **InvokeMethod** atividade. Quando usado para o **enviar** e **Receive** atividades para adicionar tipos conhecidos, o **Editor de coleção do tipo** caixa de diálogo requer as adições de tipo para ser exclusivo. Se um tipo duplicado será adicionado e a alteração é confirmada, clicando em **Okey**, uma mensagem de erro é retornada. Quando usado para o **InvokeMethod** atividade para adicionar argumentos de tipo genérico, o **Editor de coleção do tipo** caixa de diálogo permite a adição de tipos duplicados.  
  
> [!NOTE]
>  [! INCLUIR[crabout](/dotnet/framework/wcf/feature-details/data-contract-known-types).  
  
 A tabela a seguir descreve os elementos de interface de usuário do **tipo de coleção** caixa de diálogo.  
  
|Elemento da Interface do Usuário|Descrição|  
|----------------|-----------------|  
|**Lista de Tipos**|Uma lista de tipos que foram adicionados ou removidos.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Para transferir anterior o Editor de Coleção do tipo  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para transferir anterior o Editor de Coleção do tipo para o enviar e receber atividades  
  
1.  Selecione o **enviar** ou **Receive** atividade na exibição design.  
  
2.  Pressione **F4** para ativar o **propriedades** janela.  
  
3.  No **propriedades** janela, clique no botão de reticências ao lado de **KnownTypes** propriedade.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para transferir anterior o Editor de Coleção do tipo para atividades de InvokeMethod  
  
1.  Selecione o **InvokeMethod** atividade na exibição design.  
  
2.  Pressione **F4** para ativar o **propriedades** janela.  
  
3.  No **propriedades** janela, clique no botão de reticências ao lado de **GenericTypeArguments** propriedade.