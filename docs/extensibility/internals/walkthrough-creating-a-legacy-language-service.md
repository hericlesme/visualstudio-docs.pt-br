---
title: 'Passo a passo: Criando um serviço de linguagem herdado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb1fc7b6c35b2ee6ef3a767f7093f2fa0e4cb972
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144928"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Passo a passo: Criando um serviço de linguagem herdado
Usando as classes de idioma do pacote gerenciado framework (MPF) para implementar um serviço de linguagem no [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] é simples. É necessário um VSPackage para hospedar o serviço de idioma, o próprio serviço de linguagem e um analisador para o seu idioma.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto do Visual Studio pacote podem ser encontrado em três locais de modelo diferente no **novo projeto** caixa de diálogo:  
  
1.  Em extensibilidade do Visual Basic. O idioma padrão do projeto é Visual Basic.  
  
2.  Em c# extensibilidade. O idioma padrão do projeto é c#.  
  
3.  Em outra extensibilidade de tipos de projeto. O idioma padrão do projeto é C++.  
  
### <a name="create-a-vspackage"></a>Criar um VSPackage  
  
1.  Crie um novo VSPackage com o modelo de projeto de pacote do Visual Studio.  
  
     Se você estiver adicionando um serviço de idioma para um VSPackage existente, ignore as etapas a seguir e ir diretamente para o procedimento "Criar a classe de serviço de linguagem".  
  
2.  Digite MyLanguagePackage para o nome do projeto e clique em **Okey**.  
  
     Você pode usar qualquer nome que você deseja. Esses procedimentos detalhados aqui supõem MyLanguagePackage como o nome.  
  
3.  Selecione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] como o idioma e a opção para gerar um novo arquivo de chave. Clique em **Avançar**.  
  
4.  Insira as informações da empresa e o pacote apropriadas. Clique em **Avançar**.  
  
5.  Selecione **comando de Menu**. Clique em **Avançar**.  
  
     Se você não pretende dar suporte a trechos de código, basta clicar em Concluir e ignorar a próxima etapa.  
  
6.  Digite **Inserir trecho** como o **nome do comando** e `cmdidInsertSnippet` para o **ID do comando**. Clique em **Finalizar**.  
  
     O **nome do comando** e **ID de comando** pode ser que desejar, essas são apenas exemplos.  
  
### <a name="create-the-language-service-class"></a>Criar a classe de serviço de linguagem  
  
1.  Em **Solution Explorer**, com o botão direito no projeto MyLanguagePackage, escolha **adicionar**, **referência**e, em seguida, escolha o **adicionar nova referência** botão.  
  
2.  No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualStudio.Package.LanguageService** no **.NET** guia e clique em **Okey**.  
  
     Isso precisa ser feito apenas uma vez para o projeto de pacote de idioma.  
  
3.  Em **Solution Explorer**, com o botão direito no projeto VSPackage e selecione **adicionar**, **classe**.  
  
4.  Certifique-se de **classe** está selecionado na lista de modelos.  
  
5.  Digite **MyLanguageService.cs** para o nome do arquivo de classe e **adicionar**.  
  
     Você pode usar qualquer nome que você deseja. Esses procedimentos detalhados aqui supõem `MyLanguageService` como o nome.  
  
6.  No arquivo MyLanguageService.cs, adicione o seguinte `using` instruções.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modificar o `MyLanguageService` classe derivar o <xref:Microsoft.VisualStudio.Package.LanguageService> classe:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Posicione o cursor em "LanguageService" e a partir de **editar**, **IntelliSense** menu, selecione **implementação de classe abstrata**. Isso adiciona os métodos mínimo necessário para implementar uma classe de serviço de linguagem.  
  
9. Implementar os métodos abstratos, conforme descrito em [implementar um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrar o serviço de linguagem  
  
1.  Abra o arquivo MyLanguagePackagePackage.cs e adicione o seguinte `using` instruções:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrar sua classe de serviço de idioma, conforme descrito em [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md). Isso inclui os atributos de ProvideXX e as seções "Proffering o serviço de idioma". Use MyLanguageService onde este tópico usa TestLanguageService.  
  
### <a name="the-parser-and-scanner"></a>O analisador e o Scanner  
  
1.  Implementar um analisador e o scanner para o seu idioma, conforme descrito em [analisador de serviço de linguagem herdado e o Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Como você implementa o analisador e o scanner é inteiramente você e está além do escopo deste tópico.  
  
## <a name="language-service-features"></a>Recursos do serviço de linguagem  
 Para implementar cada recurso no serviço de idioma, você normalmente deriva uma classe da classe de serviço de idioma apropriado MPF implementa todos os métodos abstratos conforme necessário e substituir os métodos apropriados. Quais classes que você cria e/ou deriva é depende dos recursos que você pretende dar suporte. Esses recursos são discutidos em detalhes em [recursos de serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md). O procedimento a seguir é a abordagem geral derivando uma classe de classes de MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Derivando uma classe MPF  
  
1.  Em **Solution Explorer**, com o botão direito no projeto VSPackage e selecione **adicionar**, **classe**.  
  
2.  Certifique-se de **classe** está selecionado na lista de modelos.  
  
     Insira um nome adequado para o arquivo de classe e clique em **adicionar**.  
  
3.  No novo arquivo de classe, adicione o seguinte `using` instruções.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modifique a classe para derivar da classe MPF desejada.  
  
5.  Adicione um construtor de classe que tem pelo menos os mesmos parâmetros do construtor da classe base e passar os parâmetros do construtor para o construtor da classe base.  
  
     Por exemplo, o construtor para uma classe derivada do <xref:Microsoft.VisualStudio.Package.Source> classe pode parecer com o seguinte:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Do **editar**, **IntelliSense** menu, selecione **implementação de classe abstrata** se a classe base tiver quaisquer métodos abstratos que devem ser implementados.  
  
7.  Caso contrário, posicione o cursor dentro da classe e insira o método a ser substituído.  
  
     Por exemplo, digite `public override` para ver uma lista de todos os métodos que podem ser substituídas na classe.  
  
## <a name="see-also"></a>Consulte também  
 [Implementar um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)