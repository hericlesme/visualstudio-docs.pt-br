---
title: 'Como: adicionar marcadores de texto padrão | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bdcdbabae26a9116b1e00910ecef2f83f4075551
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-standard-text-markers"></a>Como: adicionar marcadores de texto padrão
Use o procedimento a seguir para criar um dos tipos de marcador de texto padrão fornecidos com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de núcleo.  
  
### <a name="to-create-a-text-marker"></a>Para criar um marcador de texto  
  
1.  Dependendo se você estiver usando um ou dois - sistema de coordenadas bidimensional, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para criar um novo marcador de texto.  
  
     Na chamada de método, especifique um tipo de marcador, um intervalo de texto para criar o marcador e um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface. Esse método, em seguida, retorna um ponteiro para o marcador de texto recém-criado. Tipos de marcador são tirados de <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumeração. Especifique um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface se você deseja ser informado dos eventos de marcador.  
  
    > [!NOTE]
    >  Crie marcadores de texto no thread da interface do usuário principal somente. O editor de núcleo depende do conteúdo do buffer de texto para criar os marcadores de texto e o buffer de texto não é thread-safe.  
  
## <a name="adding-a-custom-command"></a>Adicionar um comando personalizado  
 Implementando o `IVsTextMarkerClient` interface e fornecendo um ponteiro a ele de um marcador aprimora o comportamento de marcador de várias maneiras. Primeiro, isso permite que você forneça dicas para o marcador e executar comandos. Isso também permite que você para receber notificações de eventos para marcadores individuais e para criar um menu de contexto sobre o marcador. Use o procedimento a seguir para adicionar um comando personalizado para o menu de contexto do marcador.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Para adicionar um comando personalizado para o menu de contexto  
  
1.  Antes do menu de contexto é exibido, o ambiente chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> método e passa a você um ponteiro para o marcador de texto afetado e o número do item de comando no menu de contexto.  
  
     Por exemplo, os comandos de ponto de interrupção específico no menu de contexto incluem **remover ponto de interrupção** por meio de **novo ponto de interrupção**, conforme exibido na captura de tela a seguir.  
  
     ![Menu de contexto do marcador](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Devolver um texto que identifica o nome do comando personalizado. Por exemplo, **remover ponto de interrupção** pode ser um comando personalizado, se o ambiente não já forneceu-lo. Você também devolver se o comando é suportado, disponível e habilitada, e/ou uma alternância-off. O ambiente usa essas informações para exibir o comando personalizado no menu de contexto da forma correta.  
  
3.  Para executar o comando, o ambiente chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método, passando um ponteiro para o marcador de texto e o número do comando selecionado no menu de contexto.  
  
     Use essas informações desta chamada para executar quaisquer ações do marcador de texto de comando personalizado dita.  
  
## <a name="see-also"></a>Consulte também  
 [Usar marcadores de texto com a API herdado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)   
 [Como: criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md)