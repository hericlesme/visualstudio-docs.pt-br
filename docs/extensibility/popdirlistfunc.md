---
title: POPDIRLISTFUNC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44a11e6edc9666fcd7614d467a2c9ffaa86b4365
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142180"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Essa é uma função de retorno de chamada fornecida para o [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) função para atualizar um conjunto de diretórios e (opcionalmente) os nomes de arquivo para descobrir que estão sob o controle de origem.  
  
 O `POPDIRLISTFUNC` retorno de chamada deve ser chamado somente para os nomes de arquivos e diretórios (na lista fornecida para o `SccPopulateDirList` função) que são realmente sob controle de origem.  
  
## <a name="signature"></a>Assinatura  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 [in] Valor de usuário fornecido ao [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bOpções de pasta  
 [in] `TRUE` se o nome no `lpDirectoryOrFileName` é um diretório; caso contrário, o nome é um nome de arquivo.  
  
 lpDirectoryOrFileName  
 [in] Caminho local completo para um nome de diretório ou arquivo que está sob controle do código fonte.  
  
## <a name="return-value"></a>Valor de retorno  
 O IDE retorna um código de erro apropriado:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Continue o processamento.|  
|SCC_I_OPERATIONCANCELED|Pare o processamento.|  
|SCC_E_xxx|Qualquer erro de controle de origem apropriada deve parar o processamento.|  
  
## <a name="remarks"></a>Comentários  
 Se o `fOptions` parâmetro o `SccPopulateDirList` função contém o `SCC_PDL_INCLUDEFILES` sinalizador e, em seguida, a lista conterá possivelmente nomes de arquivo, como também os nomes de diretório.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Códigos de erro](../extensibility/error-codes.md)