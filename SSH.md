SSH ve Github Kimliyi.
===========

####Kimliğiniz

Git'i yapılandırmasına başlarken yapmanız gereken ilk şey adınızı ve e-posta adresinizi ayarlamaktır. Bunun önemli olmasının nedeni her bir Git kaydının bu bilgiyi kullanıyor olması ve bu bilgiler ile yaptığınız kaytlarınızı kayıt altına tutar.

```bash
    $ git config --global user.name "kullanıcı isminiz"
    $ git config --global user.email "github mailiz"
```

Bu yapılandırmayı yani, `--global` seçeneğini kullandığınızda bunu bir kez yapmanız yeterli olacaktır, çünkü Git, o sistemde yapacağınız her işlem için bu bilgileri kullanacaktır. İsmi ya da e-posta adresini projeden projeye değiştirmek isterseniz, komutu değişiklik yapmak istediğiniz proje klasörünün içinde `--global` seçeneği olmadan çalıştırabilirsiniz.

SSH key oluşturalım
=================

* öncelikle:

```bash
    $ ssh-keygen -t rsa -C "your_email@example.com"
    # Creates a new ssh key, using the provided email as a label
    # Generating public/private rsa key pair.
    # Enter file in which to save the key (/home/you/.ssh/id_rsa):
```
* Sonra, bir parola girmeniz istenir.

```bash
    Enter passphrase (empty for no passphrase): [Type a passphrase]
    # Enter same passphrase again: [Type passphrase again]
```

* Böyle bir ekran ile karşılaşmanız lazim

```bash
    Your identification has been saved in /home/you/.ssh/id_rsa.
    # Your public key has been saved in /home/you/.ssh/id_rsa.pub.
    # The key fingerprint is:
    # 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com
```

* Sonra, `ssh-agent`'e yeni anahtarı ekleyin:

```bash
    # start the ssh-agent in the background
    $ eval "$(ssh-agent -s)"
    # Agent pid 59566
    $ ssh-add ~/.ssh/id_rsa
```

* Oluşturduğumuz anahtarı kopyalamak için aşağıdaki kodu çalıştırın.

```bash
    $ sudo apt-get install xclip
    # Downloads and installs xclip. If you don't have `apt-get`, you might need to use another installer (like `yum`)
    $ xclip -sel clip < ~/.ssh/id_rsa.pub
    # Copies the contents of the id_rsa.pub file to your clipboard
```

* Alternatif olarak,
> *bu dizine bulunan `~/.ssh/id_rsa.pub` dosyasını açıp ve manuel olarak içeriğini kopyalamayabilirsiniz.*

* Şimdi anahtarı kopyaladıktan sonra, GitHub hesabımıza ekliyelim:
    * Github hesabınızda ayarlar kısmından SSH key bölümünü seciyoruz
    * Add key kısmını seciyoruz
    * Kopyaladığımız key'i buraya yapıştırdıktan sonra
sonra,

Şimdi Github hesabımız ile bağlatı kurmaya çalışalım ve daha önce oluşturduğunuz parola oldu şifrenizi kullanarak yapaçaksınız.

* Termineli açalım (`ctrl+alt+T`);

```bash
    $ ssh -T git@github.com
    # Attempts to ssh to github
```
Böyle hata mesajı ile karşılaşabilirsiniz!

```bash
    ...
    Agent admitted failure to sign using the key.
    debug1: No more authentication methods to try.
    Permission denied (publickey).
```
* Karşılaşmanız gereken mesaj böyle olması gerekiyor ve `yes` yazarak bu adımı bitirebilirsiniz.

```bash
    The authenticity of host 'github.com (207.97.227.239)' can't be established.
    # RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
    # Are you sure you want to continue connecting (yes/no)?
```
* `yes` yazıp onaylama işleminden sonra ;

```bash
    Hi username! You've successfully authenticated, but GitHub does not
    # provide shell access.
```

Good pushing :smile:


===============
[önceki](https://github.com/PAU-Projects/Github-WORKSHOP/blob/master/Kurulum.md)|[sonraki](https://github.com/PAU-Projects/Github-WORKSHOP/blob/master/Komutlar.md)
-----|----