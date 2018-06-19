---
title: Atributos condicionais de esquema XML VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975ca2f5fa6f070baf07b26cbfa0d8c3aa3b67d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138350"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionais de esquema XML do VSCT
Atributos condicionais podem ser aplicados a todas as listas e itens. Operadores lógicos e expressões de expansão de símbolo avaliadas como true ou false. Se verdadeiro, a lista associada ou o item é incluído na saída resultante.  
  
 Expansões de token podem ser testados em relação a outras expansões de token ou constantes. A função Defined é usada para testar se um determinado nome tiver sido definido, mesmo se ele não tem nenhum valor.  
  
 Quando um atributo de condição é aplicado a uma lista, a condição é aplicada a todos os elementos filho na lista. Se um elemento filho contém um atributo de condição, a condição é combinada com a expressão pai por uma operação AND.  
  
 Os valores 1, '1' e 'true' são avaliados como true e 0, '0' e 'false' são avaliados como false.  
  
## <a name="operators"></a>Operadores  
 Os operadores a seguir podem ser usados para avaliar expressões condicionais.  
  
|Operador|Definição|  
|--------------|----------------|  
|(,)|Agrupamento|  
|!|Não lógico|  
|\<, >, \<=, >=, ==, !=|Relacionais e de igualdade|  
|e|Boolean|  
|ou|Boolean|  
  
## <a name="examples"></a>Exemplos  
  
```  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)