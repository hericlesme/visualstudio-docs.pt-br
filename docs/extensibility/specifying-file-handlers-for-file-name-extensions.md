---
title: Especificando identificadores de arquivo para as extensões de nome de arquivo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d0086f8badb32431c85f16e1f74fe8f186c9b2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificando identificadores de arquivo para as extensões de nome de arquivo
Há várias maneiras de determinar o aplicativo que trata de um arquivo que tem uma extensão de arquivo específico. Os verbos OpenWithList e OpenWithProgids são duas maneiras de especificar identificadores de arquivo na entrada do registro para a extensão de arquivo.  
  
## <a name="openwithlist-verb"></a>Verbo de OpenWithList  
 Quando você clica um arquivo no Windows Explorer, você verá o **abrir** comando. Se mais de um produto está associado uma extensão, você verá um **abrir com** submenu.  
  
 Você pode registrar diferentes aplicativos para abrir uma extensão, definindo a chave de OpenWithList da extensão de arquivo em HKEY_CLASSES_ROOT. Os aplicativos listados sob essa chave para uma extensão de arquivo aparecem sob o **recomendado programas** título no **abrir com** caixa de diálogo. O exemplo a seguir mostra os aplicativos registrados para abrir a extensão de arquivo. vcproj.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  As chaves especificando aplicativos estão na lista em HKEY_CLASSES_ROOT\Applications.  
  
 Adicionando uma chave OpenWithList, você declara que seu aplicativo oferece suporte a uma extensão de arquivo, mesmo se outro aplicativo assume a propriedade da extensão. Isso pode ser uma versão futura do seu aplicativo ou outro aplicativo.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identificadores de programação (ProgIDs) são versões amigáveis do ClassIDs que identificam uma versão de um aplicativo ou objeto COM. Cada objeto de conjunto pode ser criado deve ter seu próprio ProgID. Por exemplo, VisualStudio.DTE.7.1 inicia o Visual Studio .NET 2003 enquanto inicia VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Como o proprietário de um tipo de projeto ou o tipo de item de projeto, você deve criar um ProgID específico da versão para a sua extensão de arquivo. Essas ProgIDs pode ser redundantes em que mais de um ProgID pode iniciar o mesmo aplicativo. Para obter mais informações, consulte [registrando verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Use a seguinte convenção de nomenclatura de arquivo com controle de versão ProgIDs para evitar a duplicação com o registro de outros fornecedores:  
  
|Extensão de arquivo|Versão ProgID|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Você pode registrar diferentes aplicativos que são capazes de abrir uma extensão de arquivo específico, adicionando ProgIDs com controle de versão como valores para o HKEY_CLASSES_ROOT\\*\<extensão >*\OpenWithProgids chave. Essa chave do registro contém uma lista de ProgIDs alternativo associado com a extensão de arquivo. Os aplicativos associados os ProgIDs listados aparecem no **abrir com * * * nome do produto* submenu. Se o mesmo aplicativo é especificado em ambos os `OpenWithList` e `OpenWithProgids` chaves, o sistema operacional mescla as duplicatas.  
  
> [!NOTE]
>  O `OpenWithProgids` chaves só tem suporte no Windows XP. Como outros sistemas operacionais ignorar essa chave, não o use como o registro somente para identificadores de arquivo. Use esta chave para fornecer uma melhor experiência de usuário no Windows XP.  
  
 Adicione os ProgIDs desejados como valores do tipo REG_NONE. O código a seguir fornece um exemplo de registro de ProgIDs para uma extensão de arquivo (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 O ProgID especificado como o valor padrão para a extensão de arquivo é o identificador de arquivo padrão. Se você modificar o ProgID para uma extensão de arquivo fornecido com uma versão anterior do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou que pode ser controlado por outros aplicativos, você deve registrar o `OpenWithProgids` da chave para a sua extensão de arquivo e especifique a nova ProgID na lista junto com os ProgIDs antigos que você oferece suporte. Por exemplo:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Se o antigo ProgID tem verbos associados a ele, então esses verbos também aparecerá em **abrir com** *nome do produto* no menu de atalho.  
  
## <a name="see-also"></a>Consulte também  
 [Sobre extensões de nome de arquivo](../extensibility/about-file-name-extensions.md)   
 [Registrar verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)