# SiftScan

<p align="center">
  <a href="./README_ZH.md">Chinese</a> •
  <a href="https://twitter.com/ExpLang_Cn">@ExpLang_Cn</a>
</p>

SiftScan is a tool that integrates asset identification, asset combing, asset collection, weakness detection, vulnerability detection, etc. It is committed to improving the efficiency of red-blue confrontation/vulnerability bounty.

## Instructions for use

### Config.yaml

```yaml
Control:
  IsHttp: false # Both HTTP(s) are saved (the http and https services of some websites are different businesses)
  RespStCode: [200,301,302,403,404] # White list of response codes
  Timeout: 10 # Request timeout

ICPApi:
  GetICP: "" # API for obtaining unit information by domain name url:https://www.chinaz.net/mall/a_9aUhQUNiv4.html
  GetDomain: "" # Company name to obtain domain name information API url:https://www.chinaz.net/mall/a_kT1btgYqw7.html

FOFA:
  Enable: true
  Email: ""
  APIKey: ""
  Size: "10000"
  Full: true
  IfHost: true # Whether to filter subdomains (only output the main domain name that is consistent with the main domain name, if it is false, there are more false reports)

Zoomeye:
  Enable: true
  APIKEY: ""
  AssociatedDomain: false # Whether to search for related assets (more assets, more false positives, if true, more false positives)

Hunter:
  Enable: true
  IsWeb: 3 # 1: Represents "web assets", 2: represents "non-web assets", 3: represents "all"
  APIKEY: ""
  Size: 100 # The number of collected, note: it consumes points!
  AccurateSearch: true # Whether to search accurately (if it is false, there are more false reports)

Subdomain:
  Enable: true
  IsWildcard: true # Determine whether it is general analysis
  Dictionary: "simple" # Subdomain dictionary: simple (simple dictionary) or (complete dictionary)
  Silent: true # Whether to output only the domain name
  Concurrency: 100 # Blasting concurrency (the higher the network, the more it occupies the network)

PortScan:
  PortList: ["1","7","9","13","19","21","22","23","25","37","42","49","53","69","79","80","81","85","105","109","110","111","113","123","135","137","138","139","143","161","179","222","264","384","389","402","407","443","444","445","446","465","500","502","512","513","514","515","523","524","540","548","554","587","617","623","689","705","771","783","873","888","902","910","912","921","993","995","998","1000","1024","1030","1035","1090","1098","1099","1100","1101","1102","1103","1128","1129","1158","1199","1211","1220","1234","1241","1300","1311","1352","1433","1434","1435","1440","1494","1521","1530","1533","1581","1582","1604","1720","1723","1755","1811","1900","2000","2001","2049","2082","2083","2100","2103","2121","2199","2207","2222","2323","2362","2375","2380","2381","2525","2533","2598","2601","2604","2638","2809","2947","2967","3000","3037","3050","3057","3128","3200","3217","3273","3299","3306","3311","3312","3389","3460","3500","3628","3632","3690","3780","3790","3817","4000","4322","4433","4444","4445","4659","4679","4848","5000","5038","5040","5051","5060","5061","5093","5168","5247","5250","5351","5353","5355","5400","5405","5432","5433","5498","5520","5521","5554","5555","5560","5580","5601","5631","5632","5666","5800","5814","5900","5901","5902","5903","5904","5905","5906","5907","5908","5909","5910","5920","5984","5985","5986","6000","6050","6060","6070","6080","6082","6101","6106","6112","6262","6379","6405","6502","6503","6504","6542","6660","6661","6667","6905","6988","7001","7021","7071","7080","7144","7181","7210","7443","7510","7579","7580","7700","7770","7777","7778","7787","7800","7801","7879","7902","8000","8001","8008","8014","8020","8023","8028","8030","8080","8081","8082","8087","8090","8095","8161","8180","8205","8222","8300","8303","8333","8400","8443","8444","8503","8800","8812","8834","8880","8888","8889","8890","8899","8901","8902","8903","9000","9002","9060","9080","9081","9084","9090","9099","9100","9111","9152","9200","9390","9391","9443","9495","9809","9810","9812","9813","9814","9815","9855","9999","10000","10001","10008","10050","10051","10080","10098","10162","10202","10203","10443","10616","10628","11000","11099","11211","11234","11333","12174","12203","12221","12345","12397","12401","13364","13500","13838","14330","15200","16102","17185","17200","18881","19300","19810","20010","20031","20034","20101","20111","20171","20222","22222","23472","23791","23943","25000","25025","26000","26122","27000","27017","27888","28222","28784","30000","30718","31001","31099","32764","32913","34205","34443","37718","38080","38292","40007","41025","41080","41523","41524","44334","44818","45230","46823","46824","47001","47002","48899","49152","50000","50001","50002","50003","50004","50013","50500","50501","50502","50503","50504","52302","55553","57772","62078","62514","65535","82","83","84","86","88","89","90","91","99","800","801","808","880","889","1010","1980","2018","2019","3505","6677","7000","7002","7003","7005","7007","7070","7200","7890","8002","8003","8004","8006","8009","8010","8011","8012","8016","8042","8053","8060","8069","8070","8083","8084","8085","8086","8088","8089","8091","8099","8100","8118","8123","8172","8181","8200","8243","8251","8280","8281","8360","8484","8500","8879","8881","8983","8989","9001","9043","9085","9091","9800","9981","10002","10003","12443","15672","16080","18080","18082","18091","18092","20720","28017","38501","38888"]
  Concurrency: 100 # Blasting concurrency (the higher the network, the more it occupies the network)
  WeakCheck: true # Whether it is weak detection, (example: Redis empty password, etc.)

Craw:
  Depth: 5 # Reptile depth
  Retries: 3 # Number of retries requested
  Strategy: "depth-first" # Reptile strategy: depth-first or breadth-first
  ShowBrowser: false # Whether to display the browser crawler process
  OutputFile: "" # The crawler results output the file, which is empty and not output.
  Concurrency: 10 # Target concurrency
  Parallelism: 25 # Process the number of Urls at the same time
  RateLimit: 200 # Rate limit: the maximum number of requests sent per second
  ExtensionFilter: # Specify the suffix of the filter
    - "css"
    - "jpg"
    - "png"
    - "gif"
    - "ico"
    - "webp"
    - "mp3"
    - "mp4"
    - "ttf"
    - "tif"
    - "tiff"
    - "woff"
    - "woff2"
```

### Parameter

```bash
[SiftScan] Committed to improving the efficiency of red and blue confrontation/loophole bounty. By: Explang｜Twitter: @ExpLang_Cn

Usage:
  SiftScan [flags]

Flags:
      --ai string       Intelligent scanning, enter the target Url, the target can be IP | domain name | subdomain | URL, the program will automatically identify the target type, build the scanning process and scan it.
      --debug           Debug mode
  -h, --help            help for SiftScan
  -m, --mode string     Crawling mode, simple/smart/strict, default smart (default "smart")
      --proxy string    The requested agent, for the access URL outside the wall, the direct connection is empty by default.
  -t, --target string   A single URL to execute crawling
```

### Refer to

#### Scan the target file

Automatically filter target types，Use the `--ai` parameter to specify the target file.

```bash
ExpLang ⚡ cat target.txt
	http://www.xxx.com
	120.xxx.xxx.231
	xxx科技有限责任公司
ExpLang ⚡ ./SiftScan --ai target.txt
```

#### Scan the specified target

Automatically filter the target type and use the `-t` parameter to specify the target information.

```bash
ExpLang ⚡ ./SiftScan -t "xxx科技有限责任公司"
ExpLang ⚡ ./SiftScan -t "120.xxx.xxx.231"
ExpLang ⚡ ./SiftScan -t "http://www.xxx.com"
```

#### Appoint Crawling mode

```bash
ExpLang ⚡ ./SiftScan -t "xxx科技有限责任公司" -m simple
ExpLang ⚡ ./SiftScan -t "120.xxx.xxx.231" -m smart
ExpLang ⚡ ./SiftScan -t "http://www.xxx.com" -m strict
```

## Development progress

### Asset collection

- [x] Connect the FOFA API interface to collect assets, support the main domain to collect assets, IP to collect assets, unit ICP record number collection assets.
- [x] Connect to the Zoomeye API interface to collect assets, support the main domain to collect assets, and IP to collect assets.
- [x] Connect the Hunter API interface to collect assets, and support the main domain to collect assets, IP collection assets, unit name to collect assets, and unit ICP record number to collect assets.
- [x] Enumeration and explosion of subdomain names for the main domain name.
- [x] Port detection and identification of WEB titles and services for IP and subdomains.
  - [x] HTTP
  - [x] REDIS
  - [x] SSH
  - [x] MQTT3
  - [x] MODBUS
  - [x] VNC
  - [x] TELNET
  - [x] MQTT5
  - [x] FTP
  - [x] RSYNC
  - [x] SMB
  - [x] RPC
  - [x] DNS
  - [x] OracleDB
  - [x] SMTP
  - [x] RTSP
  - [x] PostgreSQL
  - [x] MQTT5
  - [x] RDP
  - [x] HTTPS
  - [x] POP3
  - [x] SMTPS
  - [x] KAFKA
  - [x] MQTT3
  - [x] MySQL
  - [x] RDP
  - [x] MSSQL
  - [x] POP3S
  - [x] LDAP
  - [x] LDAPS
  - [x] IMAP
  - [x] IMAPS
  - [x] SNMP
  - [x] Kafka
  - [x] OPENVPN
  - [x] NETBIOS-NS
  - [x] IPSEC
  - [x] DHCP
  - [x] STUN
  - [x] NTP
  - [x] DNS

### Crawling

- [x] Support retry
- [x] Crawling depth configuration

### Weakness detection

- [ ] Weakness detection for services
  - [ ] Redis empty password
  - [ ] ...
- [ ] Web fingerprint identification
- [ ] Detect Nuclei template based on Web fingerprint

⚠️ **If you have better suggestions for functions, you can explain your needs in detail through issues!**

## References

🌟 **The order does not represent any ranking.**

[**Fingerprintx**](https://github.com/praetorian-inc/fingerprintx)

[**NucleiTP**](https://github.com/ExpLangcn/NucleiTP)

[**Nuclei**](https://github.com/projectdiscovery/nuclei)

[**Katana**](https://github.com/projectdiscovery/katana)

[**Fofa**](https://fofa.info/)

[**Zoomeye**](https://www.zoomeye.org/)

[**Hunter**](https://hunter.qianxin.com/)

[**Chinaz**](https://www.chinaz.net/)

