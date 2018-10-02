---
title: Melhores práticas para uso de snippets de código | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c775dd0f5c7242779dcded5027ebf92e51a0406
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462855"
---
# <a name="best-practices-for-using-code-snippets"></a>Práticas recomendadas para usar snippets de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [práticas recomendadas para usar trechos de código](https://docs.microsoft.com/visualstudio/ide/best-practices-for-using-code-snippets).  
  
O código em um snippet de código mostra somente a maneira mais simples de fazer algo. Para a maioria dos aplicativos, o código deve ser modificado para se adaptar ao aplicativo.  
  
## <a name="handling-exceptions"></a>Tratando exceções  
 Normalmente, o snippet de código Try...Catch bloqueia a captura e gera todas as exceções novamente. Essa pode não ser a escolha certa para seu projeto. Para cada exceção, existem várias maneiras de responder. Para obter exemplos, consulte [Como manipular uma exceção usando try/catch (Guia de Programação do C#)](http://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) e [Instrução Try... Catch...Finally](http://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b).  
  
## <a name="file-locations"></a>Locais dos arquivos  
 Quando você adaptar locais de arquivo ao seu aplicativo, deverá considerar o seguinte:  
  
-   Encontrando um local acessível. Os usuários poderão não ter acesso à pasta Arquivos de Programas do computador; portanto, armazenar arquivos com os arquivos do aplicativo pode não funcionar.  
  
-   Encontrando um local seguro. Armazenar arquivos na pasta raiz (C:\\) não é seguro. Para dados do aplicativo, é recomendável usar a pasta \Application Data. Para dados individuais do usuário, o aplicativo pode criar um arquivo para cada usuário na pasta \My Documents.  
  
-   Usando um nome de arquivo válido. Você pode usar os controles <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> para reduzir a probabilidade de nomes de arquivo inválidos. Lembre-se de que entre o momento em que o usuário seleciona um arquivo e o momento em que o código manipula o arquivo, o arquivo poderá ser excluído. Além disso, o usuário poderá não ter permissões para gravar no arquivo.  
  
## <a name="security"></a>Segurança  
 A segurança de um snippet depende do local em que ele é usado no código-fonte e de como ele é modificado quando estiver no código. A lista a seguir contém algumas das áreas que devem ser consideradas.  
  
-   Acesso ao arquivo e ao banco de dados  
  
-   Segurança de acesso do código  
  
-   Protegendo recursos (como logs de eventos, Registro)  
  
-   Armazenando segredos  
  
-   Verificando as entradas  
  
-   Passando dados para tecnologias de script  
  
 Para obter mais informações, consulte [Protegendo aplicativos](../ide/securing-applications.md).  
  
## <a name="downloaded-code-snippets"></a>Snippets de código baixados  
 Os snippets de código do IntelliSense instalados pelo Visual Studio não são em si um risco de segurança. No entanto, eles podem criar riscos de segurança no aplicativo. Snippets baixados na Internet devem ser tratados como qualquer outro conteúdo baixado – com muito cuidado.  
  
-   Baixe snippets somente em sites confiáveis e use um software antivírus atualizado.  
  
-   Abra todos os arquivos de snippet baixados no Bloco de notas ou no editor de XML do Visual Studio e examine-os cuidadosamente antes de instalá-los. Procure os seguintes problemas:  
  
    -   O snippet de código poderá danificar o sistema se for executado. Leia atentamente o código-fonte antes de executá-lo.  
  
    -   O bloco URL de Ajuda do arquivo de snippet pode conter URLs que executam um arquivo de script mal-intencionado ou exibir um site ofensivo.  
  
    -   O snippet pode conter referências que são adicionadas silenciosamente ao projeto e podem ser carregadas em qualquer lugar do sistema. Essas referências podem ter sido baixadas no computador em que você baixou o snippet. Depois, o snippet de código pode fazer uma chamada a um método na referência que executa um código mal-intencionado. Para se proteger contra um ataque desse tipo, examine os blocos Importações e Referências do arquivo de snippet.  
  
## <a name="see-also"></a>Consulte também  
 [Snippets de código do Visual Basic IntelliSense](http://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643)   
 [Protegendo aplicativos](../ide/securing-applications.md)   
 [Snippets de código](../ide/code-snippets.md)



