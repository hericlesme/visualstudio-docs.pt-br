---
title: Instalar o Xamarin para Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 4dcd83ffb1076211f8d23aa4491f853d2b7d316f
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2018
---
# <a name="setup-and-install"></a>Instalar e configurar

Para criar aplicativos nativos do iOS, do Android e do Windows com uma base de código C#/.NET comum usando o Xamarin, você precisará dos seguintes hardwares e softwares:

-   Para trabalhar com aplicativos Windows e Android: um computador Windows de desenvolvimento (não uma máquina virtual) com o Visual Studio 2017 instalado (incluindo os recursos de desenvolvimento do Xamarin).  

-   Para trabalhar com aplicativos iOS: um Mac com o macOS Serra 10.12 ou acima, com o Xcode e o Visual Studio para Mac instalados.

Não é necessário ter licenças separadas para usar a plataforma Xamarin.
 
Você poderá configurar os computadores Windows e Mac ao mesmo tempo e, enquanto os instaladores estiverem em execução, poderá analisar [Saiba mais sobre desenvolvimento móvel com Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) para ler e inspecionar o material básico necessário.

Se você tiver problemas para usar a plataforma Xamarin depois de realizar essa instalação e configuração, poste sua pergunta em [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" /> 

## <a name="pre-requisites"></a>Pré-requisitos

###  <a name="for-targeting-windows-and-android"></a>Para direcionamento ao Windows e ao Android

Confira [Requisitos de sistema da família de produtos do Visual Studio 2017](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs) para saber quais são os pré-requisitos detalhados para instalar o Visual Studio 2017.

Instale o Visual 2017 em um computador Windows físico (não em uma máquina virtual) que execute o Windows 10 com todas as atualizações instaladas. 

### <a name="for-targeting-ios"></a>Para direcionamento ao iOS

Para direcionar a emuladores e dispositivos iOS usando o computador Windows, você também precisará de um Mac ou um Mac mini em rede que execute o macOS 10.12 ou posterior e o Xcode 8.3. Confira [Instalar e configurar o Visual Studio para Mac](/visualstudio/mac/installation.md) para obter requisitos mais detalhados.

<a name="windows" /> 

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Instalação do Windows (Visual Studio e Xamarin)

Se você ainda não instalou o Visual Studio 2017, siga as etapas a seguir:

1.  [Baixe e inicie o instalador para qualquer edição do Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional ou Enterprise). O Visual Studio 2017 Community é a edição gratuita. As edições Professional e Enterprise estão disponíveis para uma avaliação de 30 dias e, em seguida, passam a exigir uma licença.

2.  Quando a caixa de diálogo **Instalando** for exibida, marque as seguintes caixas:    

    - **Celular e Jogos > Desenvolvimento Móvel com o .NET**. Essa opção também selecionará automaticamente diversas ferramentas e Software Development Kits do Android. 

        ![Selecione a opção Desenvolvimento Móvel em Jogos e Desenvolvimento Móvel](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Instalação 2 entre várias plataformas do Xamarin")

    - (Opcional) **Windows > Desenvolvimento da Plataforma Universal do Windows**. 

Se o Visual Studio 2017 já estiver instalado, mas a plataforma Xamarin ainda não, siga as etapas a seguir:

1. Execute o **Instalador do Visual Studio** pelo menu **Iniciar**.

2.  No instalador, clique no botão **Mais** e escolha **Modificar**:

    ![Como escolher a opção Modificar na instalação do Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Instalação 1 entre várias plataformas do Xamarin")

3.  Quando a caixa de diálogo **Instalando** for exibida, marque **Móvel e Jogos > Desenvolvimento Móvel com o .NET** e (opcionalmente) **Windows > Desenvolvimento na Plataforma Universal do Windows**. A opção **Desenvolvimento móvel com .NET** também deve atualizar as instalações existentes do Xamarin.

Enquanto a instalação estiver em execução, você poderá continuar com as instruções de instalação do Mac e ler [Saiba mais sobre desenvolvimento móvel com Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Após a conclusão da instalação, inicie o Visual Studio e entre com sua conta da Microsoft, se solicitado. Essa conta é a mesma que você usa com o Windows.

6.  Para testar aplicativos Android, use o [Emulador do SDK do Android](/xamarin/android/get-started/installation/android-emulator/) caso não tenha um dispositivo Android físico. 

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Configuração do Mac (ID Apple, Xcode e Xamarin)

1.  Crie uma ID Apple gratuita em [https://appleid.apple.com](https://appleid.apple.com/) se você ainda não tiver uma. Essa ID Apple é necessária para instalar e entrar no Xcode.

2.  Baixe e instale o Xcode de [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) e adicione o ID Apple, conforme descrito em [Adding Your Account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Adicionar sua conta no Xcode) (apple.com).

3.  Baixe e instale o Visual Studio para Mac, seguindo as instruções em [Instalar e configurar o Visual Studio para Mac](/visualstudio/mac/installation.md).

4.  Depois de concluir a instalação do Xamarin nos computadores Windows e Mac, siga as instruções em [Conectando-se ao Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) para que você possa trabalhar com o iOS e o Mac usando Visual Studio no computador Windows.

Ambos os computadores precisam estar na mesma rede local.