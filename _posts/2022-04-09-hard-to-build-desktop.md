---
title: 自作PCを組もう！ ─ ハード編 ─
---

思うところあって(ない)、
自宅で自作PCを初めて組み立てた。
その流れをここに記す。
なお筆者の腕は、
高スペックPCの自作は初心者であり、
バイトの一環でデスクトップを組み立てたり自身のラップトップのファンやキーボードを交換したりした程度である。

## 1. パーツ選び

最初はパーツ選び。
目的は高負荷ゲームでもサクサク動くスペックとする。
今回は自作初心者ということもあり玄人にしか扱えない部品は避けたかったので、
多少高くても扱いやすそうなものやネット上に組み立て作業動画がアップロードされているものを選択した。
また、
部品を買うときはKeepaアプリで価格を年単位で見たり（Close-up viewは無効化）、
価格.comサイトの価格推移グラフを見たりして参考にした。
以下が選択したものとその購入日時と価格。

- Fractal Design Define 7 Black TG FD-C-DEF7A-02
  - PCケース
  - 2021/01/19
  - 21,864円
- AMD Ryzen 9 5950X
  - CPU
  - 2022/02/04
  - 98,799円
- Crucial Ballistix 64GB Kit (2 x 32GB) DDR4-3200 Desktop Gaming Memory BL2K32G32C16U4B
  - メモリ
  - 2020/12/20
  - 35,185円
- MSI Radeon RX 6800 XT GAMING X TRIO 16G
  - グラフィックボード（以下、GPUと呼ぶ）。
    予定ではGPUは真っ黒なノーマルの6800 XTを買う予定だったが、
    半導体不足により年単位で入手機会がなかったため今回のノーマル+5万円な代替を買った。
  - 2022/01/31
  - 149,897円
- MSI MEG B550 UNIFY
  - マザーボード（以下、MBと呼ぶ）
  - 2021/02/06
  - 29,800円
- Noctua NH-D15 chromax.black（CPUグリス付き）
  - CPUファン。別色のが有名だが、黒で統一したかったのでこっちにした。
  - 2021/01/15
  - 13,057円
- Fractal Design ION+ 860P FD-PSU-IONP-860P-BK
  - 電源ユニット
  - 2020/12/20
  - 20,955円
- Samsung 860 EVO 1TB SATA 2.5
  - SATA系SSD
  - 2020/11/27
  - 9,980円 を2つ。一つはWindowsを、もう一つはLinuxを入れる。
- Windows 10 Home USB
  - すぐ11にする。
  - 2022/02/16
  - 17,207円

以上の計40万6,724円、全財産の5/3を注ぎ込んだ。

## 1. 組み立て

各部品の公式マニュアルや実組み立ての動画を確認した上で、次の流れで実行した。

### 1.1. MBにCPUを設置

やるだけ。

### 1.2. MBにメモリを設置

4つのメモリスロットに対して2つのメモリを入れる。
取り付ける推奨位置はマニュアルに書いてあり、
今回のMBだとDIMMA2, DIMMB2に入れる。

### 1.3. PCケースにMBを設置

今回は大きいCPUファンを付けるので先に付けた。

### 1.4. CPUファンをMBに設置

2つのデカいファンを付ける。
CPUファンから伸びるケーブル2つをYケーブル1つにまとめ、
MBのコネクタ1つに挿す。
今回は付属のLow-Noise Adaptorsも付けてみることにした。

### 1.5. SATA SSDをPCケースに設置

背面に付けた。

### 1.6. 電源ユニットをPCケースに設置しケーブル配線を決める

ここが一番時間かかる。
必要なケーブル全部を付けた電源ユニットをPCケースに固定した後ケーブルをなんとかして最終位置に伸ばしておく。
今回の構成では次のケーブルを使った。

- ATX 24ピン。MBに。
- ATX 12V（4 + 4ピン）。MB（CPU）に。
- SATA / PERIPHERAL。SSDに。
- PCI-E（6 + 2ピン）。GPUに。

名前とピン数が同じでもピン分離の数が異なるのがあるのでそれに注意する。

### 1.7. GPUを除いたケーブルを接続

上記ケーブルを適切な場所に接続する。
加えて、今回のPCケースだと[Nexus+ 2 Fan Hub](https://www.fractal-design.com/wp-content/uploads/2020/02/Define_7_Manual-V2.pdf#page=21)
というPCケース付属ファンもあるため、以下のMBに接続する。

- PWM Cable。SYS_FAN1に。
- ケース出口ファン1つ。SYS_FAN6に。
- ケース入口ファン2つ。SYS_FAN2とSYS_FAN3に。

ファンにはDCとPWMという2つの回転の仕組みがありDCが3ピンでPWMが4ピンだが、
3ピンを4ピンに挿すこともできる。
その場合ピンを右詰めに挿すか左詰めに挿すかだが、
このMBコネクタは正解でしか挿せないよう物理的に設計されているため間違えることはない。

### 1.8. GPUをMBに設置しケーブル接続

最後にGPUをPCケースに固定した後、伸ばしてたケーブルに挿す。これで完成。

## 2. Windowsのインストール

USB Flash Diskタイプので入れた。入れた後に次の設定をした。

### 2.1. Wi-Fi設定

自宅環境は ~28Mbps しかないため有線でも無線でも速度は変わらない。無線を優先する。
今回のMBにはアンテナが付いているため、firmwareを更新すればすぐ使えるようになった。

### 2.2. LED調整

デフォではGPUのLEDが一定周期で虹色に光ってて、目が痛い。
ここはラブホではないのでアプリで消す。
[MEG B550 UNIFYのユーティリティ](https://jp.msi.com/Motherboard/MEG-B550-UNIFY/support#utility)
が出しているMSI Centerをインストールし、
LED Styleを `Steady`、Colorを `#000000`、Brightnessを最小にすると光らなくなる。

## 3. Windows 11へのアップグレード

10から更新する前に次の設定が必要となる。

- BIOSでTPMの有効化
  - [公式サポート](https://support.microsoft.com/en-us/windows/enable-tpm-2-0-on-your-pc-1fd5a332-360d-4f46-a1e7-ae6b0c90645c)
    にあるように設定する。今回のMSI製MBだとDELETEキーでBIOSに入れる。
- Windows Insider Programへの加入
  - https://insider.windows.com で取引してBeta Channelに入る。

その後Windows Updateを実行すると11が落ちてくる。

## 4. Linuxのインストール

もう一つのディスクに各々で好きなLinuxディストリビューションを入れる。
入れる常套手順は割愛し、特筆すべき点だけここに記す。

### 4.1. Windows Fast Startup の無効化

https://windowsreport.com/disable-fast-startup-windows-11/ を参考に。

### 4.2. Wi-Fi設定

Windows側でアンテナのfirmware更新しておけばLinuxでもインストール時にWi-Fiが使える。
インストールディスクを抜いて再起動する前に必要なネットワークアプリをインストールしておけばインストールディスクなしでも繋がる。

### 4.3. Windows Boot Manager に認知されない

Linuxを入れて
[Windows Boot Manager を有効化](https://www.top-password.com/blog/enable-classic-boot-menu-in-windows-11/)
しても、sdaのWindowsがsdbのLinuxのEFIを読んでくれない
（もちろんBIOSレベルでLinuxの優先度をWindowsより上げれば立ち上げられるが、それを毎回やるのは酷く面倒）。
BootはWindowsで管理するのが幸せらしいが、
個人的経験を優先しLinux側で管理することにした。
Linuxの `systemd-boot` はWindowsのEFIを自動検知できるので、
sdaのどこか（おそらくsda1）のEFIをsdbの `/boot/EFI` に置けばアクセスできるようになる。

### 4.4. Display Managerの起動が初回だけ失敗する

Display ManagerであるLightDMを自動起動するようにして再起動したところ、
何故かLightDMが立ち上がらなかった。
検証のため別ttyに入りブートログをgrepしたところ確かにLightDMがexit 1しており、
`sudo bat /var/log/lightdm/lightdm.log` で更にログを読むと /usr/bin/X プロセスがexit 1していたため、
更に `sudo bat /var/log/Xorg.0.log`を読むと `(EE) open /dev/dri/card0: No such file or directory` とあり、
原因はドライバーが読み込めていないためだと分かった。
これの修正だが、最初はインストール忘れを疑ったがすべてちゃんと入っていた。
そこで試しに自動起動に失敗した後に手動でLightDMを起動したところ、
なんと正常に起動してしまった。
つまり、ドライバーの読み込みタイミングが遅いため最初のX立ち上げが失敗して全部失敗していた。
ドライバーを先読みさせれば修正できる。
`sudoedit /etc/mkinitcpio.conf` で`MODULES=(amdgpu)` を追加した後 `sudo mkinitcpio -p linux` でLinuxイメージを再作成したところ、
無事にXもLightDMも起動した。

## 5. 感想

適当でも自作できて良かった。

## 6. おまけ

| Images                                                                      |
| --------------------------------------------------------------------------- |
| <img src="/img/2022-04-09/img01.jpg" alt="Overall" width="800"/>            |
| <img src="/img/2022-04-09/img02.jpg" alt="Right Side" width="800"/>         |
| <img src="/img/2022-04-09/img03.jpg" alt="Left Side" width="800"/>          |
| <img src="/img/2022-04-09/img04.jpg" alt="Low-Noise Adaptors" width="800"/> |
| <img src="/img/2022-04-09/img05.jpg" alt="Front Fans" width="800"/>         |
| <img src="/img/2022-04-09/img06.jpg" alt="Back Fan" width="800"/>           |
| <img src="/img/2022-04-09/img07.jpg" alt="Test run" width="800"/>           |
