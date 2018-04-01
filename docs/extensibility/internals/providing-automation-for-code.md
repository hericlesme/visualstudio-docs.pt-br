---
title: Fornece automação de código | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e59f3826cbb2ed83510cd98209b4c83f9278397d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="providing-automation-for-code"></a>Fornece automação de código
Não é necessário criar um modelo de automação para seu código. O SDK de ambiente não fornece um exemplo para fazer isso. Para mais informações sobre modelos de código, consulte o <xref:EnvDTE.CodeModel> objeto.  
  
 Para implementar um modelo de código, você deve implementar todas as interfaces que são determinadas pela sua estrutura de dados interno. Os objetos devem ser derivados de `IDispatch` classe.  
  
 Os objetos que você pode estender, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, estão disponíveis a partir de <xref:EnvDTE.Project> de objeto e a seguinte aparência:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Você pode optar por implementar apenas o `CodeModel` ou `FileCodeModel` interface no objeto de retorno de seu `Project` e <xref:EnvDTE.ProjectItem> objetos. Oferece funcionalidade dessa interface apropriada para seu sistema de projeto.  
  
 Se você deseja adicionar recursos, como métodos ou propriedades, que não estão disponíveis no padrão `CodeModel` e `FileCodeModel` interfaces, crie sua própria interface que herda do padrão. Certifique-se de documentá-lo com o sistema de projeto para que os usuários finais Saiba procurá-lo. Retorna a interface padrão, mas o usuário pode chamar o `QueryInterface` método ou a conversão para a interface se ele é conhecido por existir.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)