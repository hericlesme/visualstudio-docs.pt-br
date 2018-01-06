---
title: Diretrizes de controle de origem adicionais para projetos e editores | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 308de182e604f06fff9ad25cb65428b2d48ff257
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Diretrizes de controle de origem adicionais para projetos e editores
Há um número de diretrizes de projetos e editores devem aderir para oferecer suporte a controle de origem.  
  
## <a name="guidelines"></a>Diretrizes  
 O projeto ou o editor também deve fazer o seguinte para dar suporte ao controle de origem:  
  
|Área|Projeto|Editor|Detalhes|  
|----------|-------------|------------|-------------|  
|Privada cópias de arquivos|X||O ambiente dá suporte a privada cópias dos arquivos. Ou seja, cada pessoa inscrita no projeto tem sua própria cópia particular dos arquivos no projeto.|  
|ANSI/Unicode persistência|X|X|Se você escrever o código de persistência, manter os arquivos no formato ANSI porque a maioria dos programas de controle de origem atualmente não dão suporte a Unicode.|  
|Enumerar arquivos|X||O projeto deve conter uma lista específica de todos os arquivos dentro dele e deve ser capaz de enumerar a lista de arquivos usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). O projeto também deve expor os nomes de itens por meio de seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementação e suporte a pesquisa de nome (incluindo arquivos especiais) por meio de seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementação.|  
|Formato de texto|X|X|Quando possível, os arquivos devem estar no formato de texto para dar suporte a mesclagem de versões diferentes. Arquivos que não estão no formato de texto não podem ser mesclados com outras versões do arquivo mais tarde. O formato de texto preferido é XML.|  
|Base de referência|X||Referência com base em projetos prontamente têm suporte no controle de origem. No entanto, os projetos baseados em diretório também são suportados pelo controle de origem desde que o projeto pode produzir uma lista dos seus arquivos sob demanda, independentemente de existirem esses arquivos no disco. Ao abrir um projeto do controle de origem, o arquivo de projeto é interrompido primeiro antes de qualquer um dos arquivos.|  
|Manter objetos e propriedades em ordem previsível|X|X|Manter os arquivos em uma ordem previsível, como ordem alfabética, para facilitar a mesclagem.|  
|Recarregar|X|X|Quando um arquivo é alterado no disco, seu editor deve ser capaz de recarregá-lo. Quando você participa de controle de origem, o ambiente será recarregado dados para você, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementação. O caso de recarregar mais difíceis é quando um check-out ocorre quando você chamou IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e processamento de informações. No entanto, seu código de recarregar deve ser capaz de executar essa situação.<br /><br /> O ambiente recarrega automaticamente os arquivos de projeto. No entanto, um projeto deve implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> se tiver aninhado hierarquias para oferecer suporte ao recarregar aninhados arquivos de projeto.|  
  
## <a name="see-also"></a>Consulte também  
 [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)