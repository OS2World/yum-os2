PREFIX=/@unixroot/usr
SYSCONFDIR=/@unixroot/etc

YUMETC=$(DESTDIR)$(SYSCONFDIR)/yum

all:
	echo "Nothing to do"

clean:
	rm -f *.pyc *.pyo *~

install:
	mkdir.exe -p $(YUMETC)
	mkdir.exe -p $(YUMETC)/protected.d
	mkdir.exe -p $(YUMETC)/repos.d
	mkdir.exe -p $(YUMETC)/vars

	install -m 644 yum.conf $(YUMETC)/yum.conf

	install -m 644 version-groups.conf $(YUMETC)/version-groups.conf

	mkdir.exe -p $(DESTDIR)$(SYSCONFDIR)/logrotate.d
	install -m 644 yum.logrotate $(DESTDIR)$(SYSCONFDIR)/logrotate.d/yum

	mkdir.exe -p $(DESTDIR)$(SYSCONFDIR)/rc.d/init.d
	install -m 755 yum-updatesd.init $(DESTDIR)$(SYSCONFDIR)/rc.d/init.d/yum-updatesd

	mkdir.exe -p $(DESTDIR)$(SYSCONFDIR)/dbus-1/system.d/
	install -m 755 yum-updatesd-dbus.conf $(DESTDIR)$(SYSCONFDIR)/dbus-1/system.d/yum-updatesd.conf

	install -m 755 yum-updatesd.conf $(DESTDIR)$(SYSCONFDIR)/yum/yum-updatesd.conf

	mkdir.exe -p $(YUMETC)/bash_completion.d
	install -m 644 yum.bash $(YUMETC)/bash_completion.d
	mkdir.exe -p $(YUMETC)/cron.daily
	mkdir.exe -p $(YUMETC)/sysconfig/
	install -D -m 755 0yum.cron $(YUMETC)/cron.daily/0yum.cron
	install -D -m 755 yum-cron $(YUMETC)/rc.d/init.d/yum-cron
	install -D -m 644 yum-daily.yum $(YUMETC)/yum-daily.yum
	install -D -m 644 yum-weekly.yum $(YUMETC)/yum-weekly.yum
	install -D -m 644 yum-cron.sysconf $(YUMETC)/sysconfig/yum-cron
