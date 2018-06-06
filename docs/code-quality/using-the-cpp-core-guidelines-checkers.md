---
title: Usando os verificadores de diretrizes de núcleos de C++
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: f8b031fc1251ad06fdba154c086696337e552445
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747398"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usando os verificadores de diretrizes de núcleos de C++
As diretrizes de núcleos de C++ são um conjunto portátil de diretrizes, regras e as práticas recomendadas sobre como codificar em C++ criado por especialistas de C++ e designers. Visual Studio atualmente oferece suporte a um subconjunto dessas regras como parte de suas ferramentas de análise de código do C++. Os verificadores de diretriz de núcleo são instalados por padrão no Visual Studio de 2017 e são [disponível como um pacote do NuGet para Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>O projeto de diretrizes de núcleos de C++
 As diretrizes de núcleos de C++ criado por Bjarne Stroustrup e outros, são um guia para usar o C++ moderno com segurança e eficácia. As diretrizes enfatizam a segurança de tipo estático e segurança de recursos. Eles identificarem maneiras de eliminar ou minimizar as partes mais propensas a erros do idioma e sugerem como tornar seu código mais simples e mais funcionais, de forma confiável. Essas diretrizes são mantidas pela base de C++ padrão. Para obter mais informações, consulte a documentação, [diretrizes de núcleos de C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e acessar os arquivos de projeto de documentação de diretrizes de núcleos de C++ em [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar as diretrizes de C++ Core verificar na análise de código
 Você pode habilitar a análise de código em seu projeto, selecionando o **habilitar análise de código na compilação** caixa de seleção no **análise de código** seção o **páginas de propriedade** caixa de diálogo seu projeto.

 ![Página de propriedades de configurações gerais de análise de código](../code-quality/media/cppcorecheck_codeanalysis_general.png)

 As regras de verificação de núcleo do C++ são extensões para os conjuntos de regra padrão que são executados quando a análise de código está habilitada. Porque as regras de verificação de núcleo de C++ estão em desenvolvimento, algumas regras são bem estabelecidas e alguns não estejam prontos para uso em todo o código, mas podem ainda ser informativo. As regras são divididas em dois grupos: liberado e experimental. Você pode optar por executar as regras de lançamento ou experimentais nas propriedades de seu projeto.

 ![Página de propriedades para configurações de extensões de análise de código](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

 Para habilitar ou desabilitar os conjuntos de regras C++ Core verificar, abra o **páginas de propriedade** caixa de diálogo para seu projeto. Em **propriedades de configuração**, expanda **análise de código**, **extensões**. Na lista suspensa ao lado de controle **habilitar C++ Core verificar (liberados)** ou **habilitar C++ Core verificar (Experimental)**, escolha **Sim** ou **não**. Escolha **Okey** ou **aplicar** para salvar suas alterações.

## <a name="examples"></a>Exemplos
 Aqui está um exemplo de alguns dos problemas que podem encontrar as regras de verificação de núcleo do C++:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

 Este exemplo demonstra alguns avisos que podem encontrar as regras de verificação de núcleo do C++:

-   C26494 é regra Type.5: sempre inicializar um objeto.

-   C26485 é regra Bounds.3: decay nenhum ponteiro de matriz.

-   C26481 é regra Bounds.1: não usar aritmética de ponteiro. Use `span` em seu lugar.

 Se o conjunto de regras de análise código C++ Core verificar está instalados e habilitados quando você compila seu código, os dois primeiros são saída, mas a terceira é suprimida. Aqui está a saída da compilação do código de exemplo:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

As diretrizes de núcleos de C++ existem para ajudá-lo a escrever código melhor e mais seguro. No entanto, se você tiver uma instância em que uma regra ou um perfil não deve ser aplicado, é fácil suprimi-lo diretamente no código. Você pode usar o `gsl::suppress` atributo para impedir C++ Core verificar detectar e relatar qualquer violação de uma regra no bloco de código a seguir. Você pode marcar instruções individuais para suprimir regras específicas. Você mesmo pode suprimir todo o perfil de limites, escrevendo `[[gsl::suppress(bounds)]]` sem a inclusão de um número específico de regra.

## <a name="supported-rule-sets"></a>Suporte para conjuntos de regras
Conforme novas regras são adicionadas para o verificador de diretrizes de núcleos de C++, pode aumentar o número de avisos que são produzidas para o código já existente. Você pode usar conjuntos de regras predefinidas para filtrar os tipos de regras para permitir.
Tópicos de referência para a maioria das regras estão sob [Visual Studio C++ Core verificar referência](code-analysis-for-cpp-corecheck.md).

A partir do Visual Studio 2017 versão 15,3, os conjuntos de regra com suporte são:
  - **Regras de ponteiro de proprietário** impor [verifica de gerenciamento de recursos relacionados ao proprietário<T> das diretrizes de núcleos de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Regras constantes** impor [relacionados const verificações das diretrizes de núcleos de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Regras de ponteiro bruto** impor [recursos de gerenciamento verifica relacionado ao bruto ponteiros das diretrizes de núcleos de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Regras de ponteiro exclusivas** impor [verificações de gerenciamento de recursos relacionados a tipos de semântica do ponteiro exclusivo das diretrizes de núcleos de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Limites de regras** impor o [limites perfil das diretrizes de núcleos de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Regras de tipo** impor o [tipo de perfil das diretrizes de núcleos de C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

  **Visual Studio 2017 versão 15.5**:
  - **Classe regras** algumas regras que se concentrar em uso adequado de métodos especiais e especificações virtuais. Este é um subconjunto de verificações recomendado para [classes e hierarquias de classe](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
  - **Regras de simultaneidade** uma única regra, que captura objetos protetor declarado incorretamente. Para obter mais informações, consulte [diretrizes relacionadas à simultaneidade](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
  - **Regras de declaração** algumas regras de [interfaces diretrizes](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) que se concentram em variáveis como globais são declarados.
  - **Função regras** duas verificações que ajudam com a adoção do `noexcept` especificador. Esta é uma parte das diretrizes de [limpar função design e implementação](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
  - **Regras de ponteiro compartilhado** como parte do [gerenciamento de recursos](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) imposição de diretrizes, adicionamos algumas regras específicas para ponteiros como compartilhados são passadas para funções ou usadas localmente.
  - **Regras de estilo** uma verificação simple, mas importante, que proibe o uso de [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Essa é a primeira etapa no aprimoramento de codificação de estilo e o uso de expressões e instruções em C++.

  **Visual Studio 2017 versão 15.6**:
  - **Regras aritméticas** regras para detectar aritmética [estouro](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [assinados não assinados operações](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) e [bits manipulação](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).


 Você pode optar por limitar avisos para um ou alguns dos grupos. O **mínimo nativo** e **recomendado nativo** regra conjuntos incluem regras de verificação de núcleo de C++ além de outras verificações PREfast. Para ver o disponíveis conjuntos de regras, abra a caixa de diálogo Propriedades do projeto, selecione **código Analysis\General**, abra o menu suspenso no **conjuntos de regras de** caixa de combinação e selecione **escolher vários conjuntos de regras** . Para obter mais informações sobre como usar conjuntos de regras no Visual Studio, consulte [usando conjuntos de regras para agrupar regras de análise de código](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macros
 O verificador de diretrizes de núcleos de C++ vem com um arquivo de cabeçalho que define as macros que tornam mais fácil suprimir todas categorias de avisos no código:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Essas macros correspondem aos conjuntos de regras e expandem para uma lista separada por espaços de números de aviso. Usando as construções de pragma apropriado, você pode configurar o conjunto efetivo de regras que são interessante para um projeto ou uma seção de código. No exemplo a seguir, a análise de código avisa apenas sobre ausente modificadores constantes:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atributos
 O compilador do Microsoft Visual C++ tem um suporte limitado para o GSL suprimir o atributo. Ele pode ser usado para suprimir avisos em expressões e instruções do bloco dentro de uma função.

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Supressão de análise usando opções de linha de comando
 Em vez de #pragmas, você pode usar opções de linha de comando na página de propriedades do arquivo para suprimir avisos para um projeto ou um único arquivo. Por exemplo, para desabilitar o aviso 26400 para um arquivo:

 1) Clique no arquivo em **Gerenciador de soluções**

 2) Escolha **propriedades | C / C++ | Linha de comando**

 3) No **opções adicionais** janela, adicionar `/wd26400`.

 Você pode usar a opção de linha de comando para desabilitar temporariamente todos os análise de código para um arquivo, especificando `/analyze-`. Isso gera o aviso *D9025 substituindo '/ANALYZE' com ' /ANALYZE -'*, que informa você habilitar análise de código novamente mais tarde.

 ## <a name="corecheck_per_file"></a> Habilitar o verificador de diretrizes de núcleos C++ em arquivos de projeto específico
Às vezes, pode ser útil para análise de código foco e ainda usar o Visual Studio IDE. O cenário de exemplo a seguir pode ser usado para projetos grandes para economizar tempo de compilação e tornar mais fácil para os resultados do filtro:

1.  No shell de comando do conjunto de `esp.extension` e `esp.annotationbuildlevel` variáveis de ambiente.
2.  Para herdar essas variáveis, inicie o Visual Studio, no shell de comando.
3.  Carregue seu projeto e abra suas propriedades.
4.  Habilitar análise de código, selecione os conjuntos de regra apropriado, mas não habilitar extensões de análise de código.
5.  Vá para o arquivo que você deseja analisar com o verificador de diretrizes de núcleos de C++ e abra suas propriedades.
6.  Escolha **C / C++ \Command opções de linha de** e adicione `/analyze:plugin EspXEngine.dll`
7.  Desabilitar o uso de cabeçalho pré-compilado (**C / C++ \Precompiled cabeçalhos**). Isso é necessário porque o mecanismo de extensões pode tentar ler suas informações internas de cabeçalho pré-compilado (PCH); Se o PCH compilado com as opções de projeto padrão, ele não será compatível.
8.  Recompile o projeto. As verificações de PREFast comuns devem ser executado em todos os arquivos. Porque o verificador de diretrizes de núcleos de C++ não está habilitado por padrão, ele só deve ser executado no arquivo que está configurado para usá-lo.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Como usar o verificador de diretrizes de núcleos de C++ fora do Visual Studio
Você pode usar as verificações de diretrizes de núcleos de C++ em compilações automatizadas.

### <a name="msbuild"></a>MSBuild
 O verificador de análise de código nativo (PREfast) está integrado ao ambiente do MSBuild arquivos de destino personalizado. Você pode usar as propriedades do projeto para habilitá-lo e adicionar o verificador de diretrizes de núcleos de C++ (que é baseado no PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Certifique-se de que adicionar essas propriedades antes da importação do arquivo Microsoft.Cpp.targets. Pode escolher conjuntos de regras específicas ou criar um conjunto de regras personalizado ou usar o conjunto de regras padrão que inclui outras verificações PREfast.

Você pode executar o verificador de núcleo de C++ somente em arquivos especificados usando a mesma abordagem [descrita anteriormente](#corecheck_per_file), mas o uso de arquivos do MSBuild. As variáveis de ambiente podem ser definidas usando o `BuildMacro` item:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Se você não quiser modificar o arquivo de projeto, você pode passar as propriedades na linha de comando:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projetos de MSBuild não
Se você usar um sistema de compilação não depende de MSBuild ainda é possível executar o verificador, mas você precisa para se familiarizar com alguns recursos internos de configuração do mecanismo de análise de código. Não há garantia de que essas operações internas suporte no futuro.

Você precisa definir algumas variáveis de ambiente e usar opções de linha de comando adequadas para o compilador. É melhor trabalhar no ambiente do "Prompt de comando de ferramentas nativas" para que você não precisa pesquisar caminhos específicos para o compilador, incluir diretórios, etc.

1.  **Variáveis de ambiente**
  - `set esp.extensions=cppcorecheck.dll` Isso informa ao mecanismo para carregar o módulo de diretrizes de núcleos de C++.
  - `set esp.annotationbuildlevel=ignore` Isso desabilita a lógica que processa as anotações SAL. Anotações não afetam a análise de código no verificador de diretrizes de núcleos de C++, ainda que o processamento leva tempo (às vezes, muito tempo). Essa configuração é opcional, mas altamente recomendado.
  - `set caexcludepath=%include%` É altamente recomendável que você desabilite avisos que são acionados em cabeçalhos padrão. Você pode adicionar mais caminhos aqui, por exemplo, o caminho para os cabeçalhos comuns em seu projeto.
2.  **Opções de linha de comando**
  - `/analyze`  Permite análise de código (Considere também usar /ANALYZE: apenas e /ANALYZE: quiet).
  - `/analyze:plugin EspXEngine.dll` Esta opção carrega o mecanismo de extensões de análise de código para o PREfast. Esse mecanismo, por sua vez, carrega o verificador de diretrizes de núcleos de C++.



## <a name="use-the-guideline-support-library"></a>Use a biblioteca de suporte de diretriz
 A biblioteca de suporte de diretriz foi projetada para ajudá-lo a seguir as diretrizes de núcleos. O GSL inclui definições que permitem que você substitua construções propensas a erro alternativas mais seguras. Por exemplo, você pode substituir um `T*, length` par de parâmetros com o `span<T>` tipo. O GSL está disponível em [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). A biblioteca é o código-fonte aberto, para que você pode exibir as fontes, fazer comentários ou contribuir. O projeto pode ser encontrado em [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Use as diretrizes a verificação de núcleo de C++ em projetos do Visual Studio 2015
  Se você usar o Visual Studio 2015, os conjuntos de regras de análise de código C++ Core Check não são instalados por padrão. Você deve executar algumas etapas adicionais antes de habilitar as ferramentas de análise de código C++ Core verificar no Visual Studio 2015. Microsoft fornece suporte para projetos do Visual Studio 2015 usando um pacote do Nuget. O pacote é chamado Microsoft.CppCoreCheck e está disponível em [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Este pacote requer que você tem pelo menos o Visual Studio 2015 com atualização 1 instalado.

 O pacote também instala outro pacote como uma dependência, uma biblioteca de suporte diretriz (GSL) somente cabeçalho. O GSL também está disponível no GitHub em [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 Por causa da forma que as regras de análise de código são carregadas, você deve instalar o pacote Microsoft.CppCoreCheck NuGet em cada projeto de C++ que você deseja verificar no Visual Studio 2015.

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Para adicionar o pacote de Microsoft.CppCoreCheck ao seu projeto no Visual Studio 2015

1.  Em **Solution Explorer**, com o botão direito para abrir o menu de contexto do projeto na solução que você deseja adicionar o pacote. Escolha **gerenciar pacotes NuGet** para abrir o **NuGet Package Manager**.

2.  No **NuGet Package Manager** janela, procure Microsoft.CppCoreCheck.

     ![Janela do Gerenciador de pacotes do NuGet mostra CppCoreCheck pacote](../code-quality/media/cppcorecheck_nuget_window.png)

3.  Selecione o pacote de Microsoft.CppCoreCheck e, em seguida, escolha o **instalar** botão para adicionar as regras para seu projeto.

 O pacote NuGet adiciona adicionais do MSBuild *. targets* ao seu projeto que é invocado quando você habilitar a análise de código em seu projeto. Isso *. targets* arquivo adiciona as regras de verificação de núcleo de C++ como uma extensão adicional para a ferramenta de análise de código do Visual Studio. Quando o pacote for instalado, você pode usar a caixa de diálogo páginas de propriedades para habilitar ou desabilitar as regras de lançamento e experimentais.

## <a name="see-also"></a>Consulte também
[Referência do Visual Studio C++ Core seleção](code-analysis-for-cpp-corecheck.md).

