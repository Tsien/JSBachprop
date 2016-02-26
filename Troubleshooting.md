# TroubleShooting
    
#### Secure Copy (scp)

Copy the file "foobar.txt" from a remote host to the local host

    $ scp your_username@remotehost.edu:foobar.txt /some/local/directory
    
Copy the file "foobar.txt" from the local host to a remote host

    $ scp foobar.txt your_username@remotehost.edu:/some/remote/directory

Copy the directory "foo" from the local host to a remote host's directory "bar"

    $ scp -r foo your_username@remotehost.edu:/some/remote/directory/bar
    
    
#### [Remote Access to IPython Notebooks via SSH](https://coderwall.com/p/ohk6cg/remote-access-to-ipython-notebooks-via-ssh)

On the remote machine, start the IPython notebooks server:

    remote_user@remote_host$ ipython notebook --no-browser --port=8889
    
On the local machine, start an SSH tunnel:

    local_user@local_host$ ssh -N -f -L localhost:8888:localhost:8889 remote_user@remote_host
    
Now open your browser on the local machine and type in the address bar

    localhost:8888
    
To close the SSH tunnel on the local machine, look for the process and kill it manually:

    local_user@local_host$ ps aux | grep localhost:8889
    local_user 18418  0.0  0.0  41488   684 ?        Ss   17:27   0:00 ssh -N -f -L localhost:8888:localhost:8889 remote_user@remote_host
    local_user 18424  0.0  0.0  11572   932 pts/6    S+   17:27   0:00 grep localhost:8889

    local_user@local_host$ kill -15 18418
    
#### [How to pass command line argument to gnuplot?](http://stackoverflow.com/questions/12328603/how-to-pass-command-line-argument-to-gnuplot)

    output=test1.png
    data=foo.data
    gnuplot -e "datafile='${data}'; outputname='${output}'" foo.plg
    
and foo.plg:

    set terminal png
    set outputname 
    f(x) = sin(x)
    plot datafile
    
