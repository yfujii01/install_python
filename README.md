# install_python
pythonのインストール方法

```sh
# コンパイルに必要なパッケージインストール
sudo apt-get install git gcc make openssl libssl-dev libbz2-dev libreadline-dev libsqlite3-dev -y
sudo apt-get install zlib1g-dev

# gitからpyenvインストール
sudo git clone https://github.com/pyenv/pyenv.git /usr/local/pyenv

#Path設定
echo 'export PYENV_ROOT="/usr/local/pyenv"' | sudo tee -a /etc/profile.d/pyenv.sh
echo 'export PATH="${PYENV_ROOT}/bin:${PATH}"' | sudo tee -a /etc/profile.d/pyenv.sh
source /etc/profile.d/pyenv.sh

#確認
pyenv --version

#sudo時に実行できないため設定
cd /etc
sudo sed -i -e "s/Defaults\tsecure_path/#Defaults\tsecure_path/g" ./sudoers
sudo sed -i -e "s/Defaults secure_path/#Defaults secure_path/g" ./sudoers
echo 'Defaults env_keep += "PATH"' | sudo tee -a ./sudoers
echo 'Defaults env_keep += "PYENV_ROOT"' | sudo tee -a ./sudoers

#確認
sudo pyenv --version

#pythonインストール
sudo pyenv install 3.6.5
```
