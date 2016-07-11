# minimum-vagrantfile


### これはなに？

とりあえずベストプラクティスに則ってつくった最小限のVagrant開発環境

- http://docs.ansible.com/ansible/playbooks_best_practices.html

### 構築方法

#### 1) install ansible roles

必要なパッケージは既に用意されている role を ansible-galaxy でインストールする。

```
ansible-galaxy install -r ansible/requirements.yml
```

- すると `ansible/roles/*` にインストールされる

#### 2) vagrant up

```
vagrant up
vagrant provision
```

- `ubunty/trusty64` な box イメージに
- `ansible/vagrant.yml` が playbook が適応される

#### 3) ログイン

```
vagrant ssh
```

これでおｋ

### その他

box イメージを毎回作るのが面倒な場合

```
vagrant package
```

- これで `package.box` ができる
- S3やDropboxに奥などして、vagrant の box に指定するとはやいかもれない
