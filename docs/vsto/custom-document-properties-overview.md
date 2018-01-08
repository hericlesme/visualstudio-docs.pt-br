---
title: "Visão geral de propriedades de documento personalizadas | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0a670510a7898b38ec7f61a22f8258015b112151
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-document-properties-overview"></a>Visão geral de propriedades de documento personalizadas
  Quando você compila um projeto no nível do documento, o Visual Studio adiciona duas propriedades personalizadas para o documento no projeto: assemblylocation e AssemblyName. Quando um usuário abre um documento, o aplicativo do Microsoft Office procura essas propriedades de documento personalizadas. Se existirem no documento, o aplicativo carrega o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], que inicia a personalização. Para obter mais informações, consulte [arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="assemblyname"></a>AssemblyName  
 Esta propriedade contém o CLSID de uma interface no componente de carregador de solução do Office da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. O valor CLSID é 4E3C66D5 - 58D 4-491E-A7D4-64AF99AF6E8B. Você nunca deve alterar esse valor.  
  
## <a name="assemblylocation"></a>Assemblylocation  
 Esta propriedade contém uma cadeia de caracteres que fornece detalhes sobre o manifesto de implantação para a personalização. Para obter mais informações sobre manifestos, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 O valor da propriedade The_AssemblyLocation pode ter diferentes formatos, dependendo de como a solução é implantada:  
  
-   Se a solução for publicada para ser instalado a partir de um site da Web, o caminho UNC ou um CD ou unidade USB, a propriedade assemblylocation tem o formato *DeploymentManifestPath*|*ID da solução*. A cadeia de caracteres a seguir está um exemplo:  
  
     file://deployserver/MyShare/ExcelWorkbook1.VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9  
  
-   Se você estiver em execução ou depuração a solução do Visual Studio, a propriedade assemblylocation tem o formato *DeploymentManifestName*|*ID da solução*| vstolocal. A cadeia de caracteres a seguir está um exemplo:  
  
     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal  
  
 O *ID da solução* é um GUID que o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usa para identificar a solução. O *ID da solução* é gerado automaticamente quando você compilar o projeto. O **vstolocal** termo indica para o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que o assembly deve ser carregado na mesma pasta que o documento.  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)   
 [Manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Como: publicar uma solução do Office usando ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Como criar e modificar propriedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  