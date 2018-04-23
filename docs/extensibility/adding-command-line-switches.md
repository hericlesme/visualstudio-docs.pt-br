---
title: Adicionar opções de linha de comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: daef07d0b8dd02f6823717b0c0cb5d68d837ccde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="adding-command-line-switches"></a>Adicionar opções de linha de comando
Você pode adicionar opções de linha de comando que se aplicam ao seu VSPackage quando devenv.exe é executado. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar o nome do comutador e suas propriedades. Neste exemplo, a opção de MySwitch é adicionada para uma subclasse de VSPackage denominado **AddCommandSwitchPackage** sem argumentos e com o VSPackage carregados automaticamente.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Os parâmetros nomeados são mostrados na tabela a seguir  
  
 Arguments  
 O número de argumentos para o comutador. Pode ser "*", ou uma lista de argumentos.  
  
 DemandLoad  
 Carrega automaticamente o VSPackage se isso for definido como 1, caso contrário, defina como 0.  
  
 HelpString  
 A cadeia de caracteres ou o recurso de ID de Ajuda da cadeia de caracteres para exibir com **devenv /?**.  
  
 Nome  
 O comutador.  
  
 PackageGuid  
 O GUID do pacote.  
  
 O primeiro valor dos argumentos geralmente é 0 ou 1. Um valor especial de ' *' pode ser usado para indicar que o resto inteiro da linha de comando é o argumento. Isso pode ser útil para cenários em que um usuário deve passar em uma cadeia de caracteres de comando do depurador de depuração.  
  
 O valor de DemandLoad é `true` (1) ou `false` (0) indica que o VSPackage deve ser carregado automaticamente.  
  
 O valor de HelpString é a ID de recurso da cadeia de caracteres que aparece no devenv /? Exibição da Ajuda. Esse valor deve estar no formato "#nnn" em que nnn é um número inteiro. O valor de cadeia de caracteres no arquivo de recurso deve terminar com um caractere de nova linha.  
  
 O valor do nome é o nome do comutador.  
  
 O valor de PackageGuid é o GUID do pacote que implementa essa opção. O IDE usa esse GUID para localizar o VSPackage no registro para o qual se aplica a opção de linha de comando.  
  
## <a name="retrieving-command-line-switches"></a>Recuperando opções de linha de comando  
 Quando o pacote é carregado, você pode recuperar as opções de linha de comando, executando as etapas a seguir.  
  
1.  No seu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementação, chamada `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obter o <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interface.  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> para recuperar as opções de linha de comando que o usuário inseriu.  
  
 O código a seguir mostra como descobrir se a opção de linha de comando MySwitch foi inserida pelo usuário:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 É sua responsabilidade para verificar as opções de linha de comando cada vez que o pacote é carregado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Opções de linha de comando devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilitário de CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. Arquivos de Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)