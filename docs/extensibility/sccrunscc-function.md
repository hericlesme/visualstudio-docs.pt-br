---
title: "Função SccRunScc | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRunScc
helpviewer_keywords: SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ad179325c4f34cd206a3c5e6b0840a69dd46037
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sccrunscc-function"></a>Função SccRunScc
Esta função chama a ferramenta de administração de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 nFiles  
 [in] Número de arquivos especificados na `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nomes de arquivo selecionado.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A ferramenta de administração de controle de origem foi invocada com êxito.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada.|  
|SCC_E_INITIALIZEFAILED|Falha ao inicializar o sistema de controle de origem.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção.|  
|SCC_E_CONNECTIONFAILURE|Falha ao conectar ao sistema de controle de origem.|  
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle de origem.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função permite que o chamador acessar a gama completa de recursos do sistema de controle do código-fonte por meio de uma ferramenta de administração externa. Se o sistema de controle de origem não tem nenhuma interface do usuário, o plug-in de controle de origem pode implementar uma interface para executar funções administrativas necessárias.  
  
 Esta função é chamada com uma contagem e uma matriz de nomes de arquivo para os arquivos selecionados no momento. Se a ferramenta de administração for compatível, a lista de arquivos pode ser usada para previamente os arquivos na interface de administração; Caso contrário, a lista pode ser ignorada.  
  
 Essa função geralmente é chamado quando o usuário seleciona o **iniciar \<servidor de controle de origem >** do **arquivo** -> **controle de origem** menu. Isso **iniciar** opção de menu pode ser sempre desabilitada ou até mesmo ocultada pela configuração de uma entrada de registro. Consulte [como: instalar um plug-in de controle de origem](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obter detalhes. Essa função é chamada apenas se [SccInitialize](../extensibility/sccinitialize-function.md) retorna o `SCC_CAP_RUNSCC` bit de recurso (consulte [sinalizadores de recursos](../extensibility/capability-flags.md) para obter detalhes sobre este e outros elementos de recurso).  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Como: instalar um plug-in de controle de origem](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Sinalizadores de recursos](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)