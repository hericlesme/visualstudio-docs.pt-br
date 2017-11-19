---
title: "Visão geral de extensões de código gerenciado e de gerenciamento de direitos de informação | Microsoft Docs"
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
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ff6c79d6bed7ec1b5a459f64c0e57c8c35ab4e1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Visão geral do Gerenciamento de Direitos de Informação e extensões de código gerenciado
  O Microsoft Office Word e Microsoft Office Excel fornecem gerenciamento de direitos de informação (IRM), um recurso que pode ajudá-lo a evitar que pessoas não autorizadas de exibir ou alterar informações confidenciais. Para obter detalhes sobre como funciona o gerenciamento de direitos de informações, consulte a Ajuda no aplicativo do Office específico.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>Executando o código por trás de documentos com permissões restritas  
 Se sua solução contiver um documento ou a pasta de trabalho que usa o IRM, por padrão, Word e Excel não permitem execução de qualquer código. Se você for o autor do documento ou ter acesso de controle total, você pode alterar o padrão para que a solução funciona. Para obter mais informações, consulte [como: permite que o código executado atrás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM impede o uso de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> para recuperar ou manipular dados armazenados em cache no documento.  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>Usuários finais restringindo as permissões para documentos que usam extensões de código gerenciado  
 Qualquer pessoa que tenha acesso de controle total para o documento ou a pasta de trabalho em sua solução pode usar o IRM para restringir as permissões. Por exemplo, se um usuário final no departamento de contabilidade usa uma solução que preenche automaticamente uma planilha com os dados de um banco de dados, o que o usuário desejar permitir que alterar o acesso somente a pessoas em seu departamento e acesso de leitura a outros. Quando o usuário adiciona as permissões restritas, por padrão, não é possível executar o código por trás da planilha, e a planilha não será populada com dados.  
  
 Para corrigir o problema, uma pessoa com acesso de controle total para o documento ou a pasta de trabalho deve alterar as configurações de permissão padrão para permitir o acesso programático ao modelo de objeto. Para obter mais informações, consulte [como: permite que o código executado atrás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Proteção de documento em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)   
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
  
  