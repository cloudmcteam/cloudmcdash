
# The #1 Dashboard for pterodactyl.

![Logo](https://media.discordapp.net/attachments/1122564515846950972/1129368111980761228/Ofralse.png?width=625&height=62)


Experience the power of the modern client panel for Pterodactyl, boasting an impressive array of features and a sleek, intuitive frontend that sets it apart from the rest.

While we kindly request that you maintain the copyright attribution for our dashboard, we prioritize fostering a positive collaboration and encourage respectful use.

### All features in HypeClient:
- Resource Management: Seamlessly create and manage servers and other resources.

- Coin System: Earn coins through AFK Page engagement, Linkvertise rewards, and even gift them to others.
- Renewal Mechanism: Utilize coins for resource renewal, ensuring smooth and continuous access.
- Coupon System: Redeem coupons to receive additional resources and coins as a user.
- Server Management: Effortlessly create, view, and customize servers according to your needs.
- Login Queue: Prevent server overload with a smart login queue system.
- User System: Secure authentication, password regeneration, and other essential user-related features.
- Store Integration: Exchange coins for various resources, enhancing your server's capabilities.
- Dashboard Overview: Get an insightful overview of your resources through a comprehensive dashboard.
- Resource Rewards: Earn additional resources by joining designated Discord servers.
- Admin Controls: Empower administrators with the ability to manage/create/give coins, resources, coupons, and user privileges.

## Warning & Support
We highly recommend keeping the "Created by CloudMC" notice in the footer for increased visibility and improved support. May result in DMCA actions. Thank you for your cooperation.

Get free support by keeping our "Created by CloudMC" footer credit. Join our Discord community at **[Discord](https://discord.gg/cloudmc)**.

**[Preview our Dashboard](https://demo1.cloudmc.xyz)**

![Image](https://media.discordapp.net/attachments/1125465147440386169/1129367203792289882/200shots_so.png?width=605&height=453)


## 1: Installation Guide
Please note that prior installation of Pterodactyl is required before installing this Dashboard.

```
apt update && upgrade
apt install nginx && apt install certbot
ufw allow 80
ufw allow 443
sudo apt install git
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs
git clone https://github.com/cloudmcteam/cloudmcdash.git
cd cloudmcdash && npm install
npm i pm2 -g

```
Tip: If you are using CloudMC Dashboard with a proxy, kindly ensure that your IP address is allowed in the Web Application Firewall (WAF) tools of Cloudflare. This will ensure seamless functionality and access to the Dashboard.

Apply these measures to all nodes and the Pterodactyl if custom firewalls are used.

![cfexample](https://media.discordapp.net/attachments/1122564515846950972/1129369860879695882/image.png?width=1025&height=97)

Replace "client.example.com" with your domain and client's subdomain.
```
certbot certonly -d client.example.com
```
When you do the certbot command and get "Congratulations" you are continued to the next step.

```
nano /etc/nginx/sites-enabled/cloudmcdash.conf
```
Now you'll be pasting this configuration in cloudmcdash.conf in /etc/nginx/sites-enabled

Please change <DOMAIN> and <PORT> to your client domain and your client port you set on settings.json

```
server {
    listen 80;
    server_name <domain>;
    return 301 https://$server_name$request_uri;
}
server {
    listen 443 ssl http2;
location /afkwspath {
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "upgrade";
  proxy_pass "http://localhost:<port>/afkwspath";
}
    
    server_name <domain>;
ssl_certificate /etc/letsencrypt/live/<domain>/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/<domain>/privkey.pem;
    ssl_session_cache shared:SSL:10m;
    ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers on;
location / {
      proxy_pass http://localhost:<port>/;
      proxy_buffering off;
      proxy_set_header X-Real-IP $remote_addr;
  }
}
```

```systemctl restart nginx```

Once you have ensured that no errors have occurred, you can proceed to configure your settings.json file. Before launching the Dashboard, it is necessary to set up the settings.json file.

If you experience any issues please join **[and create a ticket](https://discord.gg/cloudmc)**.




## 2: Start the Dashboard

Before you start the Dashboard, **you need to configurate settings.json**. 

When everything is set up, you are ready to type the command's:
```
cd cloudmcdash
pm2 start index.js
pm2 startup
pm2 save
```
1. Start the index.js file/dashboard using pm2: Execute pm2 start index.js to initiate the index.js file or start the dashboard.

2. Configure pm2 to start automatically on system reboot: Run pm2 startup to set up automatic startup of the client whenever the system is rebooted.

3. Save changes made with pm2: Preserve your pm2 changes by using the command pm2 save.

4. Check logs with pm2: For log monitoring purposes, employ the command pm2 logs <id> where <id> corresponds to the specific process ID or name associated with the desired log.

Note: Replace <id> with the appropriate process ID or name for the specific log you wish to check.

## Thank you for using CloudMC Dashboard.
Made with ❤ by a dedicated team of three individuals, our mission is to combat the hosting services provided by badsk and encourage users to refrain from utilizing his projects. Instead, we offer our custom dashboard and original projects that are not plagiarized.

Our dashboard boasts exclusive additional functionalities meticulously crafted by our team. The backend infrastructure of the dashboards is powered by Dashactyl, and we acknowledge and credit their contribution to our success.

Donate me https://paypal.me/khootieecat if you want (:
