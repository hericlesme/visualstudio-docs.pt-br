---
title: 'Como: definir um local de arquivo de Log personalizado para erros de implantação do ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647eed5145d9d80f9fc62249763726a5940a7345
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Como definir o local de um arquivo de log personalizado para erros de implantação do ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantém os arquivos de log de ativação para todas as implantações. Esses logs documentar todos os erros relacionados à instalação e inicialização de um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação. Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cria um arquivo de log para a ativação de cada implantação. Ele armazena esses arquivos de log na pasta arquivos temporários da Internet. O arquivo de log para uma implantação é exibido para o usuário quando ocorrer uma falha de ativação, e o usuário clica **detalhes** na caixa de diálogo de erro resultante.  
  
 Você pode alterar esse comportamento para um cliente específico usando o Editor do registro (**regedit.exe**) para definir um caminho de arquivo de log personalizado. Nesse caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] logs sucessos de ativação e falhas de todas as implantações em um único arquivo.  
  
> [!CAUTION]
>  Se você usar o Editor do Registro incorretamente, você poderá causar sérios problemas que talvez exijam a reinstalação do sistema operacional. Use o Editor do registro por seu próprio risco.  
  
> [!NOTE]
>  Você precisará Trunque ou exclua o arquivo de log, ocasionalmente, para impedir que ele fique muito grande.  
  
 O procedimento a seguir descreve como definir um local de arquivo de log personalizado para um único cliente.  
  
### <a name="to-set-a-custom-log-file-location"></a>Para definir um local de arquivo de log personalizado  
  
1.  Abra **Regedit.exe**.  
  
2.  Navegue até o nó `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Defina o valor de cadeia de caracteres `LogFilePath` para o caminho completo e o nome do seu local de log personalizado preferencial.  
  
     Esse local deve ser em um diretório no qual o usuário tem acesso de gravação. Por exemplo, no Windows Vista, crie a seguinte estrutura de pasta e definir `LogFilePath` para C:\Users\\< nome de usuário\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas de implantações ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)