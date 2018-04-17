---
title: Referência de API (desenvolvimento do Office no Visual Studio) não gerenciada | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e06ec998dc4b9c23b38526563ce8b501866769b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referência de API não gerenciada (desenvolvimento do Office no Visual Studio)
  Começando com o Microsoft Office 2007, aplicativos do Office usam o [IManagedAddin Interface](../vsto/imanagedaddin-interface.md) interface para chamar um suplemento do VSTO carregador do componente que está incluído com o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Esse componente é usado para ajudar a carga gerenciados suplementos do VSTO. Você pode criar seu próprio componente de carregador do suplemento do VSTO por implementar esta interface.  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)  
 Uma interface COM que você pode implementar para carregar e descarregar gerenciados suplemento do VSTO em aplicativos do Office.  
  
  