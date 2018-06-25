---
title: Solução de problemas de instalação com o Visual Studio 2017
description: Às vezes, as coisas podem dar errado. Se a instalação ou atualização do Visual Studio falhar, esta página poderá ajudar.
ms.date: 11/21/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99547ff029e8bde94118918b8b0c538e3f7fad7d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766032"
---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Solução de problemas de instalação e atualização do Visual Studio 2017

## <a name="symptoms"></a>Sintomas

Quando você tentar instalar ou atualizar o Visual Studio 2017, a operação falhará.

## <a name="workaround"></a>Solução alternativa

Para encontrar uma solução alternativa para esse problema, siga estas etapas.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Etapa 1: verificar se esse é um problema conhecido

Existem alguns problemas conhecidos com o instalador do Visual Studio que a Microsoft está trabalhando para corrigir. Para saber se há uma solução para o problema, consulte [a seção Problemas Conhecidos das nossas notas de versão](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#known-issues).

### <a name="step-2---check-with-the-developer-community"></a>Etapa 2: conferir com a comunidade de desenvolvedores

Pesquise em sua mensagem de erro com a [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Outros membros da comunidade podem ter documentado uma solução para o seu problema.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Etapa 3 - excluir o diretório de instalação do Visual Studio para corrigir problemas de atualização

O bootstrapper de instalação do Visual Studio é um executável leve mínimo que instala o restante do instalador do Visual Studio. A exclusão de arquivos de instalação do Visual Studio e a nova execução do bootstrapper podem resolver algumas falhas de atualização.

>[!NOTE]
Executar as seguintes ações reinstalará os arquivos do Instalador do Visual Studio e redefinirá os metadados de instalação.

1. Fechar o instalador do Visual Studio.
2. Exclua o diretório de instalação do Visual Studio. Normalmente, o diretório é `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Execute o bootstrapper de instalação do Visual Studio. Você pode encontrar o bootstrapper na pasta Downloads com um nome de arquivo que segue um padrão `vs_[Visual Studio edition]__*.exe`. Se não encontrar esse aplicativo, você poderá baixar o bootstrapper indo para a página [Downloads do Visual Studio](https://www.visualstudio.com/downloads/) e clicando em **Baixar** para sua edição do Visual Studio. Execute o arquivo executável para redefinir os metadados de instalação.
4. Tente instalar ou atualizar o Visual Studio. Se o Instalador continuar a falhar, vá para a próxima etapa.

### <a name="step-4---report-a-problem"></a>Etapa 4 - relatar um problema

Em algumas situações, como aquelas relacionadas a arquivos corrompidos, os problemas talvez precisem ser resolvidos caso a caso:

1. Colete os logs de configuração. Para saber mais detalhes, consulte [Como obter os logs de instalação do Visual Studio](#how-to-get-the-visual-studio-installation-logs).
2. Abra o instalador do Visual Studio e clique em **Relatar um problema** para abrir a ferramenta de comentários do Visual Studio.
![Você pode pressionar Tab até acessar o botão Fornecer Comentários para abrir a ferramenta de comentários](media/report-a-problem.png)
3. Dê um título ao relatório de problemas e forneça detalhes relevantes. Clique em **Avançar** para ir até a seção **Anexos** e anexar o arquivo de log gerado (normalmente, o arquivo está em `%TEMP%\vslogs.zip`).
4. Clique em **Avançar** para examinar o relatório de problemas e clique em **Enviar**.

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Etapa 5 – Executar InstallCleanup.exe para remover os arquivos de instalação

Como último recurso, você pode [remover o Visual Studio](remove-visual-studio.md) para remover todos os arquivos de instalação e informações do produto.

1. Siga as instruções em [Remover o Visual Studio](remove-visual-studio.md).
2. Execute novamente o bootstrapper descrito na [Etapa 3 - excluir o diretório do Instalador do Visual Studio para corrigir problemas de atualização](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Tente instalar ou atualizar o Visual Studio.

### <a name="step-6---contact-us-optional"></a>Etapa 6 – Entrar em contato conosco (opcional)

Se nenhuma das outras etapas possibilitarem uma instalação bem-sucedida, é possível entrar em contato conosco por meio de um chat ao vivo e obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

## <a name="how-to-troubleshoot-an-offline-installer"></a>Como solucionar problemas de um instalador offline

Aqui está uma tabela de problemas conhecidos e algumas soluções alternativas durante a instalação em um layout local que pode ajudar.

| Problema       | Item                   | Solução |
| ----------- | ---------------------- | -------- |
| Os usuários não têm acesso aos arquivos. | permissões (ACLs) | Lembre-se de ajustar as permissões (ACLs) para que elas concedam acesso de Leitura aos outros usuários *antes* de você compartilhar a instalação offline. |
| Falha na instalação de novas cargas de trabalho, novos componentes ou idiomas.  | `--layout`  | Verifique se você tem acesso à Internet se estiver instalando com base em um layout parcial e selecione as cargas de trabalho, os componentes ou idiomas que não foram baixado anteriormente nesse layout parcial. |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>Como obter os logs de instalação do Visual Studio

Os logs de instalação são necessários para solucionar a maioria dos problemas de instalação. Quando você enviar um problema usando [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) no Instalador do Visual Studio, esses logs serão incluídos automaticamente no relatório.

Caso contate o Suporte da Microsoft, talvez você precise fornecer esses logs de configuração usando a [Ferramenta de Coleta de Log do .NET Framework e o Microsoft Visual Studio](https://aka.ms/vscollect). A ferramenta de coleta de log coleta os logs de configuração de todos os componentes instalados pelo Visual Studio 2017, incluindo .NET Framework, SDK do Windows e SQL Server. Ela também coleta informações do computador, um inventário do Windows Installer e as informações de log de eventos do Instalador do Visual Studio, Windows Installer e Restauração do Sistema.

Para coletar os logs:

1. [Baixe a ferramenta](https://aka.ms/vscollect).
2. Abra um prompt de comando administrativo.
3. Execute `Collect.exe` no diretório em que você salvou a ferramenta.
4. Localize o arquivo `vslogs.zip` resultante no diretório `%TEMP%`, por exemplo, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> A ferramenta deve ser executada na mesma conta de usuário em que a instalação com falha foi executada. Se estiver executando a ferramenta em uma conta de usuário diferente, defina a opção `–user:<name>` para especificar a conta de usuário na qual a instalação com falha foi executada. Execute `Collect.exe -?` em um prompt de comando do administrador para obter informações adicionais de uso e opções.

## <a name="more-support-options"></a>Mais opções de suporte

Se nenhuma das outras etapas possibilitarem uma instalação bem-sucedida, é possível entrar em contato conosco por meio de um chat ao vivo e obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções:

* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Você pode acompanhar os problemas do produto e encontrar respostas na [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) (Comunidade de desenvolvedores do Visual Studio).
* Também é possível interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio). (Isso requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também

* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Ferramentas para detectar e gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Instalar o Visual Studio por trás de um firewall ou servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Remover o Visual Studio 2017](remove-visual-studio.md)
