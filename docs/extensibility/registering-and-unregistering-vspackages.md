---
title: Registrando e Cancelando o registro VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73dccc4aef061aaac5f5c33e098a591a7c51fcbb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="registering-and-unregistering-vspackages"></a>Registrando e Cancelando o registro VSPackages
Usar atributos para registrar um VSPackage, mas  
  
## <a name="registering-a-vspackage"></a>Registrando um VSPackage  
 Você pode usar atributos para controlar o registro de VSPackages gerenciados. Todas as informações de registro estão contidas em um arquivo .pkgdef. Para obter mais informações sobre o registro com base em arquivo, consulte [CreatePkgDef utilitário](../extensibility/internals/createpkgdef-utility.md).  
  
 O código a seguir mostra como usar os atributos padrão de registro para registrar seu VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Cancelar o registro de uma extensão  
 Se você testar para muita VSPackages diferentes e deseja removê-las da instância experimental, é possível executar o **redefinir** comando. Procure **redefinir a instância Experimental do Visual Studio** na página inicial do seu computador, ou executar este comando de linha de comando:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Se você deseja desinstalar uma extensão que você instalou na sua instância de desenvolvimento do Visual Studio, vá para **ferramentas / extensões e atualizações**, localizar a extensão e clique em **desinstalação**.  
  
 Se por alguma razão nenhum desses métodos tiver êxito na desinstalação da extensão, você pode cancelar o registro do assembly VSPackage da linha de comando da seguinte maneira:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Usar um atributo de registro personalizadas para registrar uma extensão  
  
Em certos casos, talvez seja necessário criar um novo atributo de registro para a sua extensão. Você pode usar atributos de registro para adicionar novas chaves de registro ou para adicionar novos valores para as chaves existentes. O novo atributo deve derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, e deve substituir o <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> métodos.  
  
### <a name="creating-a-custom-attribute"></a>Criando um atributo personalizado  
  
O código a seguir mostra como criar um novo atributo de registro.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 O <xref:System.AttributeUsageAttribute> é usado em classes de atributos para especificar o elemento do programa (classe, método, etc.) para que o atributo pertence, se ele pode ser usado mais de uma vez e se ele pode ser herdado.  
  
### <a name="creating-a-registry-key"></a>Criar uma chave do registro  
  
No código a seguir, o atributo personalizado cria um **personalizado** subchave sob a chave para o VSPackage que está sendo registrado.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Criando um novo valor em uma chave do registro existente  
  
Você pode adicionar valores personalizados para uma chave existente. O código a seguir mostra como adicionar um novo valor a uma chave de registro VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)