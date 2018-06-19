---
title: Como desabilitar o processo de hospedagem
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7970ff97c7aec42f8798da07cf2a4a2b6c8bea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942055"
---
# <a name="how-to-disable-the-hosting-process"></a>Como desabilitar o processo de hospedagem

Chamadas para determinadas APIs podem ser afetadas quando o processo de hospedagem está habilitado. Nesses casos, é necessário desabilitar o processo de hospedagem para retornar os resultados corretos.

## <a name="to-disable-the-hosting-process"></a>Para desabilitar o processo de hospedagem

1.  Abra um projeto executável em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Projetos que não geram executáveis (por exemplo, projetos de serviço ou biblioteca de classes) não têm essa opção.

2.  No menu **Projeto**, clique em **Propriedades**.

3.  Clique na guia **Depurar**.

4.  Desmarque a caixa de seleção **Habilitar o processo de hospedagem do Visual Studio**.

 Quando o processo de hospedagem é desabilitado, vários recursos de depuração ficam não disponíveis ou apresentam um desempenho reduzido. Para obter mais informações, consulte [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md).

 De modo geral, quando o processo de hospedagem está desabilitado:

-   O tempo necessário para iniciar a depuração de aplicativos [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] aumenta.

-   A avaliação de expressões em tempo de design fica não disponível.

-   A depuração de confiança parcial ficará não disponível.

## <a name="see-also"></a>Consulte também

- [Processo de hospedagem e depuração](../debugger/debugging-and-the-hosting-process.md)
- [Processo de hospedagem (vshost.exe)](../ide/hosting-process-vshost-exe.md)