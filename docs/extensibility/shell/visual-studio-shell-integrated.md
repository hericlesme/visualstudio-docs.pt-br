---
title: Visual Studio Shell (integrado) | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f2159e0be2f54929e28a45215588515a522b542e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrado)
Shell do Visual Studio integrado inclui o ambiente de desenvolvimento integrado (IDE), o depurador e a integração de controle de origem. Não há linguagem de programação é incluída. No entanto, o shell integrado fornecem uma estrutura que permite que você adicione linguagens de programação.  
  
 Shell do Visual Studio integrado é na verdade uma combinação de shell do Visual Studio isolada mais de uma instalação adicional que incluem componentes específicos de shell integrado.  O aplicativo de shell integrado deve incluir os dois o shell isolado pacote redistribuível do [pacote redistribuível do Microsoft Visual Studio Shell (isolado)](http://go.microsoft.com/fwlink/?LinkId=616022) , bem como o pacote redistribuível do shell integrado de [(integrado) pacote redistribuível do Microsoft Visual Studio Shell](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Antes de poder acessar os pacotes redistribuíveis do shell isolado e integrado, você será solicitado para preencher uma pesquisa de clientes breve.  Depois de preencher a pesquisa, você será direcionado para uma página de conexão do Visual Studio com links de download do pacote redistribuível.  Você pode encontrar os links de download em visitas subsequentes para o site no Visual Studio se conectar a **programas &#124; VISUAL STUDIO 2015 integrado e SHELL ISOLADO** guia.  
  
 Se você instalar o aplicativo de shell integrado no mesmo computador como uma versão completa do Visual Studio, os componentes do aplicativo serão integrados diretamente no Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Recursos do Shell integrado  
  
|||  
|-|-|  
|Área de recursos|Recurso|  
|Suporte ao idioma|-Nenhum|  
|IDE|<ul><li>Configurações<br /><br /> <ul><li>Criar configurações</li><li>Importar e exportar configurações</li><li>Redefinir as configurações</li></ul></li><li>**Caixa de ferramentas** integração</li><li>**Lista de tarefas** integração</li><li>Integração da Ajuda</li><li>**Opções de** caixa de diálogo</li><li>Gerenciamento de fontes e cores</li><li>**Saída** janela</li><li>**Comando** janela</li><li>Gerenciamento de janela</li><li>Comandos, menus e associações de chave</li><li>Tempo de execução de linguagem específica de domínio (DSL)</li></ul>|  
|Sistema de projeto e tipos de projeto|-Soluções e pastas de solução<br />-Gerenciador de configuração<br />-Gerenciamento item<br />-Projeto único e vários projetos de soluções<br />-Application Designer (Propriedades do projeto simplificado)<br />-Adicionar referência da Web<br />-Adicionar referência de serviço<br />-Único-projeto<br />-Tipos de projeto de site da Web<br />-Projetos de aplicativo web|  
|Build|-Etapas de compilação personalizada no IDE<br />-Pré-compilação para proteção de propriedade intelectual (IP)<br />-Assinatura de código<br />     MSBuild|  
|Editor|-Código de navegação de ferramentas (localização unificada, definição de fonte, herança)<br />-Código de navegação<br />-IntelliSense<br />-SmartTags<br />-Refatoração<br />-Listagem bonita<br />-Filtragem IntelliSense<br />-   **Definição de código** janela|  
|Designer|-Windows Presentation Foundation Designer<br />-Windows Forms Designer<br />-Web Designer e do Editor de HTML|  
|Dados|-   **Gerenciador de servidores** (simplificado: somente os dados). Veja a Observação 1.<br />-   **Fontes de dados** janela<br />-Todo o conjunto de controles de dados<br />-Editor de XML<br />-Data associar a fonte de dados local (. MDF ou. MDB)<br />-Data associar ao objeto<br />-Data associar ao serviço Web<br />-Dados de ligação ao servidor de banco de dados local<br />-Dados de ligação ao servidor de banco de dados remoto<br />-DDL das ferramentas de dados remotos<br />-   **Gerenciador de servidores** extensibilidade ([!INCLUDE[vsipsdk](../includes/vsipsdk_md.md)] exemplos)|  
|Depurador|-Depuração local. Consulte a Observação 2.<br />-Depuração gerenciada<br />-Depuração local<br />-Anexar ao processo de local<br />-Anexar ao processo remoto<br />-Delegado anônimo<br />-Domínios de aplicativo<br />-Depuração ASPX<br />-Atributos<br />-Break durante a avaliação de função<br />-Os pontos de interrupção<br />-Restrições de ponto de interrupção<br />-Pilha de chamadas<br />-   **Comando** janela<br />-Entre threads de depuração<br />-Dicas de dados<br />-Visualizador de dados<br />-Suporte de debugger para assistentes de depuração gerenciados (MDAs)<br />-Suporte do encaminhador de tipo depurador<br />-Suporte a DTEEvents OTB<br />-JMC seletor<br />-Teste de AppID debugger (DBGCLR)<br />-Perfil debugger<br />-Depurador ferramentas e opções<br />-Iterador de depuração<br />-A avaliação da expressão tempo de design<br />-C# o avaliador de expressão<br />-Desmontagem<br />-Editar e continuar<br />-Windows do avaliador de expressão (inspeção, locais, Autos)<br />-Auxiliar de exceção<br />-Exceções<br />-Execução<br />- Genéricos<br />-Obtendo origem à direita<br />-Depuração/Cluster HPC<br />-Integrado a depuração de vários idiomas.<br />-Depuração interOp<br />-Depuração just-in-time<br />-Depuração local<br />-Depuração gerenciada<br />-Controle manual (janela de processos)<br />-Memória<br />-Suporte de minidespejo<br />-Módulos<br />-Vários processos de depuração<br />-Depuração nativa<br />-Novo suporte de mecanismo de depuração<br />-Depuração de código otimizado<br />-Filtragem do windows saída<br />-Processo de hospedagem para depuração gerenciada<br />-Processos<br />-Quickwatch<br />-Registra<br />-Registra na pilha<br />-Depuração remota<br />-Valores de retorno<br />-Depuração de scripts<br />-Suporte do serviço fonte<br />-Segurança<br />--Lado a lado<br />-SQL<br />-Servidor de símbolos<br />-Pontos de rastreamento<br />-Thread<br />-Visualizações<br />-Depurador de transformações de linguagem de folha de estilos (XSLT) extensível|  
|Suporte de 64 bits|-a depuração de 64 bits para código gerenciado e nativo, todos os idiomas<br />-suporte a x64 nativo|  
|Controle do código fonte (SCC)|-Integração do SCC básica. Consulte a Observação 3.<br />-Ferramentas e opções de verificação|  
|Extensibilidade|-Consumir componentes VSPackages e MEF|  
  
## <a name="notes"></a>Observações  
  
#### <a name="1-data-tools"></a>1. Ferramentas de Dados  
 O shell integrado inclui ferramentas de desenvolvimento de banco de dados como o simplificado e suporte de extensibilidade de dados **Gerenciador de soluções**. No entanto, Crystal Reports, relatórios SQL e SQL Server Express não serão incluído no shell integrado.  
  
#### <a name="2-debugging-support"></a>2. Depuração de suporte  
 O shell integrado inclui o mecanismo de depuração mesmo que está incluído na versão da comunidade do Visual Studio. O mecanismo de depuração inclui o depurador comuns para código gerenciado e recursos relacionados, como a execução, anexar, defina o ponto de interrupção, editar e continuar e outros. No entanto, o mecanismo de depuração não oferece suporte a depuração de banco de dados do servidor SQL.  
  
 Embora o suporte para depuração nativa está incluído no pacote do depurador básico, você não pode estendê-lo para dar suporte a idiomas adicionais.  
  
#### <a name="3-source-code-control-integration"></a>3. Integração de controle do código fonte  
 O shell integrado fornece APIs para implementar o controle do código-fonte (SCC) e para fornecer o controle de origem com base em MSSCCI comum componentes de integração.  
  
 Embora a integração do SCC não é um recurso regular da edição do Visual Studio Pro, integração de SCC é fornecida no shell integrado.  
  
#### <a name="4-build-support"></a>4. Suporte à compilação  
 O shell integrado fornece suporte de compilação. Você pode encontrar informações sobre as compilações no [referência MSBuild](../../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Recursos não incluídos no Shell integrado  
 A seguir está uma lista dos recursos que não estão incluídos no shell integrado:  
  
-   Designer de Classe  
  
-   [Proteção preemptiva - Dotfuscator](../../ide/dotfuscator/index.md)  
  
-   Funcionalidades da linguagem  
  
-   VSHost  
  
-   Nenhum idiomas do Visual Studio ou seus modelos de projeto associado ou modelos de item de projeto, estão incluídos no shell integrado. Nenhum implementações específicas do idioma de outros recursos são incluídas, de trechos de código do Visual Basic de exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [SDK do Visual Studio](../visual-studio-sdk.md)