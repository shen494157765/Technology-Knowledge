# TechnologyKnowledge
Knowledge Notes for Coding Technology




# Linux

* Delete CUDA memory after the process was killed:

  sudo fuser -v /dev/nvidia*

* Remove files in Linux:

  rm -rf *file_name*

* Check file size in the current content:

  du -sh *

* To revise the theme:

  vim .vimrc

  vim ~/.bashrc  -> add it:   export PS1="\[\033[01;36;01m\][\u@\h \W]\$\[\033[01;00;00m\] "

* Find the space cost of every file in current file:

  ls -lh

* add user

  sudo useradd username

  sudo usermod -aG sudo username.  (add sudo power)

* kill for loop in shell

  ps -ef|grep 'script name' 

  then, get PID in second column

* clear linux syslog and kern.log

  rm -rf /var/log/\*.gz

  rm -rf /var/log/*.1

  sudo sh -c "echo "" > /var/log/kern.log"

  sudo sh -c "echo "" > /var/log/syslog"

  constrain the size of kern.log and syslog:

  $outchannel mysyslog,/var/log/syslog,1048576

  *.*;auth,authpriv.none :omfile:$mysyslog

  $outchannel mykernlog,/var/log/kern.log,1048576                                                       

  kern.*       :omfile:$mykernlog

* vim ~/.vimrc       add the following to solve the problem "Press Enter or type command to continue"

  set shortmess=a
  set cmdheight=2

* change file to unix form (used in windows or..)

  dos2unix xxx.sh

* install nvidia driver

  https://zhuanlan.zhihu.com/p/366882419

  

  

  



# Git

* 1. git status
  2. git add .
  3. git commit -m "..."
  4. git push



# Pytorch

* Runtime Error: received 0 items of ancdata:

  torch.multiprocessing.set_sharing_strategy('file_system')
  
* print local time
  
  localtime = time.asctime( time.localtime(time.time()) )
  print ("time now is :", localtime)







# Mac

* vim ~/.ssh/config

  add new ssh key
