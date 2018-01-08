---
title: "Suporte para trechos de código em um serviço de linguagem herdado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6102a5bb6298cd6403285e3d36842424b0be3412
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Suporte para trechos de código em um serviço de linguagem herdado
Um trecho de código é um trecho de código é inserido no arquivo de origem. O trecho de código em si é um modelo baseado em XML com um conjunto de campos. Esses campos são realçados depois que o trecho de código é inserido e pode ter valores diferentes dependendo do contexto no qual o trecho de código é inserido. Imediatamente depois de inserido o trecho de código, o serviço de linguagem pode formatar o trecho de código.  
  
 O trecho de código é inserido em um modo de edição especial que permite que os campos do trecho de código para ser navegado usando a tecla TAB. Os campos podem oferecer suporte a menus suspensos de estilo do IntelliSense. O usuário confirma o trecho de código para o arquivo de origem, digitando o ENTER ou a tecla ESC. Para saber mais sobre os trechos de código, consulte [trechos de código](../../ide/code-snippets.md).  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [passo a passo: Implementando trechos de código](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso melhorar o desempenho do seu serviço de linguagem e permitem que você aproveite os novos recursos do editor.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Suporte de estrutura de pacote de trechos de código gerenciado  
 A estrutura de pacote gerenciado (MPF) dá suporte a mais funcionalidade de trecho de código, leiam o modelo para inserir o trecho de código e habilitando o especial do modo de edição. O suporte é gerenciado por meio de <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe.  
  
 Quando o <xref:Microsoft.VisualStudio.Package.Source> classe é instanciada, o <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> método o <xref:Microsoft.VisualStudio.Package.LanguageService> classe é chamada para obter uma <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto (Observe que a base de <xref:Microsoft.VisualStudio.Package.LanguageService> classe sempre retorna um novo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto para cada <xref:Microsoft.VisualStudio.Package.Source> objeto).  
  
 MPF não oferece suporte a funções de expansão. Uma função de expansão é uma função nomeada que é inserida em um modelo de trecho de código e retorna um ou mais valores sejam colocados em um campo. Os valores são retornados pelo idioma do serviço em si por meio de um <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objeto. O <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objeto deve ser implementado pelo serviço de linguagem para dar suporte a funções de expansão.  
  
## <a name="providing-support-for-code-snippets"></a>Dando suporte a trechos de código  
 Para habilitar o suporte para trechos de código, você deve fornecer ou instalar os trechos de código e você deve fornecer os meios para o usuário inserir os trechos de código. Há três etapas para habilitar o suporte a trechos de código:  
  
1.  Instalando os arquivos de trecho de código.  
  
2.  Habilitação de trechos de código para o serviço de linguagem.  
  
3.  Invocar o <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto.  
  
### <a name="installing-the-snippet-files"></a>Instalar os arquivos de trecho de código  
 Todos os trechos de código para um idioma são armazenados como modelos em arquivos XML, normalmente um modelo de trecho de código por arquivo. Para obter detalhes sobre o esquema XML usado para modelos de trecho de código, consulte [referência de esquema de trechos de código](../../ide/code-snippets-schema-reference.md). Cada modelo de trecho de código é identificado com uma ID de idioma. Este idioma ID é especificado no registro e é colocada no `Language` atributo do \<código > marca no modelo.  
  
 Geralmente, há dois locais onde são armazenados os arquivos de modelo de trecho de código: 1) em que o idioma foi instalado e 2) na pasta do usuário. Esses locais são adicionados ao registro até que o Visual Studio **Gerenciador de trechos de código** pode localizar os trechos de código. A pasta do usuário é onde os trechos de código criados pelo usuário são armazenados.  
  
 O layout de pasta comum para os arquivos de modelo de trecho de código instalado tem esta aparência: *[Raiz_da_instalação]*\\*[TestLanguage]*\snippets.\\*[LCID]*\Snippets.  
  
 *[Raiz_da_instalação]*  é a pasta de instalação no seu idioma.  
  
 *[TestLanguage]*  é o nome do seu idioma como um nome de pasta.  
  
 *[LCID]*  é a ID de localidade. Isso é que as versões localizadas de como os trechos de código são armazenados. Por exemplo, a ID de localidade para o inglês é 1033, portanto *[LCID]* é substituído pelo 1033.  
  
 Um arquivo adicional deve ser fornecido e que é um arquivo de índice, geralmente chamado SnippetsIndex.xml ou ExpansionsIndex.xml (você pode usar qualquer nome de arquivo válido que termina em. xml). Esse arquivo é normalmente armazenado na *[Raiz_da_instalação]*\\*[TestLanguage]* pasta e especifica o local exato da pasta de trechos de código, bem como a ID de idioma e o GUID do idioma serviço que usa os trechos de código. O caminho exato do arquivo de índice é colocado no registro, conforme descrito posteriormente em "Instalar as entradas do Registro". Aqui está um exemplo de um arquivo SnippetsIndex.xml:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 O \<idioma > marca Especifica a ID de idioma (o `Lang` atributo) e o GUID do serviço de linguagem.  
  
 Este exemplo supõe que você instalou o serviço de idioma na pasta de instalação do Visual Studio. O LCID % é substituído por ID de localidade atual do usuário Vários \<SnippetDir > marcas podem ser adicionados, uma para cada diretório diferente e a localidade. Além disso, uma pasta de trecho de código pode conter subpastas, cada um deles é identificada no arquivo de índice com o \<SnippetSubDir > marca inserida em um \<SnippetDir > marca.  
  
 Os usuários também podem criar seus próprios trechos de código para o seu idioma. Eles normalmente são armazenados na pasta de configurações do usuário, por exemplo *[TestDocs]*\Code trechos\\*[TestLanguage]*\Test trechos de código, onde *[TestDocs]* é o local da pasta de configurações do usuário para o Visual Studio.  
  
 Os seguintes elementos de substituição podem ser colocados no caminho armazenado no \<DirPath > marca no arquivo de índice.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|LCID %|ID de localidade.|  
|Raiz_da_instalação %|Pasta de instalação raiz para o Visual Studio, por exemplo, C:\Program Files\Microsoft Visual Studio 8.|  
|% ProjDir %|Pasta que contém o projeto atual.|  
|% ProjItem %|Pasta que contém o item de projeto atual.|  
|% TestDocs %|Na pasta de configurações do usuário, por exemplo, C:\Documents and Settings\\*[username]*Documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Habilitando trechos de código para seu serviço de linguagem  
 Você pode ativar o trechos de código para o serviço de linguagem, adicionando o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> de atributo para o VSPackage (consulte [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obter detalhes). O <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> e <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parâmetros são opcionais, mas você deve incluir o `SearchPaths` parâmetro nomeado para informar o **Gerenciador de trechos de código** do local de trechos de código.  
  
 Este é um exemplo de como usar esse atributo:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>Chamando o provedor de expansão  
 O serviço de linguagem controla a inserção de qualquer trecho de código, bem como o modo de inserção é invocada.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Chamando o provedor de expansão para trechos de código  
 Há duas maneiras para chamar o provedor de expansão: usando um comando de menu ou usando um atalho de uma lista de conclusão.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Inserindo um trecho de código usando um comando de Menu  
 Para usar um comando de menu para exibir o navegador de trecho de código, você pode adicionar um comando de menu e, em seguida, chame o <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> método o <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interface em resposta a esse comando de menu.  
  
1.  Adicione um botão e um comando para o arquivo. VSCT. Você pode encontrar instruções para fazer isso no [criando uma extensão com um comando de Menu](../../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Derivar uma classe a partir de <xref:Microsoft.VisualStudio.Package.ViewFilter> classe e substituir o <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> método para indicar o suporte para o novo comando de menu. Este exemplo sempre ativa o comando de menu.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  Substituir o <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> método no <xref:Microsoft.VisualStudio.Package.ViewFilter> classe para obter o <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto e chamar o <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> método naquele objeto.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     Os seguintes métodos na <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe são chamados pelo Visual Studio na ordem fornecida durante o processo de inserir o trecho de código:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Após o <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> método é chamado, o trecho de código tenha sido inserido e o <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objeto está em um modo de edição especial usado para modificar um trecho de código que foi inserido.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Inserindo um trecho de código usando um atalho  
 Implementação de um atalho de uma lista de conclusão é muito mais envolvida que a implementação de um comando de menu. Primeiro, você deve adicionar atalhos de trecho de código para a lista de conclusão do IntelliSense word. Em seguida, você deve detectar quando um nome de atalho de trecho de código foi inserido como resultado da conclusão. Por fim, você deve obter o título do trecho de código e o caminho usando o nome do atalho e passar essa informação para o <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método sobre o <xref:Microsoft.VisualStudio.Package.ExpansionProvider> método.  
  
 Para adicionar atalhos de trecho de código para a lista de conclusão de palavras, adicioná-los para o <xref:Microsoft.VisualStudio.Package.Declarations> do objeto em seu <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Você deve se certificar de que você pode identificar o atalho como um nome de trecho de código. Para obter um exemplo, consulte [passo a passo: obtendo uma lista de instalado trechos de código (herdado de implementação)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Você pode detectar a inserção de no atalho do trecho de código no <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> método o <xref:Microsoft.VisualStudio.Package.Declarations> classe. Porque o nome do trecho de código já tenha sido inserido no arquivo de origem, ele deve ser removido quando a expansão é inserida. O <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método usa uma extensão que descreve o ponto de inserção para o trecho de código; se o intervalo inclui o nome do trecho inteira no arquivo de origem, esse nome será substituído pelo trecho de código.  
  
 Aqui está uma versão de um <xref:Microsoft.VisualStudio.Package.Declarations> classe que trata a inserção de trecho de código que recebe um nome de atalho. Outros métodos de <xref:Microsoft.VisualStudio.Package.Declarations> classe foram omitidos para fins de esclarecimento. Observe que o construtor da classe utiliza um <xref:Microsoft.VisualStudio.Package.LanguageService> objeto. Isso pode ser passado de sua versão do <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto (por exemplo, a implementação do <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe pode levar a <xref:Microsoft.VisualStudio.Package.LanguageService> no construtor de objeto e passa o objeto no seu `TestDeclarations` construtor de classe).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Quando o serviço de linguagem obtém o nome do atalho, ele chama o <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> método para obter o título do trecho de nome de arquivo e código. O serviço de linguagem, em seguida, chama o <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método no <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe para inserir o trecho de código. Os seguintes métodos são chamados pelo Visual Studio na ordem fornecida no <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe durante o processo de inserir o trecho de código:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Para obter mais informações sobre como obter uma lista de trechos de código instalado para o serviço de linguagem, consulte [passo a passo: obtendo uma lista de instalado trechos de código (herdado de implementação)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implementando a classe ExpansionFunction  
 Uma função de expansão é uma função nomeada que é inserida em um modelo de trecho de código e retorna um ou mais valores sejam colocados em um campo. Para oferecer suporte a funções de expansão em seu serviço de idioma, você deve derivar uma classe a partir de <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe e implementar o <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> método. Em seguida, você deve substituir o <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> método no <xref:Microsoft.VisualStudio.Package.LanguageService> classe para retornar uma nova instanciação da sua versão do <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe para cada função de expansão, você dá suporte. Se você oferecer suporte a uma lista de valores possíveis de uma função de expansão, você também deve substituir o <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> método o <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe para retornar uma lista desses valores.  
  
 Uma função de expansão que obtém argumentos ou precisa acessar outros campos não deve ser associada um campo editável, pois o provedor de expansão pode não ser totalmente inicializado no momento em que a função de expansão é chamada. Como resultado, a função de expansão não é capaz de obter o valor de seus argumentos ou qualquer outro campo.  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo de como uma função de expansão simples chamado `GetName` pode ser implantado. Essa função de expansão anexará um número para um nome de classe base cada vez que a função de expansão é instanciada (que corresponde a cada vez que o trecho de código associada é inserido).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Trechos de código](../../ide/code-snippets.md)   
 [Passo a passo: Obter uma lista de trechos de código instalados (implementação herdada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)