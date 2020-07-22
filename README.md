# Rails + API + Vagrant
- 見たままのボイラープレート　

## 実行環境
- Vagrant
- VirtualBox

### 環境構築
- VirtualBoxのインストール
  - https://www.virtualbox.org/wiki/Downloads
  - Homebrew使ってる人は`brew cask install virtualbox`で入ると思う
- Vagrantのインストール
  - https://www.vagrantup.com/downloads
  - Homebrewの人は`brew cask install vagrant`

## 使い方　
- 詳しく知りたい人は`Vagrant使い方`などで調べてください
- **`vagrant`コマンドは`Vagrantfile`があるディレクトリ(クローンしてきたリポジトリ)で実行する前提とします**

### リポジトリの準備
- GitHub上でUse this templateボタンを押してこのリポジトリを元に自分のリポジトリを作成する
  - 既にしてる人は何もしなくて良い
- 作成したリポジトリをローカルにクローンする

### 仮想マシンの起動
- `vagrant up`
  - 初回は時間かかるのでコーヒーでも淹れて待ちましょう
  
### 仮想マシンの停止
- `vargant halt`

### 仮想マシンの中に入る
- `vagrant ssh`
- これを実行すると仮想マシンに接続できるので、その中で`rails`コマンドや`bundle`コマンドが使えます

### 仮想マシンの削除
- `vagrant destroy`
  - これするとデータベースのデータも消えるので注意
  
### ブラウザからアクセス
- `vagrant port`で出てきた`22 (guest) => 2222 (host)`じゃない方の`(host)`側のポート番号を確認 (恐らく3000)
- `http://localhost:確認したポート番号`で接続できる