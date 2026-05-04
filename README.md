# Домашнее задание к занятию «Уязвимости и атаки на информационные системы» - Куприянов Ю.В.

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

------

### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
*Приведите ответ в свободной форме.*  

---
ОТВЕТ на задание 1.

```
kupriyanov@ntlg:~$ nmap --version
Nmap version 7.94SVN ( https://nmap.org )
Platform: x86_64-pc-linux-gnu
Compiled with: liblua-5.4.6 openssl-3.0.13 libssh2-1.11.0 libz-1.3 libpcre2-10.42 libpcap-1.10.4 nmap-libdnet-1.12 ipv6
Compiled without:
Available nsock engines: epoll poll select
kupriyanov@ntlg:~$ nmap -A 192.168.31.161

```
#### Отчёт о сканировании виртуальной машины Metasploitable

```
kupriyanov@ntlg:~$ nmap -A 192.168.31.161
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-05-04 20:26 +07
Nmap scan report for 192.168.31.161
Host is up (0.019s latency).
Not shown: 977 closed tcp ports (conn-refused)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.31.53
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
|_  2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_RC4_128_WITH_MD5
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|_    SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|_ssl-date: 2026-05-04T13:28:13+00:00; 0s from scanner time.
53/tcp   open  domain      ISC BIND 9.4.2
| dns-nsid: 
|_  bind.version: 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-title: Metasploitable2 - Linux
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
111/tcp  open  rpcbind     2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100003  2,3,4       2049/tcp   nfs
|_  100003  2,3,4       2049/udp   nfs
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
512/tcp  open  exec?
513/tcp  open  login
514/tcp  open  shell?
| fingerprint-strings: 
|   NULL: 
|_    Couldn't get address for your host (ntlg)
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
| mysql-info: 
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 9
|   Capabilities flags: 43564
|   Some Capabilities: ConnectWithDatabase, SupportsCompression, Support41Auth, SupportsTransactions, Speaks41ProtocolNew, LongColumnFlag, SwitchToSSLAfterHandshake
|   Status: Autocommit
|_  Salt: _dWi)0R-*,;&H{Re*=64
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
|_ssl-date: 2026-05-04T13:28:13+00:00; 0s from scanner time.
5900/tcp open  vnc         VNC (protocol 3.3)
| vnc-info: 
|   Protocol version: 3.3
|   Security types: 
|_    VNC Authentication (2)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-server-header: Apache-Coyote/1.1
|_http-favicon: Apache Tomcat
|_http-title: Apache Tomcat/5.5
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port514-TCP:V=7.94SVN%I=7%D=5/4%Time=69F89EA4%P=x86_64-pc-linux-gnu%r(N
SF:ULL,2B,"\x01Couldn't\x20get\x20address\x20for\x20your\x20host\x20\(ntlg
SF:\)\n");
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.20-Debian)
|   Computer name: metasploitable
|   NetBIOS computer name: 
|   Domain name: localdomain
|   FQDN: metasploitable.localdomain
|_  System time: 2026-05-04T09:28:06-04:00
|_smb2-time: Protocol negotiation failed (SMB2)
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|_nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
|_clock-skew: mean: 1h00m00s, deviation: 2h00m00s, median: 0s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 74.33 seconds
```

#### 1.1 Какие сетевые службы в ней разрешены?

На виртуальной машине Metasploitable с IP адресом 192.168.31.161 разрешены следующие сетевые службы:

- FTP (21/tcp) — vsftpd 2.3.4. Разрешён анонимный доступ (Anonymous FTP login allowed).
- SSH (22/tcp) — OpenSSH 4.7p1 Debian 8ubuntu1 (протокол 2.0).
- Telnet (23/tcp) — Linux telnetd.
- SMTP (25/tcp) — Postfix smtpd. Поддерживает команды: PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS и др.
- DNS (53/tcp) — ISC BIND 9.4.2.
- HTTP (80/tcp) — Apache httpd 2.2.8 (Ubuntu) DAV/2. Заголовок страницы: Metasploitable2 — Linux.
- RPCbind (111/tcp) — версия 2 (RPC #100000). Поддерживает NFS (порты 2049/tcp и 2049/udp).
- NetBIOS‑SSN (139/tcp) — Samba smbd 3.X–4.X (рабочая группа: WORKGROUP).
- NetBIOS‑SSN (445/tcp) — Samba smbd 3.0.20-Debian (рабочая группа: WORKGROUP).
- Java RMI (1099/tcp) — GNU Classpath grmiregistry.
- Bindshell (1524/tcp) — Metasploitable root shell.
- NFS (2049/tcp) — версии 2–4 (RPC #100003).
- FTP (2121/tcp) — ProFTPD 1.3.1.
- MySQL (3306/tcp) — MySQL 5.0.51a-3ubuntu5.
- PostgreSQL (5432/tcp) — PostgreSQL DB 8.3.0–8.3.7.
- VNC (5900/tcp) — протокол 3.3, аутентификация: VNC Authentication.
- X11 (6000/tcp) — доступ запрещён (access denied).
- IRC (6667/tcp) — UnrealIRCd.
- AJP13 (8009/tcp) — Apache Jserv (протокол v1.3).
- HTTP (8180/tcp) — Apache Tomcat/Coyote JSP engine 1.1. Заголовок: Apache Tomcat/5.5.

#### 1.2 Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей).

1. FTP (порты 21/tcp и 2121/tcp)
vsftpd 2.3.4 содержит бэкдор: позволяет получить удалённый доступ без аутентификации (CVE не присвоен, но широко известен в сообществе). Эксплойт есть в Metasploit (exploit/unix/ftp/vsftpd_234_backdoor).
Анонимный доступ разрешён (ftp-anon: Anonymous FTP login allowed): злоумышленник может скачивать/загружать файлы без пароля.
Передача данных в открытом виде: нет шифрования, трафик можно перехватить.
2. SSH (порт 22/tcp)
OpenSSH 4.7p1 (2007 г.) — содержит уязвимости, например, CVE‑2006‑5052 (переполнение буфера в аутентификации по ключам).
Используются устаревшие алгоритмы (DSA 1024 бит, RSA 2048 бит), которые могут быть скомпрометированы.
3. Telnet (порт 23/tcp)
Отсутствие шифрования: все данные (логины, пароли) передаются в открытом виде.
Уязвимость к перехвату сессии (sniffing) и атакам MITM.
4. SMTP (порт 25/tcp)
Postfix с поддержкой STARTTLS, но используется SSLv2 (уязвим к POODLE, CVE‑2014‑3566).
Шифры SSLv2 (SSL2_RC4_128_WITH_MD5 и др.) слабые и легко взламываются.
5. DNS (порт 53/tcp)
ISC BIND 9.4.2 — содержит уязвимости типа cache poisoning (CVE‑2008‑0166) и DoS (CVE‑2007‑6281).
6. HTTP (порты 80/tcp и 8180/tcp)
Apache 2.2.8 (2008 г.): уязвимости к DoS-атакам (CVE‑2011‑3192) и обходу ограничений (CVE‑2009‑3094).
Tomcat 5.5 на порту 8180: уязвимости к RCE (CVE‑2013‑4487) и LFI (CVE‑2012‑5887).
Возможные веб‑уязвимости: SQLi, XSS, directory traversal.
7. Samba (порты 139/tcp и 445/tcp)
Samba 3.0.20-Debian содержит эксплойт для удалённого выполнения кода: username map script (CVE‑2007‑2447). Атака выполняется через отправку специального SMB-запроса.
Подпись SMB отключена (message_signing: disabled) — риск атак MITM и подделки пакетов.
8. NFS (порт 2049/tcp)
NFS v2/v3 без аутентификации: если экспортированы директории, злоумышленник может монтировать их и читать/изменять файлы.
9. VNC (порт 5900/tcp)
VNC 3.3 с аутентификацией по паролю: слабые пароли легко подбираются брутфорсом.
Нет шифрования трафика (если не настроено отдельно).
10. IRC (порт 6667/tcp)
UnrealIRCd — содержит уязвимости к переполнению буфера (CVE‑2001‑1010) и DoS.
11. MySQL (порт 3306/tcp)
MySQL 5.0.51a — уязвимости к обходу аутентификации (CVE‑2012‑2122) и SQLi.
По умолчанию используется слабый пароль root или пустой пароль.
12. PostgreSQL (порт 5432/tcp)
PostgreSQL 8.3.0–8.3.7 — уязвимости к SQLi и удалённому выполнению кода (CVE‑2007‑3268).
13. RMI (порт 1099/tcp)
GNU Classpath grmiregistry — уязвимость к десериализации (CVE‑2015‑4852), позволяющая выполнить произвольный код.
14. Backdoor (порт 1524/tcp)
Bindshell — это специально созданный бэкдор в Metasploitable. Открывает оболочку с правами root без аутентификации.
15. RPC/rstatd (порты 512/tcp, 513/tcp, 514/tcp)
Устаревшие сервисы UNIX (rsh, rexec, rlogin) — передают данные в открытом виде, уязвимы к перехвату и брутфорсу.

---

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*

---

#### ОТВЕТ на задание 2.

#### 2.1 Cканирование Metasploitable в режимах SYN 

```
kupriyanov@ntlg:~/ntlg/Netology_13-01-hw$ sudo nmap -sS 192.168.31.161
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-05-04 21:19 +07
Nmap scan report for 192.168.31.161
Host is up (0.0011s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
512/tcp  open  exec
513/tcp  open  login
514/tcp  open  shell
1099/tcp open  rmiregistry
1524/tcp open  ingreslock
2049/tcp open  nfs
2121/tcp open  ccproxy-ftp
3306/tcp open  mysql
5432/tcp open  postgresql
5900/tcp open  vnc
6000/tcp open  X11
6667/tcp open  irc
8009/tcp open  ajp13
8180/tcp open  unknown
MAC Address: 08:00:27:81:D4:20 (Oracle VirtualBox virtual NIC)
```
Отправляется пакет с флагом `SYN` (первый шаг трёхэтапного рукопожатия TCP).
Если порт открыт, сервер отвечает пакетом `SYN‑ACK`.
Сканирующий хост не завершает соединение — отправляет `RST` (сброс), чтобы не открывать полноценное соединение.
Если порт закрыт, сервер сразу отвечает `RST`.
В Wireshark:
- Виден обмен `SYN → SYN-ACK → RST` для открытых портов
- Для закрытых портов: `SYN → RST`.

#### 2.2 Сканирование Metasploitable в режимах FIN

```
kupriyanov@ntlg:~/ntlg/Netology_13-01-hw$ sudo nmap -sA 192.168.31.161
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-05-04 21:24 +07
Nmap scan report for 192.168.31.161
Host is up (0.0043s latency).
All 1000 scanned ports on 192.168.31.161 are in ignored states.
Not shown: 1000 unfiltered tcp ports (reset)
MAC Address: 08:00:27:81:D4:20 (Oracle VirtualBox virtual NIC)

```

Отправляется пакет с флагом FIN (обычно отправляется при завершении соединения).
Согласно RFC 793, хост с закрытым портом должен ответить RST.
Хост с открытым портом проигнорирует такой пакет (не ответит).
В Wireshark:
- Для закрытых портов виден FIN → RST.
- Для открытых портов — только исходящий FIN.

#### 2.3 Сканирование Metasploitable в режимах Xmas

```
kupriyanov@ntlg:~/ntlg/Netology_13-01-hw$ sudo nmap -sX 192.168.31.161
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-05-04 21:25 +07
Nmap scan report for 192.168.31.161
Host is up (0.0034s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE         SERVICE
21/tcp   open|filtered ftp
22/tcp   open|filtered ssh
23/tcp   open|filtered telnet
25/tcp   open|filtered smtp
53/tcp   open|filtered domain
80/tcp   open|filtered http
111/tcp  open|filtered rpcbind
139/tcp  open|filtered netbios-ssn
445/tcp  open|filtered microsoft-ds
512/tcp  open|filtered exec
513/tcp  open|filtered login
514/tcp  open|filtered shell
1099/tcp open|filtered rmiregistry
1524/tcp open|filtered ingreslock
2049/tcp open|filtered nfs
2121/tcp open|filtered ccproxy-ftp
3306/tcp open|filtered mysql
5432/tcp open|filtered postgresql
5900/tcp open|filtered vnc
6000/tcp open|filtered X11
6667/tcp open|filtered irc
8009/tcp open|filtered ajp13
8180/tcp open|filtered unknown
MAC Address: 08:00:27:81:D4:20 (Oracle VirtualBox virtual NIC)
```

Отправляется пакет с флагами FIN, URG, PSH (как гирлянда огней — отсюда название «Xmas»).
Поведение аналогично FIN‑сканированию:
Закрытый порт отвечает RST.
Открытый порт игнорирует пакет.
В Wireshark:
- Аналогично FIN‑сканированию, но пакет имеет три флага.

#### 2.4 Сканирование Metasploitable в режимах UDP

```
kupriyanov@ntlg:~/ntlg/Netology_13-01-hw$ sudo nmap -sU 192.168.31.161
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-05-04 21:26 +07
Nmap scan report for 192.168.31.161
Host is up (0.0022s latency).
Not shown: 993 closed udp ports (port-unreach)
PORT     STATE         SERVICE
53/udp   open          domain
68/udp   open|filtered dhcpc
69/udp   open|filtered tftp
111/udp  open          rpcbind
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
2049/udp open          nfs
MAC Address: 08:00:27:81:D4:20 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1077.13 seconds
```

Отправляется пустой UDP‑пакет на целевой порт.
UDP — протокол без установления соединения, поэтому логика иная.
Если порт открыт, то обычно нет ответа, но некоторые службы могут ответить данными.
Если же порт закрыт, то сервер отправляет ICMP‑сообщение «Port Unreachable».
Фильтруемый порт: может быть ICMP «Admin Prohibited» или таймаут (нет ответа).

В Wireshark:
- Видно UDP‑пакеты к целевым портам.
- Ответы ICMP type 3 code 3 для закрытых портов.

#### В Итоге:

- SYN - инициирует начало TCP‑соединения, но не завершает его. Самый надёжный метод.

- FIN/Xmas - отправляют «необычные» TCP‑пакеты, которые должны быть проигнорированы открытыми портами. Cложнее обнаружить IDS, чем SYN или UDP.

- UDP - не использует флаги, полагается на ICMP‑ответы или отсутствие ответа. Самый медленный и менее точный метод из‑за таймаутов и фильтрации ICMP
---

