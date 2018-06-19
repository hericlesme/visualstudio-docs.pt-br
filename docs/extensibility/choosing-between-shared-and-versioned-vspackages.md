---
title: Escolhendo entre VSPackages compartilhados e com controle de versão | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce7f58d664c6a186146272af16324be2fee90983
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104612"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Escolhendo entre VSPackages compartilhados e com controle de versão
Diferentes versões do Visual Studio podem coexistir no mesmo computador. VSPackages pode dar suporte a qualquer combinação de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versões.  
  
 Você pode habilitar instalações lado a lado de VSPackages por meio de qualquer uma das duas estratégias, a estratégia compartilhada ou a estratégia de versão. Ambos acomodar a presença de várias versões de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e associadas a versões do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 A estratégia compartilhado, um VSPackage é registrado para uso em várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A estratégia de versão, várias DLLs VSPackage são instalados, uma para cada versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que você oferece suporte.  
  
## <a name="shared-vspackages"></a>VSPackages compartilhados  
 Usar um VSPackage compartilhado é apropriado quando você usa o mesmo VSPackage em várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para implementar um VSPackage compartilhado, você deve executar as seguintes etapas:  
  
-   Tornar o VSPackage compatível com várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Duas maneiras de fazer, portanto, estão disponíveis:  
  
    -   Limitar o VSPackage usando somente os recursos da versão mais antiga do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que você oferece suporte.  
  
    -   Programar o VSPackage para adaptar-se para a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no qual ele está sendo executado. Em seguida, se as consultas para serviços mais recentes falhar, o VSPackage pode oferecer outros serviços que têm suporte em versões mais antigas do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registre seu VSPackage adequadamente. Para obter mais informações, consulte [registro VSPackage](../extensibility/internals/vspackage-registration.md) e [gerenciados VSPackage registro](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registre as extensões de arquivo adequadamente. Para obter mais informações, consulte [registro de extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Criar um instalador que implanta o VSPackage para as versões apropriadas dos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [instalando VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [componente gerenciamento](../extensibility/internals/component-management.md).  
  
-   Resolver o problema de colisões de registro. Para obter mais informações, consulte [registro VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Certifique-se de que os arquivos compartilhados e com controle de versão respeitam permitir a instalação de segurança e remoção de várias versões de contagem de referência. Para obter mais informações, consulte [componente gerenciamento](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages com controle de versão  
 Sob a estratégia de VSPackage com controle de versão, você cria um VSPackage para cada versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que você oferece suporte. Isso é apropriado quando você espera tirar proveito dos serviços fornecidos por versões mais recentes do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], porque cada VSPackage pode evoluir sem afetar os outros. No entanto, a estratégia de versão de criação de vários binários, a partir de uma base de código único ou de várias bases de código independente, pode envolver mais desenvolvimento inicial que a estratégia de compartilhado. Além disso, o trabalho de configuração adicional pode ser necessário porque você deve criar um uma instalação separada para cada versão ou uma única instalação que detecta as versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que estão instalados e que oferece suporte a seu VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilidade binária  
 Em geral, a compatibilidade binária permite código nativo VSPackages desenvolvidos com versões anteriores do Visual Studio para ser executado em versões posteriores do Visual Studio. No entanto, há três exceções importantes:  
  
-   Se seu VSPackage se baseia em uma versão específica do common language runtime, ele deve determinar em qual versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está em execução.  
  
-   Um VSPackage pode ter uma dependência em um recurso específico de outro VSPackage ou outro produto. Consequentemente, o VSPackage pode ser executado somente em que a dependência seja satisfeita.  
  
-   Um VSPackage pode ser afetado por uma correção de segurança em um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack ou uma versão posterior do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Nesses casos, um VSPackage desenvolvido com uma versão anterior do [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] não pode ser executado em versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] após a correção de segurança foi aplicada. No entanto, você pode recriar seu pacote com a versão mais recente e também executar em versões anteriores.  
  
 VSPackages gerenciados deve ser criados usando uma versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] que corresponde à versão de destino do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Além de planejamento para a compatibilidade binária para seus binários VSPackage, você também deve considerar a solução e formatos de arquivo de projeto. Se seu VSPackage cria um novo tipo de projeto, você deve decidir se ele pode ser executado em apenas uma versão ou em várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [atualização personalizada projetos](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Consulte também  
 [Instalando VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gerenciamento de componente](../extensibility/internals/component-management.md)