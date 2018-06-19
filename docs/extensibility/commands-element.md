---
title: Comandos do elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d905914c9819671cf8c77d81ec8d51302467a9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108476"
---
# <a name="commands-element"></a>Elemento Commands
Representa a coleção de comandos na barra de ferramentas VSPackage. A coleção pode ter até cinco subseções, da seguinte maneira: grupos, menus, botões, combinações e bitmaps.  
  
 Cada elemento do filho subseção, por exemplo, \<Menu >, é identificado por uma ID exclusiva que é um GUID e um par de identificador numérico. O GUID identifica o conjunto de comandos"" e é usado para agrupar comandos relacionados logicamente. O VSPackage deve definir seu próprio comando definido para evitar colisões com IDs de comando que são definidos por outros VSPackages.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|pacote|Um GUID que identifica o VSPackage que fornece os comandos.<br /><br /> Por exemplo, do pacote = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Menus](../extensibility/menus-element.md)|Define todos os menus que implementa um VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando em um VSPackage.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Agrupa elementos de botão.|  
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Agrupa elementos do Bitmap.|  
|[Elemento Combos](../extensibility/combos-element.md)|Agrupa elementos de combinação.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que fornece um VSPackage ao IDE. Possíveis elementos são itens de menu, menus, barras de ferramentas e caixas de combinação.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um [comandos elemento](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como VSPackages adicionar elementos da Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)