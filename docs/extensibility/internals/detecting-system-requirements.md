---
title: Detecção de requisitos do sistema | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e98235bd224876b00714e1f71210ea69cb6faff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128698"
---
# <a name="detecting-system-requirements"></a>Detecção de requisitos do sistema
Um VSPackage não funcionará a menos que o Visual Studio está instalado. Quando você usar o Microsoft Windows Installer para gerenciar a instalação do seu VSPackage, você pode configurar o instalador para detectar se o Visual Studio está instalado. Você também pode configurar para verificar o sistema para outros requisitos, por exemplo, uma versão específica do Windows ou uma determinada quantidade de RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Detectando as edições do Visual Studio  
 Para determinar se uma edição do Visual Studio está instalada, verifique se o valor da chave do registro de instalação (REG_DWORD) 1 na pasta apropriada, conforme listado na tabela a seguir. Observe que há uma hierarquia de edições do Visual Studio:  
  
1.  Enterprise  
  
2.  Professional  
  
3.  Comunidade  
  
 Quando um "superior" edition está instalado, as chaves do registro para essa edição, bem como para edições "inferiores" são adicionadas. Ou seja, se a Enterprise edition está instalada, a chave de instalação é definida como 1 para a empresa, bem como para as edições Professional e comunidade. Portanto, você precisa verificar somente a edição "mais alta" é necessário.  
  
> [!NOTE]
>  A versão de 64 bits do editor do registro, chaves de 32 bits são exibidas no HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. As chaves do Visual Studio estão em HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produto|Chave|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrado e isolado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Detectar quando o Visual Studio está em execução  
 O VSPackage não pode ser registrado corretamente se o Visual Studio está em execução quando o VSPackage é instalado. O instalador deve detectar quando o Visual Studio está em execução e, em seguida, recusar-se instalar o programa. Windows Installer não permitem que você use as entradas da tabela para habilitar essa detecção. Em vez disso, você deve criar uma ação personalizada, da seguinte maneira: Use o `EnumProcesses` função para detectar o processo devenv.exe e, em seguida, definir uma propriedade de instalador que é usada em uma condição de inicialização ou condicionalmente exibir uma caixa de diálogo que solicita ao usuário para fechar O Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Instalar VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)