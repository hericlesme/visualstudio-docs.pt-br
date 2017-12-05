---
title: "Criar configurações do editor portátil e personalizado com o EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1df6f8e34d2b8e72486dd804ba57f0dcf2406b
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Criar configurações do editor portátil e personalizado com o EditorConfig
As configurações do editor de texto no Visual Studio são aplicáveis a todos os projetos de um tipo determinado. Dessa forma, por exemplo, se você alterar uma configuração do editor de texto do C#, essa configuração se aplicará a *todos* os projetos do C# no Visual Studio. No entanto, em alguns casos, convém usar convenções que diferem das suas próprias preferências pessoais do editor. Os arquivos [EditorConfig](http://editorconfig.org/) permitem fazer isso fornecendo texto opções comuns do editor de texto por projeto. As configurações do EditorConfig, contidas em um arquivo .editorconfig adicionado à sua base de código, substituem as configurações globais do editor de texto do Visual Studio. Isso significa que você poderá personalizar cada base de código para usar as configurações de editor de texto que você preferir. Não é necessário nenhum plug-in para usar essa funcionalidade no Visual Studio.

## <a name="coding-consistency"></a>Consistência de codificação
As configurações em arquivos EditorConfig permitem manter configurações e estilos de codificação consistentes para uma linguagem, como estilo de recuo, largura de tabulação, caracteres de fim de linha, codificação e mais, em uma base de código independentemente do editor ou IDE usado. Por exemplo, ao codificar em C#, se sua base de código tem uma convenção de preferir que os recuos sempre sejam compostos por cinco caracteres de espaço, que os documentos usem codificação UTF-8 e que cada linha sempre termine com uma CR/LF, é possível configurar um arquivo .editorconfig para fazer isso.

As convenções de codificação usadas em seus projetos pessoais podem ser diferentes das usadas nos projetos da sua equipe. Por exemplo, talvez você prefira apertar a tecla Tab para adicionar um caractere de tabulação enquanto você estiver codificando. No entanto, sua equipe pode preferir que o recuo adicione quatro caracteres de espaço em vez de um caractere de tabulação. Os arquivos EditorConfig resolvem esse problema permitindo que você tenha uma configuração para cada cenário.

Como as configurações estão contidas em um arquivo na base de código, elas viajam juntamente com essa base de código. Contanto que você abra o arquivo de código em um editor em conformidade com o EditorConfig, as configurações do editor de texto são implementadas. Para obter mais informações sobre arquivos EditorConfig, consulte o site [EditorConfig.org](http://editorconfig.org/).

## <a name="override-editorconfig-settings"></a>Substituir as configurações do EditorConfig
Quando você adiciona um arquivo .editorconfig a uma pasta em sua hierarquia de arquivos, as configurações se aplicam a todos os arquivos aplicáveis no nível e abaixo. Para substituir as configurações do EditorConfig de um projeto ou base de código específico, de modo que ele use convenções diferentes do arquivo de nível superior .editorconfig, basta adicionar um arquivo .editorconfig à raiz do diretório do projeto ou repositório da sua base de código. Certifique-se de colocar a propriedade ```root=true``` no arquivo para que o Visual Studio não procure outros arquivos .editorconfig além da estrutura de diretório. As novas configurações do arquivo .editorconfig serão aplicáveis ao nível no qual ele está localizado e aos arquivos nos subdiretórios.

```
# top-most EditorConfig file
root = true
```

![Hierarquia do EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Os arquivos do EditorConfig são lidos de cima para baixo e os arquivos do EditorConfig mais próximos são lidos por último. As convenções de seções do EditorConfig correspondentes são aplicadas na ordem em que foram lidas, portanto as convenções dos arquivos mais próximos têm precedência.

## <a name="supported-settings"></a>Configurações com suporte
O editor do Visual Studio é compatível com o seguinte, do conjunto principal de [propriedades do EditorConfig](http://editorconfig.org/#supported-properties):  

- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- raiz

Além disso, ele é compatível com as [convenções de estilo de código do .NET](../ide/editorconfig-code-style-settings-reference.md).  

Há suporte para as configurações do EditorConfig em todas as linguagens às que o Visual Studio dá suporte, exceto para XML.

## <a name="intellisense"></a>IntelliSense
O Visual Studio oferece IntelliSense limitado para a edição de arquivos .editorconfig. Se você editar muitos arquivos .editorconfig, talvez você ache a extensão [Serviço de linguagem do EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) útil.

## <a name="example"></a>Exemplo
Aqui está um exemplo que mostra o estado de recuo de um trecho de código C# antes e depois de adicionar um arquivo .editorconfig ao projeto. A configuração **Tabulações**, na caixa de diálogo **Opções** do editor de texto do Visual Studio, foi definida para produzir caracteres de espaço quando você pressiona a tecla **TAB** em seu código.

![Configuração de tabulação do Editor de texto](../ide/media/vside_editorconfig_tabsetting.png)

Conforme esperado, pressionar a tecla **TAB** na próxima linha faz a linha recuar por meio da adição de quatro caracteres de espaço em branco.

![Codificar antes de usar o EditorConfig](../ide/media/vside_editorconfig_before.png)

Adicionaremos um novo arquivo chamado .editorconfig ao projeto, com o seguinte conteúdo. A configuração `[*.cs]` significa que essa alteração será aplicada somente a arquivos .cs neste projeto.  

![Arquivo .editorconfig adicionado ao projeto](../ide/media/vside_editorconfig_addconfig.png)

Agora, ao pressionar a tecla **TAB**, você obtém caracteres de tabulação em vez de espaços.

![TAB adiciona um caractere de tabulação](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Adicionar um arquivo .editorconfig ao seu projeto ou base de código não converterá os estilos existentes em novos; isso se aplicará somente a linhas recém-adicionadas. Se você remover um arquivo .editorconfig do seu projeto ou de sua base de código, será necessário recarregar os arquivos de código para que as configurações do editor sejam revertidas para configurações globais. Os erros em arquivos .editorconfig são informados na janela Lista de Erros no Visual Studio.

## <a name="troubleshooting-editorconfig-settings"></a>Solução de problemas de configurações do EditorConfig
Se houver um arquivo do EditorConfig no local do seu projeto ou acima desse local, na estrutura do diretório, o Visual Studio aplicará as configurações do editor nesse arquivo para o seu editor. Nesse caso, você verá a seguinte mensagem na barra de status:

**"As preferências do usuário para esse tipo de arquivo foram substituídas pelas convenções de codificação desse projeto."**

Isso significa que, se as configurações do editor em **Ferramentas**, **Opções**, **Editor de Texto** (como o tamanho do recuo, tamanho da tabulação, estilo de recuo &mdash; tabulações ou espaços ou convenções de codificação como o uso de `var`) estiverem especificadas em um arquivo de EditorConfig no projeto ou acima dele na estrutura de diretório, as convenções no arquivo EditorConfig substituirão as configurações das Opções. Você pode controlar esse comportamento ativando/desativando a opção **Seguir as convenções de codificação do projeto** em **Ferramentas**, **Opções**, **Editor de Texto**. Desmarcar a opção desliga o suporte do Visual Studio ao EditorConfig.

![Opções de ferramentas – seguir as convenções de codificação do projeto](media/coding_conventions_option.png)

Você pode encontrar arquivos .editorconfig em diretórios pai ao abrir um prompt de comando e executar o seguinte comando na raiz do disco que contém seu projeto:

```
dir .editorconfig /s
```

Você pode controlar o escopo das convenções do EditorConfig configurando a propriedade ```root=true``` no arquivo .editorconfig na raiz do seu repositório ou no diretório em que o projeto reside. O Visual Studio procurará um arquivo chamado .editorconfig no diretório do arquivo aberto e em todos os diretórios pai. O Visual Studio interromperá a pesquisa se o caminho raiz do arquivo for alcançado ou se um arquivo .editorconfig com ```root=true``` for encontrado.

## <a name="support-editorconfig-for-your-language-service"></a>Dar suporte ao EditorConfig para o serviço de linguagem
Na maioria dos casos, ao implementar um serviço de linguagem do Visual Studio, nenhum trabalho adicional é necessário para dar suporte às propriedades universais do EditorConfig. O editor básico detecta automaticamente e lê o arquivo .editorconfig quando os usuários abrem arquivos e define as opções de buffer e exibição de texto apropriadas. No entanto, alguns serviços de linguagem optam por usar uma opção de exibição de texto contextual apropriada, em vez de usar configurações globais para itens como tabulações e espaços quando um usuário edita ou formata um texto. Nesses casos, o serviço de linguagem deve ser atualizado para dar suporte aos arquivos do EditorConfig.

A seguir estão as alterações necessárias para atualizar um serviço de linguagem para dar suporte a arquivos de EditorConfig, através da substituição de uma opção global _específica a um idioma_ por uma opção _contextual_:  

### <a name="indent-style"></a>Estilo de recuo
Substituir:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs  
_or_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs  

Por:  

!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  
_or_  
!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  

### <a name="indent-size"></a>Tamanho do recuo
Substituir:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize  
_or_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize  

Por:  

textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)  
_or_  
textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)  

### <a name="tab-size"></a>A guia tamanho
Substituir:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize  
_or_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize  

Por:  

textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)  
_or_  
textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)  

## <a name="see-also"></a>Consulte também
[Convenções de estilo de código do .NET](../ide/editorconfig-code-style-settings-reference.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Escrevendo código no editor](writing-code-in-the-code-and-text-editor.md)