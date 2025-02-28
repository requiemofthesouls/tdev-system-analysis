  
Так как компании важен быстрый TTM и не планируется большая нагрузка \- систему делаем модульным монолитом чтобы как можно быстрее вывести ее в прод.

Система состоит из следующих модулей:

- Модуль найма и тестирования воркеров  
- Модуль управления заказами  
- Модуль ставок  
- Модуль подбора воркеров и расчета стоимости заказа  
- Модуль сборки расходников  
- Модуль биллинга  
- Модуль проверки качества  
- Модуль уведомлений  
    
1) Модуль найма и тестирования воркеров  
   1) При поступлении новой заявки отправляется уведомление менеджерам?  
   2) Флоу выглядит таким образом что кот тестировщик оставляет заявку, после с ним связывается менеджер и назначает ему тесты. Тесты так же могут быть назначены заранее на конкретную вакансию, либо назначены после разговора с котом. В процессе тестирования должны отправляться уведомления по каждому шагу? По результатам тестов менеджер решает взять кота или нет. После принятия кота ему назначается специальный код состоящий из его характеристик, и потом он попадает в общий пул котов воркеров.  
   3) Важно: на этапе подачи заявок может быть дудос, поэтому нужно предусмотреть защиту от него.  
2) Модуль управления заказами  
   1) Кот клиент может создать заказ для выполнения услуги котом воркером. Заказ состоит из типа услуги, даты и описания что нужно сделать.  
      Типы услуг задаются менеджерами в админке.  
   2) После назначения на заказ кота воркера он запрашивает расходники в модуле сборки расходников. (здесь потенциально воркер будет ждать пока соберут расходники, поэтому стоит назначать воркера после того как на заказ соберут расходники)  
   3) После получения расходников воркер должен отметиться перед выполнением заказа прислав фотографию и нажать кнопку “Приступил”, если воркер не отметился \- заказ автоматически проваливается, при этом коту клиенту показывается предложение сформировать новый заказ (копия проваленного), флоу в этом случае будет как у нового заказа.  
   4) В конце работы воркер должен прислать фотку подписанного отчета с подписью клиента и надписью “все выполнено претензий нет”  
3) Модуль ставок  
   1) Менеджеры ставят сумму на заказ и условие. После выполнения или отмены или провала заказа система автоматически рассчитывает, кому и сколько денег надо отдать (банк делится между победителями). Это не самый критически важный проект для компании, поэтому он вряд ли будет часто меняться.  
   2) Условия могут быть “выполнен/провален” заказ  
   3) В случае проигрыша всех \- деньги достаются разработчикам  
   4) Деньги после подсчета распределяют победившим сами менеджеры.  
4) Модуль подбора воркеров и расчета стоимости заказа  
   1) Подбор выполняется рандомно  
   2) Расчет стоимости делается после подбора воркера, сам расчет будет выполнен по формуле в фиксированных 100 котоедениц  
   3) Алгоритм подбора и расчета стоимости в будущем может быть изменен  
5) Модуль сборки расходников   
   1) После того как заказ был создан нужно уведомить сотрудников отдела сборки чтобы они начали собирать расходники  
   2) Сразу после того как был создан заказ нужно запросить печеньку у поставщика, передав им информацию о клиенте, затем после того как она приедет положить ее в пакет с расходниками.  
   3) Когда расходники будут сформированы работники должны уведомить воркера о том что расходники готовы.  
6) Модуль биллинга   
   1) Для клиента каждое воскресенье формируется инвойс в котором сумма за все запрошенные задачи клиентом за текущую неделю списывается с его баланса. Необходимо показывать сколько клиент заплатит денег в конце текущей недели а так же список всех его инвойсов и их статусы оплат. Если клиент заплатил больше 10к условных кото-единиц в сумме, ему даётся скидка в 5%, если больше 20к — скидка 6%. За каждые 10к скидка увеличивается на 1%, предел скидки — 12%.  
   2) Для воркера каждый последний день месяца формируется инвойс в котором начисляется сумма, равная общим выплатам минус все штрафы за текущий месяц. Необходимо показывать сколько воркер заработал в общем, штрафы, инвойсы и их статусы. Воркер получает 60% от стоимости выполненной задачи, отменённые задачи не оплачиваются для воркера, за провальные задачи воркер получает штраф в 40 условных кото-единиц. Оплата производится через внешний сервис золотая шляпа.  
   3) Для менеджера нужно сделать возможность начислить воркеру любое количество денег.  
   4) После генерации инвойса нужно отправить уведомление на почту (для воркера и клиента). Уведомление о статусе оплаты клиентом отправляем при любом статусе. Уведомление для воркера отправляем после того как мы произвели ему выплату.  
7) Модуль проверки качества  
   1) Менеджер может проверить по любому заказу качество проверенной работы изучив работу воркера и связаться с клиентом.  
   2) Все отмененные или провальные заказы автоматически попадают менеджерам на проверку, чтобы изучить что случилось и как исправить ситуацию.  
   3) Результат заносится в специальную форму  
   4) После проверки отправляется уведомление клиенту и воркеру.  
8) Модуль уведомлений  
   1) Уведомнения отправляются только на почту

