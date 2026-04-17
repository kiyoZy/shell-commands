


find *.log -mtime -8 -mtime +0

zip test.zip `find *.log -mtime -8 -mtime +0`


df -h | grep export


LANG=en_US


●
man
which

●メモリ
/usr/sbin/prtconf | grep Memory

ps aux


●bit数確認

isainfo -v
isainfo -b


●搭載リソース確認

Solaris	/usr/sbin/prtdiag

RedHat	cat /proc/meminfo

●バージョン確認

Solaris	uname -a

CentOS
 OS	cat /etc/redhat-release
 カーネル	uname -r
 カーネルバージョン	cat /proc/version


●構文チェック
service httpd configtest
httpd -t

●ファイルディスクリプタ

0	標準入力
1	標準出力
2	標準エラー出力

●
 1>&2	標準出力を標準エラー出力にマージする
 2>&1	逆

#!/bin/bash

./	ここ




●ソースからインストール

例）vim

cd src
/usr/local/src/vim/rc

・MakeFile作成
sudo ./configure


・コンパイル
sudo make

・インストール
sudo make install


・バージョン確認

vim --version



●yum
yum list installed <***>	インストール済みパッケージ

yum list updates	アップデート可能なパッケージ
yum update <***>	アップデート
yum list <***>	インストールリスト
yum list available	利用可能なパッケージ




●行数を数える

wc -l /test.sh


●awk（オーク）

awk '{print $2}'
aaa bbb ccc
 →　bbb

ls -l | awk'{print $1}'
→1個目の内容が表示される

IS_ALIVE=`ping ${DNS_NAME} | awk'{print $3}'

ダメ
awk` ps -ef | grep aaa | grep -v grep | $8`

ps aux | grep jdk | grep aaa | grep -v grep | awk'{print $1, $2, $3}'

ls | awk'{print $0, `date`}'


ls | awk'{print strftime("%Y-%m-%d"), $0}'



●nawk（エヌオーク）

/usr/jdk/jdk1.8***/bin/jstat gcutil <pid 28973> <time 2000> | nawk'{print("%s | ", $0);system("date")}'


●cron

分　時　日　月　曜

sun mon tue wed
0     1     2     3



●find

find -L ./***	全フォルダ検索

CP_LOGS=`find -L ./ -name "<***>" -mtime -1`		今日のファイルスタンプのファイル

特定の文字を含むファイルリストを取得

find /aaa/bbb -type -print | xargs grep '<文字列>'



●function（関数）とメール

function は省略可能

say_hello() {
 echo "Hello, $1 and $2 !"
}


function aertMail() {
 mailx -s "aaa ${SERVER_NAME}" -r ${MAIL_FROM} ${MAIL_CC} ${MAIL_TO} << END
Unable to onfirm connestion to ${SERVER_NAME}.
Check server status and network.

`exit`
END
}



そのまま書けば呼び出し

alertMail



function 関数名() {

 return 値
}




●使用ポート確認

netstat -a


●

system start httpd



●バックグラウンド実行

sh ***.sh &


●比較　は半角空白を入れる

if[ $i = 10] ; then

比較演算子の場合は2重にする

if[${j} -gt "1"]; then

if[[ ${j} > "1" ]]; then


ダメ
if[[ ${AAA} != 0 ]]; then

こっちで書く
if[ ${AAA} != 0 ]; then



●ループ

#!/bin/bash

i=0
#while true
while [[ $i -lt 3]]
do
 i=$((i+1))
done



MAX=7
echo "test"
for((i=0; i<${MAX}; i++)); do
 echo $i
 sleep 4
done


