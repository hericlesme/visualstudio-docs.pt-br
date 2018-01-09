---
title: Gerenciador de pacotes nas Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: a78d79c9daaff7f5c371da6de0e290bd184c2fe0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="package-manager"></a>Gerenciador de pacotes

O gerenciador de pacotes das RTVS (Ferramentas do R para Visual Studio) é uma interface do usuário para gerenciar os pacotes R. Para abri-lo, selecione **Ferramentas do R > Janelas > Pacotes** ou pressione Ctrl + 7.

O gerenciador de pacotes tem três guias. Cada guia exibe uma lista de pacotes relevantes à esquerda e detalhes específicos para o pacote selecionado à direita, incluindo versão do pacote, descrição, licença, local de instalação e links para outras informações relevantes. Caixa de pesquisa no canto superior direito permite filtrar a lista.

> [!Tip]
> O termo na caixa de pesquisa permanece ao alternar entre as guias.

- **Disponível** permite procurar pacotes a serem instalados. Se o pacote já estiver instalado, o botão **Instalar** à direita será alterado para **Desinstalar**.

    ![Guia Pacotes disponíveis no gerenciador de pacotes das Ferramentas do R para Visual Studio](media/package-manager-available.png)

- **Instalado** mostra todos os pacotes instalados e carregados. Um ponto verde ao lado de um pacote indica que ele está carregado na sessão do R. O ícone de X vermelho na lista à esquerda ou o botão **Desinstalar** à direita pode ser usado para desinstalar o pacote. Se houver uma versão mais recente de um pacote instalado disponível, um azul a seta à direita do pacote executa a atualização.

    ![Guia Pacotes instalados no gerenciador de pacotes das Ferramentas do R para Visual Studio](media/package-manager-installed.png)

- **Carregado** exibe somente os pacotes que estão carregados na sessão do R, que são exibidos com um ponto verde. Você também pode desinstalar e atualizar pacotes aqui.

    ![Guia Pacotes carregados no gerenciador de pacotes das Ferramentas do R para Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Locais de pacote

Os pacotes são instalados nos seguintes locais:

- Os pacotes principais que vêm incluídos nas RTVS são instalados em `C:\Program Files\Microsoft\R Client\R_SERVER\library`
- Os pacotes adicionais são instalados em `%userprofile%\Documents\R\win-library\3.3`
