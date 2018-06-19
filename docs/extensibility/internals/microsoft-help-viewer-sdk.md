---
title: SDK do Microsoft Help Viewer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ddc23ab56df017ef0a37c56cd5b0a81ee33a07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135401"
---
# <a name="microsoft-help-viewer-sdk"></a>SDK do Microsoft Help Viewer
Este artigo contém as seguintes tarefas para integradores de Visual Studio Help Viewer:  
  
-   Criar um tópico (F1 suporte)  
  
-   Criando um pacote de conteúdo de marca do Visualizador da Ajuda  
  
-   Implantando um conjunto de artigos  
  
-   Adicionando Ajuda para o shell do Visual Studio (integrado ou isolado)  
  
-   Recursos adicionais  
  
### <a name="creating-a-topic-f1-support"></a>Criar um tópico (F1 suporte)  
Esta seção fornece uma visão geral dos componentes de um tópico apresentado, requisitos de tópico, uma breve descrição de como criar um tópico (incluindo os requisitos de suporte F1) e, finalmente, um tópico de exemplo com o resultado renderizado.  
  
**Visão geral de tópico do Visualizador da Ajuda**  
  
Quando um tópico é chamado para processamento, o Visualizador da Ajuda obtém os elementos de pacote de identidade visual que estão associados com o tópico no momento da instalação ou a última atualização, junto com o tópico XHTML e combina os dois para resultar na exibição de conteúdo apresentada (marca dados + dados de tópico).  O pacote de marcas contém logotipos, suporte a comportamentos de conteúdo e texto marca (direitos autoral, etc.).  Consulte "Criar pacote de marca" abaixo para obter mais informações sobre os elementos de pacote de identidade visual.  No caso de não há nenhum pacote de marcas associado ao tópico, o Visualizador da Ajuda usará o pacote de marcas fallback localizado na raiz do aplicativo Visualizador da Ajuda (Branding_en US.mshc).  
  
**Requisitos de tópico do Visualizador de ajuda**  
  
Para ser processado corretamente pelo Visualizador da Ajuda, o conteúdo do tópico bruto deve ser W3C básica 1.1 XHTML.  
  
Normalmente, um tópico contém duas seções:  
  
-   Metadados (consulte a referência de metadados de conteúdo): pai dos dados sobre o tópico, por exemplo, a ID exclusiva do tópico, o valor de palavra-chave, o tópico de ID de índice, ID de nó, etc.  
  
-   Conteúdo do corpo: compatível com W3C básica 1.1 XHTML que inclui suporte para conteúdo comportamentos (área recolhível, trecho de código, etc. Uma lista completa é mostrada abaixo).  
  
Pacote de identidade visual do Visual Studio com suporte a controles:  
  
-   Links  
  
-   Trecho de código  
  
-   CollapsibleArea  
  
-   Membro herdado  
  
-   LanguageSpecificText  
  
Suporte para cadeias de caracteres do idioma (não entre maiusculas e minúsculas):  
  
-   JavaScript  
  
-   CSharp ou c#  
  
-   cplusplus ou visualc + + ou c + +  
  
-   JScript  
  
-   VisualBasic ou vb  
  
-   f # ou fsharp ou fs  
  
-   outros - uma cadeia de caracteres que representa um nome de idioma  
  
**Criar um tópico do Visualizador da Ajuda**  
  
Criar um novo documento XHTML denominado ContosoTopic4.htm e incluir a marca de título (abaixo).  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
Em seguida, adicione dados para definir como o tópico é para ser apresentado (self marca ou não), como fazer referência a este tópico para F1, onde este tópico se encontra o Sumário, sua ID (para referência de link por outros tópicos), etc.  Consulte a tabela "Metadados de conteúdo" abaixo para obter uma lista completa de metadados com suporte.  
  
-   Nesse caso, usaremos nosso próprio pacote de marcas, uma variante do pacote de identidade visual do Visual Studio Help Viewer.  
  
-   Adicione o nome de metadados de F1 e valor (conteúdo de "Microsoft.Help.F1" = "ContosoTopic4") que corresponderá o valor fornecido de F1 no recipiente de propriedades do IDE.  (Consulte a seção de suporte de F1 para obter mais informações).   Esse é o valor que está de acordo com o F1 chamar de dentro do IDE para exibir este tópico quando F1 é escolhido no IDE.  
  
-   Adicione a ID de tópico. Isso é a cadeia de caracteres que é usada por outros tópicos para vincular a este tópico.  É a identificação de Visualizador de ajuda para este tópico.  
  
-   Para o Sumário, adicione nó do pai deste tópico para definir onde este nó de Sumário do tópico será exibido.  
  
-   Para o Sumário, adicione a ordem de nó deste tópico. Quando o nó pai possui n número de nós filhos, defina na ordem de nós filho local deste tópico. Por exemplo, este tópico é o número 4 de 4 tópicos de filho.)  
  
Seção de metadados de exemplo:  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
<meta name="SelfBranded" content="false" />     
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
**O corpo do tópico**  
  
O corpo do tópico (não incluindo o cabeçalho e rodapé) conterá links da página, uma seção de observação, uma área recolhível, um trecho de código e uma seção de texto específicos do idioma.  Consulte a seção de identidade visual para obter informações sobre as áreas do tópico apresentada.  
  
1.  Adicione uma marca de título do tópico:  `<div class="title">Contoso Topic 4</div>`  
  
2.  Adicione uma seção de Observação: `<div class="alert"> add your table tag and text </div>`  
  
3.  Adicione uma área recolhível:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Adicione um trecho de código:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Adicionar texto específico do idioma de código: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Observe que devLangnu = permite que você insira outros idiomas. Por exemplo, devLangnu = "Fortran" exibirá Fortran quando o trecho de código DisplayLanguage = Fortran  
  
6.  Adicione links de página: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Observação: para sem suporte novo "idioma de exibição" (exemplo, F #, Cobol, Fortran) colorização de código no trecho de código será monocromática.  
  
**Tópico Visualizador da Ajuda do exemplo** de código mostra como definir metadados, um trecho de código, uma área recolhível e texto específico do idioma.  
  
```html
<?xml version="1.0" encoding="utf-8"?>  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
<meta name="SelfBranded" content="false" />     
</head>  
  
<body>  
<div class="title">Contoso Topic 4</div>  
  
  <div id="header">  
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">  
        <tr id="headerTableRow2"><td align="left">  
            <span id="nsrTitle">Contoso Topic 1</span>  
          </td>  
<td align="right">  
</td></tr>  
<tr id="headerTableRow1"><td align="left">  
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>  
          </td></tr>  
      </table>  
</div>  
  
<h2>Table of Contents</h2>  
  
<ul class="toc">  
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>  
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>  
</ul>  
  
<div class="topic">  
  
<div id="mainSection">  
<div id="mainBody">  
  
<a name="introduction"></a>  
<h2>1.0 Introduction</h2>  
<p>[This documentation is for sample purposes only.]</p>  
  
<p>Contoso Topic 1 contains examples of:  
<ul>  
<li>Collapsible Area</li>  
<li>Bookmark ("See also")</li>  
<li>Code Snippets from Branding Package</li>  
</ul>  
 </p>  
<div class="alert"><table><tr><th>  
<strong>Note </strong></th></tr>  
<tr><td>  
<p>This is an example of a <span class="label">Note </span>section.    
Call out important items for your reader in this <span class="label">Note </span>box.  
</p></td></tr>  
</table>  
</div>  
</div>  
  
<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">  
  
            <a id="sectionToggle0"><!----></a>  
  
<div>  
Example of Collapsible Area  
<br/>  
Lorem ipsum dolor sit amet...  
</div>  
</CollapsibleArea>  
  
<div id="snippetGroup" >  
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >  
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip  
Dim messageBoxVB as New System.Text.StringBuilder()  
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)  
    messageBoxVB.AppendLine()  
 ...  
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")  
End Sub  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >  
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)   
{   
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();  
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );  
messageBoxCS.AppendLine();  
...  
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );  
}  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >  
some F# code  
</CodeSnippet>  
</div>  
  
<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />  
  
<a name="seealso"></a>  
<h1 class="heading">See Also</h1>  
  
    <div id="seeAlsoSection" class="section">   
    <div class="seeAlsoStyle">  
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Suporte de F1**  
  
No Visual Studio, selecionar F1 gera valores fornecidos do posicionamento do cursor dentro do IDE e preenche um "conjunto de propriedades" com os valores fornecidos (com base no local do cursor. Quando o cursor está sobre o recurso de x, o recurso x é ativa/em foco e preenche o recipiente de propriedades com valores.  Quando F1 é selecionado o recipiente de propriedades é preenchido e código de F1 do Visual Studio verifica se a fonte de ajuda os clientes padrão é local ou online (on-line é o padrão), em seguida, cria a cadeia de caracteres apropriada com base em usuários de configuração (online é o padrão) - execução do shell (consulte o guia de administrador ajuda para exe iniciar parâmetros) com parâmetros para o Visualizador da Ajuda local + palavras-chave do conjunto de propriedades se ajuda local é o padrão ou a URL do MSDN com a palavra-chave na lista de parâmetros.  
  
Se três cadeias de caracteres são retornadas para F1, conhecido para como uma cadeia de caracteres de vários valores, levar o primeiro termo, procure ocorrência, e se encontrado, podemos terminar; Caso contrário, vá para a próxima cadeia de caracteres.  Ordem é importante. Apresentação de múltiplos valores palavras-chave deve ser a cadeia de caracteres mais longa em cadeia de caracteres mais curta.  Para verificar isso no caso de palavras-chave de vários valores, examine a cadeia de caracteres de URL F1 online, que inclui a palavra-chave escolhida.  
  
No Visual Studio 2012, intencionalmente fizemos uma divisão mais forte entre online e offline, para que se a configuração do usuário para Online, em seguida, simplesmente passamos a solicitação F1 diretamente ao nosso serviço de consulta online no MSDN em vez de roteamento com o agente da biblioteca de ajuda que tivemos no Visual Studio 2010. Em seguida, contamos com um estado de "conteúdo do fornecedor instalado = true" para determinar se deve fazer algo diferente nesse contexto. Se verdadeiro, em seguida, realizamos essa lógica de roteamento e análise dependendo do que você deseja dar suporte para seus clientes. Se false, vamos apenas vá para MSDN. Se a configuração do usuário for Local, basta ir todas as chamadas para o mecanismo de ajuda local.  
  
F1 diagrama de fluxo:  
  
![Fluxo de F1](../../extensibility/internals/media/f1flow.png "F1flow")  
  
Quando a fonte de conteúdo de Ajuda do Visualizador da Ajuda padrão é definida como on-line (Iniciar no navegador):  
  
-   Os recursos do Visual Studio parceiro (VSP) emitir um valor para o recipiente de propriedades F1 (propriedade recipiente prefix.keyword e URL online para o prefixo encontrado no registro): F1 envia uma URL de VSP + parâmetros para o navegador.  
  
-   Recursos do Visual Studio (editor de idiomas, itens de menu específicos do Visual Studio, etc.): F1 envia uma URL do Visual Studio para o navegador.  
  
Quando a fonte de conteúdo de Ajuda do Visualizador da Ajuda padrão é definida como a Ajuda local (Iniciar no Visualizador da Ajuda):  
  
-   Recursos VSP onde a palavra-chave correspondem entre o recipiente de propriedades de F1 e o índice de repositório local (ou seja, o prefix.keyword de recipiente da propriedade = o valor encontrado no índice de repositório local): o tópico no Visualizador da Ajuda F1 é renderizado.  
  
-   Recursos do Visual Studio (nenhuma opção para VSP substituir o recipiente de propriedades emitido a partir de recursos do Visual Studio): F1 renderiza um tópico do Visual Studio no Visualizador da Ajuda.  
  
Defina os seguintes valores de registro para habilitar F1 Fallback para conteúdo de Ajuda do fornecedor. F1 Fallback significa que o Visualizador da Ajuda é definido para procurar conteúdo de ajuda de F1 online e o conteúdo do fornecedor é instalado localmente no disco rígido dos usuários. O Visualizador da Ajuda deve examinar a Ajuda local para o conteúdo, embora a configuração padrão para obter ajuda online.  
  
1.  Definir o **VendorContent** valor na chave do registro ajuda 2.3:  
  
    -   Para sistemas operacionais de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = DWORD: 00000001  
  
    -   Para sistemas operacionais de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = DWORD: 00000001  
  
2.  Registre o namespace de parceiro na chave do registro ajuda 2.3:  
  
    -   Para sistemas operacionais de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< namespace\>*  
  
         "local"="offline"  
  
    -   Para sistemas operacionais de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< namespace\>*  
  
         "local"="offline"  
  
**Análise de Namespace nativo de base**  
  
Para ativar a análise de um namespace base nativo, no registro adicione um novo DWORD pelo nome do: BaseNativeNamespaces e defina seu valor como 1 (sob a chave de catálogo que quiserem suporte).  Por exemplo, se você quiser usar o catálogo do Visual Studio, você poderia adicionar a chave para o caminho:  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
Quando uma palavra-chave F1 no formato de QUE CABEÇALHO/método for encontrado, o caractere '/' será analisado, resultando em construção:  
  
-   CABEÇALHO: será o namespace que pode ser usado para registrar no registro  
  
-   MÉTODO: Isso tornará a palavra-chave que é passada.  
  
Por exemplo, dada uma biblioteca personalizada chamada CustomLibrary e um método chamado MyTestMethod, quando uma solicitação chega de F1 será formatada como `CustomLibrary/MyTestMethod`.  
  
Um usuário pode, em seguida, registrar CustomLibrary como o namespace sob a seção de parceiros e fornecer qualquer chave local desejem, e a palavra-chave passada para a consulta será MyTestMethod.  
  
**Habilitar depuração de ferramenta no IDE de ajuda**  
  
Adicione a seguinte chave do registro e o valor:  
  
Tecla de Ajuda do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic: saída de depuração de exibição no valor comercial: Sim  
  
No IDE, sob o item de menu Ajuda, selecione "Depurar contexto de Ajuda"  
  
**Metadados de conteúdo**  
  
A tabela a seguir, qualquer cadeia de caracteres que aparece entre colchetes é um espaço reservado que deve ser substituído por um valor reconhecido. Por exemplo, em \<name="Microsoft.Help.Locale meta" conteúdo = "[código de idioma]" / >, "[código de idioma]" deve ser substituído por um valor como "en-us".  
  
|Propriedade (representação de HTML)|Descrição|  
|--------------------------------------|-----------------|  
|\< conteúdo de meta name="Microsoft.Help.Locale" = "[código do idioma]" / >|Define uma localidade deste tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez e deve ser inserido acima quaisquer outras marcas do Microsoft Help. Se essa marca não for usada, o texto do corpo do tópico é indexado, usando o separador de palavras que está associado com a localidade do produto, se for especificado; Caso contrário, o en-us é usado o separador de palavras. Essa marca está em conformidade com ISOC RFC 4646. Para garantir que o Microsoft Help funciona corretamente, use essa propriedade em vez do atributo de idioma de general.|  
|\< conteúdo de meta name="Microsoft.Help.TopicLocale" = "[código do idioma]" / >|Define uma localidade para este tópico quando outras localidades também são usadas. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Use essa marca quando o catálogo contém conteúdo em mais de um idioma. Vários tópicos em um catálogo podem ter a mesma ID, mas cada uma deve especificar um TopicLocale exclusivo. O tópico que especifica um TopicLocale que corresponde à localidade do catálogo é o tópico que é exibido no sumário. No entanto, todas as versões de idioma do tópico são exibidas nos resultados da pesquisa.|  
|\< título > [Title] \< /title >|Especifica o título deste tópico. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. Se o corpo do tópico não contém um título \<div > seção, o título é exibida no tópico e no sumário.|  
|\< nome da meta = "Microsoft.Help.Keywords" conteúdo = "[aKeywordPhrase]" / >|Especifica o texto de um link que é exibido no painel de índice do Visualizador da Ajuda. Quando o link é clicado, o tópico é exibido. Você pode especificar várias palavras-chave de índice para um tópico, ou você pode omitir essa marca se não quiser links deste tópico para aparecer no índice. Palavras-chave "K" de versões anteriores da Ajuda podem ser convertidas para essa propriedade.|  
|\< conteúdo de meta name="Microsoft.Help.Id" = "[TopicID]" / >|Define o identificador para este tópico. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. A ID deve ser exclusiva entre os tópicos no catálogo que tenham a mesma configuração de localidade. Em outro tópico, você pode criar um link para este tópico usando essa ID.|  
|\< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Especifica a palavra-chave F1 neste tópico. Você pode especificar várias palavras-chave F1 para um tópico, ou você pode omitir essa marca se você não quiser que este tópico a ser exibido quando um usuário de aplicativo pressiona F1. Normalmente, apenas uma palavra-chave de F1 é especificada para um tópico. Palavras-chave "F" de versões anteriores da Ajuda podem ser convertidas para essa propriedade.|  
|\< nome da meta = "Descrição" content = "[Descrição do tópico]" / >|Fornece um breve resumo do conteúdo neste tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Essa propriedade é acessada diretamente pela biblioteca de consulta; não são armazenadas no arquivo de índice.|  
 conteúdo de meta name="Microsoft.Help.TocParent" = "[parent_Id]" / >|Especifica o tópico pai deste tópico no sumário. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. O valor é o Microsoft.Help.Id do pai. Um tópico pode ter apenas um local na tabela de conteúdo. "-1" é considerado o ID de tópico para a raiz de Sumário. Em [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], que a página é a home page do Visualizador da Ajuda. Este é o mesmo motivo que especificamente adicionamos TocParent =-1 para alguns tópicos para garantir que eles aparecem na parte superior níveis. A home page do Visualizador da Ajuda é uma página do sistema e portanto não podem ser substituídas. Se um VSP tenta adicionar uma página com uma ID de -1, ele pode obter adicionado ao conjunto de conteúdo, mas o Visualizador da Ajuda sempre usará a página do sistema - home page Visualizador da Ajuda|  
|\< conteúdo de meta name="Microsoft.Help.TocOrder" = "[inteiro positivo]" / >|Especifica onde este tópico no sumário aparece em relação a seus tópicos de ponto a ponto. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. O valor é um inteiro. Um tópico que especifica um inteiro menor valor aparece acima de um tópico que especifica um número inteiro de valor mais alto.|  
|\< conteúdo de meta name="Microsoft.Help.Product" = "[product code]" / >|Especifica o produto descrita neste tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Essas informações também podem ser fornecidas como um parâmetro que é passado para o indexador de Ajuda.|  
|\< conteúdo de meta name="Microsoft.Help.ProductVersion" = "[número de versão]" / >|Especifica a versão do produto descrita neste tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Essas informações também podem ser fornecidas como um parâmetro que é passado para o indexador de Ajuda.|  
|\< conteúdo de meta name="Microsoft.Help.Category" = "[string]" / >|Usado por produtos para identificar subseções do conteúdo. Você pode identificar várias subseções para um tópico, ou você pode omitir essa marca se não quiser links para identificar qualquer subseções. Essa marca é usada para armazenar os atributos de TargetOS e TargetFrameworkMoniker quando um tópico é convertido de uma versão anterior da Ajuda. O formato do conteúdo é AttributeName:AttributeValue.|  
|\< conteúdo da meta name="Microsoft.Help.TopicVersion ="[número de versão de tópico]"/ >|Especifica a esta versão do tópico quando existem várias versões de um catálogo. Como Microsoft.Help.Id não é garantido como sendo exclusivo, essa marca é necessária quando há mais de uma versão de um tópico em um catálogo, por exemplo, quando um catálogo contém um tópico para o .NET Framework 3.5 e um tópico para o .NET Framework 4 e têm o mesmo Micro flexível. Ajuda.|  
|\< nome da meta = "SelfBranded" content = "[TRUE ou FALSE]" / >|Especifica se este tópico usa o pacote de marcas de inicialização do Gerenciador de biblioteca de Ajuda ou um pacote de marcas é específico para o tópico. Essa marca deve ser verdadeiro ou falso. Se for TRUE, em seguida, o pacote de marcas para o tópico associado substitui o pacote de marcas é definido quando o Help Library Manager para que o tópico é renderizado conforme o esperado, mesmo se for diferente do processamento de outros tipos de conteúdo é iniciado. Se for FALSE, o tópico atual é renderizado de acordo com o pacote de marcas é definido quando o Help Library Manager é iniciado. Por padrão, o Help Library Manager assume automaticamente marca seja false, a menos que a variável SelfBranded é declarada como TRUE; Portanto, você não precisa declarar \<nome meta = "SelfBranded" content = "FALSE" / >.|  
  
### <a name="creating-a-branding-package"></a>Criando um pacote de marcas  
A versão do Visual Studio inclui um número de diferentes produtos do Visual Studio, incluindo o isolado e shells integrados para parceiros do Visual Studio.  Cada um desses produtos requer um certo grau de conteúdo de ajuda baseados em tópicos de marca exclusivo para o produto, o suporte.  Por exemplo, tópicos de Visual Studio precisam ter uma apresentação de marca consistente, enquanto SQL Studio, que encapsula o Shell ISO, requer seu próprio exclusivo ajuda conteúdo identidade visual de cada tópico.  Um parceiro de Shell integrado pode querer que seus tópicos de ajuda para ser dentro do conteúdo da Ajuda do Visual Studio produto pai enquanto mantém seu próprio tópico identidade visual.  
  
Pacotes de marcação são instalados pelo produto que contém o Visualizador da Ajuda.  Para produtos do Visual Studio:  
  
-   Um pacote de marcas de fallback (Branding_\<localidade >. mshc) está instalado na raiz do aplicativo ajudar Viewer 2.3 (exemplo: C:\Program Files (x86) \Microsoft Help Viewer\v2.3), o pacote de idiomas do Visualizador da Ajuda.  Isso é usado nos casos em que o produto marca o pacote não está instalado (nenhum conteúdo foi instalado) ou em que o pacote de marcas instalado está corrompido.  Observe que os elementos do Visual Studio (logotipo e comentários) são ignorados quando o fallback de raiz do aplicativo pacote de marca é usado.  
  
-   Quando o conteúdo do Visual Studio é instalado do serviço do pacote de conteúdo, um pacote de marcas também está instalado (para o primeiro cenário de instalação de conteúdo de tempo).  Se houver uma atualização para o pacote de marcas, a atualização é instalada quando ocorre a próxima atualização de conteúdo ou a ação de instalação do pacote adicional.  
  
O Visualizador da Ajuda Microsoft oferece suporte a identidade visual de tópicos com base nos metadados do tópico.  
  
-   Em que os metadados de tópico definem própria marca = true, renderizar o tópico como está, não fazer nada (do ponto de vista de marca).  
  
-   Em que os metadados de tópico definem própria marca = false, usar o pacote de marcas associado com valor de metadados de TopicVendor.  
  
-   Conteúdo em que os metadados de tópico definem name="Microsoft.Help.TopicVendor" =\< nome de pacote de identidade visual no fornecedor MSHA >, use o pacote de marcas definido no valor do conteúdo.  
  
-   Observe que, no catálogo do Visual Studio, há um aplicativo de prioridade de pacotes de identidade visual.  Marca primeiro do Visual Studio padrão é aplicada e, em seguida, se definido nos metadados do tópico e compatível com a identidade visual associado do pacote (conforme definido no msha a instalação), o definida pelo fornecedor de identidade visual é aplicado como uma substituição.  
  
Elementos de identidade visual geralmente se encaixam em três categorias principais:  
  
-   Elementos de cabeçalho (os exemplos incluem o link de comentários, o texto de aviso condicional, o logotipo)  
  
-   Conteúdo comportamentos (os exemplos incluem elementos de texto do controle de expandir/recolher e elementos de trecho de código)  
  
-   Elementos de rodapé de página (exemplo Copyright)  
  
Itens considerados como incluem elementos marcados (detalhado nessa especificação):  
  
-   Logotipo do produto/catálogo (exemplo, o Visual Studio)  
  
-   Elementos de email e o link de comentários  
  
-   Texto de aviso  
  
-   Texto de direitos autorais  
  
Arquivos de suporte do pacote de identidade visual do Visual Studio Help Viewer incluem:  
  
-   Elementos gráficos (logotipos, ícones, etc.)  
  
-   Branding.js - suporte comportamentos de conteúdo de arquivos de script  
  
-   Branding.XML - cadeias de caracteres que é usado de forma consistente entre o conteúdo do catálogo.  Observação: para elementos de texto de localização do Visual Studio em branding.xml, incluem _locID = "\<valor exclusivo >"  
  
-   Branding.CSS - definições de estilo para consistência de apresentação  
  
-   Printing.CSS - definições de estilo para apresentação impressa consistente  
  
Conforme observado acima, pacotes de identidade visual são associados ao tópico:  
  
-   Quando SelfBranded = false é definido nos metadados, o tópico herda o catálogo de pacote de marca  
  
-   Ou, quando SelfBranded = false e há é um pacote de marca exclusivo definido no MSHA e disponíveis quando o conteúdo está instalado  
  
Para VSPs Implementando pacotes de identidade visual personalizados (conteúdo VSP, SelfBranded = True), uma maneira para prosseguir é iniciar com o pacote de marcas de fallback (instalado com o Visualizador da Ajuda) e altere o nome do arquivo como apropriado.  O Branding_\<localidade > mshc é um arquivo zip com a extensão de arquivo alterado para. mshc, portanto simplesmente altere a extensão de mshc para. zip e extraia o conteúdo.  Consulte abaixo para elementos do pacote de marca e modifique conforme apropriado (por exemplo, altere o logotipo para o logotipo VSP e a referência para o logotipo no arquivo Branding.xml, atualizar Branding.xml por informações específicas VSP, etc.).  
  
Quando todas as modificações são feitas, crie um arquivo zip que contém os elementos de identidade visual desejados e altere a extensão para. mshc.  
  
Para associar o pacote de identidade visual personalizado, crie o MSHA que contém a referência ao arquivo mshc identidade visual juntamente com o conteúdo mshc (que contém os tópicos).  Consulte abaixo para saber como criar um MSHA básico "MSHA".  
  
O arquivo Branding.xml contém um elemento de lista usado para itens específicos em um tópico de renderização consistente quando o tópico contém \<name="Microsoft.Help.SelfBranded meta" conteúdo = "false" / >.  Lista de elementos no arquivo Branding.xml Visual Studio esteja listada abaixo.  Observe que esta lista se destina a ser usado como um modelo para usuários de Shell ISO, onde eles modificar esses elementos (por exemplo, logotipo, comentários e direitos autorais) para atender às sua próprias necessidades de marca de produto.  
  
Observação: variáveis indicados por "{n}" tem dependências de código: remover ou alterar esses valores serão causar erros e, possivelmente, falha do aplicativo. Identificadores de localização (exemplo _locID="codesnippet.n") são incluídos no pacote do Visual Studio identidade visual.  
  
**Branding.XML**  
  
|||  
|-|-|  
|Recurso:|**CollapsibleArea**|  
|Uso:|Expanda o texto de controle de conteúdo será recolhida|  
|**Elemento**|**Value**|  
|ExpandText|Expandir|  
|CollapseText|Recolher|  
|Recurso:|**Trecho de código**|  
|Uso:|Texto de controle de trecho de código.  Observação: Conteúdo do trecho de código com espaço de "separação não" será alterado para o espaço.|  
|**Elemento**|**Value**|  
|CopyToClipboard|Copiar para a Área de Transferência|  
|ViewColorizedText|Exibição colorida|  
|CombinedVBTabDisplayLanguage|Visual Basic (exemplo)|  
|VBDeclaration|Declaração|  
|VBUsage|Uso|  
|Recurso:|**Comentários, rodapé e logotipo**|  
|Uso:|Forneça um controle de comentários para o cliente fornecer comentários sobre o tópico atual por email.  Texto de direitos autorais para o conteúdo.  Definição de logotipo.|  
|**Elemento**|**Valor (essas cadeias de caracteres podem ser modificadas para atender às necessidades de adoção de conteúdo.)**|  
|Direitos autorais|© 2013 Microsoft Corporation. Todos os direitos reservados.|  
|SendFeedback|\<um href = "{0}" \\{1 \\} > enviar comentários\</a > sobre este tópico à Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|Recurso:|**Isenção de responsabilidade**|  
|Uso:|Um conjunto de casos isenção de responsabilidade específicos para a máquina conteúdo traduzido.|  
|**Elemento**|**Value**|  
|MT_Editable|Este artigo foi traduzido. Se você tiver uma conexão de Internet, selecione "Veja este tópico online" para exibir a página no modo editável junto com o conteúdo original em inglês ao mesmo tempo.|  
|MT_NonEditable|Este artigo foi traduzido. Se você tiver uma conexão de Internet, selecione "Veja este tópico online" para exibir a página no modo editável junto com o conteúdo original em inglês ao mesmo tempo.|  
|MT_QualityEditable|Este artigo foi traduzido manualmente. Se você tiver uma conexão de Internet, selecione "Veja este tópico online" para exibir a página no modo editável junto com o conteúdo original em inglês ao mesmo tempo.|  
|MT_QualityNonEditable|Este artigo foi traduzido manualmente. Se você tiver uma conexão de Internet, selecione "Veja este tópico online" para exibir a página no modo editável junto com o conteúdo original em inglês ao mesmo tempo.|  
|MT_BetaContents|Este artigo foi traduzido automaticamente para uma versão preliminar. Se você tiver uma conexão de Internet, selecione "Veja este tópico online" para exibir a página no modo editável junto com o conteúdo original em inglês ao mesmo tempo.|  
|MT_BetaRecycledContents|Este artigo foi traduzido manualmente para uma versão preliminar. Se você tiver uma conexão de Internet, selecione "Veja este tópico online" para exibir a página no modo editável junto com o conteúdo original em inglês ao mesmo tempo.|  
|Recurso:|**LinkTable**|  
|Uso:|Suporte para os links do tópico online|  
|**Elemento**|**Value**|  
|LinkTableTitle|Tabela de link|  
|TopicEnuLinkText|Exibir a versão em inglês\</a > deste tópico que está disponível no seu computador.|  
|TopicOnlineLinkText|Veja este tópico \<um href = "{0}" \\{1 \\} > online\</a >|  
|OnlineText|Online|  
|Recurso:|**Controle de áudio de vídeo**|  
|Uso:|Exibir texto para conteúdo de vídeo e elementos|  
|**Elemento**|**Value**|  
|MultiMediaNotSupported|Internet Explorer 9 ou posterior deve ser instalado para dar suporte a conteúdo de {0}.|  
|VideoText|a exibição de vídeo|  
|AudioText|fluxo de áudio|  
|OnlineVideoLinkText|\<p > para exibir o vídeo associado a este tópico, clique em {0}\<um href = "\ {1 \}" > {2}here\</a >.\< / p >|  
|OnlineAudioLinkText|\<p > para ouvir o áudio associado a este tópico, clique em {0}\<um href = "\ {1 \}" > {2}here\</a >.\< / p >|  
|Recurso:|**Controle de conteúdo não está instalado**|  
|Uso:|Elementos de texto (cadeias de caracteres) usados para a renderização de contentnotinstalled.htm|  
|**Elemento**|**Value**|  
|ContentNotInstalledTitle|Nenhum conteúdo foi encontrado no seu computador.|  
|ContentNotInstalledDownloadContentText|\<p > para baixar o conteúdo em seu computador, \<um href = "{0}" \\{1 \\} > clique na guia gerenciar\</a >.\< / p >|  
|ContentNotInstalledText|\<p > nenhum conteúdo é instalado no seu computador. Consulte o administrador para a instalação de conteúdo de ajuda local.  \< /p >|  
|Recurso:|**Controle de tópico não encontrado**|  
|Uso:|Elementos de texto (cadeias de caracteres) usados para a renderização de topicnotfound.htm|  
|**Elemento**|**Value**|  
|TopicNotFoundTitle|Não é possível localizar o tópico solicitado no seu computador.|  
|TopicNotFoundViewOnlineText|\<p > o tópico solicitado não foi encontrado no seu computador, mas você pode \<um href = "{0}" \\{1 \\} > Exibir o tópico online\</a >.\< / p >|  
|TopicNotFoundDownloadContentText|\<p > consulte o painel de navegação para links para tópicos semelhantes, ou \<um href = "{0}" \\{1 \\} > clique na guia gerenciar\</a > para baixar o conteúdo em seu computador.\< / p >|  
|TopicNotFoundText|\<p > o tópico solicitado não foi encontrado no seu computador.  \< /p >|  
|Recurso:|**Tópico corrompido controle**|  
|Uso:|Elementos de texto (cadeias de caracteres) usados para a renderização de topiccorrupted.htm|  
|**Elemento**|**Value**|  
|TopicCorruptedTitle|Não é possível exibir o tópico solicitado.|  
|TopicCorruptedViewOnlineText|\<p > o Visualizador da Ajuda é não é possível exibir o tópico solicitado. Pode haver um erro no conteúdo do tópico ou uma dependência de sistema subjacente.  \< /p >|  
|Recurso:|**Controle de página inicial**|  
|Uso:|Texto oferecer suporte à exibição do conteúdo do nó de nível superior do Visualizador da Ajuda.|  
|**Elemento**|**Value**|  
|HomePageTitle|Home page Visualizador da Ajuda|  
|HomePageIntroduction|\<p > Bem-vindo ao Visualizador da Ajuda Microsoft, uma fonte essencial de informações para todos que utilizam ferramentas, produtos, tecnologias e serviços Microsoft. O Visualizador da Ajuda fornece acesso a instruções e informações de referência, código de exemplo, artigos técnicos e muito mais. Para localizar o conteúdo que necessário, procure o sumário, use a pesquisa de texto completo ou navegue pelo conteúdo usando o índice de palavra-chave.  \< /p >|  
|HomePageContentInstallText|\<p >\<br / > Use o \<um href = "{0}" \\{1 \\} > Gerenciar conteúdo\</a > guia para fazer o seguinte:\<ul >\<li > Adicionar conteúdo ao seu computador.\< / li >\<li > Verifique as atualizações para seu conteúdo local.\< / li >\<li > Remover conteúdo do seu computador.\< / li >\</ul > \< /p >|  
|HomePageInstalledBooks|Livros instalados|  
|HomePageNoBooksInstalled|Nenhum conteúdo foi encontrado no seu computador.|  
|HomePageHelpSettings|Configurações de conteúdo de ajuda|  
|HomePageHelpSettingsText|\<p > sua configuração atual é ajuda local. O Visualizador da Ajuda exibe o conteúdo que você instalou no seu computador. \<br / > para alterar a fonte de conteúdo da Ajuda, na barra de menus do Visual Studio, escolha \<span style = "{0}" > Ajuda, definir preferência da Ajuda\</span >.\< br / > \< /p >|  
|Megabytes|MB|  
  
**branding.js**  
  
O arquivo branding.js contém JavaScript usados pelos elementos de identidade visual do Visual Studio Help Viewer.  Abaixo está uma lista de elementos de identidade visual e a função JavaScript suporte.  Todas as cadeias de caracteres a ser localizada para esse arquivo são definidas na seção "Cadeias de caracteres localizáveis" na parte superior do arquivo.  Observe que o arquivo ICL foi criado para loc cadeias de caracteres dentro do arquivo branding.js.  
  
||||  
|-|-|-|  
|**Recurso de identidade Visual**|**Função JavaScript**|**Descrição**|  
|Var...||Definir variáveis|  
|Obter a linguagem de código do usuário|setUserPreferenceLang|mapeia um índice # para a linguagem de código|  
|Definir e obter valores de cookie|getCookie, setCookie||  
|Membro herdado|changeMembersLabel|Expandir/recolher membro herdado|  
|Quando SelfBranded = False|onLoad|Ler a cadeia de caracteres de consulta para verificar se é uma solicitação de impressão.  Defina todos os codesnippets para se concentrar na guia preferencial do usuário.  Se for uma impressão solicitação, em seguida, defina isPrinterFriendly como true. Verifique se o modo de alto contraste.|  
|Trecho de código|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|grave todos os objetos de controle recolhível na lista.|  
||CA_Click|com base no estado de área recolhível, define qual imagem e texto para apresentar|  
|Suporte de contraste do logotipo|isBlackBackground()|Chamado para determinar se o plano de fundo preto.  Apenas preciso quando no modo de alto contraste.|  
||isHighContrast()|usar um intervalo de cor para detectar o modo de alto contraste|  
||onHighContrast(black)|Chamado quando o alto contraste é detectado|  
|Funcionalidade LST|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|Funcionalidade de multimídia|legenda (Iniciar, end, texto, estilo)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (styleName, styleValue)||  
||showCC(id)||  
||SubTitle(ID)||  
  
**ARQUIVOS HTM**  
  
O pacote de marcas contém um conjunto de arquivos HTM que suportam cenários para comunicar as informações de chave para usuários de conteúdo de Ajuda, por exemplo uma home page que contém uma seção que descreve quais conjuntos de conteúdo estão instalados e as páginas informando ao usuário quando não é possível tópicos ser encontrado no conjunto de locais de tópicos. Observe que esses arquivos HTM podem ser modificados por produto.  Fornecedores de Shell ISO são capazes de executar o pacote de marcas padrão e alterar o comportamento e o conteúdo dessas páginas Suite sua necessidade.  Esses arquivos, consulte seu respectivo pacote de marcas para que as marcas de identidade visual para obter o conteúdo correspondente do arquivo branding.xml.  
  
||||  
|-|-|-|  
|**Arquivo**|**Use**|**Fonte de conteúdo exibido**|  
|HomePage|Isso é uma página que exibe o conteúdo atualmente instalado e qualquer outra mensagem apropriada para apresentar ao usuário sobre seu conteúdo.  Este arquivo tem o conteúdo adicional da meta dados atributo "Microsoft.Help.Id" = "-1", que coloca esse conteúdo na parte superior do Sumário conteúdo local.||  
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.XML, marca \<HomePageTitle >|  
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.XML, marca \<HomePageIntroduction >|  
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.XML, marca \<HomePageContentInstallText >|  
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Cabeçalho de seção marca Branding.xml\<HomePageInstalledBooks >, os dados gerados do aplicativo, \<HomePageNoBooksInstalled > quando nenhum manuais são instalados.|  
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Cabeçalho de seção marca Branding.xml \<HomePageHelpSettings >, seção texto \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Quando um tópico existe no conjunto de local, mas por algum motivo não pode ser exibido (corrompido conteúdo).||  
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, marca \<TopicCorruptedTitle >|  
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.XML, marca \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Quando um tópico não se encontra no conteúdo do local definido, nem está disponível online||  
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.XML, marca \<TopicNotFoundTitle >|  
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.XML, marca \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, marca \<TopicNotFoundText >|  
|contentnotinstalled.htm|Quando não houver nenhum conteúdo local instalado do produto.||  
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.XML, marca \<ContentNotInstalledTitle >|  
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.XML, marca \<ContentNotInstalledDownloadContentText >|  
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.XML, marca \<ContentNotInstalledText >|  
  
**Arquivos CSS**  
  
O pacote Visual Studio ajuda Visualizador de identidade visual contém dois arquivos de css para dar suporte à apresentação conteúda consistente Ajuda do Visual Studio:  
  
-   Branding.css - contém elementos de css para renderização where SelfBranded = false  
  
-   Printer.css - contém elementos de css para renderização where SelfBranded = false  
  
Arquivos de Branding.CSS inclui definições para a apresentação de tópico do Visual Studio (limitação é que o branding.css contidos no Branding_\<localidade > mshc do serviço do pacote podem ser alterados).  
  
**Arquivos gráficos**  
  
Conteúdo do Visual Studio exibe um logotipo do Visual Studio, bem como outros elementos gráficos.  A lista completa de arquivos gráficos no pacote de identidade visual do Visual Studio Help Viewer é mostrada abaixo.  
  
||||  
|-|-|-|  
|**Arquivo**|**Use**|**Exemplos**|  
|clear.gif|Usado para renderizar a área recolhível||  
|footer_slice.gif|Apresentação de rodapé||  
|info_icon.gif|Usado quando exibindo informações|Aviso de isenção de responsabilidade|  
|online_icon.gif|Esse ícone é a ser associado com links online||  
|tabLeftBD.gif|Usado para renderizar o contêiner de trecho de código||  
|tabRightBD.gif|Usado para renderizar o contêiner de trecho de código||  
|vs_logo_bk.gif|Usado para referências de logotipo de contraste normal, conforme definido na marca de Branding.xml \<LogoFileName >.  Para produtos do Visual Studio, o nome do logotipo é vs_logo_bk.gif.||  
|vs_logo_wh.gif|Usado para referências de logotipo alta normal, conforme definido na marca de Branding.xml \<LogoFileNameHC >.  Para produtos do Visual Studio, o nome do logotipo é vs_logo_wh.gif.||  
|ccOff.png|Legenda de gráfico||  
|ccOn.png|Legenda de gráfico||  
|ImageSprite.png|Usado para renderizar a área recolhível|Expandir ou recolher o gráfico|  
  
### <a name="deploying-a-set-of-topics"></a>Implantando um conjunto de tópicos  
Este é um tutorial muito simple e rápido para a criação de uma implantação de conteúdo do Visualizador da Ajuda definida com um arquivo MSHA e o conjunto de cabs ou MSHC que contém os tópicos. O MSHA é um arquivo XML que descreve um conjunto de cabs ou arquivos MSHC. O Visualizador da Ajuda podem ler MSHA para obter uma lista de conteúdo (o. CAB ou. Arquivos MSHC) disponível para a instalação local.  
  
Isso é apenas um livro de instruções que descrevem o esquema XML muito básico para o MSHA de Visualizador de Ajuda.  Observe que há um exemplo de implementação abaixo esta visão geral e exemplo HelpContentSetup.  
  
O nome do MSHA, para fins de livro de instruções, é HelpContentSetup (o nome do arquivo pode ser qualquer coisa, com a extensão. MSHA). HelpContentSetup (exemplo abaixo) deve conter uma lista de cabs ou MSHCs disponíveis.  Observe que o tipo de arquivo deve ser consistente dentro do MSHA (não dá suporte a uma combinação de tipos de arquivo MSHA e CAB). Para cada CAB ou MSHC, deve haver um \<div classe = "pacote" >... \</div > (veja o exemplo abaixo).  
  
Observação: no exemplo de implementação abaixo, incluímos o pacote de marcas. Isso é essencial para incluir a fim de obter o necessários elementos de renderização do conteúdo do Visual Studio e comportamentos de conteúdo.  
  
Exemplo de arquivo HelpContentSetup: (substitua o "nome 1 do conjunto de conteúdo" e "nome do conjunto 2" etc. com seus nomes de arquivo de conteúdo.)  
  
```html
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>.  
  
```  
  
1.  Criar uma pasta local, algo como "C:\SampleContent"  
  
2.  Neste exemplo, usaremos arquivos MSHC para conter os tópicos.  Um MSHC é um zip com a extensão de arquivo alterado de. zip para. MSHC.  
  
3.  Criar o abaixo HelpContentSetup como um arquivo de texto (bloco de notas foi usado para criar o arquivo) e salve-o para a pasta mencionada acima (consulte a etapa 1).  
  
Observe que a classe "Marca" existe e é exclusivo. A marca mshc está incluído neste livro de instruções para que o conteúdo instalado terão a identidade visual e os comportamentos de conteúdo que estão contidos nos MSHCs terá suporte apropriado elementos contidos no pacote de identidade visual. Sem isso, haverá erros quando o sistema procura por itens de suporte que não fazem parte de copiados (instalado) conteúdo.  
  
Para obter o pacote de marca do Visual Studio, copie o arquivo de Branding_en US.mshc em C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ para sua pasta de trabalho.  
  
```html  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>  
<div class="package">  
<span class="packageType">branding</span>  
<span class="name">Branding_en-US</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Resumo**  
  
Usando e estendendo as etapas acima permitirá VSPs implantar seus conjuntos de conteúdo para o Visual Studio Help Viewer.  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Adicionando Ajuda para o Visual Studio Shell (integrado e isolado)  
**Introdução**  
  
Este passo a passo demonstra como incorporar o conteúdo da Ajuda em um aplicativo de Shell do Visual Studio e, em seguida, implantá-lo.  
  
**Requisitos**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 isolada Redist Shell](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**Visão geral**  
  
O [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell é uma versão do [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE no qual você pode basear um aplicativo. Esses aplicativos contêm o Shell isolado junto com as extensões que você criar. Usar modelos de projeto do Shell isolado, que são incluídos no [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, a criação de extensões.  
  
As etapas básicas para criar um aplicativo baseado no Shell isolado e da Ajuda:  
  
1.  Obter o [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistribuível (um download da Microsoft).  
  
2.  No Visual Studio, crie uma extensão de Ajuda que se baseia o Shell isolado, por exemplo, a extensão de Ajuda da Contoso que é descrita posteriormente neste passo a passo.  
  
3.  Quebra a extensão e o Shell de ISO redistribuível para uma implantação de MSI (uma configuração de aplicativo). Este passo a passo não inclui uma etapa de instalação.  
  
Crie um repositório de conteúdo do Visual Studio. Para o cenário de Shell integrado, altere Studio12 Visual para o nome do catálogo de produto da seguinte maneira:  
  
-   Crie pasta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.  
  
-   Crie um arquivo chamado CatalogType.xml e adicione-o para a pasta. O arquivo deve conter as seguintes linhas de código:  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
Defina o repositório de conteúdo no registro. Para o Shell integrado, altere VisualStudio15 para o nome do catálogo de produto:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     Chave: Valor de cadeia de caracteres LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     Chave: Valor de cadeia de caracteres CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentação  
  
**Criar o projeto**  
  
Para criar uma extensão de Shell isolado:  
  
1.  No Visual Studio, em **arquivo**, escolha **novo projeto**, em **outros tipos de projetos** escolha **extensibilidade**e, em seguida, escolha  **Visual Studio Shell isolado**. Nomeie o projeto `ContosoHelpShell`) para criar um projeto de extensibilidade com base no modelo do Visual Studio Shell isolado.  
  
2.  No Solution Explorer, no projeto ContosoHelpShellUI, na pasta arquivos de recurso, abra ApplicationCommands.vsct. Verifique se que essa linha é comentada (procure "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  Pressione a tecla F5 para compilar e executar **depurar**. Na instância experimental do IDE do Shell isolado, escolha o **ajuda** menu. Verifique se o **exibir ajuda**, **adicionar e remover conteúdo da Ajuda**, e **Definir preferência da Ajuda** comandos são exibidos.  
  
4.  No Solution Explorer, no projeto ContosHelpShell, na pasta de personalização do Shell, abra ContosoHelpShell.pkgdef. Para definir o catálogo de Ajuda da Contoso, adicione as seguintes linhas:  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  No Solution Explorer, no projeto ContosHelpShell, na pasta de personalização do Shell, abra ContosoHelpShell.Application.pkgdef. Para habilitar a Ajuda F1, adicione as seguintes linhas:  
  
    ```  
    // F1 Help Provider  
  
    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="13407"  
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"  
    @="Help3 Provider"  
    [$RootKey$\HelpProviders]  
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"  
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="Help3 Provider"  
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  No Solution Explorer, no menu de contexto da solução ContosoHelpShell, escolha o **propriedades** item de menu. Em **propriedades de configuração**, selecione **do Configuration Manager**. No **configuração** coluna, altere todos os valores "Debug" para "Versão".  
  
7.  Compile a solução. Isso cria um conjunto de arquivos em uma pasta de versão, que será usada na próxima seção.  
  
Para testar isso como se implantado:  
  
1.  No computador, você está implantando Contoso para instalar baixado Shell ISO (acima).  
  
2.  Criar uma pasta no \\\Program Files (x86)\\e nomeie-o `Contoso`.  
  
3.  Copie o conteúdo da pasta de versão ContosoHelpShell a \\pasta de \Contoso\ do \Program Files (x86).  
  
4.  Inicie o Editor do registro escolhendo **executar** no **iniciar** menu e inserindo `Regedit`. No editor do registro, escolha **arquivo**e, em seguida, **importação**. Navegue até a pasta do projeto ContosoHelpShell. Na pasta ContosoHelpShell sub, escolha ContosoHelpShell.reg.  
  
5.  Crie um repositório de conteúdo:  
  
     Para o Shell ISO - criar um repositório de conteúdo do Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     Para [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrated Shell, crie a pasta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  Criar CatalogType.xml e adicione o repositório de conteúdo (etapa anterior) que contém:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Adicione as seguintes chaves do registro:  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valor de cadeia de caracteres LocationPath:  
  
     Para o Shell do ISO:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell integrado:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-dos EUA  
  
     Chave: Valor de cadeia de caracteres CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentação. Para o Shell do ISO, isso é o nome do catálogo.  
  
8.  Copie seu conteúdo (cabs ou MSHC e MSHA) para uma pasta local.  
  
9. Linha de comando do Shell integrado exemplo para testar o repositório de conteúdo. Para o Shell do ISO, altere os valores de catálogo e launchingApp conforme apropriado para coincidir com o produto.  
  
     Método de /helpQuery /catalogName VisualStudio15 "C:\Program arquivos (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" = "página & id = ContosoTopic0" /launchingApp Microsoft VisualStudio, 12.0  
  
10. Inicie o aplicativo da Contoso (a partir da raiz do aplicativo Contoso). No Shell de ISO, escolha o **ajuda** item de menu e altere o **Definir preferência da Ajuda** para **usar a Ajuda Local**.  
  
11. Dentro do shell, escolha o **ajuda** item de menu, em seguida, **exibir ajuda**. Deve iniciar o Visualizador da Ajuda local. Escolha a guia **Gerenciar Conteúdo**. Em **origem de instalação**, escolha o **disco** botão de opção. Escolha o **...**  botão e navegue até a pasta local que contém o conteúdo do Contoso (copiado para a pasta local na etapa acima). Escolha o HelpContentSetup. A Contoso agora deve aparecer como um livro nas seleções de catálogo. Escolha **adicionar**e, em seguida, escolha o **atualização** botão (canto inferior direito).  
  
12. Dentro do IDE Contoso, escolha a tecla F1 para testar a funcionalidade de F1.  
  
### <a name="additional-resources"></a>Recursos adicionais  
Para a API de tempo de execução, consulte [API de Ajuda do Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
Para obter informações adicionais sobre como usar a API de Ajuda, consulte [exemplos de código do Visualizador de ajuda](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
Para fornecer comentários sobre esses componentes, use [Microsoft Connect](http://connect.microsoft.com/).  
  
Envie sugestões de recursos para [voz do usuário Microsoft](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
Para obter ajuda adicional, experimente o [fóruns do sistema de Ajuda e documentação do desenvolvedor MSDN](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
Atualizações recentes problema, consulte o [Leiame do Visualizador de ajuda](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
Para contatar a equipe de ajuda visualizador PM diretamente, envie um email para hlpfdbk@microsoft.com