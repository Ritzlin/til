# Cannot bind some unused ports in Windows

Node was not be able to bing port `8080`.

After cmd `netstat -ano | findstr 8080`, I found that `8080` is not occupied.

---

Windows 10 will takes over some ports if Hyper-V, WSL or docker is used.

In my situation, I have Hyper-V disabled, docker with WLS-2 based in use.

List the ports that were taken

```
netsh interface ipv4 show excludedportrange protocol=tcp
```

My result

```
Startport     Endport
----------    --------
...other ports...
7998          8097
...other ports
```

Then I tried to delete this range in admin cmd

```
netsh int ipv4 delete excludedportrange protocol=tcp startport=7998 numberofports=100
```

I got `Access deinied`.

---

After search, I tried restart the `winnat`, and then it worked, `8080` was freed.

```
net stop winnat
net start winnat
```

From:
- https://superuser.com/questions/1579346/many-excludedportranges-how-to-delete-hyper-v-is-disabled
- https://github.com/docker/for-win/issues/3171#issuecomment-739740248
- https://stackoverflow.com/questions/48478869/cannot-bind-to-some-ports-due-to-permission-denied
