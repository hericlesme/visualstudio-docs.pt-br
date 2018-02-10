---
title: Instalar o SDK do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5a4721eea178e4a9ab5766760ccf1405589684
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="installing-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio
O SDK do Visual Studio é um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar o SDK do Visual Studio como parte de uma instalação do Visual Studio  
 Se você deseja incluir o VSSDK em sua instalação do Visual Studio, você deve instalar o **desenvolvimento de extensão do Visual Studio** cargas de trabalho em **outros conjuntos de ferramentas**. Isso irá instalar o SDK do Visual Studio, bem como os pré-requisitos necessários. Você pode ajustar a instalação selecionando ou desmarque componentes no resumo de exibição. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalando o SDK do Visual Studio depois de instalar o Visual Studio  
 Se você optar por instalar o SDK do Visual Studio depois de concluir a instalação do Visual Studio, execute novamente o instalador do Visual Studio e selecione o **desenvolvimento de extensão do Visual Studio** carga de trabalho.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar o SDK do Visual Studio de uma solução  
 Se você abrir uma solução com um projeto de extensibilidade sem precisar instalar primeiro o VSSDK, você será solicitado por uma barra de informações realçado acima do Gerenciador de soluções. Ele deve ser algo semelhante ao seguinte:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalando o SDK do Visual Studio a partir da linha de comando  
Assim como acontece com qualquer carga de trabalho do Visual Studio ou o componente, você também pode instalar o item da linha de comando. Consulte [usar parâmetros de linha de comando para instalar o Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obter detalhes sobre as opções de linha de comando apropriado e como determinar os identificadores de carga de trabalho ou componente.
  
 Observe que você deve usar o instalador do Visual Studio que corresponde à sua versão instalada do Visual Studio. Por exemplo, se você tiver o Visual Studio Enterprise instalada no computador, você deve executar o instalador do Visual Studio Enterprise (vs_enterprise.exe).