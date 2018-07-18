---
title: Depurar o código do usuário com apenas meu código | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fb5534d376cf1a0c60b20080df8c8bfc6ad6689
ms.sourcegitcommit: 886759fb35a88f6ef5452c5b2e33a1f71da4489a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2018
ms.locfileid: "34851819"
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Especifique se deseja depurar somente código do usuário usando o Just My Code no Visual Studio
Você pode configurar o Visual Studio para depurar system, estrutura e outras chamadas de não usuário e recolhe essas chamadas na janela de pilha de chamadas automaticamente. O recurso que habilita ou desabilita esse comportamento é chamado *Just My Code*. Este tópico descreve como usar o apenas meu código em projetos c#, Visual Basic, C++ e JavaScript.

Para a maioria das linguagens de programação, apenas meu código está habilitado por padrão.
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Habilitar ou desabilitar apenas meu código  
 Para habilitar ou desabilitar apenas meu código, escolha o **Ferramentas > Opções** menu do Visual Studio. No **Debugging** > **geral** nó, marque ou desmarque **habilitar apenas meu código**.
  
 ![Habilitar apenas meu código na caixa de diálogo Opções](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  O **habilitar apenas meu código** configuração é uma configuração global que é aplicada a todos os projetos do Visual Studio em todos os idiomas.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Mostrar o código de não usuário nas exibições de pilha de chamadas  
 Nos modos de exibição que mostram a pilha de chamadas, como o **pilha de chamadas** e **tarefas** windows, apenas meu código recolhe o código de não usuário em um quadro anotado rotulado `[External Code]`. Para exibir os quadros recolhidos, escolha **Mostrar código externo** no menu de contexto da pilha de chamadas exibição.

 ![Mostrar código externo na janela de pilha de chamadas](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  O **Mostrar código externo** configuração é salva para o criador de perfil do usuário atual. Ela é aplicada a todos os projetos em todas as linguagens que são abertos pelo usuário.
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> Apenas meu código do .NET framework  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Código de usuário e de não usuário  
 Para diferenciar o código do usuário do código de não usuário, apenas meu código examina arquivos de símbolo (. PDB) e otimizações de programa. O depurador considera o código como sendo de não usuário quando o binário não é otimizado ou quando o arquivo .pdb não está disponível.
  
 Três atributos também afetam o que o depurador considera como sendo Meu Código:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> diz ao depurador que o código ao qual se aplica não é Meu Código.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta o código do depurador, mesmo que Apenas Meu Código esteja desativado.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> informa o depurador para percorrer o código ao qual é aplicado, em vez de depurar o código.  
  
 Todos os demais códigos são considerados código de usuário.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Comportamento de depuração  
 Quando você **intervir** (atalho de teclado: F11) código de não usuário, o depurador percorre o código para a próxima instrução do usuário. Quando você **depuração circular** (teclado: Shift + F11), o depurador executa a próxima linha de código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo sai, um ponto de interrupção é atingido, ou ocorrerá uma exceção.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Comportamento de ponto de interrupção  
 Quando apenas meu código está habilitado, você pode escolher **interromper tudo** (teclado: Ctrl + Alt + Break) e interromper a execução em um local em que não há nenhum código de usuário para exibir. Quando isso acontece, a janela Sem Código Fonte será exibida. Se você escolher em um comando de etapa, o depurador leva você até a próxima linha do código do usuário.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Comportamento de exceção  
 Se uma exceção sem tratamento ocorre no código de não usuário, o depurador é interrompido na linha do código de usuário na qual a exceção foi gerada.  
  
 Se as exceções de primeira opção estiverem habilitadas para a exceção, a linha do código de usuário será realçada em verde. A pilha de chamadas exibe um quadro anotado rotulado **[código externo]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> Apenas meu código do C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Código de usuário e de não usuário  
 O Apenas Meu Código do C++ é diferente do Apenas Meu Código do .NET Framework e do JavaScript porque o comportamento de depuração é independente do comportamento da pilha de chamadas.  
  
 **Pilhas de chamadas**  
  
 Por padrão, o depurador considera estas funções como código de não usuário em janelas de pilha de chamadas:  
  
-   Funções com informações de origem retiradas no respectivo arquivo de símbolos.  
  
-   Funções nas quais os arquivos de símbolos indicam que não há nenhum arquivo de origem que corresponde ao quadro de pilhas.  
  
-   Funções especificadas na `*.natjmc` arquivos de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
 **Passo a passo**  
  
 Por padrão, somente as funções especificadas na `*.natstepfilter` arquivos de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta são considerados código de não usuário.  
  
 Você pode criar seus próprios `.natstepfilter` e `.natjmc` para personalizar a depuração e chamar o comportamento da janela de pilha no `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Comportamento de depuração  
 Quando você **intervir** (atalho de teclado: F11) código de não usuário do código do usuário, o depurador percorre o código para a próxima linha de código do usuário. Quando você **depuração circular** (teclado: Shift + F11), o depurador executa a próxima linha de código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo sai, um ponto de interrupção é atingido, ou ocorrerá uma exceção.  
  
 Se o depurador for interrompido em um código de não usuário (por exemplo, se um comando Interromper Tudo parar em um código de não usuário), a depuração continua no código de não usuário.  
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Comportamento de exceção  
 Quando o depurador atinge uma exceção, ele parar na exceção independentemente de estar ou não no usuário ou código de não usuário. O **User-unhandled** as opções a **exceções** caixa de diálogo são ignorados.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizar o comportamento de depuração  
 Você pode especificar funções para percorrer listando-os como código de não usuário em `*.natstepfilter` arquivos.  
  
-   Para especificar o código de não usuário para todos os usuários do computador do Visual Studio, adicione o arquivo. natstepfilter ao `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
-   Para especificar o código de não usuário para um usuário individual, adicione o arquivo. natstepfilter ao `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` pasta.  
  
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
|`Action`|Necessário. Um destes valores que diferenciam maiúsculas e minúsculas:<br /><br /> -   `NoStepInto`  – informa o depurador para percorrer a função correspondente.<br />-   `StepInto`  – informa o depurador para percorrer funções correspondentes, substituindo qualquer outro `NoStepInto` pelas funções correspondentes.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizar o comportamento da pilha de chamadas  
 Você pode especificar módulos, arquivos de origem e funções para serem tratados como código de não usuário em pilhas de chamadas especificando-os na `*.natjmc` arquivos.  
  
-   Para especificar o código de não usuário para todos os usuários do computador do Visual Studio, adicione o arquivo. natjmc ao `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
-   Para especificar o código de não usuário para um usuário individual, adicione o arquivo. natjmc ao `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` pasta.  
  
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
|`Name`|Necessário. O caminho completo do módulo ou dos módulos. Você pode usar os caracteres curinga do Windows `?` (zero ou um caractere) e `*` (zero ou mais caracteres). Por exemplo,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> informa o depurador para tratar todos os módulos no `\3rdParty\UtilLibs` em qualquer unidade como código externo.|  
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
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Apenas meu código do JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Código de usuário e de não usuário  
 **Classificações de código**  
  
 O Apenas Meu Código do JavaScript controla a depuração e a exibição da pilha de chamadas categorizando o código em uma destas classificações:  
  
|||  
|-|-|  
|**MyCode**|Código do usuário que você possui e controla.|  
|**LibraryCode**|Código de não usuário de bibliotecas que você usa com frequência e do qual seu aplicativo depende para funcionar corretamente (por exemplo WinJS ou jQuery).|  
|**UnrelatedCode**|Código de não usuário que pode ser executado em seu aplicativo, mas não o proprietário e seu aplicativo não depende diretamente para que funcione corretamente. (Por exemplo, isso pode incluir um anúncio do SDK que exibe anúncios). Em projetos UWP, qualquer código que é carregado no seu aplicativo a partir de um URI HTTP ou HTTPS também é considerado UnrelatedCode.|  
  
 O depurador do JavaScript classifica automaticamente estes tipos de código:  
  
-   Script que é executado passando uma cadeia de caracteres para o host fornecida `eval` função é classificada como **MyCode**.  
  
-   Script que é executado passando uma cadeia de caracteres para o `Function` construtor é classificado como **LibraryCode**.  
  
-   O script que está contido em uma referência de framework, como WinJS ou o SDK do Azure, é classificado como **LibraryCode**.  
  
-   Script que é executado passando uma cadeia de caracteres para o `setTimeout`, `setImmediate`, ou `setInterval` é classificado como **UnrelatedCode**.  
  
-   O `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Especifica outro código de usuário e de não usuário para todos os projetos de JavaScript do Visual Studio.  
  
 Você pode alterar as classificações padrão e classificar arquivos e URLs específicos adicionando um arquivo .json nomeado `mycode.json` à pasta raiz de um projeto.  
  
 Todos os demais códigos são classificados como **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Comportamento de depuração  
  
-   Se uma função não for um usuário (**MyCode**), código de **intervir** (atalho de teclado: F11) se comporta como **Step Over** (teclado: F10).  
  
-   Se uma etapa começar em não-usuário (**LibraryCode** ou **UnrelatedCode**) de código, em seguida, depuração temporária se comportará como se apenas meu código não está habilitado. Quando você percorrer de volta até o código do usuário, apenas meu código passo a passo é habilitado novamente.  
  
-   Quando uma etapa no código de usuário resultar na saída do contexto de execução atual (por exemplo, executar uma etapa na última linha de um manipulador de eventos), o depurador para na próxima linha de código de usuário executada. Por exemplo, se um retorno de chamada é executado no **LibraryCode** código o depurador continuará até que a próxima linha de código do usuário seja executada.
  
-   **Depuração circular** (teclado: Shift + F11) interrompe na próxima linha do código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo sai, um ponto de interrupção é atingido, ou ocorrerá uma exceção.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Comportamento de ponto de interrupção  
  
-   Pontos de interrupção definidos no código serão sempre atingidos independentemente da classificação desse código  
  
-   Se o `debugger` palavra-chave é encontrada em:  
  
    -   **LibraryCode** código, o depurador sempre interromperá.  
  
    -   **UnrelatedCode** código, o depurador não será interrompido.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Comportamento de exceção  
 Se ocorrer uma exceção não tratada em:  
  
-   **MyCode** ou **LibraryCode** código, o depurador sempre interromperá.  
  
-   **UnrelatedCode** código, e **MyCode** ou **LibraryCode** código está na pilha de chamadas, o depurador será interrompido.  
  
 Se as exceções de primeira chance são habilitadas para a exceção na caixa de diálogo exceções e a exceção é lançada **LibraryCode** ou **UnrelatedCode** código:  
  
-   Se a exceção for tratada, o depurador não interromperá.  
  
-   Se a exceção não for tratada, o depurador será interrompido.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizar apenas meu código  
 Para categorizar código de usuário e de não usuário para um único projeto do Visual Studio, adicione um arquivo .json denominado `mycode.json` à pasta raiz do projeto.  
  
 As classificações são executadas nesta ordem:  
  
1.  Classificações padrão  
  
2.  Classificações no `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` arquivo  
  
3.  Classificações no arquivo `mycode. json` do projeto atual.  
  
 Cada etapa de classificação substitui as etapas anteriores. Um arquivo. JSON não precisa listar todos os pares chave-valor e o **MyCode**, **bibliotecas**, e **Unrelated** valores podem ser matrizes vazias.  
  
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
  
 **Eval, Function e ScriptBlock**  
  
 O **Eval**, **função**, e **ScriptBlock** pares chave-valor determinar dinamicamente como código gerado é classificado.  
  
|||  
|-|-|  
|**Eval**|Script que é executado passando uma cadeia de caracteres à função `eval` fornecida pelo host. Por padrão, o script Eval é classificado como **MyCode**.|  
|**Função**|Script que é executado passando uma cadeia de caracteres para o construtor `Function`. Por padrão, o script Function é classificado como **LibraryCode**.|  
|**ScriptBlock**|Script que é executado passando uma cadeia de caracteres para a função `setTimeout`, `setImmediate` ou `setInterval`. Por padrão, o script ScriptBlock é classificado como **UnrelatedCode**.|  
  
 Você pode alterar o valor para um destas palavras-chave:  
  
-   `MyCode`  classifica o script como **MyCode**.  
  
-   `Library`  classifica o script como **LibraryCode**.  
  
-   `Unrelated`  classifica o script como **UnrelatedCode**.  
  
 **MyCode, Libraries e não relacionados**  
  
 O **MyCode**, **bibliotecas**, e **Unrelated** pares chave-valor especifique as urls ou arquivos que você deseja incluir em uma classificação:  
  
|||  
|-|-|  
|**MyCode**|Uma matriz de urls ou arquivos classificados como **MyCode**.|  
|**Bibliotecas**|Uma matriz de urls ou arquivos classificados como **LibraryCode**.|  
|**Não relacionados**|Uma matriz de urls ou arquivos classificados como **UnrelatedCode**.|  
  
 A cadeia de caracteres de url ou o arquivo pode conter um ou mais `*` caracteres, que correspondem a zero ou mais caracteres. `*` é o equivalente da expressão regular `.*`.
