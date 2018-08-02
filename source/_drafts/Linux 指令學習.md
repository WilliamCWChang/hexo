Linux 指令學習
===

# vim

## 用Vim做搜尋(Search)並取代(replace)
```
vim /tmp/testfile.txt
```



先按一下「Esc」→輸入「**:1,$s/123/456/g**」→再按「Enter」即可作搜尋並取代的動作!

此範例是將文字**123**更換成文字**456**，並且將此文件裡的所有符合的皆取代。

**1,$** 指的就是從頭至尾。





# systemd 
[systemctl](
https://wiki.archlinux.org/index.php/Systemd_(%E6%AD%A3%E9%AB%94%E4%B8%AD%E6%96%87))


## Network settings
 
 ```bash=
 cd /etc/systemd/network
 sudo systemctl restart systemd-networkd.service
 systemctl status systemd-networkd.service
```



linux


# dmesg
[dmesg 指令的用法](https://imsardine.github.io/2016/11/06/dmesg-command/)

```
dmesg | grep tty
```


###### tags : `linux`