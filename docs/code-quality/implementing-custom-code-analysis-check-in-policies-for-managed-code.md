---
title: Implementando políticas de seleção da análise de código personalizado para código gerenciado no Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c60c682fe4613495a90b78c47189dc6b84b38399
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923544"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementar políticas do Check-in de análise de código personalizado para código gerenciado

Uma política de check-in Especifica um conjunto de regras que devem ser executados por membros de um projeto de equipe no código-fonte antes de análise de código é verificada no controle de versão. A Microsoft fornece um conjunto de padrão *conjuntos de regras* regras de análise de código desse grupo em áreas funcionais. *Conjuntos de regras de política de check-in personalizado* especificar um conjunto de regras de análise de código que são específicos para um projeto de equipe. Um conjunto de regras é armazenado em um arquivo. RuleSet.

Políticas de check-in são definidas no nível de projeto de equipe e especificadas pelo local de um arquivo. RuleSet na árvore de controle de versão. Não há nenhuma restrição sobre o local do controle de versão do conjunto de regra personalizada de política de equipe.

Análise de código está configurada para os projetos individuais de código na janela Propriedades para cada projeto. Uma regra personalizada definida para um projeto de código é especificada pelo local físico do arquivo. RuleSet no computador local. Quando um arquivo. RuleSet é especificado que está localizado na mesma unidade como o projeto de código, o Visual Studio usa um caminho relativo para o arquivo de configuração do projeto.

É uma prática sugerida para a criação de um conjunto de regras personalizado de projeto de equipe armazenar o arquivo. RuleSet política de check-in em uma pasta especial que não é uma parte de qualquer projeto de código. Se você armazenar o arquivo em uma pasta dedicada, você pode aplicar permissões que restringem quem podem editar o arquivo de regra e você pode mover facilmente a estrutura de diretório que contém o projeto para outro diretório ou computador.

## <a name="create-the-team-project-custom-check-in-rule-set"></a>Criar o conjunto de regra personalizada de Check-in do projeto de equipe

Para criar uma regra personalizada definida para um projeto de equipe, você primeiro crie uma pasta especial para o conjunto de regras de política de check-in **Gerenciador de controle do código-fonte**. Em seguida, criar o arquivo de conjunto de regras e adicioná-lo ao controle de versão. Por fim, você pode especificar o conjunto de regras como a código check-in de política de análise para o projeto de equipe.

> [!NOTE]
> Para criar uma pasta em um projeto de equipe, primeiro você deve mapear a raiz do projeto de equipe em um local no computador local.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Para criar a pasta de controle de versão para o conjunto de regras de política de check-in

1. No Team Explorer, expanda o nó do projeto de equipe e, em seguida, clique em **controle de origem**.

2. No **pastas** painel, clique com botão direito do projeto de equipe e, em seguida, clique em **nova pasta**.

3. No painel de controle do código fonte principal, clique com botão direito **nova pasta**, clique em **Renomear**e digite um nome para a regra definir pasta.

### <a name="to-create-the-check-in-policy-rule-set"></a>Para criar o conjunto de regras de política de check-in

1. Sobre o **arquivo** , aponte para **novo**e, em seguida, clique em **arquivo**.

2. No **categorias** lista, clique em **geral**.

3. No **modelos** lista, clique duas vezes em **conjunto de regras de análise de código**.

4. [Especifique as regras de](../code-quality/how-to-create-a-custom-rule-set.md) para incluir no conjunto de regras e, em seguida, salvar a regra de conjunto de arquivo para a pasta de conjunto de regras que você criou.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Para adicionar a regra definir arquivos ao controle de versão

1. Em **Gerenciador de controle do código-fonte**, com o botão direito na nova pasta e, em seguida, clique em **adicionar itens à pasta**.

     Para obter mais informações, consulte [Git e VSTS](/vsts/git/overview).

2. Clique na regra definir o arquivo que você criou e clique **concluir**.

     O arquivo é adicionado ao controle de origem e check-out para você.

3. No **Gerenciador de controle do código-fonte** janela de detalhes, clique no nome de arquivo e, em seguida, clique em **Check-in de alterações pendentes**.

4. No **Check-in** caixa de diálogo, você tem a opção para adicionar um comentário e, em seguida, clique em **Check-In**.

    > [!NOTE]
    > Se você já configurou uma política de check-in do analysis código para seu projeto de equipe e você tiver selecionado o **impor check-in para conter somente os arquivos que fazem parte da solução atual**, você irá disparar um aviso de falha de política. Na caixa de diálogo Falha de política, selecione **substituir falha da política e continuar o check-in**. Adicione um comentário necessário e, em seguida, clique em **Okey**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Para especificar a regra definir o arquivo como a política de check-in

1. Sobre o **Team** , aponte para **as configurações de projeto de equipe**e, em seguida, clique em **controle de origem**.

2. Clique em **política de Check-in**e, em seguida, clique em **adicionar**.

3. No **política de Check-in** lista, clique duas vezes em **análise de código**e certifique-se de que o **impor análise de código para código gerenciado** caixa de seleção é marcada.

4. No **executar esse conjunto de regras** lista, clique em  **\<Selecionar conjunto de regras de controle de origem >**.

5. Digite o caminho do arquivo de conjunto de regras de política de check-in no controle de versão.

     O caminho deve estar de acordo com a seguinte sintaxe:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Você pode copiar o caminho usando um dos procedimentos a seguir em **Gerenciador de controle do código-fonte**:

    - No **pastas** painel, clique na pasta que contém o arquivo de conjunto de regras. Copie o caminho de controle de versão da pasta que aparece no **fonte** caixa e, em seguida, digite o nome do arquivo de conjunto de regras manualmente.

    - Na janela de detalhes, clique no arquivo de conjunto de regra e, em seguida, clique em **propriedades**. Sobre o **geral** guia, copie o valor em **nome do servidor**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizar projetos de código para o conjunto de regras de política de Check-in

Você especificar uma regra de política de check-in do projeto de equipe definido como o conjunto de regras de análise de código de uma configuração de projeto de código na caixa de diálogo Propriedades do projeto de código. Se o conjunto de regras está localizado na mesma unidade como o projeto de código, um caminho relativo é usado para especificar o conjunto de regras quando o caminho é selecionado na caixa de diálogo. Estruturas de controle habilita o caminho relativo as configurações de propriedades do projeto para ser portátil para outros computadores que usam a versão local semelhante.

### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Para especificar uma regra de projeto de equipe definido como o conjunto de regras de um projeto de código

1. Se necessário, recupere a pasta do conjunto de regra de política de check-in e o arquivo de controle de versão.

   Você pode executar esta etapa no **Gerenciador de controle do código-fonte** clicando com o conjunto de regras de pasta e, em seguida, clicando em **obter versão mais recente**.

2. Em **Solution Explorer**, clique com botão direito do código e, em seguida, clique em **propriedades**.

3. **Clique em análise de código**.

4. Se necessário, clique nas opções apropriadas no **configuração** e **plataforma** lista.

5. Para executar a análise de código toda vez que o projeto de código é criado usando a configuração especificada, selecione o **habilitar análise de código no Build (define a constante CODE_ANALYSIS)** caixa de seleção.

6. Para ignorar o código em componentes de outras empresas, selecione o **Suprimir resultados do código gerado** caixa de seleção.

7. No **executar esse conjunto de regras** lista, clique em  **\<procurar... >**.

8. Especifique a versão local do arquivo de conjunto de regras de política de check-in.