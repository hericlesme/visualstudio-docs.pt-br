---
title: Definindo uma imagem de plano de fundo em um diagrama
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6b81bfcf0be55236b9b9321a4f04a8dd03f8e3ab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949887"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Definindo uma imagem de plano de fundo em um diagrama
No SDK de Visualização e Modelagem do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode configurar a imagem de plano de fundo para um designer gerado usando código personalizado.

## <a name="setting-the-background-image"></a>Configurando a imagem de plano de fundo

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Para configurar uma imagem de plano de fundo de um designer gerado

1.  Copie o arquivo de imagem que você deseja usar como plano de fundo do diagrama no diretório Dsl\Resources do projeto atual.

2.  Em **Solution Explorer**, clique na pasta Dsl\Resources, aponte para **adicionar**e, em seguida, clique em **Item existente**.

3.  No **Add Existing Item** caixa de diálogo, navegue até a pasta Dsl\Resources.

4.  No **arquivos do tipo** lista, clique em **arquivos de imagem**.

5.  Clique no arquivo de imagem que você copiou para o diretório e, em seguida, clique em **adicionar**.

6.  Clique com botão direito Dsl e, em seguida, clique em **propriedades** para abrir as propriedades do projeto Dsl.

7.  Sobre o **recursos** , clique em **este projeto não contém um arquivo de recursos padrão. Clique aqui para criar um.**

8.  Adicione o arquivo de imagem para o arquivo de recurso arrastando a imagem do **Solution Explorer** na janela de recursos.

9. Abra o menu Arquivo e clique na opção para salvar as propriedades do projeto.

10. Verifique se o arquivo Dsl\Properties\Resources.resx existe e se possui o arquivo Resources.Designer.cs nele.

11. Se Resources.Designer.cs estiver ausente, clique no arquivo resx em **Gerenciador de soluções**.

12. No **propriedades** janela, defina o `Custom Tool` propriedade `ResXFileCodeGenerator`.

13. Em **Solution Explorer**, com o botão direito no projeto Dsl, aponte para **adicionar**e clique em **nova pasta**.

14. O nome da pasta **personalizado**.

15. Clique na pasta personalizada, aponte para **adicionar**e clique em **Novo Item**.

16. No **Adicionar Novo Item** na caixa de **modelos** lista, clique em **arquivo de código**.

17. No **nome** , digite `BackgroundImage.cs`e clique em **adicionar**.

18. Copie o código a seguir no arquivo BackgroundImage.cs, ajustando o namespace, o nome da classe do diagrama e o nome do recurso do arquivo de imagem.

     Substitua "MyDiagramClass" pelo nome da classe parcial do diagrama definido em Dsl\GeneratedCode\Diagrams.cs. Também é possível recuperar o namespace correto do arquivo Dsl\GeneratedCode\Diagrams.cs.

    ```
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Para obter mais informações sobre como personalizar o modelo com o código de programa, consulte [navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Consulte também

- [Definindo formas e conectores](../modeling/defining-shapes-and-connectors.md)
- [Personalizando campos de texto e imagem](../modeling/customizing-text-and-image-fields.md)
- [Navegando por um modelo no código do programa e atualizando-o](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
