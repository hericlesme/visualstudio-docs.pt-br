---
title: Elemento RequiredPlatformVersion (modelos do Visual Studio) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f7eb4ada8378ff9009987f56341a65670a3c412
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (Modelos do Visual Studio)
Especifica a versão mínima do sistema operacional que o modelo de projeto requer funcione corretamente. Esse elemento é usado para modelos de projeto que cria [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos.  
  
 O `RequiredPlatformVersion` é comparado diretamente com a versão do sistema operacional. Se o `RequiredPlatformVersion` for maior do que a versão do sistema operacional, o modelo não aparecer no **novo projeto** caixa de diálogo. Para especificar um modelo para [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou superior, defina `RequiredPlatformVersion` para 6.2.0. Para especificar um modelo para [!INCLUDE[win81](../debugger/includes/win81_md.md)] ou superior, defina RequiredPlatformVersion para 6.3.0.  
  
 Modelos que especificam `RequiredPlatformVersion`= 8 são compatíveis com o cliente anterior [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] modelos.  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 nenhuma.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica a plataforma que os destinos de modelo de projeto.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
## <a name="remarks"></a>Comentários  
 Esse texto Especifica a versão mínima do sistema operacional exigida pelo modelo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo especifica que os destinos do projeto modelo [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou posterior.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento TargetPlatformName (modelos do Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)