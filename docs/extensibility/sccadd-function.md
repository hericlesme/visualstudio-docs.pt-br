---
title: "Função SccAdd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAdd
helpviewer_keywords: SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 52137da9d14920a2fd5213f1110a74d895e51c7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sccadd-function"></a>Função SccAdd
Essa função adiciona novos arquivos ao sistema de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 nFiles  
 [in] Número de arquivos selecionados para serem adicionados ao projeto atual conforme fornecido na `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nomes totalmente qualificados de locais de arquivos a ser adicionado.  
  
 lpComment  
 [in] O comentário a ser aplicado a todos os arquivos que está sendo adicionados.  
  
 pfOptions  
 [in] Matriz de sinalizadores de comando fornecido em uma base por arquivo.  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A operação de adição foi bem-sucedida.|  
|SCC_E_FILEALREADYEXISTS|O arquivo selecionado já está sob controle de origem.|  
|SCC_E_TYPENOTSUPPORTED|Não há suporte para o tipo de arquivo (por exemplo, binário) pelo sistema de controle de origem.|  
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não oferece suporte a esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_NONSPECIFICERROR|Falha não específica; Adicione não executada.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
|SCC_E_FILENOTEXIST|Arquivo local não foi encontrado.|  
  
## <a name="remarks"></a>Comentários  
 O usual `fOptions` são substituídos aqui por uma matriz, `pfOptions`, com um `LONG` opção especificação por arquivo. Isso ocorre porque o tipo de arquivo pode variar para cada arquivo.  
  
> [!NOTE]
>  Não é válido especificar ambos `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` opções para o mesmo arquivo, mas ele é válido para especificar nenhum. A configuração não é a mesma configuração `SCC_FILETYPE_AUTO`, caso em que a fonte de controlar este plug-in detecta automaticamente o tipo de arquivo.  
  
 Abaixo está a lista de sinalizadores usados no `pfOptions` matriz:  
  
|Opção|Valor|Significado|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|O plug-in de controle de origem deve detectar o tipo de arquivo.|  
|SCC_FILETYPE_TEXT|0x01|Indica um arquivo de texto ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Indica um tipo de arquivo diferente de texto ASCII.|  
|SCC_ADD_STORELATEST|0x04|Armazena apenas a cópia mais recente do arquivo, sem deltas.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Trata o arquivo como texto ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Trata o arquivo como texto em Unicode no formato UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Trata o arquivo como texto Unicode em UTF16 Little Endian formato.|  
|SCC_FILETYPE_UTF16BE|0x40|Trata o arquivo como texto Unicode em UTF16 Big Endian Formatar.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)