---
title: Decisões de Design do controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4c1a512e104a092ae98ac86dc5e731fd1732aa33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-design-decisions"></a>Decisões de Design de controle do código-fonte
As decisões de design a seguir devem ser consideradas para projetos ao implementar o controle de origem.  
  
## <a name="will-information-be-shared-or-private"></a>Informações serão compartilhadas ou privada?  
 O mais importante decisão de design, que você pode fazer é quais informações são compartilháveis e o que é particular. Por exemplo, a lista de arquivos para o projeto compartilhada, mas dentro dessa lista de arquivos, alguns usuários talvez queira ter arquivos particulares. Configurações do compilador são compartilhadas, mas o projeto de inicialização é geralmente particular. As configurações são puramente compartilhados, compartilhados com uma substituição ou puramente privada. Por design, itens particulares, como arquivos de (configuração. suo), opções de usuário de solução não são verificadas em [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Certifique-se de armazenar informações particulares em arquivos particulares, como o arquivo. suo ou um arquivo privado específico, você cria, por exemplo, um. csproj.user arquivo para o Visual c# ou. arquivo vbproj.user do Visual Basic.  
  
 Essa decisão não está completa e pode ser feita em uma base de item por item.  
  
## <a name="will-the-project-include-special-files"></a>O projeto inclui arquivos especiais?  
 Outra decisão de design importante é se a estrutura do projeto usa arquivos especiais. Arquivos especiais são arquivos ocultos subjacentes os arquivos que são caixas de diálogo visível no Gerenciador de soluções e no check-in e check-out. Se você usar arquivos especiais, siga estas diretrizes:  
  
1.  Não associe arquivos especiais no nó raiz do projeto — ou seja, com o projeto de arquivos em si. O arquivo de projeto deve ser um único arquivo.  
  
2.  Quando arquivos especiais são adicionados, removidos ou renomeados em um projeto, apropriado <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> os eventos devem ser disparados com o conjunto de sinalizador que indica que os arquivos são arquivos especiais. Esses eventos são chamados pelo ambiente em resposta ao projeto de chamada apropriada <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos.  
  
3.  Quando o projeto ou o editor chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> para um arquivo, os arquivos especiais associados a esse arquivo não são automaticamente checked out. Passe os arquivos especiais junto com o arquivo pai. O ambiente detectará a relação entre todos os arquivos que são transmitidos e ocultar adequadamente os arquivos especiais na IU do check-out.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)