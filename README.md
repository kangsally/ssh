# ssh



- 워크스테이션에서 터미널을 열고 `ssh-keygen` 명령어를 사용하여 새 키를 생성. `-C` 플래그를 지정하여 사용자 이름에 주석을 추가

```
ssh-keygen -t rsa -f ~/.ssh/[KEY_FILENAME] -C [USERNAME]
```

```
ssh-keygen -t rsa -f ~/.ssh/es-rsa -C sally@tag-hive.com
```

-> USERNAME은 VM에  연결하는 사용자의 이름이다.

->  es-ras 와ㅏ es-ras.pub 파일 두개가 생김 .pub이 퍼블릭 키다.



-  passphrase 는 암호화할 때 사용하는 password 같은것인데 자동생성되는 입장에서 굳이 사용하지 않아도 되는 것 같다.

 

- 아래와 같이 치면 es-rsa 와 es-rsa.pub 파일이 생겼음을 확인 가능

```
ls .ssh
```



-  아래와 같이 치면 해당 키가 400권한 여부  확인 가능  ->  즉, 자신만 비공개  키를 읽을 수 있고 다른 사람은 여기에 쓸 수만 있도록 비공개 키에 대한 액세스 권한을 제한한다.

```
ls -la .ssh
```



-  만약  400권한 아니면

```
chmod 400 ~/.ssh/[KEY_FILENAME]
```



- 공개키파일을 연다 ->  키복사

```
cat .ssh/[KEY_FILENAME]
```

```
cat .ssh/es-rsa.pub
```



- VM 메타데이터 페이지로 가서 ssh-key에 붙여넣기



-  로컬  터미널과  VM 연결

```
ssh -i PATH_TO_PRIVATE_KEY USERNAME@EXTERNAL_IP
```

```
ssh -i ~/.ssh/es-rsa sally@12.123.123.3
```





https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#createsshkeys

https://cloud.google.com/compute/docs/instances/connecting-advanced

