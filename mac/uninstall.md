---
title: Desinstalando o Visual Studio para Mac
description: Instruções para desinstalar o Visual Studio para Mac e as ferramentas relacionadas.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 14afeefac0bb5aa198b2f62ba00ba85831b23ffb
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2018
---
# <a name="uninstalling-visual-studio-for-mac"></a>Desinstalando o Visual Studio para Mac

Há uma série de produtos Xamarin que permitem desenvolver aplicativos de plataforma cruzada, incluindo aplicativos autônomos como o Visual Studio para Mac.

Este guia pode ser usado para desinstalar cada produto individualmente ao navegar até a seção relevante. O conjunto completo de ferramentas Xamarin pode ser desinstalado seguindo este guia até o fim.

Se você já teve o Xamarin Studio instalado em seu computador, também poderá ser necessário seguir as instruções do guia de [desinstalação](https://developer.xamarin.com/guides/cross-platform/getting_started/installation/uninstalling_xamarin/) em developer.xamarin.com além das etapas a seguir.

## <a name="uninstall-script"></a>Scripts de Desinstalação

Você pode desinstalar o Visual Studio e seus componentes associados de uma só vez usando o [script de desinstalação](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Esse script de desinstalação contém a maioria dos comandos que você encontrará no artigo. Há duas omissões principais do script que não estão incluídas devido a possíveis dependências externas:

- **Desinstalando Mono**
- **Desinstalando o Android AVD**

Para executar o script, execute as seguintes etapas:

1. Clique com botão direito do mouse no script e selecione **Salvar Como...** para salvar o arquivo no seu Mac.
2. Abra o Terminal e altere o diretório de trabalho para o local em que o script foi baixado:

    ```bash
    $ cd /location/of/file
    ```
3. Torne o script executável e execute-o com o **sudo**:

    ```bash
    $ chmod +x ./uninstall-vsmac.sh
    $ sudo ./uninstall-vsmac.sh
    ```
4. Por fim, exclua o script de desinstalação.

## <a name="uninstall-visual-studio-for-mac"></a>Desinstalar o Visual Studio para Mac

A primeira etapa da desinstalação do Visual Studio em um Mac é localizar **Visual Studio.app** no diretório **/Aplicativos** e arrastá-lo para a **Lixeira**. Como alternativa, clique com botão direito do mouse e selecione **Mover para Lixeira** conforme é ilustrado na imagem a seguir:

![Mova o aplicativo do Visual Studio para a lixeira](media/uninstall-image1.png)

Excluir esse pacote de aplicativo removerá o Visual Studio para Mac, no entanto, é possível que outros arquivos relacionados ao Xamarin ainda permaneçam em um sistema de arquivos.

Para remover todos os vestígios do Visual Studio para Mac, os comandos a seguir devem ser executados no Terminal:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

## <a name="uninstall-mono-sdk-mdk"></a>Desinstalar o SDK do Mono (MDK)

O Mono é uma implementação de software livre do .NET Framework da Microsoft usado por todos os Produtos Xamarin – Xamarin.iOS, Xamarin.Android e Xamarin.Mac para permitir o desenvolvimento dessas plataformas em C#.

> [!WARNING]
> Há outros aplicativos fora do Visual Studio para Mac que também usam o Mono, como o Unity.
> Certifique-se de que não há outras dependências no Mono antes de desinstalá-lo.

Para remover a Estrutura Mono de um computador, execute os seguintes comandos no Terminal:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Desinstalar o Xamarin.Android

Há um número de itens necessários para a instalação e o uso do Xamarin.Android, como o SDK do Android e o SDK do Java.

Use os comandos a seguir para remover o Xamarin.Android:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Desinstalar o SDK do Android e o SDK do Java

O SDK do Android é necessário para o desenvolvimento de aplicativos Android. Para remover completamente todas as partes do SDK do Android, localize o arquivo em **~/Library/Developer/Xamarin/** e mova-o para a **Lixeira**.

O SDK do Java (JDK) não precisa ser desinstalado, pois ele já é pré-empacotado como parte do Mac OS X / macOS.

### <a name="uninstall-android-avd"></a>Desinstalar o Android AVD

> [!WARNING]
> Há outros aplicativos fora do Visual Studio para Mac que também usam o Android AVD e esses componentes Android adicionais, como o Android Studio.
> Remover esse diretório pode causar falhas em projetos no Android Studio. 

Para remover os Android AVDs e componentes Android adicionais, use o seguinte comando:

```bash
rm -rf ~/.android
```

Para remover apenas o Android AVDs, use o seguinte comando:

```bash
rm -rf ~/.android/avd
```

 

## <a name="uninstall-xamarinios"></a>Desinstalar o Xamarin.iOS

O Xamarin.iOS permite desenvolver aplicativos iOS usando C# ou F# com o Visual Studio para Mac.

Use os seguintes comandos no Terminal para remover todos os arquivos do Xamarin.iOS de um sistema de arquivos:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Desinstalar o Xamarin.Mac

O Xamarin.Mac pode ser removido do seu computador usando os dois comandos a seguir para eliminar o produto e a licença do seu Mac, respectivamente:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Desinstalar o Workbooks e o Inspector

A partir do 1.2.2, o Xamarin Workbooks e Inspector podem ser desinstalados de um terminal executando:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Para as versões mais antigas, você precisa remover manualmente os seguintes artefatos:

* Exclua o aplicativo do Workbooks em `"/Applications/Xamarin Workbooks.app"`
* Exclua o aplicativo do Inspector em `"Applications/Xamarin Inspector.app"`
* Exclua os suplementos: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` e `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Exclua o Inspector e os arquivos de suporte aqui: `/Library/Frameworks/Xamarin.Interactive.framework` e `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Desinstale o Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Desinstale o Instalador do Visual Studio

Use os comandos a seguir para remover todos os vestígios do Instalador Universal do Xamarin:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```
