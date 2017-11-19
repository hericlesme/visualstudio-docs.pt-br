---
title: Data em que o objeto (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Objeto Date (JavaScript)
Habilita o armazenamento básico e a recuperação de datas e horas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Obrigatório. O nome da variável à qual o objeto `Date` é atribuído.  
  
 `dateVal`  
 Necessário. Se um valor numérico, `dateVal` representa o número de milissegundos em tempo Universal Coordenado entre a data especificada e a meia-noite de 1º de janeiro de 1970. Se uma cadeia de caracteres, `dateVal` é analisados de acordo com as regras na [Date and Time Strings](../../javascript/date-and-time-strings-javascript.md). O `dateVal` argumento também pode ser um valor VT_DATE como retornado pelo alguns objetos ActiveX.  
  
 `year`  
 Necessário. O ano inteiro, por exemplo, 1976 (e não 76).  
  
 `month`  
 Necessário. O mês como um número inteiro entre 0 e 11 (janeiro a dezembro).  
  
 `date`  
 Necessário. A data como um número inteiro entre 1 e 31.  
  
 `hours`  
 Opcional. Deve ser fornecido se `minutes` for fornecido. Um inteiro de 0 a 23 (meia-noite de 11 pm) que especifica a hora.  
  
 minutos  
 Opcional. Deve ser fornecido se `seconds` for fornecido. Um inteiro de 0 a 59, que especifica os minutos.  
  
 `seconds`  
 Opcional. Deve ser fornecido se `milliseconds` for fornecido. Um inteiro de 0 a 59, que especifica os segundos.  
  
 `ms`  
 Opcional. Um inteiro de 0 a 999 que especifica os milissegundos.  
  
## <a name="remarks"></a>Comentários  
 Um `Date` objeto contém um número que representa um momento específico no tempo para dentro de um milissegundo. Se o valor de um argumento é maior do que o intervalo ou é um número negativo, outros valores armazenados forem modificados de acordo. Por exemplo, se você especificar segundos de 150, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] redefine o número dois minutos e 30 segundos.  
  
 Se o número for `NaN`, o objeto não representa um instante específico. Se você passar sem parâmetros para o `Date` do objeto, ele é inicializado para a hora atual (UTC). Um valor deve ser fornecido ao objeto antes de você pode usá-lo.  
  
 O intervalo de datas que pode ser representado em um `Date` objeto é de aproximadamente 285,616 anos em ambos os lados de 1º de janeiro de 1970.  
  
 Consulte [Calculando datas e horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) para obter mais informações sobre como usar o `Date` objeto e métodos relacionados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do objeto `Date`.  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>Requisitos  
 O `Date object` foi introduzido no [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Alguns membros nas listas a seguir foram introduzidos em versões posteriores. Para obter mais informações, consulte [informações de versão](../../javascript/reference/javascript-version-information.md) ou a documentação para os membros individuais.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista propriedades de `Date Object`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade Constructor](../../javascript/reference/constructor-property-date.md)|Especifica a função que cria um objeto.|  
|[Propriedade prototype](../../javascript/reference/prototype-property-date.md)|Retorna uma referência ao protótipo para uma classe de objetos.|  
  
## <a name="functions"></a>Funções  
 A tabela a seguir lista funções de `Date Object`.  
  
|Funções|Descrição|  
|---------------|-----------------|  
|[Função Date.now](../../javascript/reference/date-now-function-javascript.md)|Retorna o número de milissegundos entre 1º de janeiro de 1970 e a data e hora atuais.|  
|[Função Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Analisa uma cadeia de caracteres que contém uma data e retorna o número de milissegundos entre essa data e a meia-noite de 1º de janeiro de 1970.|  
|[Função Date.UTC](../../javascript/reference/date-utc-function-javascript.md)|Retorna o número de milissegundos entre meia-noite de 1º de janeiro de 1970 Horário Coordenado Universal (UTC) (ou GMT) e a data fornecida.|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>Métodos  
 A tabela a seguir lista métodos de `Date Object`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método getDate](../../javascript/reference/getdate-method-date-javascript.md)|Retorna o valor de dia do mês usando o horário local.|  
|[Método getDay](../../javascript/reference/getday-method-date-javascript.md)|Retorna o valor de dia da semana usando o horário local.|  
|[Método getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Retorna o valor de ano usando o horário local.|  
|[Método getHours](../../javascript/reference/gethours-method-date-javascript.md)|Retorna o valor de horas usando o horário local.|  
|[Método getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Retorna o valor de milissegundos usando o horário local.|  
|[Método getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Retorna o valor de minutos usando o horário local.|  
|[Método getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Retorna o valor de mês usando o horário local.|  
|[Método getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Retorna um valor segundos usando o horário local.|  
|[Método getTime](../../javascript/reference/gettime-method-date-javascript.md)|Retorna o valor de tempo em uma `Date` objeto como o número de milissegundos desde a meia-noite de 1º de janeiro de 1970.|  
|[Método getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Retorna a diferença de minutos entre a hora no computador host e o Horário Coordenado Universal (UTC).|  
|[Método getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Retorna o valor de dia do mês usando o UTC.|  
|[Método getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Retorna o valor de dia da semana usando o UTC.|  
|[Método getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Retorna o valor de ano usando o UTC.|  
|[Método getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Retorna o valor de horas usando o UTC.|  
|[Método getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Retorna o valor de milissegundos usando o UTC.|  
|[Método getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Retorna o valor de minutos usando o UTC.|  
|[Método getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Retorna o valor de mês usando o UTC.|  
|[Método getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Retorna os segundos de valor usando o UTC.|  
|[Método getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Retorna o valor VT_DATE em uma `Date` objeto.|  
|[Método getYear](../../javascript/reference/getyear-method-date-javascript.md)|Retorna o valor de ano.|  
|[Método hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto tem uma propriedade com o nome especificado.|  
|[Método isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retorna um valor booliano que indica se um objeto existe na cadeia de protótipo de outro objeto.|  
|[Método propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retorna um valor booliano que indica se uma propriedade especificada faz parte de um objeto e se ela é enumerável.|  
|[Método setDate](../../javascript/reference/setdate-method-date-javascript.md)|Define o dia numérico do mês usando o horário local.|  
|[Método setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)|Define o valor de ano usando o horário local.|  
|[Método setHours](../../javascript/reference/sethours-method-date-javascript.md)|Define o valor de horas usando o horário local.|  
|[Método setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Define o valor de milissegundos usando o horário local.|  
|[Método setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Define o valor de minutos usando o horário local.|  
|[Método setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Define o valor de mês usando o horário local.|  
|[Método setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Define os segundos valor usando o horário local.|  
|[Método setTime](../../javascript/reference/settime-method-date-javascript.md)|Define o valor de data e hora no `Date` objeto.|  
|[Método setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Define o dia numérico do mês usando o UTC.|  
|[Método setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Define o valor de ano usando o UTC.|  
|[Método setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Define o valor de horas usando o UTC.|  
|[Método setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Define o valor de milissegundos usando o UTC.|  
|[Método setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Define o valor de minutos usando o UTC.|  
|[Método setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Define o valor de mês usando o UTC.|  
|[Método setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Define os segundos valor usando o UTC.|  
|[Método setYear](../../javascript/reference/setyear-method-date-javascript.md)|Define o valor de ano usando o horário local.|  
|[Método toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Retorna uma data como um valor de cadeia de caracteres.|  
|[Método toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Retorna uma data convertida em uma cadeia de caracteres usando a hora de Greenwich (GMT).|  
|[Método toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|Retorna uma data como um valor de cadeia de caracteres no formato ISO.|  
|[Método toJSON](../../javascript/reference/tojson-method-date-javascript.md)|Usado para transformar dados de um tipo de objeto antes da serialização JSON.|  
|[Método toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Retorna uma data como um valor de cadeia de caracteres apropriada para a localidade atual do ambiente de host.|  
|[Método toLocaleString](../../javascript/reference/tolocalestring-date.md)|Retorna um objeto convertido em uma cadeia de caracteres usando a localidade atual.|  
|[Método toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Retorna a hora como um valor de cadeia de caracteres apropriada para a localidade atual do ambiente de host.|  
|[Método toString](../../javascript/reference/tostring-method-date.md)|Retorna uma representação em cadeia de caracteres de um objeto.|  
|[Método toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Retorna a hora como um valor de cadeia de caracteres.|  
|[Método toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Retorna uma data convertida em uma cadeia de caracteres usando o UTC.|  
|[Método valueOf](../../javascript/reference/valueof-method-date.md)|Retorna o valor primitivo do objeto especificado.|  
  
## <a name="see-also"></a>Consulte também  
 [Calculando datas e horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Cadeias de caracteres de data e hora](../../javascript/date-and-time-strings-javascript.md)