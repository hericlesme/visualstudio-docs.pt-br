---
title: Registrando extensões de nome de arquivo para implantações lado a lado | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e80aa90c5fcb6d223e63df6ed740e0295dd3adf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475640"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrando extensões de nome de arquivo para implantações lado a lado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [registrando extensões de nome de arquivo para implantações lado a lado](https://docs.microsoft.com/visualstudio/extensibility/registering-file-name-extensions-for-side-by-side-deployments).  
  
VSPackages implantado em um ambiente lado a lado, você deve registrar as extensões de nome de arquivo para associar os arquivos com a versão correta do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. A menos que você use uma extensão de nome de arquivo específicos da versão, o registro permite aos usuários abrir seu projeto e arquivos de item na versão apropriada do projeto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sobre as extensões de nome de arquivo](../extensibility/about-file-name-extensions.md)  
 Discute como extensões de nome de arquivo são registradas.  
  
 [Especificar identificadores de arquivo para extensões de nome de arquivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fornece informações sobre como registrar os aplicativos que podem abrir, editar e assim por diante, uma extensão de nome de arquivo específico.  
  
 [Registrar verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Discute como registrar verbos.  
  
 [Gerenciar associações de arquivo lado a lado](../extensibility/managing-side-by-side-file-associations.md)  
 Discute como lidar com instalações lado a lado em que uma versão específica do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deve ser invocado para abrir um arquivo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Fornecer suporte à várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Descreve os problemas relacionados a várias versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e o VSPackage durante o desenvolvimento e implantação para os usuários finais.

