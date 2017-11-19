---
title: "Página de publicação, Project Designer (desenvolvimento do Office no Visual Studio) | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
ms.assetid: 94d9bdf1-84fa-4e26-8ece-a1a0dabda5ea
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ce726d9d86bd57e5cf245010212545f0055c8ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Publicar Página, Designer de Projeto (desenvolvimento do Office no Visual Studio)
  O **publicar** página do **Project Designer** é usado para configurar as propriedades de implantação.  
  
 Para acessar essa página, selecione o projeto no **Gerenciador de soluções**e, em seguida, o **projeto** menu, escolha *Projectname* **propriedades** . Se o **publicar** página não for exibida, escolha o **publicar** guia.  
  
> [!NOTE]  
>  Você também pode definir o local de publicação **Assistente de publicação**. Para obter mais informações, consulte [Como publicar uma solução do Office usando o ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Local da pasta de publicação (site da web, servidor ftp ou caminho do arquivo)**  
 Necessário.  
  
 O local da pasta de publicação é o diretório para o qual o Visual Studio copia os arquivos de solução como os manifestos, assemblies e outros arquivos da compilação. Você deve ter acesso de gravação a esse diretório.  
  
 Opções incluem o computador local, um compartilhamento de arquivo UNC ou um site HTTP/HTTPS. O caminho pode ser local (*c:\foldername\publishfolder*) relativo (*publicar\\*), ou um local totalmente qualificado (*\\\servername\foldername* ou http://*servername/foldername*).  
  
 Por padrão, o local de publicação é *http://localhost/projectname/* se tiver instalado o IIS ou o diretório Publish se você fizer não tem o IIS instalado.  
  
 **URL da Pasta de Instalação**  
 Opcional.  
  
 A URL da pasta de instalação é o diretório do qual o usuário final instalará a personalização. Também é o caminho que a solução usará para verificar as atualizações. O caminho pode ser o mesmo que o local da pasta de publicação, mas isso não é um requisito.  
  
 Opções incluem o computador local, um compartilhamento de arquivo UNC ou um site HTTP/HTTPS. O caminho pode ser local (*c:\foldername\publishfolder*) relativo (*publicar\\*), ou um local totalmente qualificado (*\\\servername\foldername* ou http://*servername/foldername*). Todos os locais de HTTP/HTTPS devem ser criados com caracteres US-ASCII. Não há suporte para caracteres Unicode.  
  
 Se o caminho de instalação for definido, os arquivos de personalização devem ser no local para os usuários instalarem a personalização. O local deve ser definido somente se você souber o local de implantação final.  
  
 Se os arquivos de instalação estão em um local relativo ao documento ou programa de instalação, como com a opção de CD, deixe essa caixa em branco.  
  
 Esse valor pode ser atribuído posteriormente por um administrador. Para obter mais informações, consulte [como: alterar o caminho de instalação de uma solução do Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 **Pré-requisitos**  
 Os pré-requisitos podem ser incluídos com o programa de instalação ou baixados sob demanda durante a instalação.  
  
-   **Baixar pré-requisitos do site do fornecedor de componentes**: Use esta opção para baixar esses pré-requisitos da Microsoft.  
  
-   **Baixar pré-requisitos do mesmo local de meu aplicativo**: Use esta opção para os pré-requisitos no instalador do pacote. Incluir os arquivos de pré-requisito com o programa de instalação aumenta o tamanho da solução.  
  
-   **Baixar pré-requisitos no seguinte local**: Use esta opção para disponibilizar os pré-requisitos para os usuários finais separadamente como outro programa de instalação em uma página da web ou um compartilhamento de rede.  
  
 **Atualizações**  
 O intervalo de atualização determina quantas vezes a solução verifica se há atualizações. O padrão é verificar a cada sete dias.  
  
 Verificando atualizações sempre que um suplemento do VSTO ou personalização no nível do documento é carregado seria mantê-lo atualizado, mas afetaria o desempenho de inicialização.  
  
 Se você estiver implantando usando um CD ou unidade removível, defina isso para **nunca verificar se há atualizações**.  
  
 **Opções (Descrição)**  
 As opções de publicação para as seguintes propriedades podem ser definidas:  
  
-   A linguagem de publicação: a localidade da solução Office.  
  
-   Nome do publicador: o nome da empresa ou o desenvolvedor como ele aparece na **adicionar ou remover programas** ou **programas e recursos**.  
  
-   Nome do produto: o nome da solução Office como ele aparece na **adicionar ou remover programas** ou **programas e recursos**.  
  
-   URL de suporte: o local para os usuários finais contatar o suporte técnico para a solução do Office.  
  
 **Opções (configurações do Office)**  
 As opções de publicação para as seguintes propriedades podem ser definidas:  
  
-   Nome da solução: o nome da solução Office como ela aparece no aplicativo do Office.  
  
-   Descrição: a descrição da solução Office como ela aparece no aplicativo do Office.  
  
-   Comportamento de carregamento do suplemento do VSTO.  
  
    -   O carregamento durante a inicialização: Especifica que o suplemento do VSTO carrega ao inicia o aplicativo do Office.  
  
    -   Carga sob demanda: Especifica que o suplemento do VSTO é carregado quando o aplicativo requer, como quando um usuário clica em um elemento de interface do usuário que usa a funcionalidade de suplemento do VSTO.  
  
 **Idioma da publicação**  
 Essa opção define o idioma dos termos de licença de Software Microsoft e inclui os pacotes de idiomas na lista de pré-requisitos. Ele não afeta o idioma da personalização. O idioma do programa de instalação é determinado pelo idiomas instalados do Visual Studio.  
  
 Para obter mais informações sobre como alterar o **a linguagem de publicação**, consulte [como: alterar o idioma de publicação para um aplicativo ClickOnce](/visualstudio/deployment/how-to-change-the-publish-language-for-a-clickonce-application).  
  
 **Versão da Publicação**  
 Define o número de versão para a personalização. Quando o número de versão é alterado, o aplicativo é publicado como uma atualização. Uma nova pasta é criada para cada versão durante o processo de compilação para evitar a substituição da versão anteriormente publicada. Cada parte da versão de publicação (**principais**, **secundária**, **criar**, **revisão**) pode conter até cinco dígitos.  
  
 **Incrementar automaticamente a revisão com cada versão**  
 Opcional. Quando marcada (padrão), o **revisão** parte do número de versão é incrementado em um cada vez que a personalização é publicada. Isso faz com que a personalização ser publicado como uma atualização.  
  
 **Publicar Agora**  
 Publica o aplicativo usando as configurações atuais. Equivalente a **concluir** no botão o **Assistente de publicação**.  
  
## <a name="see-also"></a>Consulte também  
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Implantando uma solução do Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Pré-requisitos de solução do Office para implantação](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e)  
  
  