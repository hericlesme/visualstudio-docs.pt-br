---
title: 'Como: aplicar as chaves de produto durante a implantação do Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 07f09cbc2deedaeb701a52ffc09532e36e30c308
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879065"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Como aplicar as chaves de produto automaticamente durante a implantação do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente do Visual Studio 2017, consulte [aplicar chaves de produto durante a implantação do Visual Studio](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Você pode aplicar a chave do produto por meio de programação como parte de um script usado para automatizar a implantação do Visual Studio 2015. Chaves do produto (Product Keys) podem ser definidas em um dispositivo de forma programática durante a instalação do Visual Studio ou após a conclusão de uma instalação.  
  
## <a name="apply-the-license-during-installation"></a>Aplicar a licença durante a instalação  
 Use o parâmetro /ProductKey para aplicar uma chave de produto durante o processo de instalação do Visual Studio. Esse parâmetro de instalação pode ser usado com o /Silent parâmetro para instalar o Visual Studio em um estado já licenciado para um usuário final. Para usar o parâmetro /ProductKey, abra um prompt de comando. Execute o programa de instalação (por exemplo, vs_enterprise.exe ou vs_professional.exe) e defina o parâmetro /ProductKey com uma chave do produto (25 caracteres) que inclui sem traços:  
  
 Este é um comando de exemplo para a instalação do Visual Studio 2015 Enterprise com a chave do produto (Product Key) AAAAABBBBBCCCCCDDDDDEEEEEEE:  
  
 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## <a name="apply-the-license-after-installation"></a>Aplicar a licença após a instalação  
 É possível ativar uma versão instalada do Visual Studio com uma chave do produto (Product Key) usando o utilitário storePID.exe nos computadores de destino no modo sem confirmação. StorePID.exe é um utilitário que é instalado com o Visual Studio  **\<unidade >:\\\Program arquivos (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.  
  
 Execute o storePID.exe com privilégios elevados, usando um agente do System Center ou em um prompt de comandos com privilégios elevados, seguido pela chave do produto (Product Key) (incluindo os traços) e o MPC (Código do Produto da Microsoft). Lembre-se de incluir os traços na chave do produto (Product Key).  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 Isso é uma linha de comando de exemplo para instalar o Visual Studio 2015 Enterprise, que tem um MPC de 07060, com uma chave de produto "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`  
  
 A seguinte tabela lista os códigos MPC para cada edição do Visual Studio:  
  
|Edição do Visual Studio|MPC|  
|---------------------------|---------|  
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  
  
 Para obter mais informações sobre como obter uma chave do produto, consulte [como: localizar a chave de produto do Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).  
  
 Se o StorePID.exe aplicou a chave do produto (Product Key) com êxito, ele retornará 0. Se ele encontrar erros, retornará um número entre 1 e 6.  
  
## <a name="see-also"></a>Consulte também  
 [Instalar o Visual Studio](../install/install-visual-studio-2015.md)