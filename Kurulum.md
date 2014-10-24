Git'in Kurulumu  ![][1]
===============

Git'i kullanmaya başlayalım.

###Linux'ta Kurulum

* Git'i Linux sisteminize paket kurucu yardımıyla kurmak istiyorsanız, bunu genellikle dağıtımınızla birlikte gelen temel paket yönetim aracıyla yapabilirsiniz. Fedora kullanıcısıysanız, `yum`'u kullanabilirsiniz:

`$ yum install git-core`

* Ubuntu gibi Debian-tabanlı bir sistemdeyseniz, `apt-get`'i kullanabilirsiniz:

`$ apt-get install git`

###Mac'te Kurulum

* Git'i Mac'te kurmak için iki kolay yol vardır. En kolayı, SourceForge sayfasından indirebileceğiniz görsel Git yükleyicisini kullanmaktır.

`http://sourceforge.net/projects/git-osx-installer/`

* Diğer başlıca yol, Git'i [MacPorts](http://www.macports.org) vasıtasıyla kurmaktır. MacPorts halihazırda kurulu bulunuyorsa Git'i şu komutla kurabilirsiniz:

`$ sudo port install git-core +svn +doc +bash_completion +gitweb`

Bütün ek paketleri kurmanız şart değil, ama Git'i Subversion yazılım havuzlarıyla kullanmanız gerekecekse en azından +svn'i edinmelisiniz.

###Windows'ta Kurulum

Git'i Windows'da kurmak oldukça kolaydır.Alt kısımdaki sayfasından indirip çalıştırmanız yeterli:

`http://git-scm.com/download/win`

===========

[1]: https://github.com/PAU-Projects/Github-WORKSHOP/blob/master/images/install.png===========

|[sonraki](https://github.com/PAU-Projects/Github-WORKSHOP/blob/master/SSH.md)
-----|----