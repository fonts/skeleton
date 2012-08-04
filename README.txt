Skeleton for Collaborative Font Development
===========================================

^ Change the name above to the name of your new font! ^

This is a skeleton repository that can be used as the basis for developing
typefaces collaboratively.

There are two presumptions: you keep track of your changes with the Git
versioning system, and your source files are in the UFO format. Every time you
change the UFO font, you commit your changes into Git.

This repository comes with scripts to generate OTF’s and web fonts with
appropriate version metadata.

Where to share
--------------

To exchange and collaborate on your files you need to make your git repository
available online. Most programmers prefer the web service Github. Github is
free and comes with a lot of tools to aid the development process. It also
supports the visualization of UFO and diffs.

If working on type with programmer’s tools strikes you as unwieldy, remember
that these are some of the first forays into collaboratively working on open
source fonts. The prime advantage of Git and UFO is that they are open,
flexible standards. They work together with the tools we have now: but, more
importantly, they will work together with new type design tools we come up
with in the future. These technologies, for example, form a good basis for a
collaborative web editor in the browser.

Setting up
----------

The first step is to save one or more UFO font files in the project folder.
UFO is an open font format that is easy to process and exchange through
different tools.

Unless you use Fontlab, your font editor already supports UFO. Glyphs and
Robofont come with UFO support out of the box. The free and open source
FontForge does as well.

To install UFO for Fontlab, use Robofab: http://robofab.org/
To read up on UFO: http://unifiedfontobject.org/

Git keeps track of changes in your file. You ‘commit’ a file into git. Then,
the next time you make a change, git knows you have made a change: when you
are happy with the you commit it. The resulting change set you can share with
others, and that is how you can start to collaborate.

On the Mac, we recommend installing Git through Homebrew, because that is the
best way to install FontForge as well. See ‘Using the Command Line’ below.
After you’ve installed git you can run it from the Terminal, or use a
graphical application along with it. To read up on Git: http://git-scm.com/

License
-------

In the repository, you already find a copy of the SIL Open Font license. The
OFL is a copyleft license: everyone is free to create new versions of your
font as long as they are under the same license. Furthermore, a new version
can’t have the same name as your font. This affords you some power in making
sure your version of the font keeps corresponding to your vision. If you don’t
care about these provisions, you can also choose to license your font under
the CC0 license, which effectively makes it public domain.

While this workflow was designed around exchange across the internet, there is
nothing prohibiting you from using this workflow in-house on a proprietary
font.

Remember to remove the files OFL-COPYING.txt and OFL-FAQ.txt if you choose to
use another license.

Rakefile
--------

To further automate and facilitate the development process, this repository
contains a script called ‘Rakefile’. The Rakefile allows you to generate a
font with appropriate version metadata, and to automatically generate the
accompanying web fonts.

Rake works from the command line. See ‘Using the Command Line’ below. It
requires you to be in the project folder while you issue its commands.

The basic command

    rake

will generate OTF’s for each UFO in the ropository. To generate the OTF with
version metadata, and webfonts, type:

    rake release

this creates a specific release folder within a folder called build.

Read more on version numbers on the following section. Before using the
Rakefile, by the way, one needs to install the tools that are used by the
Rakefile. On Ubuntu/Debian this is a bit more complicated because it doesn’t
come with Ruby or Rubygems. But on OS X:

    brew install fontforge sudo gem install rake nokogiri

Version numbers
---------------

With an ever changing font file, how do you keep the different versions apart?
By giving them version numbers. The Rakefile takes care of the hassle of
embedding proper version numbers in the font metadata everytime you run `rake
release`.

A version number consists of three numbers: a major version, a minor version
and a patch version. The major and minor version number you keep update
yourself, using rake. Rake keeps track of the patch version for you. Everytime
you make a commit with Git the patch version number gets ‘bumped’ (x.y.5 ->
x.y.6).

How does this work? With Rake, you initialise a major.minor version number
(i.e. 0.3). Rake then uses the command `git describe` to figure out how many
commits have been made since the latest tag. This number becomes the ‘patch
version’. So seven commits later, we will be at version 0.3.7

With your first tag, you need to establish the version number from which you
start. Generally, 1.0.0 will be the first ‘finished’ version. If you feel like
you’ve only just begun, 0.0 or 0.1 will be a good first number. Type:

    rake init

Usually you will bump the major and the minor version number when you reach
certain goals in your project. A major version might stand for a ‘design
vision’: you start a font project with a vision of your result while you
steadily work from 0.x to 1.0, 1.0 being the first version that corresponds to
your initial vision. You than rephrase your goals for 2.0.

You can create subgoals for the minor version numbers.

To bump the minor version number (i.e. 0.5.4 -> 0.6):

    rake bump_minor

To bump the major version number (i.e. 0.5.4 -> 1.0):

    rake bump_major

You can read more about version numbers at http://semver.org/ which describes
a standard for version numbers that is used by a sizable number of software
projects.

Using the command line
----------------------

For the moment, the release workflow is pretty much command line based. There
is a unix command line available on Linux and Mac OS X. If you are using
Windows, your classmates / colleagues / children have probably been telling
you to get a Mac anyway. Though you don’t need to listen to them! You can
install Linux as well. It is a pretty good way to differentiate yourself, at
least in the field of design.

To get up to scratch with the terminal on OS X, follow:

http://i.liketightpants.net/and/absolute-beginners-unix-for-art-students-part-1
http://i.liketightpants.net/and/absolute-beginners-unix-for-art-students-part-2
http://i.liketightpants.net/and/absolute-beginners-unix-for-art-students-part-3

This also explains you how to install a package manager on OS X, called
homebrew, that you need to install the dependencies.

