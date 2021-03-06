---
title: Задание метода сортировки конечных объектов в ссылках
description: В этой статье рассматривается, как задать метода сортировки для конечных объектов в ссылках.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: bb42a98666941c5dfa50a8dfbf45635ad25dc767
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386145"
---
# <a name="set-the-ordering-method-for-targets-in-referrals"></a>Задание метода сортировки конечных объектов в ссылках

> Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Ссылка — это упорядоченный список конечных объектов, которые клиентский компьютер получает от контроллера домена или сервера пространства имен, когда пользователь обращается к корню пространства имен или к папке с конечными объектами. После получения ссылки клиент пытается получить доступ к первому конечному объекту в списке. Если конечный объект недоступен, клиент пытается получить доступ к следующему конечному объекту.
Конечные объекты на сайте клиента всегда идут первыми в ссылке. Конечные объекты вне сайта клиента располагаются согласно методу сортировки.

В следующих разделах рассказывается, как указать, в каком порядке конечные объекты должны предлагаться клиентам, а также в чем заключаются различные методы сортировки ссылок для конечных объектов.

## <a name="to-set-the-ordering-method-for-targets-in-namespace-root-referrals"></a>Задание метода сортировки конечных объектов в ссылках корня пространства имен

Выполните следующие действия, чтобы задать метод сортировки для корня пространства имен:

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши пространство имен и выберите команду **Свойства**.

3.  На вкладке **Ссылки** выберите метод сортировки.

> [!NOTE]
> Чтобы использовать для задания метода сортировки конечных объектов в ссылках корня пространства имен Windows PowerShell, используйте командлет [Set-DfsnRoot](https://technet.microsoft.com/library/jj884281.aspx) с одним из следующих параметров:
>    -   **EnableSiteCosting** для задания метода сортировки **Минимальные затраты**
>    -   **EnableInsiteReferrals** для задания метода **Исключить конечные объекты вне сайта клиента**
>    -   Если опустить параметр, задается метод сортировки **Случайный порядок**. 

Модуль ДФСН Windows PowerShell появился в Windows Server 2012.
   
## <a name="to-set-the-ordering-method-for-targets-in-folder-referrals"></a>Задание метода сортировки для конечных объектов в ссылках папок

Папки с конечными объектами наследуют метод сортировки от корня пространства имен. Метод сортировки можно переопределить, выполнив следующие действия:

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши папку с целевыми объектами и выберите команду **Свойства**.

3.  На вкладке **Ссылки** установите флажок **Исключить конечные объекты вне сайта клиента**.

> [!NOTE]
> Чтобы исключить конечные объекты папок вне сайта клиента с помощью Windows PowerShell, используйте командлет [Set-DfsnFolder –EnableInsiteReferrals](https://technet.microsoft.com/library/jj884283.aspx).

## <a name="target-referral-ordering-methods"></a>Способы сортировки ссылок для конечных объектов

Способов сортировки три:

-   Случайный порядок
-   Минимальные затраты
-   Исключить конечные объекты вне сайта клиента

## <a name="random-order"></a>Случайный порядок

При использовании этого метода конечные объекты упорядочиваются следующим образом:

1.  Целевые объекты на том же сайте Active Directory Directory (AD DS), что и клиент, перечислены в произвольном порядке в верхней части ссылки.
2.  Конечные объекты, находящиеся за пределами сайта клиента, перечисляются в случайном порядке.

При отсутствии доступных конечных серверов на этом же сайте клиентский компьютер перенаправляется на случайный конечный сервер вне зависимости от того, насколько дорогостоящим будет подключение или на каком удалении находится конечный объект.

## <a name="lowest-cost"></a>Минимальные затраты

При использовании этого метода конечные объекты упорядочиваются следующим образом:

1.  Конечные объекты на том же сайте, что и клиент, перечисляются в случайном порядке в начале ссылки.
2.  Конечные объекты, находящиеся за пределами сайта клиента, перечисляются в порядке от минимальной до максимальной стоимости подключения. Ссылки с одинаковой стоимостью подключения группируются вместе, и конечные объекты располагаются в случайном порядке внутри каждой группы.

> [!NOTE]
> Затраты на межсайтовые переходы не отображаются в оснастке "Управление DFS". Для просмотра затрат на межсайтовые переходы используйте оснастку "Active Directory - сайты и службы".

## <a name="exclude-targets-outside-of-the-clients-site"></a>Исключить конечные объекты вне сайта клиента

При использовании этого метода ссылка содержит только конечные объекты, которые находятся на том же сайте, что и клиент. Эти конечные объекты, находящиеся на том же сайте, располагаются в случайном порядке. При отсутствии конечных объектов на том же сайте клиент не получит ссылку и не сможет получить доступ к этой части пространства имен.

> [!NOTE]
> Конечные объекты, для которых задан приоритет конечного объекта "Первый из всех конечных объектов" или "Последний из всех конечных объектов", все равно присутствуют в ссылке, несмотря на то что способ сортировки — **Исключить конечные объекты вне сайта клиента**.

## <a name="see-also"></a>См. также 

-   [Настройка пространств имен DFS](tuning-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)