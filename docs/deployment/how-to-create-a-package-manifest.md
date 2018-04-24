---
title: 'Como: criar um manifesto de pacote | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54c2e6a231ce597e2ec6a3e04cf74521b6c10d2e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-package-manifest"></a>Como criar um manifesto de pacote
Para implantar os pré-requisitos para o seu aplicativo, você pode usar um pacote de bootstrapper. Um pacote de bootstrapper contém um arquivo de manifesto de produto único mas um manifesto de pacote para cada localidade. Funcionalidade compartilhada entre diferentes versões localizadas deve ir para o manifesto de produto.  
  
 Para obter mais informações sobre manifestos de pacote, consulte [como: criar um manifesto de produto](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Criando o manifesto de pacote  
  
#### <a name="to-create-the-package-manifest"></a>Para criar o manifesto de pacote  
  
1.  Crie um diretório para o pacote de bootstrapper. Este exemplo usa C:\package.  
  
2.  Crie um subdiretório com o nome da localidade, como en para inglês.  
  
3.  No Visual Studio, crie um arquivo XML denominado `package.xml`e salvá-lo para a pasta C:\package\en.  
  
4.  Adicione XML para listar o nome do pacote de bootstrapper, a cultura para esse manifesto de pacote localizado e o contrato de licença opcional. O XML a seguir usa as variáveis `DisplayName` e `Culture`, que é definido em um elemento posterior.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Adicione XML para listar todos os arquivos que estão no diretório local específico. O XML a seguir usa um arquivo chamado EULA é aplicável para o **en** localidade.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Adicione o XML para definir as cadeias de caracteres localizáveis para o pacote de bootstrapper. O XML a seguir adiciona cadeias de caracteres de erro para a localidade pt.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Copie a pasta C:\package para o diretório de bootstrapper do Visual Studio. Para Visual Studio 2010, este é o diretório de SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Exemplo  
 O manifesto de pacote contém informações específicas da localidade, como mensagens de erro, termos de licença de software e pacotes de idiomas.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)