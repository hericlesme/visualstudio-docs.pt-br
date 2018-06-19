---
title: Instalar o SDK do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 259646e0dbee4831db83a7098954d1c5144d8ead
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129059"
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
Como com qualquer carga de trabalho do Visual Studio ou o componente, você também pode instalar o **desenvolvimento de extensão do Visual Studio** cargas de trabalho (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) na linha de comando. Consulte [usar parâmetros de linha de comando para instalar o Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obter detalhes sobre as opções de linha de comando apropriada e instruções gerais sobre como determinar a carga de trabalho ou componente identificadores.
  
 Observe que você deve usar o instalador do Visual Studio que corresponde à sua versão instalada do Visual Studio. Por exemplo, se você tiver o Visual Studio Enterprise instalada no computador, você deve executar o instalador do Visual Studio Enterprise (vs_enterprise.exe).