---
title: "Criando pastas de contêiner pai para soluções | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea901fe4e380fd867db1c63e44bc1cb6e144feb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>Criando pastas de contêiner pai para soluções
Na API plug-in para fonte de controle de versão 1.2, um usuário pode especificar um destino de controle de origem de raiz única para todos os projetos da Web dentro da solução. Essa única raiz é chamado de um Super unificado raiz (SUR).  
  
 A fonte de controle de plug-in API versão 1.1, se o usuário tiver adicionado uma solução multiprojeto ao controle de origem, o usuário foi solicitado para especificar um destino de controle de origem para cada projeto da Web.  
  
## <a name="new-capability-flags"></a>Novo sinalizadores de recursos  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Novas funções  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE quase sempre criará uma pasta SUR ao adicionar uma solução ao controle de origem. Especificamente, isso é feito nos seguintes casos:  
  
-   O projeto é um compartilhamento de arquivos de projeto da Web.  
  
-   Existem diferentes unidades para o projeto e o arquivo de solução.  
  
-   Não há compartilhamentos diferentes para o projeto e o arquivo de solução.  
  
-   Projetos foram adicionados separadamente (em uma solução de controle do código-fonte).  
  
 Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sugere-se que o nome para a pasta SUR seja o mesmo que o nome da solução sem a extensão. A tabela a seguir resume o comportamento em duas versões.  
  
|Recurso|tSource 1.1 de versão de API de plug-in de controle|Versão 1.2 do API de plug-in de controle de origem|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Adicionar solução ao SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Adicionar o projeto à solução de controle do código-fonte|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Observação:** Visual Studio pressupõe que uma solução é um filho direto do SUR o.|  
  
## <a name="examples"></a>Exemplos  
 A tabela a seguir lista exemplos de dois. Em ambos os casos, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuário será solicitado a fornecer um local de destino para a solução sob controle de origem até que o *user_choice* é especificado como um destino. Quando o user_choice for especificado, a solução e dois projetos são adicionados sem avisar o usuário para destinos de controle de origem.  
  
|Solução contém|Em locais de disco|Estrutura do banco de dados padrão|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> WEB2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 A pasta SUR e subpastas são criadas independentemente da operação foi cancelada ou falha devido a um erro. Eles não serão removidos automaticamente em condições de erro ou Cancelar.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]o padrão de comportamento da versão 1.1 se o plug-in de controle de origem não retornar `SCC_CAP_CREATESUBPROJECT` e `SCC_CAP_GETPARENTPROJECT` sinalizadores de recursos. Além disso, os usuários de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pode escolher reverter para o comportamento da versão 1.1, definindo o valor da seguinte chave como DWORD: 00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na Versão 1.2 da API do plug-in de controle de código-fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)