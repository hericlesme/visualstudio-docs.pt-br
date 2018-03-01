---
title: 'Passo a passo: Exibindo a Ajuda de assinatura | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ced0eb5d3545a75ee31cff55d0e4fb9dab8c8bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-signature-help"></a>Passo a passo: Exibindo a Ajuda de assinatura
Ajuda da assinatura (também conhecido como *informações de parâmetro*) exibe a assinatura de um método em uma dica de ferramenta quando um usuário digita o caractere de início da lista de parâmetro (normalmente um parêntese de abertura). Como um parâmetro e o separador de parâmetro (geralmente uma vírgula) são digitados, a dica de ferramenta é atualizada para mostrar o próximo parâmetro em negrito. Você pode definir a assinatura ajuda no contexto de um serviço de idioma, você pode definir seu próprio tipo de conteúdo e a extensão de nome do arquivo e exibir a Ajuda de assinatura para esse tipo de apenas, ou você pode exibir a Ajuda de assinatura para um tipo de conteúdo existente (por exemplo, "texto"). Este passo a passo mostra como exibir a Ajuda de assinatura para o tipo de conteúdo "texto".  
  
 Ajuda da assinatura normalmente é disparada, digitando um caractere específico, por exemplo, "(" (parêntese de abertura) e será descartada digitando outro caractere, por exemplo, ")" (parêntese de fechamento). Recursos do IntelliSense que são disparados, digitando um caractere podem ser implementados usando um manipulador de comandos para os pressionamentos de teclas (o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) e um provedor do manipulador que implementa o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Para criar a fonte de ajuda de assinatura, que é a lista de assinaturas que participam de ajudar a assinatura, implementar a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interface e um provedor de origem que implementa o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interface. Os provedores são partes de componente do Managed Extensibility Framework (MEF) e é responsáveis para as classes de origem e o controlador de exportação e importação serviços e agentes, por exemplo, o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite que você navegue no buffer de texto e o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, que aciona a sessão de ajuda de assinatura.  
  
 Este passo a passo mostra como implementar a assinatura ajuda para um conjunto embutida de identificadores. Em implementações completas, o idioma é responsável por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual C# / extensibilidade**, em seguida, **projeto VSIX**.) Nome da solução `SignatureHelpTest`.  
  
2.  Adicione um modelo de item de classificação de Editor para o projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existente.  
  
4.  Adicione as seguintes referências ao projeto e certifique-se de **CopyLocal** é definido como `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementando a assinatura ajuda a assinaturas e parâmetros  
 A origem de assinatura ajuda se baseia em assinaturas que implementam <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, cada uma delas contém parâmetros que implementam <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Em uma implantação completa, essas informações seriam ser obtidas na documentação do idioma, mas nesse exemplo, as assinaturas são codificados.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar a assinatura ajuda assinaturas e os parâmetros  
  
1.  Adicione um arquivo de classe e denomine- `SignatureHelpSource`.  
  
2.  Adicione a seguir importa.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Adicione uma classe denominada `TestParameter` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Adicione um construtor que define todas as propriedades.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Adicione as propriedades de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Adicione uma classe denominada `TestSignature` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Adicione alguns campos particulares.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Adicione um construtor que define os campos e assina o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Declarar um `CurrentParameterChanged` eventos. Esse evento é gerado quando o usuário preenche um dos parâmetros na assinatura.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propriedade para que ele gera o `CurrentParameterChanged` evento quando o valor da propriedade é alterado.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Adicione um método que gera o `CurrentParameterChanged` evento.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Adicione um método que calcula o parâmetro atual, comparando o número de vírgulas no <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> para o número de vírgulas na assinatura.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Adicionar um manipulador de eventos para o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento que chama o `ComputeCurrentParameter()` método.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implemente a propriedade <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Esta propriedade contém um <xref:Microsoft.VisualStudio.Text.ITrackingSpan> que corresponde ao trecho de texto no buffer ao qual se aplica a assinatura.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implemente os outros parâmetros.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementando a origem de ajuda de assinatura  
 A fonte de ajudar a assinatura é o conjunto de assinaturas para o qual você pode fornecer informações.  
  
#### <a name="to-implement-the-signature-help-source"></a>Para implementar a fonte de ajuda de assinatura  
  
1.  Adicione uma classe denominada `TestSignatureHelpSource` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Adicione uma referência para o buffer de texto.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Adicione um construtor que define o buffer de texto e o provedor de origem ajuda de assinatura.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> . Neste exemplo, as assinaturas são codificados, mas uma implantação completa, você obteria essas informações na documentação do idioma.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  O método auxiliar `CreateSignature()` é fornecido apenas para ilustração.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> . Neste exemplo, há apenas duas assinaturas, cada um deles tem dois parâmetros. Portanto, esse método não é necessário. Em uma implementação mais completa, em que mais de uma fonte de assinatura ajuda estiver disponível, esse método é usado para decidir se a origem de assinatura ajudar a prioridade mais alta pode fornecer uma assinatura correspondente. Caso contrário, o método retornará nulo e a origem do próximo maior prioridade é solicitada a fornecer uma correspondência.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implemente o método Dispose ():  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementando o provedor de origem de ajuda de assinatura  
 O provedor de origem ajudar a assinatura é responsável para exportar a parte do componente Managed Extensibility Framework (MEF) e para criar uma instância de fonte de ajuda de assinatura.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar o provedor de origem ajuda de assinatura  
  
1.  Adicione uma classe denominada `TestSignatureHelpSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto" e um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes = "padrão".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> instanciando a `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>Implementar o manipulador de comandos  
 Ajuda da assinatura é normalmente disparada por um (caractere e ignorado por um) caracteres. Você pode manipular esses pressionamentos de tecla implementando um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para que ele dispara uma sessão de ajuda de assinatura quando ele recebe um (caractere precedido de um nome de método conhecidos e descarta a sessão quando ele recebe um) caracteres.  
  
#### <a name="to-implement-the-command-handler"></a>Para implementar o manipulador de comandos  
  
1.  Adicione uma classe denominada `TestSignatureHelpCommand` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Adicionar campos privados para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador (que permite que você adicione o manipulador de comandos para os manipuladores de cadeia de comando), a exibição de texto, o agente de assinatura ajuda e a sessão, um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>e a próxima <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Adicione um construtor para inicializar esses campos e adicionar o filtro de comando para os filtros de cadeia de comando.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para disparar a sessão de ajuda de assinatura quando o filtro de comando recebe um (caractere depois que um dos nomes de método conhecidos e para ignorar a sessão quando ele recebe um) caractere enquanto a sessão ainda está ativa. Em cada caso, o comando é encaminhado.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para que ele sempre encaminhe o comando.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementando o provedor de comando de ajuda de assinatura  
 Você pode fornecer o comando Help assinatura Implementando o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para instanciar o manipulador de comando quando o modo de texto é criado.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar o provedor de comando Ajuda de assinatura  
  
1.  Adicione uma classe denominada `TestSignatureHelpController` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> e exportá-lo com o <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importar o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (usado para obter o <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, devido a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto), o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (usado para localizar a palavra atual) e o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (para disparar a sessão de ajuda de assinatura).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método instanciando a `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, compile a solução SignatureHelpTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para compilar e testar a solução SignatureHelpTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e tipo de texto que inclui a palavra "Adicionar" Além de um parêntese de abertura.  
  
4.  Depois de digitar o parêntese de abertura, você deve ver uma dica de ferramenta que exibe uma lista de duas assinaturas para o `add()` método.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)