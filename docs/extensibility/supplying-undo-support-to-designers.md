---
title: Fornecendo suporte aos Designers de desfazer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98243c15f5f69a9aecba589b966d56a68201ab2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="supplying-undo-support-to-designers"></a>Fornecendo suporte de desfazer para Designers
Designers, editores, como o normalmente precisam dar suporte a operações de desfazer para que os usuários podem reverter suas alterações recentes ao modificar um elemento de código.  
  
 A maioria dos designers implementados no Visual Studio têm suporte de desfazer automaticamente fornecido pelo ambiente de.  
  
 Implementações de designer que precisam para fornecer suporte para o recurso desfazer:  
  
-   Fornece gerenciamento de desfazer ao implementar a classe base abstrata<xref:System.ComponentModel.Design.UndoEngine>  
  
-   Forneça persistência e CodeDOM dão suporte ao implementar a <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> classes.  
  
 Para obter mais informações sobre como escrever designers usando [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], consulte [Estendendo suporte em tempo de Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece uma infraestrutura de desfazer padrão por:  
  
-   Fornecer implementações de gerenciamento por meio de desfazer o <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> e <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes.  
  
-   Fornecendo suporte de CodeDOM através do padrão e persistência <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> implementações.  
  
## <a name="obtaining-undo-support-automatically"></a>Como obter suporte ao comando Desfazer automaticamente  
 Qualquer designer criado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tem suporte de desfazer automática e completo se, o designer:  
  
-   Usa um <xref:System.Windows.Forms.Control> com base em classe para sua interface do usuário.  
  
-   Utiliza o sistema de análise e geração de código padrão com base em CodeDOM de persistência e a geração de código.  
  
     Para obter mais informações sobre como trabalhar com o suporte de CodeDOM do Visual Studio, consulte [dinâmico geração de código-fonte e compilação](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usar o suporte de Desfazer Designer explícita  
 Designers devem fornecer seu próprio gerenciamento de desfazer se eles usam uma interface gráfica do usuário, conhecida como um adaptador de exibição, diferente daquela fornecida pelo <xref:System.Windows.Forms.Control>.  
  
 Um exemplo disso pode estar criando um produto com uma interface de design gráfico baseado na web em vez de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] com base em interface gráfica.  
  
 Nesses casos, será preciso registrar este adaptador de exibição com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>e fornecer gerenciamento de desfazer explícita.  
  
 Designers precisam fornecer suportam de CodeDOM e persistência se eles não usam o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornecido no modelo de geração de código a <xref:System.CodeDom> espaço de nome.  
  
## <a name="undo-support-features-of-the-designer"></a>Recursos de suporte do Designer de desfazer  
 O SDK de ambiente fornece implementações padrão de interfaces necessárias para oferecer suporte que pode ser usado pelos designers não usando de desfazer <xref:System.Windows.Forms.Control> com base em classes para as interfaces de usuário ou o modelo de CodeDOM e persistência padrão.  
  
 O <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> usando uma implementação de classe a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe para gerenciar operações de desfazer.  
  
 O Visual Studio fornece o seguinte recurso para desfazer designer:  
  
-   Funcionalidade de desfazer vinculado por vários designers.  
  
-   Unidades de filho dentro de um designer podem interagir com seus pais implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> em <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 O SDK de ambiente fornece suporte de CodeDOM e persistência fornecendo:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>como um implementações das<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Um <xref:System.ComponentModel.Design.IComponentChangeService> fornecidos pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' host de design.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Usando recursos do SDK de ambiente para fornecer suporte ao comando Desfazer  
 Para obter suporte de desfazer, um objeto que implementa um designer deve:  
  
-   Criar uma instância e inicializar uma instância do <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe com uma validade <xref:System.IServiceProvider> implementação.  
  
-   Isso <xref:System.IServiceProvider> classe deve fornecer os seguintes serviços:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Designers usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serialização de CodeDOM pode optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fornecido com o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] como a sua implementação do <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         Nesse caso, o <xref:System.IServiceProvider> classe fornecida para o <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> construtor deve retornar a este objeto como uma implementação do <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Designers usando o padrão <xref:System.ComponentModel.Design.DesignSurface> fornecidos pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] têm a garantia tem uma implementação padrão de host de design de <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
 Designers de implementar um <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mecanismo baseado em Desfazer automaticamente rastreia as alterações se:  
  
-   Alterações de propriedade são feitas por meio de <xref:System.ComponentModel.TypeDescriptor> objeto.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>eventos são gerados manualmente quando uma alteração não pode ser desfeita é confirmada.  
  
-   A modificação no designer de foi criada dentro do contexto de um <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   O designer opta por criar unidades de desfazer usando explicitamente a unidade para desfazer padrão fornecida por uma implementação de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou a implementação do Visual Studio específico <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, que é derivada de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e também fornece um implementação de ambos <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Estendendo o suporte ao tempo de design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)