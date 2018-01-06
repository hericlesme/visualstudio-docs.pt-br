---
title: 'Como: depurar fonte do .NET Framework | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 46c030a3c81f4b49fc66a06ee55d797dfe9119dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-net-framework-source"></a>Como depurar a origem do .NET Framework
A versão mais recente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece novos recursos para [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] depuração. Para depurar [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fonte, você deve ter acesso de símbolos para o código de depuração. Você também precisará habilitar a depuração em [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fonte.  
  
 Você pode habilitar [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] passo a passo e símbolo baixando no **opções** caixa de diálogo. Ao habilitar a transferência de símbolo, você pode optar por baixar imediatamente os símbolos ou apenas habilitar a opção para uma transferência posterior. Se você não baixar os símbolos imediatamente, eles serão baixados da próxima vez em que você iniciar a depuração do seu aplicativo. Você também pode fazer um download manual do **módulos** janela ou **pilha de chamadas** janela.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para ativar a depuração de origem do .NET Framework  
  
1.  Sobre o **ferramentas** menu, clique em **opção**s.  
  
2.  No **opções** caixa de diálogo, clique o **depuração** categoria.  
  
3.  No **geral** caixa, defina **habilitar o .NET Framework** passo a passo de origem.  
  
    1.  Se Apenas Meu Código tiver sido habilitado, uma caixa de diálogo de aviso mostrará que Apenas Meu Código está desabilitado agora. Clique em **OK**.  
  
    2.  Se você não tiver um local de cache de símbolo definido, outra caixa de diálogo de aviso informará que um local padrão de cache do símbolo foi definido agora. Clique em **OK**.  
  
4.  Sob o **depuração** categoria, clique em **símbolos**.  
  
5.  Se você desejar alterar o local do cache de símbolos:  
  
    1.  Abra o **depuração** nó na caixa à esquerda.  
  
    2.  Sob o **depuração** nó, clique em **símbolos**.  
  
    3.  Editar o local no **Cache símbolos de servidores de símbolos para este diretório** ou clique em **procurar** para escolher um local.  
  
6.  Se você deseja baixar os símbolos imediatamente, clique em **carregar símbolos usando acima locais**.  
  
     Este botão não está disponível no modo de design.  
  
     Se você não optar por baixar símbolos agora, os símbolos serão baixados automaticamente da próxima vez em que você iniciar a depuração do seu programa.  
  
7.  Clique em **OK** para fechar a caixa de diálogo **Opções**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para carregar símbolos de Framework usando a janela de módulos  
  
1.  No **módulos** janela, clique com botão direito, um módulo para o qual os símbolos não são carregados. Você pode determinar se os símbolos foram carregados ou não examinando o **símbolos Status** coluna.  
  
2.  Aponte para **carregar símbolos de** e clique em **Microsoft Symbol Servers** para baixar os símbolos do servidor de símbolos públicos Microsoft ou **caminho de símbolo** carregar a partir de um diretório onde você armazenou anteriormente símbolos.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para carregar símbolos de Framework usando a janela de pilha de chamadas  
  
1.  No **pilha de chamadas** janela, clique com botão direito um quadro para o qual os símbolos não são carregados. O quadro será esmaecido.  
  
2.  Aponte para **carregar símbolos de** e clique em **Microsoft Symbol Servers** ou **caminho de símbolo**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)