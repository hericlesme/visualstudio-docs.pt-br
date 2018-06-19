---
title: Controle de glifo (VSPackage de controle do código-fonte) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c3787b0afad7f89743950a922d5b19c2d204bdd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130710"
---
# <a name="glyph-control-source-control-vspackage"></a>Controle de glifo (VSPackage de controle de origem)
Parte da integração profunda disponível para VSPackages do controle de origem é a capacidade de exibir suas próprias glifos para indicar o status dos itens no controle de origem.  
  
## <a name="levels-of-glyph-control"></a>Níveis de controle de glifo  
 Um glifo de estado é um ícone que indica o status atual de um item quando exibidos, por exemplo, em **Solution Explorer** ou **exibição de classe**. Um controle de origem VSPackage pode ter dois níveis de controle de glifo. Ele pode limitar a escolha de glifos para um conjunto predefinido de glifos fornecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ou pode definir um conjunto personalizado de glifos a ser exibido.  
  
### <a name="default-set-of-glyphs"></a>Conjunto padrão de glifos  
 Para determinar os glifos de estado associados um item no **Solution Explorer**, um projeto solicita o glifo de estado do controle de origem usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Um controle de origem VSPackage pode optar por manter a opção de glifos limitado para glifos predefinidos fornecidos pelo IDE. Nesse caso, o VSPackage volta passa uma matriz de valores que representam as enumerações de glifos que são definidas em vsshell.idl. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Este é um conjunto predefinido de glifos definido pelo IDE, como um cadeado para glifo "Check In" e uma marca de seleção como o símbolo "Check-Out".  
  
### <a name="custom-set-of-glyphs"></a>Conjunto personalizado de glifos  
 Um controle de origem VSPackage pode usar seus próprio glifos para uma exclusiva "aparência" quando ele está instalado. Quando um novo controle de origem VSPackage está ativo, deve ser capaz de começar a usar seus próprio glifos mesmo se uma fonte anterior controlar VSPackage ainda está carregado, mas inativo. Nesse modo, o controle de origem VSPackage ainda pode usar os ícones existentes para manter uma aparência consistente com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se ele escolhe.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> serviço oferece suporte a uma interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, que pode implementar o VSPackage e que será exigido pelo IDE. Quando o IDE faz uma solicitação, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] por sua vez tentará obter essa interface do controle de origem atualmente registrados VSPackage. Se existir a interface no VSPackage registrado, a solicitação do IDE para glifos personalizados for bem-sucedida; Caso contrário, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE usa seu conjunto padrão de glifos.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> método é usado pela [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para obter uma lista de imagens, mostrando o controle da fonte de vários estados. O controle de origem VSPackage retorna ao IDE um identificador para a lista de imagens para seus glifos personalizados. O IDE faz uma cópia da lista de imagens neste ponto e usa-o posteriormente para escolher os glifos para exibir. Se não há suporte para a nova interface ou `IVsSccGlyphs::GetCustomGlyphList` método retornará E_NOTIMPL, em seguida, o IDE obtém seus glifos na lista padrão de glifos fornecido pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>