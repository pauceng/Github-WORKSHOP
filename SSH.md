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


===============
[önceki](https://github.com/PAU-Projects/Github-WORKSHOP/blob/master/Kurulum.md)|[sonraki](https://github.com/PAU-Projects/Github-WORKSHOP/blob/master/Komutlar.md)
-----|----