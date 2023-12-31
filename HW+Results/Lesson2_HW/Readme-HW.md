1. Собрать схему из трёх серверов. Два сервера должны иметь как минимум 3 сетевых адаптера.
Один сервер должен иметь 2 сетевых адаптера.
2. Первый интерфейс на каждой виртуальной машине имеет режим подключения bridge (сетевой
мост) или nat для предоставления доступа в интернет и по ssh из родительской операционной
системы. В этом примере используется bridge, так как есть роутер провайдера, который
раздает IP-адреса.
3. Все последующие интерфейсы между серверами организуют отдельные изолированные
сегменты. Режим подключения — LAN Segment. Делается это, чтобы изолировать
коммуникацию между сетевыми адаптерами устройств.
4. Настроить любой из интерфейсов между server1 и server2. Назначить на него адреса из
подсети 192.168.12.0/24. Второй интерфейс между ними остается отключенным и в этом
задании не участвует.
5. Настроить подсеть между server2 и server3 с адресами из подсети 192.168.23.0/24.
6. На каждом из серверов поднять dummy0-интерфейс и назначить на него ip-адрес 1.1.1.1/32,
2.2.2.2/32, 3.3.3.3/32 соответственно.
7. На серверах установить пакет frr и настроить на роутерах ospf, добавив подсети
192.168.12.0/24, 192.168.23.0/24, 1.1.1.1/32, 2.2.2.2/32, 3.3.3.3/32 в area 0.
8. Убедиться, что маршрутизация работает, и с server1 вы должны пинговать 3.3.3.3 адрес на
server3. Убедитесь, что нужный тип трафика разрешен в firewalld и что трафик не улетает в
интернет при помощи traceroute.
9. На server3 создайте 2 папки nfs_1 и nfs_2, добавьте их в export.
10. Убедитесь, что только server1 может их примонтировать.
© geekbrains.ru 25
11. Убедитесь, что после перезагрузки server1 все еще может писать и читать файлы в
примонтированных папках
12. * На server3 создайте iSCSI target размером 2GB и примонтируйте этот LUN на server1.
Создайте там файловую систему xfs. Убедитесь, что диск будет активным после перезагрузки.
Задачи со * предназначены для продвинутых учеников, которым мало сделать обычное задание.