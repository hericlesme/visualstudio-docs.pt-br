---
title: Criar pacotes de bootstrapper
ms.custom: ''
ms.date: 05/02/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29faeafb56c5c077602a3dbcba5ecbb6bb2ab118
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="create-bootstrapper-packages"></a>Criar pacotes de bootstrapper
O programa de instalação é um instalador genérico que pode ser configurado para detectar e instalar componentes redistribuíveis como arquivos do Windows Installer (.msi) e programas executáveis. O instalador também é conhecido como bootstrapper. Ele é programado por um conjunto de manifestos XML que especificam os metadados para gerenciar a instalação do componente.  Cada componente redistribuível ou pré-requisito, é um pacote de bootstrapper. Um pacote de bootstrapper é um grupo de diretórios e arquivos que contém arquivos de manifesto que descrevem como o pré-requisito deve ser instalado. 
  
O bootstrapper primeiro detecta se qualquer um dos pré-requisitos já está instalado. Se os pré-requisitos não estiverem instalados, primeiro o bootstrapper mostra os contratos de licença. Em segundo lugar, depois que o usuário final aceita os contratos de licença, a instalação dos pré-requisitos começa. Caso contrário, se forem detectados todos os pré-requisitos, o bootstrapper apenas inicia o instalador do aplicativo.  
  
## <a name="create-custom-bootstrapper-packages"></a>Criar pacotes de inicializador personalizado  
Você pode gerar os manifestos de bootstrapper usando o Editor de XML no Visual Studio. Para ver um exemplo de como criar um pacote de bootstrapper, consulte [passo a passo: criar um bootstrapper personalizado com um aviso de privacidade](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
Para criar um pacote de bootstrapper, você precisa criar um manifesto de produto e, para cada versão de um componente, um manifesto de pacote localizada.
  
* O manifesto de produto, *product.xml*, contém todos os metadados para o pacote com neutralidade de idioma. Esse manifesto contém metadados comuns a todas as versões localizadas do componente redistribuível.  Para criar esse arquivo, consulte [como: criar um manifesto de produto](../deployment/how-to-create-a-product-manifest.md).
  
* O manifesto de pacote *package.xml*, contém metadados específicos do idioma; normalmente contém mensagens de erro localizada. Um componente deve ter, pelo menos, um pacote de manifesto para cada versão localizada desse componente. Para criar esse arquivo, consulte [como: criar um manifesto de pacote](../deployment/how-to-create-a-package-manifest.md).
  
Depois que esses arquivos são criados, coloque o arquivo de manifesto do produto em uma pasta indicada para o bootstrapper personalizado. O arquivo de manifesto do pacote vai para uma pasta nomeada de acordo com a localidade. Por exemplo, se o arquivo de manifesto do pacote for para redistribuição em inglês, coloque o arquivo em uma pasta chamada en. Repita esse processo para cada localidade, como ja para japonês e de para alemão. O pacote final de bootstrapper personalizado pode ter estrutura de pastas a seguir.  

    ```
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```
  
Em seguida, copie os arquivos redistribuíveis para o local da pasta bootstrapper. Para obter mais informações, consulte [como: criar um pacote de Bootstrapper localizado](../deployment/how-to-create-a-localized-bootstrapper-package.md).
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
ou  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
Você também pode determinar o local da pasta de bootstrapper o **caminho** valor na seguinte chave do registro:  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
Em sistemas de 64 bits, use a seguinte chave do registro:  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
Cada componente redistribuível aparece em sua própria subpasta no diretório de pacotes. O produto manifesto e redistribuível arquivos deve ser colocado nessa subpasta. Versões localizadas dos manifestos de componente e o pacote devem ser colocadas em subpastas nomeadas de acordo com o nome de cultura.  
  
Depois que esses arquivos são copiados para a pasta de bootstrapper, o pacote de bootstrapper aparece automaticamente no Visual Studio **pré-requisitos** caixa de diálogo. Se o pacote de inicializador personalizado não aparecer, feche e reabra o **pré-requisitos** caixa de diálogo. Para obter mais informações, consulte [caixa de diálogo pré-requisitos](../ide/reference/prerequisites-dialog-box.md).  
  
A tabela a seguir mostra as propriedades que são preenchidas automaticamente pelo bootstrapper.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|ApplicationName|O nome do aplicativo.|  
|ProcessorArchitecture|O processador e bits por palavra da plataforma de destino de um executável. Os valores incluem o seguinte:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|O número de versão para os sistemas operacionais Microsoft Windows 95, Windows 98 ou Windows ME. A sintaxe da versão é Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|O número de versão para os sistemas operacionais Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 ou Windows 7. A sintaxe da versão é Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|A versão de assembly do Windows Installer (msi.dll) executado durante a instalação.|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|Essa propriedade será definida se o usuário tiver privilégios de administrador. Os valores são verdadeiro ou falso.|  
|InstallMode|O modo de instalação indica de onde o componente precisa ser instalado. Os valores incluem o seguinte:<br /><br /> -HomeSite - pré-requisitos estão instalados no site do fornecedor.<br />-SpecificSite - pré-requisitos estão instalados no local que você selecionar.<br />-SameSite - pré-requisitos estão instalados no mesmo local que o aplicativo.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Separando redistribuíveis das instalações do aplicativo  
Você pode evitar que seus arquivos redistribuíveis sejam implantados em projetos de instalação. Para fazer isso, crie uma lista redistribuível na pasta RedistList em seu diretório NET Framework:  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
A lista de redistribuível é um arquivo XML que você deve nomear usando o seguinte formato: *nome da empresa*. *Nome do componente*. RedistList.xml. Assim, por exemplo, se o componente é chamado Datawidgets feitas por Acme, use *Acme.DataWidgets.RedistList.xml*. Um exemplo de conteúdo da lista redistribuível pode ser semelhante a:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Caixa de diálogo pré-requisitos](../ide/reference/prerequisites-dialog-box.md)   
 [Referência de esquema de pacote e produto](../deployment/product-and-package-schema-reference.md)   
 [Use o Visual Studio 2005 Bootstrapper para sua instalação do lance](http://go.microsoft.com/fwlink/?LinkId=107537)