# install_python
pythonのインストール方法

```sh
# gitからpyenvインストール
git clone https://github.com/pyenv/pyenv.git ~/.pyenv

#Path設定
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/shims:$PATH"' >> ~/.bash_profile
source ~/.bash_profile

#確認
pyenv --version

#インストール可能バージョン一覧
pyenv install --list

#pythonインストール
pyenv install 3.6.5

#現在の設定確認
pyenv versions

#設定バージョン変更
pyenv global 3.6.5

#現在の設定確認
pyenv versions
```


## sudo時にも同じ設定を使いたい場合
```sh
#sudo時に実行できないため設定
cd /etc
sudo sed -i -e "s/Defaults\tsecure_path/#Defaults\tsecure_path/g" ./sudoers
sudo sed -i -e "s/Defaults secure_path/#Defaults secure_path/g" ./sudoers
echo 'Defaults env_keep += "PATH"' | sudo tee -a ./sudoers
echo 'Defaults env_keep += "PYENV_ROOT"' | sudo tee -a ./sudoers

#確認
sudo pyenv --version
```
