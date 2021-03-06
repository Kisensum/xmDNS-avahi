The changes made to Avahi are an attempt to transform it into an
xmDNS server as described here:

here: http://tools.ietf.org/html/draft-lynn-dnsext-site-mdns-01

Why would you want to do that?  One reason is that
xmDNS is required in order to implement SEP 2.0 - Smart Energy Profile
protocol.

These changes are incomplete but sufficient to meet the xmDNS spec
on a local segment.  No idea if this will work across routers at
a single site.

Modifications:

- Multicast address changed to `ff05::fb` (No longer works as an mDNS server!!) 
- Partial support added for .site domain -- enough to make it work.


Steps to build, install and run (from docs/INSTALL):

Many pacakges are required just to get through the ./configure step.  On Ubuntu 12.04,
the following Ansible task was used::

  - name: Packages required for Avahi build process
    apt: pkg={{ item }} state=latest
    with_items:
    - intltool
    - pkg-config
    - libgtk2.0-dev
    - libqt3-mt-dev
    - libqt4-core
    - qt4-dev-tools
    - libgtk-3-dev
    - libdbus-1-dev
    - libgdbm-dev
    - libdaemon-dev
    - python-gtk2
    - mono-mcs
    - monodoc-base
    - gtk-sharp2

Once these are installed, the build scripts should run to completion without
serious error::

	$ ./autogen.sh
	$ ./configure --sysconfdir=/etc --localstatedir=/var
	$ make
	$ make install
	$ sudo ldconfig
	$ sudo kill -HUP `cat /var/run/dbus/pid`
	$ /etc/init.d/avahi-daemon start



AVAHI SERVICE DISCOVERY SUITE

WEB SITE:
	http://avahi.org/

GIT:
	git://git.0pointer.de/avahi.git

GITWEB:
	http://git.0pointer.de/?p=avahi.git;a=summary

MAILING LIST:
	http://lists.freedesktop.org/mailman/listinfo/avahi

GIT COMMITS MAILING LIST:
	https://tango.0pointer.de/mailman/listinfo/avahi-commits

TRAC TICKET CHANGES MAILING LIST:
	https://tango.0pointer.de/mailman/listinfo/avahi-tickets

IRC:
	#avahi on irc.freenode.org

CIA:
	http://cia.navi.cx/stats/project/avahi

FRESHMEAT:
	http://freshmeat.net/projects/avahi/

OHLOH:
	http://www.ohloh.net/projects/avahi/

AUTHORS:
	Several
