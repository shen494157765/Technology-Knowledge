# TechnologyKnowledge
Knowledge Notes for Coding Technology Accumulated by Myself




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

  sudo **adduser** username
  
  sudo usermod -aG sudo username  (add sudo power)
  
  OR
  
  sudo **useradd** -d /home/username -s /bin/bash -m username
  
  sudo passwd username  (add password for account)

* kill for loop in shell

  ps -ef|grep 'script name' 

  then, get PID in second column

* clear linux syslog and kern.log

  rm -rf /var/log/\*.gz

  rm -rf /var/log/*.1

  sudo sh -c "echo "" > /var/log/kern.log"

  sudo sh -c "echo "" > /var/log/syslog"

  constrain the size of kern.log and syslog:
  
  sudo vim /etc/rsyslog.d/50-default.conf

  $outchannel mysyslog,/var/log/syslog,1048576

  *.*;auth,authpriv.none :omfile:$mysyslog

  $outchannel mykernlog,/var/log/kern.log,1048576                                                       

  kern.*       :omfile:$mykernlog
  
  sudo service rsyslog restart

* vim ~/.vimrc       add the following to solve the problem "Press Enter or type command to continue"

  set shortmess=a,
  set cmdheight=2

* change file to unix form (used in windows or..)

  dos2unix xxx.sh

* install nvidia driver

  https://zhuanlan.zhihu.com/p/366882419

* get the ip port of server

  grep Port /etc/ssh/sshd_config
  
* kill the distribution address for the error: address already in use

  ps -a, 
  kill -9 ....
  
* when linux was hacked

  1. find the process that highly dominates the CPU \
  ps -eo cmd,pcpu,pid,user --sort -pcpu | head
  
  2. get the exact path of the process \
  ls -l /proc/{pid}/exe
  
  3. remove the exact process, it might be xxx.sh or python
  
  4. revise the password of sudo \
  sudo -s  (go into the sudo terminal) \
  passwd root  (type new password twice)
  
  5. other methods: http://wlaq.xjtu.edu.cn/info/1008/1945.htm
  



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






# Discovery Northeastern University
* salloc -N 1 -p ce-mri --gres=gpu:v100:4 --cpus-per-task=48 (--time=2-00:00:00)
  
  call for gpu cpu resource

* sinfo --partition=ce-mri --Format=nodes,cpus,nodelist,gres,statecompact,features
  
  find the available resource at column 'STATE'

* squeue -p ce-mri

  find the jobs with people
  
* Submit the job
  
  conda activate ...
  
  create the run.script file: \
  #!/bin/bash \
  #SBATCH --nodes=1 \
  #SBATCH --time=7-00:00:00 \
  #SBATCH --job-name=MyJobName \
  #SBATCH --partition=ce-mri \
  #SBATCH --gres=gpu:v100:1 \
  #SBATCH --cpus-per-task=48 \
  sh /full/path/to/shell/file/run_pretrain.sh
  
  then: \
  sbatch run.script
  
  do not use nohup in shell file
  
  there will be a .out file for the print information
  
* Find the job

  squeue -u $USER
  
* Cancel the job

  scancel --name=MyJobName



