This is a simple Xray server in a container.

1) You need to install docker beforehand

2) Download the repository to a separate directory and go into it:
 mkdir ~/xray && cd ~/xray/
 git clone https://github.com/Dustlex/xray_02_compose.git
 cd ~/xray/xray_02_compose/

3) Change the contents of the .env
- UUID variable (can be generated in any UUID generator, it will be used for VLESS connection)
- PASS variable (this is the password for shadowsocks, must be 16 characters (provided you don't change the 128-bit encryption in config.json) , base64 encoded)
   + you can encode the password "pipidorka123LEXP" with the command echo -n "pipidorka123LEXP" | base64. 
   + the obtained value should be specified in the variable and when connecting in the client during shadowsocks connection.

4) Start the service: 

  docker compose up -d

- You can check the startup via docker compose logs

As a client, I recommend using Nekoray https://github.com/MatsuriDayo/nekoray/releases/download/3.23/nekoray-3.23-2023-10-14-windows64.zip.

To connect, select Server - new profile - VLESS and fill in the window:
 + Name - any
 + Address - the domain you directed to the server where you deployed the container.
 + Port - 443
 + UUID - the one you specified in the .env file.
 + FLOW - xtls-rprx-vision
 + Transport - tcp
 + Security - tls
 + Packet encoding - xudp
 + Network settings - check the box - allow insecure connection (encryption will be ok, but with a certificate that we issued in the container ourselves, not from a trusted center).
Leave everything else as it is. 

Turn on, and choose either system proxy mode or TUN mode (the latter also creates a virtual network adapter in windows, to which you can configure the connection of other adapters). 



Это простой Xray сервер в контейнере.

1) Предварительно необходимо установить docker

2) Cкачать репозиторий в отдельную директорию и зайти в нее:
 mkdir ~/xray && cd ~/xray/
 git clone https://github.com/Dustlex/xray_02_compose.git
 cd ~/xray/xray_02_compose/

3) Изменить содержимое .env
- Переменную UUID (можно сформировать в любом UUID генераторе, она будет использована для VLESS подключения)
- Переменную PASS (это пароль для shadowsocks, должен состоять из 16-ти символов (при условии что вы не измените 128-битное шифрование в config.json) , закодированный в base64)
   + закодировать пароль "pipidorka123LEXP" можно командой echo -n "pipidorka123LEXP" | base64 
   + полученное значение надо указать в переменную и при подключении в клиенте  при shadowsocks подключении

4) Запустить сервис: 

  docker compose up -d

- Проверить запуск можно через docker compose logs

В качестве клиента, рекомендую использовать Nekoray https://github.com/MatsuriDayo/nekoray/releases/download/3.23/nekoray-3.23-2023-10-14-windows64.zip

Для подключения, выбираем Сервер - новый профиль - VLESS и в окне заполняем:
 + Имя - любое
 + Адрес - домен который вы направили на сервер где разворачивали контейнер
 + Порт - 443
 + UUID - тот что вы указали в файле .env
 + FLOW - xtls-rprx-vision
 + Транспорт - tcp
 + Безопасность - tls
 + Кодирование пакетов - xudp
 + Настройки сети - ставим галочку - разрешить небезопасное подключение (шифрование будет ок, но с сертификатом что мы выпустили в контейнере сами, а не из доверенного центра)
Все остальное оставляем как есть. 

Включаем, и выбираем либо режим системного прокси, либо режим TUN (последний в т.ч. создает виртуальный сeтевой адаптер в windows , к которому можно настроить подключение других адаптеров). 
