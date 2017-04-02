##编辑器之神?
---------------------
曾看到过一篇文章，作者将vim与另一种编辑器Emacs作比较，认为Emacs是神之编辑器，而将vim称作编辑器之神。
我在很早就接触了windows系统，习惯了其图形界面的交互手段后，在初次接触vim这种脱离鼠标的编辑模式时，是相当不习惯的。究其原因，vim是30年前诞生的产物，那时计算机远没有当下普及，vim是一个需要学习成本的编辑器，而现在没有那么多人有耐心和意愿去掌握这种“高成本”而看似“无用”的编辑方式了。
但总有少部分人，一些极客，会对其展现巨大的兴趣和热情，鼓吹vim大法好，存在即合理。

###关于vim的使用介绍（forMac）
-------------------------------------------
1. 打开终端／iterm2
2. 输入 `vimtutor` 回车
-------------------------------------------
Lesson 1


  1. The cursor is moved using either the arrow keys or the hjkl keys.
         h (left)       j (down)       k (up)       l (right)

  2. To start Vim from the shell prompt type:  vim FILENAME <ENTER>

  3. To exit Vim type:     <ESC>   :q!   <ENTER>  to trash all changes.
             OR type:      <ESC>   :wq   <ENTER>  to save the changes.

  4. To delete the character at the cursor type:  x

  5. To insert or append text type:
         i   type inserted text   <ESC>         insert before the cursor
         A   type appended text   <ESC>         append after the line

NOTE: Pressing <ESC> will place you in Normal mode or will cancel
      an unwanted and partially completed command.
      
************
      
Lesson 2
      
      
    

  1. To delete from the cursor up to the next word type:    dw
  2. To delete from the cursor to the end of a line type:    d$
  3. To delete a whole line type:    dd

  4. To repeat a motion prepend it with a number:   2w
  5. The format for a change command is:
               operator   [number]   motion
     where:
       operator - is what to do, such as  d  for delete
       [number] - is an optional count to repeat the motion
       motion   - moves over the text to operate on, such as  w (word),
                  $ (to the end of line), etc.

  6. To move to the start of the line use a zero:  0

  7. To undo previous actions, type:           u  (lowercase u)
     To undo all the changes on a line, type:  U  (capital U)
     To undo the undo's, type:                 CTRL-R
     
 ************
 
Lesson 3


  1. To put back text that has just been deleted, type   p .  This puts the
     deleted text AFTER the cursor (if a line was deleted it will go on the
     line below the cursor).

  2. To replace the character under the cursor, type   r   and then the
     character you want to have there.

  3. The change operator allows you to change from the cursor to where the
     motion takes you.  eg. Type  ce  to change from the cursor to the end of
     the word,  c$  to change to the end of a line.

  4. The format for change is:

         c   [number]   motion

Now go on to the next lesson.

************

Lesson 4


  1. CTRL-G  displays your location in the file and the file status.
             G  moves to the end of the file.
     number  G  moves to that line number.
            gg  moves to the first line.

  2. Typing  /  followed by a phrase searches FORWARD for the phrase.
     Typing  ?  followed by a phrase searches BACKWARD for the phrase.
     After a search type  n  to find the next occurrence in the same direction
     or  N  to search in the opposite direction.
     CTRL-O takes you back to older positions, CTRL-I to newer positions.

  3. Typing  %  while the cursor is on a (,),[,],{, or } goes to its match.

  4. To substitute new for the first old in a line type    :s/old/new
     To substitute new for all 'old's on a line type       :s/old/new/g
     To substitute phrases between two line #'s type       :#,#s/old/new/g
     To substitute all occurrences in the file type        :%s/old/new/g
     To ask for confirmation each time add 'c'             :%s/old/new/gc
     
**********

Lesson 5


  1.  :!command  executes an external command.

      Some useful examples are:
         (MS-DOS)         (Unix)
          :!dir            :!ls            -  shows a directory listing.
          :!del FILENAME   :!rm FILENAME   -  removes file FILENAME.

  2.  :w FILENAME  writes the current Vim file to disk with name FILENAME.

  3.  v  motion  :w FILENAME  saves the Visually selected lines in file
      FILENAME.

  4.  :r FILENAME  retrieves disk file FILENAME and puts it below the
      cursor position.

  5.  :r !dir  reads the output of the dir command and puts it below the
      cursor position.
      
************

Lesson 6 

  1. Type  o  to open a line BELOW the cursor and start Insert mode.
     Type  O  to open a line ABOVE the cursor.

  2. Type  a  to insert text AFTER the cursor.
     Type  A  to insert text after the end of the line.

  3. The  e  command moves to the end of a word.

  4. The  y  operator yanks (copies) text,  p  puts (pastes) it.

  5. Typing a capital  R  enters Replace mode until  <ESC>  is pressed.

  6. Typing ":set xxx" sets the option "xxx".  Some options are:
        'ic' 'ignorecase'       ignore upper/lower case when searching
        'is' 'incsearch'        show partial matches for a search phrase
        'hls' 'hlsearch'        highlight all matching phrases
     You can either use the long or the short option name.

  7. Prepend "no" to switch an option off:   :set noic
  
********

Lesson 7 


  1. Type  :help  or press <F1> or <Help>  to open a help window.

  2. Type  :help cmd  to find help on  cmd .

  3. Type  CTRL-W CTRL-W  to jump to another window

  4. Type  :q  to close the help window

  5. Create a vimrc startup script to keep your preferred settings.

  6. When typing a  :  command, press CTRL-D to see possible completions.
     Press <TAB> to use one completion.

****************************************************************
以上是官方文档，介绍了vim的几种模式以及模式之间互相切换的命令，光标的移动，文件的操作等

--------------------------------   
##自己在使用过程中遇到的问题与解决办法
--------------------------------
- Mac系统(OS X EI Caption/Version 10.11.5)自带vim7.3版本，最新的vim是7.4版本
	+ 需要手动更改vim7.4的安装目录，否则按照默认安装目录会将系统原生的vim覆盖掉。然后在`.bash_profile`中添加一个vim命令的别名，使其指向新安装的vim7.4目录。这样在终端中输入vim时，自动使用vim7.4版本，而对原生的vim7.3无影响。不过，这样系统中存在两个不同版本vim
	+ 也可以选择自己用源代码build，式是从[http://vim.org](http://vim.org)直接下载7.4版本的源文件，之后解压出来之后，在`opt/local`中建立一个vim的源文件安装目录，进入到`/opt/local/vim/src/`目录中，分别执行：`sudo make`, `sudo make install` 
	+ 使用[MacPorts](http://www.macports.org/)
	<pre><code>如果没有安装VIM（这里好像是指没有通过port安装vim）
		$ sudo port install vim 
	如果你已经安装
		$ sudo port upgrade vim (已安装vim)
	port 的安装目录在：/opt/local ，你可以在目录/opt/local/bin找到vim
		$ sudo ln -s /opt/ocal/bin/vim /usr/local/bin/vim
		$ vim --version 
</code></pre>
	可以成功升级到vim7.4版本，但是还是有下面的错误提示问题
	
*******
	
- Terminal/iTerm2内的vim在安装[spf13](https://github.com/spf13/spf13-vim)之后出现树形文档箭头图案显示乱码
	+ 在`.vimrc`文件中加入`scriptencoding utf-8
set encoding=utf-8`

***********

- 错误提示 "neocomplete does not work this version of Vim. It requires Vim 7.3.885 or above and "if_lua" enabled Vim."
	+ `brew install vim --with-lua`

**********
## 个人习惯
- Mac键位映射设置：将caps键与control的映射关系对调
- Sublime设置为vim模式：处于Insert模式时与正常的Sublime编辑模式无异