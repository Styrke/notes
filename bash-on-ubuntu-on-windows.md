# Switch languate to English with UTF-8 support

https://perlgeek.de/en/article/set-up-a-clean-utf8-environment

# Log in to SSH without password with convenient alias

https://pinboard.in/u:Styrke/t:ssh/t:howto/

# sudo: unable to resolve host [hostname]

The hosts file `/etc/hosts` is not correctly set up from the beginning, at least in my case.
Fix the problem by adding the "computer name" (the only string in `/etc/hostname` if you're in doubt) to the first entry in `/etc/hosts`.

`/etc/hosts` should begin like this:

    127.0.0.1 localhost PHOENIX

    # The following lines are desirable for IPv6 capable hosts
    ::1 ip6-localhost ip6-loopback
    fe00::0 ip6-localnet
    ...

# Jupyter Notebook

By default Jupyter doesn't work very well on Bash on Ubuntu on Windows.
Kernels (at least python 3) won't start and will instead be caught in a bootloop.

Install Jupyter with pip for python 3 using this workaround [as described by gglanzani on the GitHub issue](https://github.com/Microsoft/BashOnWindows/issues/185#issuecomment-238470680):

    sudo add-apt-repository ppa:aseering/wsl
    sudo apt-get update
    sudo apt-get install libzmq3 libzmq3-dev
    export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu
    sudo pip3 install --no-use-wheel -v pyzmq
    sudo pip3 install jupyter
