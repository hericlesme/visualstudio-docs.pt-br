---
title: A estrutura do arquivo. XML [Content_types] | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f399cb0c88e044224d554cf8e17cc4d217498e87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>A estrutura do arquivo. XML [Content_types]
Contém informações sobre os tipos de conteúdo em um pacote do VSIX. O Visual Studio usa o arquivo. XML [Content_Types] para instalar o pacote, mas não instala o arquivo propriamente dito.  
  
> [!NOTE]
>  Embora este tópico se aplica somente a arquivos. XML [tipo_de_conteúdo] que são usados em pacotes VSIX, o tipo de arquivo. XML [Content_Types] é parte do *Open Packaging Conventions (OPC)* padrão. Para obter mais informações, consulte [OPC: um novo padrão de empacotamento seus dados](http://go.microsoft.com/fwlink/?LinkID=148207) no site do MSDN.  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem o elemento raiz e seus atributos e elementos filho.  
  
### <a name="root-element"></a>Elemento raiz  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Types`|Contém elementos filho que enumera os tipos de arquivo do pacote VSIX.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Xmlns`|(Obrigatório.) O local do esquema usado para esse arquivo. XML de [Content_Types].|  
  
### <a name="attribute-name-attribute"></a>{Nome do atributo} Atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|http://schemas.openformats.org/Package/2006/Content-Types|O local do esquema de tipos de conteúdo.|  
  
### <a name="child-elements"></a>Elementos filho  
 O `Types` elemento pode conter qualquer número de `Default` elementos.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Default`|Descreve um tipo de conteúdo do pacote VSIX. Cada tipo de arquivo do pacote deve ter seu próprio `Default` elemento.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Extension`|A extensão de nome de arquivo de um arquivo do pacote VSIX.|  
|`ContentType`|Descreve o tipo de conteúdo que está associado com a extensão de nome de arquivo.|  
  
### <a name="attribute-name-attribute"></a>{Nome do atributo} Atributo  
 O Visual Studio reconhece os seguintes `ContentType` valores associados `Extension` tipos.  
  
|Extensão|ContentType|  
|---------------|-----------------|  
|txt|texto/sem formatação|  
|pkgdef|texto/sem formatação|  
|xml|texto/xml|  
|vsixmanifest|texto/xml|  
|htm ou html|texto/html|  
|RTF|aplicativo/rtf|  
|PDF|aplicativo/pdf|  
|GIF|imagem/gif|  
|JPG ou jpeg|imagem/jpg|  
|TIFF|imagem/tiff|  
|vsix|aplicativo/zip|  
|CEP|aplicativo/zip|  
|DLL|application/octet-stream|  
|todos os outros tipos de arquivo|application/octet-stream|  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O seguinte arquivo. XML [Content_Types] descreve um pacote do VSIX típico.  
  
### <a name="code"></a>Código  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Um novo padrão para empacotar seus dados](http://go.microsoft.com/fwlink/?LinkID=148207)