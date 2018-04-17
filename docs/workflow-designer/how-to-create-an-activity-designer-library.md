---
title: 'Como: criar uma biblioteca do Designer de atividade | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0dc336db00f8a638cf20e6af79f2cf7ec030a5f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-activity-designer-library"></a>Como: Crie uma biblioteca do designer de atividade
Designers personalizados de atividade permitem que você crie uma interface de usuário para uma atividade padrão ou personalizado. Você controla a complexidade da interface do usuário e tem a capacidade de criar mais de um designer de atividade para uma atividade. Este cenário permite que você crie os designers que são personalizados para mais audiências.

### <a name="to-create-an-activity-designer-library"></a>Para criar uma biblioteca do designer de atividade

1.  Inicie o [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...**  para abrir o **novo projeto** caixa de diálogo.

3.  No **tipos de projeto** painel, selecione **fluxo de trabalho** do **Visual C#** ou **Visual Basic** agrupamentos dependendo de sua preferência idioma.

4.  No **modelos** painel, selecione **biblioteca do Designer de atividade**.

5.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.

6.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7.  No **solução** caixa, digite um nome descritivo para sua solução e clique em **Okey**.

    > [!NOTE]
    > Se você quiser adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra essa solução no [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], clique com o botão direito na solução em **Solution Explorer**e selecione **adicionar**, em seguida, **Novo projeto...**  para abrir o **novo projeto** caixa de diálogo. Continuar conforme descrito acima neste procedimento.

8.  O modelo de projeto cria uma definição de designer de atividade em XAML e o arquivo de código de implementação no código-fonte. O Designer de fluxo de trabalho do Windows é aberto e exibe a tela de seu designer de atividade.

9. Arraste [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] controla do **caixa de ferramentas** para a superfície de design para usá-los em seu designer de atividade personalizada.  Para obter um exemplo de como implementar um designer de atividade personalizada, consulte [como: criar um Designer de atividade personalizado](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

    > [!WARNING]
    > Designers de atividade personalizada podem ser usados para atividades personalizadas, bem como para padrão [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]atividades.

## <a name="see-also"></a>Consulte também

- [Criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)