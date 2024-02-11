Clone `alexrudd2:saxi` to `~/github/saxi`.  Then install with `sudo npm install -g .`

Set hostname in `/etc/hostname`.  Set IP address in `/etc/NetworkManager/system-connections`

Start `saxi` on boot.  First, copy the file `/etc/systemd/system/saxi.service`.  Then `sudo systemctl enable saxi`

Enable forwarding to `saxi` in `iptables`.  First, copy the file `/etc/iptables/iptables.rules`.  Then `systemctl enable iptables`

Clone `osresearch:plotter-vision` to `~/github/nginx`.
Modify `/etc/nginx/nginx.conf` to run as user `axi` and serve Plotter Vision on a port other than 80:
```
user axi;
<...>
    server {
        listen       8091;
        server_name  localhost;

        location / {
            root   /home/axi/github/plotter-vision/;
            index  index.html;
        }
<...>
```

Enable with `sudo systemctl enable nginx`.
