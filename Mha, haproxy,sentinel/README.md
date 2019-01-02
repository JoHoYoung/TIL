#### Ubuntu 

nginx
1. 웹서버를 설치한다.
2. 로드밸런싱도 가능하다.
```
sudo apt-get install -y
sudo apt-get install nginx
```
관련 설정은 /etc/nginx/sites-available/default 위치가 기본설정 위치로 지정되어 있다.

API 서버 설정
```
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        server_name fingo.today.live                // DNS와 연결된 도메인 이름

        # Logs
        access_log /var/log/nginx/nginx_fingo.log;      // 접근 로그의 위치
        error_log /var/log/nginx/nginx_fingo_error.log warn;  // 에러로그의 위치

        root /home/ubuntu/fingo/;
        index index.html index.htm index.nginx-debian.html;

        client_max_body_size 100M; #100mb

        location ~* ^/elb-status {
                return 200 'OK';
                add_header Content-Type text/plain;
        }

        location / {
                if ($http_x_forwarded_proto != 'https') {
                        rewrite ^ https://$server_name$request_uri? permanent;
                }   //만약 https로 접근이 오지 않으면 https로 바꿔준다.
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Host $http_host;
                proxy_set_header X-NginX-Proxy true;
                proxy_pass http://127.0.0.1:3001;   //해당 서버로 접근이 오면 3001번 포트로 연결한다.
                proxy_redirect off;
        }
}
```

ssh 설정

관련설정은 /root/.ssh 에서 이루어 진다.

SSH Key는 공개키(public key)와 비공개 키(private key)로 이루어지는데 이 두개의 관계를 이해하는 것이 SSH Key를 이해하는데 핵심이다. 키를 생성하면 공개키와 비공개키가 만들어진다. 이 중에 비공개키는 로컬 머신에 위치해야 하고, 공개키는 리모트 머신에 위치해야 한다. (로컬 머신은 SSH Client, 원격 머신은 SSH Server가 설치된 컴퓨터를 의미한다.)

비공개키를 가지고 해당 비공개키와 쌍이맞는 공개키를 가지고 있는 리모트 머신에 접근하는 방식이다.
음.. 비공개 키는 자물쇠의 열쇠, 공개키는 자물쇠 구멍 정도의 비유가 적당한것 같다.

일단 자물쇠와, 열쇠를 만들었으면 헤당 자물쇠가 내 서버의 자물쇠라는 것을 등록해아한다. 특정서버의 자물쇠 목록에 자물쇠를 등록해야 하는데 특정 서버의 자물쇠 정보는 /root/.ssh/authorized_keys 에 저장되어있다. 새로운 pub키 정보를 해당파일에 저장한다.
```
$ cat ~~~.pub >> /root/.ssh/authorized_keys 
```
* * * 
Mysql 이중화

1. Master, Slave 설정

Master, Slave 의 conf 설정 
```
[mysqld]
#
# * Basic Settings
#
log-bin         = mysql-bin
server-id=1
```
이때 Master,와 Slave의 server-id는 달라야 한다.

Master에 Replication 권한 계정 추가
```
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'1%' IDENTIFIED BY 'test';
FLUSH PRIVILEGES;
```

Slave에서 Replication 시작
```
CHANGE MASTER TO MASTER_HOST = ’18.207.215.142’, MASTER_USER=‘repl’, MASTER_PASSWORD = ‘’, MASTER_LOG_FILE = ‘mysql-bin.000002’,MASTER_PORT =. 3306,MASTER_LOG_POS = 782, MASTER_CONNECT_RETRY = 30

```
```
START SLAVE;
```

MHA 설정.

slave 서버는 Read만 가능하다. 따라서 Master Mysql 서버가 다운됐을때 write를 못하는 문제가 생긴다. 해당 문제를 해결하기위해 Master 서버 장애시 Mysql Slave를 Master로 승격시켜야한다. 

MHA는 Mysql master,slave 설정시 Master가 죽으면 Slave를 Master로 승격시키는 역할을 한다.
이때 MHA manager 서버에서 mysql서버로의 루트계정으로 접속권한이 필요하다. 처음에는 ubuntu계정으로 접속하여 구동하도록 설정하였는데 에러가 많이 났었다. 특정 파일에 접근 권한이 없어 그 파일,폴더에 접근권한을 ubuntu로 바꿨지만 그러면 mysql이 접근이 불가능하고, 새로생기는 로그파일은 ubuntu 계정으로 접근이 불가능한 문제가 있었다. 따라서 무조건 루트접속 권한을 열어줘야 한다. AWS EC2 Ubuntu instance의 경우는 기본적으로 root로 접근하는것이 막혀있는데 해당 권한을 열어주는 설정을 한다.

```
$ sudo su
$ cd /root/.ssh
$ nano authorized_keys
```
```
no-port-forwarding,no-agent-forwarding,no-X11-forwarding,command="echo 'Please login as the user \"ubuntu\" rather than the user \"root\".';echo;sleep 10" ssh-rsa ******************************dfsaadsfkweljerlk342l;adsk;alsdksda;12312kl312klj******************************q8wqw/h1fTClPUM4HlGG3FgB5MjZdTdDAk+/L6ahrn6zq88rg******************************n/MfdMbYwejGsJxKJpJXIO8TDuYGdCWUYcew7Acg2k9hi5d ~~~~~_key
```
에서 
```
no-port-forwarding,no-agent-forwarding,no-X11-forwarding,command="echo 'Please login as the user \"ubuntu\" rather than the user \"root\".';echo;sleep 10"  이부분을 지워준다.
```

Mha manager 서버에서 mysql서버들로 ssh접속이 가능해야한다. 그러기 위해선 Mha manager 에서 ssh private키를 갖고있어야 하며, mysql서버들은 pub키가 등록되어 있어야 한다. 또 manager 서버에서 ssh접근을 할때 기본적으로 해당 private키를 사용하여 접근한다는 설정이 있어야한다.


1. manager server
```
$ cd /root/.ssh
  <--- ssh 키 생성  --->
$ ls -al
-rw------- 1 root root 1606 Dec 13 08:45 authorized_keys
-r-------- 1 root root 1679 Dec 11 07:57 id_rsa_mha
-rw-r--r-- 1 root root  402 Dec 11 07:57 id_rsa_mha.pub
cat id_rsa_mha.pub >> authorized_keys
``` 
해당 키들을 mysql서버들에도 scp로 옮겨서 동일 과정을 시행한다.
그 후 ssh 접근시 사용할 config파일을 설정한다. 
```
$ sudo nano config

Host *
User root           >> ssh 접속시 root계정으로 접속하겠다는 것.
IdentityFile /home/ubuntu/.ssh/id_rsa_pem   >> 사용할 private key설정 
StrictHostKeyChecking no
CheckHostIP no              >> ssh로 접속시 (yes/no)를 묻는데 묻지않겠다는 것
```

Mha Node 설치

빌드하는데 필요한 도구를 설치한다.
```
sudo apt-get -y install build-essential devscripts dh-make fakeroot dpkg-dev debhelper libdbi-perl libmysqlclient-dev zlib1g-dev
```

빌드에 필요한 패키지를 가져온다
```
cd ~
 wget http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.033.orig.tar.gz
 wget http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.033-1build2.debian.tar.xz
```

패키지를 빌드한다

```
 mkdir work
 cp libdbd-mysql-perl_4.033.orig.tar.gz work
 cd work
 tar xf libdbd-mysql-perl_4.033.orig.tar.gz
 mv DBD-mysql-4.033 libdbd-mysql-perl_4.033
 tar xf ../libdbd-mysql-perl_4.033-1build2.debian.tar.xz -C libdbd-mysql-perl_4.033
 cd libdbd-mysql-perl_4.033
 dpkg-buildpackage -us -uc
```

빌드된 패키지를 설치한다.
```
 cd ..
 sudo dpkg -i libdbd-mysql-perl_4.033-1build2_amd64.deb
```

Mha Node를 설치한다
```
 cd 
 sudo apt-get install -y git
 git clone https://github.com/yoshinorim/mha4mysql-node
 cd mha4mysql-node
 perl Makefile.PL
 make
 sudo make install
```
이 때 다음과 같은 오류가 나오면 Perl의 Module::Install 모듈을 설치할 필요가있다. ( sudo apt-get install libmodule-install-perl 으로 OK)

```
 $ perl Makefile.PL
 Can not locate inc / Module / Install.pm in @INC (you may need to install the inc :: Module :: Install module) (@INC contains : / etc / perl /usr/local/lib/perl/5.18. 2 /usr/local/share/perl/5.18.2 / usr / lib / perl5 / usr / share / perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 / usr / local / lib / site_perl. ) at Makefile.PL line 1.
 BEGIN failed - compilation aborted at Makefile.PL line 1.
```

Mha Manager 설치

우선 필요한 perl모듈을 설치한다.
```
sudo apt-get install -y libconfig-tiny-perl liblog-dispatch-perl libparallel-forkmanager-perl
```

manager를 설치한다
```
$ git clone https://github.com/yoshinorim/mha4mysql-manager.git
$ cd mha4mysql-manager
$ perl Makefile.PL
$ make
$ sudo make install
```

masterha_ip_failover 스크립트를 위치로 옮긴다.

```
$ sudo cp -p samples/scripts/master_ip_failover /usr/local/bin/
$ chown root:root/usr/local/bin/master_ip_failover
```
FIXME__ 부분을 주석처리한다

```
[error][/usr/local/share/perl/5.22.1/MHA/MasterMonitor.pm, ln427] Error happened on checking configurations.  at /usr/local/bin/masterha_check_repl line 48.
```
의 경우 mysql의 버전을 제대로 가져오지 못해서 나는 에러이다. 해당파일의 일치하는 부분을 다음과 같이 수정하면 된다.
```
sub parse_mysql_version($) {
  my $str = shift;
 ($str) =  $str =~ m/^[^-]*/g;
  my $result = sprintf( '%03d%03d%03d', $str =~ m/(\d+)/g );
  return $result;
}
```
manager config 파일을 작성하기 전, 각 mysql서버에 mha용 계정을 만든다.
```
GRANT ALL ON *.* TO 'mha'@'%' IDENTIFIED BY 'mhapass';
FLUSH PRIVILEGES;
```

Master, Slave, Manager에 필요한 디렉토리도 만든다
```
$ sudo mkdir -p /var/log/masterha/
```

manager 서버에 설정파일을 만든다.
```
[server default]
# mysql user and password
user = mha              // 아까권한을 부여한 mha용 mysql 계정
password = mhapass      // 패스워드

# ssh user
ssh_user = root         // ssh로 접속할 계정

repl_user=repluser          //Replication 권한이 있는 계정
repl_password=repluser

# working directory on the manager
manager_workdir = /var/log/masterha

# manager log file
manager_log = /var/log/masterha.log
master_binlog_dir=/var/lib/mysql
master_ip_failover_script = /usr/local/bin/master_ip_failover
log_level=debug

# working directory on MySQL servers
remote_workdir = /var/log/masterha  //로그파일등이 저장될 위치

[server1]               //서버 정보
# master1
hostname=18.227.225.442
port=3306

[server2]
# slave1
hostname=54.185.37.228
port=3306
```
haproxy 시작
```
haproxy -f /etc/haproxy/haproxy.cfg
```

mha 시작
```
masterha_manager --conf=/var/log/masterha/test.conf
```

daemontool 로 mha 구동
Mha가 모니터링 하다가 Master에 문제가 있을시, Slave를 Master로 승격시킨다.

MHA Failover시 Haproxy를 이용한 LoadBalancing
1. Failover 발생시 새롭게 승격된 Master로 LoadBalancing 설정을 해야 서버 script단에서 정상적으로 Mysql에 접근할 수 있다.
2. 현재 mha설정에 의해 failover시 실행할 스크립트는 master_ip_failover이다.

mha.conf
```
master_ip_failover_script = /usr/local/bin/master_ip_failover
```
3. 이 스크립트가 실행될때 haproxy 설정을 변경하고 재시작 해주는 스크립트를 작성하면 된다.
```
$ nano /usr/local/bin/master_ip_failover
```
```
.
.
.
elsif ( $command eq "start" ) {

    my $exit_code = 10;
    eval {
      my $new_master_handler = new MHA::DBHelper();
        
        
        ///////// 이부분을 추가한다. 즉 새롭게 선정된 마스터 ip에 따라 haproxy설정의 master를
                  그 아이피로 바꾸어 주는 미리짜놓은 Shell Script를 실행하는 것이다.
                  해당 Shell script는 haproxy설정을 바꿔주는 스크립트이다.

	if($new_master_ip eq "54.85.7.238"){      
	system("sh /etc/haproxy/newmaster54_85_7_238.sh");
	}

        /////////
	
        $new_master_handler->connect( $new_master_ip, $new_master_port,
        $new_master_user, $new_master_password, 1 );

      ## Set read_only=0 on the new master
      $new_master_handler->disable_log_bin_local();
      print "Set read_only=0 on the new master.\n";
      $new_master_handler->disable_read_only();

      ## Creating an app user on the new master
      print "Creating app user on the new master..\n";
      #FIXME_xxx_create_user( $new_master_handler->{dbh} );
      $new_master_handler->enable_log_bin_local();
      $new_master_handler->disconnect();

      ## Update master ip on the catalog database, etc
     # FIXME_xxx;

      $exit_code = 0;
    };
    if ($@) {
      warn $@;

      # If you want to continue failover, exit 10.
      exit $exit_code;
    }
    exit $exit_code;
  }
  .
  .
  .
```
변경되는 마스터의 각 경우마다 haproxy 설정파일을 작성해놓고 cp로 덮어쓴 후, haproxy service를 재시작하는 Shell Script이다.
```
$ cat /etc/haproxy/newmaster54_85_7_238.sh

cp /etc/haproxy/newmaster54_85_7_238 /etc/haproxy/haproxy.cfg
service haproxy restart
```
```
$ cat /etc/haproxy/newmaster54_85_7_238
```
```
defaults
 log global
# mode http
 timeout connect 5000
 timeout client 50000
 timeout server 50000

listen mysql-master
 bind *:5000
 mode tcp
 option mysql-check user haproxy_check
 balance roundrobin
 server mysql1 54.85.7.238:3306 check

listen stats
bind 0.0.0.0:80       #Listen on all IP's on port 9000
    mode http
    balance
    timeout client 5000
    timeout connect 4000
    timeout server 30000

    #This is the virtual URL to access the stats page
    stats uri /haproxy_stats

    #Authentication realm. This can be set to anything. Escape space characters with a backslash.
    stats realm HAProxy\ Statistics

    #The user/pass you want to use. Change this password!
    stats auth spryfit:spryfit

    #This allows you to take down and bring up back end servers.
    #This will produce an error on older versions of HAProxy.
    stats admin if TRUE
```
디비 에러를 수정하여 초기설정으로 돌릴때 haproxy설정 초기파일도 작성을 해놓고 cp를 이용해 초기화 하고 재시작한다.
* * * 

Redis 이중화

redis master, slave 설정

```
$ cd /etc/redis
$ nano redis.conf
```
Master config
```
bind 0.0.0.0                    >> 외부에서 접근 허용
requirepass mypassword           >> 접근시 비밀번호
```

Slave config
```
slaveof 3.16.136.104 6379       >> Master 서버 정보
masterauth mypassword            >> Master 서버 redis 비밀번호
requirepass mypassword          >> 비밀번호
```
이렇게 설정을 하면 Master, Slave Replication 설정이 완료되고 slave는 read만 가능하다.

slave 서버는 Read만 가능하다. 따라서 Master redis서버가 다운됐을때 write를 못하는 문제가 생긴다. 해당 문제를 해결하기위해 Master 서버 장애시 redis Slave를 Master로 승격시켜야한다. 이기능을 지원해주는 것이 Sentinel이다.

Sentinel을 설치한다
```
$ sudo apt-get install redis-sentinel
```

Sentinel 사용시 Master가 죽으면 Slave가 Master가 되고 죽었던 Master가 살아나면 새로운 Master의 Slave가 된다. 즉 현재 Master도 새로운 Slave에 접근 할 수 있어야한다. 

Reids Master의 설정파일을 열어 다음을 추가해 준다.
```
masterauth = mypassword
```
이로서 Master가 죽었다 살아나 Slave가 됐을때, 새로운 Master의 Slave로 동작 하게된다.

Sentinel은 Master, Slave 모두에 설치, 설정 해준다.
```
$ sudo nano sentinel.conf
```
```
# Example sentinel.conf
daemonize yes
pidfile "/var/run/sentinel/redis-sentinel.pid"
logfile "/var/log/redis/redis-sentinel.log"

port 26378                      >> Sentinel을 올릴 Port

dir "/var/lib/redis"

sentinel myid 1e5afbbc551feecf2c7dd5fef26e468c64716b0d

sentinel deny-scripts-reconfig yes

sentinel monitor mymaster 3.16.136.104 6379 1   >> Monitor할 Master 정보
sentinel down-after-milliseconds mymaster 5000  >> 마스터 서버 다운 5초후 작동한다.
sentinel auth-pass mymaster mypass          >> 비밀번호
sentinel config-epoch mymaster 20
sentinel leader-epoch mymaster 20

sentinel known-slave mymaster 3.16.57.148 6379      >> Slave정보

sentinel current-epoch 20
```

```
sentinel monitor mymaster 3.16.136.104 6379 1 
에서 맨 마지막 숫자 1은 투표자들의 수를 의미한다. 즉 1의 의미는 마스터를 제외한 센티널이 2개가 있다는 뜻이다. 투표권자들은 홀수를 권장한다. 마스터가 죽었을때 투표권자들 즉 슬레이브들이 투표를 하여 다음마스터를 선정하는데 과반수에 의해 결정되므로 홀수로 설정하는것이 좋다.
```

이로서 Redis Master, Slave는 Master 서버 다운시, Sentinel에 의해 Master Slave를 재구성 한다.

 하지만 이렇게 재구성 되면 어플리케이션 단에서는 바뀐것을 어떻게 알 수 있을까. Slave는 Read만 가능하므로 새로 선정된 Master 정보를 알지 못하면 서버에서 역할을 수행하는데 무리가 있다.

  이를 해결하기 위해 haproxy를 구성한다.

Haproxy

Haproxy 설치
```
$ sudo apt-get install haproxy
```
Haproxy Loadbalancing 설정
```
$ cd /etc/haproxy
$ nano haproxy.cfg
```

```
defaults REDIS
 mode tcp
 timeout connect  4s
 timeout server  15s
 timeout client  15s
 timeout tunnel 365d

frontend ft_redis_master
 bind *:5000 name redis                 // Redis Master는  5000번 포트에 연결
 default_backend bk_redis_master

backend bk_redis_master
 option tcp-check
 tcp-check send AUTH\ mypassword\r\n    // Redis에 접근하기 위한 비밀번호
 tcp-check expect string +OK
 tcp-check send PING\r\n
 tcp-check expect string +PONG
 tcp-check send info\ replication\r\n
 tcp-check expect string role:master    // master
 tcp-check send QUIT\r\n
 tcp-check expect string +OK

 server R1 3.16.136.104:6379 check inter 1s     
 server R2 3.16.57.148:6379 check inter 1s      // health check할 서버들

frontend ft_redis_slave
 bind *:5001 name redis                 //Redis Slave는 5001번 포트에 연결
 default_backend bk_redis_slave

backend bk_redis_slave
 option tcp-check
 tcp-check send AUTH\ mypass\r\n        // Redis에 접근하기 위한 비밀번호
 tcp-check expect string +OK
 tcp-check send PING\r\n
 tcp-check expect string +PONG
 tcp-check send info\ replication\r\n
 tcp-check expect string role:slave     // slave
 tcp-check send QUIT\r\n
 tcp-check expect string +OK

 server R1 3.16.136.104:6379 check inter 1s
 server R2 3.16.57.148:6379 check inter 1s          // health check할 서버들

listen stats
bind 0.0.0.0:80       // UI 프론트 설정. 80번포트에 연결
    mode http
    balance
    timeout client 5000
    timeout connect 4000
    timeout server 30000

    #This is the virtual URL to access the stats page
    stats uri /haproxy_stats

    #Authentication realm. This can be set to anything. Escape space characters with a backslash.
    stats realm HAProxy\ Statistics

    #The user/pass you want to use. Change this password!
    stats auth mypass:mypass        >> UI 접속 패스워드

    #This allows you to take down and bring up back end servers.
    #This will produce an error on older versions of HAProxy.
    stats admin if TRUE
```
마스터, 슬레이브 상태 및 마스터 다운시 새로운 마스터가된 인스턴스의 상태도 알 수 있다.
<img width="1440" alt="screen shot 2018-12-17 at 2 25 52 pm" src="https://user-images.githubusercontent.com/37579650/50068114-ba971180-0207-11e9-8581-5129e5b0aca7.png">