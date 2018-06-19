---
title: Interface IDebugDocumentProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726246"
---
# <a name="idebugdocumentprovider-interface"></a>Interface IDebugDocumentProvider
Fornece os meios para instanciar um documento sob demanda.  
  
## <a name="remarks"></a>Comentários  
 Isso significa indireta para criar uma instância de um documento:  
  
-   Permite que o documento a ser carregado quando necessário.  
  
-   Permite que o objeto de documento a ser contido no depurador do IDE.  
  
-   Permite várias maneiras de acessar o mesmo objeto de documento.  
  
 Isso separa o documento de seu provedor e permite que o provedor de conter informações adicionais de contexto de tempo de execução, com eficiência.  
  
 Além dos métodos herdados de `IDebugDocumentInfo`, o `IDebugDocumentProvider` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Faz com que o documento a ser instanciado se ele ainda não existir.|