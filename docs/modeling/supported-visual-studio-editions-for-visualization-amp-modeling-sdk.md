---
title: Suporte para edições do Visual Studio para visualização &amp; SDK de modelagem
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 16a00dd5c0769cb49f5281570ba11433afa56dfe
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858854"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Suporte para edições do Visual Studio para visualização &amp; SDK de modelagem
Seguem listas das edições do Visual Studio que têm suporte com [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] nos ambientes de criação e implantação. Para obter mais informações sobre essas edições, consulte o Microsoft Visual Studio [Central de desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Edição de Criação
 Para definir uma DSL, é necessário ter instalados os seguintes componentes:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|SDK do Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|SDK de Visualização e Modelagem do Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edições de Implantação
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] oferece suporte às seguintes configurações para implantação das linguagens específicas do domínio que foram compiladas:

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Pacote redistribuível do Visual Studio Shell (modo integrado) pacote redistribuível

-   Pacote redistribuível Visual Studio Shell (modo isolado) pacote redistribuível

> [!NOTE]
>  Para tornar uma DSL capaz de executar em um produto Shell, você deve definir a **suporte para a edição do VS** campo no manifesto de extensão. Para obter mais informações, consulte [implantar soluções de linguagem específica do domínio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Consulte também

- [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
