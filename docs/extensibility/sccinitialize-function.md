---
title: "Função SccInitialize | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccInitialize
helpviewer_keywords: SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6bf217218dcc1830cc2acf2833aa7e31e85745d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sccinitialize-function"></a>Função SccInitialize
Essa função inicializa o plug-in de controle de origem e fornece recursos e limites para o ambiente de desenvolvimento integrado (IDE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppvContext`  
 [in] O plug-in de controle de origem pode colocar um ponteiro para a estrutura de contexto aqui.  
  
 `hWnd`  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 `lpCallerName`  
 [in] O nome do programa chamar o controle de origem plug-in.  
  
 `lpSccName`  
 [out no] O buffer em que o plug-in de controle de origem coloca seu próprio nome (não deve exceder `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Retorna o controle de origem sinalizadores de recursos do plug-in.  
  
 `lpAuxPathLabel`  
 [out no] O buffer em que o plug-in de controle de origem coloca uma cadeia de caracteres que descreve o `lpAuxProjPath` parâmetro retornado pelo [SccOpenProject](../extensibility/sccopenproject-function.md) e [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (não deve exceder `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Retorna o comprimento máximo permitido para um comentário de check-out.  
  
 `pnCommentLen`  
 [out] Retorna o comprimento máximo permitido para outros comentários.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Inicialização de controle de origem foi bem-sucedida.|  
|SCC_E_INITIALIZEFAILED|Não foi possível inicializar o sistema.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar a operação especificada.|  
|SCC_E_NONSPECFICERROR|Falha não específica; sistema de controle de origem não foi inicializado.|  
  
## <a name="remarks"></a>Comentários  
 O IDE chama essa função ao ser carregado pela primeira vez o plug-in de controle de origem. Isso permite que o IDE passar a certas informações, como o nome do chamador, para o plug-in. O IDE também obtém de volta certas informações, como o comprimento máximo permitido de comentários e recursos do plug-in.  
  
 O `ppvContext` aponta para um `NULL` ponteiro. O plug-in de controle de origem pode alocar uma estrutura para seu próprio uso e armazenar um ponteiro para a estrutura no `ppvContext`. O IDE irá passar esse ponteiro para todas as outras funções VSSCI API, permitindo que o plug-in para que as informações de contexto disponíveis sem necessidade de armazenamento global e para dar suporte a várias instâncias do plug-in. Essa estrutura deve ser desalocada quando o [SccUninitialize](../extensibility/sccuninitialize-function.md) é chamado.  
  
 O `lpCallerName` e `lpSccName` parâmetros permitem que o IDE e o plug-in de controle de origem para os nomes do exchange. Esses nomes podem ser usados simplesmente para distinguir entre várias instâncias ou, na verdade, eles podem aparecer nos menus ou caixas de diálogo.  
  
 O `lpAuxPathLabel` parâmetro é uma cadeia de caracteres usada como um comentário para identificar o caminho do projeto auxiliar que é armazenado no arquivo de solução e passado para o controle de origem plug-in em uma chamada para o [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]usa a cadeia de caracteres "projeto do SourceSafe:"; outros plug-ins de controle de origem deve abster-se de usar essa cadeia de caracteres específica.  
  
 O `lpSccCaps` parâmetro fornece o controle de origem plug-in um local para armazenar os sinalizadores de bit que indica os recursos do plug-in. (Para obter uma lista completa de funcionalidade os sinalizadores de bit, consulte [sinalizadores de recursos](../extensibility/capability-flags.md)). Por exemplo, se os planos de plug-in para gravar resultados em uma função de retorno de chamada fornecida pelo chamador, o plug-in definiria o recurso bit SCC_CAP_TEXTOUT. Isso seria sinalizar o IDE para criar uma janela de resultados de controle de versão.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Sinalizadores de recurso](../extensibility/capability-flags.md)