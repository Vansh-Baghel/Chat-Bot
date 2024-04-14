

    Steps:
    mkdir app
    cd app
    git clone https://github.com/Vansh-Baghel/Chat-Bot.git
    cd Chat-Bot
     cd client
     npm i 
     cd ..
     cd server
     sudo apt install npm
     sudo npm install pm2@latest
     sudo npm install -g pm2 --force
     pm2 start app.js --name chat_application
     sudo vim /etc/nginx/sites-available/default

         location / {
        proxy_pass http://localhost:5001; #whatever port your app runs on
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }

    sudo nginx -t
    sudo service nginx restart