---
title: 'Como: alterar o Namespace de uma linguagem específica de domínio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1407b0ca77ea6f19bc6f6f165d5524c305b69d0f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "47587429"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Como alterar o namespace de uma linguagem específica do domínio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: alterar o Namespace de uma linguagem específica de domínio](https://docs.microsoft.com/visualstudio/modeling/how-to-change-the-namespace-of-a-domain-specific-language).  
  
Você pode alterar o namespace de uma linguagem específica de domínio. Você deve fazer a alteração no valor de **Gerenciador de DSL**, nas propriedades do projeto Dsl de pacote e as informações de assembly.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para alterar o namespace de uma linguagem específica de domínio  
  
1.  Na **Gerenciador de DSL**, clique no **Dsl** nó.  
  
2.  No **propriedades** janela, altere o **Namespace** propriedade.  
  
3.  Salve a solução e transformar os modelos.  
  
4.  Sobre o **Project** menu, clique em **Dsl propriedades**.  
  
     As propriedades do projeto são exibidos.  
  
5.  Clique na guia **Aplicativo**.  
  
6.  Alterar o **namespace padrão** propriedade para o novo nome de namespace.  
  
7.  Se você também quiser alterar o nome do assembly, altere o **propriedade nome do Assembly.**  
  
8.  Se você tiver alterado o nome do Assembly, abra DslPackage\Package.tt e atualize essa linha:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Se você tiver gravado um código personalizado, certifique-se de alterar as referências de namespace e classe nos arquivos de código.  
  
10. Redefina a instância Experimental do Visual Studio.  
  
    1.  Exclua **\Users\\**_{o nome}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Sobre o Windows **inicie** menu, escolha **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**, **redefinir o Instância experimental**.  
  
11. Sobre o **construir** menu, escolha **recompilar solução**.  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



