---
title: Atrasado o carregamento de documentos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc10d7807633433b38fa8587d41c2ac3c0273ebe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="delayed-document-loading"></a>Atraso de carregamento de documentos
Quando um usuário reabre uma solução do Visual Studio, a maioria dos documentos associados não é carregada imediatamente. O quadro de janela de documento é criado em um estado pendente de inicialização e um documento de espaço reservado (chamado de um quadro de stub) é colocado na tabela de documento em execução (RDT).  
  
 A extensão pode causar documentos do projeto para ser carregado desnecessariamente consultando elementos nos documentos antes de serem carregados. Isso pode aumentar o espaço de memória geral para o Visual Studio.  
  
## <a name="document-loading"></a>Carregamento de documentos  
 O documento e o stub são totalmente inicializados quando o usuário acessa o documento, por exemplo, selecionando a guia do quadro de janela. O documento também pode ser inicializado por uma extensão que solicita os dados do documento, acessando o RDT diretamente para obter os dados de documento ou acessar o RDT indiretamente fazendo uma das seguintes chamadas:  
  
-   Método show do quadro da janela: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   O quadro de janela método GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> em qualquer uma das seguintes propriedades:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Se sua extensão de usar código gerenciado, você não deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> , a menos que você tiver certeza de que o documento não está no estado pendente de inicialização, ou você deseja que o documento seja totalmente inicializada. Isso ocorre porque esse método sempre retorna o documento que o objeto de dados, criá-lo se necessário. Em vez disso, você deve chamar um dos métodos na interface IVsRunningDocumentTable4.  
  
 Se sua extensão usa C++, você pode passar `null` para os parâmetros que você não deseja.  
  
 Você pode evitar o carregamento de documentos desnecessários chamando um dos métodos a seguir antes de você pedir as propriedades relevantes: antes de você pedir outras propriedades.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> usando <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método retorna um <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que inclui um valor para <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> se o documento ainda não foi inicializado.  
  
 Você pode descobrir quando um documento foi carregado por assinar o evento RDT que é gerado quando um documento está totalmente inicializado. Há duas possibilidades:  
  
-   Se o coletor de eventos implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, você pode assinar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   Caso contrário, você pode assinar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Este é um cenário de acesso do documento hipotético. Uma extensão que deseja exibir algumas informações sobre como abrir documentos do Visual Studio, para a instância a edição Bloquear contagem e algo sobre os dados de documento. Enumera os documentos usando o RDT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, em seguida, chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento para recuperar os dados de contagem e o documento de bloqueio editar. Se o documento está no estado pendente de inicialização, solicitar dados de documento faz com que ele seja inicializada desnecessariamente.  
  
 Uma maneira mais eficiente de fazer isso é usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obter a contagem de bloqueio de editar e, em seguida, usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar se o documento foi inicializado. Se os sinalizadores não incluir <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, o documento já foi inicializado e solicita os dados de documento com <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> não faz com que qualquer inicialização desnecessária. Se os sinalizadores incluem <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, a extensão deve evitar solicita os dados de documento até que o documento seja inicializado. Isso pode ser detectado no manipulador de eventos OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testando extensões para ver se eles forçam a inicialização  
 Não há nenhuma indicação visível para indicar se um documento foi inicializado, para que ele possa ser difíceis de descobrir se sua extensão está forçando a inicialização. Você pode definir uma chave do registro que facilita a verificação, porque ele faz com que o título de cada documento que não está totalmente inicializado para o texto `[Stub]` no título.  
  
 Em **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, defina **StubTabTitleFormatString** para **{0} [Stub]**.