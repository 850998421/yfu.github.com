---
layout: post
title: "Perldoc Complains about groff"
date: 2013-01-01 20:06
comments: true
categories: 
---
Everytime I ran perldoc, I got the following error message:

{% codeblock perldoc Complains lang:bash %}
➜  perl  perldoc -f -X
You have an old groff. Update to version 1.20.1 for good Unicode support.
If you don't upgrade, wide characters may come out oddly.

 at /Users/yfu/perl5/perlbrew/perls/perl-5.16.2/lib/5.16.2/Pod/Perldoc.pm line 1346.
 You have an old groff. Update to version 1.20.1 for good Unicode support.
 If you don't upgrade, wide characters may come out oddly.

  at /Users/yfu/perl5/perlbrew/perls/perl-5.16.2/lib/5.16.2/Pod/Perldoc.pm line 1346.
{% endcodeblock %}
<--! more -->

Then I checked the version of groff:
{% codeblock groff version lang:bash %}
➜  perl  groff -v
GNU groff version 1.19.2
Copyright (C) 2004 Free Software Foundation, Inc.
GNU groff comes with ABSOLUTELY NO WARRANTY.
You may redistribute copies of groff and its subprograms
under the terms of the GNU General Public License.
For more information about these matters, see the file named COPYING.

called subprograms:

GNU grops (groff) version 1.19.2
GNU troff (groff) version 1.19.2
{% endcodeblock %}

Obviously, it is way too old. So I need to install a more recent version of groff. One of easiest ways to installing groff (and many other missing software programs on Mac OS) is having a package manager, for example, [homebrew](http://mxcl.github.com/homebrew/),  [MacPorts](http://www.macports.org/) and [Fink](http://www.finkproject.org/). After trying MacPorts and Fink years ago, I realized that these two are a bit too complicated for me (though they seem to have more and newer versions of software). Hence, I am using homebrew as the package manager on my computer. If you haven't tried it yet, I encourage you to give it a try! You can find installation details [here](http://mxcl.github.com/homebrew/). Below is how to install newer groff using homebrew:

{% codeblock How to Install groff using homebrew lang:bash %}
➜  perl  brew search groff
homebrew/dupes/groff

➜  ~  brew tap homebrew/dupes
Cloning into '/usr/local/Library/Taps/homebrew-dupes'...
remote: Counting objects: 660, done.
remote: Compressing objects: 100% (286/286), done.
remote: Total 660 (delta 415), reused 612 (delta 374)
Receiving objects: 100% (660/660), 97.16 KiB | 157 KiB/s, done.
Resolving deltas: 100% (415/415), done.
Tapped 36 formula

➜  ~  brew install groff
==> Downloading http://ftpmirror.gnu.org/groff/groff-1.21.tar.gz
######################################################################## 100.0%
==> ./configure --prefix=/usr/local/Cellar/groff/1.21 --without-x
==> make
==> make install
/usr/local/Cellar/groff/1.21: 554 files, 20M, built in 81 seconds
{% endcodeblock %}

Note that the official homebrew does not have a formulea (which contains directions on where to download the source and how to compile) for groff. So I need to "tap" to import other formula from other people's repositories. In my case, you can find it [here](http://braumeister.org/repos/Homebrew/homebrew-dupes/formula/groff). So after seconds, I have the newest groff installed and now perldoc no longer complains about the the older groff!