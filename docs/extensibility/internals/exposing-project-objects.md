---
title: Expondo objetos do projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 668287dc8b0b5ac9dd37cb450582e3a56fb7f25e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-project-objects"></a>Expondo objetos do projeto
Tipos de projeto personalizado podem fornecer objetos de automação para permitir o acesso ao projeto usando as interfaces de automação. Cada tipo de projeto é esperado para fornecer o padrão <xref:EnvDTE.Project> objeto de automação que é acessado de <xref:EnvDTE.Solution>, que contém uma coleção de todos os projetos que estão abertos no IDE. Cada item do projeto deve ser exposta por um <xref:EnvDTE.ProjectItem> objeto acessado com `Project.ProjectItems`. Além desses objetos de automação standard, projetos podem optar por oferecer objetos de automação específica do projeto.  
  
 Você pode criar objetos de automação de nível raiz personalizada que você pode acessar tardia da raiz DTE objeto usando `DTE.<customeObjectName>` ou `DTE.GetObject("<customObjectName>")`. Por exemplo, Visual C++ cria a coleção de projeto específica do projeto C++ chamada "VCProjects", você pode acessar usando DTE. VCProjects ou DTE. GetObject("VCProjects"). Você também pode criar um Project.Object, que é exclusivo para o tipo de projeto, um Project.CodeModel, que pode ser consultado para seu objeto mais derivado, um item de projeto, que expõe ProjectItem.Object e um ProjectItem.FileCodeModel.  
  
 É uma convenção comum para projetos para expor uma coleção de projetos personalizados, específicos do projeto. Por exemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] cria uma coleção de projeto específicas de C++ que você pode acessar usando `DTE.VCProjects` ou `DTE.GetObject("VCProjects")`. Você também pode criar um `Project.Object`, que é exclusivo para o tipo de projeto, um `Project.CodeModel`, que pode ser consultado para seu objeto mais derivado, uma `ProjectItem`, que expõe `ProjectItem.Object`e um `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para contribuir um objeto de VSPackage específico para um projeto  
  
1.  Adicione as chaves apropriadas ao arquivo .pkgdef do seu VSPackage.  
  
     Por exemplo, aqui estão as configurações de .pkgdef para o projeto de linguagem do C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementar o código de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método, como no exemplo a seguir.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     No código, `g_wszAutomationProjects` é o nome de sua coleção de projetos. O `GetAutomationProjects` método cria um objeto que implementa o `Projects` interface e retorna um `IDispatch` ponteiro para o objeto de chamada, conforme mostrado no exemplo de código a seguir.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Você deve escolher um nome exclusivo para seu objeto de automação. Conflitos de nome serão imprevisíveis e colisões causam um nome de objeto conflitante para arbitrariamente descartados se vários tipos de projeto a usar o mesmo nome. Você deve incluir o nome da sua empresa ou algum aspecto exclusivo do seu nome de produto no nome do objeto de automação.  
  
     Personalizado `Projects` objeto da coleção é um ponto de entrada de conveniência para a parte restante do seu modelo de automação do projeto. O objeto de projeto também é acessível a partir de <xref:EnvDTE.Solution> coleção de projetos. Depois de criar as entradas do registro e de código apropriadas que fornecem os consumidores com `Projects` objetos de coleção, a implementação deverá fornecer restantes objetos padrão para o modelo de projeto. Para obter mais informações, consulte [projeto de modelagem](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>