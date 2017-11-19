---
title: "Criar exibições personalizadas de objetos nativos no depurador | Microsoft Docs"
ms.custom: 
ms.date: 06/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: natvis
dev_langs: C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2aa3a6f515ca039c86d453f5729800fe8e1637c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-views-of-native-objects-in-the-visual-studio-debugger"></a>Criar exibições personalizadas de objetos nativos no depurador do Visual Studio
A estrutura de Natvis do Visual Studio permite que você personalize a forma como o Visual Studio exibe os tipos nativos nas janelas de variáveis do depurador (por exemplo, o **inspecionar** janela, **locais** janela e em  **DataTips**.
  
 Natvis substitui o **autoexp.dat** arquivo que foi usado em versões anteriores do Visual Studio e sintaxe XML de ofertas, diagnósticos mais precisos, controle de versão e suporte a vários arquivos.  
  
> [!NOTE]
>  Você não pode usar a estrutura de Natvis para visualizações quando:  
>   
>  -  Você está depurando um projeto de área de trabalho do Windows do C++ com o tipo de depurador definido como **misto**.  
> -   Você está fazendo a depuração de modo misto em um aplicativo de área de trabalho do Windows no modo de compatibilidade gerenciado (**Ferramentas > Opções > Depuração > Geral > usar o modo de compatibilidade gerenciado**).  
> -   Você está depurando um aplicativo de área de trabalho do Windows no modo de compatibilidade nativo (**Ferramentas > Opções > Depuração > Geral > usar modo de compatibilidade nativo**).  
  
##  <a name="BKMK_Why_create_visualizations_"></a>Por que criar visualizações de Natvis?  
 Você pode usar a estrutura de Natvis para criar regras de visualização para os tipos que você criar para que os desenvolvedores possam vê-las facilmente durante a depuração.  
  
 Por exemplo, a ilustração a seguir mostra uma variável do tipo [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) que é exibido no depurador sem qualquer visualizações personalizadas aplicadas.  
  
 ![Visualização da caixa de texto padrão](../debugger/media/dbg_natvis_textbox_default.png "DBG_NATVIS_TextBox_Default")  
  
 A linha realçada mostra o `Text` propriedade o `TextBox` classe. A hierarquia de classe complexos torna difícil encontrar esse valor; Além disso, o depurador não saiba como interpretar o tipo de cadeia de caracteres personalizada usado pelo objeto, para que você não pode ver a cadeia de caracteres mantida dentro da caixa de texto.  
  
 O mesmo `TextBox` parece muito mais simples na janela variável quando forem aplicadas regras de visualização personalizada. Os membros importantes da classe podem ser exibidos juntos, e o depurador mostra o valor de cadeia de caracteres subjacente do tipo cadeia de caracteres personalizada.  
  
 ![Usando o Visualizador de dados de caixa de texto](../debugger/media/dbg_natvis_textbox_visualizer.png "DBG_NATVIS_TextBox_Visualizer")  
  
##  <a name="BKMK_Using_Natvis_files"></a>Usando arquivos nativos  
 arquivos. natvis são arquivos XML com uma extensão. natvis. O esquema é definido no **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  
  
 A estrutura básica de um arquivo. natvis é uma ou mais `Type` elementos, onde cada `Type` elemento representa uma entrada de visualização para um tipo cujo nome totalmente qualificado é especificado no `Name` atributo.  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  
  
  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  
  
 O Visual Studio fornece alguns arquivos. natvis **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** pasta. Esses arquivos contêm regras de visualização para muitos tipos comuns e podem servir como exemplos de quando você estiver escrevendo visualizações para novos tipos.  
  
## <a name="adding-natvis-files-to-your-projects"></a>Adicionando arquivos. natvis seus projetos  
 Você pode adicionar arquivos. natvis a qualquer projeto C++.  
  
 Para adicionar um novo arquivo. natvis, com um projeto aberto do C++, selecione o nó do projeto no **Solution Explorer**e clique em **Adicionar > novo item > Visual C++ > utilitário > arquivo de visualização do depurador (. natvis)**. O depurador carregará arquivos Natvis de projetos do C++ automaticamente. Por padrão, os arquivos Natvis em seu projeto também são inseridos no arquivo. PDB compilado pelo projeto. Isso significa que se você depurar o binário compilado por este projeto, o depurador carregará o arquivo Natvis do. o PDB mesmo se você não tiver o projeto aberto. Se você não quiser que o arquivo. natvis a serem incluídas no. o PDB, com o botão direito do arquivo. natvis no **Solution Explorer**e no **propriedades de configuração** janela conjunto **excluído da compilação**  para **Sim**.  
  
 É recomendável que você edite arquivos Natvis usando o Visual Studio qualquer alteração feita durante a depuração entrarão em vigor automaticamente quando você salvar o arquivo. Você também pode obter uma melhor experiência de edição do IntelliSense.  
  
 Arquivos Natvis que são carregados de um. PDB se aplicam somente aos tipos no módulo ao qual se refere o pdb. Por exemplo, se Module1.pdb define uma entrada para um tipo chamado `Test`, esta entrada só é aplicada para o **teste** classe Module1.dll. Se o outro módulo também define uma classe denominada **teste**, entrada de natvis do Module1.pdb não se aplica a ele.  
  
##  <a name="BKMK_natvis_location"></a>Implantando arquivos. natvis  
 Se o arquivo. natvis se aplica somente aos tipos de que você está criando um projeto do Visual Studio, você não precisa fazer nada; a. natvis está incluído no. o PDB. Você no entanto, pode adicionar arquivos. natvis para seu diretório de usuário ou para um diretório de sistema se você deseja que se aplicam a vários projetos.  
  
 A ordem na qual. natvis arquivos são avaliados é da seguinte maneira:  
  
1.  arquivos. natvis inserido em um. PDB que você está depurando (a menos que existe um arquivo de mesmo nome em um projeto carregado).  
  
2.  arquivos. natvis que fazem parte de um projeto de C++ carregado ou um item de solução de nível superior. Esse grupo inclui carregados todos os projetos em C++, incluindo bibliotecas de classe, mas ele não inclui projetos de outros idiomas (por exemplo, você não pode carregar um arquivo. natvis de um projeto c#). Para projetos executável, você deve usar os itens de solução para hospedar os arquivos. natvis que não ainda estão presentes em um. PDB, porque não há nenhum projeto C++.  
  
3.  O diretório natvis específicas do usuário (por exemplo, **%USERPROFILE%\Documents\Visual Studio 2017\Visualizers** ou **%USERPROFILE%\My Documentos\Visual Studio 2015\Visualizers**).  
  
4.  O diretório do sistema Natvis (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). Este diretório é onde os arquivos. natvis que são instalados com o Visual Studio são copiados. Se você tiver permissões de administrador, você pode adicionar outros arquivos para este diretório também.  
  
## <a name="modifying-natvis-files-while-debugging"></a>Modificando arquivos. natvis durante a depuração  
 Você pode modificar um arquivo. natvis no IDE durante a depuração do projeto no qual ele está incluído. Abra o arquivo no IDE (usando a mesma instância do Visual Studio que você está depurando com), modificá-lo e salvá-lo. Assim que o arquivo é salvo, o **inspecionar** e **locais** windows devem ser atualizado para refletir a alteração. Se você modificar o arquivo. natvis fora do IDE, as alterações não entram em vigor automaticamente. Para atualizar os windows, você pode avaliar o **.natvisreload** do **inspecionar** janela. Essa ação faz com que as alterações entrem em vigor sem reiniciar a sessão de depuração.  
  
 Você também pode adicionar ou excluir arquivos. natvis para uma solução que você está depurando, e o Visual Studio adiciona ou remove as visualizações relevantes.  
  
 Se um arquivo. natvis é inserido em um. PDB, você não pode modificá-lo enquanto você está depurando.  
  
 Use o **.natvisreload** comando quando você estiver atualizando o arquivo natvis para uma versão mais recente (por exemplo, se é verificado no controle de origem e você deseja acompanhar as alterações recentes criado por outra pessoa no arquivo). É recomendável que você edite arquivos natvis usando o editor de xml do Visual Studio.  
  
##  <a name="BKMK_Expressions_and_formatting"></a>Expressões e formatação  
 As visualizações do Natvis usam expressões do C++ para especificar os itens de dados a serem exibidos. Além dos aprimoramentos e limitações de expressões de C++ no depurador que são descritas na [o operador de contexto (C++)](../debugger/context-operator-cpp.md), você deve estar ciente das seguintes diferenças:  
  
-   As expressões do Natvis são avaliadas no contexto do objeto que está sendo visualizado, não do registro de ativação atual. Por exemplo, se você usar `x` em uma expressão de Natvis, o identificador se refere ao campo denominado `x` no objeto sendo visualizado, não para uma variável local chamada `x` na função em execução no momento. Você não pode acessar variáveis locais em expressões de Natvis, embora você possa acessar as variáveis globais.  
  
-   As expressões do natvis não permitem avaliação ou efeitos colaterais de função. Isso significa que as chamadas de função e os operadores de atribuição são ignorados. Porque [funções intrínsecas do depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) estão efeito colateral gratuitamente, elas podem ser livremente chamadas de qualquer expressão Natvis, embora outras chamadas de função não são permitidas.  
  
 Para controlar como uma expressão é exibida em uma janela variável, você pode usar qualquer um dos especificadores de formato descritos a [especificadores de formato](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) seção o [especificadores de formato em C++](../debugger/format-specifiers-in-cpp.md) tópico. Observe que os especificadores de formato são ignorados quando a entrada de virtualização é usada internamente pelo Natvis, como o `Size` expressão em uma [ArrayItems expansão](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  
  
## <a name="natvis-views"></a>Modos de exibição de Natvis  
 Modos de exibição Natvis permitem que você veja qualquer tipo em mais de uma maneira. Por exemplo, você pode definir uma exibição nomeada **simples** que fornece a você uma exibição simplificada de um tipo. Por exemplo, aqui está a visualização de `std::vector`:
  
```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  
  
 O `DisplayString` e `ArrayItems` elementos são usados no modo de exibição padrão e o modo de exibição simple, enquanto o `[size]` e `[capacity]` itens são excluídos de modo de exibição simple. Você pode usar o **, exibição** especificador para especificar um modo de exibição alternativo de formato. No **inspecionar** janela, que você especificar o modo de exibição simple como **vec,view(simple)**:  
  
 ![Janela Inspecionar com modo de exibição simple](../debugger/media/watch-simpleview.png "SimpleView de inspeção")  
  
##  <a name="BKMK_Diagnosing_Natvis_errors"></a>Diagnosticando erros de Natvis  
 Você pode usar o diagnóstico de Natvis para solucionar problemas de sintaxe e erros de análise. Quando o depurador encontrar erros em uma entrada de visualização, ele ignora os erros e o exibe o tipo na forma bruta ou seleciona outra visualização adequada. Para entender por que um determinada entrada de visualização será ignorada e para ver quais são os erros subjacentes, você pode ativar diagnóstico Natvis **Ferramentas > Opções > Depuração > janela de saída > Natvis mensagens de diagnóstico (C++)** opção. Os erros são exibidos no **saída** janela.  
  
##  <a name="BKMK_Syntax_reference"></a>Referência de sintaxe Natvis  
  
###  <a name="BKMK_AutoVisualizer"></a>Elemento AutoVisualizer  
 O `AutoVisualizer` elemento é o nó raiz do arquivo. natvis e contém o namespace `xmlns:` atributo.  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  
  
###  <a name="BKMK_Type"></a>Elemento de tipo  
 Um tipo básico tem esta aparência:  
  
```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  
  
 Ele especifica:  
  
1.  Para qual tipo essa visualização deve ser usada (atributo `Type Name`).  
  
2.  Como o valor de um objeto desse tipo deve ficar (o `DisplayString` elemento).  
  
3.  O que os membros do tipo devem ter aparência quando o usuário expande em uma janela variável (o `Expand` nó).  
  
 **Classes de modelo** o `Name` atributo o `Type` elemento aceita um asterisco `*` como um caractere curinga que pode ser usado para nomes de classe de modelo:  
  
```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
  
```  
  
 Neste exemplo, a mesma visualização é usada se o objeto é um `CAtlArray<int>` ou `CAtlArray<float>`. Se houver uma entrada de visualização específica para um `CAtlArray<float>`, em seguida, ela terá precedência sobre genéricos.  
  
 Observe que os parâmetros do modelo podem ser referenciados na entrada de visualização usando as macros $T1, $T2 e assim por diante. Para localizar exemplos dessas macros, consulte os arquivos .natvis que acompanham o Visual Studio.  
  
####  <a name="BKMK_Visualizer_type_matching"></a>Correspondência de tipo de Visualizador  
 Se uma entrada de visualização não for validado, a próxima visualização disponível é usada.  
  
#### <a name="inheritable-attribute"></a>Atributo herdável  
 Você pode especificar se uma visualização se aplica somente a um tipo base ou um tipo base e todos os tipos derivados com opcional `Inheritable` atributo. A seguir, a visualização só é aplicável a `BaseClass` tipo:  
  
```xml
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  
  
 O valor padrão de `Inheritable` é `true`.  
  
#### <a name="priority-attribute"></a>Atributo de prioridade  
 O `Priority` atributo especifica a ordem na qual alternativas definições são usadas se uma definição de falha ao analisar. Os valores possíveis de `Priority` são: `Low`, `MediumLow`,`Medium`, `MediumHigh`, e `High`, e o valor padrão é `Medium`.  
  
 O atributo de prioridade só deve ser usado para distinguir entre as prioridades de dentro do mesmo arquivo. natvis, não entre diferentes arquivos.  
  
 No exemplo a seguir, podemos primeiro analisar a entrada que corresponde a STL 2015 e, se isso falhar ao analisar, usamos a entrada alternativa para a versão de 2013 do STL:  
  
```xml
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  
  
<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  
  
####  <a name="BKMK_Versioning"></a>Elemento de versão  
 Use o elemento `Version` para definir o escopo de visualizações para módulos específicos e suas versões de modo que seja possível minimizar conflitos de nome e usar visualizações diferentes para versões diferentes de tipos. Por exemplo:  
  
```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 Neste exemplo, a visualização é aplicável somente para o `DirectUI::Border` tipo encontrado o `Windows.UI.Xaml.dll` da versão 1.0 para 1.5. A adição de elementos de versão escopos a entrada de visualização para um módulo específico e a versão e reduz incompatibilidades acidentais. No entanto, se um tipo é definido em um arquivo de cabeçalho comum que é usado por módulos diferentes, a visualização com controle de versão não é aplicada quando o tipo não é o módulo especificado.  
  
#### <a name="optional-attribute"></a>Atributo opcional  
 O `Optional` atributo pode aparecer em qualquer nó. Se qualquer subexpressão dentro de um nó opcional não conseguir analisar, esse nó será ignorado, mas o restante do elemento Type ainda é válido. O seguinte tipo, `[State]` não seja opcional, mas `[Exception]` é opcional.  Isso significa que se `MyNamespace::MyClass` contém um campo chamado _`M_exceptionHolder`, você ainda vir ambos `[State]` nó e o `[Exception]` nó, mas se o `_M_exceptionHolder` está ausente, você verá apenas o `[State]` nó.
  
```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  
  
###  <a name="BKMK_Condition_attribute"></a>Atributo de condição  
 O atributo opcional `Condition` está disponível para muitos elementos de visualização e especifica quando uma regra de visualização deve ser usada. Se a expressão dentro do atributo de condição resolve para `false`, em seguida, a regra de visualização especificada pelo elemento não será aplicada. Se ele for avaliada como true, ou se não houver nenhum `Condition` de atributo, em seguida, a regra de visualização é aplicada ao tipo. Você pode usar esse atributo para `if-else` lógica nas entradas de visualização. Por exemplo, a visualização a seguir tem duas `DisplayString` elementos de um tipo de ponteiro inteligente:  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
  
```  
  
 Quando o `_Myptr` membro é `null`, a condição do primeiro `DisplayString` elemento resolve para `true`, de modo que o formulário é exibido. Quando o `_Myptr` membro não é `null`, a condição for avaliada como `false`e a segunda `DisplayString` elemento é exibido.  
  
### <a name="includeview-and-excludeview-attributes"></a>Atributos IncludeView e ExcludeView  
 Esses atributos especificam os elementos que serão exibidos ou não exibidos em modos diferentes. Por exemplo, dada a especificação de Natvis de `std::vector`:  
  
```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  
  
 O modo de exibição simple não mostra o [tamanho] e [capacidade] itens no modo de exibição simple. Se usamos `IncludeView="simple"` em vez de `ExcludeView`, o `[size]` e `[capacity]` itens seriam exibidos no modo de exibição simple, em vez de na exibição padrão.  
  
 Você pode usar o `IncludeView` e `ExcludeView` atributos em tipos, bem como em membros individuais.  
  
###  <a name="BKMK_DisplayString"></a>DisplayString  
 Um elemento `DisplayString` especifica a cadeia de caracteres a ser exibida como o valor da variável. Aceita cadeias de caracteres arbitrárias misturadas a expressões. Tudo entre chaves é interpretado como uma expressão. Por exemplo, um `DisplayString` entrada semelhante à seguinte:  
  
```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
  
```  
  
 Significa que as variáveis do tipo `CPoint` são exibidos como mostra esta ilustração:  
  
 ![Usando um elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "DBG_NATVIS_CPoint_DisplayString")  
  
 Na expressão `DisplayString`, `x` e `y`, que são membros de `CPoint`, estão entre chaves e, portanto, seus valores são avaliados. A expressão também mostra como você pode ignorar um par de chaves usando chaves duplas ( `{{` ou `}}` ).  
  
> [!NOTE]
>  O `DisplayString` é o único elemento que aceita a sintaxe de par de chaves e cadeias de caracteres arbitrárias. Todos os outros elementos de visualização aceitam apenas expressões avaliadas pelo depurador.  
  
###  <a name="BKMK_StringView"></a>StringView  
 O elemento `StringView` define a expressão cujo valor será enviado ao visualizador interno de texto. Por exemplo, suponha que temos a seguinte visualização para o tipo `ATL::CStringT`:  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  
  
 A visualização exibe um objeto `CStringT` em uma janela variável como esta:   
  
 ![Elemento CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "DBG_NATVIS_DisplayString_CStringT")  
  
 Adicionando um `StringView` elemento indica o depurador que esse valor pode ser exibido por uma visualização de texto:  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  
  
 Observe o ícone de lupa mostrado ao lado do valor abaixo. Escolher o ícone inicia o Visualizador de texto que exibe a cadeia de caracteres que `m_pszData` aponta para.  
  
 ![Dados de CStringT com visualizador StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "DBG_NATVIS_StringView_CStringT")  
  
> [!NOTE]
>  Observe que a expressão `{m_pszData,su}` inclui um especificador de formato C++ `su` para exibir o valor como uma cadeia de caracteres Unicode. Consulte [especificadores de formato em C++](../debugger/format-specifiers-in-cpp.md) para obter mais informações.  
  
###  <a name="BKMK_Expand"></a>Expanda  
 O nó `Expand` é usado para personalizar os filhos do tipo visualizado quando o usuário o expandir nas janelas variáveis. Aceita uma lista de nós filhos que definem os elementos filhos.  
  
 O nó `Expand` é opcional.  
  
-   Se um `Expand` nó não for especificado em uma entrada de visualização, regras de expansão padrão do Visual Studio são usadas.  
  
-   Se um `Expand` nó é especificado sem nós filho sob ele, o tipo de não ser expansível nas janelas do depurador.  
  
####  <a name="BKMK_Item_expansion"></a>Expansão de item  
 O elemento `Item` é o elemento mais básico e mais comum para ser usado em um nó `Expand`. `Item` define um único elemento filho. Por exemplo, suponha que você tenha uma classe `CRect` com `top`, `left`, `right` e `bottom` como campos e a seguinte entrada de visualização:  
  
```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
  
```  
  
 O `CRect` tipo terá esta aparência:  
  
 ![CRect com expansão de elemento Item](../debugger/media/dbg_natvis_expand_item_crect1.png "DBG_NATVIS_Expand_Item_CRect1")  
  
 As expressões especificadas nos elementos `Width` e `Height` são avaliadas e mostradas na coluna de valor. O `[Raw View]` nó é criado automaticamente pelo depurador sempre que uma expansão personalizada é usada. Ele é expandido na captura de tela acima para mostrar como o modo de exibição bruto do objeto é diferente de sua visualização. A expansão padrão do Visual Studio cria uma subárvore para a classe base e lista todos os membros de dados da classe base como filhos.  
  
> [!NOTE]
>  Se a expressão do elemento item aponta para um tipo complexo, o `Item` próprio nó é expansível.  
  
####  <a name="BKMK_ArrayItems_expansion"></a>Expansão de ArrayItems  
 Use o nó `ArrayItems` para que o depurador do Visual Studio interprete o tipo como uma matriz e exiba seus elementos individuais. A visualização `std::vector` é um bom exemplo:  
  
```xml
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  
  
 Um `std::vector` mostra os elementos individuais quando expandido na janela variável:  
  
 ![std:: Vector usando a expansão de ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  
  
 No mínimo, o nó `ArrayItems` deve ter:  
  
1.  Uma expressão `Size` (que deve ser avaliada como um inteiro) para que o depurador entenda o comprimento da matriz  
  
2.  Uma expressão `ValuePointer` que deve apontar para o primeiro elemento (que deve ser um ponteiro de um tipo de elemento que não seja `void*`).  
  
 O valor padrão para o limite inferior de matriz é 0. O valor pode ser substituído usando um elemento `LowerBound` (exemplos podem ser encontrados nos arquivos .natvis que acompanham o Visual Studio).  
  
 Agora você pode usar o `[]` operador com um `ArrayItems` expansão, por exemplo `vector[i]`. O operador [] pode ser usado com qualquer visualização de uma matriz unidimensional que usa `ArrayItems` ou `IndexListItems`, mesmo que o próprio tipo não permite esse operador (por exemplo `CATLArray`).  
  
 Matrizes de várias dimensões também podem ser especificadas. O depurador precisa de apenas um pouco mais informações para exibir corretamente os elementos filho nesse caso:  
  
```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  
  
 `Direction` especifica se a matriz é de linhas principais ou de colunas principais. `Rank` especifica a classificação da matriz. O `Size` elemento aceita o implícita `$i` parâmetro, que substitui com o índice de dimensão para encontrar o comprimento da matriz dessa dimensão. Por exemplo, no exemplo anterior, a expressão `_M_extent.M_base[0]` deve fornecer o comprimento da dimensão 0, `_M_extent._M_base[1]` da primeira e sucessivamente.  
  
 Aqui está como um bidimensional `Concurrency::array` objeto examina o depurador:  
  
 ![Uma matriz bidimensional com expansão ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  
  
####  <a name="BKMK_IndexListItems_expansion"></a>Expansão de IndexListItems  
 Você pode usar o `ArrayItems` expansão, somente se os elementos da matriz são dispostos de forma contígua na memória. O depurador chega ao elemento seguinte incrementando o elemento atual com o ponteiro. Para dar suporte aos casos nos quais você precisa manipular o índice do nó de valor, os nós `IndexListItems` podem ser usados. Aqui está uma visualização usando `IndexListItems` nó:  
  
```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  
```  
  
 Agora você pode usar o `[]` operador com um `IndexListItems` expansão, por exemplo `vector[i]`. O `[]` operador pode ser usado com qualquer visualização de uma matriz unidimensional que usa `ArrayItems` ou `IndexListItems`, mesmo que o próprio tipo não permite esse operador (por exemplo `CATLArray`).  
  
 A única diferença entre `ArrayItems` e `IndexListItems` é que o `ValueNode` espera que a expressão completa para o i<sup>th</sup> elemento com o implícita `$i` parâmetro.  
  
####  <a name="BKMK_LinkedListItems_expansion"></a>Expansão de LinkedListItems  
 Se o tipo visualizado representa uma lista vinculada, o depurador pode exibir seus filhos usando um nó `LinkedListItems`. Aqui está a visualização de `CAtlList` tipo usando esse recurso:  
  
```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  
```  
  
 O elemento `Size` faz referência ao comprimento da lista. `HeadPointer` aponta para o primeiro elemento, `NextPointer` refere-se ao próximo elemento e `ValueNode` refere-se ao valor do item.  
  
-   As expressões `NextPointer` e `ValueNode` são avaliadas no contexto do elemento do nó da lista vinculada e não do tipo da lista pai. No exemplo anterior, `CAtlList` tem um `CNode` classe (encontrado no `atlcoll.h`) que representa um nó da lista vinculada. `m_pNext` e `m_element` são campos dessa classe `CNode` e não da classe `CAtlList`.  
  
-   O `ValueNode` pode ser deixado em branco ou pode conter `this` para fazer referência ao nó da lista vinculada.  
  
#### <a name="customlistitems-expansion"></a>Expansão de CustomListItems  
 O `CustomListItems` expansão lhe permite escrever lógica personalizada para percorrer uma estrutura de dados como uma tabela de hash. Você deve usar `CustomListItems` para visualizar dados estruturas que tudo o que você precisa avaliar ser expresso através de expressões C++, mas não se ajustam bem a molde para `ArrayItems`, `TreeItems`, ou`LinkedListItems.`  
  
 O visualizador para CAtlMap é um ótimo exemplo de onde `CustomListItems` é apropriado.  
  
```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  
  
        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

Você pode usar `Exec` para executar o código dentro de um `CustomListItems` expansão usando as variáveis e os objetos definidos no `CustomListItems` expansão. Não é possível usar `Exec` para avaliar funções.

Você pode usar os operadores lógicos, operadores aritméticos e operadores de atribuição com `Exec`.

Há suporte para as seguintes funções intrínsecas:

- `strlen, wcslen, strnlen, wcsnlen, strcmp, wcscmp, _stricmp, _strcmpi, _wcsicmp, strncmp, wcsncmp, _strnicmp, _wcsnicmp, memcmp, memicmp, wmemcmp, strchr, wcschr, memchr, wmemchr, strstr, wcsstr, __log2, __findNonNull`
- `GetLastError, TlsGetValue, DecodeHString, WindowsGetStringLen, WindowsGetStringRawBuffer, WindowsCompareStringOrdinal, RoInspectCapturedStackBackTrace, CoDecodeProxy, GetEnvBlockLength, DecodeWinRTRestrictedException, DynamicMemberLookup, DecodePointer, DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`
  
####  <a name="BKMK_TreeItems_expansion"></a>Expansão de TreeItems  
 Se o tipo visualizado representa uma árvore, o depurador pode percorrer a árvore e exibir seus filhos usando um nó `TreeItems`. Aqui está a visualização de `std::map` tipo usando esse recurso:  
  
```xml
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  
```  
  
 A sintaxe é semelhante do `LinkedListItems` nó. `LeftPointer`, `RightPointer` e `ValueNode` são avaliados no contexto da classe de nó de árvore e `ValueNode` pode ser deixado vazio ou ter `this` para fazer referência ao nó da árvore.  
  
####  <a name="BKMK_ExpandedItem_expansion"></a>Expansão de ExpandedItem  
 O elemento `ExpandedItem` pode ser usado para gerar uma exibição filho agregada exibindo propriedades de classes base ou de membros de dados como se fossem filhos do tipo visualizado. A expressão especificada é avaliada e os nós filhos do resultado são acrescentados à lista filho do tipo visualizado. Por exemplo, suponha que temos um tipo de ponteiro inteligente `auto_ptr<vector<int>>`, que normalmente exibe como:  
  
 ![Auto &#95; ptr &#60; vetor &#60; int &#62; &#62; expansão padrão](../debugger/media/dbg_natvis_expand_expandeditem_default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  
  
 Para ver os valores do vetor, faça uma pesquisa detalhada de dois níveis na janela variável que passa pelo membro _Myptr. Adicionando um elemento `ExpandedItem`, você pode eliminar a variável `_Myptr` da hierarquia e exibir diretamente o vetor elements::  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 ![Auto &#95; ptr &#60; vetor &#60; int &#62; &#62; Expansão de ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  
  
 O exemplo a seguir mostra como agregar as propriedades da classe base em uma classe derivada. Suponha que a classe `CPanel` seja derivada de `CFrameworkElement`. Em vez de repetir as propriedades provenientes da classe base `CFrameworkElement`, o nó `ExpandedItem` permite que essas propriedades sejam acrescentadas à lista filho da classe `CPanel`. O **nd** especificador de formato, o que desativa a visualização de correspondência para a classe derivada, é necessário aqui. Caso contrário, a expressão `*(CFrameworkElement*)this` faz com que o `CPanel` visualização a ser aplicada novamente porque regras de correspondência de tipo de visualização padrão considerá-la mais adequado. Usando o **nd** especificador de formato instrui o depurador a usar a visualização de classe base ou a expansão da classe base padrão se a classe base não tem uma visualização.  
  
```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
####  <a name="BKMK_Synthetic_Item_expansion"></a>Expansão de Item sintético  
 Enquanto o elemento `ExpandedItem` fornece uma exibição de dados mais simples eliminando as hierarquias, o nó `Synthetic` faz o oposto. Ele permite que você crie um elemento filho artificial (ou seja, um elemento filho não é um resultado de uma expressão). Esse elemento filho pode conter seus próprios elementos filhos. No exemplo a seguir, a visualização do tipo `Concurrency::array` usa um nó de `Synthetic` para mostrar uma mensagem de diagnóstico para o usuário:  
  
```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  
  
```  
  
 ![Concurrency com expansão de elemento sintético](../debugger/media/dbg_natvis_expand_synthetic.png "DBG_NATVIS_Expand_Synthetic")  
  
###  <a name="BKMK_HResult"></a>HResult  
 O elemento `HResult` permite que você personalize as informações que são exibidas para um HRESULT em janelas do depurador. O elemento `HRValue` deve conter o valor de 32 bits do HRESULT que deve ser personalizado. O elemento `HRDescription` contém as informações que são exibidas no depurador.  
  
```  
  
<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  
  
###  <a name="BKMK_UIVisualizer"></a>UIVisualizer  
 Um elemento `UIVisualizer` registra um plug-in de visualizador gráfico no depurador. Um plug-in de visualizador gráfico cria uma caixa de diálogo ou outra interface para exibir uma variável ou um objeto de maneira apropriada para o tipo de dados. O Visualizador de plug-in deve ser criado como um [VSPackage](../extensibility/internals/vspackages.md) e precisa expor um serviço que pode ser consumido pelo depurador. O arquivo .natvis contém informações de registro para o plug-in, como o nome, a GUID do serviço exposto e também os tipos que ele pode visualizar.  
  
 Veja um exemplo de um elemento UIVisualizer:  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  
  
 Um `UIVisualizer` é identificado por um `ServiceId`  -  `Id` par de atributo. `ServiceId` é a GUID do serviço exposto pelo pacote do visualizador, `Id` é um identificador exclusivo que pode ser usado para diferenciar visualizadores se um serviço fornecer mais de um visualizador. No exemplo anterior, o mesmo serviço de visualizador fornece dois visualizadores.  
  
 O atributo `MenuName` é o que os usuários veem como sendo o nome do visualizador quando abrem o menu suspenso ao lado do ícone de lupa nas janelas variáveis do depurador, por exemplo:  
  
 ![Menu de atalho do menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  
  
 Cada tipo definido no arquivo .natvis deve listar explicitamente os visualizadores de interface de usuário que podem exibi-los. O depurador corresponde as referências do visualizador nas entradas de tipo para corresponder os tipos aos visualizadores registrados. Por exemplo, o seguinte tipo de entrada para `std::vector` faz referência a UIVisualizer em nosso exemplo anterior.  
  
```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  
  
 Você pode ver um exemplo de UIVisualizer na extensão de inspeção de imagem usado para exibir os bitmaps de memória: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  
  
### <a name="customvisualizer-element"></a>Elemento CustomVisualizer  
 `CustomVisualizer`é um ponto de extensibilidade que especifica uma extensão do VSIX que você pode escrever para controlar a visualização de código que é executado no Visual Studio. Para obter mais informações sobre como escrever extensões VSIX, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md). Escrevendo um visualizador personalizado é muito mais trabalho do que escrever uma definição de natvis XML, mas você é livre de restrições sobre quais natvis dá suporte ou não dá suporte. Os visualizadores personalizados têm acesso ao conjunto completo de APIs, que pode ser usado para consultar e modificar o processo de depuração ou se comunicar com outras partes do Visual Studio de extensibilidade do depurador.  
  
 Você pode usar o `Condition`, `IncludeView`, e `ExcludeView` atributos em elementos de CustomVisualizer.