---
title: "Tabela de documento de persistência e execução | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 062c623ec1de779733e41a8abcad8ca478155dba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="persistence-and-the-running-document-table"></a>A tabela de documentos em execução e persistência
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, os projetos são totalmente responsáveis por gerenciar a persistência de seus itens de projeto, eles fazer usando o serviço, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Os documentos são a unidade básica de persistência no ambiente do Visual Studio. Projetos de coordenam a abertura, salvando e renomeação de documentos com a tabela em execução documento (RDT), um recurso que controla o estado de todos os documentos abertos.  
  
## <a name="managing-persistence"></a>Gerenciamento de persistência  
 Projetos de controle de serviço de persistência do ambiente Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interface. Enquanto o ambiente nunca diretamente solicita um documento para manter em si, ele solicita que o projeto proprietário (ou hierarquia) para salvar o documento. Isso torna possível para o projeto salvar seus dados de item de projeto em arquivos locais, arquivos remotos, um banco de dados, um repositório ou outra mídia.  
  
 O ambiente global mantém o RDT. O ambiente mantém as entradas para todas as janelas abertas e documentos em RDT, o que torna possível para que eles possam recebem notificações especiais, como quando uma solução é fechada. Além disso, o RDT possibilita que o ambiente rastrear seus nós correspondentes no **Gerenciador de soluções**. O RDT mantém um registro por objeto aberto, persistente, incluindo arquivos de projeto e item de projeto de documentos.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de documento em execução](../../extensibility/internals/running-document-table.md)   
 [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)