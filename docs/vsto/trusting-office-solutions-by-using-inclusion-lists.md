---
title: Confiar em soluções do Office usando listas de inclusão | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e8b26ef4c262f830cd2c6444b56e05f128316c6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="trusting-office-solutions-by-using-inclusion-lists"></a>Confiando em soluções do Office usando listas de inclusões
  Listas de inclusão permitem aos usuários conceder confiança a soluções do Office que são assinados com um certificado que identifica o Editor. Listas de inclusão são específicas do usuário, e eles podem ser usados para personalizações no nível do documento e suplementos do VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Quando um usuário inicia uma solução do Office que não tenha sido concedida a relação de confiança para o usuário, a solução do Microsoft Office solicitará que ele ou ela uma decisão de segurança com um [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt confiável. Se o usuário decidir confiar a solução, as execuções de personalização e o usuário não é solicitado na próxima vez.  
  
## <a name="inclusion-list-and-windows-installer"></a>Lista de inclusão e do Windows Installer  
 A instalação de soluções do Office para o diretório de arquivos de programa usando o Windows Installer requer direitos de administrador. Para soluções do Office no diretório de arquivos de programa, o Visual Studio Tools for Office Runtime não verifica a lista de inclusão porque as soluções do Office já receberam permissão FullTrust.  
  
## <a name="clickonce-trust-prompt"></a>Prompt confiável do ClickOnce  
 Usando o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] implementação para soluções do Office, os administradores pode configurar o nível de confiança prompt para permitir Avisar, desabilitar solicitando ou exigem um certificado confiável. Essa configuração é feita usando uma chave do registro que controla o acesso à lista de inclusão.  
  
 Se o aviso for desabilitado, podem ser instaladas apenas as soluções que têm um certificado confiável e conhecido. Se o nível de solicitação é definido como Authenticode necessária, a solução deve ser assinada com um certificado de uma autoridade conhecido, mas não requer um certificado que se conecte a uma autoridade raiz confiável (um certificado confiável). Se o prompt é permitido, a solução poderia ser assinada com um certificado com uma identidade desconhecido. Nesse cenário, a decisão de confiança é adiada para o usuário final e um certificado temporário seria suficiente para instalar uma solução.  
  
 Para obter mais informações, consulte [como: configurar a segurança da lista de inclusão](../vsto/how-to-configure-inclusion-list-security.md) e a tabela 2, intitulada solicitando nível do registro chave valor iniciar efeitos, em [Configurar editores confiáveis do ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Estrutura da lista de inclusão  
 Uma entrada da lista de inclusão válido tem duas partes: um caminho para o manifesto de implantação e a chave pública usada para assinar a solução. Depois que uma solução é adicionada à lista de inclusão, ele é considerado confiável. Quando a solução do Office é executado, o aplicativo do Office compara a chave pública na lista de inclusão com a chave de assinatura no manifesto de implantação para verificar se a solução que está sendo executado é o mesmo que a versão original de confiável.  
  
## <a name="see-also"></a>Consulte também  
 [Concedendo confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md)   
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)  
  
  