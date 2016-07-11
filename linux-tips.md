# disk usage for current subdirectories
du -sh ./*

# Linux command options
r       recursive
f       force
v       verbose
i       interactive


cp -p file.txt  file.txt_back # copy and preserve attributes

preserve   the   specified   attributes   (default:  mode,owner-
              ship,timestamps), if possible  additional  attributes:  context,
              links, xattr, all
```
>>   - append to file
curl -OL url - download resource from url
!!   - Repeating run previous commands
head sonnets.txt - shows the first 10 lines of the file
tail sonnets.txt -shows the last 10 lines of the file
cat sonnets.txt - show file
wc - wordcount
2620 17670 95635 sonnets.txt
newlines|word counts|bytes
more -
less -
G - go to end of file
1G - got to beginning of file
```
# Useful linux command

To list directory content recursively

	$ls -R

tree - list contents of directories in a tree-like format.

# search string "SO4" in templete folder recursively and return row number
grep -rn SO4 template/

# Check linux os version

	$cat /etc/os-release

# Install wget in Mac OS X
	curl -O http://ftp.gnu.org/gnu/wget/wget-1.14.tar.gz
	tar xvzf wget-1.14.tar.gz
	cd wget-1.14
	./configure --with-ssl=openssl
	make
	sudo make install

# vim game
http://vim-adventures.com/


# Install brew
$ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# Install wget
$brew install wget


# byte of vim
http://files.swaroopch.com/vim/byte_of_vim_v051.pdf

vim command
========

i - change to insert mode.
a - add after current cursor.

[ESC] - change to command mode.
x - dlete the character in the current cursor.
:wq - save and quit 
:w - save
:q - quit
o - add one new line.
0 - go to line beginning.
$ - go to line end

yy - copy current line  
p - paste
u - undo

compile c language source file with gcc compiler
========
```
  $gcc hello.c
  $ls
  a.out hello.c
  # To run
  $ ./a.out
```  
