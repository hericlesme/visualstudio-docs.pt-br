---
title: Erros da política de análise do código
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 625b67972095728d1e9f5c0fd9fa9e5d8da60786
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="code-analysis-policy-errors"></a>Erros da política de análise do código
Os seguintes erros ocorrem se a política de análise de código não for atendida no check-in:

 **As configurações de análise de código para um ou mais projetos não são compatíveis com a política de análise de código.**

 Os requisitos de análise de código fazer check-in de controle de origem do projeto de equipe não foi atendida para um ou mais projetos de código. Esse erro pode ser causado por uma ou mais das seguintes condições:

1.  Análise de código não está habilitada na compilação de todos os projetos na solução.

2.  A regra local definida para o projeto no Visual Studio tem menos restritivo **ação** definir que a regra de projeto de equipe, por exemplo, definir uma regra que é definida como **ação**=**erro**  no servidor tem seu **ação** definida como **aviso** ou **nenhum** na regra definida sendo executado no Visual Studio).

3.  A regra no conjunto especificada no Visual Studio não contém todas as regras que são especificadas na regra conjunto especificada na análise de código check-in política de projeto de equipe.

 **A política de análise de código falha. Há erros no projeto {0} ou a compilação não está atualizada.**

 A compilação contém erros ou os erros foram corrigidos, mas a análise de código não foi executada após a correção.

 **Falha de check-in. A política de análise de código requer que você verifique por meio do Visual Studio com uma solução aberta.**

 A política de análise de código requer que todos os arquivos em check-in devem estar na solução atualmente aberta. Para corrigir esse erro, abra a solução que contém o arquivo de check-in.

 **Nem todos os arquivos no check-in pendente estão dentro da solução atualmente aberta.**

 A política de análise de código requer que todos os arquivos em check-in devem estar na solução atualmente aberta. Esse erro é gerado quando há uma solução aberta, mas alguns arquivos na exibição de "verificação pendente em" não fazem parte da solução atualmente aberta. Para corrigir esse erro, abra a solução que contém o arquivo de check-in.

 **A versão do '{0}' não está correta. O nome forte especificado na diretiva é '\\{1 \\}'.**

 Esse erro se aplicam a projetos do .NET. Um arquivo. dll de regra necessárias à política de análise de código existe no computador local, mas a chave pública/versão não corresponde. Para corrigir esse erro, criador da política deve atualizar as DLLs no *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  diretório em seu computador.

 **'{0}' especificado na diretiva de assembly não existe.**

 Esse erro se aplicam a projetos do .NET. Uma regra necessária à política de análise de código não tem a dll correspondente instalada no computador cliente. Para corrigir esse erro, o criador de política deve atualizar a dll no *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  diretório em seu computador.

 **Configurações de regra do projeto {0} não estão em conformidade com a política de análise de código.**

 Esse erro se aplicam a projetos do .NET. As configurações de regras de código gerenciado não são tão estritas como a política exige. Para corrigir esse erro, a configuração do cliente deve ser o mesmo ou mais rígidos do que o requisito de política no servidor.

 **Análise de código não está habilitada na configuração ativa. Alterne para a configuração {0} e compilar o projeto \\{1 \\} antes de fazer check-in.**

 Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a configuração ativa não tem a análise de código habilitada, mas há pelo menos um code analysis habilitado.

 **Você deve habilitar a análise de código para binários gerenciados nas propriedades do projeto {0} e compilar antes de fazer check-in.**

 Esse erro se aplica a [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplicativos .NET. Requer que a política de análise de código gerenciado para ser executada, mas ela não está habilitada no projeto atual no cliente.

 **Você deve habilitar a análise de código nas propriedades do projeto {0} e compilar antes de fazer check-in.**

 Esse erro aplicado a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projetos e projetos da Web. Requer que a política de análise de código gerenciado para ser executada, mas ela não está habilitada no projeto atual no cliente.

 **Você deve habilitar a análise de código C/C++ nas propriedades do projeto {0} e compilar antes de fazer check-in.**

 Esse erro se aplicam a projetos não gerenciados. A política de análise de código requer a análise de código para C/C++, mas ela não está habilitada no projeto atual no cliente.

## <a name="see-also"></a>Consulte também
 [Erros de aplicativo de análise de código](../code-quality/code-analysis-application-errors.md)