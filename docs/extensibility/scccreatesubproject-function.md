---
title: "Função SccCreateSubProject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCreateSubProject
helpviewer_keywords: SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce9c4ec33a76afbba1b334fdc5bac5aee17e334
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="scccreatesubproject-function"></a>Função SccCreateSubProject
Esta função cria um subprojeto com o nome especificado em um projeto existente do pai especificado pelo `lpParentProjPath` argumento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 lpUser  
 [out no] O nome de usuário (até SCC_USER_SIZE, incluindo o terminador nulo).  
  
 lpParentProjPath  
 [in] Uma cadeia de caracteres que identifica o caminho do projeto pai (até SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 lpSubProjName  
 [in] O nome sugerido subprojeto (até SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 lpAuxProjPath  
 [out no] Cadeia de caracteres auxiliar que identifica o projeto (até SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 lpSubProjPath  
 [out no] Cadeia de caracteres de saída identifica o caminho para o subprojeto (até SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Subprojeto foi criado com êxito.|  
|SCC_E_INITIALIZEFAILED|Não foi possível inicializar o projeto pai.|  
|SCC_E_INVALIDUSER|O usuário não pôde fazer logon sistema de controle de origem.|  
|SCC_E_COULDNOTCREATEPROJECT|Não é possível criar o subprojeto.|  
|SCC_E_PROJSYNTAXERR|Sintaxe de projeto inválido.|  
|SCC_E_UNKNOWNPROJECT|O projeto pai é desconhecido para o plug-in de controle de origem.|  
|SCC_E_INVALIDFILEPATH|Caminho de arquivo inválido ou inutilizável.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_CONNECTIONFAILURE|Houve um problema de conexão de plug-in de controle de origem.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Se já existir um subprojeto com o nome, a função pode alterar o nome padrão para criar um exclusivo, por exemplo, adicionando "_\<número >" a ele. O chamador deve estar preparado para aceitar as alterações `lpUser`, `lpSubProjPath`, e `lpAuxProjPath`. O `lpSubProjPath` e`lpAuxProjPath` argumentos são usados em uma chamada para o [SccOpenProject](../extensibility/sccopenproject-function.md). Não deve ser modificados pelo chamador após retornar. Essas cadeias de caracteres fornecem uma maneira para o plug-in para rastrear as informações necessárias para associar um projeto de controle de origem. O chamador IDE não exibirá esses dois parâmetros no retorno, porque o plug-in pode usar uma cadeia de caracteres formatada que pode não ser adequada para exibição. A função retorna um código de êxito ou falha e, se for bem-sucedido, preenche a variável `lpSubProjPath` com o caminho completo do projeto para o novo projeto.  
  
 Essa função é semelhante do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), exceto que ele silenciosamente cria um projeto em vez de solicitar que o usuário selecione um. Quando o `SccCreateSubProject` função é chamada, `lpParentProjName` e `lpAuxProjPath` não estará vazio e corresponderá a um projeto válido. Essas cadeias de caracteres geralmente são recebidas pelo IDE de uma chamada anterior para o `SccGetProjPath` função ou o [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 O `lpUser` argumento é o nome de usuário. O IDE passará o mesmo nome de usuário que anteriormente tinha recebido do `SccGetProjPath`, e o plug-in de controle de origem deve usar o nome como padrão. Se o usuário já tiver uma conexão aberta com o plug-in, em seguida, o plug-in deve tentar eliminar os avisos para verificar se que a função funciona silenciosamente. No entanto, se o logon falhar, o plug-in deve solicitar o usuário para um logon e, quando ele recebe um logon válido, passe o nome de volta `lpUser`. Como o plug-in pode alterar essa cadeia de caracteres, o IDE sempre será alocar um buffer de tamanho (SCC_USER_LEN + 1 ou SCC_USER_SIZE, que inclui o espaço para o terminador nulo). Se a cadeia de caracteres for alterada, a nova cadeia de caracteres deve ser um nome de logon válido (pelo menos como válido como a cadeia de caracteres antiga).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Observações técnicas para SccCreateSubProject e SccGetParentProjectPath  
 Adicionando soluções e projetos ao controle de origem foi simplificado no Visual Studio para minimizar o número de vezes que um usuário é solicitado a selecionar locais no sistema de controle de origem. Essas alterações são ativadas pelo Visual Studio se um plug-in de controle de origem dá suporte às duas novas funções, `SccCreateSubProject` e `SccGetParentProjectPath`. No entanto, a seguinte entrada do registro pode ser usada para desabilitar essas alterações e reverter para o comportamento anterior do Visual Studio (origem controle plug-in API versão 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
 Se essa entrada do registro não existe ou é definida como DWORD: 00000000, Visual Studio tenta usar as novas funções, `SccCreateSubProject` e `SccGetParentProjectPath`.  
  
 Se a entrada do registro é definida como DWORD: 00000001, o Visual Studio não tentará usar essas novas funções e as operações de adicionar ao controle de origem funcionam como nas versões anteriores do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)