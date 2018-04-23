---
title: Determinar se deve implementar um VSPackage de controle do código-fonte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 203144e5b262c093204fe9eafa3a2a5db85eccb3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Determinar se deve implementar um VSPackage de controle do código-fonte
Esta seção aborda as opções de plug-ins de controle de origem e de controle de origem VSPackages para estender o controle de origem soluções e fornece diretrizes gerais sobre como escolher um caminho de integração adequada.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solução de controle de origem pequeno com recursos limitados  
 Se você tiver recursos limitados e não pode ser sobrecarregado com a sobrecarga de gravação de um pacote de controle de origem, você pode criar plug-ins baseada em API de plug-in de controle de origem. Isso permite que você trabalhe lado a lado com pacotes de controle de origem, e você pode alternar entre plug-ins de controle do código-fonte e pacotes sob demanda. Para obter mais informações, consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solução de controle de origem grandes com um conjunto avançado de recursos  
 Se você quiser implementar uma solução de controle de origem que fornece um modelo de controle de origem avançada que não é capturado adequadamente usando a API de plug-in de controle de origem, você pode considerar um pacote de controle de origem como o caminho de integração. Isso se aplica especialmente se você substituiria o pacote de adaptador de controle de origem (que se comunica com plug-ins de controle de origem e fornece um controle de origem básico da interface do usuário) em vez disso, com seus próprios para que você pode manipular os eventos de controle de origem de forma personalizada. Se você já tiver uma fonte satisfatório controlar a interface do usuário e deseja preservar essa experiência em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], a opção de pacote de controle de origem permite fazer exatamente isso. O pacote de controle de origem não é genérico e destina-se somente para uso com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Se você quiser implementar uma solução de controle de origem que fornece a flexibilidade e maior controle sobre a lógica de controle de origem e a interface do usuário, talvez você prefira a rota de integração do pacote de controle de origem. Você pode:  
  
1.  Registrar seu próprio controle de origem VSPackage (consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Substitua o controle da fonte padrão da interface do usuário com a interface do usuário personalizada (consulte [Interface de usuário personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Especifique os glifos a ser usada e tratar eventos de glifo de Gerenciador de soluções (consulte [controle de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Manipular eventos de consulta editar e salvar consulta (consulte [consulta Editar consulta salvar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Consulte também  
 [Criar um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)