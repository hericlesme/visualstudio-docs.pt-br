---
title: Elemento UsedCommand | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4888733abf142f6582706406decbea0bf84ce519
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Permite que um VSPackage acessar um comando que é definido em outro arquivo. VSCT. Por exemplo, se seu VSPackage usa o padrão de **cópia** comando, que é definido como o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, você pode adicionar o comando a um menu ou barra de ferramentas sem implementá-lo novamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. O GUID do par de ID de GUID que identifica o comando.|  
|id|Necessário. A ID do par de ID de GUID que identifica o comando.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Agrupa elementos de UsedCommand e outros UsedCommands agrupamentos.|  
  
## <a name="remarks"></a>Comentários  
 Adicionando um comando para o `<UsedCommands>` elemento, um VSPackage informa o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que o VSPackage exige que o comando de ambiente. Você deve adicionar um `<UsedCommand>` elemento para qualquer comando que o pacote requer que não pode ser incluído em todas as versões e as configurações do Visual Studio. Por exemplo, se seu pacote chama um comando que é específico para o Visual C++, o comando não será disponibilizado para usuários do Visual Web Developer, a menos que você incluir um `<UsedCommand>` elemento para o comando.  
  
## <a name="example"></a>Exemplo  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)