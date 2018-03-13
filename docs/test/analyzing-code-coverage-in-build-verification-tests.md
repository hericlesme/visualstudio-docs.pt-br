---
title: "Analisando a cobertura de código em testes de verificação de build | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 3f02166c89837dfd122ab8a8c71913c659ab1dd2
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analisando a cobertura de código em testes de verificação de build
A análise de cobertura de código no Microsoft Visual Studio mostra quanto de seu código está sendo utilizado por testes automatizados. Para obter mais informações, consulte [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Quando você faz check-in de seu código, os testes serão executados no servidor de compilação, juntamente com os outros testes de outros membros da equipe. (Se você ainda não tiver configurado isso, consulte [Executar testes no processo de build](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) É importante analisar a cobertura de código no serviço de build, pois isso dá o panorama mais atualizado e mais abrangente da cobertura em todo o projeto. Isso também incluirá os testes automatizados do sistema e outros testes codificados que você normalmente não executa nos computadores de desenvolvimento.  
  
1.  No Team Explorer, abra **Compilações** e adicione ou edite uma definição de build.  
  
2.  Na página **Processo**, expanda **Testes Automatizados**, **Fonte de Teste**, **Configurações de Execução**. Defina **Tipo de Arquivo de Configurações de Execução** como **Cobertura de Código Habilitada**.  
  
     Se você tiver mais de uma definição de Fonte de Teste, repita essa etapa para cada uma.  
  
    -   *Mas não há nenhum campo denominado **Tipo de Arquivo de Configurações de Execução**.*  
  
         Em **Testes Automatizados**, selecione **Assembly de Teste** e escolha o botão de reticências **[...]** no final da linha. Na caixa de diálogo **Adicionar/Editar Execução de Teste**, em **Test Runner**, selecione **Visual Studio Test Runner**.  
  
 ![Configurar a definição de build para cobertura de código](../test/media/codecoverage-plaincc.png "CodeCoverage plainCC")  
  
 Após a execução do build, os resultados da cobertura de código aparecem no resumo do build.  
  
## <a name="see-also"></a>Consulte também  
 [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
