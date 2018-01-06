---
title: "Guia de Introdução com o modelo de projeto do VSIX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c87fd485a0d682dc21de21dfe32b83cfc29b520a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-the-vsix-project-template"></a>Guia de Introdução com o modelo de projeto do VSIX
Você pode usar o modelo de projeto do VSIX para criar uma extensão ou para uma extensão existente para a implantação do pacote. O modelo de projeto do VSIX tem versões do Visual Basic e Visual c# e é instalado como parte do SDK do Visual Studio.  
  
 O modelo de projeto do VSIX apenas consiste em um arquivo de source.extension.vsixmanifest, que contém informações sobre a extensão e os ativos de que enviá-lo.  
  
 Para localizar o modelo de projeto do VSIX, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Implantando um modelo de projeto personalizado usando o modelo de projeto do VSIX  
 As etapas a seguir mostram como usar o projeto do VSIX para empacotar um modelo de projeto que você pode compartilhar com outros desenvolvedores ou carregar a Galeria do Visual Studio.  
  
1.  Crie um modelo de projeto.  
  
    1.  Abra o projeto do qual criar um modelo. Este projeto pode ser de qualquer tipo de projeto.  
  
    2.  No menu **Projeto**, clique em **Exportar Modelo**. Conclua as etapas do assistente.  
  
         Um arquivo. zip é criado no %USERPROFILE%\My Documentos\Visual Studio  *\<versão >*\My exportado modelos\\.  
  
2.  Crie um projeto vazio do VSIX.  
  
     Sobre o **arquivo** menu, clique em **novo** e, em seguida, clique em **projeto**. Selecione **Visual Basic** ou **Visual C#**. Sob o nó selecionado, selecione **extensibilidade**e, em seguida, selecione **projeto VSIX**.  
  
3.  Adicione o arquivo. zip para o projeto. Definir seu **copiar para diretório de saída** propriedade `Copy Always`.  
  
4.  No **Solution Explorer**, clique duas vezes o `source.extension.vsixmanifest` arquivo para abri-lo no **Designer de manifesto do VSIX**e, em seguida, faça as seguintes alterações:  
  
    -   Definir o **nome do produto** campo **meu modelo de projeto**.  
  
    -   Definir o **ID de produto** campo **MyProjectTemplate - 1**.  
  
    -   Definir o **autor** campo **Fabrikam**.  
  
    -   Definir o **descrição** campo **meu modelo de projeto**.  
  
    -   No **ativos** seção, adicione um **Microsoft.VisualStudio.ProjectTemplate** digite e definir o caminho para o nome do arquivo. zip.  
  
5.  Salve e feche o arquivo source.extension.vsixmanifest.  
  
6.  Compile o projeto.  
  
7.  No diretório de saída, clique duas vezes no arquivo .vsix.  
  
8.  Um **instalador VSIX** caixa de mensagem aparece. Siga as instruções para instalar a extensão.  
  
9. Feche o Visual Studio e, em seguida, abra-o novamente.  
  
10. Selecione **extensões e atualizações** (no **ferramentas** menu) e selecione o **modelos** categoria. Uma das extensões disponíveis deve ser **meu modelo de projeto**.  
  
11. O novo modelo de projeto aparece no **novo projeto** caixa de diálogo no mesmo local que o modelo de projeto original. Por exemplo, se você tiver criado um modelo chamado **VB Console** de um aplicativo de console do Visual Basic, **VB Console** aparece no painel mesmo como o Visual Basic **aplicativo de Console**modelo.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Para especificar o local do modelo na caixa de diálogo Novo projeto  
  
1.  Pastas de modelo estão localizadas no *caminho de instalação do Visual Studio*\Common7\IDE\ProjectTemplates e *caminho de instalação do Visual Studio*\Common7\IDE\ItemTemplates diretórios. Os nomes das seções de nível superior na caixa de diálogo Novo projeto não exatamente corresponder aos nomes das pastas de modelo. Quando eles forem diferentes, use o nome da pasta do modelo.  
  
     Altere a extensão de arquivo .vsix para. zip e, em seguida, abra o arquivo.  
  
2.  Crie uma nova pasta com o mesmo nome que a seção da caixa de diálogo Novo projeto que de modelo deve aparecer no.  
  
3.  Se o modelo deve aparecer em uma subseção, crie uma subpasta de mesmo nome.  
  
4.  Mova o arquivo. zip de modelo para a nova pasta.  
  
5.  Altere a extensão. zip para .vsix.  
  
6.  Abra o manifesto do VSIX.  
  
7.  No manifesto do VSIX, atualize o **ativo** caminho do modelo para que ele aponte para a raiz da árvore de diretório que contém o arquivo de modelo. Por exemplo, se o modelo estiver em \CSharp\Windows, a referência deve apontar para \CSharp.