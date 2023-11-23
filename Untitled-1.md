44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@ip-172-31-77-251 ~ ]# set-hostname els
Last login: Wed Nov 22 15:56:45 UTC 2023 from 49.47.233.200 on pts/0

------------------------------------------------------------------------------------------------
---------------------------------> install elasticsearch  <-------------------------------------
------------------------------------------------------------------------------------------------
44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# vim /etc/yum.repos.d/elasticsearch.repo

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# dnf install elasticsearch -y
Last metadata expiration check: 0:00:42 ago on Wed 22 Nov 2023 03:58:36 PM UTC.
Dependencies resolved.
====================================================================================================================================================
 Package                               Architecture                   Version                           Repository                             Size
====================================================================================================================================================
Installing:
 elasticsearch                         x86_64                         8.11.1-1                          elasticsearch                         601 M

Transaction Summary
====================================================================================================================================================
Install  1 Package

Total download size: 601 M
Installed size: 1.2 G
Downloading Packages:
elasticsearch-8.11.1-x86_64.rpm                                                                                      25 MB/s | 601 MB     00:24
----------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                25 MB/s | 601 MB     00:24
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                            1/1
  Running scriptlet: elasticsearch-8.11.1-1.x86_64                                                                                              1/1
Creating elasticsearch group... OK
Creating elasticsearch user... OK

  Installing       : elasticsearch-8.11.1-1.x86_64                                                                                              1/1
  Running scriptlet: elasticsearch-8.11.1-1.x86_64                                                                                              1/1
--------------------------- Security autoconfiguration information ------------------------------

Authentication and authorization are enabled.
TLS for the transport and HTTP layers is enabled and configured.

The generated password for the elastic built-in superuser is : MFmjOSKynopiPCWr8bBs

If this node should join an existing cluster, you can reconfigure this with
'/usr/share/elasticsearch/bin/elasticsearch-reconfigure-node --enrollment-token <token-here>'
after creating an enrollment token on your existing cluster.

You can complete the following actions at any time:

Reset the password of the elastic built-in superuser with
'/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic'.

Generate an enrollment token for Kibana instances with
 '/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana'.

Generate an enrollment token for Elasticsearch nodes with
'/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node'.

-------------------------------------------------------------------------------------------------
### NOT starting on installation, please execute the following statements to configure elasticsearch service to start automatically using systemd
 sudo systemctl daemon-reload
 sudo systemctl enable elasticsearch.service
### You can start elasticsearch service by executing
 sudo systemctl start elasticsearch.service

[/usr/lib/tmpfiles.d/elasticsearch.conf:1] Line references path below legacy directory /var/run/, updating /var/run/elasticsearch → /run/elasticsearch; please update the tmpfiles.d/ drop-in file accordingly.

  Verifying        : elasticsearch-8.11.1-1.x86_64                                                                                              1/1

Installed:
  elasticsearch-8.11.1-1.x86_64

Complete!
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# sudo systemctl daemon-reload

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# sudo systemctl enable elasticsearch.service
Created symlink /etc/systemd/system/multi-user.target.wants/elasticsearch.service → /usr/lib/systemd/system/elasticsearch.service.

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# sudo systemctl start elasticsearch.service

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# netstat -lntp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1/systemd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      806/sshd
tcp6       0      0 :::111                  :::*                    LISTEN      1/systemd
tcp6       0      0 :::9200                 :::*                    LISTEN      1701/java
tcp6       0      0 127.0.0.1:9300          :::*                    LISTEN      1701/java
tcp6       0      0 ::1:9300                :::*                    LISTEN      1701/java
tcp6       0      0 :::22                   :::*                    LISTEN      806/sshd
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
--------------------------------------> install kibana  <-----------------------------------------
------------------------------------------------------------------------------------------------

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# dnf install kibana
Last metadata expiration check: 0:06:18 ago on Wed 22 Nov 2023 03:58:36 PM UTC.
Dependencies resolved.
====================================================================================================================================================
 Package                          Architecture                     Version                            Repository                               Size
====================================================================================================================================================
Installing:
 kibana                           x86_64                           8.11.1-1                           elasticsearch                           303 M

Transaction Summary
====================================================================================================================================================
Install  1 Package

Total download size: 303 M
Installed size: 867 M
Is this ok [y/N]: y
Downloading Packages:
kibana-8.11.1-x86_64.rpm                                                                                             22 MB/s | 303 MB     00:13
----------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                22 MB/s | 303 MB     00:13
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                            1/1
  Running scriptlet: kibana-8.11.1-1.x86_64                                                                                                     1/1
  Installing       : kibana-8.11.1-1.x86_64                                                                                                     1/1
  Running scriptlet: kibana-8.11.1-1.x86_64                                                                                                     1/1
Creating kibana group... OK
Creating kibana user... OK

Kibana is currently running with legacy OpenSSL providers enabled! For details and instructions on how to disable see https://www.elastic.co/guide/en/kibana/8.11/production.html#openssl-legacy-provider
Created Kibana keystore in /etc/kibana/kibana.keystore

[/usr/lib/tmpfiles.d/elasticsearch.conf:1] Line references path below legacy directory /var/run/, updating /var/run/elasticsearch → /run/elasticsearch; please update the tmpfiles.d/ drop-in file accordingly.

  Verifying        : kibana-8.11.1-1.x86_64                                                                                                     1/1

Installed:
  kibana-8.11.1-1.x86_64

Complete!

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# systemctl enable kibana
Created symlink /etc/systemd/system/multi-user.target.wants/kibana.service → /usr/lib/systemd/system/kibana.service.

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# systemctl start kibana

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# netstat -lntp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:5601          0.0.0.0:*               LISTEN      1979/node
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1/systemd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      806/sshd
tcp6       0      0 :::111                  :::*                    LISTEN      1/systemd
tcp6       0      0 :::9200                 :::*                    LISTEN      1701/java
tcp6       0      0 127.0.0.1:9300          :::*                    LISTEN      1701/java
tcp6       0      0 ::1:9300                :::*                    LISTEN      1701/java
tcp6       0      0 :::22                   :::*                    LISTEN      806/sshd


44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# vim /etc/kibana/kibana.yml

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# yum install nginx
Last metadata expiration check: 0:15:31 ago on Wed 22 Nov 2023 04:17:52 PM UTC.
Dependencies resolved.
====================================================================================================================================================
 Package                                   Architecture         Version                                               Repository               Size
====================================================================================================================================================
Installing:
 nginx                                     x86_64               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream               570 k
Installing dependencies:
 dejavu-fonts-common                       noarch               2.35-7.el8                                            baseos                   74 k
 dejavu-sans-fonts                         noarch               2.35-7.el8                                            baseos                  1.6 M
 fontconfig                                x86_64               2.13.1-4.el8                                          baseos                  274 k
 fontpackages-filesystem                   noarch               1.44-22.el8                                           baseos                   16 k
 gd                                        x86_64               2.2.5-7.el8                                           appstream               144 k
 jbigkit-libs                              x86_64               2.1-14.el8                                            appstream                55 k
 libX11                                    x86_64               1.6.8-7.el8                                           appstream               612 k
 libX11-common                             noarch               1.6.8-7.el8                                           appstream               211 k
 libXau                                    x86_64               1.0.9-3.el8                                           appstream                37 k
 libXpm                                    x86_64               3.5.12-11.el8                                         appstream                59 k
 libjpeg-turbo                             x86_64               1.5.3-12.el8                                          appstream               157 k
 libtiff                                   x86_64               4.0.9-29.el8                                          appstream               189 k
 libwebp                                   x86_64               1.0.0-9.el8                                           appstream               274 k
 libxcb                                    x86_64               1.13.1-1.el8                                          appstream               229 k
 libxslt                                   x86_64               1.1.32-6.el8                                          baseos                  250 k
 nginx-all-modules                         noarch               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream                23 k
 nginx-filesystem                          noarch               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream                24 k
 nginx-mod-http-image-filter               x86_64               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream                35 k
 nginx-mod-http-perl                       x86_64               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream                46 k
 nginx-mod-http-xslt-filter                x86_64               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream                33 k
 nginx-mod-mail                            x86_64               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream                64 k
 nginx-mod-stream                          x86_64               1:1.14.1-9.module_el8.0.0+1060+3ab382d3               appstream                85 k
Enabling module streams:
 nginx                                                          1.14

Transaction Summary
====================================================================================================================================================
Install  23 Packages

Total download size: 4.9 M
Installed size: 15 M
Is this ok [y/N]: y
Downloading Packages:
(1/23): jbigkit-libs-2.1-14.el8.x86_64.rpm                                                                          1.5 MB/s |  55 kB     00:00
(2/23): libX11-1.6.8-7.el8.x86_64.rpm                                                                                14 MB/s | 612 kB     00:00
(3/23): gd-2.2.5-7.el8.x86_64.rpm                                                                                   2.9 MB/s | 144 kB     00:00
(4/23): libXau-1.0.9-3.el8.x86_64.rpm                                                                               4.5 MB/s |  37 kB     00:00
(5/23): libX11-common-1.6.8-7.el8.noarch.rpm                                                                        9.5 MB/s | 211 kB     00:00
(6/23): libXpm-3.5.12-11.el8.x86_64.rpm                                                                             5.3 MB/s |  59 kB     00:00
(7/23): libjpeg-turbo-1.5.3-12.el8.x86_64.rpm                                                                        13 MB/s | 157 kB     00:00
(8/23): libwebp-1.0.0-9.el8.x86_64.rpm                                                                               22 MB/s | 274 kB     00:00
(9/23): libtiff-4.0.9-29.el8.x86_64.rpm                                                                             8.8 MB/s | 189 kB     00:00
(10/23): libxcb-1.13.1-1.el8.x86_64.rpm                                                                              12 MB/s | 229 kB     00:00
(11/23): nginx-all-modules-1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch.rpm                                         2.7 MB/s |  23 kB     00:00
(12/23): nginx-filesystem-1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch.rpm                                          3.0 MB/s |  24 kB     00:00
(13/23): nginx-1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64.rpm                                                      20 MB/s | 570 kB     00:00
(14/23): nginx-mod-http-image-filter-1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64.rpm                               2.2 MB/s |  35 kB     00:00
(15/23): nginx-mod-http-perl-1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64.rpm                                       2.9 MB/s |  46 kB     00:00
(16/23): nginx-mod-http-xslt-filter-1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64.rpm                                4.1 MB/s |  33 kB     00:00
(17/23): nginx-mod-mail-1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64.rpm                                            6.2 MB/s |  64 kB     00:00
(18/23): dejavu-fonts-common-2.35-7.el8.noarch.rpm                                                                  8.5 MB/s |  74 kB     00:00
(19/23): nginx-mod-stream-1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64.rpm                                          6.0 MB/s |  85 kB     00:00
(20/23): fontpackages-filesystem-1.44-22.el8.noarch.rpm                                                             3.8 MB/s |  16 kB     00:00
(21/23): fontconfig-2.13.1-4.el8.x86_64.rpm                                                                          21 MB/s | 274 kB     00:00
(22/23): libxslt-1.1.32-6.el8.x86_64.rpm                                                                             22 MB/s | 250 kB     00:00
(23/23): dejavu-sans-fonts-2.35-7.el8.noarch.rpm                                                                     39 MB/s | 1.6 MB     00:00
----------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                13 MB/s | 4.9 MB     00:00
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                            1/1
  Installing       : fontpackages-filesystem-1.44-22.el8.noarch                                                                                1/23
  Installing       : libjpeg-turbo-1.5.3-12.el8.x86_64                                                                                         2/23
  Installing       : dejavu-fonts-common-2.35-7.el8.noarch                                                                                     3/23
  Installing       : dejavu-sans-fonts-2.35-7.el8.noarch                                                                                       4/23
  Installing       : fontconfig-2.13.1-4.el8.x86_64                                                                                            5/23
  Running scriptlet: fontconfig-2.13.1-4.el8.x86_64                                                                                            5/23
  Installing       : libxslt-1.1.32-6.el8.x86_64                                                                                               6/23
  Running scriptlet: nginx-filesystem-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch                                                           7/23
  Installing       : nginx-filesystem-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch                                                           7/23
  Installing       : libwebp-1.0.0-9.el8.x86_64                                                                                                8/23
  Installing       : libXau-1.0.9-3.el8.x86_64                                                                                                 9/23
  Installing       : libxcb-1.13.1-1.el8.x86_64                                                                                               10/23
  Installing       : libX11-common-1.6.8-7.el8.noarch                                                                                         11/23
  Installing       : libX11-1.6.8-7.el8.x86_64                                                                                                12/23
  Installing       : libXpm-3.5.12-11.el8.x86_64                                                                                              13/23
  Installing       : jbigkit-libs-2.1-14.el8.x86_64                                                                                           14/23
  Running scriptlet: jbigkit-libs-2.1-14.el8.x86_64                                                                                           14/23
  Installing       : libtiff-4.0.9-29.el8.x86_64                                                                                              15/23
  Installing       : gd-2.2.5-7.el8.x86_64                                                                                                    16/23
  Running scriptlet: gd-2.2.5-7.el8.x86_64                                                                                                    16/23
  Installing       : nginx-mod-http-perl-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                       17/23
  Running scriptlet: nginx-mod-http-perl-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                       17/23
  Installing       : nginx-mod-http-xslt-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                18/23
  Running scriptlet: nginx-mod-http-xslt-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                18/23
  Installing       : nginx-mod-mail-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                            19/23
  Running scriptlet: nginx-mod-mail-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                            19/23
  Installing       : nginx-mod-stream-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                          20/23
  Running scriptlet: nginx-mod-stream-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                          20/23
  Installing       : nginx-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                                     21/23
  Running scriptlet: nginx-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                                     21/23
  Installing       : nginx-mod-http-image-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                               22/23
  Running scriptlet: nginx-mod-http-image-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                               22/23
  Installing       : nginx-all-modules-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch                                                         23/23
  Running scriptlet: nginx-all-modules-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch                                                         23/23
  Running scriptlet: fontconfig-2.13.1-4.el8.x86_64                                                                                           23/23
  Verifying        : gd-2.2.5-7.el8.x86_64                                                                                                     1/23
  Verifying        : jbigkit-libs-2.1-14.el8.x86_64                                                                                            2/23
  Verifying        : libX11-1.6.8-7.el8.x86_64                                                                                                 3/23
  Verifying        : libX11-common-1.6.8-7.el8.noarch                                                                                          4/23
  Verifying        : libXau-1.0.9-3.el8.x86_64                                                                                                 5/23
  Verifying        : libXpm-3.5.12-11.el8.x86_64                                                                                               6/23
  Verifying        : libjpeg-turbo-1.5.3-12.el8.x86_64                                                                                         7/23
  Verifying        : libtiff-4.0.9-29.el8.x86_64                                                                                               8/23
  Verifying        : libwebp-1.0.0-9.el8.x86_64                                                                                                9/23
  Verifying        : libxcb-1.13.1-1.el8.x86_64                                                                                               10/23
  Verifying        : nginx-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                                     11/23
  Verifying        : nginx-all-modules-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch                                                         12/23
  Verifying        : nginx-filesystem-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch                                                          13/23
  Verifying        : nginx-mod-http-image-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                               14/23
  Verifying        : nginx-mod-http-perl-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                       15/23
  Verifying        : nginx-mod-http-xslt-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                16/23
  Verifying        : nginx-mod-mail-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                            17/23
  Verifying        : nginx-mod-stream-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64                                                          18/23
  Verifying        : dejavu-fonts-common-2.35-7.el8.noarch                                                                                    19/23
  Verifying        : dejavu-sans-fonts-2.35-7.el8.noarch                                                                                      20/23
  Verifying        : fontconfig-2.13.1-4.el8.x86_64                                                                                           21/23
  Verifying        : fontpackages-filesystem-1.44-22.el8.noarch                                                                               22/23
  Verifying        : libxslt-1.1.32-6.el8.x86_64                                                                                              23/23

Installed:
  dejavu-fonts-common-2.35-7.el8.noarch                                        dejavu-sans-fonts-2.35-7.el8.noarch
  fontconfig-2.13.1-4.el8.x86_64                                               fontpackages-filesystem-1.44-22.el8.noarch
  gd-2.2.5-7.el8.x86_64                                                        jbigkit-libs-2.1-14.el8.x86_64
  libX11-1.6.8-7.el8.x86_64                                                    libX11-common-1.6.8-7.el8.noarch
  libXau-1.0.9-3.el8.x86_64                                                    libXpm-3.5.12-11.el8.x86_64
  libjpeg-turbo-1.5.3-12.el8.x86_64                                            libtiff-4.0.9-29.el8.x86_64
  libwebp-1.0.0-9.el8.x86_64                                                   libxcb-1.13.1-1.el8.x86_64
  libxslt-1.1.32-6.el8.x86_64                                                  nginx-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64
  nginx-all-modules-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch             nginx-filesystem-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.noarch
  nginx-mod-http-image-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64   nginx-mod-http-perl-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64
  nginx-mod-http-xslt-filter-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64    nginx-mod-mail-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64
  nginx-mod-stream-1:1.14.1-9.module_el8.0.0+1060+3ab382d3.x86_64

Complete!


44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# vim /etc/nginx/nginx.conf

#  location / {
#    proxy_pass http://localhost:5601;
#  }

44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# systemctl restart nginx


44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana
eyJ2ZXIiOiI4LjExLjEiLCJhZHIiOlsiMTcyLjMxLjc3LjI1MTo5MjAwIl0sImZnciI6Ijc3NTU2ZWYyZDg5NWI1ODM5ODgyNmJiODU0YjQxNDA4MzMzYjM1ZDg0NGUwNzg5M2UzMjBkMjMwMjkwNDIyZWYiLCJrZXkiOiIyQ1hzOTRzQlU2YkJ6TnhncDM3cDpTZHlHTUxlN1RUdVl6RFhKblhTcFN3In0=


44.221.50.44 | 172.31.77.251 | r5.large | null
[ root@els ~ ]# /usr/share/kibana/bin/kibana-verification-code
Your verification code is:  492 853

----------  --------------------------------------------------------------------------------------





















--------------------------- Security autoconfiguration information ------------------------------

Authentication and authorization are enabled.
TLS for the transport and HTTP layers is enabled and configured.

The generated password for the elastic built-in superuser is : t_w+soeu7V2V**ukrRBB

If this node should join an existing cluster, you can reconfigure this with
'/usr/share/elasticsearch/bin/elasticsearch-reconfigure-node --enrollment-token <token-here>'
after creating an enrollment token on your existing cluster.

You can complete the following actions at any time:

Reset the password of the elastic built-in superuser with
'/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic'.

Generate an enrollment token for Kibana instances with
 '/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana'.

Generate an enrollment token for Elasticsearch nodes with
'/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node'.

-------------------------------------------------------------------------------------------------
### NOT starting on installation, please execute the following statements to configure elasticsearch service to start automatically using systemd
 sudo systemctl daemon-reload
 sudo systemctl enable elasticsearch.service
### You can start elasticsearch service by executing
 sudo systemctl start elasticsearch.service

[/usr/lib/tmpfiles.d/elasticsearch.conf:1] Line references path below legacy directory /var/run/, updating /var/run/elasticsearch → /run/elasticsearch; please update the tmpfiles.d/ drop-in file accordingly.

  Verifying        : elasticsearch-8.11.1-1.x86_64                          1/1

Installed:
  elasticsearch-8.11.1-1.x86_64

  [ root@elk ~ ]# /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
This tool will reset the password of the [elastic] user to an autogenerated value.
The password will be printed in the console.
Please confirm that you would like to continue [y/N]y


Password for the [elastic] user successfully reset.
New value: sdpN7ETpwFZpjZtP6EEv
