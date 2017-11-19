---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugContainerField::EnumFields
helpviewer_keywords: IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e1eb67855ae1e13970ad5eab2eba8dd6308abbb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Cria um enumerador para os campos do contêiner.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwKindFilter`  
 [in] Uma combinação de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que selecione os campos a serem enumerados. Tipos de campo podem descrever tipos de armazenamento, como classe ou informações primitivo ou específicas, como o ponteiro "this", parâmetro ou local.  
  
 `dwModifiersFilter`  
 [in] Uma combinação de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que selecione os campos a serem enumerados. Modificadores de campo podem ser permissões de acesso, como público ou privado ou informações de armazenamento, como estático, final ou virtual.  
  
 `pszNameFilter`  
 [in] O nome do campo a ser enumerado. Isso pode ser um valor nulo se todos os campos devem ser retornadas.  
  
 `nameMatch`  
 [in] Um valor da [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumeração que controla se a pesquisa diferencia maiusculas de minúsculas ou não.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de campos. Retorna um valor nulo se não houver nenhum campo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou S_FALSE se houver campos. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O `dwKindFilter`, `dwModifiersFilter`, e `pszNameFilter` parâmetros podem ser combinados, por exemplo, para selecionar todos os métodos virtuais públicos denominados "Meumetodo".  
  
## <a name="see-also"></a>Consulte também  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)