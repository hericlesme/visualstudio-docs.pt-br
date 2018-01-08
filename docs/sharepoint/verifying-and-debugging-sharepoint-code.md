---
title: "Verificando e depurando código do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d3717d3bee3665705ce39307b640e02a931cd75f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="verifying-and-debugging-sharepoint-code"></a>Verificando e depurando código do SharePoint
  Usando o IntelliTrace e testes de unidade, você pode mais fácil depurar suas soluções do SharePoint e certifique-se de que cada método neles funciona corretamente. Você pode usar esses recursos para projetos do SharePoint no [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] seguindo os mesmos procedimentos para outros tipos de projetos.  
  
## <a name="intellitrace"></a>IntelliTrace  
 Usando o IntelliTrace, você pode determinar não apenas o estado atual da sua solução do SharePoint, mas também eventos que ocorreram no passado e o contexto em que elas ocorreram. Você pode navegar para frente e para trás para vários pontos no tempo em sua solução do SharePoint onde os eventos de interesse foram registrados e examinar os estados e os valores das variáveis em cada ponto. Usando essa navegação dinâmica, você pode mais rapidamente e facilmente depurar suas soluções do SharePoint sem a necessidade de definir vários pontos de interrupção. Você também pode salvar a sessão de depuração em um arquivo de log (. itrace) do IntelliTrace, abri-lo mais tarde no Visual Studio Ultimate e realizar a depuração após falhar. O arquivo. itrace inclui informações detalhadas sobre quando e onde ocorreram erros específicos do SharePoint, para que você pode descobrir o que está causando os erros mais facilmente. As informações no arquivo. itrace são um subconjunto do log de erro completa que cria ULS log unificado do sistema () no SharePoint. Essas informações incluem eventos que são específicos para o SharePoint, como quando um perfil de usuário está aberto ou fechado e quando propriedades em um projeto são carregados, o SharePoint lido ou alterado. Você pode configurar quais eventos de registros do IntelliTrace. Para obter mais informações, consulte [usando IntelliTrace dados salvo](/visualstudio/debugger/using-saved-intellitrace-data) e [configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 Quando ocorre um erro no SharePoint, a caixa de diálogo de erro exibe um identificador de "ID de correlação" para esse erro. Você também pode obter IDs de correlação de eventos que são listados no arquivo. itrace. Para exibir uma lista de todos os eventos que ocorreram com uma ID de correlação especificado, você pode inserir a ID no **Analysis** seção da página de resumo do IntelliTrace. Nessa seção, você pode optar por exibir somente os nomes dos eventos que ocorreram ou os nomes dos eventos junto com suas informações de chamada, como o nome da função, os pontos de entrada e saída, parâmetros e valores de retorno.  
  
 Você pode obter eventos do Visual Studio no IntelliTrace escolhendo o **F5** chave. Para obter os eventos que são específicos para o SharePoint, no entanto, você deve coletar dados do IntelliTrace em soluções do SharePoint usando o Microsoft Monitoring Agent. Essa ferramenta coleta dados do IntelliTrace e cria arquivos. itrace para aplicativos que são implantados fora do Visual Studio. Para obter mais informações, consulte [funcionalidades do IntelliTrace](/visualstudio/debugger/intellitrace-features) e [usando o coletor autônomo do IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).  
  
## <a name="unit-testing"></a>Teste de unidade  
 Você encontrará erros mais facilmente em seu código executando testes de unidade, no qual você pode gravar e executar o código de teste dentro de métodos de teste. Esses métodos contêm variáveis vazias e uma instrução Assert que você pode usar para verificar a lógica e a funcionalidade de seu projeto com base no modelo de objeto do SharePoint. Para obter mais informações, consulte [Efetuar teste de unidade em seu código](/visualstudio/test/unit-test-your-code).  
  
### <a name="support-for-microsoft-fakes-framework"></a>Suporte para Microsoft Fakes Framework  
 Suporte a projetos do SharePoint Microsoft Fakes, que é uma estrutura de isolamento no qual você pode criar com base em delegado teste stubs e shims em aplicativos baseados no .NET Framework. Usando a estrutura de falsificações, você pode criar, manter e injetar implementações fictícios nos testes de unidade. Esses stubs e shims isolam os testes de unidade do ambiente. Você pode criar stubs para testar o código que consome interfaces ou classes não lacradas com métodos substituíveis. Você pode criar shims para redirecionar chamadas embutida para classes lacradas com métodos estáticos ou não pode ser substituído para uma implementação alternativa de correção. Você também pode usar representantes com tipos de stub e shim dinamicamente personalizar o comportamento de membros individuais de stub. Para obter mais informações, consulte [isolando código em teste com o Microsoft Fakes](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[IntelliTrace](/visualstudio/debugger/intellitrace)|Descreve como depurar soluções do Visual Studio mais facilmente usando o IntelliTrace.|  
|[Instruções passo a passo: depurando um aplicativo do SharePoint usando o IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Demonstra como localizar erros de codificação em um projeto do SharePoint usando o IntelliTrace.|  
|[Efetuar teste de unidade em seu código](/visualstudio/test/unit-test-your-code)|Descreve como localizar erros lógicos em seu código usando testes de unidade.|  
  
## <a name="see-also"></a>Consulte também  
 [Melhorar a qualidade do código](/visualstudio/test/improve-code-quality)  
  
  