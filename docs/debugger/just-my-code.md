---
title: "Depurar o código do usuário com Just My Code | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 476ff209f96aa5729d20bd9a5a5d12c9e5a5c39a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Especifique se deseja depurar somente código de usuário usando apenas meu código do Visual Studio
Você pode configurar o Visual Studio para passar por sistema, framework e outras chamadas de não usuário automaticamente e recolher dessas chamadas na janela de pilha de chamadas. O recurso que habilita ou desabilita a esse comportamento é chamado *apenas meu código*. Este tópico descreve como usar apenas meu código em projetos c#, Visual Basic, C++ e JavaScript.

Para a maioria das linguagens de programação, apenas meu código está habilitado por padrão.
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a>Habilitar ou desabilitar apenas meu código  
 Para habilitar ou desabilitar apenas meu código, escolha o **Ferramentas > Opções** menu do Visual Studio. No **depuração** > **geral** nó, escolha ou desmarque **habilitar apenas meu código**.
  
 ![Habilitar apenas meu código na caixa de diálogo Opções](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  O **habilitar apenas meu código** é uma configuração global que é aplicada a todos os projetos do Visual Studio em todos os idiomas.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a>Mostrar o código não-usuário nas exibições de pilha de chamada  
 Nos modos de exibição que mostram a pilha de chamadas, como o **pilha de chamadas** e **tarefas** windows, apenas meu código recolhe o código de não usuário em um quadro com anotações de rotulado `[External Code]`. Para exibir os quadros recolhidos, escolha **Mostrar código externo** no menu de contexto da pilha de chamadas exibir.

 ![Mostrar código externo na janela de pilha de chamadas](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  O **Mostrar código externo** configuração é salva para o criador de perfil do usuário atual. Ela é aplicada a todos os projetos em todas as linguagens que são abertos pelo usuário.
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a>Apenas meu código do .NET framework  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a>Código de usuário e não-usuário  
 Para diferenciar o código do usuário do código não-usuário, apenas meu código examina arquivos de símbolo (. PDB) e as otimizações de programa. O depurador considera o código como sendo de não usuário quando o binário não é otimizado ou quando o arquivo .pdb não está disponível.
  
 Três atributos também afetam o que o depurador considera como sendo Meu Código:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> diz ao depurador que o código ao qual se aplica não é Meu Código.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta o código do depurador, mesmo que Apenas Meu Código esteja desativado.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> informa o depurador para percorrer o código ao qual é aplicado, em vez de depurar o código.  
  
 Todos os demais códigos são considerados código de usuário.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a>Comportamento de revisão  
 Quando você **intervir** (atalho do teclado: F11) código não-usuário, o depurador vai sobre o código para a próxima instrução do usuário. Quando você **sair** (teclado: Shift + F11), o depurador é executado para a próxima linha do código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo sai, um ponto de interrupção é atingido, ou ocorrerá uma exceção.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a>Comportamento de ponto de interrupção  
 Quando apenas meu código está habilitado, você pode escolher **Break All** (teclado: Ctrl + Alt + Break) e interromper a execução em um local onde não há nenhum código de usuário para exibir. Quando isso acontece, a janela Sem Código Fonte será exibida. Se você escolher em um comando de etapa, o depurador leva você até a próxima linha do código do usuário.  
  
###  <a name="BKMK_NET_Exception_behavior"></a>Comportamento de exceção  
 Se uma exceção sem tratamento ocorre no código de não usuário, o depurador é interrompido na linha do código de usuário na qual a exceção foi gerada.  
  
 Se as exceções de primeira opção estiverem habilitadas para a exceção, a linha do código de usuário será realçada em verde. A pilha de chamadas exibe um quadro anotado rotulado **[código externo]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a>Apenas meu código do C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a>Código de usuário e não-usuário  
 O Apenas Meu Código do C++ é diferente do Apenas Meu Código do .NET Framework e do JavaScript porque o comportamento de depuração é independente do comportamento da pilha de chamadas.  
  
 **Pilhas de chamadas**  
  
 Por padrão, o depurador considera estas funções como código de não usuário em janelas de pilha de chamadas:  
  
-   Funções com informações de origem retiradas no respectivo arquivo de símbolos.  
  
-   Funções nas quais os arquivos de símbolos indicam que não há nenhum arquivo de origem que corresponde ao quadro de pilhas.  
  
-   Funções especificadas na `*.natjmc` arquivos de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
 **Passo a passo**  
  
 Por padrão, apenas funções especificado em `*.natstepfilter` arquivos de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta são considerados código não-usuário.  
  
 Você pode criar seus próprios `.natstepfilter` e `.natjmc` para personalizar a revisão e chamar o comportamento de janela de pilha `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a>Comportamento de revisão  
 Quando você **intervir** (atalho do teclado: F11) código de não usuário do código do usuário, as etapas de depurador sobre o código para a próxima linha de código do usuário. Quando você **sair** (teclado: Shift + F11), o depurador é executado para a próxima linha do código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo sai, um ponto de interrupção é atingido, ou ocorrerá uma exceção.  
  
 Se o depurador for interrompido em um código de não usuário (por exemplo, se um comando Interromper Tudo parar em um código de não usuário), a depuração continua no código de não usuário.  
  
###  <a name="BKMK_CPP_Exception_behavior"></a>Comportamento de exceção  
 Quando o depurador atinge uma exceção, ele parará na exceção independentemente de ser em código não-usuário ou do usuário. O **manipulado pelo usuário** opções no **exceções** caixa de diálogo são ignorados.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a>Personalizar o comportamento de revisão  
 Você pode especificar funções para depurar a tecla listá-los como código de não usuário em `*.natstepfilter` arquivos.  
  
-   Para especificar o código de não usuário para todos os usuários do computador do Visual Studio, adicione o arquivo .natstepfilter para o `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
-   Para especificar o código de não usuário para um usuário individual, adicione o arquivo .natstepfilter para o `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` pasta.  
  
 Os arquivos .natstepfilter são arquivos XML com esta sintaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Função|Necessário. Especifica uma ou mais funções como funções de não usuário.|  
|`Name`|Necessário. Uma expressão regular formatada como ECMA-262 que especifica o nome completo da função a ser correspondida. Por exemplo:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> informa ao depurador que todos os métodos em `MyNS::MyClass` devem ser considerados como código de não usuário. A correspondência diferencia maiúsculas e minúsculas.|  
|`Module`|Opcional. Uma expressão regular formatada como ECMA-262 que especifica o caminho completo do módulo que contém a função. A correspondência não diferencia maiúsculas de minúsculas.|  
|`Action`|Necessário. Um destes valores que diferenciam maiúsculas e minúsculas:<br /><br /> -   `NoStepInto`-informa o depurador para percorrer a função correspondente.<br />-   `StepInto`-informa o depurador para passar para as funções correspondentes, substituindo qualquer outro `NoStepInto` para as funções correspondentes.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a>Personalizar o comportamento da pilha de chamada  
 Você pode especificar os módulos, arquivos de origem e funções a serem tratados como código de não usuários em pilhas de chamadas, especificando-os em `*.natjmc` arquivos.  
  
-   Para especificar o código de não usuário para todos os usuários do computador do Visual Studio, adicione o arquivo .natjmc para o `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
-   Para especificar o código de não usuário para um usuário individual, adicione o arquivo .natjmc para o `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` pasta.  
  
 Os arquivos .natjmc são arquivos XML com esta sintaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Atributos do elemento de módulo**  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Necessário. O caminho completo do módulo ou dos módulos. Você pode usar os caracteres curinga do Windows `?` (zero ou um caractere) e `*` (zero ou mais caracteres). Por exemplo,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> informa o depurador para tratar todos os módulos no `\3rdParty\UtilLibs` em qualquer unidade de código externo.|  
|`Company`|Opcional. O nome da empresa que publica o módulo inserido no arquivo executável. Você pode usar esse atributo para resolver a ambiguidade dos módulos.|  
  
 **Atributos do elemento de arquivo**  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Necessário. O caminho completo do arquivo ou arquivos de origem a serem tratados como código externo. Você pode usar os caracteres curinga do Windows `?` e `*` ao especificar o caminho.|  
  
 **Atributos do elemento de função**  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Necessário. O nome totalmente qualificado da função a ser tratada como código externo.|  
|`Module`|Opcional. O nome ou o caminho completo do módulo que contém a função. Você pode usar esse atributo para resolver a ambiguidade de funções com o mesmo nome.|  
|`ExceptionImplementation`|Quando definido como `true`, a pilha de chamadas exibe a função que lançou a exceção em vez dessa função.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a>Apenas meu código do JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a>Código de usuário e não-usuário  
 **Classificações de código**  
  
 O Apenas Meu Código do JavaScript controla a depuração e a exibição da pilha de chamadas categorizando o código em uma destas classificações:  
  
|||  
|-|-|  
|**MyCode**|Código do usuário que você possui e controla.|  
|**LibraryCode**|Código de não usuário de bibliotecas que você usa com frequência e do qual seu aplicativo depende para funcionar corretamente (por exemplo WinJS ou jQuery).|  
|**UnrelatedCode**|Código não-usuário que poderia estar em execução no seu aplicativo, mas não o proprietário e seu aplicativo diretamente não confiar para funcionar corretamente. (Por exemplo, isso pode incluir um anúncio SDK que exibe anúncios). Em projetos UWP, qualquer código que é carregado em seu aplicativo de um URI HTTP ou HTTPS também é considerado UnrelatedCode.|  
  
 O depurador do JavaScript classifica automaticamente estes tipos de código:  
  
-   Script executado ao passar uma cadeia de caracteres para o host fornecido `eval` função é classificada como **MyCode**.  
  
-   Script executado ao passar uma cadeia de caracteres para o `Function` construtor é classificado como **LibraryCode**.  
  
-   Script que está contido em uma referência do framework, como WinJS ou SDK do Azure, é classificado como **LibraryCode**.  
  
-   Script executado ao passar uma cadeia de caracteres para o `setTimeout`, `setImmediate`, ou `setInterval` funções é classificado como **UnrelatedCode**.  
  
-   O `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Especifica outro código de usuário e não do usuário para todos os projetos de JavaScript do Visual Studio.  
  
 Você pode alterar as classificações padrão e classificar arquivos e URLs específicos adicionando um arquivo .json nomeado `mycode.json` à pasta raiz de um projeto.  
  
 Todos os outros códigos é classificado como **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a>Comportamento de revisão  
  
-   Se uma função não for um usuário (**MyCode**) código, **intervir** (atalho do teclado: F11) se comporta como **contornar** (teclado: F10).  
  
-   Se uma etapa começa em não-usuário (**LibraryCode** ou **UnrelatedCode**) de código, e em seguida, passar temporariamente se comporta como se apenas meu código não está habilitado. Quando você entrar novamente para o código de usuário, apenas meu código passo a passo é habilitado novamente.  
  
-   Quando uma etapa no código de usuário resultar na saída do contexto de execução atual (por exemplo, executar uma etapa na última linha de um manipulador de eventos), o depurador para na próxima linha de código de usuário executada. Por exemplo, se um retorno de chamada for executada em **LibraryCode** código o depurador continua até que executa a próxima linha de código do usuário.
  
-   **Sair** (teclado: Shift + F11) parar na próxima linha do código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo sai, um ponto de interrupção é atingido, ou ocorrerá uma exceção.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a>Comportamento de ponto de interrupção  
  
-   Pontos de interrupção definidos no código sempre serão atingidos, independentemente da classificação do código  
  
-   Se o `debugger` palavra-chave é encontrado em:  
  
    -   **LibraryCode** código, o depurador sempre quebra.  
  
    -   **UnrelatedCode** código, o depurador não parar.  
  
###  <a name="BKMK_JS_Exception_behavior"></a>Comportamento de exceção  
 Se ocorrer uma exceção não tratada em:  
  
-   **MyCode** ou **LibraryCode** código, o depurador sempre quebra.  
  
-   **UnrelatedCode** código, e **MyCode** ou **LibraryCode** é de código na pilha de chamadas, as quebras de depurador.  
  
 Se as exceções de primeira chance estão habilitadas para a exceção na caixa de diálogo exceções e a exceção é lançada no **LibraryCode** ou **UnrelatedCode** código:  
  
-   Se a exceção é manipulada, não interrompe o depurador.  
  
-   Se a exceção não for tratada, o depurador será interrompido.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a>Personalizar apenas meu código  
 Para categorizar código de usuário e de não usuário para um único projeto do Visual Studio, adicione um arquivo .json denominado `mycode.json` à pasta raiz do projeto.  
  
 As classificações são executadas nesta ordem:  
  
1.  Classificações padrão  
  
2.  Classificações no `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` arquivo  
  
3.  Classificações no arquivo `mycode. json` do projeto atual.  
  
 Cada etapa de classificação substitui as etapas anteriores. Um arquivo. JSON não é necessário listar todos os pares chave / valor e o **MyCode**, **bibliotecas**, e **não relacionado** valores podem ser matrizes vazias.  
  
 Os arquivos .json MyCode usam esta sintaxe:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec",  
        . .  
        "UrlOrFileSpec"  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ]  
}  
  
```  
  
 **Avaliação, função e ScriptBlock**  
  
 O **Eval**, **função**, e **ScriptBlock** determinam como dinamicamente os pares chave-valor código gerado é classificado.  
  
|||  
|-|-|  
|**Eval**|Script que é executado passando uma cadeia de caracteres à função `eval` fornecida pelo host. Por padrão, o script Eval é classificado como **MyCode**.|  
|**Função**|Script que é executado passando uma cadeia de caracteres para o construtor `Function`. Por padrão, o script de função é classificado como **LibraryCode**.|  
|**ScriptBlock**|Script que é executado passando uma cadeia de caracteres para a função `setTimeout`, `setImmediate` ou `setInterval`. Por padrão, o script ScriptBlock é classificado como **UnrelatedCode**.|  
  
 Você pode alterar o valor para um destas palavras-chave:  
  
-   `MyCode`classifica o script como **MyCode**.  
  
-   `Library`classifica o script como **LibraryCode**.  
  
-   `Unrelated`classifica o script como **UnrelatedCode**.  
  
 **MyCode, bibliotecas e não relacionados**  
  
 O **MyCode**, **bibliotecas**, e **não relacionado** pares chave-valor especificar os urls ou arquivos que você deseja incluir em uma classificação:  
  
|||  
|-|-|  
|**MyCode**|Uma matriz de urls ou arquivos que são classificados como **MyCode**.|  
|**Bibliotecas**|Uma matriz de urls ou arquivos que são classificados como **LibraryCode**.|  
|**Não relacionados**|Uma matriz de urls ou arquivos que são classificados como **UnrelatedCode**.|  
  
 A cadeia de caracteres de url ou o arquivo pode conter um ou mais `*` caracteres, que correspondem a zero ou mais caracteres. `*`é o equivalente da expressão regular `.*`.