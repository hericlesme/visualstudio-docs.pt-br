---
title: Registro de um tipo de projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e6c91f2c92dd121cd135aef4291c7f7983206ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134627"
---
# <a name="registering-a-project-type"></a>Registro de um tipo de projeto
Quando você cria um novo tipo de projeto, você deve criar entradas do registro que habilitam [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para reconhecer e trabalhar com o tipo de projeto. Você normalmente cria essas entradas do registro usando um arquivo de script (. rgs) do registro.  
  
 No exemplo a seguir, as instruções do registro fornecem caminhos padrão e dados, onde aplicável, seguido por uma tabela que contém entradas do script do registro para cada instrução. As tabelas fornecem as entradas de script e informações adicionais sobre as instruções.  
  
> [!NOTE]
>  As seguintes informações de registro deve ser um exemplo do tipo e fins de entradas nos scripts de registro, que você escreverá para registrar o tipo de projeto. As entradas reais e seus usos podem variar com base nos requisitos específicos do seu tipo de projeto. Você deve revisar os exemplos disponíveis para localizar aquele parecida com o tipo de projeto que você está desenvolvendo e, em seguida, examine o script de registro para esse exemplo.  
  
 Os exemplos a seguir são de HKEY_CLASSES_ROOT.  
  
## <a name="example"></a>Exemplo  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nome e uma descrição dos arquivos de tipo de projeto que têm a extensão .figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Tipo de conteúdo para os arquivos de projeto.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Ícone padrão usado para um projeto desse tipo. A declaração de % % MODULE é concluída no registro para o local padrão do tipo de projeto DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Aplicativo padrão no qual este tipo de projeto será aberto.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Comando padrão que será executado quando um projeto desse tipo é aberto.|  
  
 Os exemplos a seguir são de HKEY_LOCAL_MACHINE e estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Exemplo  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@` (Padrão)|REG_SZ|`FigPrj Project VSPackage`|Nome localizável deste registrado VSPackage (tipo de projeto).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Caminho da DLL do tipo de projeto. O IDE carrega essa DLL e passa o CLSID VSPackage para `DllGetClassObject` obter <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> para construir o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> objeto.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nome da empresa que desenvolveu o tipo de projeto.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nome para o tipo de projeto.|  
|`ProductVersion`|REG_SZ|`9.0`|Número de versão do tipo de projeto de versão.|  
|`MinEdition`|REG_SZ|`professional`|Edição do VSPackage que está sendo registrado.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|O pacote carregar a chave para o projeto VSPackage. A chave é validada quando um projeto é carregado depois que o ambiente foi iniciado.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nome do arquivo de satélite DLL que contém recursos localizados para o tipo de projeto.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Caminho de DLL satélite.|  
|`FigProjectsEvents`|REG_SZ|Consulte a declaração de valor.|Determina a cadeia de caracteres de texto retornada para este evento de automação.|  
|`FigProjectItemsEvents`|REG_SZ|Consulte a declaração de valor.|Determina a cadeia de caracteres de texto retornada para este evento de automação.|  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Exemplo  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Nome padrão de projetos deste tipo.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID do recurso de nome devem ser recuperados a DLL satélite registrado em pacotes.|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe do VSPackage registrado em pacotes.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho padrão dos arquivos de modelo de projeto. Esses são os arquivos exibidos pelo modelo do novo projeto.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Caminho padrão dos arquivos de modelo de Item de projeto. Estes são os arquivos exibidos pelo modelo adicionar novo Item.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Permite que o IDE implementar o **abrir** caixa de diálogo.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Usado pelo IDE para determinar se o projeto que está sendo aberto é tratado por este tipo de projeto (fábrica de projeto). O formato de mais de uma entrada é uma lista delimitada por ponto e vírgula. Por exemplo, "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Usado pelo IDE como a extensão de nome de arquivo padrão para a operação Salvar como.|  
|`Filter Settings`|REG_DWORD|Vários, consulte as instruções e comentários, a tabela a seguir.|Essas configurações são usadas para definir vários filtros para exibir os arquivos nas caixas de diálogo de interface do usuário.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID de recurso para modelos de Item de adicionar.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|O caminho dos itens de projeto exibido na caixa de diálogo para o **Adicionar Novo Item** modelo.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Determina a ordem de classificação no nó de árvore de arquivos exibidos no **Adicionar Novo Item** caixa de diálogo.|  
  
 A tabela a seguir mostra as opções de filtros disponíveis no segmento de código anterior.  
  
|Opção de filtro|Descrição|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Indica que o filtro é um dos filtros comuns no **localizar nos arquivos** caixa de diálogo. Os filtros comuns são listados na lista de filtros antes dos filtros não marcado como comuns.|  
|`CommonOpenFilesFilter`|Indica que o filtro é um dos filtros comuns no **abrir arquivo** caixa de diálogo. Os filtros comuns são listados na lista de filtros antes dos filtros não marcado como comuns.|  
|`FindInFilesFilter`|Indica que o filtro deve ser um dos filtros no **localizar nos arquivos** caixa de diálogo caixa e serão listados após os filtros comuns.|  
|`NotOpenFileFilter`|Indica que o filtro não será usado no **abrir arquivo** caixa de diálogo.|  
|`NotAddExistingItemFilter`|Indica que o filtro não será usado no adicionar **Item existente** caixa de diálogo.|  
  
 Por padrão, se um filtro não tem um ou mais dos seguintes sinalizadores de conjunto, o filtro é usado no **Add Existing Item** caixa de diálogo e o **abrir arquivo** caixa de diálogo depois que os filtros comuns são listados. O filtro não é usado no **localizar nos arquivos** caixa de diálogo.  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Exemplo  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID de recurso para modelos de projeto novo.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho para projetos do tipo registrado do projeto padrão.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Conjuntos de ordem de classificação dos projetos exibidos na caixa de diálogo Assistente para novos projetos.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que os projetos deste tipo são exibidos somente na caixa de diálogo Novo projeto.|  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Exemplo  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Nenhum|Valor padrão que indica que as entradas a seguir são para as entradas de arquivos diversos projetos.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valor de ID de recurso para os arquivos de modelo de adicionar novos itens.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|O caminho padrão dos itens que serão exibidos no **Adicionar Novo Item** caixa de diálogo.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Estabelece a ordem de classificação para exibição no nó de árvore de **Adicionar Novo Item** caixa de diálogo.|  
  
 O exemplo a seguir está localizado no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Exemplo  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 O item de menu aponta o IDE para o recurso usado para recuperar as informações de menu. Quando esses dados foram mesclados no banco de dados do menu, a mesma chave será adicionada na seção MenusMerged do registro. O VSPackage não deve modificar qualquer coisa na seção MenusMerged diretamente. O campo de dados na tabela a seguir, há três vírgula--campos separados. O primeiro campo identifica um caminho completo de um arquivo de recurso de menu:  
  
-   Se o primeiro campo for omitido, o recurso de menu é carregado do satélite DLL identificado pelo GUID VSPackage.  
  
 O segundo campo identifica uma ID de recurso de menu do tipo CTMENU:  
  
-   Se a ID de recurso é especificada, e o caminho do arquivo é fornecido pelo primeiro parâmetro, um recurso de menu é carregado do caminho de arquivo completo.  
  
-   Se a ID de recurso é fornecida, mas o caminho do arquivo não é, o recurso de menu é carregado da DLL satélite.  
  
-   Se o caminho completo do arquivo for fornecido e a ID de recurso for omitido, o arquivo a ser carregado deve ser um arquivo CTO.  
  
 O último campo identifica o número de versão para o recurso CTMENU. Você pode mesclar o menu novamente, alterando o número de versão.  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|% CLSID_Package %|REG_SZ|`,1000,1`|O recurso para recuperar as informações de menu.|  
  
 Todos os exemplos a seguir estão localizados no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valor de ID de recurso para os modelos de projeto figuras novo projeto.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho padrão do diretório novos projetos. Itens nesse diretório serão exibidos no **Assistente do novo projeto** caixa de diálogo.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Estabelece a ordem na qual projetos serão exibidos no nó de árvore do **novo projeto** caixa de diálogo.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que os projetos deste tipo são exibidos somente no **novo projeto** caixa de diálogo.|  
  
 O exemplo a seguir está localizado no registro na chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe do VSPackage registrado.|  
|`UseInterface`|REG_DWORD|`1`|1 indica que a interface do usuário será usada para interagir com este projeto. 0 indica que não há nenhuma interface do usuário.|  
  
 Arquivos de the.vsz que controlam os novos tipos de projeto frequentemente contêm uma entrada RELATIVE_PATH. Esse caminho é relativo ao caminho especificado na entrada \ProductDir do tipo de projeto na seguinte chave de instalação:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Por exemplo, os modelos de projeto do Enterprise Frameworks adicione as seguintes entradas de registro:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Isso significa que se você incluir um PROJECT_TYPE = EF entrada no arquivo. vsz, localiza o ambiente que seu. vsz arquivos no diretório ProductDir especificado anteriormente.  
  
## <a name="see-also"></a>Consulte também  
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Criar instâncias de projetos usando fábricas de projetos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)