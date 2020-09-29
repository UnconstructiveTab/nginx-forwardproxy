# NGINX Forward Proxy

```
cd /tmp
apt source nginx
git clone https://github.com/chobits/ngx_http_proxy_connect_module
cd ngx*
wget https://github.com/chobits/ngx_http_proxy_connect_module/blob/master/patch/proxy_connect.patch
cd ../
cd nginx-*
patch -p1 < ../ngx_http_proxy_connect_module/proxy_connect.patch
apt install libpcre3 libpcre3-dev zlib1g zlib1g-dev libssl-dev
./configure --add-module=/tmp/ngx_http_proxy_connect_modul
make && sudo make install
rm /usr/local/nginx/conf/nginx.conf
wget -P /usr/local/nginx/conf/ https://raw.githubusercontent.com/UnconstructiveTab/nginx-forwardproxy/master/nginx.conf
wget https://github-file/nginx.service
cp nginx.service /etc/systemd/system/nginx.service
systemctl start nginx.service
systemctl enable nginx.service
systemctl status nginx.service
```
