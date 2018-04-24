---
title: 'Como: sinal de arquivos de instalação com SignTool.exe (ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc4dc7b2f96b1d36e91e8114458a7a8e9f3231f3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Como assinar arquivos de instalação com SignTool.exe (ClickOnce)
Você pode usar o SignTool.exe para assinar um programa de instalação (setup.exe). Esse processo ajuda a garantir que arquivos violados não sejam instalados nos computadores dos usuários finais.  
  
 Por padrão, o ClickOnce tem manifestos e um programa de instalação assinados. No entanto, se você quiser alterar os parâmetros do programa de instalação mais tarde, assine o programa de instalação mais tarde. Se você alterar os parâmetros depois que o programa de instalação for assinado a assinatura é corrompida.  
  
 O procedimento a seguir gera manifestos assinados e um programa de instalação não assinado. A assinatura do ClickOnce está habilitada no Visual Studio para gerar manifestos assinados. O programa de instalação é deixado sem assinatura para que o cliente possa assinar o executável com seu próprio certificado.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Para gerar um programa de instalação não assinado e assinar mais tarde  
  
1.  No computador de desenvolvimento, instale o certificado com qual você deseja assinar os manifestos.  
  
2.  Selecione o projeto na **Gerenciador de soluções**.  
  
3.  Sobre o **projeto** menu, clique em *ProjectName* **propriedades**.  
  
4.  No **assinatura** página, desmarque **assinar os manifestos ClickOnce**.  
  
5.  No **publicar** , clique em **pré-requisitos**.  
  
6.  Verifique se todos os pré-requisitos estão selecionados e, em seguida, clique em **Okey**.  
  
7.  No **publicar** página, verifique se as configurações de publicação e, em seguida, clique em **publicar agora**.  
  
     A solução publica o manifesto de aplicativo não assinado, o manifesto de implantação não assinado, os arquivos específicos de versão e o programa de instalação não assinado no local da pasta de publicação.  
  
8.  No **publicar** , clique em **pré-requisitos**.  
  
9. No **pré-requisitos** caixa de diálogo, desmarque **criar o programa de instalação para instalar os componentes de pré-requisito**.  
  
10. No **publicar** página, verifique se as configurações de publicação e, em seguida, clique em **publicar agora**.  
  
     A solução publica o manifesto de aplicativo assinado, o manifesto de implantação assinado, os arquivos específicos de versão e o local da pasta de publicação. O programa de instalação não assinado não é substituído pelo processo de publicação.  
  
11. No site do cliente, abra um prompt de comando.  
  
12. Mude para o diretório que contém o arquivo .exe.  
  
13. Assine o arquivo .exe com o seguinte comando:  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Por exemplo, para assinar o programa de instalação, use um dos seguintes comandos:  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Como assinar manifestos de aplicativo e implantação novamente](../deployment/how-to-re-sign-application-and-deployment-manifests.md)