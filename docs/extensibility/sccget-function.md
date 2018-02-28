---
title: "Função SccGet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 73f5c55b39d855eb084206ef27e2254d50377b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sccget-function"></a>Função SccGet
Essa função recupera uma cópia de um ou mais arquivos para exibição e a compilação, mas não para edição. Na maioria dos sistemas, os arquivos são marcados como somente leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
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
 [in] Matriz de nomes totalmente qualificados dos arquivos a serem recuperados.  
  
 fOptions  
 [in] Sinalizadores de comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Êxito da operação de obtenção.|  
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|  
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não oferece suporte a esta operação.|  
|SCC_E_FILEISCHECKEDOUT|Não é possível obter o arquivo que o usuário tem check-out.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NOSPECIFIEDVERSION|Uma versão inválida ou data/hora especificado.|  
|SCC_E_NONSPECIFICERROR|Falha não específica; arquivo não foi sincronizado.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|  
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado para executar esta operação.|  
  
## <a name="remarks"></a>Comentários  
 Esta função é chamada com uma contagem e uma matriz de nomes de arquivos a serem recuperados. Se o IDE passa o sinalizador `SCC_GET_ALL`, isso significa que os itens na `lpFileNames` não são arquivos, mas diretórios e que todos os arquivos sob controle de origem nos diretórios de determinado devem ser recuperados.  
  
 O `SCC_GET_ALL` sinalizador pode ser combinado com o `SCC_GET_RECURSIVE` sinalizador para recuperar todos os arquivos nos diretórios de determinado e também todos os subdiretórios.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`nunca deve ser passado sem `SCC_GET_ALL`. Além disso, observe que se diretórios C:\A e C:\A\B são ambos repassadas recursiva obtém, C:\A\B e seus subdiretórios serão realmente recuperados duas vezes. É responsabilidade do IDE, e não a fonte de controle do plug-in — para certificar-se de que duplicatas como esta são mantidas fora da matriz.  
  
 Por fim, mesmo que o plug-in de controle de uma origem especificada a `SCC_CAP_GET_NOUI` sinalizador na inicialização, indicando que ele não tem uma interface do usuário para um comando Get, essa função ainda pode ser chamada pelo IDE para recuperar arquivos. O sinalizador simplesmente significa que o IDE não exibe um item de menu Get e que o plug-in não é esperado para fornecer qualquer interface de usuário.  
  
## <a name="renaming-and-sccget"></a>Renomear e SccGet  
 Situação: um usuário faz check-out de um arquivo, por exemplo, a.txt e modifica. Antes de a.txt pode fazer check-in, um segundo usuário renomeia a.txt para b.txt no banco de dados de controle de origem, o check-out b.txt, faz algumas modificações no arquivo e verifica o arquivo de. O primeiro usuário que deseja que as alterações feitas pelo segundo usuário para que o primeiro usuário renomeia a versão local do arquivo a.txt para b.txt e faz um get no arquivo. No entanto, o cache local que mantém o controle de números de versão ainda considera a primeira versão do a.txt é armazenada localmente e assim o controle de origem não é possível resolver as diferenças.  
  
 Há duas maneiras de resolver essa situação em que o cache local de versões de controle de origem se torna fora de sincronia com o banco de dados de controle de origem:  
  
1.  Não permita renomeação de um arquivo de banco de dados de controle de origem que está sendo verificado.  
  
2.  É o equivalente de "excluir antigo" seguido de "Adicionar novo". O seguinte algoritmo é uma maneira de fazer isso.  
  
    1.  Chamar o [SccQueryChanges](../extensibility/sccquerychanges-function.md) função para saber mais sobre a renomeação de a.txt para b.txt no banco de dados de controle de origem.  
  
    2.  Renomear o local a.txt para b.txt.  
  
    3.  Chamar o `SccGet` função a.txt e b.txt.  
  
    4.  Como a.txt não existe no banco de dados de controle de origem, o cache da versão local é limpos das informações de versão a.txt ausente.  
  
    5.  O arquivo b.txt check-out será mesclado com o conteúdo do arquivo b.txt local.  
  
    6.  O arquivo atualizado b.txt agora pode fazer check-in.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)