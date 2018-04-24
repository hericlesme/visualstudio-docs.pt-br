---
title: '&lt;InstallChecks&gt; elemento (Bootstrapper) | Microsoft Docs'
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
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51fcfd8aaa0048cac3fb9a33c7974132655de87a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; elemento (Bootstrapper)
O `InstallChecks` elemento dá suporte a partir de uma variedade de testes para o computador local para garantir que todos os pré-requisitos apropriados para um aplicativo foi instalados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## <a name="assemblycheck"></a>AssemblyCheck  
 Este é um elemento filho opcional de `InstallChecks`. Para cada instância do `AssemblyCheck`, o inicializador garantirá que o assembly identificado pelo elemento existe no cache de assembly global (GAC). Ele não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para armazenar o resultado. Essa propriedade pode ser referenciada de um teste sob o `InstallConditions` elemento, que é um filho do `Command` elemento. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Necessário. O nome totalmente qualificado do assembly para verificar.|  
|`PublicKeyToken`|Necessário. A forma abreviada de chave pública associado a esse assembly de nome forte. Todos os assemblies no GAC devem ter um nome, uma versão e uma chave pública.|  
|`Version`|Necessário. A versão do assembly.<br /><br /> O número de versão tem o formato \< *versão principal*>.\< *versão secundária*>.\< *versão da compilação*>.\< *versão revisão*>.|  
|`Language`|Opcional. O idioma de um assembly localizado. O padrão é `neutral`.|  
|`ProcessorArchitecture`|Opcional. O processador do computador afetado por essa instalação. O padrão é `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck  
 Este é um elemento filho opcional de `InstallChecks`. Para cada instância do `ExternalCheck`, o inicializador executar o programa externo nomeado em um processo separado e armazenar seu código de saída na propriedade indicada pelo `Property`. `ExternalCheck` é útil para implementar as verificações de dependência complexos, ou quando a única maneira de verificar a existência de um componente é uma instância.  
  
 `ExternalCheck` não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para armazenar o resultado. Essa propriedade pode ser referenciada de um teste sob o `InstallConditions` elemento, que é um filho do `Command` elemento. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Necessário. O programa externo para executar. O programa deve ser parte do pacote de distribuição de instalação.|  
|`Arguments`|Opcional. Fornece os argumentos de linha de comando para o executável chamado pelo `PackageFile`.|  
  
## <a name="filecheck"></a>Não  
 Este é um elemento filho opcional de `InstallChecks`. Para cada instância do `FileCheck`, o inicializador determinará se o arquivo existe e retornar o número de versão do arquivo. Se o arquivo não tiver um número de versão, o inicializador define a propriedade nomeada pelo `Property` como 0. Se o arquivo não existir, `Property` não está definida como qualquer valor.  
  
 `FileCheck` não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para armazenar o resultado. Essa propriedade pode ser referenciada de um teste sob o `InstallConditions` elemento, que é um filho do `Command` elemento. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Necessário. O nome do arquivo a ser localizado.|  
|`SearchPath`|Necessário. O disco ou a pasta na qual procurar o arquivo. Isso deve ser um caminho relativo, se `SpecialFolder` é atribuído; caso contrário, ele deve ser um caminho absoluto.|  
|`SpecialFolder`|Opcional. Uma pasta que tem um significado especial para o Windows ou para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. O padrão é interpretar `SearchPath` como um caminho absoluto. Os valores válidos incluem o seguinte:<br /><br /> `AppDataFolder`. A pasta de dados de aplicativo para este [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo; específicos do usuário atual.<br /><br /> `CommonAppDataFolder`. A pasta de dados do aplicativo usada por todos os usuários.<br /><br /> `CommonFilesFolder`. A pasta de arquivos comuns para o usuário atual.<br /><br /> `LocalDataAppFolder`. A pasta de dados para aplicativos móveis não.<br /><br /> `ProgramFilesFolder`. A pasta de arquivos de programa padrão para aplicativos de 32 bits.<br /><br /> `StartUpFolder`. A pasta que contém todos os aplicativos iniciados na inicialização do sistema.<br /><br /> `SystemFolder`. A pasta que contém as DLLs do sistema de 32 bits.<br /><br /> `WindowsFolder`. A pasta que contém a instalação do sistema Windows.<br /><br /> `WindowsVolume`. A unidade ou partição que contém a instalação do sistema Windows.|  
|`SearchDepth`|Opcional. A profundidade na qual Pesquisar subpastas do compartilhamento de arquivo nomeado. A pesquisa é de profundidade. O padrão é 0, o que restringe a pesquisa a pasta de nível superior especificada por `SpecialFolder` e **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Este é um elemento filho opcional de `InstallChecks`. Para cada instância do `MsiProductCheck`, o inicializador verifica se a instalação do Microsoft Windows Installer especificada foi executado até ser concluído. O valor da propriedade é definido com o estado do produto instalado. Um valor positivo indica que o produto foi instalado, 0 ou -1 indica que não está instalado. (Consulte a função do SDK do Windows Installer MsiQueryFeatureState para obter mais informações.) . Se o Windows Installer não estiver instalado no computador, `Property` não está definido.  
  
 `MsiProductCheck` não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para armazenar o resultado. Essa propriedade pode ser referenciada de um teste sob o `InstallConditions` elemento, que é um filho do `Command` elemento. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Necessário. O GUID para o produto instalado.|  
|`Feature`|Opcional. O GUID de um recurso específico do aplicativo instalado.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Este é um elemento filho opcional de `InstallChecks`. Para cada instância do `RegistryCheck`, o inicializador verifica se a chave do Registro especificada existe, ou se ele tem o valor indicado.  
  
 `RegistryCheck` não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para armazenar o resultado. Essa propriedade pode ser referenciada de um teste sob o `InstallConditions` elemento, que é um filho do `Command` elemento. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Necessário. O nome da chave do Registro.|  
|`Value`|Opcional. O nome do valor do registro para recuperar. O padrão é retornar o texto do valor padrão. `Value` deve ser um DWORD ou uma cadeia de caracteres.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Este é um elemento filho opcional de `InstallChecks`. Para cada instância do `RegistryFileCheck`, o inicializador recupera a versão do arquivo especificado, primeira tentativa de recuperar o caminho para o arquivo de chave do registro especificado. Isso é particularmente útil se você quiser pesquisar um arquivo em um diretório especificado como um valor no registro.  
  
 `RegistryFileCheck` não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para armazenar o resultado. Essa propriedade pode ser referenciada de um teste sob o `InstallConditions` elemento, que é um filho do `Command` elemento. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Necessário. O nome da chave do Registro. Seu valor é interpretado como o caminho para um arquivo, a menos que o `File` atributo está definido. Se essa chave não existir, `Property` não está definido.|  
|`Value`|Opcional. O nome do valor do registro para recuperar. O padrão é retornar o texto do valor padrão. `Value` deve ser uma cadeia de caracteres.|  
|`FileName`|Opcional. O nome de um arquivo. Se especificado, o valor obtido da chave do registro deve para ser um caminho de diretório, e esse nome é anexado a ele. Se não for especificado, o valor retornado do registro deve para ser o caminho completo para um arquivo.|  
|`SearchDepth`|Opcional. A profundidade na qual Pesquisar subpastas do compartilhamento de arquivo nomeado. A pesquisa é de profundidade. O padrão é 0, o que restringe a pesquisa a pasta de nível superior especificada pelo valor da chave do registro.|  
  
## <a name="remarks"></a>Comentários  
 Enquanto os elementos sob `InstallChecks` definir os testes a serem executados, eles não executá-los. Para executar os testes, você deve criar `Command` elementos sob o `Commands` elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra o `InstallChecks` elemento como ele é usado no arquivo de produto para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Quando `InstallChecks` são avaliadas, geram propriedades. As propriedades são usadas pelo `InstallConditions` para determinar se um pacote deve instalar, ignorar ou falhar. A seguinte tabela lista o `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Se houver `FailIf` condição for avaliada como true, o pacote falhará. O restante das condições não será avaliado.|  
|`BypassIf`|Se houver `BypassIf` condição for avaliada como true, o pacote será ignorado. O restante das condições não será avaliado.|  
  
## <a name="predefined-properties"></a>Propriedades predefinidas  
 A seguinte tabela lista o `BypassIf` e `FailIf` elementos:  
  
|Propriedade|Observações|Valores possíveis|  
|--------------|-----------|---------------------|  
|`Version9X`|Número de versão de um sistema de operacional do Windows 9x X.|4.10 = Windows 98|  
|`VersionNT`|Número de versão de um sistema operacional do Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|Número de versão de um sistema de operacional de 64 bits no Windows NT.|Mesmo que mencionadas anteriormente.|  
|`VersionMsi`|Número de versão do serviço Windows Installer.|2.0 = Windows Installer 2.0|  
|`AdminUser`|Especifica se um usuário tem privilégios de administrador em um sistema operacional do Windows NT.|0 = sem privilégios de administrador<br /><br /> 1 = privilégios de administrador|  
  
 Por exemplo, para bloquear a instalação em um computador executando o Windows 95, use o código como o seguinte:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Consulte também  
 [\<Comandos > elemento](../deployment/commands-element-bootstrapper.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)