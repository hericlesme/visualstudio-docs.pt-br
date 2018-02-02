---
title: "Passo a passo: Analisando código C/C++ em busca de defeitos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9b0f8e36cddca227062550775c9f6098aeb1c6f
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Instruções passo a passo: analisando código do C/C++ em busca de defeitos
Este passo a passo demonstra como analisar o código C/C++ em busca de possíveis defeitos de código usando a ferramenta de análise de código para código C/C++.  
  
 Neste passo a passo, percorra o processo de usar a análise de código para analisar seu código C/C++ em busca de possíveis defeitos de código.  
  
 Você executará as seguintes etapas:  
  
-   Execute análise de código em código nativo.  
  
-   Analise os avisos de defeito de código.  
  
-   Tratar avisos como erro.  
  
-   Anote o código-fonte para melhorar a análise de defeito de código.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  
  
-   Uma cópia do [exemplo de demonstração](../code-quality/demo-sample.md).  
  
-   Noções básicas sobre do C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Para executar a análise de defeito de código em código nativo  
  
1.  Abra a solução de demonstração em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     A solução de demonstração agora preenche **Gerenciador de soluções**.  
  
2.  Sobre o **criar** menu, clique em **recompilar solução**.  
  
     A solução seja criada sem erros ou avisos.  
  
3.  Em **Solution Explorer**, selecione o projeto CodeDefects.  
  
4.  No menu **Projeto**, clique em **Propriedades**.  
  
     O **páginas de propriedade CodeDefects** caixa de diálogo é exibida.  
  
5.  Clique em **de análise de código**.  
  
6.  Clique o **habilitar análise de código para C/C++ na compilação** caixa de seleção.  
  
7.  Recompile o projeto CodeDefects.  
  
     Avisos da análise de código são exibidos na **lista de erros**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Para analisar os avisos de defeito de código  
  
1.  Sobre o **exibição** menu, clique em **lista de erros**.  
  
     Dependendo do perfil de desenvolvedor que você escolheu na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], talvez você precise aponte para **outras janelas** no **exibição** menu e clique **lista de erros**.  
  
2.  No **lista de erros**, clique duas vezes o seguinte aviso:  
  
     Aviso C6230: conversão implícita entre tipos semanticamente diferentes: usando HRESULT em um contexto Boolean.  
  
     O editor de código exibe a linha que causou o aviso na função `bool``ProcessDomain()`. Esse aviso indica que um HRESULT está sendo usada em uma instrução 'if' onde um resultado booleano é esperado.  
  
3.  Corrija esse aviso usando a macro SUCCEEDED. Seu código deve se parecer com o código a seguir:  
  
   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )  
   ```  
  
4.  No **lista de erros**, clique duas vezes o seguinte aviso:  
  
     Aviso C6282: operador incorreto: atribuição a constante no contexto do teste. Foi = = pretendido?  
  
5.  Teste de igualdade para corrigir este aviso. Seu código deve se parecer com o código a seguir:  
  
   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
   ```  
  
### <a name="to-treat-warning-as-an-error"></a>Tratar aviso como erro  
  
1.  No arquivo Bug.cpp, adicione o seguinte `#pragma` instrução para o início do arquivo para tratar o aviso C6001 como um erro:  
  
   ```cpp
   #pragma warning (error: 6001)  
   ```  
  
2.  Recompile o projeto CodeDefects.  
  
     No **lista de erros**, C6001 agora aparece como um erro.  
  
3.  Corrija os erros de C6001 duas restantes no **lista de erros** Inicializando `i` e `j` como 0.  
  
4.  Recompile o projeto CodeDefects.  
  
     O projeto é compilado sem avisos ou erros.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Para corrigir os avisos de anotação do código fonte no annotation.c  
  
1.  No Solution Explorer, selecione o projeto de anotações.  
  
2.  No menu **Projeto**, clique em **Propriedades**.  
  
     O **páginas de propriedades de anotações** caixa de diálogo é exibida.  
  
3.  Clique em **de análise de código**.  
  
4.  Selecione o **habilitar análise de código para C/C++ na compilação** caixa de seleção.  
  
5.  Recompile o projeto de anotações.  
  
6.  No **lista de erros**, clique duas vezes o seguinte aviso:  
  
     Aviso C6011: desreferência de ponteiro nulo 'newNode'.  
  
     Esse aviso indica falha pelo chamador para verificar o valor de retorno. No caso, uma chamada para **AllocateNode** pode retornar um valor nulo (consulte o arquivo de cabeçalho annotations.h para declaração de função para AllocateNode).  
  
7.  Abra o arquivo annotations.cpp.  
  
8.  Para corrigir esse aviso, use uma instrução 'if' para testar o valor de retorno. Seu código deve se parecer com o código a seguir:  
  
   ```cpp
   if (NULL != newNode)  
   {  
   newNode->data = value;  
   newNode->next = 0;  
   node->next = newNode;  
   }
   ```
  
9. Recompile o projeto de anotações.  
  
     O projeto é compilado sem avisos ou erros.  
  
### <a name="to-use-source-code-annotation"></a>Para usar a anotação do código fonte  
  
1.  Anotar parâmetros formais e retornar o valor da função `AddTail` usando as condições anteriores e subsequentes, conforme mostrado neste exemplo:  
  
   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```
  
2.  Recompile o projeto de anotações.  
  
3.  No **lista de erros**, clique duas vezes o seguinte aviso:  
  
     Aviso C6011: 'node' ponteiro de cancelamento de referência nula.  
  
     Esse aviso indica que o nó passado para a função pode ser nulo e indica o número da linha em que o aviso foi gerado.  
  
4.  Para corrigir esse aviso, use uma instrução 'if' para testar o valor de retorno. Seu código deve se parecer com o código a seguir:  
  
   ```cpp
   . . .  
   LinkedList *newNode = NULL;   
   if (NULL == node)  
   {  
        return NULL;  
        . . .  
   }  
   ```  
  
5.  Recompile o projeto de anotações.  
  
     O projeto é compilado sem avisos ou erros.  
  
## <a name="see-also"></a>Consulte também

[Passo a passo: analisando código gerenciado em busca de defeitos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)  
[Análise de código para C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)