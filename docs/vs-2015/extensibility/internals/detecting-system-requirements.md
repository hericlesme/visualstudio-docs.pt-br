---
title: Detectar os requisitos do sistema | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c9bdb2a9f33f848ed0ba879aa178efd8dd96016
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475860"
---
# <a name="detecting-system-requirements"></a>Detecção de requisitos do sistema
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [requisitos do sistema detectando](https://docs.microsoft.com/visualstudio/extensibility/internals/detecting-system-requirements).  
  
Um VSPackage não funcionará a menos que o Visual Studio está instalado. Quando você usa o Microsoft Windows Installer para gerenciar a instalação de seu VSPackage, você pode configurar o instalador para detectar se o Visual Studio está instalado. Você também pode configurá-lo para verificar o sistema para outros requisitos, por exemplo, uma versão específica do Windows ou uma determinada quantidade de RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Detectando as edições do Visual Studio  
 Para determinar se uma edição do Visual Studio está instalada, verifique se que o valor da chave do registro de instalação é (REG_DWORD) 1 na pasta apropriada, conforme listado na tabela a seguir. Observe que há uma hierarquia de edições do Visual Studio:  
  
1.  Enterprise  
  
2.  Professional  
  
3.  Comunidade  
  
 Quando uma edição "superior" é instalada, as chaves do registro para essa edição, bem como para as edições "inferiores" são adicionadas. Ou seja, se a Enterprise edition estiver instalada, a chave de instalação é definida como 1 para a empresa, bem como para as edições Professional e da comunidade. Portanto, você precisa apenas verificar a edição de "melhor" você precisa.  
  
> [!NOTE]
>  Na versão de 64 bits do editor do registro, chaves de 32 bits são exibidas em HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. As chaves do Visual Studio estão sob HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produto|Chave|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrado e isolado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Detectar quando o Visual Studio está em execução  
 O VSPackage não pode ser registrado corretamente se o Visual Studio está em execução quando o VSPackage é instalado. O instalador deve detectar quando o Visual Studio está em execução e, em seguida, se recusará a usar o programa. Windows Installer não permite que você use as entradas da tabela para habilitar essa detecção. Em vez disso, você deve criar uma ação personalizada, da seguinte maneira: Use o `EnumProcesses` função para detectar o processo de devenv.exe e, em seguida, definir uma propriedade de instalador que é usada em uma condição de inicialização ou condicionalmente exibir uma caixa de diálogo que solicita ao usuário para fechar Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Instalar VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

