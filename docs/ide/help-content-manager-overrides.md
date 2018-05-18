---
title: Substituições do Gerenciador de Conteúdo da Ajuda
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8baf096a0ead512cddf9f33801c4504c2a5a4502
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="help-content-manager-overrides"></a>Substituições do Gerenciador de Conteúdo da Ajuda

Você pode alterar o comportamento padrão do Help Viewer e dos recursos relacionados à Ajuda na IDE do Visual Studio. Algumas opções são especificadas com a criação de um arquivo [.pkgdef](https://blogs.msdn.microsoft.com/visualstudio/2009/12/18/whats-a-pkgdef-and-why/) para definir vários valores de chave do Registro. Outras são definidas diretamente no registro.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Como controlar o comportamento do Help Viewer usando um arquivo .pkgdef

1. Crie um arquivo *.pkgdef* com a primeira linha igual a `[$RootKey$\Help]`.

2. Adicione qualquer ou todos os valores de chave do Registro descritos na tabela a seguir em linhas separadas, por exemplo `"UseOnlineHelp"=dword:00000001`.

3. Copie o arquivo para *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<edição\>\Common7\IDE\CommonExtensions*.

4. Execute `devenv /updateconfiguration` em um prompt de comando do desenvolvedor.

### <a name="registry-key-values"></a>Valores de chave do Registro

|Valor da chave do Registro|Tipo|Dados|Descrição|
|------------------|----|----|-----------|
|NewContentAndUpdateService|cadeia de caracteres|\<URL em HTTP para o ponto de extremidade de serviço\>|Define um ponto de extremidade de serviço exclusivo|
|UseOnlineHelp|DWORD|`0` para especificar a Ajuda local, `1` para especificar a Ajuda online|Definir padrão de Ajuda online ou offline|
|OnlineBaseUrl|cadeia de caracteres|\<URL em HTTP para o ponto de extremidade de serviço\>|Definir um ponto de extremidade F1 exclusivo|
|OnlineHelpPreferenceDisabled|DWORD|`0` para habilitar ou `1` para desabilitar a opção de preferência de Ajuda online|Desabilitar a opção de preferência de Ajuda online|
|DisableManageContent|DWORD|`0` para habilitar ou `1` para desabilitar a guia **Gerenciar Conteúdo** no Help Viewer|Desabilitar a guia **Gerenciar Conteúdo**|
|DisableFirstRunHelpSelection|DWORD|`0` para habilitar ou `1` para desabilitar os recursos da Ajuda que são configurados na primeira vez que o Visual Studio é iniciado|Desabilitar a instalação de conteúdo na primeira inicialização do Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Conteúdo do arquivo .pkgdef de exemplo

```
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Usar o Editor do Registro para alterar o comportamento do Help Viewer

Os dois comportamentos a seguir podem ser controlados através da definição de valores da chave do Registro no Editor do Registro.

|Tarefa|Chave do Registro|Valor|Dados|
|----------|-----|------|----|
|Substituir a prioridade do trabalho BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (em um computador de 64 bits)\Microsoft\Help\v2.3|BITSPriority|**foreground**, **high**, **normal** ou **low**|
|Aponte para o repositório de conteúdo local no compartilhamento de rede|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Consulte também

- [Guia do administrador do Help Viewer](../ide/help-viewer-administrator-guide.md)
- [Argumentos da linha de comando para o Gerenciador de Conteúdo da Ajuda](../ide/command-line-arguments-for-the-help-content-manager.md)
- [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)
- [Modificar o shell isolado usando o arquivo .pkgdef](../extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)