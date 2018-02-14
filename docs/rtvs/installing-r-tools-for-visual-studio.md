---
title: Instalando as Ferramentas do R para Visual Studio | Microsoft Docs
description: "Como instalar as Ferramentas do R para Visual Studio no Visual Studio 2017 e no Visual Studio 2015, incluindo instalações offline."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
dev_langs:
- R
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: c4ca5a7fea1a84c4f4a38396daebd3e01412d9d7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Como instalar as Ferramentas do R para Visual Studio

Neste artigo:

- [Versões do Visual Studio com suporte](#supported-versions-of-visual-studio)
- [Instalando as RTVS no Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Instalando as RTVS no Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Instalação offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Depois de instalar as Ferramentas do R, talvez você queira configurar o Visual Studio com um layout otimizado para cientista de dados, conforme descrito no artigo [Opções](options-for-r-tools-in-visual-studio.md).

## <a name="supported-versions-of-visual-studio"></a>Versões do Visual Studio com suporte

Há suporte para as RTVS (Ferramentas do R para Visual Studio) no Windows nas edições Enterprise, Professional e Community (gratuita) do [Visual Studio 2017](https://www.visualstudio.com/downloads/) e [Visual Studio 2015 Atualização 3 (ou superior)](http://go.microsoft.com/fwlink/?LinkId=691129) (download direto).

No momento, não há suporte para as RTVS no Visual Studio para Mac.

As RTVS não serão instaladas se você tiver somente o Shell do Visual Studio incluído com produtos como o Visual Studio Test Professional e o SQL Server Management Studio. O Shell do Visual Studio não tem os componentes necessários para as RTVS.

## <a name="installing-rtvs-in-visual-studio-2017"></a>Instalando as RTVS no Visual Studio 2017

1. Execute o instalador do Visual Studio. (Consulte [Downloads](https://www.visualstudio.com/downloads/) se você ainda não tiver o Visual Studio instalado.) No Windows 7, certifique-se de que o instalador está atualizado para mostrar a versão do Visual Studio *15.2 build 26430.12* ou posterior.

1. Selecione a carga de trabalho **Ciência de dados e aplicativos analíticos**:

    ![Carga de trabalho de ciência de dados e aplicativos analíticos no VS2017](media/installation-data-science-workload.png)

1. Defina quaisquer opções adicionais no lado direito, sob o mesmo nome de carga de trabalho. Por padrão, essa carga de trabalho inclui suporte a F# e Python. Para R, os requisitos mínimos são **Suporte à linguagem R**, **Suporte de tempo de execução para desenvolvimento em R** e **Microsoft R Client**.

As RTVS são instaladas em: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` em que `<version>` é normalmente `2017` e `<edition>` é `Community`, `Professional` ou `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Instalando as RTVS no Visual Studio 2015

Com o Visual Studio 2015, você precisa instalar um interpretador de R e as Ferramentas do R separadamente.

### <a name="install-an-r-interpreter"></a>Instalar um interpretador de R

As RTVS requerem uma instalação de 64 bits do R versão 3.2.1 ou posterior em uma ou mais das seguintes fontes:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

O Microsoft R Open e o CRAN R permitem várias versões lado a lado. O Microsoft R Client, no entanto, dá suporte a apenas uma versão e sempre usa a última que foi instalada.

### <a name="install-the-r-tools"></a>Instalar as Ferramentas R

Baixe as RTVS para Visual Studio 2015 em [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). As RTVS verificam se há uma versão adequada do Visual Studio e ajudam a instalar um interpretador de R, caso isso ainda não tenha sido feito.

> [!Note]
> O instalador autônomo das RTVS funciona apenas com o Visual Studio 2015; com o Visual Studio 2017, instale o suporte ao R por meio da [Carga de trabalho para Aplicativos de ciência de dados e análise](#installing-rtvs-in-visual-studio-2017) conforme descrito anteriormente.

As RTVS para Visual Studio 2015 estão instaladas em: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalação offline do Visual Studio e das RTVS

A instalação offline é adequada para computadores que não estão conectados à Internet:

1. Siga as instruções para criar um instalador offline para sua versão do Visual Studio: 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Para o Visual Studio 2015, baixe os instaladores das RTVS offline em [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) e em [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip). 

1. Instale o Visual Studio e as RTVS dos instaladores offline.

## <a name="see-also"></a>Consulte também

- [Introdução ao R](getting-started-with-r.md)
- [Projetos de exemplo das Ferramentas do R](getting-started-samples.md)
- [Obtendo ajuda](getting-started-help.md)
- [Configurações de opção](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (anteriormente conhecido como R Server)](/machine-learning-server/)