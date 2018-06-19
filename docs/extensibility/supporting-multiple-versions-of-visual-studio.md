---
title: Suporte a várias versões do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 317ec1f214d18989c3b2c5c27fe9df9309239631
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137814"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Suporte a várias versões do Visual Studio
O termo *lado a lado* significa que você pode instalar e manter várias versões de um produto no mesmo computador. Para VSPackages, isso significa que um usuário pode ter várias versões do Visual Studio instaladas no mesmo computador. No entanto, você não pode ter versões lado a lado de seu VSPackages carregados em uma única versão do Visual Studio.  
  
 Antes de fazer o VSPackage capaz de ser carregado no lado a lado versões do Visual Studio, considere o seguinte:  
  
-   Você deve determinar qual estratégia de implementação lado a lado que devem ser seguidas.  
  
     Para obter mais informações, consulte [escolhendo entre compartilhados e com controle de versão VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Seus formatos de arquivo de solução e projeto devem ajustar sua estratégia de implementação.  
  
     Para obter mais informações, consulte [atualização personalizada projetos](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) e [registro de extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   O instalador deve lidar com a sua estratégia de implementação para que os componentes com controle de versão e componentes compartilhados por todas as versões, esteja corretamente instalados e registrados.  
  
     Para obter mais informações, consulte [instalando VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e também [componente gerenciamento](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Instalar uma versão do Visual Studio também instala uma versão correspondente do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por exemplo, a instalação do Visual Studio 2010 e o Visual Studio 2012 no mesmo computador também instala versões 4.0 e 4.5 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], respectivamente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Escolher entre VSPackages compartilhados e com controle de versão](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explica como resolver problemas de lado a lado no seu VSPackage.  
  
 [Registrar extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Descreve como o VSPackage pode registrar as associações de arquivo em um cenário lado a lado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Instalar VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
