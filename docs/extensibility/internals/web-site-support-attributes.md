---
title: Atributos de suporte do Site da Web | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 504046999814b4766fa9e5e8c006a02049e7007d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-attributes"></a>Atributos de suporte do Site da Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Projeto de site pode ser estendido para oferecer suporte para Web linguagens de programação. O idioma deve ser registrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que os modelos de projeto podem aparecer no **novo Site** caixa de diálogo quando o idioma é selecionado.  
  
 O exemplo de IronPython Studio inclui suporte do site da web. Ele inclui as seguintes classes de atributo para registrar o IronPython como uma linguagem de code-behind para novos projetos da Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Esse atributo é colocado no projeto de idioma. Ele adiciona o idioma para a lista de idiomas de programação da Web a **idioma** lista o **novo Site** caixa de diálogo. Por exemplo, o seguinte adiciona IronPython à lista:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Esse atributo também define o caminho de modelos para apontar para a pasta de modelos. Para obter mais informações sobre o local da pasta de modelos, consulte [modelos de suporte do Site](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Esse atributo é colocado no projeto de idioma. Ele permite que o projeto de Site da Web aninhar um tipo de arquivo (relacionado) em outro tipo de arquivo (primário) no **Gerenciador de soluções**.  
  
 Por exemplo:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Especifica que um arquivo de code-behind IronPython está relacionado a um arquivo. aspx. Quando uma nova página da Web. aspx é criada em uma solução de site da Web de IronPython, um novo arquivo de origem py é gerado e aparece como um nó filho da página. aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Esse atributo é colocado no pacote de idiomas do projeto. Ele seleciona o provedor do Intellisense para o idioma.  
  
 Por exemplo:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Especifica que uma instância de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, devem ser criados sob demanda para fornecer serviços de idioma.  
  
 A implementação IVsIntellisenseProject trata referências e chama o compilador de linguagem quando uma página da Web com o código foi solicitada, mas não é armazenado em cache.  
  
## <a name="see-also"></a>Consulte também  
 [Suporte ao site](../../extensibility/internals/web-site-support.md)