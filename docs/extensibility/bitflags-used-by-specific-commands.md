---
title: Os sinalizadores de bit usados por comandos específicos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bc59c79e0f047cc7880332c4c23643ab2136c86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108780"
---
# <a name="bitflags-used-by-specific-commands"></a>Sinalizadores de bit usados por comandos específicos
O comportamento de um número de funções da API de plug-in de controle de origem pode ser modificado, definindo um ou mais bits em um único valor. Esses valores são conhecidos como os sinalizadores de bit. O sinalizadores de bit vários utilizada a API de plug-in de controle de origem são detalhados aqui, agrupados por função em que os utiliza.  
  
## <a name="checked-out-flag"></a>Check-Out de sinalizador  
 Este sinalizador pode ser definido para qualquer um de [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Manter o arquivo com check-out.|  
  
## <a name="add-flags"></a>Adicione sinalizadores  
 Esses sinalizadores são usados pelo [SccAdd](../extensibility/sccadd-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|O plug-in de controle de origem é esperado para detectar automaticamente se o arquivo é texto ou binário.|  
|`SCC_FILETYPE_TEXT`|0x01|Tipo de arquivo é texto.|  
|`SCC_FILETYPE_BINARY`|0x04|Tipo de arquivo é binário. **Observação:** `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` sinalizadores são mutuamente exclusivos.   Defina exatamente um ou nenhum.|  
|`SCC_ADD_STORELATEST`|0x02|Armazenar a versão mais recente somente (sem deltas).|  
  
## <a name="diff-flags"></a>Sinalizadores de comparação  
 O [SccDiff](../extensibility/sccdiff-function.md) usa esses sinalizadores para definir o escopo de uma operação de comparação. O `SCC_DIFF_QD_xxx` sinalizadores são mutuamente exclusivos. Se qualquer um deles for especificado, nenhum comentário visual é receber. Em um "comparação rápido" (QD), o plug-in não determina como o arquivo é diferente, apenas se ele for diferente. Se nenhuma desses sinalizadores for especificados, que um "comparação visual" é feito; diferenças de arquivo detalhadas são computadas e exibidas. Se o QD solicitada não é suportada, o plug-in será movido para o próximo melhor. Por exemplo, se o IDE solicita uma soma de verificação e o plug-in não suporte para isso, o plug-in não um conteúdo completo Verifique (ainda muito mais rápido do que uma exibição visual).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignore diferenças de maiusculas.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignore as diferenças de espaço em branco. **Observação:** o `SCC_DIFF_IGNORECASE` e `SCC_DIFF_IGNORESPACE` sinalizadores são os sinalizadores de bit opcional.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD comparando o conteúdo do arquivo inteiro.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD pela soma de verificação.|  
|`SCC_DIFF_QD_TIME`|0x0040|QD pelo carimbo de data/hora do arquivo.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Esta é uma máscara usada para verificar se todos os de sinalizadores de QD aos bit. Não deve ser passado para uma função; os QD três os sinalizadores de bit são mutuamente exclusivos. QD sempre não significa nenhuma exibição da interface do usuário.|  
  
## <a name="populatelist-flag"></a>Sinalizador de PopulateList  
 Este sinalizador é usado pelo [SccPopulateList](../extensibility/sccpopulatelist-function.md) no `fOptions` parâmetro.  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|O IDE está passando diretórios, não arquivos.|  
  
## <a name="populatedirlist-flags"></a>Sinalizadores de PopulateDirList  
 Esses sinalizadores são usados pelo [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) no `fOptions` parâmetro.  
  
|Valor de opção|Valor|Descrição|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Examine a somente um nível de diretórios para diretórios (esse é o padrão).|  
|SCC_PDL_RECURSIVE|0x0001|Recursivamente examinar todos os diretórios em cada diretório especificado.|  
|SCC_PDL_INCLUDEFILES|0x0002|Inclua nomes de arquivo no processo de verificação.|  
  
## <a name="openproject-flags"></a>Sinalizadores de OpenProject  
 Esses sinalizadores são usados pelo [SccOpenProject](../extensibility/sccopenproject-function.md) no `dwFlags` parâmetro.  
  
|Valor de opção|Valor|Descrição|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Se o projeto não existe no controle de origem, crie-o. Se este sinalizador não for definido, solicitar o usuário para o projeto para criar (a menos que `SCC_OP_SILENTOPEN` sinalizador for especificado).|  
|SCC_OP_SILENTOPEN|0x00000002L|Não solicitar ao usuário para criar um projeto; retorne `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Obtém sinalizadores  
 Esses sinalizadores são usados pelo [SccGet](../extensibility/sccget-function.md) e [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|O IDE é a transmissão de diretórios, arquivos não: obter todos os arquivos nesses diretórios.|  
|`SCC_GET_RECURSIVE`|0x00000002L|O IDE está passando diretórios: obter esses diretórios e todos os seus subdiretórios.|  
  
## <a name="noption-values"></a>Valores de nOption  
 Esses sinalizadores são usados pelo [SccSetOption](../extensibility/sccsetoption-function.md) no `nOption` parâmetro.  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Definir status da fila de eventos.|  
|`SCC_OPT_USERDATA`|0x00000002L|Especificar dados de usuário para `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|O IDE pode manipular Cancelar|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Defina um retorno de chamada para alterações de nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Desabilitar o controle plug-in da interface do usuário check-out fonte e não definir diretório de trabalho.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Adicione do sistema de controle de origem para especificar um diretório de trabalho. Tente compartilhar no projeto associado, se for um descendente direto.|  
  
## <a name="dwval-bitflags"></a>dwVal os sinalizadores de bit  
 Esses sinalizadores são usados pelo [SccSetOption](../extensibility/sccsetoption-function.md) no `dwVal` parâmetro.  
  
|Sinalizador|Valor|Descrição|Usado por `nOption` valor|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende a atividade de fila de evento.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita o log de eventos de fila.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Padrão) Tem o modo sem cancelar; plug-in deve fornecer se desejado.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE manipula Cancelar.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Padrão) Okey fazer check-out do plug-in da interface do usuário; definir o diretório de trabalho.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Nenhum plug-in check-out da interface do usuário, nenhuma pasta de trabalho.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)