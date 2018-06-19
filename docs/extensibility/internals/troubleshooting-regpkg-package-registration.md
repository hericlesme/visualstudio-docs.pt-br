---
title: Solucionando problemas de registro do pacote RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4857e41888962a92dced87d63fa2b63161ecac55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137112"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solucionando problemas de registro do pacote RegPkg
> [!NOTE]
>  É a melhor maneira de registrar os pacotes no Visual Studio usando .pkgdef arquivos. Isso permite a implantação de extensão sem a necessidade de acessar o registro do sistema. Arquivos de Pkgdef são criados usando o [CreatePkgDef utilitário](../../extensibility/internals/createpkgdef-utility.md).  
  
 Para registrar um pacote usando RegPkg em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve usar a versão do RegPkg apropriado para seu pacote.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versões de RegPkg relacionadas às versões do pacote  
 Há duas versões do RegPkg. Uma versão é incluída no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Use esta versão para registrar os pacotes que foram criados usando um dos seguintes assemblies:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Ele não pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll anterior.  
  
 A versão anterior do RegPkg pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll. No entanto, ele não pode registrar os pacotes criados com versões posteriores do assembly.  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../../extensibility/internals/vspackages.md)