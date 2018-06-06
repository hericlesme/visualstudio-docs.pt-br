---
title: Avisos e Erros XAML
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a263f361e28c515f1694238c4d60fdeffb95f03a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746618"
---
# <a name="xaml-errors-and-warnings"></a>Avisos e Erros XAML

Ao criar XAML, o Visual Studio analisa o código conforme você digita. Um rabisco aparece em uma linha de código quando um erro é detectado. Se você passar o mouse sobre o rabisco, verá mais informações sobre o erro ou aviso. Em alguns erros e avisos, uma lâmpada de Ação rápida é exibida. Ela também aparece ao pressionar **Ctrl**+**.** o atalho de teclado exibe as opções para corrigir o problema.

## <a name="error-types"></a>Tipos de erro

Em segundo plano, várias ferramentas analisam o XAML em paralelo. Erros de XAML são categorizados em um dos três seguintes tipos, com base na ferramenta que detectou o erro:

|**Erro detectado por**|**Formato do código de erro**|
|--------------------------------|-----------------|
|Serviço de linguagem XAML (Editor XAML)|XLSxxxx|
|XAML Designer|XDGxxxx|
|Editar e Continuar em XAML|XECxxxx|

> [!Note]
> Nem todos os erros/avisos têm um código correspondente. Geralmente, esses erros são do XAML Designer.


## <a name="suppress-xaml-designer-errors"></a>Suprimir erros do XAML Designer

Abra a caixa de diálogo **Opções** selecionando **Ferramentas > Opções** e, em seguida, selecione **Editor de Texto > XAML > Diversos**.

Desmarque a caixa de seleção **Mostrar erros detectados pelo XAML Designer**.

![Suprimir erros do XAML Designer](../designers/media/suppress_xaml_designer_errors.png)


