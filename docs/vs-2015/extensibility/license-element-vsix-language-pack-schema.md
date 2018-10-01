---
title: Elemento (esquema de pacote de idiomas do VSIX) de licença | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecf1913878137d84346275beccb512027f74f8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465917"
---
# <a name="license-element-vsix-language-pack-schema"></a>Elemento License (esquema de pacote de idiomas do VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [elemento License (esquema de pacote de idiomas do VSIX)](https://docs.microsoft.com/visualstudio/extensibility/license-element-vsix-language-pack-schema).  
  
Opcional. O caminho de uma versão localizada do arquivo de licença para a extensão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Nenhum||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento LanguagePack do VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Necessário. Fornece o elemento raiz para um pacote de idiomas do VSIX.|  
  
## <a name="text-value"></a>Valor de texto  
 O caminho relativo do arquivo de licença localizado a ser exibido.  
  
## <a name="remarks"></a>Comentários  
 Se o `License` elemento for definido, em seguida, o texto do arquivo de licença designado será exibido durante a instalação e o usuário deve aceitar a licença para continuar.  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|Namespace|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Nome do esquema|Esquema de pacote de idiomas do VSIX|  
|Arquivo de validação|VSIXLanguagePackSchema.xsd|  
|Pode ser vazio|Não aplicável|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema do pacote de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizar pacotes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

