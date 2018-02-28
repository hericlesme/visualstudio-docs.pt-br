---
title: Acessando o Buffer de texto usando a API herdado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 77002e095690da85e73f1a79d405cb5174b96851
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Acessando o Buffer de texto usando a API herdado
O texto é responsável por gerenciar fluxos de texto e persistência de arquivo. Embora o buffer pode ler ou gravar outros formatos, toda a comunicação comum com o buffer é realizada usando o Unicode. APIs herdado, o buffer de texto pode usar um - ou um sistema de coordenadas bidimensional para identificar os locais de caractere no buffer.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Dimensão de um e dois sistemas de coordenadas  
 Uma posição de coordenadas unidimensional baseia-se a posição do caractere a partir do primeiro caractere no buffer, como 147. Você usa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interface para acessar um local unidimensional no buffer. Um sistema de coordenadas bidimensional baseia-se em pares de linha e de índice. Por exemplo, um caractere no buffer no 43, 5 seria na linha 43, cinco caracteres à direita do primeiro caractere na linha. Acessar um local bidimensional no buffer usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface. Tanto o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaces implementadas pelo objeto de buffer de texto (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) e pode ser acessado do outro usando `QueryInterface`. O diagrama a seguir mostra essas e outras interfaces de chave em <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Objeto de Buffer de texto](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Objeto de buffer de texto  
  
 Embora o sistema de coordenadas funciona no buffer de texto, ela é otimizada para usar coordenadas bidimensionais. Um sistema de coordenadas unidimensional pode criar sobrecarga de desempenho. Portanto, use o sistema de coordenadas bidimensional sempre que possível.  
  
 O texto de responsabilidade de segundo do buffer é persistência de arquivo. Para fazer isso, o objeto de buffer de texto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e atua como o componente de objeto de dados de documentos para itens de projeto e outros componentes do ambiente envolvidos na persistência. Para obter mais informações, consulte [abrir e salvar itens de projeto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Alterar configurações de exibição usando a API herdado](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explica como alterar as configurações de exibição usando a API herdada.  
  
 [Usando o Gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explica como usar o Gerenciador de texto para monitorar as configurações globais.  
  
## <a name="see-also"></a>Consulte também  
 [Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)