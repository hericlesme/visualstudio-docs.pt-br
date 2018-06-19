---
title: Função SccPopulateList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26e7bbb4a99c3cd649eedb7638feb5b6170b3b59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140285"
---
# <a name="sccpopulatelist-function"></a>Função SccPopulateList
Esta função atualiza uma lista de arquivos para um comando de controle de origem em particular e fornece o status de controle de origem em todos os arquivos de determinado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 n Ncomando  
 [in] O comando de controle de origem que será aplicado a todos os arquivos de `lpFileNames` matriz (consulte [comando código](../extensibility/command-code-enumerator.md) para obter uma lista de comandos possíveis).  
  
 nFiles  
 [in] Número de arquivos a `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Uma matriz de nomes de arquivo conhecida para o IDE.  
  
 pfnPopulate  
 [in] A função de retorno de chamada IDE para chamar para adicionar e remover arquivos (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).  
  
 pvCallerData  
 [in] Valor a ser passados inalterados para a função de retorno de chamada.  
  
 lpStatus  
 [out no] Uma matriz para o plug-in para retornar os sinalizadores de status para cada arquivo de controle de origem.  
  
 fOptions  
 [in] Sinalizadores de comando (consulte a seção "PopulateList sinalizador" [os sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obter detalhes).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Êxito.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função examina a lista de arquivos para o seu status atual. Ele usa o `pfnPopulate` função de retorno de chamada para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`. Por exemplo, se o comando é `SCC_COMMAND_CHECKIN` e um arquivo na lista não for verificado, o retorno de chamada é usado para informar o chamador. Ocasionalmente, o plug-in de controle de origem pode encontrar outros arquivos que podem ser parte do comando e adicioná-los. Isso permite, por exemplo, um usuário do Visual Basic para check-out de um arquivo. bmp que é usado pelo seu projeto, mas não aparecem no arquivo de projeto do Visual Basic. Um usuário escolhe o **obter** comando no IDE. O IDE exibirá uma lista de todos os arquivos que ele achar que o usuário pode obter, mas antes que a lista é exibida, o `SccPopulateList` função é chamada para certificar-se de que a lista a ser exibida é atualizada.  
  
## <a name="example"></a>Exemplo  
 O IDE criará uma lista de arquivos que ele achar que o usuário pode obter. Antes de exibir essa lista, ele chama o `SccPopulateList` funcionar, fornecendo o plug-in de controle de origem a oportunidade de adicionar e excluir arquivos da lista. O plug-in modifica a lista chamando a função de retorno de chamada fornecido (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter mais detalhes).  
  
 Continua o plug-in chamar o `pfnPopulate` função, que adiciona e exclui arquivos, quando ele for concluído e retorna o `SccPopulateList` função. O IDE pode exibir a lista. O `lpStatus` matriz representa todos os arquivos da lista original passado pelo IDE. O plug-in, preenche o status de todos esses arquivos Além disso, para fazer com que usa a função de retorno de chamada.  
  
> [!NOTE]
>  Um plug-in de controle de origem sempre tem a opção de simplesmente retornará imediatamente por essa função, deixando a lista como está. Se um plug-in implementa essa função, ele indicará isso definindo o `SCC_CAP_POPULATELIST` sinalizador de bit de recurso na primeira chamada para o [SccInitialize](../extensibility/sccinitialize-function.md). Por padrão, o plug-in deve sempre considerar todos os itens sendo passados são arquivos. No entanto, se o IDE define o `SCC_PL_DIR` sinalizador no `fOptions` parâmetro, todos os itens que está sendo transmitidos devem ser considerados diretórios. O plug-in deve adicionar todos os arquivos que pertencem a diretórios. O IDE nunca passará uma mistura de arquivos e diretórios.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)