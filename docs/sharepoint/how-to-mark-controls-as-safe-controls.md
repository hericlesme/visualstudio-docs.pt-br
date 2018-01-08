---
title: 'Como: marcar controles como controles seguros | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bd659a1df9782c4e16dd2664a27a87e858e54ef2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Como marcar controles como controles seguros
  Para segurança, o SharePoint faz distinção entre os controles da Web que estejam protegidos contra injeção de script e controles da Web que não são. Protegido por controles, ou *controles seguros*, podem ser acessados por usuários não confiáveis. Você pode marcar controles como seguro na propriedade entradas de controle de segurança de um item de projeto do SharePoint ou no **Package Designer** quando você adiciona um assembly para o pacote. Para saber mais, veja  
  
 [Alteração das configurações de arquivo de Web. config](http://go.microsoft.com/fwlink/?LinkId=178965) e [Registrando um Assembly de parte da Web como um controle seguro](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Esses procedimentos são para fins ilustrativos. Marcar controles seguros somente se você tiver certeza de que eles estejam protegidos.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Marcar controles seguros na propriedade de entradas de controle de segurança  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Para marcar controles como seguro ou não seguro na propriedade de entradas de controle de segurança  
  
1.  Crie uma solução do SharePoint com um projeto do Visual Web Part.  
  
2.  Adicionar dois controles para a Web part: uma caixa de texto e um botão. Deixe os nomes de valores padrão, TextBox1 e Button1, respectivamente.  
  
3.  Adicionar duas entradas para a Web part **entradas de controle de segurança** propriedade. Para fazer isso, escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) próximo ao **entradas de controle de segurança** propriedade o  **Propriedades** janela.  
  
     O **entradas de controle de segurança** caixa de diálogo é exibida.  
  
4.  No **entradas de controle de segurança** caixa de diálogo caixa, escolha o **adicionar** botão duas vezes para adicionar duas entradas de controle de segurança para o **membros** painel: uma para o botão e uma caixa de texto.  
  
5.  Escolha a primeira entrada de controle de segurança e, em seguida, altere o valor de seu **seguro** propriedade para **False**, sua **nome do tipo** propriedade **Button1**e sua **seguro contra Script** propriedade **False**.  
  
     Esta etapa identifica o controle de botão como um controle não seguro.  
  
6.  Escolha a segunda entrada de controle de segurança na lista. Deixe o valor de seu **seguro** a propriedade como **True** e defina seu **nome do tipo** propriedade **TextBox1** e sua **seguro No Script** propriedade **True**.  
  
     O controle de caixa de texto está marcado como um controle que é seguro contra injeção de script.  
  
7.  Escolha o botão **OK** para fechar a caixa de diálogo.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Marcar controles seguros no Designer de pacote  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Para marcar controles como seguro ou não seguro no Designer de pacote  
  
1.  Crie uma solução do SharePoint com um projeto do Visual Web Part.  
  
2.  Adicionar dois controles para a Web part: uma caixa de texto e um botão. Deixe os nomes de valores padrão, TextBox1 e Button1, respectivamente.  
  
     Anote o namespace do controle, porque ele é usado posteriormente.  
  
3.  Na barra de menus, escolha **criar**, **compilar solução** para compilar o projeto.  
  
4.  Crie outra solução do SharePoint.  
  
5.  Em **Solution Explorer**, abra o menu de atalho para o arquivo de pacote e, em seguida, escolha **abrir** para abrir o **Package Designer**.  
  
6.  No **Package Designer**, escolha o **avançado** guia.  
  
7.  Em **Assemblies adicionais**, escolha o **adicionar** botão e, em seguida, escolha **adicionar Assembly existente** da lista.  
  
8.  No **adicionar Assembly existente** caixa de diálogo caixa, escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) próximo ao  **Caminho de origem**.  
  
9. Escolha o assembly da solução do SharePoint que você criou na etapa 1 e, em seguida, escolha o **abrir** botão.  
  
10. Neste exemplo, deixe o **destino de implantação** opção como GlobalAssemblyCache.  
  
     Esta etapa faz com que o assembly implantar o sistema de Cache de Assembly Global (GAC). Se você quiser que o assembly para implantar na pasta do aplicativo (Bin) da Web, selecione essa opção. Para obter mais informações, consulte [implantação de Web Parts do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. No **controles seguros** caixa, escolha o **clique aqui para adicionar um novo item** botão.  
  
12. Digite os valores para as propriedades da tabela a seguir.  
  
    |Nome da Propriedade|Valor|  
    |-------------------|-----------|  
    |Namespace|O namespace totalmente qualificado para o controle, como **BdcModelProject1.VisualWebPart1**.|  
    |Nome do tipo|Button1|  
    |Nome do Assembly|Nome de um conjunto de alta segurança, como: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Limpar o **seguro** caixa de seleção.|  
    |Segurança em Script|Deixe o **seguro contra Script** caixa de seleção desmarcada.|  
  
    > [!NOTE]  
    >  O **nome do Assembly** valor para assemblies adicionados por meio do **avançado** guia do **Package Designer** não é um token, ele deve ser um assembly de nome forte. Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Escolha a tecla Tab para criar outra entrada de controle de segurança.  
  
14. Escolha o **clique aqui para adicionar um novo item** novamente.  
  
15. Digite os valores para as propriedades da tabela a seguir.  
  
    |Nome da Propriedade|Valor|  
    |-------------------|-----------|  
    |Namespace|O namespace totalmente qualificado para o controle, como **BdcModelProject1.VisualWebPart1**.|  
    |Nome do tipo|TextBox1|  
    |Nome do Assembly|Nome de um conjunto de alta segurança, como: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Selecione o **seguro** caixa de seleção.|  
    |Segurança em Script|Selecione o **seguro contra Script** caixa de seleção.|  
  
16. Escolha a tecla Tab e, em seguida, escolha o **Okey** para fechar a caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Fornecimento de empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  