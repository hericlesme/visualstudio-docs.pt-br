---
title: Guia do administrador do Help Viewer
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bccbd4f1365ea42b3e0331283a5659502038e133
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="help-viewer-administrator-guide"></a>Guia do administrador do Help Viewer

O Visualizador da Ajuda permite que você gerencie instalações da ajuda local para ambientes de rede com ou sem acesso à internet. O conteúdo da Ajuda local é configurado por máquina. Por padrão, os usuários devem ter direitos de administrador para atualizar a instalação da Ajuda local.

Se seu ambiente de rede permite que os clientes acessem a Internet, você pode usar o executável do **Gerenciador de Conteúdo da Ajuda** para implantar conteúdo da Ajuda local através da Internet. Para obter mais informações sobre a sintaxe de linha de comando *HlpCtntMgr.exe*, consulte [Argumentos da linha de comando para o Gerenciador de Conteúdo da Ajuda](../ide/command-line-arguments-for-the-help-content-manager.md).

Para obter informações sobre como criar conteúdo, criar um ponto de extremidade de serviço de Intranet e tipos de atividades semelhantes, consulte o [SDK do Help Viewer](../extensibility/internals/microsoft-help-viewer-sdk.md).

Se você não tiver acesso à Internet em seu ambiente de rede, o Help Viewer poderá implantar conteúdo de Ajuda local através da Intranet ou de um compartilhamento de rede. Você também pode desabilitar as opções da Ajuda do IDE do Visual Studio usando [substituições de chave do Registro](../ide/help-content-manager-overrides.md) para as funcionalidades, como:

- ajuda online versus offline

- instalação de conteúdo na primeira inicialização do IDE

- especificação de um serviço de conteúdo de intranet

- gerenciamento de conteúdo

## <a name="deploy-local-help-content-from-the-internet"></a>Implantar conteúdo de Ajuda local da Internet

Você pode usar o **Gerenciador de Conteúdo da Ajuda** (*HlpCtntMgr.exe*) para implantar conteúdo de Ajuda local da Internet em computadores cliente. Use a seguinte sintaxe:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Para obter mais informações sobre a sintaxe de linha de comando *HlpCtntMgr.exe*, consulte [Argumentos da linha de comando para o Gerenciador de Conteúdo da Ajuda](../ide/command-line-arguments-for-the-help-content-manager.md).

Requisitos:

-   Os computadores cliente devem ter acesso à Internet.

-   Os usuários devem ter direitos de administrador para atualizar, adicionar, ou remover o conteúdo da ajuda local depois que foi instalado.


Restrições:

-   A fonte padrão para Ajuda ainda será online.

### <a name="example"></a>Exemplo

O exemplo a seguir instala o conteúdo do inglês para o Visual Studio para um computador cliente.

#### <a name="to-install-english-content-from-the-internet"></a>Para instalar o conteúdo em inglês da Internet

1.  Escolha **Iniciar** e **Executar**.

2.  Digite o seguinte:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  Pressione **ENTER**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Implantar conteúdo pré-instalado de Ajuda local em computadores cliente

Você pode instalar um conjunto de conteúdo online em um computador, e então copiar o conjunto de conteúdo instalado em outros computadores.

Requisitos:

-   O computador em que você instala o conjunto de conteúdo deve ter acesso à Internet.

-   Os usuários devem ter direitos de administrador para atualizar, adicionar, ou remover o conteúdo da ajuda local depois que foi instalado.

    > [!TIP]
    > Se os usuários não tiverem direitos de administrador, é recomendável que você desabilite a guia **Gerenciar Conteúdo** no Visualizador da Ajuda. Para obter mais informações, consulte [Substituições do Gerenciador de Conteúdo da Ajuda](../ide/help-content-manager-overrides.md).

Restrições:

-   A fonte padrão para Ajuda ainda será online.

### <a name="create-the-content-set"></a>Crie o conjunto de conteúdo

Antes de criar o conjunto de conteúdo básico, primeiro você deve desinstalar todo o conteúdo local do Visual Studio no computador de destino.

#### <a name="to-uninstall-local-help"></a>Para desinstalar a ajuda local

1.  No Help Viewer, escolha a guia **Gerenciar Conteúdo**.

2.  Navegue até o conjunto de documentos do Visual Studio.

3.  Escolha **Remover** ao lado de cada subitem.

4.  Escolha **Atualizar** para desinstalar.

5.  Navegue até *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* e verifique se a pasta contém somente o arquivo *catalogType.xml*.

 Depois que remover todo conteúdo da Ajuda do Visual Studio local, você estará pronto para fazer download da ajuda do Visual Studio local, você está pronto para baixar o conjunto de conteúdo básico.

#### <a name="to-download-the-content"></a>Para baixar o conteúdo

1.  No Help Viewer, escolha a guia **Gerenciar Conteúdo**.

2.  Em **Documentação Recomendada** ou **Documentação Disponível**, navegue até os conjuntos de documentação que você deseja baixar e, em seguida, escolha **Adicionar**.

3.  Escolha **Atualizar**.


Em seguida, você precisará empacotar o conteúdo para que ele seja implantado em computadores clientes.

#### <a name="to-package-the-content"></a>Para criar um pacote com o conteúdo

1.  Crie uma pasta para copiar o conteúdo para uma implantação posterior. Por exemplo: *C:\VSHelp*.

2.  Abra *cmd.exe* com permissões de Administrador.

3.  Navegue até a pasta que você criou na etapa 1.

4.  Digite o seguinte:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o `

     Por exemplo: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Implantar o conteúdo

1.  Crie um compartilhamento de rede e copie o conteúdo da ajuda nesse local.

     Por exemplo, copie o conteúdo em *C:\VSHelp* para *\\\myserver\VSHelp*.

2.  Crie um arquivo *.bat* para conter o script de implantação do conteúdo da ajuda. Como o cliente provavelmente tenha um bloqueio de leitura em alguns dos arquivos que estão sendo excluídos como parte do envio, você deve encerrar cliente antes de enviar atualizações. Por exemplo:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3.  Execute o arquivo *.bat* nos computadores locais em que você deseja instalar o conteúdo da Ajuda.

## <a name="see-also"></a>Consulte também

- [Argumentos da linha de comando para o Gerenciador de Conteúdo da Ajuda](../ide/command-line-arguments-for-the-help-content-manager.md)
- [Substituições do Gerenciador de Conteúdo da Ajuda](../ide/help-content-manager-overrides.md)
- [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)
- [SDK do Help Viewer](../extensibility/internals/microsoft-help-viewer-sdk.md)