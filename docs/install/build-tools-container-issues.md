---
title: "Problemas conhecidos de contêineres | Microsoft Docs"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 75825d368d0098c466c44a23fa18ac1af7b06e64
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="known-issues-for-containers"></a>Problemas conhecidos de contêineres

Existem alguns problemas ao instalar o Visual Studio em um contêiner do Docker.

## <a name="windows-container"></a>Contêiner do Windows

Estes problemas conhecidos ocorrem quando as Ferramentas de Build do Visual Studio 2017 são instaladas em um contêiner do Windows.

* Não é possível instalar o Visual Studio em um contêiner com base na imagem microsoft/windowsservercore:10.0.14393.1593. Imagens marcadas com as versões mais antigas ou mais recentes do Windows devem funcionar.
* Não é possível instalar versões do SDK do Windows mais antigas que a 10.0.14393. A instalação de certos pacotes falha e as cargas de trabalho que dependem desses pacotes não funcionarão.
* É necessário passar `-m 2GB` (ou mais) ao compilar a imagem. Algumas cargas de trabalho exigem mais memória que o padrão de 1 GB quando instaladas.
* É necessário configurar o Docker para usar discos maiores que o padrão de 20 GB.
* Você deve passar `--norestart` na linha de comando. A partir dessa gravação, tentar reiniciar um contêiner do Windows dentro do contêiner retorna `ERROR_TOO_MANY_OPEN_FILES` para o host.

## <a name="build-tools-container"></a>Contêiner das Ferramentas de Build

Os problemas conhecidos a seguir podem ocorrer ao usar o contêiner das Ferramentas de Build. Para saber se os problemas foram corrigidos ou se existem outros problemas conhecidos, acesse https://developercommunity.visualstudio.com.

* O IntelliTrace pode não funcionar em [alguns cenários](https://github.com/Microsoft/vstest/issues/940) dentro de um contêiner.

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, consulte a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md) para obter dicas de solução de problemas. Além disso, você pode relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), no IDE do Visual Studio ou compartilhar uma sugestão conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579). É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas. Também é possível interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio) (exige uma conta do [GitHub](https://github.com/)).

## <a name="see-also"></a>Consulte também

* [Instalar ferramentas de build em um contêiner](build-tools-container.md)
* [Exemplo avançado para contêineres](advanced-build-tools-container.md)
