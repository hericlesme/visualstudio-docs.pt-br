---
title: Instalar em ambientes de rede não confiável ou de baixa largura de banda | Microsoft Docs
description: Saiba como usar o instalador do Visual Studio quando sua rede não for confiável ou quando você tiver pouca largura de banda, bem como usar a linha de comando para fazer baixar os arquivos de instalação.
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: b273efb06e7b2e70617d28dcafc85735bcfb1fd1
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138794"
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Instalar o Visual Studio 2017 em ambientes de rede não confiável ou de baixa largura de banda

Recomendamos que você experimente o novo instalador da Web do Visual Studio&mdash;, pois acreditamos que ele lhe proporcionará uma boa experiência na maioria das situações.

 > [!div class="button"]
 > [Baixe o Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

No entanto, se sua conexão de Internet não está disponível ou não é confiável, é possível usar a linha de comando para criar um cache local dos arquivos necessários para concluir uma instalação offline. Veja como.

> [!NOTE]
> Se você for um administrador de empresas que deseja executar uma implantação do Visual Studio 2017 em uma rede de estações de trabalho cliente protegidas da Internet por firewall, confira nossas páginas [Criar uma instalação de rede do Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Instalar os certificados necessários para a instalação offline do Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Etapa 1 – Baixar o bootstrapper do Visual Studio

Comece baixando o bootstrapper do Visual Studio para sua edição do Visual Studio escolhida.

O arquivo de instalação &mdash; ou para ser mais específico, um arquivo bootstrapper &mdash; corresponderá ou será semelhante a um dos listados a seguir.

| Edição                    | Arquivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Comunidade Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Etapa 2 – Criar um cache local de instalação

É preciso ter uma conexão com a Internet para concluir esta etapa. Para criar um layout local, abra um prompt de comando e use um dos comandos dos exemplos a seguir. Estes exemplos supõem que você esteja usando a edição Community do Visual Studio; ajuste o comando conforme apropriado para sua edição.

- Para .NET Web e desenvolvimento de área de trabalho do .NET, execute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Para a área de trabalho do .NET e o desenvolvimento do Office, execute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Para desenvolvimento do C++ da área de trabalho, execute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Para criar um layout de local completo com todos os recursos (isso levará algum tempo&mdash;, pois temos _muitos_ recursos!), execute:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Se você quiser instalar um idioma diferente do inglês, altere `en-US` para uma localidade da lista na parte inferior desta página. Use esta [lista de componentes e cargas de trabalho disponíveis](workload-and-component-ids.md) para personalizar ainda mais o cache de instalação conforme necessário.

> [!IMPORTANT]
> Um layout completo do Visual Studio 2017 exige, pelo menos, 35 GB de espaço em disco e pode demorar um pouco para ser baixado. Consulte [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) para saber mais sobre como criar um layout apenas com os componentes que você deseja instalar.

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>Etapa 3 – Instalar o Visual Studio do cache local

> [!TIP]
> Ao executar de um cache local de instalação, usaremos as versões locais de cada um desses arquivos. Porém, se você selecionar componentes que não estão no cache durante a instalação, tentaremos baixá-los da Internet.

Para garantir que você instale somente os arquivos que baixou, use as mesmas opções de linha de comando que usou para criar o cache de layout. Por exemplo, se você tiver criado um cache de layout com o seguinte comando:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Use este comando para executar a instalação:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Caso ocorra um erro indicando que a assinatura é inválida, será necessário instalar certificados atualizados. Abra a pasta Certificados no cache offline. Clique duas vezes em cada um dos arquivos de certificado e, em seguida, clique no assistente do Gerenciador de Certificados. Se for solicitado a fornecer uma senha, deixe-a em branco.

## <a name="list-of-language-locales"></a>Lista de localidades de idioma

| **Localidade de idioma** | **Linguagem** |
| ----------------------- | --------------- |
| cs-CZ | Tcheco |
| de-DE | Alemão |
| en-US | Inglês |
| es-ES | Espanhol |
| fr-FR | Francês |
| it-IT | Italiano |
| ja-JP | Japonês |
| ko-KR | Coreano |
| pl-PL | Polonês |
| pt-BR | Português - Brasil |
| ru-RU | Russo |
| tr-TR | Turco |
| zh-CN | Chinês – Simplificado |
| zh-TW | Chinês – Tradicional |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [IDs de carga de trabalho e de componente do Visual Studio 2017](workload-and-component-ids.md)
