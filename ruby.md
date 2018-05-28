# install\_ruby
rubyのインストール方法

```sh
# gitからrbenvインストール
git clone https://github.com/rbenv/rbenv.git ~/.rbenv

# rubyビルド用のプラグインをインストール
git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

#Path設定
echo 'export RBENV_ROOT="$HOME/.rbenv"' >> ~/.bashrc
echo 'export PATH="$RBENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'export PATH="$RBENV_ROOT/shims:$PATH"' >> ~/.bashrc
source ~/.bashrc

#確認
rbenv --version

#インストール可能バージョン一覧
rbenv install --list

#pythonインストール
rbenv install 2.5.1

#現在の設定確認
rbenv versions

#設定バージョン変更
rbenv global 2.5.1

#現在の設定確認
rbenv versions
```


## sudo時にも同じ設定を使いたい場合
```sh
#sudo時に実行できないため設定
cd /etc
sudo sed -i -e "s/Defaults\tsecure_path/#Defaults\tsecure_path/g" ./sudoers
sudo sed -i -e "s/Defaults secure_path/#Defaults secure_path/g" ./sudoers
echo 'Defaults env_keep += "PATH"' | sudo tee -a ./sudoers
echo 'Defaults env_keep += "RBENV_ROOT"' | sudo tee -a ./sudoers

#確認
sudo rbenv --version
```
