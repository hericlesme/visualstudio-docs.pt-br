---
title: Interface IManagedAddin | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: ce339bb56368ab5c7e88d1cc8956a3b19a7e89b3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="imanagedaddin-interface"></a>Interface IManagedAddin
  Implementar a interface IManagedAddin para criar um componente que carrega gerenciados suplementos do VSTO. Essa interface foi adicionada no sistema Microsoft Office 2007.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos que são definidos pela interface IManagedAddin.  
  
|Nome|Descrição|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Chamado quando um Microsoft Office aplicativo carrega um Add-in do VSTO gerenciado.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Chamado logo antes de um Microsoft Office aplicativo descarrega um gerenciado VSTO suplemento.|  
  
## <a name="remarks"></a>Comentários  
 Aplicativos do Microsoft Office, começando com o sistema do Microsoft Office 2007, usam a interface IManagedAddin para ajudar a carga de suplementos do VSTO do Office. Você pode implementar a interface IManagedAddin para criar seu próprio carregador de suplemento do VSTO e gerenciado de tempo de execução para suplementos do VSTO, em vez de usar o carregador do suplemento do VSTO (VSTOLoader.dll) e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obter mais informações, consulte [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Como os suplementos gerenciados são carregados  
 Quando um aplicativo é iniciado, ocorrem as seguintes etapas:  
  
1.  O aplicativo descobre suplementos do VSTO procurando entradas na seguinte chave do registro:  
  
     HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nome do aplicativo >*\Addins\  
  
     Cada entrada na chave do registro é uma ID exclusiva do suplemento do VSTO. Normalmente, isso é o nome do assembly do suplemento do VSTO.  
  
2.  O aplicativo procura um `Manifest` entrada na entrada para cada suplemento do VSTO.  
  
     Gerenciado suplementos do VSTO podem armazenar o caminho completo de um manifesto no `Manifest` entrada HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nome do aplicativo >*\Addins\\  *\<na ID de->*. Um manifesto é um arquivo (normalmente, um arquivo XML) que fornece informações que são usadas para ajudar a carregar o suplemento do VSTO.  
  
3.  Se o aplicativo encontra uma `Manifest` entrada, o aplicativo tenta carregar um componente do carregador do suplemento do VSTO gerenciado. O aplicativo faz isso ao tentar criar um objeto COM que implementa a interface IManagedAddin.  
  
     O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclui um componente do carregador do suplemento do VSTO (VSTOLoader.dll), ou você pode criar seus próprios Implementando a interface IManagedAddin.  
  
4.  O aplicativo chama o [IManagedAddin::Load](../vsto/imanagedaddin-load.md) método e passa o valor da `Manifest` entrada.  
  
5.  O [IManagedAddin::Load](../vsto/imanagedaddin-load.md) método executa as tarefas necessárias para carregar o VSTO suplemento, como configurar a política de segurança e de domínio de aplicativo para o Add-in do VSTO que está sendo carregado.  
  
 Para obter mais informações sobre o registro chaves que usam aplicativos do Microsoft Office para descobrir e carregar gerenciados suplementos do VSTO, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-for-implementing-imanagedaddin"></a>Diretrizes para implementar IManagedAddin  
 Se você implementar IManagedAddin, você deve registrar a DLL que contém a implementação por meio do seguinte CLSID:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Aplicativos do Microsoft Office usam esse CLSID para criar o objeto COM que implementa IManagedAddin.  
  
> [!CAUTION]  
>  Esse CLSID também é usado por VSTOLoader.dll no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Portanto, se você usar IManagedAddin para criar seu próprio carregador de suplemento do VSTO e o componente de tempo de execução, você não pode implantar seu componente para computadores que estão executando suplementos do VSTO que dependem de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API não gerenciada &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  