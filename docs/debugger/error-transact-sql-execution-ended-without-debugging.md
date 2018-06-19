---
title: 'Erro: Execução de Transact-SQL terminou sem depuração | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3ccb86621295bb102738e5154f30bd45c6db358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474005"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erro: execução de Transact-SQL encerrada sem depuração
Esse erro ocorre quando você está tentando depurar um procedimento do Transact-SQL ou SQLCLR e o depurador não recebe mensagens de depuração do SQL Server.  
  
 Isso pode ocorrer devido a problemas de rede ou problemas no SQL Server, mas a causa mais provável é um problema de permissões.  
  
 Há duas contas envolvidas:  
  
-   A conta de aplicativo é a conta de usuário como o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está sendo executado.  
  
-   A conta de conexão é a identidade usada para fazer a conexão com o SQL Server. Isso não é necessariamente o mesmo que a identidade que o Visual Studio está executando como se a conexão estivesse usando a autenticação do SQL.  
  
 A depuração de SQL exige que a conta do aplicativo deva corresponder à conta de conexão ou ser sysadmin.  
  
 Se você estiver usando um logon do SQL como sa, a conta de aplicativo deverá ser configurada no SQL Server como um sysadmin. Por padrão, os administradores no computador em que o SQL está sendo executado são sysadmins do SQL Server.  
  
 Para corrigir esse erro, talvez seja necessário:  
  
-   Verificar suas configurações de permissões. Para obter mais informações, consulte [como: definir permissões do SQL Server para depuração](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Verifique se a depuração do SQL está configurada corretamente.  
  
-   Consulte o administrador de rede ou banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Configuração de depuração de SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Como: definir as permissões do SQL Server para depuração](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Depuração remota](../debugger/remote-debugging.md)