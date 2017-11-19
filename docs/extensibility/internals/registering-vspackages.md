---
title: Registrando VSPackages | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d580d3d74d8648b7181ac1ca384d3232fa8225b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="registering-vspackages"></a>Registrando VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]se baseia em arquivos de .pkgdef para descrever e localizar um VSPackage. Um arquivo .pkgdef contém todas as informações de registro que outra forma seriam adicionadas ao registro do sistema. VSPackages gerenciados são registrados por adicionar atributos ao código-fonte e, em seguida, executar o [CreatePkgDef utilitário](../../extensibility/internals/createpkgdef-utility.md) no assembly resultante para gerar um arquivo de .pkgdef.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Especificar o local do arquivo VSPackage ao Shell do VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descreve o caminho de carregamento para VSPackages.  
  
 [Registrar e cancelar o registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica como registrar um VSPackage.  
