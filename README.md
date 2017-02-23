Idea is to have a diary for kids or whatever

Download gmail mailbox via google takeout and convert mbox formated emails to pdfs
or connect directly to gmail via imaps/oauth2.

This code is based on PDF::API2 and IMAGEMAGICK Librarys.
The Design for the Infobox is a dirty quick layout. This has to be improved in
the future.

Licence: GPLv2

===================================================

Help:

./mbox2pdf --options

--mboxfile=FILE              choose mbox file<br>
--verbose                    enable verbose logging<br>
--debug                      enable debugging<br>
--type mbox|imap             choose whether you want to use a local mbox file or a remote imap account<br>
--testlimit=Start(,End)      choose at which position you want to start to generate the pdf file<br>
--onlyyear=YEAR              choose a special year

You need a config.pl file in your execute dir
and you have to change the path to this file
inside the code
===================================================

# --------------------------------------------------
# This is my config file
(
mboxfile        => "mbox file",<br>
filename        => "your filename",<br>
path            => "your path",<br>
oauth_token     => "yourtoken",<br>
username        => '.......@gmail.com'<br>
)
# -------------------------------------------------

configure in developer console credintials for external use.
download gmail-oauth-tools and execute:

python oauth2.py --generate_oauth2_token --client_id=YOUR_CLIENT_ID --client_secret=YOUR_CLIENT_SECRET 

use Access Token as oauth_token in config.pl

# -------------------------------------------------
Libs:

 use Data::Dumper;
 use Mail::IMAPClient;
 use Mail::Mbox::MessageParser;
 use MIME::Parser;
 use MIME::Words qw(:all);
 use MIME::Body;
 use MIME::Base64;
 use Date::Parse;
 use Getopt::Long;
 use PDF::API2;
 use PDF::TextBlock;
 use Digest::MD5 qw(md5_hex); 
 use URI::Escape;
 use Encode;
 use utf8;
 use Image::Magick;
