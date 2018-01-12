---
title: "Como o salvamento automático afeta soluções do Office | Microsoft Docs"
ms.custom: 
ms.date: 07/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: autosave
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ced97cb56e099eec70ea2b87c7d1a31ee7d4d89d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-autosave-impacts-office-solutions"></a>Como o salvamento automático afeta soluções do Office

Salvamento automático é um recurso do Excel, PowerPoint e Word que, quando ativados, permite que edições do usuário a ser salvo automaticamente e continuamente. Se o salvamento automático está desativado, em seguida, salvar deve ser disparado manualmente para que as alterações do usuário sejam persistentes. Com a adição desse recurso, talvez seja necessário fazer ajustes para sua solução do Office para garantir que ele funciona perfeitamente até mesmo durante o salvamento automático está em. Para obter detalhes, consulte [como ele afeta macros e suplementos](https://msdn.microsoft.com/vba/office-shared-vba/articles/how-autosave-impacts-addins-and-macros). Para obter mais informações sobre o salvamento automático em geral, consulte [o que é o salvamento automático?](https://support.office.com/en-US/article/What-is-AutoSave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5).

Observação: O salvamento automático para Windows Desktop Word, Excel e PowerPoint foi introduzido no 2017 e está disponível para assinantes do Office 365. Os usuários que compraram uma licença permanente para o Office 2016 ou anteriores atualmente não tem acesso ao recurso coautoria. (Excel Online, Excel para o Android, o Excel para iOS e Excel Mobile na Windows Store também dar suporte a salvamento automático). 

## <a name="see-also"></a>Consulte também
[Desenvolvendo soluções do Office](./developing-office-solutions.md)
