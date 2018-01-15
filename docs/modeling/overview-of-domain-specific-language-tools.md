---
title: "Visão geral das ferramentas de linguagem específica do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7c1a163e50e2f237430ba13d57a76cfc0d6b1d67
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="overview-of-domain-specific-language-tools"></a>Visão geral das Ferramentas de Linguagem Específica do Domínio
Ferramentas de linguagem específica de domínio (ferramentas de DSL), que são hospedados em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], permitem que você criar uma linguagem específica de domínio e, em seguida, gerar tudo o que os usuários devem ter para criar modelos com base no idioma.  
  
 As ferramentas a seguir estão incluídas nas ferramentas de DSL:  
  
-   Assistente de projeto que usa modelos de solução diferentes para ajudá-lo a começar a desenvolver sua linguagem específica de domínio.  
  
-   Um designer gráfico para criar e editar a definição de linguagem específica de domínio.  
  
-   Um mecanismo de validação que verifica se a definição de linguagem específica de domínio está bem formada e exibe os erros e avisos se houver problemas.  
  
-   Um gerador de código que usa uma definição de linguagem específica de domínio como entrada e produz código-fonte como saída.  
  
## <a name="the-dsl-tools-solution"></a>A solução de ferramentas DSL  
 O Assistente de Designer específica de domínio fornece os seguintes modelos de solução:  
  
-   Fluxo de tarefas  
  
-   Diagramas de classe  
  
-   Idioma mínimo  
  
-   Modelos de componente  
  
-   WPF mínima  
  
-   Windows. Forms mínima  
  
-   Biblioteca DSL  
  
 Para obter mais informações, consulte [escolhendo um modelo de solução de linguagem específica de domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 O assistente cria um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução que tem os seguintes projetos:  
  
-   DSL  
  
     O projeto de Dsl define a linguagem específica de domínio e suas ferramentas de edição e de processamento.  
  
-   **DslPackage**  
  
     O projeto DslPackage determina como as ferramentas de linguagem integram [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>A Interface gráfica de ferramentas DSL  
 Você pode usar a interface gráfica de ferramentas de DSL para adicionar elementos e relações para sua linguagem específica de domínio. Depois que você adicionou os elementos, você pode definir sua aparência mapeando-os para as formas, como personalizar cores e adicionando decoradores. Você também pode adicionar elementos à caixa de ferramentas.  
  
## <a name="validation-in-dsl-tools"></a>Validação em ferramentas DSL  
 DSL fornece um nível de validação para certificar-se de que o modelo de domínio atenda aos requisitos básicos para geração de código. Normalmente, quando você cria sua própria linguagem específica de domínio, você poderia adicionar sua própria validação para expressar as regras de lógica de negócios. Para obter mais informações sobre validação personalizada, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).  
  
 É recomendável que você valide sua linguagem específica de domínio geralmente quando estiver criando. Se sua linguagem específica de domínio tem erros de validação, não é possível gerar código-fonte. O processo de geração de código-fonte dos modelos é executado clicando **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções. Sempre que você modificar a definição de idioma, certifique-se de **transformar todos os modelos de**. Para obter mais informações, consulte [como: criar uma solução de linguagem específica de domínio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personalização das ferramentas DSL  
 Você pode fornecer código adicional para refinar o comportamento do modelo e definir restrições em seu idioma. Se necessário, você pode fazer alterações significativas, modificando os modelos de texto.  
  
## <a name="distributing-your-dsl-solution"></a>Distribuir sua solução DSL  
 Ferramentas de DSL gera um pacote hospedado em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. O pacote exibe uma caixa de ferramentas, um Gerenciador DSL e outros elementos de interface do usuário que permitem aos usuários criar modelos usando a linguagem específica de domínio.  
  
 Quando você compilar e executar a solução de ferramentas de DSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], uma segunda instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mostra a aparência de sua linguagem específica de domínio para o usuário do idioma. Depois de verificar se tudo está funcionando corretamente, você pode distribuir o `.vsix` arquivo será localizado na pasta de compilação do projeto DslPackage. Esse arquivo pode ser usado para instalar o DSL como um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão em outros computadores.  Para obter mais informações, consulte [implantar soluções de linguagem específica de domínio](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Consulte também  
 [A instância Experimental](../extensibility/the-experimental-instance.md)   
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)