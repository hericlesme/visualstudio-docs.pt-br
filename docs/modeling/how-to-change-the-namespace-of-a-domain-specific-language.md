---
title: "Como: alterar o Namespace de uma linguagem específica do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 468cf24ccb16452c93583b2aa99af560d920bcf4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Como alterar o namespace de uma linguagem específica do domínio
Você pode alterar o namespace de uma linguagem específica de domínio. Você deve fazer a alteração no **DSL Explorer**, nas propriedades do projeto Dsl pacote e as informações de assembly.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para alterar o namespace de uma linguagem específica do domínio  
  
1.  Em **DSL Explorer**, clique no **Dsl** nó.  
  
2.  No **propriedades** janela, altere o **Namespace** propriedade.  
  
3.  Salve a solução e transformar os modelos.  
  
4.  Sobre o **projeto** menu, clique em **Dsl propriedades**.  
  
     As propriedades de projeto aparecem.  
  
5.  Clique na guia **Aplicativo**.  
  
6.  Alterar o **namespace padrão** propriedade para o novo nome de namespace.  
  
7.  Se você também quiser alterar o nome do assembly, altere o **propriedade nome do Assembly.**  
  
8.  Se você tiver alterado o nome do Assembly, abra DslPackage\Package.tt e atualize essa linha:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Se você tiver gravado qualquer código personalizado, certifique-se de alterar as referências de namespace e classe nos arquivos de código.  
  
10. Redefina a instância Experimental do Visual Studio.  
  
    1.  Excluir **\Users\\***{seu nome}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  No Windows **iniciar** menu, escolha **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**, **redefinir o Instância experimental**.  
  
11. Sobre o **criar** menu, escolha **recompilar solução**.  
  
## <a name="see-also"></a>Consulte também

[Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)