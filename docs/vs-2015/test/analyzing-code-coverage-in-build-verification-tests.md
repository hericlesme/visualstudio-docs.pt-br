---
title: Analisando a cobertura de código em testes de verificação de build | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: gewarren
manager: douge
ms.openlocfilehash: f0cbcf51d6b7eb3229366216a86d191d5946f30f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475264"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analisando a cobertura de código em testes de verificação de build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [analisando a cobertura de código em testes de verificação de compilação](https://docs.microsoft.com/visualstudio/test/analyzing-code-coverage-in-build-verification-tests).  
  
A análise de cobertura de código no Microsoft Visual Studio mostra quanto de seu código está sendo utilizado por testes automatizados. Para obter mais informações, consulte [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Quando você faz check-in de seu código, os testes serão executados no servidor de compilação, juntamente com os outros testes de outros membros da equipe. (Se você ainda não tiver configurado isso, consulte [Executar testes no processo de build](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) É útil analisar a cobertura de código no serviço de build, pois isso dá o panorama mais atualizado e mais abrangente da cobertura em todo o projeto. Também incluirá os testes automatizados do sistema e outros testes codificados que você normalmente não executa nos computadores de desenvolvimento.  
  
1.  No Team Explorer, abra **Compilações** e adicione ou edite uma definição de build.  
  
2.  Na página **Processo**, expanda **Testes Automatizados**, **Fonte de Teste**, **Configurações de Execução**. Defina **Tipo de Arquivo de Configurações de Execução** como **Cobertura de Código Habilitada**.  
  
     Se você tiver mais de uma definição de Fonte de Teste, repita essa etapa para cada uma.  
  
    -   *Mas não há nenhum campo denominado **Tipo de Arquivo de Configurações de Execução**.*  
  
         Em **Testes Automatizados**, selecione **Assembly de Teste** e escolha o botão de reticências **[...]** no final da linha. Na caixa de diálogo **Adicionar/Editar Execução de Teste**, em **Test Runner**, selecione **Visual Studio Test Runner**.  
  
 ![Configurar a definição de build para cobertura de código](../test/media/codecoverage-plaincc.png "CodeCoverage plainCC")  
  
 Após a execução do build, os resultados da cobertura de código aparecem no resumo do build.  
  
## <a name="see-also"></a>Consulte também  
 [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)



