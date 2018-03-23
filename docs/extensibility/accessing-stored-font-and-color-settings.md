---
title: Acessando configurações de cor e fonte armazenado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 78fc7c343cc570742d2d246a60d3093485800132
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="accessing-stored-font-and-color-settings"></a>Acessando configurações de cor e fonte armazenado
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) armazena as configurações modificadas para fontes e cores no registro. Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface para acessar essas configurações.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Para iniciar a persistência de estado de fontes e cores
 Informações de fonte e cor são armazenadas por categoria no seguinte local do registro: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<versão do Visual Studio >*\FontAndColors\\  *\<CategoryGUID >*], onde  *\<CategoryGUID >* é o GUID de categoria.

 Portanto, para iniciar a persistência, um VSPackage deve:

-   Obter um <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface chamando `QueryService` em relação ao provedor de serviços globais.

     `QueryService` deve ser chamado com um argumento de ID do serviço de `SID_SVsFontAndColorStorage` e um argumento de ID de interface de `IID_IVsFontAndColorStorage`.

-   Use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método para abrir uma categoria a ser mantido usando o GUID da categoria e um sinalizador de modo como argumentos.

     O modo especificado pelo `fFlags` argumento, é construído a partir de valores a <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumeração. Este modo de controles:

    -   As configurações que podem ser acessadas por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

    -   Todas as configurações ou apenas as configurações que modificam os usuários e que são recuperáveis por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

    -   A maneira de propagar as alterações nas configurações do usuário.

    -   O formato dos valores de cor que são usados.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>A persistência de estado de uso de fontes e cores
 Persistência de fontes e cores envolve:

-   Sincronizando as configurações de IDE com as configurações armazenadas no registro.

-   Propagação de informações de modificação do registro.

-   Configurando e recuperando as configurações armazenadas no registro.

 Sincronizar as configurações de armazenamento com as configurações de IDE é amplamente transparente. O IDE subjacente automaticamente grava as configurações atualizadas para **itens de exibição** para as entradas do registro das categorias.

 Se vários VSPackages compartilham uma categoria específica, um VSPackage deve exigir que os eventos são gerados quando os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface são usadas para modificar as configurações do registro armazenado.

 Por padrão, a geração de eventos não está habilitada. Para habilitar a geração de eventos, uma categoria deve ser aberta usando <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Abrir uma categoria faz com que o IDE chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> método que implementa um VSPackage.

> [!NOTE]
>  Modificações por meio de **fontes e cores** página de propriedade geram eventos independentes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface para determinar se é necessária uma atualização de configurações de fonte e cor em cache antes de chamar os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> classe.

### <a name="storing-and-retrieving-information"></a>Armazenar e recuperar informações
 Para obter ou definir informações de que um usuário pode modificar para um item de exibição nomeada em uma categoria de abrir, VSPackages chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> métodos.

 Informações sobre a fonte de atributos para uma categoria específica é obtida usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> métodos.

> [!NOTE]
>  O `fFlags` argumento que é passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método categoria tiver sido aberto define o comportamento do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos. Por padrão, esses métodos retornam somente informações sobre como exibir os itens que foram alterados. No entanto, se uma categoria é aberta usando o <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> sinalizador, ambos atualizado e itens de exibição inalterado podem ser acessados por <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 Por padrão, somente alterado **itens de exibição** informação é mantida no registro. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface não pode ser usada para recuperar todas as configurações de fontes e cores.

> [!NOTE]
>  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos retornam REGDB_E_KEYMISSING, (0x80040152L) quando você usá-las para recuperar informações sobre inalterado **itens de exibição**.

 As configurações de todos os **exibir itens** em uma determinada **categoria** pode ser obtida usando os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Implementação de categorias personalizadas e itens de exibição](../extensibility/implementing-custom-categories-and-display-items.md)