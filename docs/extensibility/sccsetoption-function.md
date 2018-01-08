---
title: "Função SccSetOption | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccSetOption
helpviewer_keywords: SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70fe624984adce58191ee7d354185eac0bb527ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sccsetoption-function"></a>Função SccSetOption
Esta função define opções que controlam o comportamento do plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 nOption  
 [in] A opção que está sendo definida.  
  
 dwVal  
 [in] Configurações para a opção.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A opção foi definida com êxito.|  
|SCC_I_SHARESUBPROJOK|Retornado se `nOption` foi `SCC_OPT_SHARESUBPROJ` e o plug-in de controle de origem permite que o IDE definir a pasta de destino.|  
|SCC_E_OPNOTSUPPORTED|A opção não foi definida e não deve ser considerada.|  
  
## <a name="remarks"></a>Comentários  
 O IDE chama esta função para controlar o comportamento do plug-in de controle de origem. O primeiro parâmetro, `nOption`, indica o valor que está sendo definido, enquanto o segundo, `dwVal`, indica o que fazer com esse valor. O plug-in armazena essas informações associadas com um `pvContext``,` IDE deve chamar esta função depois de chamar o [SccInitialize](../extensibility/sccinitialize-function.md) (mas não necessariamente após cada chamada para o [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Resumo das opções e seus valores:  
  
|`nOption`|`dwValue`|Descrição|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita/desabilita em segundo plano enfileiramento de mensagens de evento.|  
|`SCC_OPT_USERDATA`|Valor arbitrário|Especifica um valor de usuário a serem passados para o [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) função de retorno de chamada.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se o IDE atualmente suporta o cancelamento de uma operação.|  
|`SCC_OPT_NAMECHANGEPFN`|Ponteiro para o [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) função de retorno de chamada|Define um ponteiro para uma função de retorno de chamada de alteração de nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se o IDE permite a verificação de fora de seus arquivos manualmente (com a interface de usuário de controle de origem) ou se eles devem fazer check-out apenas por meio do plug-in de controle de origem.|  
|`SCC_OPT_SHARESUBPROJ`|N/D|Se o plug-in de controle de origem permite que o IDE especificar a pasta local do projeto, o plug-in retornará `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Se `nOption` é `SCC_OPT_EVENTQUEUE`, o IDE é desabilitar (ou reabilitar) processamento em segundo plano. Por exemplo, durante uma compilação, o IDE pode instruir o plug-in para interromper o processamento ocioso em qualquer tipo de controle de origem. Após a compilação, ele seria reabilitar o processamento em segundo plano para manter fila de eventos do plug-in atualizado. Correspondente para o `SCC_OPT_EVENTQUEUE` valor `nOption`, há dois valores possíveis para `dwVal`, ou seja, `SCC_OPT_EQ_ENABLE` e `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Se o valor de `nOption` é `SCC_OPT_HASCANCELMODE`, o IDE permite aos usuários cancelar operações longas. Configuração `dwVal` para `SCC_OPT_HCM_NO` (o padrão) indica que o IDE não tem nenhum modo de cancelamento. O plug-in de controle de origem deve oferecer seu próprio botão Cancelar se desejar que o usuário poderá cancelar. `SCC_OPT_HCM_YES`indica que o IDE fornece a capacidade de cancelar uma operação, o SCC plug-in não necessário exibir seu próprio botão Cancelar. Se o IDE define `dwVal` para `SCC_OPT_HCM_YES`, prepare-se para responder a `SCC_MSG_STATUS` e `DOCANCEL` mensagens enviadas para o `lpTextOutProc` função de retorno de chamada (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Se o IDE não definir essa variável, o plug-in não deve enviar essas duas mensagens.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Se nOption for definido como `SCC_OPT_NAMECHANGEPFN`e de origem permitem plug-in de controle e o IDE, o plug-in pode, na verdade, renomear ou mover um arquivo durante uma operação de controle de origem. O `dwVal` será definida como um ponteiro de função de tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante uma operação de controle de origem, o plug-in pode chamar essa função, passando três parâmetros. Esses são o nome antigo (com o caminho totalmente qualificado) de um arquivo, o novo nome (com o caminho totalmente qualificado) do arquivo e um ponteiro para informações que têm relevância para o IDE. O IDE envia esse ponteiro última chamando `SccSetOption` com `nOption` definida como `SCC_OPT_USERDATA`, com `dwVal` apontando para os dados. Suporte para essa função é opcional. Um plug VSSCI-que usa essa capacidade deve inicializar suas função ponteiro dados variáveis de usuário e a `NULL`, e ele não deve chamar uma função de renomeação, a menos que ele tem um. Ele também deverá estar preparado para manter o valor foi fornecido ou alterá-lo em resposta a uma nova chamada para `SccSetOption`. Isso não acontece no meio de uma operação de comando de controle de origem, mas isso pode ocorrer entre comandos.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Se nOption for definido como `SCC_OPT_SCCCHECKOUTONLY`, o IDE está indicando que os arquivos no projeto aberto no momento devem nunca fazer check-out manualmente por meio da interface do usuário do sistema de controle de origem. Em vez disso, os arquivos devem fazer check-out apenas por meio do controle de origem de plug-in no controle do IDE. Se `dwValue` é definido como `SCC_OPT_SCO_NO`, isso significa que os arquivos devem ser tratados normalmente por plug-in e podem fazer check-out por meio do controle de origem da interface do usuário. Se `dwValue` é definido como `SCC_OPT_SCO_YES`, em seguida, somente o plug-in pode fazer check-out de arquivos e interface de usuário do sistema de controle de origem não deve ser chamado. Isso é para situações em que o IDE pode ter "pseudo arquivos" que fazem sentido fazer check-out apenas por meio do IDE.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Se`nOption` é definido como `SCC_OPT_SHARESUBPROJ`, o IDE é o teste se o plug-in de controle de origem pode usar uma pasta local especificada ao adicionar arquivos do controle de origem. O valor de `dwVal` parâmetro não faz diferença nesse caso. Se o plug-in permite que o IDE especificar a pasta de destino local onde os arquivos serão adicionados de fonte de controlar quando o [SccAddFromScc](../extensibility/sccaddfromscc-function.md) é chamado, o plug-in deve retornar `SCC_I_SHARESUBPROJOK` quando o `SccSetOption` é de função chamado. O IDE, em seguida, usa o `lplpFileNames` parâmetro o `SccAddFromScc` função passar na pasta de destino. O plug-in usa essa pasta de destino para colocar os arquivos adicionados do controle de origem. Se o plug-in não retornar `SCC_I_SHARESUBPROJOK` quando o `SCC_OPT_SHARESUBPROJ` opção for definida, o IDE assume que o plug-in é capaz de adicionar arquivos apenas na pasta local atual.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)