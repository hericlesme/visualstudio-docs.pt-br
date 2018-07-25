---
title: Perguntas e respostas sobre o IntelliCode
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079305"
---
# Perguntas Frequentes sobre o Visual Studio IntelliCode

Obrigado por seu interesse no Visual Studio IntelliCode! Esperamos que esta pequena seleção de perguntas frequentes responda a algumas das dúvidas que você possa ter.

## P. O que é o Visual Studio IntelliCode?

No Build 2018, a Microsoft anunciou o Visual Studio IntelliCode, uma nova funcionalidade que aprimora o desenvolvimento de software usando a IA. O IntelliCode ajuda desenvolvedores e equipes a escrever código com confiança, localizar problemas mais rapidamente e concentrar revisões de código.

Uma exibição antecipada de como o IntelliCode funciona mostrou como ele melhora o processo de desenvolvimento de software das seguintes maneiras:

- Fornece conclusões de código com percepção de contexto
- Orienta os desenvolvedores a aderir aos padrões e estilos de sua equipe
- Encontra problemas de código difíceis de detectar
- Concentra revisões de código chamando atenção para áreas que realmente importam

Os desenvolvedores podem encontrar mais informações e se inscrever para receber notícias e versões prévias privadas futuras em [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. O que o Visual Studio IntelliCode possibilita que os clientes façam?

O Visual Studio IntelliCode é um conjunto de recursos que oferecem novas melhorias de produtividade por meio de IA (inteligência artificial).

Os desenvolvedores podem [baixar uma extensão experimental](https://go.microsoft.com/fwlink/?linkid=872707) para o Visual Studio 2017 versão 15.7 e posteriores. Atualmente, a extensão fornece:

- O IntelliSense Aprimorado por IA, que prevê a API que provavelmente é a mais correta para uso pelo desenvolvedor, em vez de apenas apresentar uma lista de membros em ordem alfabética. Ele usa o contexto de código atual do desenvolvedor e padrões para fornecer essa lista dinâmica.

- Inferência de estilo de código e convenções de formatação que ajuda você a manter o código consistente criando dinamicamente um [arquivo .editorconfig](../create-portable-custom-editor-options.md) da base de código para definir estilos de codificação e formatos. Essas convenções permitem que o Visual Studio ofereça correções automáticas de estilo e formato para limpar o documento.

Atualizaremos a extensão com mais recursos nos próximos meses.

## P. Por que a inferência do EditorConfig faz com que o nome de arquivo seja precedido por 1?

Um problema conhecido na extensibilidade do Visual Studio fará com que o nome de arquivo .editorconfig seja precedido por 1 quando você o criar clicando com o botão direito do mouse e escolhendo **Adicionar > Novo Item**. Arquivos nomeados dessa maneira não são reconhecidos pelo processador do editorconfig no Visual Studio. Esse problema foi corrigido no Visual Studio 2017 versão 15.8 Versão Prévia 4, mas até essa versão, você pode resolver o problema removendo o 1 na caixa de diálogo **Adicionar Novo Item**.

## P. Não consigo ver minhas Convenções do EditorConfig entrando em vigor. Por quê?
Há duas razões comuns pelas quais esse problema pode ocorrer:

- Em versões do Visual Studio 2017 anteriores a 15.8 Versão Prévia 3, você precisará fechar e reabrir todos os documentos abertos para ver as convenções criadas no arquivo EditorConfig entrarem em vigor. Esse problema foi corrigido na versão 15.8 Versão Prévia 3.
- As convenções de formatação nunca são exibidas na **Lista de Erros** ou como “rabiscos” no código. No entanto, elas podem ser corrigidas usando a nova extensão Formatar Documento (Ctrl+K, Ctrl+D) no Visual Studio 2017 versão 15.8 Versão Prévia 3 ou posterior

## P. A extensão Formatar Documento não está corrigindo minhas convenções de estilo. Por quê?
Há duas razões comuns pelas quais esse problema pode ocorrer:

- Talvez você não esteja usando o Visual Studio 2017 versão 15.8 Versão Prévia 3 ou superior. Você precisará dessa versão para poder usar o comando estendido “Formatar Documento” e executar a limpeza de código adicional no documento atual.
- Talvez você não tenha aceito as correções de estilo. A funcionalidade estendida da funcionalidade de correção de problemas baseados em convenção da extensão Formatar Documento só abrange um conjunto fixo de problemas. Você pode alterar quais problemas são corrigidos em **Ferramentas – Opções** em **Editor de Texto > C# > Estilo de Código > Formatação > Geral > Configurações de Formatar Documento (Experimento)**. Observe que as configurações padrão não corrigem algumas convenções de estilo. Você pode aceitá-las por meio de **Ferramentas > Opções**. Por exemplo, a opção "Aplicar preferências de tipo implícitas/explícitas" executará as regras de estilo sobre o uso de `var`.

## P. Quais Convenções do EditorConfig podem ser inferidas pelo Visual Studio IntelliCode?

No momento, esse recurso é experimental e, portanto, ainda não damos suporte ao conjunto completo de convenções documentado na [referência de configurações de estilo de código](../editorconfig-code-style-settings-reference.md).

Atualmente, o IntelliCode pode inferir as seguintes convenções:

Convenções de formatação:

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

Convenções de estilo
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## P. Há outras funcionalidades que serão incluídas na extensão do Visual Studio IntelliCode?

Estamos trabalhando ativamente em diversos recursos que teremos o prazer de compartilhar publicamente assim que estiverem disponíveis. Inscreva-se para receber notícias e atualizações em [https://aka.ms/intellicode](https://aka.ms/intellicode) e seja o primeiro a saber quando novas funcionalidades estiverem disponíveis.

## P: O que torna o "IntelliSense assistido por IA" fornecido pelo IntelliCode melhor do que o IntelliSense comum da plataforma?

Com o IntelliCode, a lista de conclusão sugere a API que mais provavelmente é a correta para o desenvolvedor usar, em vez de apresentar uma simples lista de membros em ordem alfabética. Ele usa o contexto de código atual do desenvolvedor e padrões baseados em 2000 projetos de software livre de alta qualidade do GitHub, cada um deles com mais de 100 estrelas, para fornecer essa lista dinâmica. Os resultados formam um modelo que prevê as chamadas à API mais prováveis e mais relevantes.

## P: As sugestões de conclusão do IntelliCode são boas?

Estamos usando as recomendações do IntelliCode internamente na Microsoft há algum tempo e acreditamos que as sugestões são úteis. No entanto, só poderemos confirmar a utilidade dessas recomendações quando vocês a usarem ao codificar. Gostaríamos que vocês experimentassem a [extensão IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) no Visual Studio. Conte-nos como ela funciona para você e envie-nos seus comentários. Também treinaremos nosso modelo com base no que vocês escolherem em nossas recomendações e atualizaremos a extensão conforme o modelo se aperfeiçoa.

> [!NOTE]
> Nenhum código definido pelo usuário é coletado. Confira a pergunta sobre [privacidade](#privacy).

## P. Qual é o futuro do IntelliCode?

Estamos explorando uma ampla gama de maneiras de aumentar a produtividade do desenvolvedor usando IA e outras técnicas avançadas. No Microsoft Build 2018, mostramos uma exibição antecipada de alguns dos cenários em que acreditamos que a IA poderá ajudar os desenvolvedores, mas há muitos outros! Estamos interessados em saber mais dos desenvolvedores que fazem experimentos com o que mostramos, portanto, inscreva-se para receber notícias e atualizações em [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. Quanto custa?

No momento, não temos nenhum anúncio relacionado a preços.

## P. Quando o IntelliCode será lançado?

O IntelliSense assistido por IA do IntelliCode está, atualmente, em sua primeira versão prévia experimental. Continuaremos atualizando a extensão experimental e adicionaremos mais recursos no futuro. Não temos nenhuma agenda para uma versão final, mas apreciamos os comentários de desenvolvedores para que possamos fornecer as melhores experiências possíveis. Você pode se inscrever para receber notícias e atualizações em [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. Essa experiência só está disponível no Visual Studio e para o C#?

A experiência foi mostrada no build 2018 no Visual Studio de 2017 em uma base de código C#. No entanto, estamos ansiosos para expandir o IntelliCode para mais idiomas e ferramentas da família do Visual Studio no futuro.

## P. <a name="whynointellisense"/> Não consigo ver as sugestões do IntelliCode em minha experiência de edição do C#. O que está acontecendo?

As sugestões do IntelliCode são exibidas na interface do usuário padrão do Visual Studio IntelliSense para C#. As extensões que substituem essa interface do usuário impedem a exibição das sugestões "estreladas" do IntelliCode na parte superior da lista. Verifique se as extensões estão causando esse comportamento desativando-as e, em seguida, tentando usar o IntelliSense novamente.

Se isso não resolver o problema para você, relate o problema por meio da funcionalidade [Relatar um Problema](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) do Visual Studio e mencione o IntelliCode no relatório.

## P. Qual versão do Visual Studio é necessária para executar essa extensão?

A extensão IntelliCode do Visual Studio é compatível com o Visual Studio 2017 versão 15.7, versão prévia 5 e posteriores (todas as SKUs). A instalação da extensão será interrompida pela mensagem "Esta extensão não é instalável em nenhum dos produtos atualmente instalados." se a versão mínima exigida não estiver instalada.

## P. Essa experiência só está disponível em inglês?

O IntelliCode é uma extensão em versão prévia hoje, e estamos ansiosos para saber o quanto essas funcionalidades são úteis para um conjunto mais amplo de clientes. Quando o IntelliCode deixar de ser uma versão prévia, certamente consideraremos os locais e idiomas que terão suporte primeiro e como ele será oferecido, com base nos seus comentários.

## <a name="privacy"/> P: E quanto à privacidade? Vocês estão enviando meu código para a nuvem? Quais dados do cliente estão sendo enviados à Microsoft?

Os desenvolvedores são convidados a experimentar o Visual Studio IntelliCode como uma extensão de versão prévia experimental. A finalidade da extensão é permitir que os desenvolvedores testem os recursos do IntelliCode e forneçam comentários à equipe do produto.

Nós coletamos alguns dados anônimos de uso e de relatório de erros da extensão para ajudar a melhorar o produto. Nenhum código definido pelo usuário é enviado à Microsoft, mas nós coletamos informações sobre seu uso dos resultados do IntelliCode. Os dados só incluem os tipos e membros de .NET e de software livre que você selecionou na lista de sugestões do IntelliCode. Os desenvolvedores podem recusar o [Programa de Aperfeiçoamento da Experiência do Visual Studio](../../ide/visual-studio-experience-improvement-program.md), que desativa a coleta de dados para a extensão do IntelliCode também. Na barra de menus, selecione **Ajuda** > **Enviar Comentários** > **Configurações**. Na caixa de diálogo **Programa de Aperfeiçoamento da Experiência do Visual Studio**, selecione **Não, prefiro não participar** e, em seguida, selecione **OK**.

A extensão do IntelliCode pode pedir periodicamente que o desenvolvedor responda uma pesquisa, que também é anônima. Os usuários podem se inscrever para receber notícias e uma versão prévia privada futura. No momento, não é obrigatório que façam isso para usar a extensão experimental.

Recursos futuros podem exigir acesso a um serviço, que exigirá a inscrição. Quando esses recursos estiverem prontos para a versão prévia privada, publicaremos mais detalhes.
