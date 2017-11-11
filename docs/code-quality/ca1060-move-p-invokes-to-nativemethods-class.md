---
title: 'CA1060: Move P-Invokes to NativeMethods class | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 6c876ce1a73dbc4be34202cf2e7a2b5f775d3d7d
ms.contentlocale: pt-br
ms.lasthandoff: 08/30/2017

---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Move P/Invokes to NativeMethods class
|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A method uses Platform Invocation Services to access unmanaged code and is not a member of one of the **NativeMethods** classes.  
  
## <a name="rule-description"></a>Rule Description  
 Platform Invocation methods, such as those that are marked by using the <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribute, or methods that are defined by using the `Declare` keyword in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], access unmanaged code. These methods should be in one of the following classes:  
  
-   **NativeMethods** - This class does not suppress stack walks for unmanaged code permission. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> must not be applied to this class.) This class is for methods that can be used anywhere because a stack walk will be performed.  
  
-   **SafeNativeMethods** - This class suppresses stack walks for unmanaged code permission. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> is applied to this class.) This class is for methods that are safe for anyone to call. Callers of these methods are not required to perform a full security review to make sure that the usage is secure because the methods are harmless for any caller.  
  
-   **UnsafeNativeMethods** - This class suppresses stack walks for unmanaged code permission. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> is applied to this class.) This class is for methods that are potentially dangerous. Any caller of these methods must perform a full security review to make sure that the usage is secure because no stack walk will be performed.  
  
 These classes are declared as `internal` (`Friend`, in Visual Basic) and declare a private constructor to prevent new instances from being created. The methods in these classes should be `static` and `internal` (`Shared` and `Friend` in Visual Basic).  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, move the method to the appropriate **NativeMethods** class. For most applications, moving P/Invokes to a new class that is named **NativeMethods** is enough.  
  
 However, if you are developing libraries for use in other applications, you should consider defining two other classes that are called **SafeNativeMethods** and **UnsafeNativeMethods**. These classes resemble the **NativeMethods** class; however, they are marked by using a special attribute called **SuppressUnmanagedCodeSecurityAttribute**. When this attribute is applied, the runtime does not perform a full stack walk to make sure that all callers have the **UnmanagedCode** permission. The runtime ordinarily checks for this permission at startup. Because the check is not performed, it can greatly improve performance for calls to these unmanaged methods, It also enables code that has limited permissions to call these methods.  
  
 However, you should use this attribute with great care. It can have serious security implications if it is implemented incorrectly..  
  
 For information about how to implement the methods, see the **NativeMethods** Example, **SafeNativeMethods** Example, and **UnsafeNativeMethods** Example.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example declares a method that violates this rule. To correct the violation, the **RemoveDirectory** P/Invoke should be moved to an appropriate class that is designed to hold only P/Invokes.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)] [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## <a name="nativemethods-example"></a>NativeMethods Example  
  
### <a name="description"></a>Description  
 Because the **NativeMethods** class should not be marked by using **SuppressUnmanagedCodeSecurityAttribute**, P/Invokes that are put in it will require **UnmanagedCode** permission. Because most applications run from the local computer and run together with full trust, this is usually not a problem. However, if you are developing reusable libraries, you should consider defining a **SafeNativeMethods** or **UnsafeNativeMethods** class.  
  
 The following example shows an **Interaction.Beep** method that wraps the **MessageBeep** function from user32.dll. The **MessageBeep** P/Invoke is put in the **NativeMethods** class.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)] [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## <a name="safenativemethods-example"></a>SafeNativeMethods Example  
  
### <a name="description"></a>Description  
 P/Invoke methods that can be safely exposed to any application and that do not have any side effects should be put in a class that is named **SafeNativeMethods**. You do not have to demand permissions and you do not have to pay much attention to where they are called from.  
  
 The following example shows an **Environment.TickCount** property that wraps the **GetTickCount** function from kernel32.dll.  
  
### <a name="code"></a>Code  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)] [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods Example  
  
### <a name="description"></a>Description  
 P/Invoke methods that cannot be safely called and that could cause side effects should be put in a class that is named **UnsafeNativeMethods**. These methods should be rigorously checked to make sure that they are not exposed to the user unintentionally. The rule [CA2118: Review SuppressUnmanagedCodeSecurityAttribute usage](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) can help with this. Alternatively, the methods should have another permission that is demanded instead of **UnmanagedCode** when they use them.  
  
 The following example shows a **Cursor.Hide** method that wraps the **ShowCursor** function from user32.dll.  
  
### <a name="code"></a>Code  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)] [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## <a name="see-also"></a>See Also  
 [Design Warnings](../code-quality/design-warnings.md)