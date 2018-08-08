---
title: Como abrir várias soluções
description: Saiba como abrir mais de uma solução no Visual Studio para Mac e como abrir mais de uma instância do aplicativo.
author: asb3993
ms.author: amburns
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 85d300c5131dad2d6f4480fceb4770e2e8a126a5
ms.sourcegitcommit: b544e2157ac20866baf158eef9cfed3e3f1d68b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388488"
---
# <a name="opening-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Abrindo várias soluções ou instâncias do Visual Studio para Mac

Por padrão, todos os aplicativos de um Mac, incluindo o Visual Studio para Mac, são aplicativos de _instância única_. Isso significa que se o aplicativo que você deseja usar já estiver aberto (ilustrado por um "ponto" sob o ícone no encaixe), clicar no ícone novamente abrirá a instância em execução, em vez de uma nova.  Caso precise de instâncias adicionais do aplicativo, solicite ao sistema para abri-las para você, conforme descrito na [próxima seção](#open-a-second-instance-of-visual-studio-for-mac).

Além disso, quando você abre uma solução, o comportamento padrão é abrir a solução em um novo espaço de trabalho e fechar o espaço de trabalho atual (se necessário). Substitua esse comportamento padrão mantendo o espaço de trabalho atual aberto, conforme descrito na seção [Abrir uma segunda solução](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Abrir uma segunda instância do Visual Studio para Mac

Para abrir uma segunda instância do IDE, abra o aplicativo **Terminal** e insira a seguinte linha:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Abrir uma segunda solução dentro de uma instância única

Para abrir uma segunda solução junto com a primeira solução, use as seguintes etapas:

1. Com sua primeira solução já aberta, selecione **Arquivo > Abrir**.
2. Navegue pelo sistema de arquivos para encontrar a solução existente.
3. Selecione o arquivo **.sln** e pressione o botão **Opções**:
    
    ![local do botão de opções](media/open-multiple-solutions-image3.png)
4. Desmarque a caixa **Fechar espaço de trabalho atual**:

    ![captura de tela do espaço de trabalho atual](media/open-multiple-solutions-image1.png)

1. Pressione o botão Abrir para abrir a segunda solução no Painel de Soluções.

**Como alternativa**, se você abriu a solução recentemente, use as seguintes etapas:

1. Acesse o item de menu Arquivo > Soluções Recentes:

    ![captura de tela do menu de Soluções Recentes](media/open-multiple-solutions-image2.png)

1. Mantenha a tecla **Ctrl** pressionada e selecione a solução. Essa combinação abre a segunda Solução no Painel de Soluções.
