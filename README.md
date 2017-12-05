# Slackbot
Slack plugin for tipping each other with UTCoin

Inspired by [OKIMOCHI](https://github.com/campfire-inc/OKIMOCHI) (&copy; CAMPFIRE and Joe Miyamoto).

## Setup
### 1. Download UTCoin
```
git clone https://github.com/m1nam1/UTCoin.git
```

### 2. Install packages
```
cd UTCoin
yarn # or npm install
```

### 3. Deploy UTCoin
Ropsten にデプロイする場合
```
truffle migrate --network ropsten
```

既にデプロイされた UTCoin を使う場合は、上のコマンドを実行する代わりに、その migrate 時に生成された `build` ディレクトリを使用してください。

### 4. Download utcoin-bot
```
cd .. # move out of UTCoin
git clone https://github.com/m1nam1/utcoin-bot.git
```

### 5. Install packages
```
cd utcoin-bot
yarn # or npm install
```

### 6. Add artifacts
```
mkdir artifacts
cp ../utcoin/build/contracts/UTCoin.json artifacts
```

### 7. Create config.js
```
cd .. # move to root
vi config.js
```

以下の内容で保存
```
// Ropsten
exports.utcoin_address = '0x...'; // デプロイされた UTCoin のアドレス
exports.deposit_address = '0x...'; // デポジットとして使いたいアドレス
```

### 8. Run Slackbot
あらかじめ Slack で bot のトークンを取得しておいてください。
```
token=[slackbot token] node bot.js
```

## Usage
以下は Slack での操作です。

監視させたいチャンネルに Bot を招待します。
```
/invite @utcoin-bot
```

Bot が招待されたチャンネルで reaction が発生すると、reaction されたユーザーに一定の UTCoin が送金されます。

チップ量を変更するには、`bot.js` の `tip_amount` の値を変更してください。 (default = 10)

### Commands
The commands are activated by direct message or direct mention.

- Help
```
help
```

- Ping
```
hi # or hello
```

- Register address
```
set my address to 0x...
```

- Display address
```
my address
```

- Display UTCoin balance
```
my balance
```

- Display deposit balance
```
deposit balance
```

- Transfer UTCoin (Only direct message)
```
send [amount] UTC to @[username]
```
