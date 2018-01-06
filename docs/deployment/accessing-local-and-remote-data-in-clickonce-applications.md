---
title: Acesso a dados locais e remotos em aplicativos ClickOnce | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d22180b0e48a875eaef3ab9e3b8ceac35b1fa6ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>Acessando dados locais e remotos em aplicativos ClickOnce
A maioria dos aplicativos consuma nem produza dados. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Fornece uma variedade de opções para ler e gravar dados, localmente e remotamente.  
  
## <a name="local-data"></a>Dados locais  
 Com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], você pode carregar e armazenar dados localmente usando qualquer um dos seguintes métodos:  
  
-   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Diretório de dados  
  
-   Armazenamentos isolado  
  
-   Outros arquivos locais  
  
### <a name="clickonce-data-directory"></a>Diretório de dados do ClickOnce  
 Cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo instalado em um computador local tem um diretório de dados, armazenado na pasta de documentos e as configurações do usuário. Qualquer arquivo incluído em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo e marcada como um arquivo de "dados" é copiado para esse diretório quando um aplicativo é instalado. Arquivos de dados podem ser de qualquer tipo de arquivo usado com mais frequência sendo texto, XML e arquivos de banco de dados, como arquivos. mdb do Microsoft Access.  
  
 O diretório de dados destina-se a dados de aplicativos gerenciados, o que é dados que o aplicativo armazena e mantém explicitamente. Todos estáticos, nondependency arquivos não está marcados como "dados" no manifesto do aplicativo em vez disso, residirão no diretório de aplicativo. Este diretório é onde residem os arquivos executáveis (.exe) do aplicativo e assemblies.  
  
> [!NOTE]
>  Quando um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo for desinstalado, o diretório de dados também é removido. Nunca use o diretório de dados para armazenar dados de usuários finais gerenciados, como documentos.  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>Marcar os arquivos de dados em uma distribuição do ClickOnce  
 Para colocar um arquivo existente dentro do diretório de dados, você deve marcar o arquivo existente como um arquivo de dados no seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivo de manifesto de aplicativo do aplicativo. Para obter mais informações, consulte [Como incluir um arquivo de dados em um aplicativo ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>Leitura e gravação para o diretório de dados  
 A leitura do diretório de dados requer que seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solicitação de aplicativo permissão de leitura; da mesma forma, a gravação para o diretório requer permissão de gravação. Seu aplicativo terá essa permissão automaticamente se ele estiver configurado para ser executado com confiança total. Para obter mais informações sobre como elevar permissões para seu aplicativo usando a elevação de permissões ou implantação de aplicativos confiáveis, consulte [proteger os aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Se sua organização não usar a implantação de aplicativos confiáveis e desativou a elevação de permissões, declarando permissões irá falhar.  
  
 Depois que seu aplicativo tiver essas permissões, ele pode acessar o diretório de dados por meio de chamadas de método em classes dentro de <xref:System.IO>. Você pode obter o caminho do diretório de dados em um Windows Forms [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo usando o <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> propriedade definida no <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> propriedade <xref:System.Deployment.Application.ApplicationDeployment>. Essa é a maneira recomendada e mais conveniente para acessar seus dados. O exemplo de código a seguir demonstra como fazer isso para um arquivo de texto denominado CSV.txt incluir em sua implantação como um arquivo de dados.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]  
  
 Para obter mais informações sobre como marcar arquivos na sua implantação, como arquivos de dados, consulte [como: incluir um arquivo de dados em um aplicativo ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 Você também pode obter o caminho do diretório de dados usando as variáveis relevantes no <xref:System.Windows.Forms.Application> classe, como <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 Manipulação de outros tipos de arquivos pode exigir permissões adicionais. Por exemplo, se você quiser usar um arquivo de banco de dados (. mdb) do Access, seu aplicativo deve declarar confiança total para usar o relevantes <xref:System.Data> classes.  
  
#### <a name="data-directory-and-application-versions"></a>Diretório de dados e versões de aplicativos  
 Cada versão de um aplicativo tem seu próprio diretório de dados, que é isolado de outras versões. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]cria esse diretório independentemente se os arquivos de dados são incluídos na implantação para que o aplicativo tem um local para criar novos arquivos de dados em tempo de execução. Quando uma nova versão de um aplicativo é instalada, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] copiará todos os arquivos de dados existentes do diretório de dados da versão anterior para diretório a nova versão de dados — se foram incluídas na implantação original ou criados pelo aplicativo.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]substituirá a versão mais antiga do arquivo com a versão mais recente do servidor se um arquivo de dados tem um valor de hash diferente na versão antiga do aplicativo como a nova versão. Além disso, se a versão anterior do aplicativo criado um novo arquivo tem o mesmo nome como um arquivo incluído na implantação da nova versão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] substituirá o arquivo da versão antiga com o novo arquivo. Em ambos os casos, os arquivos antigos serão incluídos em um subdiretório no diretório de dados denominado `.pre`, de modo que o aplicativo ainda pode acessar os dados antigos para fins de migração.  
  
 Se você precisar de mais refinado de migração de dados, você pode usar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API de implantação para realizar a migração personalizada de diretório Data antigo para o novo diretório de dados. Você precisará testar para um download disponível usando <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, baixe a atualização usando <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> ou <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>, e fazer qualquer migração de dados funcionam no seu próprio após a atualização for concluída.  
  
### <a name="isolated-storage"></a>Armazenamentos isolado  
 Armazenamento isolado fornece uma API para criar e acessar arquivos por meio de uma API simples. O local real dos arquivos armazenados é ocultado do desenvolvedor e o usuário.  
  
 Isolada funciona de armazenamento em todas as versões dos [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Armazenamento isolado também funciona em aplicativos parcialmente confiáveis sem a necessidade de concessões de permissão adicional. Se seu aplicativo deve ser executado em confiança parcial, mas deve manter dados específicos do aplicativo, você deve usar armazenamento isolado.  
  
 Para obter mais informações, consulte [armazenamento isolado](/dotnet/standard/io/isolated-storage).  
  
### <a name="other-local-files"></a>Outros arquivos locais  
 Se seu aplicativo deve funcionar com ou salvar dados do usuário final, como relatórios, imagens, músicas e assim por diante, seu aplicativo exige <xref:System.Security.Permissions.FileIOPermission> para ler e gravar dados no sistema de arquivos local.  
  
## <a name="remote-data"></a>Dados remotos  
 Em algum momento, seu aplicativo provavelmente terá que recuperar informações de um site remoto, como dados ou mercado de informações do cliente. Esta seção discute as técnicas mais comuns para recuperar os dados remotos.  
  
### <a name="accessing-files-by-using-http"></a>Acessando arquivos por meio de HTTP  
 Você pode acessar dados de um servidor Web usando o <xref:System.Net.WebClient> ou <xref:System.Net.HttpWebRequest> classe no <xref:System.Net> namespace. Os dados podem ser qualquer um dos arquivos estáticos ou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativos que retornam dados XML ou texto não processado. Se os dados estiverem em formato XML, a maneira mais rápida para recuperar os dados é usando o <xref:System.Xml.XmlDocument> classe cuja <xref:System.Xml.XmlDocument.Load%2A> método usa uma URL como um argumento. Para obter um exemplo, consulte [ler um documento XML no DOM](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).  
  
 Você deve considerar a segurança quando o aplicativo acessar dados remotos por HTTP. Por padrão, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] acesso do aplicativo aos recursos da rede pode ser restrito, dependendo de como seu aplicativo foi implantado. Essas restrições são aplicadas para impedir que programas mal-intencionados obtenham acesso a dados remotos com privilégios ou usando um computador do usuário para atacar outros computadores na rede.  
  
 A tabela a seguir lista as estratégias de implantação, que você pode usar e suas permissões de Web padrão.  
  
|Tipo de implantação|Permissões de rede padrão|  
|---------------------|---------------------------------|  
|Instalação do Web|Só pode acessar o servidor Web do qual o aplicativo foi instalado|  
|Instalação de compartilhamento de arquivo|Não é possível acessar todos os servidores da Web|  
|Instalação do CD-ROM|Pode acessar todos os servidores da Web|  
  
 Se seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo não pode acessar um servidor da Web devido a restrições de segurança, o aplicativo deve declarar <xref:System.Net.WebPermission> para esse site. Para obter mais informações sobre como aumentar permissões de segurança para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, consulte [proteger os aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
### <a name="accessing-data-through-an-xml-web-service"></a>Acessando dados através de um serviço Web XML  
 Se você expuser seus dados como um serviço Web XML, você pode acessar os dados usando um proxy de serviço da Web em XML. O proxy é uma [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] classe que você cria usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. As operações do serviço Web XML — como recuperar clientes, pedidos de inserção e assim por diante — são expostos como métodos no proxy. Isso torna muito mais fácil de usar do que o texto não processado ou arquivos XML Web services.  
  
 Se o serviço Web XML opera em HTTP, o serviço será vinculado pelas mesmas restrições de segurança que o <xref:System.Net.WebClient> e <xref:System.Net.HttpWebRequest> classes.  
  
### <a name="accessing-a-database-directly"></a>Acessando um banco de dados diretamente  
 Você pode usar as classes no <xref:System.Data> namespace para estabelecer conexões diretas com um servidor de banco de dados, como o SQL Server em sua rede, mas você deve considerar as questões de segurança. Ao contrário das solicitações HTTP, solicitações de conexão de banco de dados sempre são proibidas por padrão em confiança parcial; Você somente terá essa permissão por padrão se você instalar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo de um CD-ROM. Isso permite que seu aplicativo de confiança total. Para habilitar o acesso a um banco de dados do SQL Server, seu aplicativo deve solicitar <xref:System.Data.SqlClient.SqlClientPermission> -; o para habilitar o acesso a um banco de dados diferente do SQL Server, ele deve solicitar <xref:System.Data.OleDb.OleDbPermission>.  
  
 Na maioria das vezes, não será necessário que acessar o banco de dados diretamente, mas será acessá-lo em vez disso, por meio de um aplicativo de servidor Web escrito em [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou um serviço Web XML. Acessar o banco de dados dessa maneira é frequentemente o melhor método se suas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será implantado em um servidor Web. Você pode acessar o servidor em confiança parcial sem elevar as permissões do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Como incluir um arquivo de dados em um aplicativo ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)