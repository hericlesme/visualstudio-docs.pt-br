---
title: O comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: db916372691ce5e336e142aeb72288193e1ed807
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="the-dsltexttransform-command"></a>O comando DslTextTransform
DslTextTransform.cmd é um script que chama TextTransform.exe e executa-o com opções comuns. Você pode usar DslTextTransformation.cmd para automatizar uma noturna compilação do seu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projetos. Para obter mais informações, consulte [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd está localizado no seguinte diretório:

 **\<Caminho de instalação do Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Você pode especificar os argumentos a seguir como entrada para DslTextTransform.cmd:

-   O diretório de saída do projeto de modelo de domínio.

-   O diretório de saída do projeto definição designer.

-   O local do arquivo de modelo de texto.

 DslTextTransform.cmd processa o arquivo de modelo de texto especificado usando os processadores de diretiva padrão e assemblies. Se você criar processadores de diretivas personalizadas, você pode criar seu próprio arquivo de lote que chama TextTransform.exe. Nesse arquivo de lote, você pode especificar seus assemblies e os processadores de diretiva personalizados associados.