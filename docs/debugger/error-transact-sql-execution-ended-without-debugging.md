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
ms.openlocfilehash: 5e6ae81608ee476e3748fde6830dfaa11c119f7a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283126"
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
 [Configuração de depuração de SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))   
 [Como: definir permissões do SQL Server para depuração](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Depuração remota](../debugger/remote-debugging.md)