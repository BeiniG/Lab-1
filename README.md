# Лабораторная работа 1
Цель лабороторной работы: изучение утилит Linux
## Tutorial

Задаём переменные для работы с GitHub, а также создаём псевдоним для команды edit:
```sh
$ export GITHUB_USERNAME=<имя_пользователя>
$ export GIST_TOKEN=<сохраненный_токен>
$ alias edit=<nano|vi|vim|subl>
```
Создаем рабочую папку внутри директории текущего пользователя

```bash
$ mkdir -p ${GITHUB_USERNAME}/workspace
$ cd ${GITHUB_USERNAME}/workspace
$ pwd
$ cd ..
$ pwd
```
Вывод:

```bash
$ /home/vboxuser/BeniG/workspace
$ /home/vboxuser/BeniG
```
Создаем структуру подпапок для разделения задач, проектов и отчетов. Затем переходим обратно в рабочую директорию с помощью команды cd:

```bash
$ mkdir -p workspace/tasks/
$ mkdir -p workspace/projects/
$ mkdir -p workspace/reports/
$ cd workspace
```
Устанавливаем Node.js:

```bash
# Debian
$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
$ tar -xf node-v6.11.5-linux-x64.tar.xz
$ rm -rf node-v6.11.5-linux-x64.tar.xz
$ mv node-v6.11.5-linux-x64 node
```
Заходим в директорию Node.js, чтобы убедиться, что установка прошла нормально.

```bash
$ ls node/bin
$ echo ${PATH}
```
Изменяем пути для доступности Node.js:

```bash
$ export PATH=${PATH}:`pwd`/node/bin
$ echo ${PATH}
```
Создаём скрипт, активирующий Node.js

```bash
$ mkdir scripts
$ cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
$ source scripts/activate
```
Скачиваем пакет gist:

```bash
$ gem install gist
```
Перемещаем токен в защищённый файл:

```bash
$ (umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
```
# Report
Сначала папку, в которую копируются материалы лабораторной работы. Затем создаем Report.md.

```bash
$ export LAB_NUMBER=01
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```
# Homework
1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания:
https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
<details>
<summary>Процесс скачивания</summary>

```bash
--2026-02-21 12:06:11--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
Resolving sourceforge.net (sourceforge.net)... 104.18.12.149, 104.18.13.149, 2606:4700::6812:c95, ...
Connecting to sourceforge.net (sourceforge.net)|104.18.12.149|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/ [following]
--2026-02-21 12:06:12--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download [following]
--2026-02-21 12:06:12--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 302 Found
Location: https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABpmXWEwfV3IjhBuX6NMztn-01kn1-QBq9qwCIdJyrwwEAdDIZg3CYL2WS7JsI2fSO6sZv2MJsvH0L_QctSV8QsHUMNNA%3D%3D&use_mirror=sf-eu-introserv-1&r= [following]
--2026-02-21 12:06:12--  https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABpmXWEwfV3IjhBuX6NMztn-01kn1-QBq9qwCIdJyrwwEAdDIZg3CYL2WS7JsI2fSO6sZv2MJsvH0L_QctSV8QsHUMNNA%3D%3D&use_mirror=sf-eu-introserv-1&r=
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 104.18.12.149, 104.18.13.149, 2606:4700::6812:c95, ...
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.12.149|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://sf-eu-introserv-1.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1 [following]
--2026-02-21 12:06:13--  https://sf-eu-introserv-1.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1
Resolving sf-eu-introserv-1.dl.sourceforge.net (sf-eu-introserv-1.dl.sourceforge.net)... 141.95.66.71
Connecting to sf-eu-introserv-1.dl.sourceforge.net (sf-eu-introserv-1.dl.sourceforge.net)|141.95.66.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111710205 (107M) [application/x-gzip]
Saving to: ‘boost_1_69_0.tar.gz’

boost_1_69_0.tar.gz 100%[===================>] 106.53M  3.98MB/s    in 23s     

2026-02-21 12:06:37 (4.56 MB/s) - ‘boost_1_69_0.tar.gz’ saved [111710205/111710205]
```

</details>

2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0 Это можно сделать с помощью команды:
```bash
$ tar -xf boost_1_69_0.tar.gz
```
3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории. Используем команду:
```bash
$ find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
```
Параметры: -maxdepth 1 – Поиск будет осуществляться только в самой директории. type f - Поиск только файлов. wc -l - Позволяет вывести количество файлов. В консоль вывелось число 24.

4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории. Прописываем

```bash
$ find ~/boost_1_69_0 -type f | wc -l
```
Консоль выдаёт число 75440.

5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp). Используем команду:

```bash
$ find ~/boost_1_69_0 -type f \( -name "*.h" -o -name "*.hpp" -o -name "*.hxx" \) | wc -l
```
Параметры -name - поиск файлов с необходимыми нам расширениями. В терминале выдается значение 28538.
Для подсчёта файлов с расширением .cpp используем следующую команду:

```bash
$ find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l
```
Консоль выдала значение 13789.
Для подсчёта всех остальных файлов используем следующую команду

```bash
$ find ~/boost_1_69_0 -type f ! \( -name "*.h" -o -name "*.hpp" -o -name "*.hxx" -o -name "*.cpp" \) | wc -l
```
В итоге получаем число 33113.

6. Найдите полный пусть до файла any.hpp внутри библиотеки boost. Для поиска полного пути используем команду:

```bash
$ find ~/boost_1_69_0 -type f -name "any.hpp"
```
В таком случае терминал выдаст такой список:

```bash
/home/vboxuser/boost_1_69_0/boost/type_erasure/any.hpp
/home/vboxuser/boost_1_69_0/boost/hana/any.hpp
/home/vboxuser/boost_1_69_0/boost/hana/fwd/any.hpp
/home/vboxuser/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
/home/vboxuser/boost_1_69_0/boost/fusion/include/any.hpp
/home/vboxuser/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/vboxuser/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/vboxuser/boost_1_69_0/boost/any.hpp
/home/vboxuser/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/home/vboxuser/boost_1_69_0/boost/proto/detail/any.hpp
```
7. Выведите в консоль все файлы, где упоминается последовательность boost::asio. Для этого можно воспользоваться командой:

```bash
$ grep -rl "boost::asio" ~/boost_1_69_0
```
<details>
<summary>Список файлов</summary>

```bash
/home/vboxuser/boost_1_69_0/doc/html/boost_process/extend.html
/home/vboxuser/boost_1_69_0/doc/html/boost_process/tutorial.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ResolveHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__unicast__hops.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffered_stream/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffered_stream/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/error__misc_category.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffer_copy.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload15.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload16.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload10.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload14.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload11.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload12.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload7.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload9.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until/overload13.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/deadline_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/WaitHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ShutdownHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ssl__stream.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/MoveAcceptHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/use_future_t.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/dynamic_vector_buffer/const_buffers_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/dynamic_vector_buffer/mutable_buffers_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/thread_pool/make_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/thread_pool/add_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver_query/hints.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/placeholders__bytes_transferred.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ConnectHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/spawn/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_at/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_at/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_at/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/local__stream_protocol/acceptor.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ReadHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__misc_errors__gt_.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/transfer_at_least.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__addrinfo_errors__gt_/value.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/MutableBufferSequence.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/send_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/get_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/get_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_receive_from/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_receive_from/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/shutdown/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/shutdown/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/basic_datagram_socket/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/basic_datagram_socket/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/basic_datagram_socket/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/basic_datagram_socket/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/receive_from/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/basic_datagram_socket.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/connect/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/connect/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_receive/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/send_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/set_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/set_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/open/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/open/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/broadcast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/remote_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/remote_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_send_to/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_send_to/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/linger.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/send_to/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/do_not_route.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/receive_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_connect.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/reuse_address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/release/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/release/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/bind/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/bind/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_send/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/async_send/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/debug.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/enable_connection_aborted.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/keep_alive.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/out_of_band_inline.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/send/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/local_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/local_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/receive_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_datagram_socket/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/const_buffers_1/value_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/WriteHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload10.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload11.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload12.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload8.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload7.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/connect/overload9.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/system_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/system_context/make_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/system_context/add_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/random_access_handle/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/random_access_handle/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/read_some_at/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/write_some_at/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/async_write_some_at.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/async_read_some_at.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/random_access_handle.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__random_access_handle/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__work/work/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__work/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__work/work.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__work/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__misc_errors__gt_/value.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/expires_from_now/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/expires_from_now/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/cancel_one/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/cancel_one/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/expires_at/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/expires_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/streambuf.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/dynamic_string_buffer/const_buffers_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/dynamic_string_buffer/mutable_buffers_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/placeholders__endpoint.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write/overload10.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write/overload9.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/generic__datagram_protocol.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/placeholders__iterator.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/to_v4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/operator_eq_.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/to_v6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/address/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/address/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/operator_eq_/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__address/operator_eq_/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/thread_pool.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/error__ssl_category.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/async_write_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/write_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/async_read_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/stream_descriptor.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/stream_descriptor/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/stream_descriptor/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/read_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__stream_descriptor/release.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__boost__asio__ssl__error__stream_errors__gt_/value.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__netdb_errors__gt_.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/RangeConnectHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ssl__error__stream_category.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ssl__rfc2818_verification.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/send_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/send_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/broadcast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/linger.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/do_not_route.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/receive_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/reuse_address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/debug.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/enable_connection_aborted.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/keep_alive.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/out_of_band_inline.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/socket_base/receive_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/Handler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffered_write_stream/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffered_write_stream/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ssl__stream/native_handle.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ssl__stream/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ssl__stream/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffer_cast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/HandshakeHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__boost__asio__ssl__error__stream_errors__gt_.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/serial_port.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/async_write_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/write_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/serial_port/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/serial_port/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/serial_port/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/serial_port/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/async_read_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/read_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/serial_port/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__multicast__outbound_interface.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/overlapped_handle/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/overlapped_handle/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_handle/overlapped_handle.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/mutable_buffer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__tcp/acceptor.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__tcp/no_delay.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/send_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/get_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/get_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/shutdown/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/shutdown/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/connect/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/connect/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/send_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/set_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/set_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/open/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/open/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/broadcast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/remote_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/remote_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/linger.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/basic_socket.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/do_not_route.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/receive_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/basic_socket/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/basic_socket/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/basic_socket/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/basic_socket/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/async_connect.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/reuse_address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/release/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/release/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/bind/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/bind/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/debug.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/enable_connection_aborted.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/keep_alive.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/out_of_band_inline.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/local_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/local_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/receive_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__basic_errors__gt_.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/placeholders__results.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/null_buffers/value_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_until.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffer_sequence_begin.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/spawn.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/generic__raw_protocol.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/steady_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_at/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_at/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_at/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_at/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_connect/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_connect/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_connect/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_connect/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_connect/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_connect/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffered_read_stream/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffered_read_stream/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_streambuf.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/error__addrinfo_category.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/send_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/get_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/get_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/shutdown/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/shutdown/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/connect/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/connect/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_write_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_receive/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/send_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/set_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/set_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/write_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/open/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/open/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/broadcast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/remote_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/remote_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/linger.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/do_not_route.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_read_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/basic_stream_socket.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/receive_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_connect.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/reuse_address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/basic_stream_socket/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/basic_stream_socket/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/basic_stream_socket/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/basic_stream_socket/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/release/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/release/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/receive/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/bind/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/bind/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_send/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/async_send/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/debug.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/enable_connection_aborted.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/keep_alive.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/out_of_band_inline.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/send/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/send/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/local_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/local_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/receive_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/read_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_stream_socket/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context/make_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context/add_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_endpoint/basic_endpoint/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_endpoint/basic_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_endpoint/address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_endpoint/address/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_endpoint/address/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_endpoint/basic_endpoint.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write_at/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write_at/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write_at/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write_at/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/write_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_deadline_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/mutable_buffers_1/value_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_completion/completion_handler_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/SignalHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read/overload10.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/read/overload9.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/IteratorConnectHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/send_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/get_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/get_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/basic_socket_acceptor.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/send_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/set_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/set_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/open/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/open/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/broadcast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/linger.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/listen/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/do_not_route.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/receive_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/async_accept.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload10.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload11.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload12.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload8.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload7.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/accept/overload9.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/reuse_address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/release/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/release/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/basic_socket_acceptor/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/basic_socket_acceptor/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/basic_socket_acceptor/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/basic_socket_acceptor/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/bind/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/bind/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/debug.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/enable_connection_aborted.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/keep_alive.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/out_of_band_inline.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/local_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/local_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/receive_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_acceptor/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/error__netdb_category.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/AcceptHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/generic__stream_protocol.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/transfer_all.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/send_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/get_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/get_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/shutdown/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/shutdown/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/connect/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/connect/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/async_receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/async_receive/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/send_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/set_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/set_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/open/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/open/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/broadcast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/remote_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/remote_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/linger.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/async_send.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/do_not_route.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/receive_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/async_connect.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/reuse_address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/release/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/release/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/receive/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/bind/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/bind/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/debug.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/enable_connection_aborted.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/keep_alive.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/out_of_band_inline.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/send/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/local_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/local_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/receive_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_seq_packet_socket/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__service/service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__service/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__service/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write_at/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write_at/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write_at/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/object_handle.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/object_handle/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/object_handle/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__object_handle/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/expires_from_now/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/expires_from_now/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/basic_waitable_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/cancel_one/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/cancel_one/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/expires_after.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/basic_waitable_timer/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/basic_waitable_timer/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/basic_waitable_timer/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/expires_at/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/expires_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_waitable_timer/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_write/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/execution_context/make_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/execution_context/add_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/dynamic_buffer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__multicast__enable_loopback.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/experimental__detached_t.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_iostream/expires_from_now/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_iostream/expires_after.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_iostream/expires_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/stream_handle.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/async_write_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/write_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/stream_handle/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/stream_handle/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/async_read_some.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/read_some/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__stream_handle/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_streambuf_ref/const_buffers_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_streambuf_ref/mutable_buffers_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_io_object/basic_io_object.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_io_object/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_io_object/executor_type.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_io_object/basic_io_object/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_io_object/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/signal_set/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/signal_set/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/signal_set/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/signal_set/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set/signal_set.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__v6_only.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__multicast__leave_group.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor_base/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_ptr/overlapped_ptr.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_ptr/reset.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_ptr/overlapped_ptr/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/windows__overlapped_ptr/reset/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/transfer_exactly.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__multicast__join_group.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__netdb_errors__gt_/value.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__ssl_errors__gt_.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__multicast__hops.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/error__system_category.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__strand.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__addrinfo_errors__gt_.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/add_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/signal_set.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload8.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/async_read_until/overload7.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__basic_errors__gt_/value.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/descriptor/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/descriptor/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/descriptor.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/posix__descriptor/release.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/buffer_sequence_end.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/async_resolve/overload6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/async_resolve/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/async_resolve/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/async_resolve/overload5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/async_resolve/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/async_resolve/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/basic_resolver/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/cancel.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/basic_resolver.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ip__basic_resolver/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/placeholders__signal_number.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__strand/context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__strand/strand.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__strand/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/io_context__strand/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/high_resolution_timer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_streambuf/expires_from_now/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_streambuf/expires_after.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_socket_streambuf/expires_at/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/yield_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/const_buffer.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/BufferedHandshakeHandler.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/is_error_code_enum_lt__ssl_errors__gt_/value.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/ConstBufferSequence.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/wait/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/wait/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_wait.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/send_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/get_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/get_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_receive_from/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_receive_from/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/shutdown/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/shutdown/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/receive_from/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/connect/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/connect/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_receive/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/send_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/set_option/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/set_option/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/open/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/open/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/broadcast.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/remote_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/remote_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_send_to/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_send_to/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/linger.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/send_to/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/basic_raw_socket.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/bytes_readable.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/do_not_route.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/receive_buffer_size.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_connect.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/get_io_context.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/reuse_address.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/release/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/release/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/receive/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/close/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/close/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/bind/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/bind/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/cancel/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/cancel/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/io_control/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/io_control/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_send/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/async_send/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/debug.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/enable_connection_aborted.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/keep_alive.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/out_of_band_inline.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/send/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/local_endpoint/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/local_endpoint/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/receive_low_watermark.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/get_io_service.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/native_non_blocking/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/native_non_blocking/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/native_non_blocking/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/basic_raw_socket/overload4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/basic_raw_socket/overload3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/basic_raw_socket/overload1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/reference/basic_raw_socket/basic_raw_socket/overload2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/index.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/examples/cpp03_examples.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/examples/cpp11_examples.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/serialization/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/serialization/connection.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/serialization/client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server3/reply.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server3/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server3/connection.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server3/reply.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server3/connection.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server3/server.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server4/reply.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server4/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server4/reply.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server4/main.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server4/server.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server4/request_parser.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/reply.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/connection.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/reply.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/io_context_pool.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/io_context_pool.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/connection.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server2/server.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server/reply.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server/connection.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server/reply.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server/connection.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/server/server.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/client/sync_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/http/client/async_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/echo/blocking_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/echo/blocking_udp_echo_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/echo/blocking_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/echo/async_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/echo/blocking_tcp_echo_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/echo/async_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/socks4/socks4.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/socks4/sync_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/spawn/parallel_grep.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/spawn/echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/invocation/prioritised_handlers.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/multicast/sender.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/multicast/receiver.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/services/basic_logger.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/services/daytime_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/services/logger_service.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/services/logger_service.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/windows/transmit_file.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/timers/time_t_timer.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/allocation/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/buffers/reference_counted.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/ssl/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/ssl/client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/icmp/ping.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/icmp/ipv4_header.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/nonblocking/third_party_lib.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/chat/chat_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/chat/chat_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/chat/posix_chat_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/timeouts/async_tcp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/timeouts/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/timeouts/blocking_udp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/timeouts/blocking_token_tcp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/timeouts/blocking_tcp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/porthopper/protocol.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/porthopper/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/porthopper/client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/fork/daemon.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/fork/process_per_connection.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/local/connect_pair.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/local/iostream_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/local/stream_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/local/stream_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/iostreams/http_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/iostreams/daytime_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp03/iostreams/daytime_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/http/server/reply.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/http/server/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/http/server/connection.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/http/server/reply.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/http/server/connection.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/http/server/server.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/echo/blocking_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/echo/blocking_udp_echo_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/echo/blocking_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/echo/async_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/echo/blocking_tcp_echo_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/echo/async_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/executors/priority_scheduler.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/executors/actor.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/executors/bank_account_1.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/executors/pipeline.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/executors/bank_account_2.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/executors/fork_join.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/socks4/socks4.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/socks4/sync_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/spawn/parallel_grep.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/spawn/echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/futures/daytime_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/invocation/prioritised_handlers.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/multicast/sender.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/multicast/receiver.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/timers/time_t_timer.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/allocation/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/buffers/reference_counted.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/ssl/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/ssl/client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/chat/chat_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/chat/chat_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/operations/composed_1.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/operations/composed_3.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/operations/composed_5.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/operations/composed_4.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/operations/composed_2.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/timeouts/async_tcp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/timeouts/server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/timeouts/blocking_udp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/timeouts/blocking_token_tcp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/timeouts/blocking_tcp_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/fork/daemon.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/fork/process_per_connection.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/local/connect_pair.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/local/iostream_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/local/stream_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/local/stream_client.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/handler_tracking/async_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp11/handler_tracking/custom_tracking.hpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp17/coroutines_ts/range_based_for.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp17/coroutines_ts/chat_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp17/coroutines_ts/echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp17/coroutines_ts/refactored_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/example/cpp17/coroutines_ts/double_buffered_echo_server.cpp
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/net_ts.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer3/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer5/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime7/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime4.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime6/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime6.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime7.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer5.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer2/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime3.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime2/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer1/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer2.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime5/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer1.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime1/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime3/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tutdaytime4/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/tutorial/tuttimer4/src.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/core/allocation.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/core/line_based.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/core/coroutine.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/core/coroutines_ts.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/core/strands.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/core/spawn.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/signals.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/networking/other_protocols.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/networking/protocols.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/posix/stream_descriptor.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/posix/fork.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/cpp2011/move_handlers.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/cpp2011/futures.html
/home/vboxuser/boost_1_69_0/doc/html/boost_asio/overview/ssl.html
/home/vboxuser/boost_1_69_0/doc/html/boost/process/std_in.html
/home/vboxuser/boost_1_69_0/doc/html/boost/process/std_out.html
/home/vboxuser/boost_1_69_0/doc/html/boost/process/on_exit.html
/home/vboxuser/boost_1_69_0/doc/html/boost/process/spawn.html
/home/vboxuser/boost_1_69_0/doc/html/boost/process/async_pipe.html
/home/vboxuser/boost_1_69_0/doc/html/process/reference.html
/home/vboxuser/boost_1_69_0/boost/asio/buffered_write_stream.hpp
/home/vboxuser/boost_1_69_0/boost/asio/async_result.hpp
/home/vboxuser/boost_1_69_0/boost/asio/raw_socket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/buffer.hpp
/home/vboxuser/boost_1_69_0/boost/asio/waitable_timer_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/coroutine.hpp
/home/vboxuser/boost_1_69_0/boost/asio/io_context.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_socket.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_streambuf.hpp
/home/vboxuser/boost_1_69_0/boost/asio/buffered_read_stream.hpp
/home/vboxuser/boost_1_69_0/boost/asio/spawn.hpp
/home/vboxuser/boost_1_69_0/boost/asio/signal_set_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/execution_context.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_datagram_socket.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_socket_iostream.hpp
/home/vboxuser/boost_1_69_0/boost/asio/generic/datagram_protocol.hpp
/home/vboxuser/boost_1_69_0/boost/asio/generic/raw_protocol.hpp
/home/vboxuser/boost_1_69_0/boost/asio/generic/seq_packet_protocol.hpp
/home/vboxuser/boost_1_69_0/boost/asio/generic/stream_protocol.hpp
/home/vboxuser/boost_1_69_0/boost/asio/generic/detail/endpoint.hpp
/home/vboxuser/boost_1_69_0/boost/asio/generic/detail/impl/endpoint.ipp
/home/vboxuser/boost_1_69_0/boost/asio/generic/basic_endpoint.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ts/netfwd.hpp
/home/vboxuser/boost_1_69_0/boost/asio/uses_executor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/write.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_io_object.hpp
/home/vboxuser/boost_1_69_0/boost/asio/buffers_iterator.hpp
/home/vboxuser/boost_1_69_0/boost/asio/read_until.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_waitable_timer.hpp
/home/vboxuser/boost_1_69_0/boost/asio/is_executor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/io_context_strand.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_stream_socket.hpp
/home/vboxuser/boost_1_69_0/boost/asio/serial_port_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/posix/stream_descriptor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/posix/stream_descriptor_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/posix/basic_stream_descriptor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/posix/basic_descriptor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/posix/descriptor_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/posix/descriptor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_socket_streambuf.hpp
/home/vboxuser/boost_1_69_0/boost/asio/seq_packet_socket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_deadline_timer.hpp
/home/vboxuser/boost_1_69_0/boost/asio/read_at.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/object_handle_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/random_access_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/overlapped_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/stream_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/basic_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/basic_random_access_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/basic_stream_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/object_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/overlapped_ptr.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/random_access_handle_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/stream_handle_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/windows/basic_object_handle.hpp
/home/vboxuser/boost_1_69_0/boost/asio/signal_set.hpp
/home/vboxuser/boost_1_69_0/boost/asio/use_future.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/context_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/context.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/stream.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/stream_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/rfc2818_verification.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/impl/context.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/impl/error.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/impl/context.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/io.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/stream_core.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/buffered_handshake_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/impl/engine.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/impl/openssl_init.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/engine.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/write_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/openssl_init.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/detail/read_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ssl/error.hpp
/home/vboxuser/boost_1_69_0/boost/asio/stream_socket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/connect.hpp
/home/vboxuser/boost_1_69_0/boost/asio/handler_invoke_hook.hpp
/home/vboxuser/boost_1_69_0/boost/asio/write_at.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/buffered_write_stream.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/io_context.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/buffered_read_stream.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/spawn.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/write.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/read_until.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/io_context.ipp
/home/vboxuser/boost_1_69_0/boost/asio/impl/read_at.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/connect.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/write_at.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/read.hpp
/home/vboxuser/boost_1_69_0/boost/asio/impl/execution_context.ipp
/home/vboxuser/boost_1_69_0/boost/asio/impl/serial_port_base.ipp
/home/vboxuser/boost_1_69_0/boost/asio/read.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_raw_socket.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_timer_scheduler.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/resolve_endpoint_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_utils.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/is_buffer_sequence.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/resolver_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/service_registry.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_resolver_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/buffer_sequence_adapter.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/std_static_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_serial_port_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/signal_handler.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_null_buffers_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/null_socket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/null_reactor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_async_manager.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winapp_thread.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_io_context.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/conditionally_enabled_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_static_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/handler_cont_helpers.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/resolve_query_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_recvfrom_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/posix_static_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/resolver_service_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/socket_option.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/signal_set_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_connect_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/handler_tracking.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/timer_queue.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_ssocket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/null_static_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_object_handle_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/std_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/descriptor_write_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_socket_send_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_overlapped_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/handler_invoke_helpers.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_recvmsg_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/noncopyable.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/null_thread.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/thread_group.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winsock_init.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_handle_read_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_handle_write_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/conditionally_enabled_event.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/buffered_stream_storage.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_socket_connect_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_socket_recv_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_serial_port_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_accept_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/kqueue_reactor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactor_op_queue.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/handler_type_requirements.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/descriptor_read_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_overlapped_ptr.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_wait_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/strand_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/epoll_reactor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/scheduler.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/winrt_timer_scheduler.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_static_mutex.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/throw_error.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/strand_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/winrt_timer_scheduler.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_iocp_serial_port_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_iocp_io_context.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/descriptor_ops.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_thread.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/reactive_descriptor_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/kqueue_reactor.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/socket_ops.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/strand_executor_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/reactive_serial_port_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/signal_set_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/resolver_service_base.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/posix_mutex.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/eventfd_select_interrupter.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/winrt_ssocket_service_base.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_tss_ptr.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/handler_tracking.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_mutex.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/posix_thread.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/posix_tss_ptr.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/select_reactor.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/strand_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/reactive_socket_service_base.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_iocp_handle_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/winsock_init.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_iocp_socket_service_base.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/pipe_select_interrupter.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/dev_poll_reactor.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/epoll_reactor.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_iocp_io_context.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/posix_event.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/dev_poll_reactor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/select_reactor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/socket_select_interrupter.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_event.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/buffer_sequence_adapter.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/win_object_handle_service.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/service_registry.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/impl/scheduler.ipp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_sendto_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_ssocket_service_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_recvfrom_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_service_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_accept_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_descriptor_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_recv_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/descriptor_ops.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_service_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_handle_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_send_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_send_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/deadline_timer_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/posix_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/string_view.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_null_buffers_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_recv_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_socket_connect_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/winrt_resolve_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/dev_poll_reactor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/select_reactor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/consuming_buffers.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/reactive_wait_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/handler_alloc_helpers.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/wait_handler.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/wince_thread.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/completion_handler.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/null_mutex.hpp
/home/vboxuser/boost_1_69_0/boost/asio/detail/win_iocp_socket_recvmsg_op.hpp
/home/vboxuser/boost_1_69_0/boost/asio/datagram_socket_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/executor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_seq_packet_socket.hpp
/home/vboxuser/boost_1_69_0/boost/asio/buffered_stream.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_signal_set.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_socket_acceptor.hpp
/home/vboxuser/boost_1_69_0/boost/asio/socket_acceptor_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/deadline_timer_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/icmp.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/resolver_service.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/basic_resolver_entry.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/address.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/basic_resolver_results.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/v6_only.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/address_v6.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/tcp.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/basic_resolver_query.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/unicast.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/network_v4.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/udp.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/basic_resolver.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/network_v6.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/basic_resolver_iterator.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/multicast.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/address_v6.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/address.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/network_v6.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/address_v6.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/address.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/network_v4.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/address_v4.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/network_v6.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/network_v4.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/address_v4.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/basic_endpoint.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/impl/host_name.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ip/detail/endpoint.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/detail/socket_option.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/detail/impl/endpoint.ipp
/home/vboxuser/boost_1_69_0/boost/asio/ip/address_v4.hpp
/home/vboxuser/boost_1_69_0/boost/asio/ip/basic_endpoint.hpp
/home/vboxuser/boost_1_69_0/boost/asio/socket_base.hpp
/home/vboxuser/boost_1_69_0/boost/asio/serial_port.hpp
/home/vboxuser/boost_1_69_0/boost/asio/local/datagram_protocol.hpp
/home/vboxuser/boost_1_69_0/boost/asio/local/stream_protocol.hpp
/home/vboxuser/boost_1_69_0/boost/asio/local/connect_pair.hpp
/home/vboxuser/boost_1_69_0/boost/asio/local/detail/endpoint.hpp
/home/vboxuser/boost_1_69_0/boost/asio/local/detail/impl/endpoint.ipp
/home/vboxuser/boost_1_69_0/boost/asio/local/basic_endpoint.hpp
/home/vboxuser/boost_1_69_0/boost/asio/basic_serial_port.hpp
/home/vboxuser/boost_1_69_0/boost/asio/error.hpp
/home/vboxuser/boost_1_69_0/boost/asio/thread_pool.hpp
/home/vboxuser/boost_1_69_0/boost/asio/experimental/impl/co_spawn.hpp
/home/vboxuser/boost_1_69_0/boost/asio/experimental/impl/detached.hpp
/home/vboxuser/boost_1_69_0/boost/asio/experimental/detached.hpp
/home/vboxuser/boost_1_69_0/boost/asio/placeholders.hpp
/home/vboxuser/boost_1_69_0/boost/asio/completion_condition.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/ostream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/static_buffer.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/buffers_prefix.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/buffers_adapter.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/multi_buffer.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/buffered_read_stream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/bind_handler.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/buffers_cat.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/flat_buffer.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/type_traits.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/static_buffer.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/flat_static_buffer.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/buffers_adapter.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/read_size.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/buffers_prefix.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/flat_buffer.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/handler_ptr.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/multi_buffer.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/buffers_suffix.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/buffered_read_stream.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/impl/buffers_cat.ipp
/home/vboxuser/boost_1_69_0/boost/beast/core/flat_static_buffer.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/detail/buffers_ref.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/detail/bind_handler.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/detail/type_traits.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/buffers_to_string.hpp
/home/vboxuser/boost_1_69_0/boost/beast/core/buffers_suffix.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/chunk_encode.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/span_body.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/parser.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/string_body.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/write.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/vector_body.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/basic_parser.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/basic_file_body.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/type_traits.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/empty_body.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/impl/basic_parser.ipp
/home/vboxuser/boost_1_69_0/boost/beast/http/impl/fields.ipp
/home/vboxuser/boost_1_69_0/boost/beast/http/impl/serializer.ipp
/home/vboxuser/boost_1_69_0/boost/beast/http/impl/write.ipp
/home/vboxuser/boost_1_69_0/boost/beast/http/impl/file_body_win32.ipp
/home/vboxuser/boost_1_69_0/boost/beast/http/impl/read.ipp
/home/vboxuser/boost_1_69_0/boost/beast/http/impl/chunk_encode.ipp
/home/vboxuser/boost_1_69_0/boost/beast/http/read.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/fields.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/serializer.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/basic_dynamic_body.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/detail/chunk_encode.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/buffer_body.hpp
/home/vboxuser/boost_1_69_0/boost/beast/http/error.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/stream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/role.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/rfc6455.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/ssl.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/ping.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/handshake.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/accept.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/teardown.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/write.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/close.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/stream.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/impl/read.ipp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/detail/utf8_checker.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/detail/stream_base.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/detail/mask.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/detail/pausation.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/detail/frame.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/teardown.hpp
/home/vboxuser/boost_1_69_0/boost/beast/websocket/ssl.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/timeout_service.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/timeout_socket.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/impl/timeout_service.ipp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/impl/timeout_socket.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/impl/flat_stream.ipp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/detail/timeout_service.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/detail/service_base.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/detail/impl/timeout_service.ipp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/detail/flat_stream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/ssl_stream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/core/flat_stream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/test/stream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/test/impl/stream.ipp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/http/icy_stream.hpp
/home/vboxuser/boost_1_69_0/boost/beast/experimental/http/impl/icy_stream.ipp
/home/vboxuser/boost_1_69_0/boost/log/sinks/syslog_backend.hpp
/home/vboxuser/boost_1_69_0/boost/process/async.hpp
/home/vboxuser/boost_1_69_0/boost/process/io.hpp
/home/vboxuser/boost_1_69_0/boost/process/spawn.hpp
/home/vboxuser/boost_1_69_0/boost/process/system.hpp
/home/vboxuser/boost_1_69_0/boost/process/async_system.hpp
/home/vboxuser/boost_1_69_0/boost/process/async_pipe.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/traits/async.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/posix/io_context_ref.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/posix/async_in.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/posix/async_out.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/posix/async_pipe.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/posix/sigchld_service.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/windows/io_context_ref.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/windows/async_in.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/windows/async_out.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/windows/async_pipe.hpp
/home/vboxuser/boost_1_69_0/boost/process/detail/async_handler.hpp
/home/vboxuser/boost_1_69_0/libs/fiber/doc/callbacks.qbk
/home/vboxuser/boost_1_69_0/libs/fiber/doc/integration.qbk
/home/vboxuser/boost_1_69_0/libs/fiber/doc/asio.qbk
/home/vboxuser/boost_1_69_0/libs/fiber/doc/fibers.qbk
/home/vboxuser/boost_1_69_0/libs/fiber/examples/asio/exchange.cpp
/home/vboxuser/boost_1_69_0/libs/fiber/examples/asio/ps/subscriber.cpp
/home/vboxuser/boost_1_69_0/libs/fiber/examples/asio/ps/server.cpp
/home/vboxuser/boost_1_69_0/libs/fiber/examples/asio/ps/publisher.cpp
/home/vboxuser/boost_1_69_0/libs/fiber/examples/asio/round_robin.hpp
/home/vboxuser/boost_1_69_0/libs/fiber/examples/asio/autoecho.cpp
/home/vboxuser/boost_1_69_0/libs/thread/test/test_9303.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/strand.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/signal_set.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/use_future.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/is_write_buffered.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/write.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/socket_base.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/error.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/write_at.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/serial_port_base.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/serial_port.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/coroutine.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/io_context.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/generic/seq_packet_protocol.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/generic/stream_protocol.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/generic/raw_protocol.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/generic/datagram_protocol.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/read_at.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/unit_test.hpp
/home/vboxuser/boost_1_69_0/libs/asio/test/connect.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/posix/stream_descriptor.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/windows/object_handle.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/windows/overlapped_ptr.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/windows/random_access_handle.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/windows/stream_handle.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/system_timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ssl/stream.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/archetypes/deprecated_async_ops.hpp
/home/vboxuser/boost_1_69_0/libs/asio/test/archetypes/async_ops.hpp
/home/vboxuser/boost_1_69_0/libs/asio/test/deadline_timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/buffer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/streambuf.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/buffered_read_stream.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/latency/tcp_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/latency/udp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/latency/udp_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/latency/tcp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/buffered_write_stream.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/read.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/network_v4.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/v6_only.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/host_name.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/udp.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/network_v6.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/address.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/multicast.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/unicast.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/tcp.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/address_v4.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/address_v6.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/ip/icmp.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/is_read_buffered.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/buffered_stream.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/buffers_iterator.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/local/connect_pair.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/local/stream_protocol.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/local/datagram_protocol.cpp
/home/vboxuser/boost_1_69_0/libs/asio/test/read_until.cpp
/home/vboxuser/boost_1_69_0/libs/asio/doc/using.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/ShutdownHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/SignalHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/BufferedHandshakeHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/ConstBufferSequence.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/ReadHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/ConnectHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/WriteHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/MoveAcceptHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/Handler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/WaitHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/IteratorConnectHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/MutableBufferSequence.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/ResolveHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/HandshakeHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/AcceptHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/requirements/RangeConnectHandler.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/reference.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/reference.xsl
/home/vboxuser/boost_1_69_0/libs/asio/doc/tutorial.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/examples.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/posix.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/buffers.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/strands.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/signals.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/protocols.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/allocation.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/line_based.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/other_protocols.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/basics.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/coroutine.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/cpp2011.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/coroutines_ts.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/ssl.qbk
/home/vboxuser/boost_1_69_0/libs/asio/doc/overview/spawn.qbk
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/serialization/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/serialization/connection.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/serialization/client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server3/reply.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server3/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server3/connection.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server3/reply.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server3/connection.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server3/server.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server4/reply.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server4/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server4/reply.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server4/main.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server4/server.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server4/request_parser.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/reply.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/connection.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/reply.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/io_context_pool.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/io_context_pool.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/connection.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server2/server.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server/reply.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server/connection.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server/reply.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server/connection.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/server/server.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/client/sync_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/http/client/async_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/echo/blocking_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/echo/blocking_udp_echo_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/echo/blocking_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/echo/async_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/echo/blocking_tcp_echo_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/echo/async_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/socks4/socks4.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/socks4/sync_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/spawn/parallel_grep.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/spawn/echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/invocation/prioritised_handlers.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/multicast/sender.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/multicast/receiver.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/services/basic_logger.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/services/daytime_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/services/logger_service.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/services/logger_service.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/windows/transmit_file.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime2/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime3/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime5/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime4/client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime7/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/timer5/timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/timer3/timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/timer4/timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/timer2/timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime6/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/timer1/timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime_dox.txt
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/timer_dox.txt
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime1/client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/timers/time_t_timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/allocation/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/buffers/reference_counted.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/ssl/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/ssl/client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/icmp/ping.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/icmp/ipv4_header.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/nonblocking/third_party_lib.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/chat/chat_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/chat/chat_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/chat/posix_chat_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/timeouts/async_tcp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/timeouts/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/timeouts/blocking_udp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/timeouts/blocking_token_tcp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/timeouts/blocking_tcp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/porthopper/protocol.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/porthopper/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/porthopper/client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/fork/daemon.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/fork/process_per_connection.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/local/connect_pair.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/local/iostream_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/local/stream_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/local/stream_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/iostreams/http_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/iostreams/daytime_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp03/iostreams/daytime_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/http/server/reply.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/http/server/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/http/server/connection.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/http/server/reply.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/http/server/connection.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/http/server/server.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/echo/blocking_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/echo/blocking_udp_echo_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/echo/blocking_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/echo/async_udp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/echo/blocking_tcp_echo_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/echo/async_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/executors/priority_scheduler.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/executors/actor.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/executors/bank_account_1.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/executors/pipeline.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/executors/bank_account_2.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/executors/fork_join.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/socks4/socks4.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/socks4/sync_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/spawn/parallel_grep.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/spawn/echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/futures/daytime_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/invocation/prioritised_handlers.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/multicast/sender.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/multicast/receiver.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/timers/time_t_timer.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/allocation/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/buffers/reference_counted.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/ssl/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/ssl/client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/nonblocking/third_party_lib.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/chat/chat_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/chat/chat_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/operations/composed_1.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/operations/composed_3.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/operations/composed_5.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/operations/composed_4.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/operations/composed_2.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/timeouts/async_tcp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/timeouts/server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/timeouts/blocking_udp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/timeouts/blocking_token_tcp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/timeouts/blocking_tcp_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/fork/daemon.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/fork/process_per_connection.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/local/connect_pair.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/local/iostream_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/local/stream_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/local/stream_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/handler_tracking/async_tcp_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/handler_tracking/custom_tracking.hpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp11/iostreams/http_client.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/range_based_for.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/chat_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/refactored_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/double_buffered_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/coroutine2/doc/coro.qbk
/home/vboxuser/boost_1_69_0/libs/coroutine2/doc/motivation.qbk
/home/vboxuser/boost_1_69_0/libs/phoenix/example/adapted_echo_server.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/doc/http_snippets.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/doc/http_examples.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/doc/core_snippets.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/doc/websocket_snippets.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/doc/core_examples.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/doc/exemplars.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/bench/parser/bench_parser.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/bench/parser/nodejs_parser.hpp
/home/vboxuser/boost_1_69_0/libs/beast/test/bench/wsload/wsload.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/bench/buffers/bench_buffers.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/buffers_cat.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/type_traits.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/flat_buffer.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/buffer_test.hpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/static_buffer.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/flat_static_buffer.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/multi_buffer.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/buffer.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/bind_handler.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/buffered_read_stream.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/buffers_suffix.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/read_size.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/buffers_adapter.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/core/buffers_prefix.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/file_body.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/write.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/dynamic_body.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/basic_parser.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/serializer.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/parser.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/test_parser.hpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/message_fuzz.hpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/span_body.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/read.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/http/chunk_encode.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/read2.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/write.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/read1.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/accept.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/ping.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/utf8_checker.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/close.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/handshake.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/test.hpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/doc_snippets.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/websocket/stream.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/experimental/timeout_service.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/experimental/icy_stream.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/experimental/timeout_socket.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/beast/experimental/flat_stream.cpp
/home/vboxuser/boost_1_69_0/libs/beast/test/extras/include/boost/beast/test/yield_to.hpp
/home/vboxuser/boost_1_69_0/libs/beast/test/extras/include/boost/beast/test/sig_wait.hpp
/home/vboxuser/boost_1_69_0/libs/beast/test/extras/include/boost/beast/test/websocket.hpp
/home/vboxuser/boost_1_69_0/libs/beast/doc/docca/include/docca/doxygen.xsl
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/ref/boost__beast__websocket__async_teardown/overload3.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/ref/boost__beast__websocket__async_teardown/overload1.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/ref/boost__beast__websocket__async_teardown/overload2.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/ref/boost__beast__http__error.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/ref/boost__beast__basic_timeout_socket/async_write_some.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/ref/boost__beast__basic_timeout_socket/async_read_some.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/more_examples/expect_100_continue_server.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/using_io/example_detect_ssl.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/html/beast/using_io/writing_composed_operations.html
/home/vboxuser/boost_1_69_0/libs/beast/doc/qbk/03_core/1_asio.qbk
/home/vboxuser/boost_1_69_0/libs/beast/doc/qbk/07_concepts/Streams.qbk
/home/vboxuser/boost_1_69_0/libs/beast/doc/qbk/07_concepts/DynamicBuffer.qbk
/home/vboxuser/boost_1_69_0/libs/beast/doc/qbk/reference.qbk
/home/vboxuser/boost_1_69_0/libs/beast/doc/qbk/08_design/4_faq.qbk
/home/vboxuser/boost_1_69_0/libs/beast/doc/qbk/08_design/3_websocket_zaphoyd.qbk
/home/vboxuser/boost_1_69_0/libs/beast/doc/qbk/00_main.qbk
/home/vboxuser/boost_1_69_0/libs/beast/example/echo-op/echo_op.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/async-ssl/http_server_async_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/sync-ssl/http_server_sync_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/small/http_server_small.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/fast/http_server_fast.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/async/http_server_async.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/coro/http_server_coro.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/flex/http_server_flex.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/sync/http_server_sync.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/stackless-ssl/http_server_stackless_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/stackless/http_server_stackless.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/server/coro-ssl/http_server_coro_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/client/async-ssl/http_client_async_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/client/sync-ssl/http_client_sync_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/client/crawl/http_crawl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/client/async/http_client_async.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/client/coro/http_client_coro.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/client/sync/http_client_sync.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/http/client/coro-ssl/http_client_coro_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/doc/http_examples.hpp
/home/vboxuser/boost_1_69_0/libs/beast/example/common/detect_ssl.hpp
/home/vboxuser/boost_1_69_0/libs/beast/example/common/server_certificate.hpp
/home/vboxuser/boost_1_69_0/libs/beast/example/common/root_certificates.hpp
/home/vboxuser/boost_1_69_0/libs/beast/example/common/session_alloc.hpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/async-ssl/websocket_server_async_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/sync-ssl/websocket_server_sync_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/fast/websocket_server_fast.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/async/websocket_server_async.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/coro/websocket_server_coro.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/sync/websocket_server_sync.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/stackless-ssl/websocket_server_stackless_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/stackless/websocket_server_stackless.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/server/coro-ssl/websocket_server_coro_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/client/async-ssl/websocket_client_async_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/client/sync-ssl/websocket_client_sync_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/client/async/websocket_client_async.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/client/coro/websocket_client_coro.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/client/sync/websocket_client_sync.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/websocket/client/coro-ssl/websocket_client_coro_ssl.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/cppcon2018/net.hpp
/home/vboxuser/boost_1_69_0/libs/beast/example/advanced/server-flex/advanced_server_flex.cpp
/home/vboxuser/boost_1_69_0/libs/beast/example/advanced/server/advanced_server.cpp
/home/vboxuser/boost_1_69_0/libs/beast/CHANGELOG.md
/home/vboxuser/boost_1_69_0/libs/coroutine/doc/html/coroutine/motivation.html
/home/vboxuser/boost_1_69_0/libs/coroutine/doc/coro.qbk
/home/vboxuser/boost_1_69_0/libs/coroutine/doc/motivation.qbk
/home/vboxuser/boost_1_69_0/libs/log/doc/tmp/sinks_reference.xml
/home/vboxuser/boost_1_69_0/libs/log/src/syslog_backend.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/system_test2.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_fut.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/spawn_fail.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/bind_stderr.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/on_exit.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/exit_code.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/bind_stdout.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/bind_stdout_stderr.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_system_stackful_except.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_system_fail.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_system_future.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/bind_stdin.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/spawn.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_system_stackful_error.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/wait.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/system_test1.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/on_exit2.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_pipe.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/on_exit3.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_system_stackless.cpp
/home/vboxuser/boost_1_69_0/libs/process/test/async_system_stackful.cpp
/home/vboxuser/boost_1_69_0/libs/process/doc/tutorial.qbk
/home/vboxuser/boost_1_69_0/libs/process/doc/extend.qbk
/home/vboxuser/boost_1_69_0/libs/process/doc/autodoc.xml
/home/vboxuser/boost_1_69_0/libs/process/example/io.cpp
/home/vboxuser/boost_1_69_0/libs/process/example/wait.cpp
/home/vboxuser/boost_1_69_0/libs/process/example/async_io.cpp
```

</details>

8. Скомпилирутйе *boost*. Можно воспользоваться [инструкцией](https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html#or-build-custom-binaries) или [ссылкой](https://codeyarns.com/2017/01/24/how-to-build-boost-on-linux/)
<details>
<summary>Компиляция</summary>

```bash
Performing configuration checks

    - default address-model    : 64-bit (cached)
    - default architecture     : x86 (cached)
    - C++11 mutex              : yes (cached)
    - lockfree boost::atomic_flag : yes (cached)
    - Boost.Config Feature Check: cxx11_auto_declarations : yes (cached)
    - Boost.Config Feature Check: cxx11_constexpr : yes (cached)
    - Boost.Config Feature Check: cxx11_defaulted_functions : yes (cached)
    - Boost.Config Feature Check: cxx11_final : yes (cached)
    - Boost.Config Feature Check: cxx11_hdr_mutex : yes (cached)
    - Boost.Config Feature Check: cxx11_hdr_tuple : yes (cached)
    - Boost.Config Feature Check: cxx11_lambdas : yes (cached)
    - Boost.Config Feature Check: cxx11_noexcept : yes (cached)
    - Boost.Config Feature Check: cxx11_nullptr : yes (cached)
    - Boost.Config Feature Check: cxx11_rvalue_references : yes (cached)
    - Boost.Config Feature Check: cxx11_template_aliases : yes (cached)
    - Boost.Config Feature Check: cxx11_thread_local : yes (cached)
    - Boost.Config Feature Check: cxx11_variadic_templates : yes (cached)
    - has_icu builds           : yes (cached)
warning: Graph library does not contain MPI-based parallel components.
note: to enable them, add "using mpi ;" to your user-config.jam
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - iconv (libc)             : yes (cached)
    - icu                      : yes (cached)
warning: non-free usage requirements <runtime-link>shared ignored
warning: in main-target build_options at libs/locale/build/Jamfile.v2:414
warning: non-free usage requirements <runtime-link>shared ignored
warning: in main-target build_flags at libs/locale/build/Jamfile.v2:415
    - native-atomic-int32-supported : yes (cached)
    - native-syslog-supported  : yes (cached)
    - pthread-supports-robust-mutexes : yes (cached)
    - compiler-supports-ssse3  : yes (cached)
    - compiler-supports-avx2   : yes (cached)
    - gcc visibility           : yes (cached)
    - long double support      : yes (cached)
warning: skipping optional Message Passing Interface (MPI) library.
note: to enable MPI support, add "using mpi ;" to user-config.jam.
note: to suppress this message, pass "--without-mpi" to bjam.
note: otherwise, you can safely ignore this message.
    - libbacktrace builds      : yes (cached)
    - addr2line builds         : yes (cached)
    - WinDbg builds            : no  (cached)
    - WinDbgCached builds      : no  (cached)
    - BOOST_COMP_GNUC >= 4.3.0 : no  (cached)
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)

Component configuration:

    - atomic                   : building
    - chrono                   : building
    - container                : building
    - context                  : building
    - contract                 : building
    - coroutine                : building
    - date_time                : building
    - exception                : building
    - fiber                    : building
    - filesystem               : building
    - graph                    : building
    - graph_parallel           : building
    - iostreams                : building
    - locale                   : building
    - log                      : building
    - math                     : building
    - mpi                      : building
    - program_options          : building
    - python                   : building
    - random                   : building
    - regex                    : building
    - serialization            : building
    - stacktrace               : building
    - system                   : building
    - test                     : building
    - thread                   : building
    - timer                    : building
    - type_erasure             : building
    - wave                     : building

...patience...
...patience...
...patience...
...patience...
...patience...
...patience...
...found 43481 targets...
...updating 409 targets...
gcc.compile.c++ bin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/pthread/thread.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/ios_base.h:39,
                 from /usr/include/c++/14/ios:44,
                 from /usr/include/c++/14/ostream:40,
                 from ./boost/system/error_code.hpp:17,
                 from ./boost/system/system_error.hpp:11,
                 from ./boost/thread/exceptions.hpp:22,
                 from ./boost/thread/pthread/thread_data.hpp:10,
                 from ./boost/thread/thread_only.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:11:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from ./boost/thread/exceptions.hpp:20:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
In file included from ./boost/concept/assert.hpp:35,
                 from ./boost/concept_check.hpp:20,
                 from ./boost/range/concepts.hpp:19,
                 from ./boost/range/size_type.hpp:20,
                 from ./boost/range/size.hpp:21,
                 from ./boost/range/functions.hpp:20,
                 from ./boost/range/iterator_range_core.hpp:38,
                 from ./boost/algorithm/string/iter_find.hpp:19,
                 from ./boost/algorithm/string/split.hpp:16,
                 from libs/thread/src/pthread/thread.cpp:34:
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::constraint<Model>::failed() [with Model = boost::algorithm::FinderConcept<boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/algorithm/string/iter_find.hpp:77:13:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp:47:52: warning: ‘this’ pointer is null [-Wnonnull]
   47 |     static void failed() { ((Model*)0)->constraints(); }
      |                            ~~~~~~~~~~~~~~~~~~~~~~~~^~
In file included from ./boost/algorithm/string/iter_find.hpp:26:
./boost/algorithm/string/concept.hpp:40:18: note: in a call to non-static member function ‘void boost::algorithm::FinderConcept<FinderT, IteratorT>::constraints() [with FinderT = boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >; IteratorT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   40 |             void constraints()
      |                  ^~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept_check.hpp:167:5:   required from ‘struct boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/range/concepts.hpp:125:16:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
  125 |         struct IncrementableIteratorConcept : CopyConstructible<Iterator>
      |                ^~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
    885 |       return_prefix iterator_core_access::base_op(                              \
      |                     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  886 |           *static_cast<Derived1 const*>(&lhs)                                   \
      |           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  887 |         , *static_cast<Derived2 const*>(&rhs)                                   \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  888 |         , BOOST_ITERATOR_CONVERTIBLE(Derived2,Derived1)                         \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  889 |       );                                                                        \
      |       ~                                           
/usr/include/c++/14/bits/stl_vector.h:1673:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
 1673 |             for (; __first != __last; ++__first)
      |                    ~~~~~~~~^~~~~~~~~
/usr/include/c++/14/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
  711 |           _M_range_initialize(__first, __last,
      |           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~
  712 |                               std::__iterator_category(__first));
      |                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
  178 |             SequenceSequenceT Tmp(itBegin, itEnd);
      |                               ^~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::CopyConstructible<TT>::~CopyConstructible() [with TT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:167:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  167 |     BOOST_CONCEPT_USAGE(CopyConstructible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >]’
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’
   32 |   inline yes has_constraints_(Model*, wrap_constraints<Model,&Model::constraints>* = 0);
      |                                                              ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >::value’
   44 |       , value = sizeof( detail::has_constraints_((Model*)0) ) == sizeof(detail::yes) );
      |                       ~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >’
   45 |     typedef boost::integral_constant<bool, value> type;
      |                                                   ^~~~
./boost/concept/detail/general.hpp:51:8:   [ skipping 19 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
  885 |       return_prefix iterator_core_access::base_op(                              \
      |                     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  886 |           *static_cast<Derived1 const*>(&lhs)                                   \
      |           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  887 |         , *static_cast<Derived2 const*>(&rhs)                                   \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  888 |         , BOOST_ITERATOR_CONVERTIBLE(Derived2,Derived1)                         \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  889 |       );                                                                        \
      |       ~                                           
/usr/include/c++/14/bits/stl_vector.h:1673:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
 1673 |             for (; __first != __last; ++__first)
      |                    ~~~~~~~~^~~~~~~~~
/usr/include/c++/14/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
  711 |           _M_range_initialize(__first, __last,
      |           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~
  712 |                               std::__iterator_category(__first));
      |                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
  178 |             SequenceSequenceT Tmp(itBegin, itEnd);
      |                               ^~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::incrementable_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/range/concepts.hpp:136:13:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
  147 |         struct SinglePassIteratorConcept
      |                ^~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   32 |   inline yes has_constraints_(Model*, wrap_constraints<Model,&Model::constraints>* = 0);
      |                                                              ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
   44 |       , value = sizeof( detail::has_constraints_((Model*)0) ) == sizeof(detail::yes) );
      |                       ~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
  885 |       return_prefix iterator_core_access::base_op(                              \
      |                     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  886 |           *static_cast<Derived1 const*>(&lhs)                                   \
      |           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  887 |         , *static_cast<Derived2 const*>(&rhs)                                   \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  888 |         , BOOST_ITERATOR_CONVERTIBLE(Derived2,Derived1)                         \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  889 |       );                                                                        \
      |       ~                                           
/usr/include/c++/14/bits/stl_vector.h:1673:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
 1673 |             for (; __first != __last; ++__first)
      |                    ~~~~~~~~^~~~~~~~~
/usr/include/c++/14/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
  711 |           _M_range_initialize(__first, __last,
      |           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~
  712 |                               std::__iterator_category(__first));
      |                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
  178 |             SequenceSequenceT Tmp(itBegin, itEnd);
      |                               ^~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::IncrementableIteratorConcept<Iterator>::~IncrementableIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:136:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  136 |             BOOST_CONCEPT_USAGE(IncrementableIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept_check.hpp:233:5:   required from ‘struct boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
  147 |         struct SinglePassIteratorConcept
      |                ^~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   32 |   inline yes has_constraints_(Model*, wrap_constraints<Model,&Model::constraints>* = 0);
      |                                                              ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
   44 |       , value = sizeof( detail::has_constraints_((Model*)0) ) == sizeof(detail::yes) );
      |                       ~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
  885 |       return_prefix iterator_core_access::base_op(                              \
      |                     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  886 |           *static_cast<Derived1 const*>(&lhs)                                   \
      |           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  887 |         , *static_cast<Derived2 const*>(&rhs)                                   \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  888 |         , BOOST_ITERATOR_CONVERTIBLE(Derived2,Derived1)                         \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  889 |       );                                                                        \
      |       ~                                           
/usr/include/c++/14/bits/stl_vector.h:1673:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
 1673 |             for (; __first != __last; ++__first)
      |                    ~~~~~~~~^~~~~~~~~
/usr/include/c++/14/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
  711 |           _M_range_initialize(__first, __last,
      |           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~
  712 |                               std::__iterator_category(__first));
      |                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
  178 |             SequenceSequenceT Tmp(itBegin, itEnd);
      |                               ^~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::EqualityComparable<TT>::~EqualityComparable() [with TT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:233:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  233 |     BOOST_CONCEPT_USAGE(EqualityComparable) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >]’
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’
   32 |   inline yes has_constraints_(Model*, wrap_constraints<Model,&Model::constraints>* = 0);
      |                                                              ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >::value’
   44 |       , value = sizeof( detail::has_constraints_((Model*)0) ) == sizeof(detail::yes) );
      |                       ~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >’
   45 |     typedef boost::integral_constant<bool, value> type;
      |                                                   ^~~~
./boost/concept/detail/general.hpp:51:8:   [ skipping 18 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
  885 |       return_prefix iterator_core_access::base_op(                              \
      |                     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  886 |           *static_cast<Derived1 const*>(&lhs)                                   \
      |           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  887 |         , *static_cast<Derived2 const*>(&rhs)                                   \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  888 |         , BOOST_ITERATOR_CONVERTIBLE(Derived2,Derived1)                         \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  889 |       );                                                                        \
      |       ~                                           
/usr/include/c++/14/bits/stl_vector.h:1673:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
 1673 |             for (; __first != __last; ++__first)
      |                    ~~~~~~~~^~~~~~~~~
/usr/include/c++/14/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
  711 |           _M_range_initialize(__first, __last,
      |           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~
  712 |                               std::__iterator_category(__first));
      |                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
  178 |             SequenceSequenceT Tmp(itBegin, itEnd);
      |                               ^~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::single_pass_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/range/concepts.hpp:158:13:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   32 |   inline yes has_constraints_(Model*, wrap_constraints<Model,&Model::constraints>* = 0);
      |                                                              ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
   44 |       , value = sizeof( detail::has_constraints_((Model*)0) ) == sizeof(detail::yes) );
      |                       ~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
   45 |     typedef boost::integral_constant<bool, value> type;
      |                                                   ^~~~
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
  885 |       return_prefix iterator_core_access::base_op(                              \
      |                     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  886 |           *static_cast<Derived1 const*>(&lhs)                                   \
      |           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  887 |         , *static_cast<Derived2 const*>(&rhs)                                   \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  888 |         , BOOST_ITERATOR_CONVERTIBLE(Derived2,Derived1)                         \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  889 |       );                                                                        \
      |       ~                                           
/usr/include/c++/14/bits/stl_vector.h:1673:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
 1673 |             for (; __first != __last; ++__first)
      |                    ~~~~~~~~^~~~~~~~~
/usr/include/c++/14/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
  711 |           _M_range_initialize(__first, __last,
      |           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~
  712 |                               std::__iterator_category(__first));
      |                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
  178 |             SequenceSequenceT Tmp(itBegin, itEnd);
      |                               ^~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::SinglePassIteratorConcept<Iterator>::~SinglePassIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:158:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  158 |             BOOST_CONCEPT_USAGE(SinglePassIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >]’
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/range/concepts.hpp:284:9:   required from ‘struct boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
   32 |   inline yes has_constraints_(Model*, wrap_constraints<Model,&Model::constraints>* = 0);
      |                                                              ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >::value’
   44 |       , value = sizeof( detail::has_constraints_((Model*)0) ) == sizeof(detail::yes) );
      |                       ~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >’
   45 |     typedef boost::integral_constant<bool, value> type;
      |                                                   ^~~~
./boost/concept/detail/general.hpp:51:8:   [ skipping 8 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
  885 |       return_prefix iterator_core_access::base_op(                              \
      |                     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  886 |           *static_cast<Derived1 const*>(&lhs)                                   \
      |           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  887 |         , *static_cast<Derived2 const*>(&rhs)                                   \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  888 |         , BOOST_ITERATOR_CONVERTIBLE(Derived2,Derived1)                         \
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  889 |       );                                                                        \
      |       ~                                           
/usr/include/c++/14/bits/stl_vector.h:1673:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
 1673 |             for (; __first != __last; ++__first)
      |                    ~~~~~~~~^~~~~~~~~
/usr/include/c++/14/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
  711 |           _M_range_initialize(__first, __last,
      |           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~
  712 |                               std::__iterator_category(__first));
      |                               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
  178 |             SequenceSequenceT Tmp(itBegin, itEnd);
      |                               ^~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::SinglePassRangeConcept<T>::~SinglePassRangeConcept() [with T = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:284:9: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  284 |         BOOST_CONCEPT_USAGE(SinglePassRangeConcept)
      |         ^~~~~~~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -pedantic -fvisibility=hidden -Wextra -Wno-long-long -Wno-unused-parameter -Wunused-function -pedantic -DBOOST_ALL_NO_LIB=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_DONT_USE_CHRONO -DBOOST_THREAD_POSIX -DNDEBUG  -I"." -c -o "bin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/pthread/thread.o" "libs/thread/src/pthread/thread.cpp"

...failed gcc.compile.c++ bin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/pthread/thread.o...
...skipped <pbin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_thread.a(clean) for lack of <pbin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>pthread/thread.o...
...skipped <pbin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_thread.a for lack of <pbin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>pthread/thread.o...
...skipped <pboost_output/lib>libboost_thread.a for lack of <pbin.v2/libs/thread/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_thread.a...
gcc.compile.c++ bin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/posix/stack_traits.o
In file included from ./boost/coroutine/stack_traits.hpp:14,
                 from libs/coroutine/src/posix/stack_traits.cpp:7:
./boost/coroutine/detail/config.hpp:17:4: warning: #warning "Boost.Coroutine is now deprecated. Please switch to Boost.Coroutine2. To disable this warning message, define BOOST_COROUTINES_NO_DEPRECATION_WARNING." [-Wcpp]
   17 | #  warning                  "Boost.Coroutine is now deprecated. Please switch to Boost.Coroutine2. To disable this warning message, define BOOST_COROUTINES_NO_DEPRECATION_WARNING."
      |    ^~~~~~~
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/ios_base.h:39,
                 from /usr/include/c++/14/ios:44,
                 from /usr/include/c++/14/ostream:40,
                 from ./boost/system/error_code.hpp:17,
                 from ./boost/system/system_error.hpp:11,
                 from ./boost/thread/exceptions.hpp:22,
                 from ./boost/thread/pthread/thread_data.hpp:10,
                 from ./boost/thread/thread_only.hpp:17,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/coroutine/src/posix/stack_traits.cpp:22:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from ./boost/thread/exceptions.hpp:20:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_COROUTINES_SOURCE -DBOOST_DISABLE_ASSERTS -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DNDEBUG  -I"." -c -o "bin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/posix/stack_traits.o" "libs/coroutine/src/posix/stack_traits.cpp"

...failed gcc.compile.c++ bin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/posix/stack_traits.o...
...skipped <pbin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_coroutine.a(clean) for lack of <pbin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>posix/stack_traits.o...
...skipped <pbin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_coroutine.a for lack of <pbin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>posix/stack_traits.o...
...skipped <pboost_output/lib>libboost_coroutine.a for lack of <pbin.v2/libs/coroutine/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_coroutine.a...
gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/collator.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/locale_classes.h:41,
                 from /usr/include/c++/14/locale:41,
                 from ./boost/locale/collator.hpp:16,
                 from libs/locale/src/icu/collator.cpp:9:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/collator.cpp:11:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from /usr/include/c++/14/bits/locale_classes.h:40:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_LOCALE_NO_WINAPI_BACKEND=1 -DBOOST_LOCALE_WITH_ICONV=1 -DBOOST_LOCALE_WITH_ICU=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_NO_LIB=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DNDEBUG  -I"." -c -o "bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/collator.o" "libs/locale/src/icu/collator.cpp"

...failed gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/collator.o...
gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/date_time.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/locale_classes.h:41,
                 from /usr/include/c++/14/locale:41,
                 from ./boost/locale/date_time_facet.hpp:18,
                 from libs/locale/src/icu/date_time.cpp:9:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/date_time.cpp:15:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from /usr/include/c++/14/bits/locale_classes.h:40:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_LOCALE_NO_WINAPI_BACKEND=1 -DBOOST_LOCALE_WITH_ICONV=1 -DBOOST_LOCALE_WITH_ICU=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_NO_LIB=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DNDEBUG  -I"." -c -o "bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/date_time.o" "libs/locale/src/icu/date_time.cpp"

...failed gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/date_time.o...
gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/formatter.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/ios_base.h:39,
                 from /usr/include/c++/14/ios:44,
                 from /usr/include/c++/14/ostream:40,
                 from ./boost/locale/formatting.hpp:18,
                 from libs/locale/src/icu/formatter.cpp:9:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/predefined_formatters.hpp:14,
                 from libs/locale/src/icu/formatter.cpp:25:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from ./boost/locale/time_zone.hpp:17,
                 from ./boost/locale/formatting.hpp:17:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
libs/locale/src/icu/formatter.cpp: In constructor ‘boost::locale::impl_icu::{anonymous}::init::init()’:
libs/locale/src/icu/formatter.cpp:41:72: warning: ignoring return value of ‘bool std::has_facet(const locale&) [with _Facet = boost::locale::impl_icu::icu_formatters_cache]’, declared with attribute ‘nodiscard’ [-Wunused-result]
   41 |             struct init { init() { std::has_facet<icu_formatters_cache>(std::locale::classic()); } } instance;
      |                                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~
In file included from /usr/include/c++/14/bits/locale_classes.h:888,
                 from /usr/include/c++/14/bits/ios_base.h:41:
/usr/include/c++/14/bits/locale_classes.tcc:167:5: note: declared here
  167 |     has_facet(const locale& __loc) throw()
      |     ^~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_LOCALE_NO_WINAPI_BACKEND=1 -DBOOST_LOCALE_WITH_ICONV=1 -DBOOST_LOCALE_WITH_ICU=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_NO_LIB=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DNDEBUG  -I"." -c -o "bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/formatter.o" "libs/locale/src/icu/formatter.cpp"

...failed gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/formatter.o...
gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/numeric.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/locale_classes.h:41,
                 from /usr/include/c++/14/locale:41,
                 from libs/locale/src/icu/numeric.cpp:9:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/predefined_formatters.hpp:14,
                 from libs/locale/src/icu/numeric.cpp:19:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from /usr/include/c++/14/bits/locale_classes.h:40:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_LOCALE_NO_WINAPI_BACKEND=1 -DBOOST_LOCALE_WITH_ICONV=1 -DBOOST_LOCALE_WITH_ICU=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_NO_LIB=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DNDEBUG  -I"." -c -o "bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/numeric.o" "libs/locale/src/icu/numeric.cpp"

...failed gcc.compile.c++ bin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/numeric.o...
...skipped <pbin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_locale.a(clean) for lack of <pbin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>icu/collator.o...
...skipped <pbin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_locale.a for lack of <pbin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>icu/collator.o...
...skipped <pboost_output/lib>libboost_locale.a for lack of <pbin.v2/libs/locale/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_locale.a...
gcc.compile.c++ bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/severity_level.o
In file included from /usr/include/x86_64-linux-gnu/bits/local_lim.h:81,
                 from /usr/include/x86_64-linux-gnu/bits/posix1_lim.h:161,
                 from /usr/include/limits.h:195,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/limits.h:210,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/limits.h:34,
                 from ./boost/log/detail/config.hpp:33,
                 from libs/log/src/severity_level.cpp:16:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from libs/log/src/severity_level.cpp:23:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/functional:49,
                 from ./boost/config/no_tr1/functional.hpp:21,
                 from ./boost/smart_ptr/intrusive_ptr.hpp:24,
                 from ./boost/log/sources/severity_feature.hpp:20,
                 from libs/log/src/severity_level.cpp:18:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden -fno-strict-aliasing -ftemplate-depth-1024 -DBOOST_ALL_NO_LIB=1 -DBOOST_ATOMIC_STATIC_LINK=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_FILESYSTEM_STATIC_LINK=1 -DBOOST_HAS_ICU=1 -DBOOST_LOG_BUILDING_THE_LIB=1 -DBOOST_LOG_HAS_PTHREAD_MUTEX_ROBUST -DBOOST_LOG_USE_AVX2 -DBOOST_LOG_USE_NATIVE_SYSLOG -DBOOST_LOG_USE_SSSE3 -DBOOST_LOG_WITHOUT_DEBUG_OUTPUT -DBOOST_LOG_WITHOUT_EVENT_LOG -DBOOST_SPIRIT_USE_PHOENIX_V3=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_DONT_USE_CHRONO=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DDATE_TIME_INLINE -DNDEBUG -D_XOPEN_SOURCE=600 -D__STDC_CONSTANT_MACROS  -I"." -I"/usr/include" -I"libs/log/src" -c -o "bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/severity_level.o" "libs/log/src/severity_level.cpp"

...failed gcc.compile.c++ bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/severity_level.o...
gcc.compile.c++ bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/event.o
In file included from /usr/include/x86_64-linux-gnu/bits/local_lim.h:81,
                 from /usr/include/x86_64-linux-gnu/bits/posix1_lim.h:161,
                 from /usr/include/limits.h:195,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/limits.h:210,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/limits.h:34,
                 from ./boost/log/detail/config.hpp:33,
                 from libs/log/src/event.cpp:16:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden -fno-strict-aliasing -ftemplate-depth-1024 -DBOOST_ALL_NO_LIB=1 -DBOOST_ATOMIC_STATIC_LINK=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_FILESYSTEM_STATIC_LINK=1 -DBOOST_HAS_ICU=1 -DBOOST_LOG_BUILDING_THE_LIB=1 -DBOOST_LOG_HAS_PTHREAD_MUTEX_ROBUST -DBOOST_LOG_USE_AVX2 -DBOOST_LOG_USE_NATIVE_SYSLOG -DBOOST_LOG_USE_SSSE3 -DBOOST_LOG_WITHOUT_DEBUG_OUTPUT -DBOOST_LOG_WITHOUT_EVENT_LOG -DBOOST_SPIRIT_USE_PHOENIX_V3=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_DONT_USE_CHRONO=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DDATE_TIME_INLINE -DNDEBUG -D_XOPEN_SOURCE=600 -D__STDC_CONSTANT_MACROS  -I"." -I"/usr/include" -I"libs/log/src" -c -o "bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/event.o" "libs/log/src/event.cpp"

...failed gcc.compile.c++ bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/event.o...
...skipped <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_log.a(clean) for lack of <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>severity_level.o...
...skipped <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_log.a for lack of <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>severity_level.o...
...skipped <pboost_output/lib>libboost_log.a for lack of <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_log.a...
gcc.compile.c++ bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/setup/init_from_settings.o
In file included from /usr/include/x86_64-linux-gnu/bits/local_lim.h:81,
                 from /usr/include/x86_64-linux-gnu/bits/posix1_lim.h:161,
                 from /usr/include/limits.h:195,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/limits.h:210,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/14/include/limits.h:34,
                 from ./boost/log/detail/config.hpp:33,
                 from ./boost/log/detail/setup_config.hpp:20,
                 from libs/log/src/setup/init_from_settings.cpp:26:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/log/sinks/async_frontend.hpp:39,
                 from ./boost/log/sinks.hpp:25,
                 from libs/log/src/setup/init_from_settings.cpp:54:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from /usr/include/c++/14/bits/locale_classes.h:40,
                 from /usr/include/c++/14/bits/ios_base.h:41,
                 from /usr/include/c++/14/ios:44,
                 from libs/log/src/setup/init_from_settings.cpp:28:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden -fno-strict-aliasing -ftemplate-depth-1024 -DBOOST_ALL_NO_LIB=1 -DBOOST_ATOMIC_STATIC_LINK=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_FILESYSTEM_STATIC_LINK=1 -DBOOST_HAS_ICU=1 -DBOOST_LOG_HAS_PTHREAD_MUTEX_ROBUST -DBOOST_LOG_SETUP_BUILDING_THE_LIB=1 -DBOOST_LOG_USE_AVX2 -DBOOST_LOG_USE_NATIVE_SYSLOG -DBOOST_LOG_USE_SSSE3 -DBOOST_LOG_WITHOUT_EVENT_LOG -DBOOST_SPIRIT_USE_PHOENIX_V3=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_DONT_USE_CHRONO=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DDATE_TIME_INLINE -DNDEBUG -D_XOPEN_SOURCE=600 -D__STDC_CONSTANT_MACROS  -I"." -I"/usr/include" -I"libs/log/src" -c -o "bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/setup/init_from_settings.o" "libs/log/src/setup/init_from_settings.cpp"

...failed gcc.compile.c++ bin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/setup/init_from_settings.o...
...skipped <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_log_setup.a(clean) for lack of <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>setup/init_from_settings.o...
...skipped <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_log_setup.a for lack of <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>setup/init_from_settings.o...
...skipped <pboost_output/lib>libboost_log_setup.a for lack of <pbin.v2/libs/log/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_log_setup.a...
gcc.compile.c++.pch bin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden/../src/tr1/pch.hpp.gch
In file included from ./boost/cstdfloat.hpp:22,
                 from ./boost/math/tools/test_value.hpp:29,
                 from ./boost/math/special_functions/lambert_w.hpp:64,
                 from ./boost/math/special_functions.hpp:73,
                 from libs/math/build/../src/tr1/pch.hpp:9:
./boost/math/cstdfloat/cstdfloat_limits.hpp:35:13: error: redefinition of ‘class std::numeric_limits<__float128>’
   35 |       class numeric_limits<boost::math::cstdfloat::detail::float_internal128_t>
      |             ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from ./boost/math/special_functions/airy.hpp:10,
                 from ./boost/math/special_functions.hpp:15:
/usr/include/c++/14/limits:2089:12: note: previous definition of ‘class std::numeric_limits<__float128>’
 2089 |     struct numeric_limits<__float128>
      |            ^~~~~~~~~~~~~~~~~~~~~~~~~~

    "g++" -x c++-header -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden -fvisibility=hidden -DBOOST_ALL_NO_LIB=1 -DBOOST_BUILD_PCH_ENABLED -DNDEBUG -I"." -I"libs/math/src/tr1" -c -o "bin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden/../src/tr1/pch.hpp.gch" "libs/math/build/../src/tr1/pch.hpp"

...failed gcc.compile.c++.pch bin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden/../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_legendre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>beta.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_1.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_2.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_3.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_i.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_j.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_k.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_neumann.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_1.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_2.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_3.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>expint.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>hermite.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>laguerre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>legendre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>riemann_zeta.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_bessel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_legendre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_neumann.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1.a(clean) for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerre.o...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerre.o...
...skipped <pboost_output/lib>libboost_math_tr1.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1.a...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_legendref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>betaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_1f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_2f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_3f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_if.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_jf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_kf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_neumannf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_1f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_2f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_3f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>expintf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>hermitef.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>laguerref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>legendref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>riemann_zetaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_besself.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_legendref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_neumannf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1f.a(clean) for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerref.o...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1f.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerref.o...
...skipped <pboost_output/lib>libboost_math_tr1f.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1f.a...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_legendrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>betal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_1l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_2l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>comp_ellint_3l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_il.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_jl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_bessel_kl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cyl_neumannl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_1l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_2l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>ellint_3l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>expintl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>hermitel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>laguerrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>legendrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>riemann_zetal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_bessell.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_legendrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>sph_neumannl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1l.a(clean) for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerrel.o...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1l.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>assoc_laguerrel.o...
...skipped <pboost_output/lib>libboost_math_tr1l.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_tr1l.a...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acosh.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>asinh.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>atanh.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cbrt.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>copysign.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>erfc.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>erf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>expm1.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fmax.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fmin.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fpclassify.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>hypot.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>lgamma.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>llround.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>log1p.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>lround.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>nextafter.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>nexttoward.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>round.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>tgamma.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>trunc.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99.a(clean) for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acosh.o...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acosh.o...
...skipped <pboost_output/lib>libboost_math_c99.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99.a...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acoshf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>asinhf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>atanhf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cbrtf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>copysignf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>erfcf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>erff.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>expm1f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fmaxf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fminf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fpclassifyf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>hypotf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>lgammaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>llroundf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>log1pf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>lroundf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>nextafterf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>nexttowardf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>roundf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>tgammaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>truncf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99f.a(clean) for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acoshf.o...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99f.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acoshf.o...
...skipped <pboost_output/lib>libboost_math_c99f.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99f.a...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acoshl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>asinhl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>atanhl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>cbrtl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>copysignl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>erfcl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>erfl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>expm1l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fmaxl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fminl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>fpclassifyl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>hypotl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>lgammal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>llroundl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>log1pl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>lroundl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>nextafterl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>nexttowardl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>roundl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>tgammal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>truncl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99l.a(clean) for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acoshl.o...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99l.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>acoshl.o...
...skipped <pboost_output/lib>libboost_math_c99l.a for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/link-static/threading-multi/visibility-hidden>libboost_math_c99l.a...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/list.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/list.hpp:8,
                 from libs/python/src/list.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/list.o" "libs/python/src/list.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/list.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/long.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/long.hpp:8,
                 from libs/python/src/long.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/long.o" "libs/python/src/long.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/long.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/dict.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/dict.hpp:8,
                 from libs/python/src/dict.cpp:4:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/dict.o" "libs/python/src/dict.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/dict.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/tuple.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/tuple.hpp:8,
                 from libs/python/src/tuple.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/tuple.o" "libs/python/src/tuple.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/tuple.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/str.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/str.hpp:8,
                 from libs/python/src/str.cpp:4:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/str.o" "libs/python/src/str.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/str.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/slice.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/slice.hpp:9,
                 from libs/python/src/slice.cpp:1:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/slice.o" "libs/python/src/slice.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/slice.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/from_python.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/converter/from_python.hpp:8,
                 from libs/python/src/converter/from_python.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/from_python.o" "libs/python/src/converter/from_python.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/from_python.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/registry.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/type_id.hpp:8,
                 from ./boost/python/converter/registry.hpp:7,
                 from libs/python/src/converter/registry.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/registry.o" "libs/python/src/converter/registry.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/registry.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/type_id.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/type_id.hpp:8,
                 from libs/python/src/converter/type_id.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/type_id.o" "libs/python/src/converter/type_id.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/type_id.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/enum.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_core.hpp:10,
                 from ./boost/python/object/enum_base.hpp:8,
                 from libs/python/src/object/enum.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/enum.o" "libs/python/src/object/enum.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/enum.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/class.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from libs/python/src/object/class.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/class.o" "libs/python/src/object/class.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/class.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/function.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object/function.hpp:8,
                 from ./boost/python/docstring_options.hpp:8,
                 from libs/python/src/object/function.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/function.o" "libs/python/src/object/function.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/function.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/inheritance.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/type_id.hpp:8,
                 from ./boost/python/object/inheritance.hpp:8,
                 from libs/python/src/object/inheritance.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/inheritance.o" "libs/python/src/object/inheritance.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/inheritance.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/life_support.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object/life_support.hpp:7,
                 from libs/python/src/object/life_support.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/life_support.o" "libs/python/src/object/life_support.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/life_support.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/pickle_support.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/make_function.hpp:8,
                 from libs/python/src/object/pickle_support.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/pickle_support.o" "libs/python/src/object/pickle_support.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/pickle_support.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/errors.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/errors.hpp:12,
                 from libs/python/src/errors.cpp:10:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/errors.o" "libs/python/src/errors.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/errors.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/module.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/scope.hpp:8,
                 from libs/python/src/module.cpp:9:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/module.o" "libs/python/src/module.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/module.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/builtin_converters.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/handle.hpp:8,
                 from libs/python/src/converter/builtin_converters.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/builtin_converters.o" "libs/python/src/converter/builtin_converters.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/builtin_converters.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/arg_to_python_base.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/handle.hpp:8,
                 from ./boost/python/converter/arg_to_python_base.hpp:7,
                 from libs/python/src/converter/arg_to_python_base.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/arg_to_python_base.o" "libs/python/src/converter/arg_to_python_base.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/converter/arg_to_python_base.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/iterator.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_fwd.hpp:8,
                 from ./boost/python/object/iterator_core.hpp:8,
                 from libs/python/src/object/iterator.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/iterator.o" "libs/python/src/object/iterator.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/iterator.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/stl_iterator.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from libs/python/src/object/stl_iterator.cpp:10:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/stl_iterator.o" "libs/python/src/object/stl_iterator.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/stl_iterator.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object_protocol.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_protocol.hpp:8,
                 from libs/python/src/object_protocol.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object_protocol.o" "libs/python/src/object_protocol.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object_protocol.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object_operators.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_operators.hpp:8,
                 from libs/python/src/object_operators.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object_operators.o" "libs/python/src/object_operators.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object_operators.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/wrapper.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/detail/wrapper_base.hpp:7,
                 from ./boost/python/wrapper.hpp:7,
                 from libs/python/src/wrapper.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/wrapper.o" "libs/python/src/wrapper.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/wrapper.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/import.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from ./boost/python/import.hpp:8,
                 from libs/python/src/import.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/import.o" "libs/python/src/import.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/import.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/exec.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from ./boost/python/exec.hpp:8,
                 from libs/python/src/exec.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/exec.o" "libs/python/src/exec.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/exec.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/function_doc_signature.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/converter/registrations.hpp:8,
                 from libs/python/src/object/function_doc_signature.cpp:9:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DBOOST_PYTHON_STATIC_LIB -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/function_doc_signature.o" "libs/python/src/object/function_doc_signature.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden/object/function_doc_signature.o...
...skipped <pbin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden>libboost_python313.a(clean) for lack of <pbin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden>list.o...
...skipped <pbin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden>libboost_python313.a for lack of <pbin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden>list.o...
...skipped <pboost_output/lib>libboost_python313.a for lack of <pbin.v2/libs/python/build/gcc-14.2.0/release/link-static/python-3.13/threading-multi/visibility-hidden>libboost_python313.a...
gcc.compile.c++ bin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/shared_ptr_base.h:61,
                 from /usr/include/c++/14/bits/shared_ptr.h:53,
                 from /usr/include/c++/14/memory:80,
                 from ./boost/config/no_tr1/memory.hpp:21,
                 from ./boost/get_pointer.hpp:14,
                 from ./boost/bind/mem_fn.hpp:25,
                 from ./boost/mem_fn.hpp:22,
                 from ./boost/bind/bind.hpp:26,
                 from ./boost/bind.hpp:22,
                 from ./boost/thread/pthread/shared_mutex.hpp:12,
                 from ./boost/thread/shared_mutex.hpp:28,
                 from libs/type_erasure/src/dynamic_binding.cpp:14:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_CHRONO_STATIC_LINK=1 -DBOOST_SYSTEM_STATIC_LINK=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_LIB=1 -DNDEBUG  -I"." -c -o "bin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o" "libs/type_erasure/src/dynamic_binding.cpp"

...failed gcc.compile.c++ bin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o...
...skipped <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_type_erasure.a(clean) for lack of <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>dynamic_binding.o...
...skipped <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_type_erasure.a for lack of <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>dynamic_binding.o...
...skipped <pboost_output/lib>libboost_type_erasure.a for lack of <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden>libboost_type_erasure.a...
gcc.compile.c++ bin.v2/libs/thread/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden/pthread/thread.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/ios_base.h:39,
                 from /usr/include/c++/14/ios:44,
                 from /usr/include/c++/14/ostream:40,
                 from ./boost/system/error_code.hpp:17,
                 from ./boost/system/system_error.hpp:11,
                 from ./boost/thread/exceptions.hpp:22,
                 from ./boost/thread/pthread/thread_data.hpp:10,
                 from ./boost/thread/thread_only.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:11:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/14/string:49,
                 from ./boost/thread/exceptions.hpp:20:
/usr/include/c++/14/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
In file included from ./boost/concept/assert.hpp:35,
                 from ./boost/concept_check.hpp:20,
                 from ./boost/range/concepts.hpp:19,
                 from ./boost/range/size_type.hpp:20,
                 from ./boost/range/size.hpp:21,
                 from ./boost/range/functions.hpp:20,
                 from ./boost/range/iterator_range_core.hpp:38,
                 from ./boost/algorithm/string/iter_find.hpp:19,
                 from ./boost/algorithm/string/split.hpp:16,
                 from libs/thread/src/pthread/thread.cpp:34:
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::constraint<Model>::failed() [with Model = boost::algorithm::FinderConcept<boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/algorithm/string/iter_find.hpp:77:13:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
   71 |     &::boost::concepts::requirement_<ModelFnPtr>::failed>    \
      |     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
  146 |             return ::boost::algorithm::iter_split(
      |                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^
  147 |                 Result,
      |                 ~~~~~~~                           
  148 |                 Input,
      |                 ~~~~~~                            
  149 |                 ::boost::algorithm::token_finder( Pred, eCompress ) );
      |                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
libs/thread/src/pthread/thread.cpp:537:29:   required from here
  537 |                 boost::split(key_val, line, boost::is_any_of(":"));
      |                 ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp:47:52: warning: ‘this’ pointer is null [-Wnonnull]
   47 |     static void failed() { ((Model*)0)->constraints(); }
      |                            ~~~~~~~~~~~~~~~~~~~~~~~~^~
In file included from ./boost/algorithm/string/iter_find.hpp:26:
./boost/algorithm/string/concept.hpp:40:18: note: in a call to non-static member function ‘void boost::algorithm::FinderConcept<FinderT, IteratorT>::constraints() [with FinderT = boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >; IteratorT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’

    "g++" -x c++-header -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden -fvisibility=hidden -DBOOST_ALL_NO_LIB=1 -DBOOST_BUILD_PCH_ENABLED -DBOOST_MATH_TR1_DYN_LINK=1 -DNDEBUG -I"." -I"libs/math/src/tr1" -c -o "bin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden/../src/tr1/pch.hpp.gch" "libs/math/build/../src/tr1/pch.hpp"

...failed gcc.compile.c++.pch bin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden/../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_laguerre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_legendre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>beta.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_1.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_2.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_3.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_i.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_j.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_k.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_neumann.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_1.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_2.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_3.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>expint.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>hermite.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>laguerre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>legendre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>riemann_zeta.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_bessel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_legendre.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_neumann.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_tr1.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_laguerre.o...
...skipped <pboost_output/lib>libboost_math_tr1.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_tr1.so.1.69.0...
...skipped <pboost_output/lib>libboost_math_tr1.so for lack of <pboost_output/lib>libboost_math_tr1.so.1.69.0...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_laguerref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_legendref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>betaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_1f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_2f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_3f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_if.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_jf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_kf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_neumannf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_1f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_2f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_3f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>expintf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>hermitef.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>laguerref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>legendref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>riemann_zetaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_besself.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_legendref.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_neumannf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_tr1f.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_laguerref.o...
...skipped <pboost_output/lib>libboost_math_tr1f.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_tr1f.so.1.69.0...
...skipped <pboost_output/lib>libboost_math_tr1f.so for lack of <pboost_output/lib>libboost_math_tr1f.so.1.69.0...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_laguerrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_legendrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>betal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_1l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_2l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>comp_ellint_3l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_il.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_jl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_bessel_kl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cyl_neumannl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_1l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_2l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>ellint_3l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>expintl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>hermitel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>laguerrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>legendrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>riemann_zetal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_bessell.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_legendrel.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>sph_neumannl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_tr1l.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>assoc_laguerrel.o...
...skipped <pboost_output/lib>libboost_math_tr1l.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_tr1l.so.1.69.0...
...skipped <pboost_output/lib>libboost_math_tr1l.so for lack of <pboost_output/lib>libboost_math_tr1l.so.1.69.0...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>acosh.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>asinh.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>atanh.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cbrt.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>copysign.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>erfc.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>erf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>expm1.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fmax.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fmin.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fpclassify.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>hypot.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>lgamma.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>llround.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>log1p.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>lround.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>nextafter.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>nexttoward.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>round.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>tgamma.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>trunc.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_c99.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>acosh.o...
...skipped <pboost_output/lib>libboost_math_c99.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_c99.so.1.69.0...
...skipped <pboost_output/lib>libboost_math_c99.so for lack of <pboost_output/lib>libboost_math_c99.so.1.69.0...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>acoshf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>asinhf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>atanhf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cbrtf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>copysignf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>erfcf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>erff.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>expm1f.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fmaxf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fminf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fpclassifyf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>hypotf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>lgammaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>llroundf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>log1pf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>lroundf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>nextafterf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>nexttowardf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>roundf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>tgammaf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>truncf.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_c99f.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>acoshf.o...
...skipped <pboost_output/lib>libboost_math_c99f.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_c99f.so.1.69.0...
...skipped <pboost_output/lib>libboost_math_c99f.so for lack of <pboost_output/lib>libboost_math_c99f.so.1.69.0...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>acoshl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>asinhl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>atanhl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>cbrtl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>copysignl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>erfcl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>erfl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>expm1l.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fmaxl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fminl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>fpclassifyl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>hypotl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>lgammal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>llroundl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>log1pl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>lroundl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>nextafterl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>nexttowardl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>roundl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>tgammal.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>truncl.o for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>../src/tr1/pch.hpp.gch...
...skipped <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_c99l.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>acoshl.o...
...skipped <pboost_output/lib>libboost_math_c99l.so.1.69.0 for lack of <pbin.v2/libs/math/build/gcc-14.2.0/release/threading-multi/visibility-hidden>libboost_math_c99l.so.1.69.0...
...skipped <pboost_output/lib>libboost_math_c99l.so for lack of <pboost_output/lib>libboost_math_c99l.so.1.69.0...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/list.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/list.hpp:8,
                 from libs/python/src/list.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/list.o" "libs/python/src/list.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/list.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/long.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/long.hpp:8,
                 from libs/python/src/long.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/long.o" "libs/python/src/long.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/long.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/dict.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/dict.hpp:8,
                 from libs/python/src/dict.cpp:4:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/dict.o" "libs/python/src/dict.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/dict.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/tuple.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/tuple.hpp:8,
                 from libs/python/src/tuple.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/tuple.o" "libs/python/src/tuple.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/tuple.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/str.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/str.hpp:8,
                 from libs/python/src/str.cpp:4:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/str.o" "libs/python/src/str.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/str.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/slice.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/slice.hpp:9,
                 from libs/python/src/slice.cpp:1:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/slice.o" "libs/python/src/slice.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/slice.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/from_python.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/converter/from_python.hpp:8,
                 from libs/python/src/converter/from_python.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/from_python.o" "libs/python/src/converter/from_python.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/from_python.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/registry.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/type_id.hpp:8,
                 from ./boost/python/converter/registry.hpp:7,
                 from libs/python/src/converter/registry.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/registry.o" "libs/python/src/converter/registry.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/registry.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/type_id.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/type_id.hpp:8,
                 from libs/python/src/converter/type_id.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/type_id.o" "libs/python/src/converter/type_id.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/type_id.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/enum.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_core.hpp:10,
                 from ./boost/python/object/enum_base.hpp:8,
                 from libs/python/src/object/enum.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/enum.o" "libs/python/src/object/enum.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/enum.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/class.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from libs/python/src/object/class.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/class.o" "libs/python/src/object/class.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/class.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/function.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object/function.hpp:8,
                 from ./boost/python/docstring_options.hpp:8,
                 from libs/python/src/object/function.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/function.o" "libs/python/src/object/function.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/function.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/inheritance.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/type_id.hpp:8,
                 from ./boost/python/object/inheritance.hpp:8,
                 from libs/python/src/object/inheritance.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/inheritance.o" "libs/python/src/object/inheritance.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/inheritance.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/life_support.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object/life_support.hpp:7,
                 from libs/python/src/object/life_support.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/life_support.o" "libs/python/src/object/life_support.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/life_support.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/pickle_support.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/make_function.hpp:8,
                 from libs/python/src/object/pickle_support.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/pickle_support.o" "libs/python/src/object/pickle_support.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/pickle_support.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/errors.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/errors.hpp:12,
                 from libs/python/src/errors.cpp:10:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/errors.o" "libs/python/src/errors.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/errors.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/module.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/scope.hpp:8,
                 from libs/python/src/module.cpp:9:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/module.o" "libs/python/src/module.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/module.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/builtin_converters.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/handle.hpp:8,
                 from libs/python/src/converter/builtin_converters.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/builtin_converters.o" "libs/python/src/converter/builtin_converters.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/builtin_converters.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/arg_to_python_base.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/handle.hpp:8,
                 from ./boost/python/converter/arg_to_python_base.hpp:7,
                 from libs/python/src/converter/arg_to_python_base.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/arg_to_python_base.o" "libs/python/src/converter/arg_to_python_base.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/converter/arg_to_python_base.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/iterator.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_fwd.hpp:8,
                 from ./boost/python/object/iterator_core.hpp:8,
                 from libs/python/src/object/iterator.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/iterator.o" "libs/python/src/object/iterator.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/iterator.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/stl_iterator.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from libs/python/src/object/stl_iterator.cpp:10:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/stl_iterator.o" "libs/python/src/object/stl_iterator.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/stl_iterator.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object_protocol.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_protocol.hpp:8,
                 from libs/python/src/object_protocol.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object_protocol.o" "libs/python/src/object_protocol.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object_protocol.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object_operators.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/object_operators.hpp:8,
                 from libs/python/src/object_operators.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object_operators.o" "libs/python/src/object_operators.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object_operators.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/wrapper.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/detail/wrapper_base.hpp:7,
                 from ./boost/python/wrapper.hpp:7,
                 from libs/python/src/wrapper.cpp:5:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/wrapper.o" "libs/python/src/wrapper.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/wrapper.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/import.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from ./boost/python/import.hpp:8,
                 from libs/python/src/import.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/import.o" "libs/python/src/import.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/import.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/exec.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from ./boost/python/exec.hpp:8,
                 from libs/python/src/exec.cpp:6:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/exec.o" "libs/python/src/exec.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/exec.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/function_doc_signature.o
In file included from ./boost/python/detail/prefix.hpp:13,
                 from ./boost/python/converter/registrations.hpp:8,
                 from libs/python/src/object/function_doc_signature.cpp:9:
./boost/python/detail/wrap_python.hpp:50:11: fatal error: pyconfig.h: No such file or directory
   50 | # include <pyconfig.h>
      |           ^~~~~~~~~~~~
compilation terminated.

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python3.13" -c -o "bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/function_doc_signature.o" "libs/python/src/object/function_doc_signature.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden/object/function_doc_signature.o...
...skipped <pbin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden>libboost_python313.so.1.69.0 for lack of <pbin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden>list.o...
...skipped <pboost_output/lib>libboost_python313.so.1.69.0 for lack of <pbin.v2/libs/python/build/gcc-14.2.0/release/python-3.13/threading-multi/visibility-hidden>libboost_python313.so.1.69.0...
...skipped <pboost_output/lib>libboost_python313.so for lack of <pboost_output/lib>libboost_python313.so.1.69.0...
gcc.compile.c++ bin.v2/libs/type_erasure/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o
In file included from /usr/include/pthread.h:33,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr-default.h:35,
                 from /usr/include/x86_64-linux-gnu/c++/14/bits/gthr.h:157,
                 from /usr/include/c++/14/ext/atomicity.h:35,
                 from /usr/include/c++/14/bits/shared_ptr_base.h:61,
                 from /usr/include/c++/14/bits/shared_ptr.h:53,
                 from /usr/include/c++/14/memory:80,
                 from ./boost/config/no_tr1/memory.hpp:21,
                 from ./boost/get_pointer.hpp:14,
                 from ./boost/bind/mem_fn.hpp:25,
                 from ./boost/mem_fn.hpp:22,
                 from ./boost/bind/bind.hpp:26,
                 from ./boost/bind.hpp:22,
                 from ./boost/thread/pthread/shared_mutex.hpp:12,
                 from ./boost/thread/shared_mutex.hpp:28,
                 from libs/type_erasure/src/dynamic_binding.cpp:14:
./boost/thread/pthread/thread_data.hpp:60:5: error: missing binary operator before token "("
   60 | #if PTHREAD_STACK_MIN > 0
      |     ^~~~~~~~~~~~~~~~~

    "g++"   -fvisibility-inlines-hidden -fPIC -m64 -pthread -O3 -finline-functions -Wno-inline -Wall -fvisibility=hidden  -DBOOST_ALL_NO_LIB=1 -DBOOST_CHRONO_DYN_LINK=1 -DBOOST_SYSTEM_DYN_LINK=1 -DBOOST_THREAD_BUILD_DLL=1 -DBOOST_THREAD_POSIX -DBOOST_THREAD_USE_DLL=1 -DBOOST_TYPE_ERASURE_DYN_LINK -DNDEBUG  -I"." -c -o "bin.v2/libs/type_erasure/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o" "libs/type_erasure/src/dynamic_binding.cpp"

...failed gcc.compile.c++ bin.v2/libs/type_erasure/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o...
...skipped <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden>libboost_type_erasure.so.1.69.0 for lack of <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden>dynamic_binding.o...
...skipped <pboost_output/lib>libboost_type_erasure.so.1.69.0 for lack of <pbin.v2/libs/type_erasure/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden>libboost_type_erasure.so.1.69.0...
...skipped <pboost_output/lib>libboost_type_erasure.so for lack of <pboost_output/lib>libboost_type_erasure.so.1.69.0...
...skipped <pbin.v2/libs/wave/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden>libboost_wave.so.1.69.0 for lack of <pbin.v2/libs/thread/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden>libboost_thread.so.1.69.0...
...skipped <pboost_output/lib>libboost_wave.so.1.69.0 for lack of <pbin.v2/libs/wave/build/gcc-14.2.0/release/threadapi-pthread/threading-multi/visibility-hidden>libboost_wave.so.1.69.0...
...skipped <pboost_output/lib>libboost_wave.so for lack of <pboost_output/lib>libboost_wave.so.1.69.0...
...failed updating 76 targets...
...skipped 333 targets...
```

</details>

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs. Это можно делать с помощью следующих комманд:
```bash
$ mkdir -p ~/boost-libs
$ mv ~/boost_1_69_0/stage/lib/* ~/boost-libs/
```
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории. Это можно с помощью следующих команд:
```bash
$ cd ~/boost-libs
$ ls -lh
```

<details>
<summary>Список файлов с их занятой памятью</summary>

```bash
total 24M 
rw-rw-r-- 1 vboxuser vboxuser 2.4K Feb 21 13:12 libboost_atomic.a
lrwxrwxrwx 1 vboxuser vboxuser   25 Feb 21 13:14 libboost_atomic.so -> libboost_atomic.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  16K Feb 21 13:14 libboost_atomic.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 229K Feb 21 13:18 libboost_chrono.a
lrwxrwxrwx 1 vboxuser vboxuser   25 Feb 21 13:14 libboost_chrono.so -> libboost_chrono.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  57K Feb 21 13:14 libboost_chrono.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 149K Feb 21 13:12 libboost_container.a
lrwxrwxrwx 1 vboxuser vboxuser   28 Feb 21 13:14 libboost_container.so -> libboost_container.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 104K Feb 21 13:14 libboost_container.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser  20K Feb 21 13:12 libboost_context.a
lrwxrwxrwx 1 vboxuser vboxuser   26 Feb 21 13:14 libboost_context.so -> libboost_context.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  24K Feb 21 13:14 libboost_context.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 319K Feb 21 13:12 libboost_contract.a
lrwxrwxrwx 1 vboxuser vboxuser   27 Feb 21 13:14 libboost_contract.so -> libboost_contract.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 168K Feb 21 13:14 libboost_contract.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 149K Feb 21 13:12 libboost_date_time.a
lrwxrwxrwx 1 vboxuser vboxuser   28 Feb 21 13:14 libboost_date_time.so -> libboost_date_time.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  89K Feb 21 13:14 libboost_date_time.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 1.5K Feb 21 13:14 libboost_exception.a
-rw-rw-r-- 1 vboxuser vboxuser 229K Feb 21 13:12 libboost_fiber.a
lrwxrwxrwx 1 vboxuser vboxuser   24 Feb 21 13:15 libboost_fiber.so -> libboost_fiber.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  97K Feb 21 13:15 libboost_fiber.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 400K Feb 21 13:12 libboost_filesystem.a
lrwxrwxrwx 1 vboxuser vboxuser   29 Feb 21 13:14 libboost_filesystem.so -> libboost_filesystem.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 145K Feb 21 13:14 libboost_filesystem.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 824K Feb 21 13:13 libboost_graph.a
lrwxrwxrwx 1 vboxuser vboxuser   24 Feb 21 13:16 libboost_graph.so -> libboost_graph.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 383K Feb 21 13:16 libboost_graph.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 162K Feb 21 13:13 libboost_iostreams.a
lrwxrwxrwx 1 vboxuser vboxuser   28 Feb 21 13:16 libboost_iostreams.so -> libboost_iostreams.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  83K Feb 21 13:16 libboost_iostreams.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 206K Feb 21 13:11 libboost_prg_exec_monitor.a
lrwxrwxrwx 1 vboxuser vboxuser   35 Feb 21 13:18 libboost_prg_exec_monitor.so -> libboost_prg_exec_monitor.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 111K Feb 21 13:18 libboost_prg_exec_monitor.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 1.5M Feb 21 13:10 libboost_program_options.a
lrwxrwxrwx 1 vboxuser vboxuser   34 Feb 21 13:18 libboost_program_options.so -> libboost_program_options.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 654K Feb 21 13:18 libboost_program_options.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser  78K Feb 21 13:10 libboost_random.a
lrwxrwxrwx 1 vboxuser vboxuser   25 Feb 21 13:18 libboost_random.so -> libboost_random.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  56K Feb 21 13:18 libboost_random.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 3.1M Feb 21 13:13 libboost_regex.a
lrwxrwxrwx 1 vboxuser vboxuser   24 Feb 21 13:15 libboost_regex.so -> libboost_regex.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 1.4M Feb 21 13:15 libboost_regex.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 1.2M Feb 21 13:10 libboost_serialization.a
lrwxrwxrwx 1 vboxuser vboxuser   32 Feb 21 13:18 libboost_serialization.so -> libboost_serialization.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 466K Feb 21 13:18 libboost_serialization.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser  35K Feb 21 13:10 libboost_stacktrace_addr2line.a
lrwxrwxrwx 1 vboxuser vboxuser   39 Feb 21 13:18 libboost_stacktrace_addr2line.so -> libboost_stacktrace_addr2line.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  39K Feb 21 13:18 libboost_stacktrace_addr2line.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser  19K Feb 21 13:10 libboost_stacktrace_backtrace.a
lrwxrwxrwx 1 vboxuser vboxuser   39 Feb 21 13:18 libboost_stacktrace_backtrace.so -> libboost_stacktrace_backtrace.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 112K Feb 21 13:18 libboost_stacktrace_backtrace.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser  13K Feb 21 13:10 libboost_stacktrace_basic.a
lrwxrwxrwx 1 vboxuser vboxuser   35 Feb 21 13:18 libboost_stacktrace_basic.so -> libboost_stacktrace_basic.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  22K Feb 21 13:18 libboost_stacktrace_basic.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 2.7K Feb 21 13:10 libboost_stacktrace_noop.a
lrwxrwxrwx 1 vboxuser vboxuser   34 Feb 21 13:18 libboost_stacktrace_noop.so -> libboost_stacktrace_noop.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  16K Feb 21 13:18 libboost_stacktrace_noop.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 1.3K Feb 21 13:18 libboost_system.a
lrwxrwxrwx 1 vboxuser vboxuser   25 Feb 21 13:14 libboost_system.so -> libboost_system.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  15K Feb 21 13:14 libboost_system.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 2.2M Feb 21 13:18 libboost_test_exec_monitor.a
-rw-rw-r-- 1 vboxuser vboxuser  51K Feb 21 13:18 libboost_timer.a
lrwxrwxrwx 1 vboxuser vboxuser   24 Feb 21 13:18 libboost_timer.so -> libboost_timer.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser  45K Feb 21 13:18 libboost_timer.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 2.2M Feb 21 13:11 libboost_unit_test_framework.a
lrwxrwxrwx 1 vboxuser vboxuser   38 Feb 21 13:19 libboost_unit_test_framework.so -> libboost_unit_test_framework.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 913K Feb 21 13:19 libboost_unit_test_framework.so.1.69.0
-rw-rw-r-- 1 vboxuser vboxuser 4.5M Feb 21 13:12 libboost_wave.a
-rw-rw-r-- 1 vboxuser vboxuser 773K Feb 21 13:10 libboost_wserialization.a
lrwxrwxrwx 1 vboxuser vboxuser   33 Feb 21 13:18 libboost_wserialization.so -> libboost_wserialization.so.1.69.0
-rwxrwxr-x 1 vboxuser vboxuser 330K Feb 21 13:18 libboost_wserialization.so.1.69.0
```

</details>

11. Найдите топ10 самых "тяжёлых". Найти такие файлы можно с помощью команды:
```bash
$ ls -S | head -10
```
Вывод:
```bash
libboost_wave.a
libboost_regex.a
libboost_test_exec_monitor.a
libboost_unit_test_framework.a
libboost_program_options.a
libboost_regex.so.1.69.0
libboost_serialization.a
libboost_unit_test_framework.so.1.69.0
libboost_graph.a
libboost_wserialization.a
```
