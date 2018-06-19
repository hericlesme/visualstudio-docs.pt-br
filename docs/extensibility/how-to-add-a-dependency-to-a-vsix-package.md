---
title: 'Como: adicionar uma dependência a um pacote do VSIX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0704a72ba70e2a00baab99d327702ec6c08f1775
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133216"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Como: adicionar uma dependência a um pacote do VSIX

Você pode configurar uma implantação de pacote VSIX que instala todas as dependências que não ainda estão presentes no computador de destino. Para fazer isso, inclua as dependências do VSIX para o arquivo source.extension.vsixmanifest.

## <a name="to-add-a-dependency"></a>Para adicionar uma dependência

1. Abra o arquivo source.extension.vsixmanifest no **Design** exibição. Vá para o **dependências** guia e clique em **novo**.

2. Para adicionar uma extensão instalada: no **adicionar nova dependência** caixa de diálogo, selecione **extensão instalada** e, em seguida, para o **nome**, selecione uma extensão na lista.

3. Para adicionar outro VSIX que não está instalado:: no **adicionar nova dependência** caixa de diálogo, selecione **arquivo no sistema de arquivos** e, em seguida, use o **procurar** para selecionar o VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Exigir uma versão específica do Visual Studio

Se sua extensão requer uma versão específica do Visual Studio de 2017, por exemplo, depende de um recurso lançado no 15,3, você pode especificar o número de compilação em seu VSIX **InstallationTarget**. Por exemplo, a versão 15,3 tem um número de compilação de '15.0.26730.3'. Você pode ver o mapeamento de versões para criar números [aqui](../install/visual-studio-build-numbers-and-release-dates.md). Observe que usando o número de versão '15,3' não funcionará corretamente.

Se sua extensão requer 15,3 ou superior, você deve declarar o **InstallationTarget versão** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

O VSIXInstaller detectará as versões anteriores do Visual Studio e informar ao usuário que é necessária uma atualização posterior.


## <a name="see-also"></a>Consulte também

 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [Anatomia de um pacote do VSIX](../extensibility/anatomy-of-a-vsix-package.md) [Preparando extensões para a implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)