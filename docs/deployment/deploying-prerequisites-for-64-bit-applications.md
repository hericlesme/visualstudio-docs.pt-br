---
title: "Implantando pré-requisitos para aplicativos de 64 bits | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: aefb619487fba984e8f625dfe414c2f514f28c70
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Implantando pré-requisitos para aplicativos de 64 bits
A implantação do ClickOnce oferece suporte à instalação de aplicativos em plataformas de 64 bits. As plataformas de destino são **x86** para plataformas de 32 bits, **x64** para dar suporte os conjuntos de instruções AMD64 e EM64T, de máquinas e **Itanium** para o processador Itanium de 64 bits.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A tabela a seguir lista os redistribuíveis que você pode usar como pré-requisitos para a instalação do seu aplicativo de 64 bits.  
  
 Se você selecionar um pré-requisito que não tem componentes de 64 bits, poderá ver um aviso informando que os pacotes selecionados não estão disponíveis para a plataforma de 64 bits.  
  
|Redistribuível|Suporte a x64|Suporte a IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Sim|Não|  
|Bibliotecas de tempo de execução do Visual C++ 2010 (IA64)|Não|Sim|  
|Bibliotecas de tempo de execução do Visual C++ 2010 (x64)|Sim|Não|  
|Microsoft .NET Framework 4 (x86 e x64)|Sim||  
|Perfil de cliente do Microsoft .NET Framework 4 (x86 e x64)|Sim||  
  
## <a name="see-also"></a>Consulte também  
 [Implantando aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md)   
 [Como instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Aplicativos de 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)