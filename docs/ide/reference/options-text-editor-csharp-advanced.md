---
title: Opções, Editor de Texto, C#, Avançado
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a7675d711a4a1df6af4643a459f49b6ef518e5b4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950680"
---
# <a name="options-text-editor-c-advanced"></a>Opções, Editor de Texto, C#, Avançado

Use a página de opções **Avançado** para modificar as configurações de formatação do editor, de refatoração de código e de comentários da documentação XML para C#. Para acessar essa página de opções, escolha **Ferramentas** > **Opções** e, em seguida, **Editor de Texto** > **C#** > **Avançado**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="analysis"></a>Análise

- Habilitar análise de solução completa

   Permite a análise de código em todos os arquivos na solução, não apenas nos arquivos de código abertos. Para obter mais informações, confira [Análise de solução completa](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

- Executar análise de recurso do editor em processo externo (experimental)

## <a name="using-directives"></a>Usando diretivas

- Colocar as diretivas “System” primeiro ao classificar os usos

- Separar usando grupos de diretivas

- Sugerir usos para tipos em assemblies de referência

- Sugerir usos para tipos em pacotes NuGet

## <a name="highlighting"></a>Realce

- Realçar referências a símbolo sob o cursor

   Quando o cursor é posicionado em um símbolo, ou ao clicar em um símbolo, todas as instâncias desse símbolo no arquivo de código são realçadas.

- Realçar palavras-chave relacionadas sob o cursor

## <a name="outlining"></a>Estrutura de tópicos

- Entre no modo estrutura de tópicos quando os arquivos abrem

   Quando selecionado, descreve o arquivo de código automaticamente, o que cria blocos de código recolhíveis. Na primeira vez que um arquivo é aberto, blocos #regions e blocos de códigos inativos são recolhidos.

- Mostrar separadores de linha de procedimento

- Mostrar estrutura de tópicos para construções no nível da declaração

- Mostrar estrutura de tópicos para construções no nível do código

- Mostrar estrutura de tópicos para regiões de pré-processador e de comentários

- Recolher #regions ao recolher para definições

## <a name="fading"></a>Esmaecimento

- Esmaecer usos não utilizados

- Esmaecer código inacessível

## <a name="block-structure-guides"></a>Guias de estrutura de bloco

- Mostrar guias para construções no nível da declaração

- Mostrar guias para construções no nível do código

## <a name="editor-help"></a>Ajuda do Editor

- Gerar comentários da documentação XML para ///

   Quando selecionado, insere os elementos XML dos comentários da documentação XML depois que você digita a introdução de comentário `///`. Para obter mais informações sobre a documentação XML, confira [Comentários da documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

- Inserir \* no início das novas linhas ao escrever comentários /\* \*/

- Mostrar visualização para acompanhamento de renomeação

- Dividir literais de cadeia de caracteres ao pressionar Enter

- Relatar espaços reservados inválidos nas chamadas a 'string.Format'

## <a name="extract-method"></a>Extrair Método

- Não colocar ref nem out no struct personalizado

## <a name="implement-interface-or-abstract-class"></a>Implementar Interface ou classe abstrata

- Ao inserir propriedades, eventos e métodos, coloque-os com outros membros do mesmo tipo ou no final

- Ao gerar propriedades, prefira propriedades de lançamento ou prefira propriedades automáticas

## <a name="see-also"></a>Consulte também

- [Como inserir comentários XML para geração de documentação](../../ide/reference/generate-xml-documentation-comments.md)
- [Comentários de documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentando seu código com comentários em XML (Guia do C#)](/dotnet/csharp/codedoc)
- [Configurando opções do editor específicas a um idioma](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)