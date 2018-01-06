---
title: "Política de modelo e na janela Propriedades | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 51735bf0f46e5a1ead6f989a8e75745ebc8e6e35
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="template-policy-and-the-properties-window"></a>Política de modelo e na janela Propriedades
Quando um projeto está contido dentro de um projeto de modelo de empresa, projeto modelo enterprise pode impor a política. Política de modelo torna-se um sistema de restrição que pode ser usado para definir valores padrão para propriedades, ocultar propriedades, adicionar propriedades e assim por diante.  
  
 Usando a política de modelo para controlar a exibição das informações de **propriedades** janela é diferente de implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Controla as propriedades do objeto no nível do componente, enquanto diretiva de modelo pode ser usada para restringir as propriedades de objeto no nível da solução ou projeto. Em outras palavras  
  
-   Implementar os métodos em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> para determinar o que é exibido o **propriedades** janela para objetos específicos  
  
-   Usar a política de modelo no nível de projeto e solução para determinar o que é exibido o **propriedades** janela de objetos especificados anteriormente  
  
 Usando a diretiva de modelo para restringir seletivamente propriedades específicas no **propriedades** janela quando um item de projeto de um tipo especificado está selecionada no **Solution Explorer** pode ser útil para todos os membros do a equipe de desenvolvimento trabalhando em um projeto. Por exemplo, usando a política de modelo, você pode configurar todas as informações de cadeia de caracteres de conexão em um banco de dados para os desenvolvedores e verifique a cadeia de conexão somente leitura. Dessa forma, você pode fornecer uma maneira simples de garantir que cada desenvolvedor usa o caminho correto para acesso a dados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estender as propriedades](../../extensibility/internals/extending-properties.md)