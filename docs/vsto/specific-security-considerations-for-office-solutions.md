---
title: "Considerações sobre segurança específicas para soluções do Office | Microsoft Docs"
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
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f7f2e865ccb94a9996e13f7cf3c695784623fded
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="specific-security-considerations-for-office-solutions"></a>Considerações sobre segurança específicas para soluções do Office
  Os recursos de segurança fornecidos pelo Microsoft .NET Framework e do Microsoft Office podem ajudar a proteger as soluções do Office contra possíveis ameaças de segurança. Este tópico explica essas ameaças e fornece recomendações para ajudar a proteger contra elas. Ela também inclui informações sobre como as configurações de segurança do Microsoft Office afetam soluções do Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Confiável código é redefinido em um novo documento mal-intencionado  
 Um invasor pode executar código confiável destina-se para uma finalidade específica, por exemplo, fazer o download de informações pessoais para um aplicativo de emprego, e reutilizá-lo em outro documento, como uma planilha. O código não sabe que o documento original não está em execução e outras ameaças, como revelar informações pessoais ou execução de código com privilégios maiores, quando aberto por outro usuário pode abrir. Como alternativa, o invasor simplesmente pode modificar os dados na planilha, de modo que, quando enviado para a vítima, ele se comporta inesperadamente. Alterando os valores, fórmulas ou características de apresentação de uma planilha vinculada ao código, é possível que um usuário mal-intencionado atacar a outro usuário, enviando um arquivo modificado. Também é possível que os usuários que não deveriam ser consulte Modificando os valores na planilha de informações de acesso.  
  
 Como o local do assembly e o local do documento devem ter evidências suficientes para executar, esse ataque não é fácil de montagem. Por exemplo, documentos em anexos de email ou em servidores da intranet não confiáveis não tem permissões suficientes para executar.  
  
 Para tornar esse ataque possível, o código em si deve ser escrito de forma que ele toma decisões com base nos dados potencialmente não confiáveis. Um exemplo é criar uma planilha que contém uma célula oculta que contém o nome de um servidor de banco de dados. O usuário submete a planilha em uma página ASPX, que tenta se conectar ao servidor usando a autenticação do SQL e uma senha de SA embutido. Um invasor pode substituir o conteúdo da célula oculto com um nome de computador diferente e obter a senha de SA. Para evitar esse problema, senhas nunca codificar e sempre verifique as IDs do servidor em relação a uma lista interna de servidores que são conhecidos em boas condições antes de acessar o servidor.  
  
### <a name="recommendations"></a>Recomendações  
  
-   Sempre valide entrada de dados e, se ela é proveniente do usuário, o documento, um banco de dados, um serviço web ou qualquer outra fonte.  
  
-   Tenha cuidado ao expor determinados tipos de funcionalidades, como obter dados privilegiados em nome do usuário e colocá-lo em uma planilha desprotegida.  
  
-   Dependendo do tipo de aplicativo, pode fazer sentido para verificar se o documento original está em execução antes de executar qualquer código. Por exemplo, verificar se ele está em execução de um documento armazenado em um local seguro e conhecido.  
  
-   Pode ser uma boa ideia para exibir um aviso quando o documento for aberto, se seu aplicativo executa as ações privilegiadas. Por exemplo, você pode criar uma tela inicial ou uma caixa de diálogo de inicialização dizendo que o aplicativo acessar informações pessoais e que o usuário optar por continuar ou em Cancelar. Se um usuário final obtém um aviso desse tipo de um documento aparentemente inocente, ele poderá ser encerrar o aplicativo antes de qualquer coisa seja comprometida.  
  
## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Código está bloqueado pela proteção de modelo de objeto do Outlook  
 Microsoft Office pode impedir que o código usando determinadas propriedades, métodos e objetos no modelo de objeto. Restringindo o acesso a esses objetos, Outlook ajuda a impedir que emails worms e vírus usando o modelo de objeto para fins mal-intencionados. Esse recurso é conhecido como a proteção de modelo de objeto do Outlook. Se um suplemento do VSTO tenta usar um método ou propriedade restritos, enquanto a proteção de modelo de objeto é ativada, o Outlook exibe um aviso de segurança que permite que o usuário parar a operação ou permite que o usuário conceder acesso a propriedade ou método por um período limitado tempo. Se o usuário para a operação, o Outlook suplementos do VSTO criados por meio de soluções do Office no Visual Studio gerará um <xref:System.Runtime.InteropServices.COMException>.  
  
 A proteção de modelo de objeto pode afetar os suplementos do VSTO de maneiras diferentes, dependendo se o Outlook é usado com o Microsoft Exchange Server:  
  
-   Se o Outlook não for usado com o Exchange, um administrador pode habilitar ou desabilitar a proteção de modelo de objeto para todos os suplementos do VSTO no computador.  
  
-   Se o Outlook é usado com o Exchange, um administrador pode habilitar ou desabilitar a proteção de modelo de objeto para todos os suplementos do VSTO no computador, ou o administrador pode especificar que certos suplementos do VSTO podem ser executada sem encontrar o protetor de modelo de objeto. Os administradores também podem modificar o comportamento de proteção de modelo de objeto para determinadas áreas do modelo de objeto. Por exemplo, administradores podem permitir automaticamente suplemento do VSTO enviar email programaticamente, mesmo que a proteção de modelo de objeto esteja habilitada.  
  
 A partir do Outlook 2007, o comportamento de proteção de modelo de objeto foi alterado para melhorar a experiência de desenvolvedor e o usuário enquanto ajuda a proteger o Outlook. Para obter mais informações, consulte [alterações de segurança de código no Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).  
  
### <a name="minimizing-object-model-guard-warnings"></a>Minimizando avisos de proteção do modelo de objeto  
 Para evitar avisos de segurança quando você usar métodos e propriedades restritas, certifique-se de que seu suplemento do VSTO obtém objetos do Outlook do `Application` campo o `ThisAddIn` classe em seu projeto. Para obter mais informações sobre esse campo, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Somente objetos do Outlook obtidos do objeto podem ser confiável para a proteção de modelo de objeto. Por outro lado, os objetos que são obtidos de um novo objeto Microsoft.Office.Interop.Outlook.Application não são confiáveis e restrito de propriedades e métodos gerará avisos de segurança se a proteção de modelo de objeto é ativada.  
  
 O exemplo de código a seguir exibe um aviso de segurança se a proteção de modelo de objeto é ativada. A propriedade para a classe Microsoft.Office.Interop.Outlook.MailItem é restringida pela proteção de modelo de objeto. O objeto Microsoft.Office.Interop.Outlook.MailItem não é confiável porque o código obtém a ele de um Microsoft.Office.Interop.Outlook.Application que é criado usando o **novo** operador, em vez de obtenção do `Application` campo.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]  
  
 O exemplo de código a seguir demonstra como usar o restrito a propriedade de um objeto de Microsoft.Office.Interop.Outlook.MailItem que é confiável para a proteção de modelo de objeto. O código usa a confiável `Application` campo para obter o Microsoft.Office.Interop.Outlook.MailItem.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Se o Outlook é usado com o Exchange, em seguida, obter todos os objetos do Outlook do `ThisAddIn.Application` não garante que o suplemento do VSTO será capaz de acessar todo o modelo de objeto do Outlook. Por exemplo, se um administrador do Exchange define automaticamente o Outlook negar todas as tentativas de acessar informações de endereço usando o modelo de objeto do Outlook, Outlook não permitirá que o exemplo de código anterior acessar a propriedade To, mesmo que use o exemplo de código o confiável `ThisAddIn.Application` campo.  
  
### <a name="specifying-which-add-ins-to-trust-when-using-exchange"></a>Especificar os complementos para confiança ao usar o Exchange  
 Quando o Outlook é usado com o Exchange, os administradores podem especificar que certos suplementos do VSTO podem ser executada sem encontrar o protetor de modelo de objeto. Outlook suplementos do VSTO criados por meio de soluções do Office no Visual Studio não podem ser confiáveis individualmente; elas só podem ser confiáveis como um grupo.  
  
 Outlook confia um VSTO suplemento com base em um código hash da DLL de ponto de entrada do suplemento do VSTO. Todos os Outlook suplementos do VSTO que se destinam a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usar a mesma DLL de ponto de entrada (VSTOLoader.dll). Isso significa que, se um administrador confia qualquer VSTO suplemento que tem como alvo o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para ser executada sem encontrar o protetor de modelo de objeto e todos os outros suplementos do VSTO que tem como alvo o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] também são confiáveis. Para obter mais informações sobre como confiar em específicos suplementos do VSTO para ser executada sem encontrar o protetor de modelo de objeto, consulte [especificar o método usa o Outlook para gerenciar recursos de prevenção de vírus](http://go.microsoft.com/fwlink/?LinkId=128773).  
  
## <a name="permission-changes-do-not-take-effect-immediately"></a>As alterações não entram em vigor imediatamente  
 Se o administrador ajusta as permissões para um documento ou um assembly, os usuários deverão encerrar e, em seguida, reinicie todos os aplicativos do Office para essas alterações devem ser aplicadas.  
  
 Outros aplicativos que hospedam aplicativos do Microsoft Office também podem impedir que as novas permissões de imposição. Os usuários devem fechar todos os aplicativos que usam o Office, hospedado ou autônomo, quando as políticas de segurança são alteradas.  
  
## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Configurações da Central de confiabilidade do Microsoft Office System não afetam os suplementos ou personalizações no nível do documento  
 Os usuários podem impedir suplementos do VSTO carregamento, definindo uma opção no **Central de confiabilidade**. No entanto, suplementos do VSTO e personalizações de nível de documento criadas por meio de soluções do Office no Visual Studio não são afetadas por essas configurações de confiança.  
  
 Se o usuário impede que suplementos do VSTO carregamento usando o **Central de confiabilidade**, não carregará os seguintes tipos de suplementos do VSTO:  
  
-   Gerenciado e COM suplementos do VSTO.  
  
-   Documentos inteligentes de gerenciados e não gerenciados.  
  
-   Gerenciado e automação suplementos do VSTO.  
  
-   Componentes gerenciados e dados em tempo real.  
  
 Os procedimentos a seguir descrevem como os usuários podem usar o **Central de confiabilidade** para restringir os suplementos do VSTO de carregamento no Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e o Microsoft Office 2010. Esses procedimentos não afetam as personalizações criadas usando ferramentas de desenvolvimento do Office no Visual Studio ou suplementos do VSTO.  
  
#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>Para desabilitar o suplemento do VSTO no Microsoft Office 2010 e Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplicativos  
  
1.  Escolha o **arquivo** guia.  
  
2.  Escolha o *ApplicationName* **opções** botão.  
  
3.  No painel de categorias, escolha **Central de confiabilidade**.  
  
4.  No painel de detalhes, escolha **definições**.  
  
5.  No painel de categorias, escolha **suplementos**.  
  
6.  No painel de detalhes, selecione **suplementos sejam assinados por um fornecedor confiável aplicativo exigir** ou **desabilitar todos os complementos do aplicativo**.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)  
  
  