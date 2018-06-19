---
title: Localizando pacotes VSIX | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d94e390374ca2eb77b4332b3a5c253acce69f051
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143407"
---
# <a name="localizing-vsix-packages"></a>Localizando pacotes VSIX

Você pode localizar um pacote do VSIX criando um arquivo Extension.vsixlangpack para cada idioma de destino e, em seguida, colocando-os na pasta correta. Quando um pacote localizado estiver instalado, o nome localizado da extensão é exibido junto com uma descrição localizada. Se você fornecer um arquivo de licença localizada ou uma URL que aponta para informações localizadas, elas também são exibidas.

Se o conteúdo do pacote VSIX inclui um VSPackage que adiciona os comandos de menu ou outra interface de usuário, consulte [comandos de Menu Localizando](../extensibility/localizing-menu-commands.md) para obter informações sobre como localizar os novos elementos de interface do usuário.

## <a name="directory-structure"></a>Estrutura de diretórios

 Quando um usuário instala uma extensão, **extensões e atualizações** verifica o nível superior do pacote VSIX para uma pasta cujo nome corresponde à localidade do Visual Studio do computador de destino. Se **extensões e atualizações** localiza um .vsixlangpack de arquivos na pasta, ele substitui os valores localizados no arquivo para os valores correspondentes no arquivo .vsixmanifest. Esses valores são exibidos quando a extensão está sendo instalada. O exemplo a seguir mostra a estrutura de diretório para um pacote do VSIX está localizado em espanhol (es-ES) e francês (fr-FR).  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Os modelos de projeto do VSIX com suporte no [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] gerar um manifesto do VSIX e nomeie-a como source.extension.vsixmanifest. Quando o Visual Studio compila o projeto, ele copia o conteúdo do arquivo Extension.VsixManifest no pacote do VSIX.

## <a name="the-extensionvsixlangpack-file"></a>O arquivo Extension.vsixlangpack

O arquivo Extension.vsixlangpack segue o [pacote de idiomas de VSIX esquema 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Esse esquema tem um `PackageLanguagePackManifest`, que é seguido por um `Metadata` elemento filho. O elemento de metadados pode conter elementos filho até 6, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, e `Icon`. Esses elementos filho correspondem ao `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, e `Icon` elementos filho de `Metadata` elemento do arquivo Extension.vsixmanifest.

Quando você cria um arquivo de vsixlangpack, você deve definir o `Include in Vsix` propriedade `true`. Caso contrário, o texto de instalação localizado será ignorado.

### <a name="to-set-the-include-in-vsix-property"></a>Para definir a incluir na propriedade Vsix

1. Em **Solution Explorer**, clique no arquivo Extension.vsixlangpack e, em seguida, clique em **propriedades**.

2.  Na grade de propriedades, clique em **incluir VSIX**e defina seu valor como `true`.

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O exemplo a seguir mostra as partes relevantes de um arquivo de Extension.vsixmanifest, junto com o arquivo Extension.vsixlangpack correspondente para espanhol. Os valores do pacote de idiomas substituem os valores do manifesto de se a localidade do Visual Studio do computador de destino é definida como Spanish.

### <a name="code"></a>Código

 [Extension.vsixmanifest]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [Extension.vsixlangpack]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
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
|[Referência de esquema LanguagePack 2.0 VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Um pacote de idiomas VSIX descreve as informações de localização de um arquivo de implantação .vsix.|
|[Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descreve a estrutura e o conteúdo de um pacote do vsix.|
|[Localizar os comandos de menu](../extensibility/localizing-menu-commands.md)|Mostra como localizar outros recursos de texto em uma extensão.|