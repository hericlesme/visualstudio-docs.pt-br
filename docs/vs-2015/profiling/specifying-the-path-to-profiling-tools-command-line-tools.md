---
title: Especificando o caminho para ferramentas de linha de comando de ferramentas de criação de perfil | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ccf7739a8efacacec3c48b47a59d6db6f6e8de8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462822"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Especificando o demarcador para ferramentas de linha de comando de ferramentas de criação de perfil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [especificando o caminho para ferramentas de linha de comando de ferramentas de criação de perfil](https://docs.microsoft.com/visualstudio/profiling/specifying-the-path-to-profiling-tools-command-line-tools).  
  
O caminho das ferramentas de linha de comando das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] não é adicionado à variável de ambiente PATH. Em computadores de 32 bits, as ferramentas permanecem em um único diretório. Existem versões de 32 e 64 bits das ferramentas de criação de perfil em computadores de 64 bits.  
  
## <a name="32-bit-computers"></a>Computadores 32 bits  
 Em computadores de 32 bits, o diretório das ferramentas de criador de perfil padrão é *Unidade*Arquivos de Programas\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Computadores de 64 bits  
 Em computadores de 64 bits, especifique o caminho de acordo com a plataforma de destino do aplicativo cujo perfil foi criado.  
  
-   No caso de aplicativos de 32 bits, o diretório padrão das ferramentas de criação de perfil é:  
  
     *Unidade*Arquivos de Programas (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   No caso de aplicativos de 64 bits, o diretório padrão das ferramentas de criação de perfil é:  
  
     *Unidade*\Arquivos de Programas (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64



