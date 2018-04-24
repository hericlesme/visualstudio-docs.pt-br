---
title: Como criar uma solução de linguagem específica do domínio
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 955c8f7a6dbc55d61b1cba77f38b2d394742e49c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Como criar uma solução de linguagem específica do domínio
Uma linguagem específica de domínio (DSL) é criada usando um especializado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução.

## <a name="prerequisites"></a>Pré-requisitos
 Antes de iniciar este procedimento, você deve primeiro instalar esses componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|SDK de Visualização e Modelagem do Visual Studio||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>Criando uma solução de linguagem específica de domínio

#### <a name="to-create-a-domain-specific-language-solution"></a>Para criar uma solução de linguagem específica de domínio

1.  Inicie o assistente DSL.

    1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.

    2.  A caixa de diálogo **Novo Projeto** é exibida.

    3.  Em **tipos de projeto**, expanda o **outros tipos de projetos** nó e clique em **extensibilidade**.

    4.  Clique em **Designer de linguagem específica de domínio**.

    5.  No **nome** , digite um nome para a solução. Clique em **OK**.

         O **Assistente de Designer de linguagem específica de domínio** é exibida.

        > [!NOTE]
        >  Preferencialmente, o nome que você digitar deve ser um Visual C# identificador válido, pois ela pode ser usada para gerar o código.

     ![Criar caixa de diálogo DSL](../modeling/media/create_dsldialog.png "Create_DSLDialog")

2.  Escolha um modelo DSL.

     No **selecionar opções de linguagem específica de domínio** página, selecione um dos modelos de solução como **mínimo idioma**. Escolha um modelo que é semelhante ao DSL que você deseja criar.

     Para obter mais informações sobre modelos de solução, consulte [escolhendo um modelo de solução de linguagem específica de domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).

3.  Digite uma extensão de nome de arquivo **extensão de arquivo** página. Ele deve ser exclusivo no seu computador e em todos os computadores nos quais você deseja instalar o DSL. Você deve ver a mensagem **nenhum aplicativo ou editores do Visual Studio usam essa extensão**.

    -   Se você usou a extensão de nome de arquivo anteriores DSLs experimentais que não foram totalmente instaladas, você pode limpá-los fora usando o **redefinir a instância Experimental** ferramenta, que pode ser encontrada na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menu SDK.

    -   Se houver outro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão que usa essa extensão de arquivo foi completamente instalado no seu computador, considere a possibilidade de desinstalá-lo. Sobre o **ferramentas** menu, clique em **Gerenciador de extensões**.

4.  Inspecionar e ajustar se necessário, os campos nas páginas restantes do assistente. Quando estiver satisfeito com as configurações, clique em **concluir**. Para obter mais informações sobre as configurações, consulte [páginas do Assistente de Designer DSL](#settings).

     O assistente cria uma solução que tem dois projetos que são nomeados **Dsl** e **DslPackage**.

    > [!NOTE]
    >  Se você vir uma mensagem que o alerta não executar modelos de texto de fontes não confiáveis, clique em **Okey**. Você pode definir essa mensagem não seja exibida novamente.

##  <a name="settings"></a> As páginas do Assistente do Designer de DSL
 Você pode deixar vários campos não alterados de seus valores padrão. No entanto, certifique-se de que você defina o campo de extensão de arquivo.

### <a name="solution-settings-page"></a>Página de configurações da solução
 **Modelo que você deseja basear sua linguagem específica de domínio?**
Escolha um modelo que é semelhante ao DSL que você deseja criar. Os modelos diferentes fornecem pontos de partida. Quando você seleciona um modelo de solução, o assistente exibe uma descrição. Para obter mais informações sobre modelos de solução, consulte [escolhendo um modelo de solução de linguagem específica de domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **O que você deseja nomear sua linguagem específica de domínio?**
O padrão é o nome da solução. Código é gerado no caso desse valor. Ele deve ser válido como um nome de classe c#.

### <a name="file-extension-page"></a>Página de extensão de arquivo
 **Qual extensão de modelo deve arquivos usam?**
Digite uma nova extensão de arquivo.

 Verifique se que essa extensão de arquivo não já foi registrado para uso neste computador, da seguinte maneira:

 Procure **outras ferramentas e aplicativos registrados para lidar com essa extensão**. Se você vir a mensagem **nenhum aplicativo ou editores do Visual Studio usam essa extensão**, em seguida, você pode usar essa extensão de arquivo.

 Se você vir uma lista de ferramentas ou pacotes, você deve fazer o seguinte:

-   Digite uma extensão de arquivo diferente.

     \- ou -

-   Redefinir o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instância Experimental. Isso cancelará todas as DSLs que você criou anteriormente. Sobre o **iniciar** menu, clique em **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**e, em seguida, **redefinir o Instância do Microsoft Visual Studio 2010 Experimental**. Você pode recriar outras DSLs que você deseja usar novamente.

     \- ou -

-   Se um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão que usa essa extensão de arquivo tiver sido completamente instalado no seu computador, desinstalá-lo. Sobre o **ferramentas** menu, clique em **Gerenciador de extensões**.

### <a name="product-settings-page"></a>Página de configurações do produto
 **O que é o nome do produto que pertence a nova linguagem específica de domínio?**
O padrão é o nome DSL.

 Esse valor é usado no Windows Explorer (ou Explorador de arquivos) para descrever os arquivos que têm essa extensão de arquivo.

 **O que é o nome da empresa que o produto pertence a?**
Nome da sua empresa.

 Esse valor é incorporado nas propriedades do pacote DSL AssemblyInfo.

 **O que é o namespace raiz para projetos nesta solução?**
O padrão é um nome composto de sua empresa e nomes de produtos.

### <a name="signing-page"></a>Página Assinatura
 **Criar um arquivo de chave de nome forte** a opção padrão é criar uma nova chave para assinar seu assembly DSL.

 **Use a chave de nome forte existente** Use esta opção se você deseja integrar seu DSL com outro assembly.

 Para obter mais informações sobre nomes fortes, consulte [Creating and Using Strong-Named Assemblies](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Consulte também

- [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)
- [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
