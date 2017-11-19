---
title: Exibindo arquivos usando o comando Abrir arquivo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2cbcb6e6239552ae32c817601634587a2fe3a41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Exibindo arquivos usando o comando Abrir arquivo
As etapas a seguir descrevem como o IDE manipula o **abrir arquivo** comando, que está disponível na **arquivo** menu em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. As etapas também descrevem como projetos devem responder a chamadas que se originam esse comando.  
  
 Quando um usuário clica o **abrir arquivo** comando o **arquivo** menu e seleciona um arquivo do **abrir arquivo** caixa de diálogo, o seguinte processo ocorre.  
  
1.  Usando a tabela de documento em execução, o IDE determina se o arquivo já está aberto em um projeto.  
  
    -   Se o arquivo estiver aberto, o IDE resurfaces a janela.  
  
    -   Se o arquivo não estiver aberto, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para cada projeto para determinar qual projeto pode abrir o arquivo de consulta.  
  
        > [!NOTE]
        >  Em sua implementação do projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, forneça um valor de prioridade que indica o nível no qual seu projeto abre o arquivo. Valores de prioridade são fornecidos no <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeração.  
  
2.  Cada projeto responde com um nível de prioridade que indica a importância coloca em que está sendo o projeto para abrir o arquivo.  
  
3.  O IDE usa os critérios a seguir para determinar qual projeto abre o arquivo:  
  
    -   O projeto que responde com a prioridade mais alta (DP_Intrinsic) abre o arquivo. Se mais de um projeto responde com essa prioridade, o projeto primeiro a responder abre o arquivo.  
  
    -   Se nenhum responde de projeto com a prioridade mais alta (DP_Intrinsic), mas responde de todos os projetos com a prioridade mais baixa, mesmo, o projeto ativo abre o arquivo. Se nenhum projeto estiver ativo, o projeto primeiro a responder abre o arquivo.  
  
    -   Se nenhum projeto declarações apropriar do arquivo (DP_Unsupported), o projeto arquivos diversos abre o arquivo.  
  
         Se uma instância do projeto arquivos diversos for criada, o projeto sempre responde com o valor DP_CanAddAsExternal. Esse valor indica que o projeto pode abrir o arquivo. Este projeto é usado para hospedar arquivos abertos que não estão em qualquer outro projeto. A lista de itens neste projeto não é persistente; Este projeto está visível no **Solution Explorer** apenas quando ele é usado para abrir um arquivo.  
  
         Se o projeto arquivos diversos não indica que ele pode abrir o arquivo, uma instância do projeto não foi criada. Nesse caso, o IDE cria uma instância do projeto arquivos diversos e informa o projeto para abrir o arquivo.  
  
4.  Assim que o IDE determina qual projeto abre o arquivo, ele chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método no projeto.  
  
5.  O projeto, em seguida, tem a opção de abrir o arquivo usando um editor específico do projeto ou um editor padrão. Para obter mais informações, consulte [como: editores específicos de projeto abertos](../../extensibility/how-to-open-project-specific-editors.md) e [como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md), respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Exibindo arquivos usando a abrir com o comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Como abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)