---
title: 'Passo a passo: Configurar e usar um personalizado conjunto de regras | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b9a7046930d12ebb940820eb25c4563b0a3213e3
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Instruções passo a passo: configurando e usando um conjunto de regras personalizado

Este passo a passo mostra como usar as ferramentas de análise de código que foram configuradas para usar um personalizado *conjunto de regras* em uma biblioteca de classe. Você pode selecionar um conjunto de regras que se relaciona ao tipo de projeto que você especificou para sua solução, ou pode selecionar conjuntos de regras alternativa para atender uma necessidade específica, como verificação de código herdado para problemas que podem ser corrigidos de forma incondicional. Em ambos os casos, os conjuntos de regras também podem ser personalizados para ajustá-las aos seus requisitos de projeto.  
  
Neste passo a passo, você percorrer esses processos:  
  
-   Crie uma biblioteca de classe.  
  
-   Selecione o **regras de diretriz do Design básico Microsoft** conjunto de regras de análise de código.  
  
-   Adicione seu próprio código à classe.  
  
-   Execute análise de código.  
  
-   Personalize o conjunto de regras.  
  
-   Executar análise de código e ver como o conjunto de regras personalização comportamento funciona.  
  
## <a name="using-rule-sets-with-code-analysis"></a>Usando conjuntos de regras com análise de código

Primeiro, crie uma biblioteca de classe simples.  
  
### <a name="create-a-class-library"></a>Criar uma biblioteca de classes  
  
1.  Sobre o **arquivo** menu, clique em **novo** e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo **tipos de projeto**, clique em **Visual C#**.  
  
3.  Em **Visual C#**, selecione **biblioteca de classes**.  
  
4.  No **nome** caixa de texto, digite **RuleSetSample** e, em seguida, clique em **Okey**.  
  
 Em seguida, você selecionará o **regras de diretriz do Design básico Microsoft** conjunto de regras e salvá-lo com o seu projeto.  
  
### <a name="select-a-code-analysis-rule-set"></a>Selecione um conjunto de regras de análise de código  
  
1.  Sobre o **analisar** menu, clique em **configurar a análise de código para RuleSetSample**.  
  
     As configurações de análise de código aparecem.  
  
2.  No **executar esse conjunto de regras** lista suspensa, selecione **Microsoft todas as regras**.  
  
     Para obter mais informações sobre os conjuntos de regras disponíveis, consulte [referência de conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md).  
  
     No menu Arquivo, clique em **salvar itens selecionados** para atualizar o arquivo de projeto com informações sobre o conjunto de regras que você selecionou e suas configurações.  
  
    > [!TIP]
    >  Em uma situação real, uma prática recomendada usar para priorizar os problemas que você deseja direcionar com análise de código é iniciar com o **mínimo recomendado regras** conjunto de regras e corrigir os problemas desejados e, em seguida, adicionar paulatinamente mais regras ou regra define a encontrar e corrigir os problemas adicionais.  
  
 Em seguida, você adicionará um código para a biblioteca de classes que será usada para demonstrar as violações de CA1704 "Identificadores devem ser grafados corretamente" regra de análise de código. Para obter mais informações, consulte [CA1704: os identificadores devem ser grafados corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
### <a name="add-your-own-code"></a>Adicionar seu próprio código  
  
-   No Solution Explorer, abra o arquivo Class1.cs e substitua o código existente pelo seguinte:  
  
    ```csharp
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }
    ```
  
Agora você pode executar a análise de código no projeto RuleSetSample e procure os erros e avisos gerados na janela lista de erros.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Executar análise de código no projeto RuleSetSample  
  
1.  Sobre o **analisar** menu, clique em **executar análise de código em RuleSetSample**.  
  
2.  Na janela lista de erros, clique em **avisos** e, em seguida, clique no **descrição** cabeçalho de coluna para classificar os avisos ordem alfanumérica.  
  
     Em um aplicativo do mundo real, você deve corrigir quaisquer violações de regra vale a pena corrigir neste ponto, ou opcionalmente desativar ou suprimir uma regra se você determinou que não era vale a pena corrigir. Para obter mais informações, consulte [suprimir avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3.  Observe os avisos de CA1704. Essas violações nessa regra indicam que "considere fornecer um nome mais significativo para os parâmetros." Você pode corrigir o problema no seu código, ou você pode desabilitar a regra, conforme explicado no próximo procedimento.  
  
 Em seguida, você personalizará o conjunto de regras para excluir o aviso CA1704, "Identificadores devem ser grafados corretamente".  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizar a regra definida para seu projeto desabilitar uma regra específica  
  
1.  Sobre o **analisar** menu, clique em **configurar a análise de código para RuleSetSample**.  
  
2.  No **executar esse conjunto de regras** suspensa lista, verifique o **Microsoft todas as regras** regra conjunto ainda está realçado e, em seguida, clique em **abrir**. A página do conjunto de regra é exibida.  
  
3.  Expanda o nó de categoria de Microsoft.Naming e, em seguida, selecione o aviso CA1704.  
  
4.  Sob o **ação** coluna, selecione **None.** Isso impede que CA1704 exibir como um aviso ou erro na janela lista de erros.  
  
     Agora é um bom momento para fazer experiências com vários botões de barra de ferramentas e opções para se familiarizar com eles de filtragem. Por exemplo, você pode usar o **Group By** lista suspensa para ajudar a localizar uma regra específica, ou uma categoria de regras. Outro exemplo é que você pode usar o **ocultar regras desabilitadas** botão na barra de ferramentas de páginas de conjunto de regra para ocultar ou Mostrar todas as regras com o **ação** coluna definida como **nenhum**. Isso pode ser útil se você deseja procurar todas as regras que desativada para verificar que você ainda deseja sejam desabilitadas.  
  
5.  No menu Exibir, clique na janela Propriedades. Tipo **meu conjunto de regras personalizado** na caixa Nome da janela de ferramentas de propriedades. Isso altera o nome de exibição da nova regra definida [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE.  
  
6.  Sobre o **arquivo** menu, clique em **salvar Rules.ruleset todos da Microsoft** salvar a regra personalizada definida. Navegue até a pasta raiz do seu projeto. Em **o nome do arquivo** caixa de texto, digite **MyCustomRuleSet**. O conjunto de regras personalizado agora pode ser selecionado para uso com o seu projeto.  
  
Com o novo conjunto de regras criado, agora você tem que definir as configurações de projeto para especificar que você deseja usar a nova regra com ele.  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Especifique a nova regra definida para uso com o seu projeto  
  
1.  No Gerenciador de soluções, clique com o botão direito e, em seguida, selecione **propriedades**.  
  
2.  No **propriedades** , clique em **análise de código**.  
  
     No **executar esse conjunto de regras** lista suspensa, clique em  **\<procurar... >**. Navegue até a pasta raiz do seu projeto de código e, em seguida, selecione **MyCustomRuleSet.ruleset**. Este é o novo conjunto de regras que você criou no procedimento anterior.  
  
3.  Sobre o **arquivo** menu, clique em **salvar** para salvar sua configuração de projeto. O conjunto de regras personalizado agora pode ser usado com o seu projeto.  
  
 Por fim, você executará novamente usando o conjunto de regras MyCustomRuleSet de análise de código. Observe que a janela lista de erros não exibirá a violação de regra de desempenho CA1704.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Executar análise de código no projeto RuleSetSample pela segunda vez  
  
1.  Sobre o **analisar** menu, clique em **executar análise de código em RuleSetSample**.  
  
2.  Na janela lista de erros, observe que quando você clica em **avisos**, você não verá mais as violações do aviso CA1704 para a regra "Identificadores devem ser grafados corretamente".  
  
## <a name="see-also"></a>Consulte também

[Como: configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[Referência do conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md)