---
title: Página Opções, Propriedades do Nó de Fontes e Cores | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18524cb3b27a05763187b9d5567d127af39c25d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466271"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Página de Opções, Fontes e Cores, Propriedades de Nó
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [página de opções, fontes e cores de propriedades de nó](https://docs.microsoft.com/visualstudio/ide/reference/options-page-fonts-and-colors-node-properties).  
  
  
Este documento descreve as propriedades de fonte e de cor de uma janela de ferramentas registrada para ser exibida em **Fontes e Cores** na categoria **Ambiente** da caixa de diálogo **Opções**. Isso dá suporte à natureza dinâmica de grupos de itens de coloração, que poderão ser alterados se os VSPackages forem instalados ou desinstalados.  
  
 A seção a seguir mostra um exemplo de um tipo de janela registrada e as propriedades disponíveis para cada janela.  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor de Texto, impressora ou caixas de diálogo e janelas de ferramentas  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 -ou-  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 -ou-  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|FontFamily|Get/Set (Cadeia de Caracteres)|O nome da fonte a ser usado, como “Courier New”.|  
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Um valor de <xref:EnvDTE.vsFontCharSet>, especificando o tipo de conjunto de caracteres a ser usado, como hebraico ou russo.|  
|FontSize|Get/Set (Curto)|O tamanho da fonte a ser usado, em pontos. Por exemplo, 10 ou 12.|  
  
## <a name="see-also"></a>Consulte também  
 [Controlando configurações de opções](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinando os nomes de itens de propriedades em páginas de opções](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Página Opções, Propriedades do Nó de Ambiente](../../ide/reference/options-page-environment-node-properties.md)   
 [Página de Opções, Propriedades do Nó de Editor de Texto](../../ide/reference/options-page-text-editor-node-properties.md)



