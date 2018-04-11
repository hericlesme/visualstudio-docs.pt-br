---
title: As instruções para criar modelos de texto T4 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: accf32ad313cbbfe11c2e85fdfe3101ab428c4a4
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Diretrizes para escrever modelos de texto T4
Essas diretrizes gerais podem ser úteis se você estiver gerando o código do programa ou outros recursos de aplicativo em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Eles não são fixas regras.  
  
## <a name="guidelines-for-design-time-t4-templates"></a>Diretrizes para modelos T4 de tempo de Design  
 Modelos T4 de tempo de design são modelos de geram código em seu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto em tempo de design. Para obter mais informações, consulte [geração de código de tempo de Design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Gere variável aspectos do aplicativo.  
 Geração de código é mais útil para os aspectos do aplicativo que podem ser alteradas durante o projeto, ou será alterado entre versões diferentes do aplicativo. Separe esses aspectos variável dos aspectos mais invariáveis para que você possa determinar mais facilmente o que precisa ser gerado. Por exemplo, se seu aplicativo fornece um site da Web, separe a página padrão que serve de funções da lógica que define os caminhos de navegação de uma página para outra.  
  
 Codifica os aspectos de variável em um ou mais modelos de origem.  
 Um modelo é um arquivo ou banco de dados que lê cada modelo para obter valores específicos de variável partes do código que será gerado. Modelos podem ser bancos de dados, arquivos XML de seu próprio design, diagramas ou linguagens específicas de domínio. Normalmente, um modelo é usado para gerar muitos arquivos em um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Cada arquivo é gerado a partir de um modelo separado.  
  
 Você pode usar mais de um modelo em um projeto. Por exemplo, você pode definir um modelo de navegação entre páginas da Web e um modelo separado para o layout das páginas.  
  
 Focar o modelo nas necessidades dos usuários e o vocabulário, não em sua implementação.  
 Por exemplo, um aplicativo do site, você esperaria de modelo para se referir a páginas da Web e hiperlinks.  
  
 Idealmente, escolha uma forma de apresentação que atenda o tipo de informação que representa o modelo. Por exemplo, um modelo de caminhos de navegação por meio de um site da Web pode ser um diagrama das caixas e setas.  
  
 Teste o código gerado.  
 Use testes manuais ou automatizados para verificar se o código resultante funciona conforme os usuários precisam. Evite a geração de testes do mesmo modelo do qual o código é gerado.  
  
 Em alguns casos, os testes gerais podem ser executados no modelo diretamente. Por exemplo, você poderia escrever um teste que garante que todas as páginas no site da Web podem ser alcançada pela navegação de qualquer outro.  
  
 Permitir código personalizado: gerar classes parciais.  
 Permitir código que você escrever manualmente além para o código gerado. É comum para um esquema de geração de código para ser capaz de levar em conta todas as possíveis variações que podem surgir. Portanto, você deve esperar adicionar ou substituir a parte do código gerado. Onde o material gerado está em uma linguagem .NET, como [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], duas estratégias são especialmente úteis:  
  
-   Classes geradas devem ser parciais. Isso permite que você adicionar conteúdo ao código gerado.  
  
-   Classes devem ser geradas em pares, um herdar de outro. A classe base deve conter todas as propriedades e métodos gerados, e a classe derivada deve conter somente os construtores. Isso permite que seu código manual substituir qualquer um dos métodos gerados.  
  
 Em outros idiomas gerados como XML, use o `<#@include#>` diretiva fazer combinações simples do conteúdo gerado e manual. Em casos mais complexos, você talvez precise gravar uma etapa de pós-processamento que combina o arquivo gerado com quaisquer arquivos manual.  
  
 Mover o material comum em modelos de tempo de execução ou arquivos de inclusão  
 Para evitar a repetição semelhantes blocos de texto e código em vários modelos, use o `<#@ include #>` diretiva. Para obter mais informações, consulte [T4 incluem diretiva](../modeling/t4-include-directive.md).  
  
 Você pode também criar modelos de texto de tempo de execução em um projeto separado e, em seguida, chamá-los a partir do modelo de tempo de design. Para fazer isso, use o `<#@ assembly #>` diretiva para acessar o projeto separado. Para obter exemplos, consulte ["Herança em modelos de texto" no Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
 Considere a possibilidade de mover grandes blocos de código em um assembly separado.  
 Se você tiver blocos de código grande e blocos de recurso de classe, ele pode ser útil mover alguns desse código em métodos que você compila um projeto separado. Você pode usar o `<#@ assembly #>` diretiva para acessar o código no modelo. Para obter mais informações, consulte [diretiva de Assembly T4](../modeling/t4-assembly-directive.md).  
  
 Você pode colocar os métodos em uma classe abstrata que o modelo pode ser herdada. A classe abstrata deve herdar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Para obter mais informações, consulte [diretiva de modelo T4](../modeling/t4-template-directive.md).  
  
 Gerar código, não os arquivos de configuração  
 Um método de gravação de um aplicativo de variável é escrever um código de programa genérico que aceita um arquivo de configuração. Um aplicativo criado dessa maneira é muito flexível e pode ser reconfigurado quando alterarem os requisitos de negócios, sem recompilar o aplicativo. No entanto, uma desvantagem dessa abordagem é que o aplicativo será um desempenho inferior que um aplicativo mais específico. Além disso, seu código de programa será mais difícil de ler e manter, em parte porque ela tem sempre lidar com os tipos mais genéricos.  
  
 Por outro lado, um aplicativo cujos variável partes são gerados antes da compilação pode ser fortemente tipado. Isso torna muito mais fácil e mais confiáveis para escrever código manual e integrá-lo com gerado partes do software.  
  
 Para obter todos os benefícios de geração de código, tente gerar o código de programa em vez de arquivos de configuração.  
  
 Usar uma pasta de código gerado  
 Coloque os modelos e os arquivos gerados em uma pasta de projeto chamada **código gerado**, para torná-lo limpar esses não são arquivos que devem ser editados diretamente. Se você criar código personalizado para substituir ou adicionar a classes geradas, coloque as classes em uma pasta denominada **código personalizado**. A estrutura de um projeto típico tem esta aparência:  
  
```  
MyProject  
   Custom Code  
      Class1.cs  
      Class2.cs  
   Generated Code  
      Class1.tt  
          Class1.cs  
      Class2.tt  
          Class2.cs  
   AnotherClass.cs  
  
```  
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Diretrizes para modelos T4 (pré-processados) de tempo de execução  
 Mover o material comum em modelos de herdados  
 Você pode usar a herança para compartilhar os métodos e blocos de texto entre modelos de texto T4. Para obter mais informações, consulte [diretiva de modelo T4](../modeling/t4-template-directive.md).  
  
 Você também pode usar incluem arquivos com modelos de tempo de execução.  
  
 Mova grandes corpos de código para uma classe parcial.  
 Cada modelo de tempo de execução gera uma definição de classe parcial que tem o mesmo nome que o modelo. Você pode escrever um arquivo de código que contém outra definição parcial da mesma classe. Você pode adicionar os construtores, métodos e campos para a classe dessa maneira. Esses membros podem ser chamados de blocos de código no modelo.  
  
 Uma vantagem disso é que o código é mais fácil de escrever, porque o IntelliSense está disponível. Além disso, você pode obter uma separação melhor entre a apresentação e a lógica subjacente.  
  
 Por exemplo, em **MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 Em **MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 Permitir código personalizado: fornecer pontos de extensão  
 Considere gerar métodos virtuais em \<blocos de recurso de classe #+ #>. Isso permite que um único modelo a ser usado em vários contextos sem modificação. Em vez de modificar o modelo, você pode construir uma classe derivada que fornece a lógica adicional mínima. A classe derivada pode ser um código comum, ou pode ser um modelo de tempo de execução.  
  
 Por exemplo, no MyStandardRunTimeTemplate.tt:  
  
```  
This page is copyright <#= CompanyName() #>.  
<#+ protected virtual string CompanyName() { return ""; } #>  
```  
  
 No código de um aplicativo:  
  
```  
class FabrikamTemplate : MyStandardRunTimeTemplate  
{  
  protected override string CompanyName() { return "Fabrikam"; }  
}  
...  
  string PageToDisplay = new FabrikamTemplate().TextTransform();  
  
```  
  
## <a name="guidelines-for-all-t4-templates"></a>Diretrizes para todos os modelos T4  
 Coleta de dados separada da geração de texto  
 Tente evitar a combinação de computação e blocos de texto. Em cada modelo de texto, use a primeira \<bloco de código de # #> para definir as variáveis e executar cálculos complexos. Do primeiro bloco de texto até o fim do modelo ou a primeira \<bloquear o recurso de classe #+ #> evitar expressões longas e evitar condicionais e loops, a menos que eles contêm blocos de texto. Essa prática torna o modelo mais fácil de ler e manter.  
  
 Não use `.tt` para incluir arquivos  
 Usar uma extensão de nome de arquivo diferente, como `.ttinclude` para arquivos de inclusão. Use `.tt` somente de arquivos que você deseja ser processada como tempo de execução ou tempo de design de modelos de texto. Em alguns casos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reconhece `.tt` arquivos e define automaticamente suas propriedades para processamento.  
  
 Inicie cada modelo como um protótipo fixado.  
 Grave um exemplo do código ou texto que você deseja gerar e certifique-se de que ele está correto. Altere a extensão para. TT e inserir o código que modifica o conteúdo ao ler o modelo de forma incremental.  
  
 Considere o uso de modelos de tipo.  
 Embora você possa criar um esquema XML ou banco de dados para seus modelos, ele pode ser útil criar uma domínio específico DSL (linguagem). Uma DSL tem a vantagem de que ele gera uma classe para representar cada nó de esquema e as propriedades para representar os atributos. Isso significa que você pode programar em termos do modelo de negócios. Por exemplo:  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 Considere o uso de diagramas para seus modelos.  
 Muitos modelos com mais eficácia são apresentados e gerenciados simplesmente como tabelas de texto, especialmente se eles forem muito grandes.  
  
 No entanto, para alguns tipos de requisitos de negócios, é importante esclarecer conjuntos complexos de relações e fluxos de trabalho e diagramas são o melhor meio adequado. Uma vantagem de um diagrama é que é fácil abordar com usuários e outros participantes. Gerando o código de um modelo no nível de requisitos de negócios, você faz seu código mais flexível quando alterarem os requisitos.  
  
 Você também pode criar seu próprio tipo de diagrama como uma linguagem específica de domínio (DSL). Código pode ser gerado a partir de UML e DSLs. Para obter mais informações, consulte [analisando e arquitetura de modelagem](../modeling/analyze-and-model-your-architecture.md).  
  
## <a name="see-also"></a>Consulte também  
 [Geração de código de tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
