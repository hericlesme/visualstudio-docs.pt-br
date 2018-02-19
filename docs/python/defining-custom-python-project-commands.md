---
title: Como definir comandos de menu personalizados para projetos Python no Visual Studio | Microsoft Docs
description: "Demonstra como editar arquivos de projeto e de destinos para adicionar comandos personalizados ao menu de contexto do projeto Python no Visual Studio. Os comandos podem ser invocados em programas executáveis, scripts, módulos, trechos de código embutido e pip."
ms.custom: 
ms.date: 02/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 24eeb39abdee21d5441c88a3fa253d4818fe61e1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="defining-custom-commands-for-python-projects"></a>Definindo comandos personalizados para projetos Python

No processo de trabalhar com seus projetos Python, é provável que você precise alternar para uma janela de comando para executar scripts ou módulos específicos, executar comandos de pip ou executar uma outra ferramenta qualquer. Para melhorar o fluxo de trabalho, você pode adicionar comandos personalizados ao submenu **Python** no menu de contexto do projeto Python. Esses comandos podem ser executados em uma janela de console ou na janela de saída do Visual Studio. Você também pode usar expressões regulares para instruir o Visual Studio como analisar os erros e avisos da saída do comando.

Por padrão, esse menu contém apenas o único comando **Executar Pylint**:

![Aparência padrão do submenu Python no menu de contexto do projeto](media/custom-commands-default-menu.png)

Os comandos personalizados aparecem nesse mesmo menu de contexto. Os comandos personalizados são adicionados diretamente a um arquivo de projeto, aplicando-se a esse projeto individual. Você também pode definir comandos personalizados em um arquivo `.targets` que pode ser facilmente importado em vários arquivos de projeto.

Alguns modelos de projeto Python no Visual Studio já adicionam seus próprios comandos personalizados usando arquivos `.targets`. Por exemplo, os modelos Projeto Bottle Web e Projeto Flask Web adicionam dois comandos, **Iniciar servidor** e **iniciar servidor de depuração**. O modelo Projeto Django Web adiciona esses mesmos comandos além de alguns outros:

![Aparência do submenu Python em um menu de contexto do projeto Django](media/custom-commands-django-menu.png)

Cada comando personalizado pode se referir a um arquivo Python, um módulo Python, um código Python embutido, um executável qualquer ou um comando de pip. Você também pode especificar como e onde o comando é executado.

> [!Tip]
> Sempre que você fizer alterações em um arquivo de projeto em um editor de texto, será necessário recarregar o projeto no Visual Studio para aplicar essas alterações. Por exemplo, você precisará recarregar o projeto depois de adicionar definições de comando personalizadas para que esses comandos sejam exibidos no menu de contexto do projeto.
>
> Como você deve saber, o Visual Studio fornece um meio para editar diretamente o arquivo de projeto. Primeiro, clique com o botão direito do mouse no arquivo de projeto e selecione **Descarregar projeto**, em seguida, clique com botão direito do mouse novamente e selecione **Editar (nome-do-projeto)** para abrir o projeto no editor do Visual Studio. Em seguida, faça edições e salve-as, clique com botão direito do mouse no projeto mais uma vez e selecione **Recarregar projeto**, que também solicita que você confirme o fechamento do arquivo de projeto no editor.
>
> No entanto, ao desenvolver um comando personalizado, pode ser entendiante realizar todos esses cliques. Para obter um fluxo de trabalho mais eficiente, carregue o projeto no Visual Studio e também abra o arquivo `'.pyproj` em um editor completamente separado (como outra instância do Visual Studio, o Visual Studio Code, o bloco de notas, etc.). Quando você salvar as alterações no editor e alternar para o Visual Studio, o Visual Studio detectará alterações e perguntará se você deseja recarregar o projeto ["O projeto (name) foi modificado fora do ambiente."]. Selecione **Recarregar** e as alterações serão aplicadas imediatamente em apenas uma etapa.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Passo a passo: adicionar um comando em um arquivo de projeto

Para familiarizar-se com comandos personalizados, esta seção apresenta um exemplo simples que executa diretamente um arquivo de inicialização de projeto usando python.exe. (Esse comando é efetivamente o mesmo que usar **Depurar > Iniciar Sem Depuração**.)

1. Crie um novo projeto chamado "Python-CustomCommands" usando o modelo "Aplicativo Python". (Confira [Início rápido: criar um projeto do Python com base em um modelo no Visual Studio](quickstart-02-project-from-template.md) para obter instruções, se você ainda não estiver familiarizado com o processo.)

1. Em `Python_CustomCommands.py`, adicione o código `print("Hello custom commands")`.

1. Clique com botão direito do mouse no projeto em **Gerenciador de Soluções**, selecione **Python** e observe que o único comando que aparece no submenu é **Executar PyLint**. Seus comandos personalizados aparecem neste mesmo submenu.

1. Como sugerido na introdução, abra `Python-CustomCommands.pyproj` em um editor de texto separado. Em seguida, adicione as seguintes linhas ao final do arquivo, dentro do `</Project>` de fechamento e salve o arquivo.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Retorne ao Visual Studio e selecione **Recarregar** quando ele perguntar sobre a alteração no arquivo. Em seguida, verifique o menu do **Python** novamente para ver se **Executar PyLint** ainda é o único item mostrado, porque as linhas que você adicionou somente replicam o grupo de propriedades padrão do `<PythonCommands>` que contém o comando PyLint.

1. Alterne para o editor com o arquivo de projeto e adicione a seguinte definição de `<Target>` após o `<PropertyGroup>`. Conforme será explicado mais adiante neste artigo, esse elemento `Target` define um comando personalizado para executar o arquivo de inicialização (identificado pela propriedade "StartupFile") usando `python.exe` em uma janela de console. O atributo `ExecuteIn="consolepause"` usa um console que espera até que você pressione uma tecla antes de ser fechado.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Adicione o valor do atributo `Name` do destino ao grupo de propriedades `<PythonCommands>` adicionado anteriormente, para que o elemento fique semelhante ao do código abaixo. Adicionar o nome do destino nessa lista é o que o adiciona ao menu **Python**.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Se você quiser que o comando apareça antes daqueles que já estão definidos em `$(PythonCommands)`, coloque-os antes desse token.

1. Salve o arquivo de projeto, alterne para o Visual Studio e recarregue o projeto quando solicitado. Clique com o botão direito do mouse no projeto "Python-CustomCommands" e selecione **Python**. Um item **Executar arquivo de inicialização** deverá ser exibido no menu. Se o item de menu não for exibido, verifique se você adicionou o nome ao elemento `<PythonCommands>`. Confira também a [Solução de problemas](#troubleshooting) posteriormente neste artigo.

    ![Comando personalizado que aparece no submenu de contexto Python](media/custom-commands-walkthrough-menu-item.png)

1. Selecione o comando **Executar arquivo de inicialização** e uma janela de comando deverá aparecer com o texto "Olá comandos personalizados" e "Pressione qualquer tecla para continuar. . .".  Pressione uma tecla para fechar a janela.

    ![Saída do comando personalizado em uma janela de console](media/custom-commands-walkthrough-console.png)

1. Retorne ao editor com o arquivo de projeto e altere o valor do atributo `ExecuteIn` para `output`. Salve o arquivo, alterne para o Visual Studio, recarregue o projeto e invoque o comando novamente. Neste momento, você verá que a saída do programa aparece na janela **Saída** do Visual Studio:

    ![Saída do comando personalizado na janela de saída](media/custom-commands-walkthrough-output-window.png)

1. Para adicionar mais comandos, defina um elemento `<Target>` adequado para cada comando, adicione o nome do destino no grupo de propriedades `<PythonCommands>` e recarregue o projeto no Visual Studio.

>[!Tip]
> Se você invocar um comando que use propriedades do projeto, como `($StartupFile)`, e o comando falhar porque o token está indefinido, o Visual Studio desabilitará o comando até que você recarregue o projeto. No entanto, fazer alterações no projeto que definem a propriedade não atualiza o estado desses comandos, portanto, você ainda precisa recarregar o projeto nesses casos.

## <a name="command-target-structure"></a>Estrutura de destino do comando

O formato geral do elemento `<Target>` é mostrado no pseudocódigo a seguir:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Para referenciar propriedades do projeto ou variáveis de ambiente em valores de atributo, use o nome dentro de um token `$()`, como `$(StartupFile)` e `$(MSBuildProjectDirectory)`. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Atributos de destino

| Atributo | Necessária | Descrição |
| --- | --- | --- |
| Nome | Sim | O identificador do comando dentro do projeto do Visual Studio. Esse nome deve ser adicionado ao grupo de propriedades `<PythonCommands>` para que o comando seja exibido no submenu Python. |
| Rotular | Sim | O nome de exibição da interface do usuário que é exibido no submenu Python. |
| Retorna | Sim | Deve conter `@(Commands)`, que identifica o destino como um comando. |

### <a name="createpythoncommanditem-attributes"></a>Atributos de CreatePythonCommandItem

Todos os valores de atributo não diferenciam maiúsculas de minúsculas.

| Atributo | Necessária | Descrição |
| --- | --- | --- |
| TargetType | Sim | Especifica o que atributo de destino contém e como ele é usado junto com o atributo de argumentos:<ul><li>**executable**: executar o executável nomeado em Target, acrescentando o valor em Arguments, como se fosse inserido diretamente na linha de comando. O valor deve conter apenas um nome de programa sem argumentos.</li><li>**script**: executar `python.exe` com o nome do arquivo em Target, seguido pelo valor em Arguments.</li><li>**module**: executar `python -m` seguido pelo nome do módulo em Target, seguido pelo valor em Arguments.</li><li>**code**: executar o código embutido contido em Target. O valor de Arguments é ignorado.</li><li>**pip**: executar `pip` com o comando em Target, seguido por Arguments; é ExecuteIn é definido como "output", no entanto, o pip assume o comando `install` e usa o Target como o nome do pacote.</li></ul> |
| Destino | Sim | O nome de arquivo, o nome do módulo, o código ou comando pip a ser usado, dependendo do TargetType. |
| Arguments | Opcional | Especifica uma cadeia de caracteres de argumentos (se houver) a ser fornecida ao destino. Observe que, quando o TargetType é `script`, os argumentos são fornecidos para o programa Python, não ao `python.exe`. Ignorado para o TargetType `code`. |
| ExecuteIn | Sim | Especifica o ambiente no qual o comando deve ser executado:<ul><li>**console**: (padrão) executa o Target e os argumentos como se eles fossem inseridos diretamente na linha de comando. Uma janela de comando aparece quando o Target está em execução, em seguida, ela é fechada automaticamente.</li><li>**consolepause**: igual a um console, mas espera por um pressionamento de tecla antes de fechar a janela.</li><li>**output**: executa o Target e exibe seus resultados na janela de saída no Visual Studio. Se o TargetType for "pip", o Visual Studio usará o Target como o nome do pacote e acrescentará Arguments.</li><li>**repl**: executa o Target na [Janela Interativa do Python](interactive-repl.md). O nome de exibição opcional é usado para o título da janela.</li><li>**none**: comporta-se como o console.</li></ul>|
| WorkingDirectory | Opcional | A pasta na qual o comando deve ser executado. |
| ErrorRegex<br>WarningRegEx | Opcional | Usado somente quando ExecuteIn é `output`. Ambos os valores especificam uma expressão regular com a qual o Visual Studio analisa a saída do comando para mostrar erros e avisos na janela Lista de Erros. Se não for especificado, o comando não afetará a janela Lista de Erros. Para obter mais informações sobre o que o Visual Studio espera, confira [Grupos de captura nomeados](#named-capture-groups-for-regular-expression). |
| RequiredPackages | Opcional | Uma lista dos requisitos de pacote para o comando usando o mesmo formato que [requirements.txt](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). O comando **Executar PyLint**, por exemplo, especifica `pylint>=1.0.0`. Antes de executar o comando, o Visual Studio verifica se todos os pacotes na lista estão instalados. O Visual Studio usa o pip para instalar todos os pacotes ausentes. |
| Ambiente | Opcional | Uma cadeia de caracteres de variáveis de ambiente a ser definida antes da execução do comando. Cada variável usa o formato NOME=VALOR com várias variáveis separadas por ponto e vírgula. Uma variável com vários valores precisa estar entre aspas simples ou duplas, como 'NAME=VALUE1;VALUE2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Grupos de captura nomeados para expressões regulares

Durante a análise de erros e avisos de uma saída de comando, o Visual Studio espera que as expressões regulares nos valores `ErrorRegex` e `WarningRegex` usem os seguintes grupos nomeados:

- `(?<message>...)`: texto do erro
- `(?<code>...)`: código do erro
- `(?<filename>...)`: nome do arquivo para o qual o erro foi relatado
- `(?<line>...)`: número de linha do local no arquivo em que o erro foi relatado.
- `(?<column>...)`: número da coluna do local no arquivo em que o erro foi relatado.

Por exemplo, PyLint gera avisos da seguinte forma:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Para permitir que o Visual Studio extraia as informações corretas desses avisos e mostre-as na janela **Lista de Erros**, o valor de `WarningRegex` para o comando **Executar Pylint** deve ser o seguinte:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Observe que `msg_id` no valor deve ser realmente `code`, confira o [Problema 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="creating-a-targets-file-with-custom-commands"></a>Criando um arquivo .targets com comandos personalizados

Definir comandos personalizados em um arquivo de projeto disponibiliza esses comandos apenas para esse arquivo de projeto. Para usar os comandos em vários arquivos de projeto, defina o grupo de propriedades `<PythonCommands>` e todos os elementos `<Target>` em um arquivo `.targets`. Em seguida, importe esse arquivo nos arquivos de projeto individuais.

O arquivo `.targets` é formatado da seguinte maneira:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Para carregar um arquivo `.targets` em um projeto, coloque um elemento `<Import Project="(path)">` em qualquer lugar dentro do elemento `<Project>`. Por exemplo, se você tiver um arquivo chamado `CustomCommands.targets` em uma subpasta `targets` em seu projeto, use o seguinte código:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Sempre que você alterar o arquivo `.targets`, será necessário recarregar a *solução* que contém o projeto, não recarregar apenas o projeto.

## <a name="example-commands"></a>Comandos de exemplo

### <a name="run-pylint-module-target"></a>Executar PyLint (destino do módulo)

O código a seguir aparece no arquivo `Microsoft.PythonTools.targets`:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Executar a instalação de pip com um pacote específico (destino de pip)

O comando a seguir executa `pip install my-package` na janela de saída. Esse comando pode ser usado, por exemplo, ao desenvolver um pacote e testar sua instalação. Observe que Target contém o nome do pacote em vez do comando `install`, que é considerado ao usar `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Mostrar pacotes de pip desatualizados (destino de pip)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Executar um executável com consolepause

O comando a seguir simplesmente executa `where` para mostrar os arquivos Python sendo iniciados na pasta do projeto:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage;ShowOutdatedPackages;ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Comandos para executar o servidor e executar o servidor de depuração

Para explorar como os comandos **Iniciar servidor** e **Iniciar servidor de depuração** para projetos Web são definidos, examine o [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

## <a name="troubleshooting"></a>Solução de problemas

### <a name="message-the-project-file-could-not-be-loaded"></a>Mensagem: "Não foi possível carregar o arquivo de projeto"

Indica que há erros de sintaxe no arquivo de projeto. A mensagem inclui o erro específico com um número de linha e a posição do caractere.

### <a name="console-window-closes-immediately-after-command-is-run"></a>A janela do console é fechada imediatamente após a execução do comando

Use `ExecuteIn="consolepause"` em vez de `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>O comando não aparece no menu

Verifique se o comando está incluído no grupo de propriedades `<PythonCommands>` e se o nome na lista de comandos corresponde ao nome especificado no elemento `<Target>`.

Por exemplo, nos elementos a seguir, o nome "Example" no grupo de propriedades não corresponde ao nome "ExampleCommand" no destino. O Visual Studio não encontra um comando chamado "Example", portanto, não aparece nenhum comando. Use "ExampleCommand" na lista de comandos ou altere o nome do destino para apenas "Example".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Mensagem: Ocorreu um erro durante a execução de (nome do comando). Falha ao obter o comando (nome do destino) do projeto.

Indica que o conteúdo dos elementos `<Target>` ou `<CreatePythonCommandItem>` estão incorretos. Os motivos possíveis incluem:

- O atributo `Target` obrigatório está vazio.
- O atributo `TargetType` obrigatório está vazio ou contém um valor não reconhecido.
- O atributo `ExecuteIn` obrigatório está vazio ou contém um valor não reconhecido.
- `ErrorRegex` ou `WarningRegex` está especificado sem a configuração de `ExecuteIn="output"`.
- Atributos não reconhecidos existem no elemento. Por exemplo, você pode ter usado `Argumnets` (escrito de forma incorreta) em vez de `Arguments`.

Os valores de atributo poderão ficar vazios se você fizer referência a uma propriedade que não esteja definida. Por exemplo, se você usar o token `$(StartupFile)`, mas nenhum arquivo de inicialização tiver sido definido no projeto, o token será resolvido como uma cadeia de caracteres vazia. Nesses casos, é interessante definir um valor padrão. Por exemplo, os comandos **Executar servidor** e **Executar servidor de depuração** definidos nos modelos de projeto Bottle, Flask e Django considerarão `manage.py` como o padrão se você não especificar um arquivo de inicialização do servidor nas propriedades do projeto.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>O Visual Studio trava e falha ao executar o comando

Provavelmente você está tentando executar um comando do console com `ExecuteIn="output"` e, nesse caso, o Visual Studio pode falhar ao tentar analisar a saída. Use `ExecuteIn="console"` em seu lugar. (Confira o [Problema 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operate-program-or-batch-file"></a>O comando executável "não é reconhecido como um comando interno ou externo, programa de operação ou arquivo em lotes"

Ao usar `TargetType="executable"`, o valor em `Target` precisa ser *somente* o nome do programa sem argumentos, como "python" ou "python.exe". Mover argumentos para o atributo `Arguments`.
