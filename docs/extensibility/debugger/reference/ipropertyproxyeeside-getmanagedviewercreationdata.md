---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc4d81470a1ea15573171a80034efcd6daf720ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera informações sobre o visualizador para esse tipo de propriedade para criar uma instância desse visualizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `assemName`  
 [out] Retorna o nome do assembly que contém este objeto.  
  
 `assemBytes`  
 [out] Retorna um [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contém os bytes de assembly do objeto (Este é um valor nulo se nenhuma bytes estão disponíveis).  
  
 `assemPdb`  
 [out] Retorna um `IEEDataStorage` objeto que contém o símbolo de armazena informações para esse objeto (Este é um valor nulo se nenhum armazenamento de símbolo está disponível).  
  
 `className`  
 [out] Retorna o nome da classe que contém este objeto.  
  
 `alr`  
 [out] Retorna um valor da [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumeração que indica o local do assembly.  
  
 `replacementOk`  
 [out] Retorna zero (`TRUE`) se o valor do objeto pode ser alterado; zero (`FALSE`) se o objeto é somente leitura.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado por visualizadores de tipo para instanciar um visualizador gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)