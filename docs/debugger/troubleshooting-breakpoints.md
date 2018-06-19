---
title: Solucionar problemas de pontos de interrupção no depurador do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d587809a9690e312e923ba184c9d90c38405a5d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477099"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Solucionar problemas de pontos de interrupção no depurador do Visual Studio

## <a name="breakpoint-warnings"></a>Avisos de ponto de interrupção

Durante a depuração, um ponto de interrupção tem dois estados possíveis de visual: um círculo vermelho sólido e um vazio (branco preenchido) círculo. Se o depurador é capaz de definir com êxito um ponto de interrupção no processo de destino, ele permanecerá um círculo vermelho sólido. Se o ponto de interrupção é um círculo vazio, o ponto de interrupção está desabilitado ou aviso ocorreu ao tentar definir o ponto de interrupção. Para determinar a diferença, passe o mouse sobre o ponto de interrupção e veja se há um aviso.

As duas seções a seguir descrevem os avisos importantes e como corrigi-los. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Nenhum símbolo foi carregado para esse documento" 

Vá para o **módulos** janela (**depurar** > **Windows** > **módulos**) e verifique se o módulo é carregado.  
* Verifique se o módulo é carregado, o **Status símbolo** coluna para ver se os símbolos foram carregados. 
  * Se os símbolos não são carregados, verifique o status de símbolo para diagnosticar o problema. No menu de contexto em um módulo de **módulos** janela, clique em **informações de carga de símbolo...**  para ver onde o depurador pesquisados para tentar carregar símbolos. Para obter mais informações sobre como carregar símbolos, consulte [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Se os símbolos foram carregados, isso significa que o PDB não contém informações sobre os arquivos de origem. Estas são algumas causas possíveis: 
    * Se os arquivos de origem foram adicionados recentemente, confirme que uma versão atualizada do módulo está sendo carregada.  
    * É possível criar os PDBs removidos usando o **/PDBSTRIPPED** opção de vinculador. Os PDBs não contêm informações de arquivo de origem. Confirme se que você estiver trabalhando com um completo PDB e não um PDB extraído.  
    * O arquivo PDB parcialmente está corrompido. Tente excluir o arquivo e executar uma compilação limpa do módulo para ver se isso resolve o problema. 

* Se o módulo não está carregado, verifique o seguinte para encontrar a causa: 
  * Confirme que você está depurando o processo certo. 
  * Verifique se você está depurando o tipo correto de código. Você pode descobrir que tipo de código que o depurador está configurado para depurar o **processos** janela (**depurar** > **Windows**  >  **Processos**). Por exemplo, se você está tentando depurar o código c#, confirmar que o depurador está configurado para o tipo apropriado do .NET Framework (por exemplo, gerenciados (v4\*) versus gerenciado (v2\*/v3\*) versus gerenciado (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… o código-fonte atual é diferente da versão incorporada..." 

Se um arquivo de origem foi alterado e a fonte não coincide mais com o código que você está depurando, o depurador não definirá os pontos de interrupção no código por padrão. Normalmente, esse problema ocorre quando um arquivo de origem for alterado, mas o código-fonte não foi recriado. Para corrigir esse problema, recrie o projeto. Se o sistema de compilação considera que o projeto já está atualizado, embora ele não estiver, você pode forçar o sistema de projeto para reconstruir por salvar o arquivo de origem novamente ou com o projeto de limpeza criar saída antes de compilar. 

Em raras situações, convém depurar sem a necessidade de código-fonte correspondente. Isso pode levar a uma experiência de depuração muito confusa, portanto certifique-se de que isso é como você deseja continuar.  

Para desabilitar essas verificações de segurança, siga um destes procedimentos: 
* Para modificar um único ponto de interrupção, passe o mouse sobre o ícone de ponto de interrupção no editor e clique no ícone de configurações (engrenagem). Uma janela de inspeção é adicionada para o editor. Na parte superior da janela Inspeção, há um hiperlink que indica o local do ponto de interrupção. Clique no hiperlink para permitir a modificação do local do ponto de interrupção e verificar **permitir que o código-fonte seja diferente do original**.
* Para modificar essa configuração para todos os pontos de interrupção, vá para **depurar** > **opções e configurações**. Sobre o **depuração/geral** página, desmarque o **requer arquivos de origem que correspondam exatamente à versão original** opção. Certifique-se de reativar essa opção quando tiver terminado de depuração. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>O ponto de interrupção foi definido com êxito (sem aviso), mas não foi atingido 

Esta seção fornece informações para solucionar problemas quando o depurador não estiver exibindo todos os avisos – o ponto de interrupção é um círculo vermelho sólido durante a depuração ativamente, ainda que o ponto de interrupção não está sendo atingido. 

Aqui estão algumas coisas para verificar: 
1. Se seu código é executado no processo de mais de um ou mais de um computador, certifique-se de que você está depurando o processo certo ou computador.  
2. Confirme se o seu código está em execução. Uma maneira fácil de testar isso é adicionar uma chamada para `System.Diagnostics.Debugger.Break` (C# /VB) ou `__debugbreak` (C++) para a linha de código em que você está tentando definir o ponto de interrupção e, em seguida, recrie seu projeto. 
3. Se você estiver depurando código otimizado, verifique se a função em que o ponto de interrupção é definido não está sendo embutida dentro de outra função. O `Debugger.Break` teste descrito na verificação de anterior pode trabalhar para testar isso também. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Excluí um ponto de interrupção, mas continuar a pressionar ele quando iniciar a depuração novamente 

Se você excluir um ponto de interrupção durante a depuração, você pode atingir o ponto de interrupção novamente na próxima vez que você iniciar a depuração. Para interromper a alcançar este ponto de interrupção, verifique se todas as instâncias do ponto de interrupção são removidas do **pontos de interrupção** janela.  
