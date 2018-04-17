---
title: Colaboração de desenvolvimento de soluções do Office | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10415a6983c158ae1c117a5b3f9a8b2e1c546a0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Desenvolvimento de colaboração de soluções do Office
  Vários desenvolvedores podem trabalhar em um projeto do Office, da mesma forma que eles colaboram em outros projetos do Visual Studio. O Visual Studio corretamente localiza a instalação do Microsoft Office em cada computador, mesmo se o Office é instalado em locais diferentes. No entanto, há algumas considerações importantes a serem consideradas.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Depurar propriedades não são compartilhadas  
 Depurar propriedades não são compartilhadas entre vários usuários sob controle de origem. Projetos Visual Basic e Visual c# armazenam propriedades de depuração em um arquivo específico do usuário (*ProjectName*. vbproj.user ou *ProjectName*. csproj.user), e esse arquivo não está sob controle de origem. Se a depuração de mais de uma pessoa, cada pessoa deve inserir propriedades de depuração manualmente.  
  
 Se o projeto está hospedado em um compartilhamento de rede em vez de no controle do código-fonte, algumas etapas adicionais devem ser executadas para habilitar os desenvolvedores de colaboração para abrir a solução e o assembly de teste.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Controle de origem requer o Check-Out de todos os arquivos  
 Se você usar o controle de origem para seus projetos, você deve verificar todos os arquivos em um arquivo de código em **Solution Explorer** (como os arquivos de código classe ThisAddIn, ThisWorkbook ou ThisDocument) sempre que você alterar o arquivo de código, até mesmo o arquivos que são ocultos por padrão. Se você verificar somente o arquivo de código de nível superior, as alterações podem ser perdidas.  
  
 Depois de fazer suas alterações, verifique todos os arquivos novamente. Para obter mais informações sobre arquivos de código oculto em projetos, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Segurança para colaboração Informal em uma rede  
 Todas as soluções de nível de documento que estão em um local de rede (como \\ \\ *Servername*\\*Sharename*), o local totalmente qualificado deve ser adicionado ao a lista de pasta confiável no aplicativo do Microsoft Office que você está trabalhando. Selecione a opção para incluir as subpastas da pasta principal, ou especificamente adicione debug e criar pastas à lista de pastas confiáveis. Para obter mais informações sobre como fazer isso, consulte [concedendo confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
 Os certificados temporários que são gerados automaticamente em tempo de compilação não estão protegidos por senhas. Os certificados contêm o nome de logon do desenvolvedor e outras informações pessoais. Se você implantar as personalizações que foram assinadas por certificados temporários, outros usuários poderá acessar essas informações.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Compilando soluções do Office](../vsto/building-office-solutions.md)  
  
  