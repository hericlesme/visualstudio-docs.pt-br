---
title: ': Get_undecoratednameex | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 078826c799cf99cadd1812ff88dc29663a759baf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470236"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Recupera parte ou todo um nome não decorado para um C++ decorado nome (vinculação).  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `undecoratedOptions`  
 [in] Especifica uma combinação de sinalizadores que controlam o que é retornado. Consulte a seção comentários para os valores específicos e o que fazer.  
  
 `pRetVal`  
 [out] Retorna que o nome não decorado para um C++ decorado por nome.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 O `undecorateOptions` pode ser uma combinação dos sinalizadores a seguir.  
  
> [!NOTE]
>  Os nomes de sinalizador não estão definidos no SDK do DIA, para que seja necessário adicionar as declarações em seu código ou usar os valores brutos.  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Habilita completo undecoration.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Remove os sublinhados da Microsoft estendido palavras-chave.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Desabilita expansão de estendidas palavras-chave da Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Desabilita expansão de tipo de retorno para declaração primário.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Desabilita a expansão do modelo de declaração.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Desabilita expansão de especificador de linguagem de declaração.|  
|UNDNAME_RESERVED1|0x0020|RESERVADO.|  
|UNDNAME_RESERVED2|0x0040|RESERVADO.|  
|UNDNAME_NO_THISTYPE|0x0060|Desabilita todos os modificadores no `this` tipo.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Desabilita expansão dos especificadores de acesso de membros.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Desabilita expansão "throw-assinaturas" para funções e ponteiros para funções.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Desabilita expansão de `static` ou `virtual` membros.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Desativa a expansão do modelo do Microsoft para retorna UDT.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates nomes decorados de 32 bits.|  
|UNDNAME_NAME_ONLY|0x1000|Obtém somente o nome de declaração primário; Retorna apenas [escopo::] nome.  Expande os parâmetros do modelo.|  
|UNDNAME_TYPE_ONLY|0x2000|A entrada é apenas um tipo de codificação; compõe um declarador abstrato.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Os parâmetros de modelo real estão disponíveis.|  
|UNDNAME_NO_ECSU|0x8000|Suprime enum/classe/struct/união.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Suprime a verificação de caracteres de identificador válido.|  
|UNDNAME_NO_PTR64|0x20000|Não inclui ptr64 na saída.|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)