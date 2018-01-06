---
title: "Códigos de erro | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 13eff6aca9470e88be788fe3fcb625fecc32c2c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-codes"></a>Códigos de erro
Quando uma função de API de plug-in de controle de origem retorna um erro, ele deve ser um dos seguintes códigos de erro. Todos os erros são negativos, avisos ou códigos de erro informativa positivos, e o sucesso é 0.  
  
|Código do erro|Valor|Descrição|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Plug-in suporta a adição de arquivos do controle de origem em duas etapas. Para obter mais informações, consulte [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|O arquivo local é diferente do arquivo do banco de dados de controle de origem (por exemplo, [SccDiff](../extensibility/sccdiff-function.md) podem retornar esse valor).|  
|`SCC_I_RELOADFILE`|5|Arquivo local foi alterado durante a operação de controle de origem. Se possível, o IDE deve recarregar o arquivo.|  
|`SCC_I_FILENOTAFFECTED`|4|O arquivo não é afetado.|  
|`SCC_I_PROJECTCREATED`|3|O projeto foi criado durante a operação de controle de origem (por exemplo, durante uma chamada para [SccOpenProject](../extensibility/sccopenproject-function.md) quando `SCC_OP_CREATEIFNEW` sinalizador for especificado).|  
|`SCC_I_OPERATIONCANCELED`|2|Operação foi cancelada.|  
|`SCC_I_ADV_SUPPORT`|1|Plug-in suporta opções avançadas para o comando especificado. Para obter mais informações, consulte [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Êxito.|  
|`SCC_E_INITIALIZEFAILED`|-1|Erro: Falha na inicialização.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Erro: o projeto é desconhecido.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Erro: não foi possível criar o projeto.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Erro: o arquivo não foi extraído.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Erro: o arquivo já foi extraído.|  
|`SCC_E_FILEISLOCKED`|-6|Erro: o arquivo está bloqueado.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Erro: o arquivo é check-out exclusivo.|  
|`SCC_E_ACCESSFAILURE`|-8|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|`SCC_E_CHECKINCONFLICT`|-9|Erro: Houve um conflito durante o check-in.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Erro: o arquivo já existe.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Erro: o arquivo não está sob controle de origem.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Erro: o arquivo foi extraído.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Erro: não há nenhuma versão especificada.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Erro: não há suporte para a operação.|  
|`SCC_E_NONSPECIFICERROR`|-15|Erro não específico.|  
|`SCC_E_OPNOTPERFORMED`|-16|Erro, a operação não foi executado.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Erro: o tipo de arquivo, por exemplo, binário, não há suporte ao sistema de controle do código de origem.|  
|`SCC_E_VERIFYMERGE`|-18|Arquivo tiver sido mesclados automaticamente, mas não foi verificado porque ela é a verificação de usuário pendentes.|  
|`SCC_E_FIXMERGE`|-19|Arquivo tiver sido mesclados automaticamente, mas não tiver sido incluído devido a um conflito de mesclagem deve ser resolvido manualmente.|  
|`SCC_E_SHELLFAILURE`|-20|Erro devido a uma falha de shell.|  
|`SCC_E_INVALIDUSER`|-21|Erro: o usuário é inválido.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Erro: o projeto já está aberto.|  
|`SCC_E_PROJSYNTAXERR`|-23|Erro de sintaxe do projeto.|  
|`SCC_E_INVALIDFILEPATH`|-24|Erro: o caminho do arquivo é inválido.|  
|`SCC_E_PROJNOTOPEN`|-25|Erro: o projeto não está aberto.|  
|`SCC_E_NOTAUTHORIZED`|-26|Erro: o usuário não autorizado para executar esta operação.|  
|`SCC_E_FILESYNTAXERR`|-27|Erro de sintaxe de arquivo.|  
|`SCC_E_FILENOTEXIST`|-28|Erro, o arquivo local não existe.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Erro: Ocorreu uma falha de conexão.|  
|`SCC_E_UNKNOWNERROR`|-30|Erro desconhecido.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operação de obtenção do plano de fundo está em andamento.|  
  
## <a name="macros-provided-for-quick-checking"></a>Macros fornecidas para verificação rápida  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Comentários  
 Todas as funções de API de plug-in de controle do código-fonte (exceto o [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), e [SccDiff](../extensibility/sccdiff-function.md)) devem ter sucesso quando os arquivos locais que são transmitidos como argumentos não existe na pasta de trabalho. Por exemplo, o IDE pode emitir uma chamada para o [SccCheckout](../extensibility/scccheckout-function.md) ou [SccUncheckout](../extensibility/sccuncheckout-function.md) em um arquivo que não existe na pasta de trabalho, mas existe no sistema de controle de origem. Essa chamada será bem-sucedida. Somente quando nenhum arquivo na pasta de trabalho ou no sistema de controle de origem é a função espera falhe.  
  
 Determinadas funções, como `SccAdd` e `SccCheckin`, especificamente deve retornar `SCC_E_FILENOTEXIST` quando o arquivo na pasta de trabalho não existe. Outras funções devem ter êxito quando o arquivo de trabalho não existe, se as funções operam em um nome de arquivo válido no sistema de controle de origem.  
  
 O plug-in de controle de origem não deve fazer nenhuma suposição sobre privilégios em um arquivo na pasta de trabalho, mesmo que o plug-in que foi marcada o arquivo somente leitura durante alguma operação. Um arquivo na pasta de trabalho pode ser movido, excluído e alterado fora de controle do plug-in.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)