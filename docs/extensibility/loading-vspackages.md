---
title: Carregando VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 008cd31bc3d9f909477089e608393f596bfb0682
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="loading-vspackages"></a>Carregando VSPackages
VSPackages só são carregados no Visual Studio quando sua funcionalidade é necessária. Por exemplo, um VSPackage é carregado quando o Visual Studio usa uma fábrica de projeto ou um serviço que implementa o VSPackage. Esse recurso é chamado de carregamento atrasado, que é usado sempre que possível melhorar o desempenho.  
  
> [!NOTE]
>  O Visual Studio pode determinar a certas informações VSPackage, como os comandos que oferece um VSPackage, sem carregar o VSPackage.  
  
 VSPackages pode ser definidos como autoload em um contexto de interface de usuário específico, por exemplo, quando uma solução é aberta. O <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo define neste contexto.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Autoloading um VSPackage em um contexto específico  
  
-   Adicionar o `ProvideAutoLoad` atributo aos atributos VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Ver os campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obter uma lista de contextos de interface do usuário e seus valores GUID.  
  
-   Definir um ponto de interrupção no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
-   Compile o VSPackage e iniciar a depuração.  
  
-   Carregar uma solução ou criar um.  
  
     O VSPackage carrega e interrompida no ponto de interrupção.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forçar um VSPackage carregar  
 Em algumas circunstâncias, um VSPackage talvez precise forçar VSPackage outro a ser carregado. Por exemplo, um VSPackage leve pode carregar um VSPackage maior em um contexto que não está disponível como um CMDUIContext.  
  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forçar um VSPackage para carregar.  
  
-   Inserir este código para o <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método o VSPackage que força o VSPackage outro carregar:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Quando o VSPackage é inicializado, ele forçará `PackageToBeLoaded` para carregar.  
  
     Carregamento de força não deve ser usado para comunicação de VSPackage. Use [usando e fornecer serviços](../extensibility/using-and-providing-services.md) em vez disso.
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)
