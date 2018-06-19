---
title: Referência de esquema 2.0 de pacote de idiomas VSIX | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 571f90f31014dcc4d5686483bfc037e458f4a31e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139647"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Referência de esquema 2.0 do VSIX Language Pack

O esquema do pacote de idiomas de VSIX fornece informações de instalação localizado para pacotes VSIX. A versão 2.0 desse esquema dá suporte a elementos de localização adicionais.

## <a name="language-pack-schema"></a>Esquema do pacote de idioma

O elemento raiz do arquivo de pacote de idioma é `<PackageLanguagePackManifest>`, com um atributo de `Version`, que é a versão do formato de pacote de idioma. Este tópico descreve a versão 2.0 do formato de pacote de idioma, que é especificado no manifesto, definindo o `Version` para o valor do atributo `Version="2.0.0"`. O elemento raiz contém exatamente um filho `<Metadata>` elemento.

### <a name="packagelangaugepackmanifest-element"></a>Elemento PackageLangaugePackManifest

Dentro de `<PackageLanguagePackManifest>` elemento deve existir o seguinte elemento:
|Título|Descrição|
|-----------|-----------------|
|`<Metadata>`| O elemento contêiner para todos os metadados de pacote localizado

### <a name="metadata-element"></a>Elemento de metadados

Dentro de `<Metadata>` elemento pode ter os seguintes elementos:
|Título|Descrição|
|-----------|-----------------|
|`<DisplayName>`|O nome localizado da extensão a ser instalado|
|`<Description>`|A descrição localizada da extensão a ser instalado|
|`<License>`| Um caminho para uma versão localizada da licença da extensão|
|`<MoreInfo>`| Um link para informações localizadas sobre a extensão|
|`<ReleaseNotes>`| Um caminho ou um link para uma versão localizada das notas de versão|
|`<Icon>`| Um caminho para uma versão localizada do ícone de extensões|

### <a name="sample-manifest"></a>Manifesto de exemplo

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Consulte também

|Título|Descrição|
|-----------|-----------------|
|[Localizar pacotes VSIX](../extensibility/localizing-vsix-packages.md)|Mostra como fornecer suporte à instalação localizada para um pacote do VSIX.|
|[Referência do Esquema de extensão 2.0 do VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|Um manifesto do VSIX descreve o conteúdo de um arquivo de implantação .vsix, que permite que uma extensão do Visual Studio ser instalado usando o **extensões e atualizações** caixa de diálogo.|
|[Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Mostra como usar o **extensões e atualizações** caixa de diálogo para instalar, remover, ativar e desativar extensões.|