---
title: "Personalizando transformação de texto T4 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 56eb5c11984e60e16374853ef1911ae831476d64
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-t4-text-transformation"></a>Personalizando transformação de texto T4
Modelos de texto são um recurso do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que permitem que você gerar o código do programa ou outros arquivos de texto por meio de um processo de transformação. Usando [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], você pode estender o processo de transformação de modelo padrão, personalizando o processador de diretiva de modelo de texto ou o host de modelo de texto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [O processo de transformação de modelo de texto](../modeling/the-text-template-transformation-process.md)  
 Descreve como funciona a transformação de texto e explica a função de host do modelo e os processadores de diretiva.  
  
 [Criando processadores de diretiva de modelo de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 O processador de diretiva lida com as diretivas no modelo, como `<#@template#>.` ele é executado durante a compilação do modelo e pode carregar os assemblies e outros recursos. Ele também pode inserir o código que carregará recursos em tempo de execução. Definindo seu próprios processador de diretiva, você pode reduzir a complexidade de seus modelos.  
  
 [Invocando transformação de texto em uma extensão do VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Se você estiver escrevendo um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão como um manipulador de eventos ou de comando de menu, sua extensão poderá usar o serviço de modelagem de texto para transformar qualquer modelo de texto. Você pode passar dados de parâmetro para o modelo usando o objeto de sessão e obter os valores de dentro do modelo usando o `<#@parameter#>` diretiva.  
  
 [Processando modelos de texto usando um host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Quando o código do modelo de texto é executado, o host fornece acesso a arquivos externos e o estado do aplicativo. Por exemplo, o host que executa transformações de texto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode fornecer acesso ao Gerenciador de soluções. Ele também exibe os erros na janela da mensagem de erro. Se você deseja executar transformações de texto em um contexto diferente, você pode definir seu próprio host que fornece acesso para os serviços disponíveis nesse contexto.  
  
 Se você estiver escrevendo um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão, considere usar o serviço de transformação de texto existente em vez de escrever seu próprio host. Para obter mais informações, consulte [invocando transformação de texto em uma extensão VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Referência  
 [Gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md)  
  
 Fornece a sintaxe de diretivas de modelo de texto e blocos de controle.