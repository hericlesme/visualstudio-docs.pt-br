---
title: Implementação de categorias personalizadas e itens de exibição | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9593a7addcd9a3f100f45f69e7e692c396e33bfe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementação de categorias personalizadas e itens de exibição
Um VSPackage pode fornecer controle de fontes e cores de texto para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) por meio de categorias personalizadas e itens de exibição.

 Categorias personalizadas e exibir itens estão no **fontes e cores** página de propriedades. Para abrir o **fontes e cores** página de propriedade, no **ferramentas** menu, clique em **opções**. Expanda **ambiente** e, em seguida, clique em **fontes e cores**.

 Ao usar esse mecanismo, VSPackages deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface e suas interfaces associadas.

 Em princípio, esse mecanismo pode ser usado para modificar todas as existentes **exibir itens** e **categorias** que eles contêm. No entanto, ele não deve ser usado para modificar o **texto EditorCategory** ou seus **exibir itens**. Para obter mais informações, consulte [visão geral de cor e de fonte](../extensibility/font-and-color-overview.md).

 Para implementar personalizado **categorias** ou **exibir itens**, um VSPackage deve:

-   Crie ou identifique categorias no registro.

     A implementação do IDE do **fontes e cores** página de propriedades usa essas informações para consultar corretamente para o serviço de suporte a uma determinada categoria.

-   Criar ou identificar grupos (opcionais) no registro.

     Ele pode ser útil definir um grupo, que representa a união de duas ou mais categorias. Se um grupo é definido, o IDE automaticamente mescla subcategorias e distribui os itens de exibição dentro do grupo.

-   Implementa o suporte do IDE.

-   Controlar as alterações de fonte e cor.

 Para obter informações, consulte [acessar fonte armazenado e as configurações de cor](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>Para criar ou identificar categorias

-   Construir um tipo especial de entrada de registro de categoria em [HKLM\Software\Microsoft. \Visual Studio\\*\<versão do Visual Studio >*\FontAndColors\\`<Category>`]

     *\<Categoria >* é o nome da categoria não localizada.

-   Preencha o registro com dois valores:

    |Nome|Tipo|Dados|Descrição|
    |----------|----------|----------|-----------------|
    |Categoria|REG_SZ|GUID|Um GUID criado para identificar a categoria.|
    |Pacote|REG_SZ|GUID|O GUID do serviço VSPackage que oferece suporte a categoria.|

 O serviço especificado no registro deve fornecer uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> para a categoria correspondente.

## <a name="to-create-or-identify-groups"></a>Para criar ou identificar grupos

-   Construir um tipo especial de entrada de registro de categoria em [HKLM\Software\Microsoft. \Visual Studio\\*\<versão do Visual Studio >*\FontAndColors\\  *\<grupo >*]

     *\<grupo >* é o nome do grupo não localizada.

-   Preencha o registro com dois valores:

    |Nome|Tipo|Dados|Descrição|
    |----------|----------|----------|-----------------|
    |Categoria|REG_SZ|GUID|Um GUID criado para identificar o grupo.|
    |Pacote|REG_SZ|GUID|O GUID do serviço que dá suporte à categoria.|

 O serviço especificado no registro deve fornecer uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> para o grupo correspondente.

## <a name="to-implement-ide-support"></a>Para implementar o suporte IDE

-   Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, que retorna um uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface ou uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface IDE para cada **categoria** ou grupo GUID fornecida.

-   Para cada **categoria** oferece suporte a ele, um VSPackage implementa uma instância separada do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface.

-   Os métodos implementados por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> deve fornecer o IDE com:

    -   Lista de **exibir itens** no **categoria.**

    -   Nomes localizáveis para **exibir itens**.

    -   Exibir informações de cada membro de **categoria**.

    > [!NOTE]
    >  Cada **categoria** deve conter pelo menos um **exibir o item**.

-   O IDE usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface para definir uma união de várias categorias.

     Sua implementação fornece o IDE com:

    -   Uma lista da **categorias** que compõem um grupo específico.

    -   Acesso a instâncias de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> suporte cada **categoria** dentro do grupo.

    -   Nomes de grupo localizável.

-   Atualizando o IDE:

     O IDE armazena informações sobre **fontes e cores** configurações. Portanto, depois de qualquer modificação do IDE **fontes e cores** configuração, é aconselhável para certificar-se de que o cache é atualizado.

 Atualizando o cache é feito por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> de interface e pode ser executados itens selecionados globalmente ou apenas em.

## <a name="to-handle-font-and-color-changes"></a>Para lidar com a fonte e cor alterações
 Para suporte a coloração de texto que exibe um VSPackage corretamente, o serviço de colorização que suporta o VSPackage deve responder às alterações iniciada pelo usuário feitas por meio de **fontes e cores** página de propriedades. Um VSPackage faz isso por:

-   Tratamento de eventos gerados pelo IDE Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interface.

     O IDE chama o método apropriado seguindo as modificações do usuário da **fontes e cores** página. Por exemplo, ele chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> método se uma nova fonte é selecionada.

     -ou-

-   Sondando o IDE para que as alterações.

     Isso pode ser feito por meio do sistema implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface. Embora principalmente para suporte de persistência, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> método pode ser usado para obter informações de fontes e cores para **exibir itens**. Para obter mais informações, consulte [acessar fonte armazenado e as configurações de cor](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Para garantir que os resultados obtidos por meio de sondagem estejam corretos, que pode ser útil usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface para determinar se uma liberação de cache e atualização são necessárias antes de chamar os métodos de recuperação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Obtendo informações de cores para coloração de texto e fonte](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Acessando configurações de cor e fonte armazenado](../extensibility/accessing-stored-font-and-color-settings.md)
- [Como: acessar o esquema de cores e fontes internas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Visão geral de cor e de fonte](../extensibility/font-and-color-overview.md)