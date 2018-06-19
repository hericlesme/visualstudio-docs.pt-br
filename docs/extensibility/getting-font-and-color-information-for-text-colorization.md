---
title: Obtendo informações de cores para coloração de texto e fonte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c86e37d6d7da9da0a6b0978770bf7d7564fa19c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129690"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtendo informações de cores para coloração de texto e fonte
O processo que renderiza ou exibe coloridos serão texto em elementos de interface do usuário depende do tipo de projeto, sua tecnologia e developer preferências. O **fontes e cores** página de propriedade armazena as configurações.

 A maioria das implementações que exibem texto coloridos serão necessário o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> e associados de interfaces para as configurações de exibição de apresentação, recuperar e armazenar texto.

> [!NOTE]
>  Ao personalizar o editor de núcleo (que dá suporte a **EditorCategory texto**), é recomendável que você use a tecnologia de cores no serviço de linguagem. Para obter mais informações, consulte [visão geral de cor e de fonte](../extensibility/font-and-color-overview.md).

## <a name="getting-default-font-and-color-information"></a>Obtendo informações de cor e a fonte padrão
 Todos os a **fontes e cores** as configurações de qualquer janela de exibição de texto devem ser especificadas no **exibir itens** de um **categoria**. Para obter mais informações, consulte [fontes e cores, ambiente, caixa de diálogo Opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Para colorir, um VSPackage deve obter atual **fontes e cores** configurações. Um VSPackage pode obter as configurações atuais das seguintes maneiras, dependendo de suas necessidades:

-   Use o mecanismo de persistência de fontes e cores para recuperar o estado atual ou armazenado. Para obter mais informações, consulte [acessar fonte armazenado e as configurações de cor](../extensibility/accessing-stored-font-and-color-settings.md).

-   Use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface de um serviço que fornece dados de fontes e cores para obter uma instância de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, se o VSPackage também não é o provedor de fonte e cor.

-   Implementar a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Para garantir que os resultados obtidos por meio de sondagem são atualizadas, pode ser útil usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface para determinar se uma atualização é necessária antes de chamar os métodos de recuperação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

Depois que você obteve as informações de fonte e cor, analise o texto a ser exibido para identificar elementos que requerem colorização. Exiba o texto na janela usando apropriadas fontes e cores.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Usando fontes e texto](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Trabalhando com cor](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (interface gráfica de dispositivo)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)