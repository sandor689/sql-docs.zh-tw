---
title: 使用 SQL 陳述式中的項目 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], elements supported
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77b7fdcfbc91e63451615b20c7eedf2748f687c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909703"
---
# <a name="elements-used-in-sql-statements"></a>使用 SQL 陳述式中的項目
先前所列的 SQL 陳述式中，會使用下列項目。  
  
## <a name="element"></a>元素  
 *基底資料表識別碼*:: =*使用者定義名稱*  
  
 *基底資料表名稱*:: =*基底資料表識別碼*  
  
 *布林值因素*:: = [NOT]*布林值主要*  
  
 *布林值主要*:: = 比較 *-述詞* &#124; (*搜尋條件*)  
  
 *布林值詞彙*:: =*布林值因素*[AND *boolean 詞彙*]  
  
 *字元字串常值*:: = ' {*字元*}...' (*字元*是驅動程式/資料來源的字元集中的任何字元。 若要包含單引號的常值字元 （"） 字元的字串常值中，使用兩個常值的引號字元 ['']。)  
  
 *資料行識別碼*:: =*使用者定義名稱*  
  
 *資料行名稱*:: = [*資料表名稱*。]*資料行識別碼*  
  
 *比較運算子*:: = < &#124; > &#124; \<= &#124; > = &#124; = &#124; <>  
  
 *比較述詞*:: =*運算式*比較運算子的運算式  
  
 *資料型別*:: =*字元字串類型*(*字元字串類型*是""DATA_TYPE""中的資料行 SQLGetTypeInfo 傳回的結果集的任一個 SQL_CHAR 任何資料類型或SQL_VARCHAR。)  
  
 *數字*:: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9  
  
 *動態參數*:: =？  
  
 *運算式*:: = 詞彙&#124;運算式 {+&#124;–} 詞彙  
  
 *因素*:: = [*+*&#124;*–*]*主要*  
  
 *插入值*:: =  
  
 *動態參數*  
  
 &#124;*常值*  
  
 &AMP;#124;NULL  
  
 &AMP;#124;使用者  
  
 *字母*:: = *lower case 字母&#124;上限大小寫字母*  
  
 *常值*:: =*字元字串常值*  
  
 *lower case 字母*:: = &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; h&#124;我&#124;j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r&#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y &#124; z  
  
 *order by 子句*:: ORDER BY =*排序規格*[，*排序規格*]...  
  
 *主要*:: =*資料行名稱*  
  
 &#124;*動態參數*  
  
 &#124;*常值*  
  
 &#124;(*運算式*)  
  
 *搜尋條件*:: = *boolean 詞彙*[或者*搜尋條件*]  
  
 *select 清單*:: = \* &#124; *選取子清單*[，*選取子清單*]... (*select 清單*不能包含參數。)  
  
 *選取子清單*:: =*運算式*  
  
 *排序規格*:: = {*不帶正負號整數&#124;資料行名稱*} [*ASC &#124; DESC*]  
  
 *資料表識別碼*:: =*使用者定義名稱*  
  
 *資料表名稱*:: =*資料表識別碼*  
  
 *資料表參考*:: =*資料表名稱*  
  
 *資料表的參考清單*:: =*資料表參考*[，*資料表參考*]...  
  
 *詞彙*:: =*因素* &#124; *詞彙*{\*&#124;*/*}*因素*  
  
 *不帶正負號整數*:: = {*位數*}  
  
 *大小寫字母大寫*:: = *A &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; H&#124;我&#124;J &#124; K &#124; L &#124; M &#124; N &#124; O &#124; P &#124;Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; X &#124; Y &#124; Z*  
  
 *使用者定義名稱*:: =*字母*[*位數* &#124; *字母* &#124; *_*]...
