---
title: Tabela de comando do Visual Studio (. Arquivos VSCT) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0692f0b32544edf7d5d7cec4b0ab4592c4219b3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473165"
---
# <a name="visual-studio-command-table-vsct-files"></a>Arquivos .Vsct (Visual Studio Command Table)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tabela de comando do Visual Studio (. VSCT) arquivos](https://docs.microsoft.com/visualstudio/extensibility/internals/visual-studio-command-table-dot-vsct-files).  
  
Um arquivo de configuração da tabela de comando é um arquivo de texto que descreve o conjunto de comandos que contém um VSPackage. O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] comando compilador tabela (VSCT) compila a configuração baseada em XML (arquivos. VSCT) em arquivos de saída (CTO já) da tabela de comando binário. Os arquivos de CTO já resultantes são iguais aos que são criados usando o compilador de tabela (CTC) do comando para compilar os arquivos de configuração. ctc. No entanto, os arquivos. VSCT de baseado em XML tem algumas vantagens, como um editor de XML e o IntelliSense XML.  
  
 Para saber mais sobre a sintaxe e semântica de arquivos. VSCT, consulte [criar tabela de comando de XML (. Arquivos de VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Projetar arquivos da tabela de comandos XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Descreve como criar arquivos. VSCT.  
  
 [Como criar um arquivo .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compara os métodos para a criação de um arquivo. VSCT. Descreve o processo de criação manual de um novo arquivo. VSCT.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fornece detalhes sobre cada seção do arquivo de configuração do XML do comando tabela.  
  
 [Configuração da tabela de comando (. Arquivos CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Apresenta uma visão geral do formato de arquivo. ctc preterido.  
  
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Descreve a especificação de formato de tabela do comando.  
  
 [Recursos em VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Descreve como usar os recursos gerenciados e em VSPackages gerenciados.  
  
 [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica como criar uma interface do usuário que inclui menus, barras de ferramentas e caixas de combinação de comando.

