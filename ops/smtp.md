# Kọ olupin fifiranṣẹ imeeli SMTP tirẹ

## Preamble

SMTP le ra awọn iṣẹ taara lati ọdọ awọn olutaja awọsanma, gẹgẹbi:

* [Amazon SES SMTP](https://docs.aws.amazon.com/ses/latest/dg/send-email-smtp.html)
* [Ali awọsanma imeeli titari](https://www.alibabacloud.com/help/directmail/latest/three-mail-sending-methods)

O tun le kọ olupin meeli tirẹ - fifiranṣẹ ailopin, idiyele gbogbogbo kekere.

Ni isalẹ, a ṣe afihan ni igbese nipa igbese bi a ṣe le kọ olupin meeli tiwa.

## Aṣayan olupin

Olupin SMTP ti o gbalejo funrarẹ nilo IP ti gbogbo eniyan pẹlu awọn ebute oko oju omi 25, 456, ati 587 ṣiṣi.

Awọn awọsanma ti gbogbo eniyan ti o wọpọ ti dina awọn ebute oko oju omi wọnyi nipasẹ aiyipada, ati pe o le ṣee ṣe lati ṣii wọn nipa gbigbe aṣẹ iṣẹ kan, ṣugbọn o jẹ wahala pupọ lẹhin gbogbo rẹ.

Mo ṣeduro rira lati ọdọ agbalejo kan ti o ni awọn ebute oko oju omi wọnyi ṣii ati ṣe atilẹyin eto awọn orukọ ìkápá yiyipada.

Nibi, Mo ṣeduro [Contabo](https://contabo.com) .

Contabo jẹ olupese alejo gbigba ti o da ni Munich, Jẹmánì, ti a da ni 2003 pẹlu awọn idiyele ifigagbaga pupọ.

Ti o ba yan Euro bi owo rira, idiyele naa yoo din owo (olupin ti o ni iranti 8GB ati awọn CPUs 4 jẹ nipa 529 yuan fun ọdun kan, ati idiyele fifi sori akọkọ jẹ ọfẹ fun ọdun kan).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/UoAQkwY.webp)

Nigbati o ba n paṣẹ, akiyesi `prefer AMD` , ati olupin pẹlu AMD Sipiyu yoo ni iṣẹ to dara julọ.

Ni atẹle yii, Emi yoo gba VPS Contabo gẹgẹbi apẹẹrẹ lati ṣe afihan bi o ṣe le kọ olupin meeli tirẹ.

## Eto eto Ubuntu

Awọn ọna ẹrọ nibi ni Ubuntu 22.04

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/smpIu1F.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/m7Mwjwr.webp)

Ti olupin lori ssh ba han `Welcome to TinyCore 13!` (gẹgẹ bi o ṣe han ninu nọmba ni isalẹ), o tumọ si pe eto ko ti fi sii sibẹsibẹ. Jọwọ ge asopọ ssh ki o duro fun iṣẹju diẹ lati wọle lẹẹkansi.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/-qKACz9.webp)

Nigbati `Welcome to Ubuntu 22.04.1 LTS` yoo han, ipilẹṣẹ ti pari, ati pe o le tẹsiwaju pẹlu awọn igbesẹ wọnyi.

### [Iyan] Bibẹrẹ agbegbe idagbasoke

Igbese yii jẹ iyan.

Fun irọrun, Mo fi fifi sori ẹrọ ati iṣeto eto ti sọfitiwia ubuntu sinu [github.com/wactax/ops.os/tree/main/ubuntu](https://github.com/wactax/ops.os/tree/main/ubuntu) .

Ṣiṣe aṣẹ atẹle lati fi sori ẹrọ pẹlu titẹ kan.

```
bash <(curl -s https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

Awọn olumulo Kannada, jọwọ lo aṣẹ atẹle dipo, ati ede, agbegbe aago, ati bẹbẹ lọ yoo ṣeto laifọwọyi.

```
CN=1 bash <(curl -s https://ghproxy.com/https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

### Contabo jeki IPV6

Mu IPV6 ṣiṣẹ ki SMTP tun le fi imeeli ranṣẹ pẹlu awọn adirẹsi IPV6.

satunkọ `/etc/sysctl.conf`

Ṣatunṣe tabi ṣafikun awọn ila wọnyi

```
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.lo.disable_ipv6 = 0
```

Tẹle [ikẹkọ contabo: Ṣafikun Asopọmọra IPv6 si olupin rẹ](https://contabo.com/blog/adding-ipv6-connectivity-to-your-server/)

Ṣatunkọ `/etc/netplan/01-netcfg.yaml` , fi awọn ila diẹ kun bi o ṣe han ninu nọmba ti o wa ni isalẹ (faili iṣeto aiyipada Contabo VPS ti ni awọn ila wọnyi, o kan ko ṣe akiyesi wọn).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/5MEi41I.webp)

Lẹhinna `netplan apply` lati jẹ ki iṣeto ni ipa.

Lẹhin ti iṣeto ni aṣeyọri, o le lo `curl 6.ipw.cn` lati wo adiresi ipv6 ti nẹtiwọọki ita rẹ.

## Ops ibi ipamọ iṣeto ni oniye

```
git clone https://github.com/wactax/ops.soft.git
```

## Ṣẹda ijẹrisi SSL ọfẹ fun orukọ ìkápá rẹ

Fifiranṣẹ meeli nilo ijẹrisi SSL fun fifi ẹnọ kọ nkan ati wíwọlé.

A lo [acme.sh](https://github.com/acmesh-official/acme.sh) lati ṣe awọn iwe-ẹri.

acme.sh jẹ ohun elo iforukọsilẹ adaṣe adaṣe orisun ṣiṣi,

Tẹ ile-ipamọ atunto ops.soft, ṣiṣe `./ssl.sh` , ati pe folda `conf` yoo ṣẹda ninu **itọsọna oke** .

Wa olupese DNS rẹ lati [acme.sh dnsapi](https://github.com/acmesh-official/acme.sh/wiki/dnsapi) , edit `conf/conf.sh` .

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Qjq1C1i.webp)

Lẹhinna ṣiṣe `./ssl.sh 123.com` lati ṣe ipilẹṣẹ `123.com` ati `*.123.com` awọn iwe-ẹri fun orukọ ìkápá rẹ.

Ibẹrẹ akọkọ yoo fi [acme.sh](https://github.com/acmesh-official/acme.sh) sori ẹrọ laifọwọyi ati ṣafikun iṣẹ ṣiṣe eto fun isọdọtun laifọwọyi. O le wo `crontab -l` , iru ila kan wa bi atẹle.

```
52 0 * * * "/mnt/www/.acme.sh"/acme.sh --cron --home "/mnt/www/.acme.sh" > /dev/null
```

Ọna fun ijẹrisi ti ipilẹṣẹ jẹ nkan bii `/mnt/www/.acme.sh/123.com_ecc。`

Isọdọtun ijẹrisi yoo pe `conf/reload/123.com.sh` script, satunkọ iwe afọwọkọ yii, o le ṣafikun awọn aṣẹ bii `nginx -s reload` lati sọ kaṣe ijẹrisi ti awọn ohun elo ti o jọmọ.

## Kọ olupin SMTP pẹlu chasquid

[chasquid](https://github.com/albertito/chasquid) jẹ olupin SMTP orisun ṣiṣi ti a kọ ni ede Go.

Gẹgẹbi aropo fun awọn eto olupin meeli atijọ gẹgẹbi Postfix ati Sendmail, chasquid rọrun ati rọrun lati lo, ati pe o tun rọrun fun idagbasoke atẹle.

Ṣiṣe `./chasquid/init.sh 123.com` yoo fi sori ẹrọ laifọwọyi pẹlu titẹ kan (rọpo 123.com pẹlu orukọ ìkápá fifiranṣẹ rẹ).

## Ṣe atunto Ibuwọlu Imeeli DKIM

DKIM ni a lo lati fi awọn ibuwọlu imeeli ranṣẹ lati ṣe idiwọ awọn lẹta lati ni itọju bi àwúrúju.

Lẹhin ti aṣẹ naa nṣiṣẹ ni aṣeyọri, iwọ yoo ti ọ lati ṣeto igbasilẹ DKIM (gẹgẹbi a ṣe han ni isalẹ).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/LJWGsmI.webp)

Kan ṣafikun igbasilẹ TXT kan si DNS rẹ (gẹgẹbi a ṣe han ni isalẹ).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/0szKWqV.webp)

## Wo ipo iṣẹ & awọn akọọlẹ

 `systemctl status chasquid` Wo ipo iṣẹ.

Ipo ti iṣẹ ṣiṣe deede jẹ bi o ṣe han ninu nọmba ni isalẹ

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/CAwyY4E.webp)

 `grep chasquid /var/log/syslog` tabi `journalctl -xeu chasquid` le wo akọọlẹ aṣiṣe naa.

## Yiyipada ašẹ orukọ iṣeto ni

Orukọ ašẹ yiyipada ni lati gba adiresi IP laaye lati yanju si orukọ ašẹ ti o baamu.

Ṣiṣeto orukọ ìkápá iyipada le ṣe idiwọ awọn apamọ lati jẹ idanimọ bi àwúrúju.

Nigbati a ba gba meeli naa, olupin gbigba yoo ṣe itupalẹ orukọ ašẹ iyipada lori adiresi IP ti olupin fifiranṣẹ lati jẹrisi boya olupin fifiranṣẹ ni orukọ ìkápá iyipada to wulo.

Ti olupin ti nfiranṣẹ ko ba ni orukọ-ašẹ iyipada tabi ti orukọ-ašẹ ko ba ni ibamu pẹlu adiresi IP ti olupin ti nfiranṣẹ, olupin ti n gba le da imeeli naa mọ bi àwúrúju tabi kọ ọ.

Ṣabẹwo [https://my.contabo.com/rdns](https://my.contabo.com/rdns) ati tunto bi o ṣe han ni isalẹ

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/IIPdBk_.webp)

Lẹhin ti ṣeto orukọ ašẹ iyipada, ranti lati tunto ipinnu siwaju ti orukọ ìkápá ipv4 ati ipv6 si olupin naa.

## Ṣatunkọ orukọ olupin ti chasquid.conf

Ṣe atunṣe `conf/chasquid/chasquid.conf` si iye ti orukọ ìkápá yiyipada.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/6Fw4SQi.webp)

Lẹhinna ṣiṣe `systemctl restart chasquid` lati tun iṣẹ naa bẹrẹ.

## Afẹyinti conf si ibi ipamọ git

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Fier9uv.webp)

Fun apẹẹrẹ, Mo ṣe afẹyinti folda conf si ilana github ti ara mi gẹgẹbi atẹle

Ṣẹda ile-ipamọ ikọkọ ni akọkọ

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ZSCT1t1.webp)

Tẹ itọsọna conf ki o fi silẹ si ile-itaja naa

```
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:wac-tax-key/conf.git
git push -u origin main
```

## Fi olufiranṣẹ kun

sure

```
chasquid-util user-add i@wac.tax
```

Le fi olufiranṣẹ kun

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/khHjLof.webp)

### Daju pe ọrọ igbaniwọle ti ṣeto daradara

```
chasquid-util authenticate i@wac.tax --password=xxxxxxx
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/e92JHXq.webp)

Lẹhin fifi olumulo kun, `chasquid/domains/wac.tax/users` yoo ni imudojuiwọn, ranti lati fi silẹ si ile-itaja naa.

## DNS ṣafikun igbasilẹ SPF

SPF ( Ilana Ilana Olufiranṣẹ ) jẹ imọ-ẹrọ ijẹrisi imeeli ti a lo lati ṣe idiwọ jibiti imeeli.

O ṣe idanimọ idanimọ ti olufiranṣẹ kan nipa ṣiṣe ayẹwo pe adiresi IP olufiranṣẹ naa baamu awọn igbasilẹ DNS ti orukọ ìkápá ti o sọ pe o jẹ, idilọwọ awọn ẹlẹtan lati firanṣẹ awọn imeeli iro.

Ṣafikun awọn igbasilẹ SPF le ṣe idiwọ awọn imeeli lati jẹ idanimọ bi àwúrúju bi o ti ṣee ṣe.

Ti orukọ olupin rẹ ko ba ṣe atilẹyin iru SPF, kan ṣafikun igbasilẹ iru TXT.

Fun apẹẹrẹ, SPF ti `wac.tax` jẹ bi atẹle

`v=spf1 a mx include:_spf.wac.tax include:_spf.google.com ~all`

SPF fun `_spf.wac.tax`

`v=spf1 a:smtp.wac.tax ~all`

Ṣe akiyesi pe Mo ni `include:_spf.google.com` nibi, eyi jẹ nitori Emi yoo tunto `i@wac.tax` gẹgẹbi adirẹsi fifiranṣẹ ni apoti ifiweranṣẹ Google nigbamii.

## DNS iṣeto ni DMARC

DMARC jẹ abbreviation ti (Ijeri Ifiranṣẹ orisun-ibugbe, Ijabọ & Ibamu).

O ti wa ni lo lati Yaworan SPF bounces (boya ṣẹlẹ nipasẹ iṣeto ni aṣiṣe, tabi ẹnikan ti wa ni dibon lati wa ni o lati fi spam).

Ṣafikun igbasilẹ TXT `_dmarc` ,

Awọn akoonu jẹ bi wọnyi

```
v=DMARC1; p=quarantine; fo=1; ruf=mailto:ruf@wac.tax; rua=mailto:rua@wac.tax
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/k44P7O3.webp)

Itumọ ti paramita kọọkan jẹ bi atẹle

### p (Ìlànà)

Tọkasi bi o ṣe le mu awọn imeeli ti o kuna SPF (Ilana Ilana Olufiranṣẹ) tabi ijẹrisi DKIM (DomainKeys Identified Mail). O le ṣeto paramita p si ọkan ninu awọn iye mẹta:

* kò: Ko si igbese ti wa ni ya, nikan ni ijerisi esi ti wa ni je pada si awọn Olu nipasẹ awọn imeeli iroyin siseto.
* Quarantine: Fi meeli ti ko ti kọja ijẹrisi naa sinu folda spam, ṣugbọn kii yoo kọ meeli taara.
* kọ: Taara kọ awọn apamọ ti o kuna ijerisi.

### fun (Awọn aṣayan Ikuna)

Ṣe alaye iye alaye ti a da pada nipasẹ ẹrọ ijabọ. O le ṣeto si ọkan ninu awọn iye wọnyi:

* 0: Jabọ afọwọsi esi fun gbogbo awọn ifiranṣẹ
* 1: Nikan jabo awọn ifiranṣẹ ti o kuna ijerisi
* d: Nikan jabo ašẹ orukọ ijerisi ikuna
* s: nikan jabo SPF ijerisi ikuna
* l: Nikan jabo awọn ikuna ijerisi DKIM

### rua & ruf

* rua (URI Ijabọ fun awọn ijabọ apapọ): Adirẹsi imeeli fun gbigba awọn ijabọ akojọpọ
* ruf (URI ijabọ fun awọn ijabọ iwaju): adirẹsi imeeli lati gba awọn ijabọ alaye

## Ṣafikun awọn igbasilẹ MX lati firanṣẹ awọn imeeli si Mail Google

Nitoripe Emi ko le rii apoti leta ile-iṣẹ ọfẹ ti o ṣe atilẹyin awọn adirẹsi gbogbo agbaye (Catch-All, le gba awọn imeeli eyikeyi ti a fi ranṣẹ si orukọ ìkápá yii, laisi awọn ihamọ lori awọn ami-iṣaaju), Mo lo chasquid lati firanṣẹ gbogbo awọn imeeli si apoti ifiweranṣẹ Gmail mi.

**Ti o ba ni apoti ifiweranṣẹ iṣowo ti ara rẹ, jọwọ ma ṣe yipada MX ki o foju igbesẹ yii.**

Ṣatunkọ `conf/chasquid/domains/wac.tax/aliases` , ṣeto apoti ifiweranṣẹ

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/OBDl2gw.webp)

`*` tọkasi gbogbo awọn apamọ, `i` jẹ asọtẹlẹ adirẹsi imeeli ti olumulo fifiranṣẹ ti o ṣẹda loke. Lati dari meeli, olumulo kọọkan nilo lati ṣafikun laini kan.

Lẹhinna ṣafikun igbasilẹ MX (Mo tọka taara si adirẹsi ti orukọ ašẹ yiyipada nibi, bi a ṣe han ni laini akọkọ ni nọmba ni isalẹ).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/7__KrU8.webp)

Lẹhin ti iṣeto ti pari, o le lo awọn adirẹsi imeeli miiran lati fi imeeli ranṣẹ si `i@wac.tax` ati `any123@wac.tax` lati rii boya o le gba awọn imeeli wọle ni Gmail.

Ti kii ba ṣe bẹ, ṣayẹwo akọọlẹ chasquid ( `grep chasquid /var/log/syslog` ).

## Fi imeeli ranṣẹ si i@wac.tax pẹlu Google Mail

Lẹhin ti Google Mail gba meeli naa, Mo nireti nipa ti ara lati dahun pẹlu `i@wac.tax` dipo i.wac.tax@gmail.com.

Ṣabẹwo [https://mail.google.com/mail/u/1/#settings/accounts](https://mail.google.com/mail/u/1/#settings/accounts) ki o tẹ "Fi adirẹsi imeeli miiran kun".

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/PAvyE3C.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/_OgLsPT.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/XIUf6Dc.webp)

Lẹhinna, tẹ koodu ijẹrisi ti o gba nipasẹ imeeli ti o firanṣẹ si.

Nikẹhin, o le ṣeto bi adiresi olufiranṣẹ aiyipada (pẹlu aṣayan lati dahun pẹlu adirẹsi kanna).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/a95dO60.webp)

Ni ọna yii, a ti pari idasile olupin meeli SMTP ati ni akoko kanna lo Google Mail lati firanṣẹ ati gba awọn imeeli.

## Fi imeeli ranṣẹ lati ṣayẹwo boya iṣeto ni aṣeyọri

Tẹ `ops/chasquid` sii

Ṣiṣe `direnv allow` lati fi awọn igbẹkẹle sii (direnv ti fi sori ẹrọ ni ilana ibẹrẹ bọtini ọkan ti tẹlẹ ati pe o ti ṣafikun kio kan si ikarahun naa)

lẹhinna ṣiṣe

```
user=i@wac.tax pass=xxxx to=iuser.link@gmail.com ./sendmail.coffee
```

Itumọ ti awọn paramita jẹ bi atẹle

* olumulo: SMTP orukọ olumulo
* kọja: SMTP ọrọigbaniwọle
* to: olugba

O le fi imeeli idanwo ranṣẹ.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ae1iWyM.webp)

A ṣe iṣeduro lati lo Gmail lati gba awọn imeeli idanwo lati ṣayẹwo boya awọn atunto jẹ aṣeyọri.

### TLS boṣewa ìsekóòdù

Bi o ṣe han ninu nọmba ti o wa ni isalẹ, titiipa kekere wa, eyiti o tumọ si pe ijẹrisi SSL ti ṣiṣẹ ni aṣeyọri.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/SrdbAwh.webp)

Lẹhinna tẹ "Fi Imeeli Atilẹba han"

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/qQQsdxg.webp)

### DKIM

Gẹgẹbi a ṣe han ninu nọmba ti o wa ni isalẹ, oju-iwe meeli atilẹba Gmail n ṣe afihan DKIM, eyiti o tumọ si pe iṣeto DKIM jẹ aṣeyọri.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/an6aXK6.webp)

Ṣayẹwo Ti gba ni akọsori ti imeeli atilẹba, ati pe o le rii pe adirẹsi olupin jẹ IPV6, eyiti o tumọ si pe IPV6 tun tunto ni aṣeyọri.
