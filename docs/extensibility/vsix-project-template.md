---
title: Modelo de projeto do VSIX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24a2937b37aa339f85e197f6ff2bb49cbb0ce86f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-project-template"></a>Modelo de projeto do VSIX
Você pode usar o modelo de projeto do VSIX para incluir uma ou mais extensões do Visual Studio em um projeto do VSIX e, em seguida, publique o pacote no [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web.  
  
 Dá suporte à implantação do VSIX VSPackages, assemblies, componentes MEF, modelos de projeto, modelos de item, controles de caixa de ferramentas e tipos de extensão personalizada.  
  
> [!NOTE]
>  Para usar projetos do VSIX, você deve instalar o SDK do Visual Studio. Para obter mais informações sobre o SDK do Visual Studio, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Onde encontrar o modelo de projeto do VSIX  
 O modelo de projeto do VSIX está disponível na **novo projeto** caixa de diálogo. Expanda o **Visual Basic** nó ou o **Visual C#** nó e, em seguida, escolha **extensibilidade**.  
  
> [!TIP]
>  Assegure-se de que o .NET Framework 4.5 ou superior é especificado na lista suspensa na parte superior do **novo projeto** caixa de diálogo.  
  
## <a name="uses-of-the-vsix-project-template"></a>Usos do modelo de projeto do VSIX  
 O modelo de projeto do VSIX tem dois usos principais:  
  
-   Para implantar modelos de projeto, modelos de item e outras extensões que não têm suporte do VSIX.  
  
-   Para incluir as saídas de várias extensões para o pacote de implantação de um.  
  
 Você não precisa usar o modelo de projeto do VSIX para implantar VSPackages ou outros tipos de extensões que tenham VSIX suporte.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empacotando uma extensão em um projeto do VSIX vazio  
 Você pode empacotar uma extensão existente ou uma extensão que não tenham VSIX suporte, encapsulando-os em um projeto vazio do VSIX. A extensão a ser encapsulado deve ser de um tipo que é compatível com o [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empacotar uma extensão usando um projeto do VSIX  
  
1.  Crie os projetos que compõem a sua extensão.  
  
2.  Criar um projeto do VSIX usando o **projeto VSIX** modelo.  
  
     Source.Extension.vsixmanifest é aberto em **Designer de manifesto**.  
  
3.  Sobre o **ativos** guia, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
4.  No **tipo** , escolha o tipo de extensão para adicionar.  
  
5.  Para adicionar um elemento de extensão ou conteúdo que está incluído na solução atual (por exemplo, um modelo de item ou um assembly compilado), execute as seguintes etapas:  
  
    1.  No **fonte** , escolha **um projeto na solução atual**.  
  
    2.  No **projeto** , escolha o nome da extensão.  
  
    3.  No **inserir nesta pasta** , digite o nome de uma pasta na qual inserir o ativo e, em seguida, escolha o **Okey** botão.  
  
6.  Para adicionar uma extensão ou um elemento de conteúdo que não está incluído na solução atual, execute as seguintes etapas:  
  
    1.  No **fonte** caixa de listagem, escolha **arquivo no sistema de arquivos**.  
  
    2.  No **caminho** campo, digite o caminho completo para o arquivo de extensão compilado ou compactado ou use o **procurar** botão para procurar o arquivo.  
  
    3.  No **inserir nesta pasta** , digite o nome de uma pasta na qual inserir o ativo e, em seguida, escolha o **Okey** botão.  
  
7.  Se você desejar que seu pacote para incluir extensões adicionais, você deve adicioná-los da mesma maneira.  
  
8.  Compile a solução.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]cria um arquivo de .vsix que contém um arquivo de manifesto do VSIX, um arquivo. XML de [Content_Types] e todos os ativos de extensão que você adicionou ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema 2.0 de extensão do VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)