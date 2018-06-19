---
title: Personalizando transformação de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b3960d0e511ab42de2bd81765fb395d2e013a493
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948841"
---
# <a name="customizing-t4-text-transformation"></a>Personalizando transformação de texto T4

Modelos de texto são um recurso do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que permitem que você gerar o código do programa ou outros arquivos de texto por meio de um processo de transformação. Usando [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], você pode estender o processo de transformação de modelo padrão, personalizando o processador de diretiva de modelo de texto ou o host de modelo de texto.

## <a name="in-this-section"></a>Nesta seção
 [O processo de transformação de modelo de texto](../modeling/the-text-template-transformation-process.md) descreve o funcionamento de transformação de texto e explica a função de host do modelo e os processadores de diretiva.

 [Criando processadores de diretiva de modelo do personalizado T4 texto](../modeling/creating-custom-t4-text-template-directive-processors.md) o processador de diretiva lida com as diretivas no modelo, como `<#@template#>.` ele é executado durante a compilação do modelo e pode carregar os assemblies e outros recursos. Ele também pode inserir o código que carregará recursos em tempo de execução. Definindo seu próprios processador de diretiva, você pode reduzir a complexidade de seus modelos.

 [Invocando transformação de texto em uma extensão VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) se você estiver escrevendo um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão como um manipulador de eventos ou de comando de menu, sua extensão poderá usar o serviço de modelagem de texto para transformar qualquer modelo de texto. Você pode passar dados de parâmetro para o modelo usando o objeto de sessão e obter os valores de dentro do modelo usando o `<#@parameter#>` diretiva.

 [Processando modelos de texto usando um Host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md) quando executa o código do modelo de texto, o host fornece acesso a arquivos externos e o estado do aplicativo. Por exemplo, o host que executa transformações de texto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode fornecer acesso ao Gerenciador de soluções. Ele também exibe os erros na janela da mensagem de erro. Se você deseja executar transformações de texto em um contexto diferente, você pode definir seu próprio host que fornece acesso para os serviços disponíveis nesse contexto.

 Se você estiver escrevendo um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão, considere usar o serviço de transformação de texto existente em vez de escrever seu próprio host. Para obter mais informações, consulte [invocando transformação de texto em uma extensão VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referência

- [Escrever um modelo de texto T4](../modeling/writing-a-t4-text-template.md) fornece a sintaxe de diretivas de modelo de texto e blocos de controle.