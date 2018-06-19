---
title: Problemas conhecidos de contêineres
description: Saiba mais sobre os problemas conhecidos que podem ocorrer quando as Ferramentas de Build do Visual Studio 2017 são instaladas em um contêiner do Windows.
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b33bae8474e2ed047766d8c749b088216820f095
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
ms.locfileid: "31620242"
---
# <a name="known-issues-for-containers"></a>Problemas conhecidos de contêineres

Há alguns problemas ao instalar o Visual Studio em um contêiner do Docker.

## <a name="windows-container"></a>Contêiner do Windows

Estes problemas conhecidos ocorrem quando as Ferramentas de Build do Visual Studio 2017 são instaladas em um contêiner do Windows.

* Não é possível instalar o Visual Studio em um contêiner com base na imagem microsoft/windowsservercore:10.0.14393.1593. Imagens marcadas com as versões mais antigas ou mais recentes do Windows devem funcionar.
* Não é possível instalar versões do SDK do Windows mais antigas que a 10.0.14393. A instalação de certos pacotes falha e as cargas de trabalho que dependem desses pacotes não funcionarão.
* Passe `-m 2GB` (ou mais) ao compilar a imagem. Algumas cargas de trabalho exigem mais memória que o padrão de 1 GB quando instaladas.
* Configure o Docker para usar discos maiores que o padrão de 20 GB.
* Passe `--norestart` na linha de comando. A partir dessa gravação, tentar reiniciar um contêiner do Windows dentro do contêiner retorna `ERROR_TOO_MANY_OPEN_FILES` para o host.
* Se você basear sua imagem diretamente no microsoft/windowsservercore, o .NET Framework poderá não ser instalado corretamente e nenhum erro de instalação será indicado. Código gerenciado não poderá ser executado depois que a instalação for concluída. Em vez disso, baseie sua imagem no [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) ou mais recente. Por exemplo, você poderá ver um erro ao compilar com o MSBuild, como:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): erro MSB6003: Não foi possível executar o executável da tarefa especificado "csc.exe". Não foi possível carregar o arquivo ou assembly “System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" ou uma de suas dependências. O sistema não pode encontrar o arquivo especificado.

## <a name="build-tools-container"></a>Contêiner das Ferramentas de Build

Os problemas conhecidos a seguir podem ocorrer ao usar o contêiner das Ferramentas de Build. Para ver se os problemas foram corrigidos ou se há outros problemas conhecidos, visite https://developercommunity.visualstudio.com.

* O IntelliTrace pode não funcionar em [alguns cenários](https://github.com/Microsoft/vstest/issues/940) dentro de um contêiner.

## <a name="get-support"></a>Obter suporte

Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:

* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Você pode acompanhar os problemas do produto e encontrar respostas na [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) (Comunidade de desenvolvedores do Visual Studio).
* Também é possível interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também

* [Instalar ferramentas de build em um contêiner](build-tools-container.md)
* [Exemplo avançado para contêineres](advanced-build-tools-container.md)
* [IDs de carga de trabalho e de componente das Ferramentas de Build do Visual Studio 2017](workload-component-id-vs-build-tools.md)
