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
- 何が入ってるかは [ansible/requirements.yml](ansible/requirements.yml) を参照

#### 2) vagrant up

```
vagrant up
vagrant provision
```

- `ubunty/trusty64` な box イメージに
- `ansible/vagrant.yml` が playbook が適応される
- role毎の vars に関しては下記を参照
  - [ansible/group_vars/all.yml](ansible/group_vars/all.yml)
  - [ansible/vagrant.yml](ansible/vagrant.yml)

#### 3) ログイン

```
vagrant ssh
```

これでおｋ

### その他

ex.) box イメージを毎回作るのが面倒な場合

```
vagrant package
```

- これで `package.box` ができる
- S3やDropboxに奥などして、vagrant の box に指定するとはやいかもれない
