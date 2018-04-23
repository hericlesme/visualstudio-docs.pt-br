---
title: 'Passo a passo: Criando um Editor personalizado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc70112dc89a1866a4688fd39d8a2aae129387b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-editor"></a>Passo a passo: Criando um Editor personalizado
O modelo de projeto VSPackage pode criar um editor personalizado simple em C++.  O modelo de projeto VSPackage não suporta projetos c# ou Visual Basic. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Modelo de projeto de pacote do Visual Studio  
 O modelo de projeto de pacote do Visual Studio pode ser encontrado no **novo projeto** caixa de diálogo na pasta de extensibilidade do C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Para criar um VSPackage usando o modelo de pacote do Visual Studio  
  
1.  Crie um projeto com o modelo de pacote do Visual Studio.  
  
2.  Selecione o **Editor personalizado** opção e clique em **próximo**. O **opções do Editor de** página é exibida.  
  
3.  Digite o nome do seu editor no **nome do Editor** caixa. Digite a extensão de arquivo que você deseja estar associados ao seu editor no **extensão de arquivo** caixa. O editor está disponível para arquivos com esta extensão. A extensão de arquivo é registrada para o Visual Studio apenas, não para o Windows. Digite o nome de arquivo padrão para novos documentos criados com o editor no **nome de arquivo padrão** caixa.  
  
4.  Clique em **concluir** para criar o VSPackage na pasta que você especificou.  
  
### <a name="to-test-your-custom-editor"></a>Para testar seu editor personalizado  
  
1.  Sobre o **arquivo** , aponte para **novo** e, em seguida, clique em **arquivo**.  
  
2.  No **modelos instalados** painel do **novo arquivo** caixa de diálogo, selecione o modelo de arquivo, em seguida, o arquivo de tipo que você acabou de registrar.  
  
3.  Clique em **abrir** para exibir e editar o documento.  
  
     O editor oferece suporte a operações de recortar e colar, localizar e substituir e abra e de carga.  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)