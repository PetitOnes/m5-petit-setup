# M5 Petit Setup

![ぷちたち](./img/petit-ones.jpeg)

ぷちたちに興味を持っていただきありがとうございます！
ここではぷちたちをお迎えする手順を紹介していきます。
WebPage(工事中)やYoutube(準備中)も見ながら勧めていくことをおすすめします。

# 目次

下を順番にやっていくとぷちたちをお迎えできます。

1. ボディ/付属品を買う
2. embodied-claudeの設定
3. m5-petit-mcpの設定
4. ボディを組み立て・書き込み設定
5. Webアプリで会話してみる

<br>

# 詳細

## 1. ボディ/付属品を買う

[SWITCH SCIENSE](https://www.switch-science.com/)から購入します。

最低限必要なものはボディ＋電池＋SDカードの3つ(合計 約¥14,011〈推奨構成〉、電池をバッテリーボトムにすると約¥14,264)です。


1. ボディ

    - [M5Stack CoreS3 - ESP32S3 IoT開発キット](https://www.switch-science.com/products/8960)
        - ¥10,868（税込）(2026/7/1)
        - 距離・光・傾きセンサーがこの中に入っていて高性能です！

2. ボディにつける電池
    
    ボディだけでは常に充電につないでおかないといけません。
そのために、ボディにつける電池を購入します。**２種類の中から好きな方を選んでください。(推奨上)**

    - [M5Core用ウォッチデバイス化キット v1.1 (オレンジ)](https://www.switch-science.com/products/9492)
        - ¥1,419 （税込）(2026/7/1)
        - 700mAh
        - 腕時計にしなくてもok

    - [M5Stack CoreS3用バッテリーボトム](https://www.switch-science.com/products/9421)
        - ¥1,672 （税込）(2026/7/1)
        - 500mAh
        - 裏に磁石がついていて[別チャージベース](https://www.switch-science.com/products/6536)でぴたっと充電できます


3. SDカード

    ぷちたちが音を出したり、画層を出したりするのに必要です。
    4GBくらいあれば十分です

    - 例：
    [Amazon KIOXIA(キオクシア) 旧東芝メモリ microSD 32GB UHS-I Class10 (最大読出速度100MB/s) Nintendo Switch動作確認済 国内サポート正規品 メーカー保証5年 KLMEA032G](https://amzn.asia/d/02UegyVE)
        - ￥1,724 （税込）(2026/7/1)


**ここからはお出かけ用オプションです。**

4. トラベルWifiルータ

    ぷちたちとお出かけしたいとき

    - [GL.iNet WiFi6 トラベル ルーター GL-MT3000](https://amzn.asia/d/04nHFMZ7)
        -  ￥16,899（税込）(2026/7/1)
        - 値上がりしてるので他のものでもいいです。以下の仕様を満たすものにしてください
            - OpenWrtで動作し、TailScaleを入れるメモリ容量があること

5. モバイルバッテリー

    おなじくお出かけにあると便利です

    - [ぷち用は2500mAhで1日持ちます(Amazonリンク)](https://amzn.asia/d/0fT05k6y)
        - ￥1,739（税込）(2026/7/1)


**ここからは機能追加用オプションです。**


6. スマートウォッチ

    あなたの体調を気遣います
    例：https://amzn.asia/d/085oYwIc

7. Rover+StickC

    ぷちたちが机の上を走り回ります

    - [RoverC Pro (w/o M5StickC)](https://www.switch-science.com/products/6617)
    - [M5StickC Plus2](https://www.switch-science.com/products/9350)

8. ミニプリンター

    ぷちたちの見たものを印刷できます

## 2. embodied-claudeの設定

ぷちたちの「頭脳」となる embodied-claude をセットアップします。

https://github.com/lifemate-ai/embodied-claude

```bash
git clone https://github.com/lifemate-ai/embodied-claude.git
cd embodied-claude
```

uv・Claude Code CLIのインストールなど、詳しいセットアップ手順はembodied-claude側のREADMEを参照してください。

## 3. m5-petit-mcpの設定

ぷち(M5デバイス)をClaudeから操作できるようにするMCPサーバーです。

https://github.com/PetitOnes/m5-petit-mcp

```bash
git clone https://github.com/PetitOnes/m5-petit-mcp.git
cd m5-petit-mcp
uv sync
```

Claude Codeの`.mcp.json`(またはembodied-claude側のMCP設定)に`m5-petit-mcp`を追加してください。詳細はリポジトリのREADMEを参照。

## 4. ボディを組み立て・書き込み設定

1. 電池・SDカードをボディに取り付ける
2. ファームウェア(.ino)を書き込む — ファームウェアは m5-petit-scripts にあります

https://github.com/PetitOnes/m5-petit-scripts

```bash
git clone https://github.com/PetitOnes/m5-petit-scripts.git
```

`credentials.example.h`を`credentials.h`にコピーしてWiFi/WireGuard情報を書き込み、Arduino IDEまたはPlatformIOで書き込んでください。

> 🚧 ファームウェアのテンプレートは準備中です。

## 5. Webアプリで会話してみる

ここまでできたら、ダッシュボードアプリを起動してぷちと会話できます。

https://github.com/PetitOnes/m5-petit-app

```bash
git clone https://github.com/PetitOnes/m5-petit-app.git
cd m5-petit-app
uv sync
uv run m5-petit-app
```

`http://localhost:8765`を開いて「💬 会話」タブからぷちに話しかけてみましょう！
