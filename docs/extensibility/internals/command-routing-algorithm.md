---
title: Algoritmo de roteamento de comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aba7ddcdda4dd4eabbb9266e0fa89c916bb028f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="command-routing-algorithm"></a>Algoritmo de roteamento de comando
No Visual Studio comandos são tratados por um número de diferentes componentes. Comandos são roteados do contexto interno, que é baseado na seleção atual, para o contexto mais externo de (também conhecido como global). Para obter mais informações, consulte [disponibilidade](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Ordem de resolução de comando  
 Comandos são passados para os seguintes níveis de contexto do comando:  
  
1.  Suplementos: O ambiente oferece primeiro o comando para quaisquer suplementos que estão presentes.  
  
2.  Comandos de prioridade: esses comandos são registrados usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Eles são chamados de cada comando no Visual Studio e são chamados na ordem em que eles foram registrados.  
  
3.  Comandos de menu de contexto: um comando localizado em um menu de contexto é oferecido pela primeira vez para o destino do comando que é fornecido para o menu de contexto e para o roteamento típico.  
  
4.  Barra de ferramentas definir destinos de comando: esses destinos de comando são registrados quando você chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. O `pCmdTarget` parâmetro pode ser `null`. Se não for `null`, em seguida, o destino do comando é usado para atualizar todos os comandos localizados na barra de ferramentas que você está configurando. Se o shell está configurando sua barra de ferramentas, ele passa a moldura da janela como o `pCmdTarget` para que todas as atualizações para os comandos em seu fluxo de barra de ferramentas por meio do quadro da janela, mesmo quando ele não está no foco.  
  
5.  Janela de ferramenta: Ferramenta windows, que normalmente é implementam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface, também deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface para que o Visual Studio pode obter o destino do comando quando a janela da ferramenta é a janela ativa. No entanto, se a janela de ferramenta que tem foco é a **projeto** janela e, em seguida, o comando é roteada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface que é o pai comum dos itens selecionados. Se esta seleção se estender por vários projetos, o comando é roteado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hierarquia. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface contém o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> métodos semelhantes para os comandos correspondentes no <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
6.  Janela de documento: Se o comando tem o sinalizador de RouteToDocs definido em seu arquivo. VSCT, Visual Studio procurará um destino de comando no objeto de exibição de documento, que é uma instância de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface ou uma instância de um objeto de documento (normalmente um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interface ou um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface). Se o objeto de exibição de documento não oferece suporte para o comando, o Visual Studio encaminha o comando para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface que é retornado. (Esta é uma interface opcional para objetos de dados de documento.)  
  
7.  Hierarquia atual: A hierarquia atual pode ser o projeto que possui a janela de documento ativa ou a hierarquia selecionada no **Gerenciador de soluções**. O Visual Studio procura o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface é implementada na hierarquia atual ou ativa. A hierarquia deve dar suporte a comandos válidos sempre que a hierarquia está ativa, mesmo se uma janela de documento de um item de projeto tem foco. No entanto, comandos que se aplicam somente quando **Solution Explorer** tem foco deve ter suporte usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface e sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>métodos.  
  
     **Recortar**, **cópia**, **colar**, **excluir**, **Renomear**, **digite**e **DoubleClick** comandos requerem tratamento especial. Para obter informações sobre como lidar com **excluir** e **remover** comandos em hierarquias, consulte o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interface.  
  
8.  Global: Se um comando não foi tratado pelos contextos mencionados anteriormente, o Visual Studio tenta encaminhá-lo para o VSPackage que possui um comando que implementa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Se o VSPackage já não foi carregado, ele não será carregado quando o Visual Studio chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. O VSPackage é carregado apenas quando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [Design de comando](../../extensibility/internals/command-design.md)