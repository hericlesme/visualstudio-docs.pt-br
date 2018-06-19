---
title: Expondo os tipos de Designers visuais | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28dcc17c74a5b5ef3c9784fafe972beb6f170d90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135968"
---
# <a name="exposing-types-to-visual-designers"></a>Expondo os tipos de Designers visuais
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve ter acesso a definições de classe e tipo em tempo de design para exibir um designer visual. Classes são carregadas de um conjunto predefinido de assemblies que incluem o conjunto completo de dependência do projeto atual (referências e suas dependências). Ele também pode ser necessário para designers visuais para classes de acesso e tipos que são definidos em arquivos gerados por ferramentas personalizadas.  
  
 O [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas de projeto dão suporte para acessar tipos e classes geradas por meio portátil temporário arquivos executáveis (PEs temporário). Qualquer arquivo gerado por uma ferramenta personalizada pode ser compilado em um assembly temporário para que os tipos podem ser carregados a partir desses assemblies e expostos aos designers. A saída de cada ferramenta personalizada é compilada em um PE temporário separado, e o êxito ou falha desta compilação temporários depende apenas se o arquivo gerado pode ser compilado. Mesmo que um projeto não pode ser compilado como um todo, individuais PEs temporário ainda podem estar disponíveis para designers.  
  
 O sistema de projeto fornece suporte completo para o controle de alterações para o arquivo de saída de uma ferramenta personalizada, desde que essas alterações são o resultado da execução da ferramenta personalizada. Cada vez que a ferramenta personalizada é executada, um novo PE temporário é gerado e são enviadas notificações apropriadas para designers.  
  
> [!NOTE]
>  Porque o arquivo de programas temporários de executável geração ocorre em segundo plano, sem erros são relatados para o usuário se a compilação falhar.  
  
 Ferramentas personalizadas que se beneficiar do suporte de PE temporário devem seguir as regras a seguir:  
  
-   `GeneratesDesignTimeSource` deve ser definido como 1 no registro.  
  
     Nenhuma compilação de arquivo executável do programa ocorre sem essa configuração.  
  
-   O código gerado deve estar no mesmo idioma em que a configuração de projeto global.  
  
     O PE temporário é compilado, independentemente de qual ferramenta personalizada informa como a extensão solicitada na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> desde que `GeneratesDesignTimeSource` é definido como 1 no registro. A extensão não precisa ser. vb,. cs ou. jsl; pode ser qualquer extensão.  
  
-   O código gerado pela ferramenta personalizada deve ser válido, e ele deve compilar seu próprio usando apenas o conjunto de referências presentes no projeto no momento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> conclui a execução.  
  
     Quando um PE temporário é compilado, o único arquivo de origem fornecido ao compilador é a saída da ferramenta personalizada. Portanto, uma ferramenta personalizada que usa um PE temporário deve gerar os arquivos de saída que podem ser compilados independentemente de outros arquivos no projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao objeto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementando geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)   
 [Registrar geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md)