---
title: "Registro e seleção (VSPackage de controle do código-fonte) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 118f715e71f610d4e9dc2589767f6fb54ab4e814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registro e seleção (VSPackage de controle de origem)
Um controle de origem VSPackage deve ser registrado para expô-lo para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se mais de um controle de origem VSPackage é registrado, o usuário pode selecionar quais VSPackage carregar em momentos apropriados. Consulte [VSPackages](../../extensibility/internals/vspackages.md) para obter mais detalhes sobre VSPackages e como registrá-los.  
  
## <a name="registering-a-source-control-package"></a>Registrar um pacote de controle de origem  
 O pacote de controle do código-fonte está registrado para que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente encontrará-lo e consulta para seus recursos com suporte. Isso está de acordo com um esquema de carregamento de atraso no qual uma instância de um pacote é criada somente quando seus recursos e comandos são necessários ou que são solicitados explicitamente.  
  
 VSPackages colocar as informações em uma chave de registro específicos da versão, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, onde *X* é o número de versão principal e *Y* é o número de versão secundária. Essa prática oferece a capacidade de dar suporte à instalação lado a lado de várias versões dos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário (IU) oferece suporte para seleção entre o controle de origem instalado vários plug-ins (por meio do pacote de adaptador de controle de origem), bem como controle de origem VSPackages. Pode haver apenas um plug-in de controle de origem ativa ou VSPackage por vez. No entanto, conforme descrito abaixo, o IDE permite alternar entre os plug-ins de controle de origem e VSPackages por meio de um solução com base em troca de pacote mecanismo automático. Há alguns requisitos por parte do controle de origem VSPackage para habilitar esse mecanismo de seleção.  
  
### <a name="registry-entries"></a>Entradas do registro  
 Um pacote de controle de origem precisa três GUIDs privadas:  
  
-   GUID do pacote: Esse é o GUID do principal para o pacote que contém a implementação de controle de origem (chamada ID_Package nesta seção).  
  
-   GUID de controle de origem: Este é um GUID para o controle de origem VSPackage usada para registrar o Stub de controle de origem Studio Visual e também é usado como um contexto de interface do usuário do comando GUID. O serviço de controle de origem GUID está registrado sob o controle de origem GUID. No exemplo, o GUID do controle de origem é chamado ID_SccProvider.  
  
-   GUID de serviço de controle de origem: Este é o serviço privado GUID usado pelo Visual Studio (chamado SID_SccPkgService nesta seção). Além disso, o pacote de controle de origem precisa definir outros GUIDs para VSPackages, janelas de ferramentas e assim por diante.  
  
 As seguintes entradas do registro devem ser feitas por um controle de origem VSPackage:  
  
|Nome da chave|Entradas|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(padrão) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(padrão) = rg_sz:\<nome amigável do pacote ><br /><br /> Serviço = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(padrão) = rg_sz: #\<ID de recurso para o nome localizado ><br /><br /> Pacote = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Observe que o nome da chave, `SourceCodeControl`, já está sendo usado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e não está disponível como uma opção para \<PackageName >.)|(padrão) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Selecionando um pacote de controle de origem  
 Vários de plug-ins baseada em API de plug-in de controle de origem e VSPackages podem ser registrados simultaneamente de controle de origem. O processo de selecionar um plug-in de controle de origem ou o VSPackage deve garantir que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o plug-in ou VSPackage no momento apropriado e pode adiar a carregar componentes desnecessários até que eles são necessários. Além disso, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve remover todos os da interface do usuário de outros VSPackages inativos, incluindo itens de menu, caixas de diálogo e barras de ferramentas e exibir a interface do usuário para o VSPackage active.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carrega um controle de origem VSPackage quando é executada a qualquer uma das seguintes operações:  
  
-   Solução é aberta (quando a solução estiver sob controle do código-fonte).  
  
     Quando uma solução ou projeto sob controle de origem é aberto, o IDE faz com que o controle de origem VSPackage que foi designado para a solução a ser carregado.  
  
-   Qualquer um dos comandos de menu do controle de origem VSPackage são executados.  
  
 Um controle de origem que VSPackage deve carregar todos os componentes necessários apenas quando eles realmente vai ser usado (conhecido como carregamento atrasado).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Troca automática VSPackage baseado na solução  
 Manualmente, você pode trocar VSPackages de controle de origem por meio de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opções** caixa de diálogo do **controle de origem** categoria. Troca automática de pacotes por solução significa que um pacote de controle de origem que foram designado para uma determinada solução é automaticamente definido como ativa quando essa solução é aberta. Cada pacote de controle de origem deve implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Controla a alternância entre os dois plug-ins de controle (Implementando a API de plug-in de controle de origem) de origem e VSPackages do controle de origem.  
  
 O pacote de adaptador de controle de origem é usado para alternar para qualquer baseada em API de plug-in de controle de origem plug-in. O processo de alternar para o pacote intermediário do adaptador de controle de origem e determinar quais plug-in de controle de origem deve ser definido como ativo ou inativo é transparente ao usuário. O pacote do adaptador está sempre ativo quando qualquer plug-in de controle de origem está ativo. Alternar entre dois valores de plug-ins de controle de origem para simplesmente carregar e descarregar a DLL de plug-in. No entanto, alternar para um controle de origem VSPackage, envolve a interagir com o IDE para carregar o VSPackage apropriado.  
  
 Um controle de origem VSPackage é chamado quando nenhuma solução é aberta e a chave do registro para o VSPackage está no arquivo de solução. Quando a solução é aberta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] localiza o valor do registro e carrega o controle de origem apropriado VSPackage. Controle de origem de todos os VSPackages deve ter as entradas do Registro descritas acima. Uma solução que está sob controle de origem está marcada como sendo associado a um controle de origem em particular VSPackage. Fonte controle VSPackages deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> para habilitar automático com base em solução VSPackage troca.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interface do usuário para seleção de pacote e a alternância de Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornece uma interface do usuário para controle de origem VSPackage e seleção de plug-in no **opções** caixa de diálogo do **controle de origem** categoria. Ele permite que o usuário para selecionar o plug-in de controle de origem ativa ou VSPackage. Inclui uma lista suspensa:  
  
-   Todos os pacotes de controle de origem instalados  
  
-   Todos os instalado plug-ins de controle de origem  
  
-   Opção "Nenhum", que desabilita o controle do código fonte  
  
 A interface de usuário para a opção de controle de origem ativa está visível. A seleção de VSPackage oculta a interface do usuário para o VSPackage anterior e mostra a interface do usuário para uma nova. O VSPackage ativo é selecionado em uma base por usuário. Se um usuário tiver várias cópias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abrir simultaneamente, cada uma delas pode usar um VSPackage active diferente. Se vários usuários fizerem logon no mesmo computador, cada usuário pode ter instâncias separadas do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abrir, cada um com um VSPackage active diferente. Quando várias instâncias do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estão fechados por um usuário, o controle de origem VSPackage que estava ativa para a última solução aberta se torna o controle de origem padrão VSPackage, sejam definidos ativos na reinicialização.  
  
 Diferentemente das versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], uma reinicialização do IDE não é a única maneira de alternar VSPackages de controle de origem. Seleção de VSPackage é automática. Alternância de pacotes requer privilégios de usuário do Windows (não administrador ou usuário avançado).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Recursos](../../extensibility/internals/source-control-vspackage-features.md)   
 [Criando um controle de origem plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)