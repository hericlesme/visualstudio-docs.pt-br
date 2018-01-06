---
title: 'Como: registrar tipos de arquivo do Editor | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 679223f21bd839a8d94b299319ad22c6701bc407
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-editor-file-types"></a>Como: registrar tipos de arquivo do Editor
A maneira mais fácil para registrar tipos de arquivo do editor está usando os atributos de registro fornecidos como parte do [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] pacote framework (MPF) classes gerenciadas. Se você estiver implementando seu pacote no formato nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], você também pode escrever um script de registro que registra seu editor e as extensões associadas.  
  
## <a name="registration-using-mpf-classes"></a>Usando Classes MPF de registro  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Para registrar tipos de arquivo do editor usando classes MPF  
  
1.  Forneça o <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> classe com os parâmetros adequados para seu editor na classe de seu VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Onde ". Exemplo de"é a extensão que está registrada para este editor e"32"é o nível de prioridade.  
  
     O `projectGuid` é o GUID para os tipos de arquivo diverso, definidos em <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>. O tipo de arquivo diverso é fornecido, para que o arquivo resultante não será parte do processo de compilação.  
  
     `TemplateDir`representa a pasta que contém os arquivos de modelo são incluídos com o exemplo de editor básico gerenciado.  
  
     `NameResourceID`é definido no arquivo do projeto BasicEditorUI Resources.h e identifica o editor como "My Editor".  
  
2.  Substituir o método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Na implementação do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método, chame o <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> método e passe a instância de sua fábrica de editor, como demonstrada abaixo.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Esta etapa registra a fábrica do editor e as extensões de arquivo do editor.  
  
3.  Cancelar o registro as fábricas de editor.  
  
     Fábricas de editor são automaticamente canceladas quando o VSPackage é descartado. Se o objeto de fábrica de editor implementar o <xref:System.IDisposable> interface, seu `Dispose` método é chamado depois que a fábrica foi não registrou com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Registro usando um Script de registro  
 Registrar fábricas de editor e tipos de arquivo no formato nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] é feito usando um script de registro para gravar o registro do windows, conforme ilustrado a seguir.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Para registrar tipos de arquivo do editor usando um script de registro  
  
1.  No seu script de registro, definir a fábrica do editor e a cadeia de caracteres do GUID de fábrica do editor conforme o `GUID_BscEditorFactory` seção do script de registro a seguir. Além disso, defina a extensão e a prioridade da extensão do editor:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     A extensão de arquivo do editor neste exemplo é identificada como "RTF" e a prioridade for "50". As cadeias de caracteres do GUID são definidas no arquivo de Resource.h do projeto de exemplo BscEdit.  
  
2.  Registre o VSPackage.  
  
3.  Registre a fábrica do editor.  
  
     A fábrica de editor é registrada no <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementação.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     As cadeias de caracteres do GUID são definidas no arquivo Resource.h do projeto BscEdit.