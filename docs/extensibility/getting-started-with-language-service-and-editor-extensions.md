---
title: Introdução ao serviço de linguagem e as extensões de Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 21
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5f7b7440ff2f42eba1d138872071d4e51d2402c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Introdução ao serviço de linguagem e extensões do Editor
Você pode usar extensões de editor para adicionar recursos de serviço de linguagem, como a estrutura de tópicos, correspondência de chaves, IntelliSense e lâmpadas para sua linguagem de programação ou a qualquer tipo de conteúdo. Você também pode personalizar a aparência e comportamento do editor do Visual Studio, por exemplo texto cores, margens, ornamentos e outros elementos visuais. Você também pode definir seu próprio tipo de conteúdo e especificar a aparência e o comportamento dos modos de exibição de texto no qual o conteúdo será exibido.  
  
 Para começar a escrever extensões de editor, use os modelos de projeto do editor que são instalados como parte do SDK do Visual Studio. O SDK do Visual Studio é um conjunto para download de ferramentas que facilitam a desenvolver extensões do Visual Studio, usando VSPackages ou usando o Managed Extensibility Framework (MEF).  
  
> [!NOTE]
>  Para obter mais informações sobre o SDK do Visual Studio, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
 É recomendável que você Aprenda sobre as tecnologias e os conceitos a seguir antes de escrever suas próprias extensões de editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>O Windows Presentation Foundation (WPF) e extensões do Editor  
 A interface do usuário do Visual Studio editor (UI) é implementada usando o Windows Presentation Foundation (WPF). O WPF fornece uma experiência visual e um modelo de programação consistente que separa os aspectos visuais do código da lógica de negócios. Quando você criar extensões de editor, você pode usar muitos recursos e elementos do WPF. Para obter mais informações, consulte [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>O Managed Extensibility Framework (MEF) e extensões do Editor  
 Editor do Visual Studio usa o Managed Extensibility Framework (MEF) para gerenciar seus componentes e extensões. O MEF também permite que os desenvolvedores mais facilmente criar extensões para um aplicativo host como o Visual Studio. Nessa estrutura, você define uma extensão de acordo com um contrato MEF e exportá-lo como uma parte do componente MEF. O aplicativo host gerencia as partes do componente, localizando-os, registrando-os e certificando-se de que eles serão aplicados ao contexto correto.  
  
> [!NOTE]
>  Para obter mais informações sobre o MEF no editor, consulte [Managed Extensibility Framework no Editor de](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Pontos de extensão do Editor do Visual Studio e extensões  
 Pontos de extensão do editor são partes de componente MEF que você pode personalizar e estender. Em alguns casos você estender o ponto de extensão implementando uma interface e exportá-lo junto com os metadados corretos. Em outros casos basta declarar uma extensão e exportá-lo como um tipo específico.  
  
 Esses são alguns dos tipos básicos de extensões do editor:  
  
-   Margens e barras de rolagem  
  
-   Marcas  
  
-   Adornos  
  
-   Opções  
  
-   IntelliSense  
  
 Para obter mais informações sobre pontos de extensão de editor, consulte [serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Implantando extensões de Editor  
 No Visual Studio, você pode implantar extensões de editor adicionando um arquivo de metadados chamado source.extension.vsixmanifest à solução, compilar a solução e, em seguida, adicionando uma cópia dos arquivos binários e o manifesto em uma pasta que é conhecida para o Visual Studio. O arquivo de manifesto define as informações básicas sobre a extensão (por exemplo, nome, autor, versão e tipo de conteúdo). Para obter mais informações sobre o arquivo de manifesto do VSIX e como implantar extensões, consulte [envio extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Quando você instala uma extensão em um computador, inclua os binários e manifesto em uma subpasta da pasta que é conhecida para o Visual Studio.  
  
> [!WARNING]
>  Você não precisa se preocupar sobre os detalhes de manifestos e locais de implantação se você usar um dos modelos de extensibilidade de editor que estão incluídos no Visual Studio. Os modelos contém tudo o que é necessário para registrar e implantar uma extensão.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Extensões em execução na instância Experimental  
 Você pode proteger a sua versão de trabalho do Visual Studio enquanto estiver desenvolvendo uma extensão, implantando-a na seguinte pasta experimental (no Windows Vista e Windows 7):  
  
 *% LOCALAPPDATA %*\VisualStudio\10.0Exp\Extensions\\*empresa*\\*ExtensionID*  
  
 onde *% LOCALAPPDATA %* é o nome do usuário conectado, *empresa* é o nome da empresa que possui a extensão, e *ExtensionID* é a ID da extensão.  
  
 Quando você implantar uma extensão para o local experimental, ele é executado no modo de depuração. Uma segunda instância do Visual Studio é iniciada e é denominada **Microsoft Visual Studio - instância Experimental**.  
  
## <a name="managing-extensions"></a>Gerenciamento de extensões  
 Extensões para o Visual Studio são listadas no **extensões e atualizações** (no **ferramentas** menu). Se você estiver testando uma extensão na instância experimental, ele é listado em **extensões e atualizações** na instância experimental, mas não está listado na instância de desenvolvimento.  
  
 Para obter mais informações, consulte [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Usando modelos para criar extensões de Editor  
 Você pode usar modelos de editor para criar extensões de MEF que personalizam classificadores, ornamentos e as margens. Há modelos para projetos c# e Visual Basic. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Você também pode usar o modelo de projeto do VSIX para criar extensões. Este modelo fornece apenas os elementos que são necessárias para implantar qualquer tipo de extensão e incluir o arquivo source.extension.vsixmanifest, as referências de assembly necessárias e um arquivo de projeto que inclui as tarefas de compilação que permitem que você implante o extensão. Para obter mais informações, consulte [modelo de projeto do VSIX](../extensibility/vsix-project-template.md).  
  
 Você também pode criar editor de componentes do MEF de uma extensão de pacote do Visual Studio. Consulte as instruções a seguir para obter detalhes:  
  
-   [Passo a passo: Usar um comando de Shell com uma extensão do editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Passo a passo: Usar uma chave de atalho com uma extensão do editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)