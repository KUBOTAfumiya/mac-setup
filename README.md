# Mac端末初期設定（フロントエンドエンジニア向け）

## Macの設定
### 不可視ファイルの表示
```
defaults write com.apple.finder AppleShowAllFiles -boolean true
killall Finder # Finder再起動
```

### ダウンロードしたすべてのアプリケーションの実行を許可
```
sudo spctl --master-enable # ダウンロードしたすべてのアプリケーションの実行を許可
```
（Apple側がGUIでの変更を不可にしたり、今後変更できなくなる可能性あり）


## パッケージマネージャーのインストール

### Xcodeコマンドラインツールのインストール
```
xcode-select --install
```

### Homebrewのインストール
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
```

## パッケージのインストール
```
sh 01_install_package.sh
```

ファイルの中身は[01_install_package.sh](/01_install_package.sh)参照。

### 【補足】パーミッション変更
実行権限を付与する必要がある場合、下記コマンドを実行
```
chmod 744 01_install_package.sh
```

## アプリケーションのインストール

```
sh 02_install_application.sh
```

ファイルの中身は[02_install_application.sh](/02_install_application.sh)参照。

## コマンドライン環境構築
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Nodeの設定
適宜ターミナルの再起動を行うこと。

### anyenv のインストール
```
brew install anyenv
echo 'eval "$(anyenv init -)"' >> ~/.zshrc
anyenv install --init
```

### nodenv のインストール
```
anyenv install nodenv
```

### Nodeのインストール
最新バージョンを仮でグローバルインストールする。（LTSなどでもよし）

#### 最新バージョンの確認
```
nodenv install -l
```

#### 最新バージョンのインストールとグローバル設定
```
nodenv install {最新バージョン}
nodenv global {最新バージョン}
```

## Visual Stdio Code拡張機能のインストール
```
sh 03_install_vscode_extension.sh
```

ファイルの中身は[03_install_vscode_extension.sh](/03_install_vscode_extension.sh)参照。

### 【補足】インストール済拡張機能の確認
下記コマンドでインストール済拡張機能を確認できるので、移行前などに確認しておくと良い。
```
code --list-extensions
```