---
title: 'Como: habilitar e desabilitar editar e continuar (c#, VB, C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 9070913d1106eb5e2ca04160ad95c6a6fd46f752
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480447"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Como: habilitar e desabilitar editar e continuar (c#, VB, C++)
Você pode desabilitar ou habilitar editar e continuar no **opções** caixa de diálogo em tempo de design. Não é possível alterar essa configuração enquanto você está depurando.  
  
Editar e Continuar só funciona em compilações de depuração. Para o C++ nativo, Editar e Continuar exige o uso da opção /INCREMENTAL. Para obter mais informações sobre os requisitos de recurso em C++, consulte [postagem de blog](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) e [editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
#### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar/desabilitar a função Editar e Continuar  
  
1.  Se você estiver em uma sessão de depuração, pare a depuração (**Shift + F5**).

2.  Abrir página de opções de depuração (**Ferramentas > Opções > depuração**).
  
3.  Selecione **geral**e role para baixo até **editar e continuar** categoria (painel direito).  
  
4.  Para habilitar, selecione o **habilitar editar e continuar** caixa de seleção. Para desabilitar, desmarque a caixa de seleção.  
  
    > [!NOTE]
    >  Se IntelliTrace estiver habilitado e você coletar eventos de IntelliTrace e informações de chamada, Editar e Continuar estará desabilitado. Para obter mais informações, consulte [IntelliTrace](../debugger/intellitrace.md).

5. (C++) Para habilitar, selecione **habilitar nativo editar e continuar**. Para desabilitar, desmarque a caixa de seleção.

6. (C++) Defina opções adicionais para código nativo.

    - **Aplicar alterações ao continuar (somente nativo)**  
        Automaticamente, o Visual Studio compila e aplica as alterações de código pendentes feitas ao continuar o processo de um estado de interrupção. Se não estiver selecionada, você pode optar por aplicar as alterações usando o item "Aplicar alterações de código" no menu Depurar.  
  
    - **Avisar sobre código obsoleto (somente nativo)**  
        Obter avisos sobre código obsoleto. 
  
7.  Clique em **OK**.    
  
## <a name="see-also"></a>Consulte também  
 [Editar e continuar](../debugger/edit-and-continue.md)