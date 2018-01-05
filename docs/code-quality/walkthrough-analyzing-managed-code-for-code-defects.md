---
title: "Passo a passo: Analisando código gerenciado em busca de defeitos de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ea39704ea232fb304257b897087f0ae60d19c4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Instruções passo a passo: analisando código gerenciado em busca de defeitos de código
Neste passo a passo, você pode analisar um projeto gerenciado em busca de defeitos de código usando a ferramenta de análise de código.  
  
 Este passo a passo o guiará pelo processo de uso de análise de código para analisar seus assemblies de código gerenciado do .NET para conformidade com as diretrizes de Design do Microsoft .NET Framework.  
  
 Neste passo a passo, você:  
  
-   Analisar e corrigir os avisos de defeito de código.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Criar uma biblioteca de classes  
  
#### <a name="to-create-a-class-library"></a>Para criar uma biblioteca de classes  
  
1.  Sobre o **arquivo** menu de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], clique em **novo** e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo **tipos de projeto**, clique em **Visual C#**.  
  
3.  Em **modelos**, selecione **biblioteca de classes**.  
  
4.  No **nome** caixa de texto, digite **CodeAnalysisManagedDemo** e, em seguida, clique em **Okey**.  
  
5.  Depois que o projeto é criado, abra o arquivo Class1.cs.  
  
6.  Substitua o texto existente em Class1. cs com o código a seguir:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Salve o arquivo Class1.cs.  
  
## <a name="analyze-the-project"></a>Analisar o projeto  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analisar um projeto gerenciado em busca de defeitos de código  
  
1.  Selecione o projeto CodeAnalysisManagedDemo na **Gerenciador de soluções**.  
  
2.  No menu **Projeto**, clique em **Propriedades**.  
  
     A página de propriedades CodeAnalysisManagedDemo é exibida.  
  
3.  Clique em **CodeAnalysis**.  
  
4.  Verifique se **habilitar análise de código no Build (define a constante CODE_ANALYSIS**) é verificada.  
  
5.  Do **executar esse conjunto de regras** lista suspensa, selecione **Microsoft todas as regras**.  
  
6.  Sobre o **arquivo** menu, clique em **salvar itens selecionados**e, em seguida, feche as páginas de propriedades de ManagedDemo.  
  
7.  No **criar** menu, clique em **ManagedDemo criar**.  
  
     Os avisos de compilação de projeto CodeAnalysisManagedDemo são relatados no **análise de código** e **saída** windows.  
  
     Se o **análise de código** janela não aparecerem, no **analisar** menu, escolha **Windows** e **escolha análise de código**.  
  
## <a name="correct-the-code-analysis-issues"></a>Corrija os problemas de análise de código  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Para corrigir as violações de regras de análise de código  
  
1.  Sobre o **exibição** menu, clique em **lista de erros**.  
  
     Dependendo do perfil de desenvolvedor que você escolheu, talvez você precise aponte para **outras janelas** no **exibição** menu e clique **lista de erros**.  
  
2.  Em **Solution Explorer**, clique em **Mostrar todos os arquivos**.  
  
3.  Em seguida, expanda o nó de propriedades e, em seguida, abra o arquivo AssemblyInfo.  
  
4.  Use o seguinte para corrigir avisos:  
  
-   [CA1014: Marcar assemblies com CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'demonstração' deve ser marcada com CLSCompliantAttribute e seu valor deve ser true.  
  
    -   Adicione o código `using``System;` para o arquivo AssemblyInfo.  
  
         Em seguida, adicione o código `[assembly: CLSCompliant(true)]` até o final do arquivo AssemblyInfo.  
  
         Recompile o projeto.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demo(String) pública  
  
    -   Adicionar o construtor `public demo (String s) : base(s) { }` para a classe `demo`.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demonstração pública (cadeia de caracteres, exceção)  
  
    -   Adicionar o construtor `public demo (String s, Exception e) : base(s, e) { }` para a classe `demo`.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: protegido demonstração (SerializationInfo, StreamingContext)  
  
    -   Adicione o código `using System.Runtime.Serialization;` para o início do arquivo Class1.cs.  
  
         Em seguida, adicione o construtor`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Recompile o projeto.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demo() pública  
  
    -   Adicionar o construtor `public demo () : base() { }` para a classe `demo` **.**  
  
         Recompile o projeto.  
  
-   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija o uso de maiusculas e minúsculas do nome do namespace 'testCode' alterando-o para 'TestCode'.  
  
    -   Alterar o uso de maiusculas e minúsculas do namespace `testCode` para `TestCode`.  
  
-   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija o uso de maiusculas e minúsculas do tipo nome 'demonstração' alterando-o para 'Demonstração'.  
  
    -   Alterar o nome do membro `Demo`.  
  
-   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija o uso de maiusculas e minúsculas do item' nome de membro' alterando-o para 'Item'.  
  
    -   Alterar o nome do membro `Item`.  
  
-   [CA1710: Os identificadores devem ter sufixo correto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Renomear 'testCode.demo' termine em 'Exception'.  
  
    -   Alterar o nome da classe e seus construtores para `DemoException`.  
  
-   [CA2210: Os Assemblies devem ter nomes fortes válidos](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): assinar 'ManagedDemo' com uma chave de nome forte.  
  
    -   Sobre o **projeto** menu, clique em **ManagedDemo propriedades**.  
  
         As propriedades de projeto aparecem.  
  
         Clique em **assinatura**.  
  
         Selecione o **assinar o assembly** caixa de seleção.  
  
         No **escolher um arquivo de chave de nome de cadeia de caracteres** lista, selecione  **\<novo... >**.  
  
         O **criar chave de nome forte** caixa de diálogo é exibida.  
  
         No **nome do arquivo de chave**, digite TestKey.  
  
         Insira uma senha e, em seguida, clique em **Okey**.  
  
         Sobre o **arquivo** menu, clique em **salvar itens selecionados**e, em seguida, feche as páginas de propriedades.  
  
         Recompile o projeto.  
  
-   [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: adicionar um atributo [Serializable] para o tipo 'demonstração', pois este tipo implementa ISerializable.  
  
    -   Adicionar o `[Serializable ()]` de atributo para a classe `demo`.  
  
         Recompile o projeto.  
  
 Depois de concluir as alterações, o arquivo Class1.cs deve parecer com o seguinte:  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>Excluir avisos da análise de código  
  
#### <a name="to-exclude-code-defect-warnings"></a>Para excluir os avisos de defeito de código  
  
1.  Para cada um dos avisos restantes, faça o seguinte:  
  
    1.  Na janela análise de código, selecione o aviso.  
  
    2.  Escolha **ações**, em seguida, escolha **suprimir mensagem**e, em seguida, escolha **no arquivo de supressão do projeto**.  
  
     Para obter mais informações, consulte [como: suprimir avisos usando o Item de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Recompile o projeto.  
  
     O projeto é compilado sem avisos ou erros.