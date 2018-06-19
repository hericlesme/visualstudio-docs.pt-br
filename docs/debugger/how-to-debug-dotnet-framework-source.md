---
title: 'Como: depurar fonte do .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8377ed73479441272b2f1910767fa7e2a4ff0196
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475633"
---
# <a name="how-to-debug-net-framework-source"></a>Como depurar a origem do .NET Framework
Para depurar o código-fonte do .NET Framework, você deve ter acesso aos símbolos para o código de depuração. Você também precisará habilitar a depuração em código-fonte do .NET Framework.  
  
 Você pode habilitar o .NET Framework revisão e símbolo baixando no **opções** caixa de diálogo. Ao habilitar a transferência de símbolo, você pode optar por baixar imediatamente os símbolos ou apenas habilitar a opção para uma transferência posterior. Se você não baixar os símbolos imediatamente, eles serão baixados da próxima vez em que você iniciar a depuração do seu aplicativo. Você também pode fazer um download manual do **módulos** janela ou **pilha de chamadas** janela.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para ativar a depuração de origem do .NET Framework  
  
1.  Sobre o **ferramentas** menu, clique em **opção**s.  
  
2.  No **opções** caixa de diálogo, clique o **depuração** categoria.  
  
3.  No **geral** caixa, defina **fonte do .NET Framework permitem passo a passo.**  
  
    1.  Se Apenas Meu Código tiver sido habilitado, uma caixa de diálogo de aviso mostrará que Apenas Meu Código está desabilitado agora. Clique em **OK**.  
  
    2.  Se você não tiver um local de cache de símbolo definido, outra caixa de diálogo de aviso informará que um local padrão de cache do símbolo foi definido agora. Clique em **OK**.  
  
4.  Sob o **depuração** categoria, clique em **símbolos**.  
  
5.  Se você quiser alterar o local do cache de símbolos, edite o local no **símbolos neste diretório de Cache** ou clique em **procurar** para escolher um local.  
  
6.  Se você deseja baixar os símbolos imediatamente, clique em **carregar símbolos usando acima locais**.  
  
     Esse botão não está disponível no modo de design, mas está disponível durante a depuração.  
  
     Se você não optar por baixar símbolos agora, os símbolos serão baixados automaticamente da próxima vez em que você iniciar a depuração do seu programa.  
  
7.  Clique em **OK** para fechar a caixa de diálogo **Opções**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para carregar símbolos de Framework usando a janela de módulos  
  
1.  No **módulos** janela (durante a depuração, escolha **depurar** > **Windows** > **módulos**), Clique em um módulo para o qual os símbolos não são carregados. Você pode determinar se os símbolos foram carregados ou não examinando o **símbolos Status** coluna.  
  
2.  Aponte para **configurações de símbolo** e clique em **Microsoft Symbol Servers** para baixar os símbolos do servidor de símbolos públicos de Microsoft. Ou, clique com botão direito do módulo e escolha **carregar símbolos** carregar a partir de um diretório onde você armazenou anteriormente símbolos.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para carregar símbolos de Framework usando a janela de pilha de chamadas  
  
1.  No **pilha de chamadas** janela, clique com botão direito um quadro para o qual os símbolos não são carregados. O quadro será esmaecido.  
  
2.  Aponte para **configurações de símbolo** e clique em **Microsoft Symbol Servers**, ou com o botão direito do módulo e escolha **caminho de símbolo**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)