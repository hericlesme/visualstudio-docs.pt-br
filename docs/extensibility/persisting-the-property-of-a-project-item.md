---
title: Manter a propriedade de um Item de projeto | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6b0bc529e01d8ef34b6959b98d773857000ec1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138048"
---
# <a name="persisting-the-property-of-a-project-item"></a>Manter a propriedade de um Item de projeto
Talvez você queira manter uma propriedade que você adicionar a um item de projeto, como o autor de um arquivo de origem. Você pode fazer isso ao armazenar a propriedade no arquivo de projeto.

 A primeira etapa para manter uma propriedade em um arquivo de projeto é obter a hierarquia do projeto como uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface. Você pode obter essa interface usando automação ou usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Depois de obter a interface, você pode usá-lo para determinar qual item de projeto está selecionado no momento. Uma vez que a ID do item de projeto, você pode usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> para adicionar a propriedade.

 Nos procedimentos a seguir, você manter a propriedade de VsPkg.cs `Author` com o valor `Tom` no arquivo de projeto.

### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Para obter a hierarquia de projeto com o objeto DTE

1.  Adicione o seguinte código ao seu VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Para manter a propriedade de item de projeto com o objeto DTE

1.  Adicione o seguinte código ao código fornecido no método no procedimento anterior:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Para obter a hierarquia de projeto usando IVsMonitorSelection

1.  Adicione o seguinte código ao seu VSPackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

2.

### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Para manter a propriedade de item de projeto selecionado, considerando a hierarquia de projeto

1.  Adicione o seguinte código ao código fornecido no método no procedimento anterior:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-verify-that-the-property-is-persisted"></a>Para verificar se a propriedade é mantida

1.  Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e, em seguida, abra ou crie uma solução.

2.  Selecione o projeto item VsPkg.cs em **Gerenciador de soluções**.

3.  Usar um ponto de interrupção ou caso contrário, determinar que seu VSPackage seja carregado e SetItemAttribute é executado.

    > [!NOTE]
    > É possível autoload um VSPackage no contexto da interface do usuário <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Para obter mais informações, consulte [VSPackages carregar](../extensibility/loading-vspackages.md).

4.  Fechar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e, em seguida, abra o arquivo de projeto no bloco de notas. Você deve ver o \<Autor > marca com o valor de Tom, da seguinte maneira:

    ```xml
    <Compile Include="VsPkg.cs">
        <Author>Tom</Author>
    </Compile>
    ```

## <a name="see-also"></a>Consulte também

- [Ferramentas personalizadas](../extensibility/internals/custom-tools.md)