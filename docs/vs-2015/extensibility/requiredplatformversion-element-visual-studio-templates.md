---
title: Elemento RequiredPlatformVersion (modelos do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fb35bfefeb7722c3ec488a1f9caf63cd49202dd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466936"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (Modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [elemento RequiredPlatformVersion (modelos do Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/requiredplatformversion-element-visual-studio-templates).  
  
Especifica a versão mínima do sistema operacional que o modelo de projeto requer para funcionar corretamente. Esse elemento é usado para modelos de projeto que cria [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplicativos.  
  
 O `RequiredPlatformVersion` valor é comparado diretamente com a versão do sistema operacional. Se o `RequiredPlatformVersion` é maior do que a versão do sistema operacional, o modelo não aparecer na **novo projeto** caixa de diálogo. Para especificar um modelo para [!INCLUDE[win8](../includes/win8-md.md)] ou superior, defina `RequiredPlatformVersion` para 6.2.0. Para especificar um modelo para [!INCLUDE[win81](../includes/win81-md.md)] ou superior, defina RequiredPlatformVersion para 6.3.0.  
  
 Modelos que especificam `RequiredPlatformVersion`= 8 são compatíveis com o cliente anterior [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] modelos.  
  
 VSTemplate  
TemplateData  
... TargetPlatformName  
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
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica a plataforma de que os destinos de modelo de projeto.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
## <a name="remarks"></a>Comentários  
 Esse texto Especifica a versão mínima do sistema operacional necessária ao modelo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo especifica que os destinos de modelo de projeto [!INCLUDE[win8](../includes/win8-md.md)] ou posterior.  
  
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

