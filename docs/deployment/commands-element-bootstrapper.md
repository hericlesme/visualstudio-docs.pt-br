---
title: '&lt;Comandos&gt; elemento (Bootstrapper) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: ac8580a1b930d4ad18db9eebb275e4eb67d80c62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Comandos&gt; elemento (Bootstrapper)
O `Commands` elemento implementa testes descritos pelos elementos sob o `InstallChecks` elemento e declara qual pacote de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bootstrapper deve ser instalado se o teste falhar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `Commands` elemento é necessário. O elemento tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Reboot`|Opcional. Determina se o sistema deve ser reiniciado caso qualquer um dos pacotes retornar um código de saída de reinicialização. A lista a seguir mostra os valores válidos:<br /><br /> `Defer`. A reinicialização é adiada até que algum momento futuro.<br /><br /> `Immediate`. Faz com que uma reinicialização imediata se um dos pacotes retornou um código de saída de reinicialização.<br /><br /> `None`. Faz com que qualquer solicitação de reinicialização para ser ignorado.<br /><br /> O padrão é `Immediate`.|  
  
## <a name="command"></a>Comando  
 O `Command` é um elemento filho do `Commands` elemento. Um `Commands` elemento pode ter um ou mais `Command` elementos. O elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`PackageFile`|Necessário. O nome do pacote para instalar deve uma ou mais das condições especificadas pela `InstallConditions` retornar false. O pacote deve ser definido no mesmo arquivo usando um `PackageFile` elemento.|  
|`Arguments`|Opcional. Um conjunto de argumentos de linha de comando para passar para o arquivo de pacote.|  
|`EstimatedInstallSeconds`|Opcional. O tempo estimado, em segundos, ele usará para instalar o pacote. Esse valor determina o tamanho da barra de progresso que exibe o inicializador para o usuário. O padrão é 0, caso em que nenhum tempo de previsão é especificada.|  
|`EstimatedDiskBytes`|Opcional. A quantidade estimada de espaço em disco, em bytes, que o pacote ocupará após a instalação for concluída. Esse valor é usado em requisitos de espaço em disco rígido que o bootstrapper exibe para o usuário. O padrão é 0, no qual caso o bootstrapper não mostra os requisitos de espaço em disco rígido.|  
|`EstimatedTempBytes`|Opcional. A quantidade estimada de espaço temporário em disco, em bytes, o que exigirá que o pacote.|  
|`Log`|Opcional. O caminho para o arquivo de log que gera o pacote, relativo ao diretório raiz do pacote.|  
  
## <a name="installconditions"></a>InstallConditions  
 O `InstallConditions` elemento é um filho de `Command` elemento. Cada `Command` elemento pode ter no máximo uma `InstallConditions` elemento. Se nenhum `InstallConditions` existir, o pacote especificado por `Condition` sempre será executado.  
  
## <a name="bypassif"></a>BypassIf  
 O `BypassIf` elemento é um filho de `InstallConditions` elemento e descreve uma condição positiva sob a qual o comando não deve ser executado. Cada `InstallConditions` elemento pode ter zero ou mais `BypassIf` elementos.  
  
 `BypassIf`tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para testar. A propriedade deve anteriormente foram definida por um filho de `InstallChecks` elemento. Para obter mais informações, consulte [ \<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Necessário. O tipo de comparação a ser executada. A lista a seguir mostra os valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Necessário. O valor a ser comparado com a propriedade.|  
|`Schedule`|Opcional. O nome de um `Schedule` marca que define quando essa regra deve ser avaliada.|  
  
## <a name="failif"></a>FailIf  
 O `FailIf` elemento é um filho de `InstallConditions` elemento e descreve uma condição positiva sob a qual a instalação deverá parar. Cada `InstallConditions` elemento pode ter zero ou mais `FailIf` elementos.  
  
 `FailIf`tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Necessário. O nome da propriedade para testar. A propriedade deve anteriormente foram definida por um filho de `InstallChecks` elemento. Para obter mais informações, consulte [ \<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Necessário. O tipo de comparação a ser executada. A lista a seguir mostra os valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Necessário. O valor a ser comparado com a propriedade.|  
|`String`|Opcional. O texto a ser exibido para o usuário em caso de falha.|  
|`Schedule`|Opcional. O nome de um `Schedule` marca que define quando essa regra deve ser avaliada.|  
  
## <a name="exitcodes"></a>ExitCodes  
 O `ExitCodes` elemento é um filho de `Command` elemento. O `ExitCodes` elemento contém um ou mais `ExitCode` elementos, que determinam o que deve fazer a instalação em resposta a um código de saída de um pacote. Pode haver um opcional `ExitCode` elemento sob um `Command` elemento. `ExitCodes`não tem atributos.  
  
## <a name="exitcode"></a>ExitCode  
 O `ExitCode` elemento é um filho de `ExitCodes` elemento. O `ExitCode` elemento determina o que deve fazer a instalação em resposta a um código de saída de um pacote. `ExitCode`não contém nenhum elemento filho e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Value`|Necessário. O valor de código de saída ao qual este `ExitCode` elemento se aplica.|  
|`Result`|Necessário. Como a instalação deve reagir a este código de saída. A lista a seguir mostra os valores válidos:<br /><br /> `Success`. Sinaliza o pacote instalado como com êxito.<br /><br /> `SuccessReboot`. Sinalizadores de pacote instalado como com êxito e, em seguida, instrui o sistema seja reiniciado.<br /><br /> `Fail`. Sinaliza o pacote como falha.<br /><br /> `FailReboot`. Sinalizadores de pacote como falha e instrui o sistema seja reiniciado.|  
|`String`|Opcional. O valor a ser exibido para o usuário em resposta a este código de saída.|  
|`FormatMessageFromSystem`|Opcional. Determina se é necessário usar a mensagem de erro fornecida pelo sistema que corresponde ao código de saída, ou use o valor fornecido no `String`. Os valores válidos são `true`, que significa que você use o erro fornecido pelo sistema, e `false`, que significa usar a cadeia de caracteres fornecida pelo `String`. O padrão é `false`. Se essa propriedade for `false`, mas `String` não está definida, o erro fornecido pelo sistema será usado.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define os comandos para instalar o .NET Framework 2.0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de pacote e produto](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md)