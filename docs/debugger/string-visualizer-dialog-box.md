---
title: Exibir cadeias de caracteres em um visualizador de cadeia de caracteres | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3a0575b02422bf83dd560d3eae5724b0a50d3f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Cadeias de caracteres de exibição em um visualizador de cadeia de caracteres no Visual Studio
Enquanto você está depurando, você pode abrir um visualizador de cadeia de caracteres em cadeias de caracteres de exibição que são muito longos para exibição em uma janela de dica ou depurador de dados. Em muitos cenários, o visualizador pode ajudar a identificar as cadeias de caracteres malformadas.

Os visualizadores de cadeia de caracteres padrão incluem XML, texto sem formatação, HTML e JSON. Para alguns outros tipos, como objetos WPF que aparecem no depurador do windows, como o **Autos** janela, você também pode abrir visualizadores.

## <a name="open-a-string-visualizer"></a>Abrir um visualizador de cadeia de caracteres

Para exibir um texto sem formatação, a cadeia de caracteres JSON, HTML ou XML, clique no ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ícone visualizador") ao passar o mouse sobre uma variável que contém um valor de cadeia de caracteres. Você deve estar pausada no depurador para ver o ícone de lupa.

![Abrir um visualizador de cadeia de caracteres](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Exibir dados de cadeia de caracteres

O **expressão** campo no Visualizador de cadeia de caracteres mostra a variável atual ou colocado em cima de expressão no depurador.

O **valor** campo mostra o valor de cadeia de caracteres. O Visualizador de texto mostra o texto sem formatação.

Um espaço em branco **valor** indica que o visualizador específico não é possível reconhecer o tipo de cadeia de caracteres. Por exemplo, o Visualizador XML mostra um espaço em branco **valor** para cadeia de caracteres formatadas como uma cadeia de caracteres de texto simples (com nenhuma marcação XML) ou JSON. Se você precisar exibir uma cadeia de caracteres não reconhecida em um visualizador, use o Visualizador de texto.

### <a name="view-json-string-data"></a>Exibir dados de cadeia de caracteres JSON

Uma cadeia de caracteres JSON bem formada será semelhante à ilustração a seguir no Visualizador de JSON. JSON malformado pode exibir um ícone de erro (ou em branco, se não reconhecido).

![Visualizador de cadeia de caracteres JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizador de cadeia de caracteres JSON")

### <a name="view-xml-string-data"></a>Exibir dados de cadeia de caracteres XML

Uma cadeia de caracteres XML bem formada será semelhante à ilustração a seguir no Visualizador de XML. XML malformado pode exibir sem as marcas XML (ou o espaço em branco se não reconhecido).

![Visualizador de cadeia de caracteres XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizador de cadeia de caracteres XML")

### <a name="view-html-string-data"></a>Dados de cadeia de caracteres de exibição HTML

Uma cadeia de caracteres HTML bem formada parece semelhante ao modo de exibição que você veria se a cadeia de caracteres é renderizada em um navegador, conforme mostrado na ilustração a seguir. HTML malformado pode ser exibido como texto sem formatação.

![Visualizador de cadeia de caracteres HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizador de cadeia de caracteres HTML")

## <a name="see-also"></a>Consulte também  
 [Criar visualizadores personalizados (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)