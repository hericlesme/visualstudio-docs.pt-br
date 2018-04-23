---
title: 'Como: atualizar uma extensão do Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c37f26ed8215bb7eac360c978ba902c8e95975ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-update-a-visual-studio-extension"></a>Como: atualizar uma extensão do Visual Studio
Você pode atualizar uma extensão do Visual Studio em seu sistema usando **extensões e atualizações** para instalar a versão atualizada. Se você criar uma versão atualizada de uma extensão, significam como atualizados aumentando o número de versão no manifesto do VSIX.  
  
 As atualizações são instaladas quando o manifesto do VSIX da extensão de entrada tem o mesmo `ID` como instalado e uma maior `Version` número. Se o `Version` número é igual ou inferior, o pacote não pode ser instalado. Se o `ID` valores não coincidirem, o pacote ainda não estiver instalado é reconhecido como uma extensão separada.  
  
 Para ajudar a evitar conflitos durante o desenvolvimento, é recomendável que você desinstale as versões anteriores de extensões em andamento e também desinstala ou desabilitar outras extensões de potencialmente conflitantes.  
  
### <a name="to-update-an-extension-on-your-system"></a>Para atualizar uma extensão no seu sistema  
  
1.  Sobre o **ferramentas** menu, clique em **extensões e atualizações**.  
  
2.  No painel esquerdo, clique em **atualizações**.  
  
3.  No painel central, clique na atualização que você deseja instalar.  
  
     O número de versão da extensão atualizada é exibido no painel direito, junto com outras informações.  
  
4.  Na parte inferior do painel direito, clique em **atualização**.  
  
### <a name="to-publish-an-update-of-an-extension"></a>Para publicar uma atualização de uma extensão  
  
1.  No Visual Studio, abra a solução para a extensão que você deseja atualizar. Faça as alterações.  
  
    > [!IMPORTANT]
    >  Não assinado que todas as extensões de usuário não são atualizadas automaticamente. Você sempre deve assinar suas extensões.  
  
2.  Em **Solution Explorer**, abra source.extension.manifest.  
  
3.  No designer de manifesto, aumente o valor do número no **versão** campo.  
  
4.  Salve a solução e compilá-lo.  
  
5.  Carregar o novo arquivo .vsix (na pasta \bin\Debug\ do projeto) para o [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site da Web.  
  
     Quando um usuário que tenha uma versão anterior da extensão abre **extensões e atualizações**, a nova versão será exibida no **atualizações** listar, desde que a ferramenta é definida automaticamente procurar atualizações.  
  
     Você pode habilitar ou desabilitar a verificação automática de atualizações na parte inferior da **atualizações** painel (**habilitar/desabilitar a detecção automática de atualizações disponíveis**), as alterações que o **verificar atualizações** definindo em **Ferramentas / opções / ambiente / extensões e atualizações**.  
  
    > [!NOTE]
    >  A partir do Visual Studio 2015 Atualização 2, é possível especificar (em **Ferramentas/Opções/Ambiente/Extensões e Atualizações**) se você deseja atualizações automáticas para extensões por usuário, todas as extensões do usuário ou ambas (a configuração padrão).  
  
## <a name="see-also"></a>Consulte também  
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
