---
title: Ícones de Modo de Exibição de Classe e Pesquisador de Objetos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f0a4371ae086e158f3fd7025e9867ffb99c92090
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="class-view-and-object-browser-icons"></a>Ícones do Pesquisador de Objetos e do Modo de Exibição de Classe

**Modo de Exibição de Classe** e **Pesquisador de Objetos** exibem ícones que representam entidades de código, por exemplo, namespaces, classes, funções e variáveis. A tabela a seguir ilustra e descreve os ícones.

|Ícone|Descrição|Ícone|Descrição|
|----------|-----------------|----------|-----------------|
|![Símbolo de namespace](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|espaço de nome|![Símbolo de declaração](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Método ou função|
|![Ícone de classe](../ide/media/vxclass_icon.gif "vxClass_Icon")|Classe|![Símbolo de operador](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|Operador|  
|![Símbolo de interface pirulito](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|Interface|![Símbolo de propriedade](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|propriedade|
|![Símbolo de estrutura](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|Estrutura|![Ícone de campo](../ide/media/vxfield_icon.gif "vxField_Icon")|Campo ou variável|  
|![Símbolo de união](../ide/media/vxunion_icon.gif "vxUnion_Icon")|União|![Símbolo de evento](../ide/media/vxevent_icon.gif "vxEvent_Icon")|Evento|  
|![Símbolo de enumeração](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![Ícone de constante](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|Constante|  
|![Símbolo de definição de tipo](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![Símbolo do item Enumerar](../ide/media/vxenumitem_icon.gif "vxEnumItem_Icon")|Item Enum|  
|![Símbolo do módulo do Visual Studio](../ide/media/vxmodule_icon.gif "vxModule_Icon")|Módulo|![Símbolo de item do mapa](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|Item de Mapa|  
|![Símbolo de método de extensão](../ide/media/extensionmethod.gif "ExtensionMethod")|Método de extensão|![Símbolo de declaração](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Declaração externa|  
|![Símbolo de delegado](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|delegado|![Ícone de erro para o Modo de Exibição de Classe e Pesquisador de Objetos](../ide/media/erroricon.gif "ErrorIcon")|Erro|  
|![Símbolo de exceção](../ide/media/vxexception_icon.gif "vxException_Icon")|Exceção|![Símbolo de modelo](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|Modelo|  
|![Símbolo de mapa](../ide/media/vxmap_icon.gif "vxMap_Icon")|Mapa|![Símbolo de ponto de exclamação de erro](../ide/media/vxerror_icon.gif "vxError_Icon")|Unknown|  
|![Símbolo de encaminhamento de tipo](../ide/media/ob_type_forward.gif "ob_type_forward")|Encaminhamento de tipo|||  

## <a name="signal-icons"></a>Ícones de sinal

Os ícones de sinal a seguir aplicam-se a todos os ícones anteriores e indicam sua acessibilidade.

|Ícone|Descrição|
|----------|-----------------|  
|\<Nenhum ícone de sinal>|Público. Acessível de qualquer lugar neste componente e de qualquer componente que faça referência a ele.|  
|![Símbolo de sinal protegido](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|Protegido. Acessível da classe ou do tipo recipiente ou daqueles derivados da classe ou do tipo recipiente.|  
|![Símbolo de sinal privado](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|Privado. Acessível somente na classe ou no tipo recipiente.|  
|![Símbolo de sinal lacrado](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|Lacrado.|  
|![Símbolo de amigo&#47;interno do sinal](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|Amigo/interno. Acessível somente no projeto.|  
|![Ícone de seta do sinal](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|Atalho. Um atalho para o objeto.|

> [!NOTE]
> Se seu projeto estiver incluído em um banco de dados de controle do código-fonte, ícones de sinal adicionais poderão ser exibidos para indicar o status de controle de origem, como check-in ou check-out.

## <a name="see-also"></a>Consulte também

[Exibir a estrutura do código](../ide/viewing-the-structure-of-code.md)