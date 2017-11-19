---
title: Registro de modelos de projeto e Item | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c1cb9e31384822dddcdd3668bfb3a54bc2782d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="registering-project-and-item-templates"></a>Registro de modelos de projeto e Item
Tipos de projeto devem registrar os diretórios onde se encontram os modelos de projeto e item de projeto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa as informações de registro associadas os tipos de projeto para determinar o que mostrar o **adicionar novo projeto** e **Adicionar Novo Item** caixas de diálogo.  
  
 Para obter mais informações sobre modelos, consulte [adicionando projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Entradas do registro para projetos  
 Os exemplos a seguir mostram as entradas de registro em HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versão*>. As tabelas a seguir explicam os elementos usados nos exemplos.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|@|REG_SZ|Nome padrão de projetos desse tipo.|  
|DisplayName|REG_SZ|ID do recurso de nome devem ser recuperados a DLL satélite registrado em pacotes.|  
|Pacote|REG_SZ|ID de classe do pacote registrados em pacotes.|  
|ProjectTemplatesDir|REG_SZ|Caminho padrão dos arquivos de modelo de projeto. Os arquivos de modelo de projeto são exibidos pelo **novo projeto** modelo.|  
  
### <a name="registering-item-templates"></a>Modelos de Item do registro  
 Você deve registrar o diretório onde você armazena os modelos de item.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|@|REG_SZ|ID de recurso para modelos de Item de adicionar.|  
|TemplatesDir|REG_SZ|O caminho dos itens de projeto exibido na caixa de diálogo para o **Adicionar Novo Item** assistente.|  
|TemplatesLocalizedSubDir|REG_SZ|ID do recurso de uma cadeia de caracteres que nomeia o subdiretório de TemplatesDir que contém modelos localizados. Porque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o recurso de cadeia de caracteres a partir de DLLs satélites se você tê-los, cada DLL satélite pode conter um nome de subdiretório localizado diferente.|  
|SortPriority|REG_DWORD|Definir SortPriority para controlar a ordem na qual os modelos são exibidos no **Adicionar Novo Item** caixa de diálogo. Valores maiores de SortPriority exibida anteriormente na lista de modelos.|  
  
### <a name="registering-file-filters"></a>Filtros de arquivo de registro  
 Opcionalmente, você pode registrar os filtros que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa quando solicita para nomes de arquivo. Por exemplo, o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrar o o **abrir arquivo** caixa de diálogo:  
  
 **Arquivos do Visual c# (\*. cs,\*. resx,\*Settings,\*. xsd,\*. WSDL);\*. CS,\*. resx,\*Settings,\*. xsd,\*. WSDL)**  
  
 Para dar suporte a registro de vários filtros, cada filtro é registrado no seu próprio subchave sob HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versão*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*subchave*>. O nome da subchave é arbitrário; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignora o nome da subchave e usa apenas seus valores.  
  
 Você pode controlar os contextos em que um filtro é usado Definindo sinalizadores, mostrados na tabela a seguir. Se um filtro não tem qualquer sinalizador definido, ele será listado após os filtros comuns no **Add Existing Item** caixa de diálogo e o **abrir arquivo** caixa de diálogo, mas ele não será usado no **localizar nos arquivos**  caixa de diálogo.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Faz com que o filtro de um dos filtros comuns no **localizar nos arquivos** caixa de diálogo. Filtros comuns são listados na lista de filtros antes dos filtros não marcado como comuns.|  
|CommonOpenFilesFilter|REG_DWORD|Faz com que o filtro de um dos filtros comuns no **abrir arquivo** caixa de diálogo. Filtros comuns são listados na lista de filtros antes dos filtros não marcado como comuns.|  
|FindInFilesFilter|REG_DWORD|Lista o filtro após os filtros comuns a **localizar nos arquivos** caixa de diálogo.|  
|NotOpenFileFilter|REG_DWORD|Indica que o filtro não é usado no **abrir arquivo** caixa de diálogo.|  
|NotAddExistingItemFilter|REG_DWORD|Indica que o filtro não é usado no **Add Existing Item** caixa de diálogo.|  
|SortPriority|REG_DWORD|Defina SortPriority para controlar a ordem na qual os filtros são exibidos. Valores maiores de SortPriority exibida anteriormente na lista de filtros.|  
  
## <a name="directory-structure"></a>Estrutura de diretórios  
 VSPackages pode colocar pastas e arquivos de modelo em qualquer lugar em um disco local ou remoto, como o local está registrado através do ambiente de desenvolvimento integrado (IDE). No entanto, para facilitar a organização, recomendamos a seguinte estrutura de diretório no caminho de instalação do produto.  
  
 \Templates  
  
 \Projects (contém os modelos de projeto)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (contém os itens de projeto)  
  
 \Class  
  
 \Form  
  
 \Web página  
  
 \HelperFiles (contém os arquivos usados em itens de vários arquivos de projeto)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Localizando aplicativos](../../ide/localizing-applications.md)   
 [CATIDs para objetos normalmente usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)