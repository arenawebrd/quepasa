<p align="center">
	<img src="https://github.com/sufficit/sufficit-quepasa/raw/main/src/assets/favicon.png" alt="Quepasa-logo" width="100" />	
	<p align="center">Quepasa é um software de código aberto, totalmente gratuito, para troca de mensagens com a plataforma Whatsapp</p>
</p>
<hr />
<p align="left">
	<img src="https://telegram.org/favicon.ico" alt="Telegram-logo" width="32" />
	<span>Grupo e Canal Telegram: </span>
	<a href="https://t.me/quepasa_api" target="_blank">Group</a>
	<span> || </span>
	<a href="https://t.me/quepasa_channel" target="_blank">Channel</a>
</p>
<hr />
<p align="left">
	<img src="https://telegram.org/favicon.ico" alt="Telegram-logo" width="32" />
	<span>Grupo WhatsaAPP: </span>
	<a href="https://t.me/quepasa_api" target="_blank">Group</a>
</p>
----------------------------------------------------------------------------
</p>
Manual de Instalação Chatwoot+N8N+Quepasa
</p>
----------------------------------------------------------------------------
</p>
Vamos precisar de 3 subdomínios
</p>
1º Chatwoot
</p>
chatwoot.dominio.com.br
</p>
2º N8N
</p>
n8n.dominio.com.br
</p>
3º Quepasa
</p>
quepa.dominio.com.br
</p>
----------------------------------------------------------------------------
</p>
Manual de Instalação ChatWoot
</p>
sudo apt update && sudo apt upgrade
</p>
wget https://get.chatwoot.app/linux/install.sh
</p>
chmod +x install.sh
</p>
./install.sh --install
</p>
Use as opções abaixo
</p>
yes
</p>
chatwoot.dominio.com.br
</p>
contato@dominio.com.br
</p>
yes
</p>
yes
</p>
nano /home/chatwoot/chatwoot/.env 
</p>
Adicione
</p>
----------------------------------------------------------------------------
</p>
Manual de Instalação N8N
</p>
sudo apt update && sudo apt upgrade
</p>
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
</p>
sudo apt-get install -y nodejs
</p>
sudo npm install n8n -g
</p>
npm update -g n8n
</p>
npm install pm2 -g
</p>
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
</p>
sudo apt install ./google-chrome-stable_current_amd64.deb
</p>
sudo nano /etc/nginx/sites-available/n8n
</p>
server {
</p>
  server_name n8n.dominio.com.br;
</p>
  location / {
</p>
    proxy_pass http://127.0.0.1:5678;
</p>
    proxy_http_version 1.1;
</p>
    proxy_set_header Upgrade $http_upgrade;
</p>
    proxy_set_header Connection 'upgrade';
</p>
    proxy_set_header Host $host;
</p>
    proxy_set_header X-Real-IP $remote_addr;
</p>
    proxy_set_header X-Forwarded-Proto $scheme;
</p>
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
</p>
    proxy_cache_bypass $http_upgrade;
</p>
    proxy_buffering off;
</p>
    proxy_cache off;
</p>
  }
</p>
  }
</p>
sudo ln -s /etc/nginx/sites-available/n8n /etc/nginx/sites-enabled
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>
pm2 start n8n --cron-restart="0 0 * * *" -- start
</p>
----------------------------------------------------------------------------
</p>
Manual de Instalação API Quepasa
</p>
git clone https://github.com/sufficit/sufficit-quepasa /opt/quepasa-source
</p>
bash /opt/quepasa-source/helpers/install.sh
</p>
sudo nano /etc/nginx/sites-available/quepasa
</p>
server {
</p>
  server_name quepasa.dominio.com.br;
</p>
  location / {
</p>
    proxy_pass http://127.0.0.1:31000;
</p>
    proxy_http_version 1.1;
</p>
    proxy_set_header Upgrade $http_upgrade;
</p>
    proxy_set_header Connection 'upgrade';
</p>
    proxy_set_header Host $host;
</p>
    proxy_set_header X-Real-IP $remote_addr;
</p>
    proxy_set_header X-Forwarded-Proto $scheme;
</p>
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
</p>
    proxy_cache_bypass $http_upgrade;
</p>
  }
</p>
  }

sudo ln -s /etc/nginx/sites-available/quepasa /etc/nginx/sites-enabled
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>
nano /opt/quepasa-source/src/.env
</p>
Alterar linha 1
</p>
WEBSOCKETSSL=false
</p>
para
</p>
WEBSOCKETSSL=true
</p>
systemctl restart quepasa
</p>
----------------------------------------------------------------------------
</p>
Primeira parte da Instalação Finalizadas
</p>
Acesse:
</p>
chatwoot.dominio.com.br
</p>
n8n.dominio.com.br
</p>
quepa.dominio.com.br/setup
</p>
Faça os cadastros em todos eles
</p>
----------------------------------------------------------------------------
</p>
----------------------------------------------------------------------------
</p>
Instalar NO no N8N
</p>
n8n-nodes-chatwoot
</p>
n8n-nodes-quepasa
</p>
Baixar Workflow
</p>
Disponiveis nesse Github
</p>
----------------------------------------------------------------------------
</p>
Criando Seu Bot Agente
</p>
Acesse: chatwoot.dominio.com.br/superadmin
</p>
Crie seu Token Platform Apps
</p>
----------------------------------------------------------------------------
</p>
Crie uma Automação conforme a imagem abaixo
</p>
<img src="https://github.com/EngajamentoFlow/quepasa/blob/main/Automa%C3%A7%C3%A3o.png" alt="Automação" width="100" />
</p>
----------------------------------------------------------------------------
</p>
Criando sua Caixa de Entrada
</p>
Criar um contato no Chatwoot
</p>
Quepasa Control
</p>
control@quepasa.io
</p>
Envia uma mensagem para
 </p>
Contato Criado
</p>
Quepasa Control
</p>
/qrcode
</p>
Apos escanear Qrcode execute os seguintes comandos
</p>
/info
</p>
/webhook update
</p>
Duvidas veja como criar sua Caixa de Entrada
</p>
https://drive.google.com/drive/folders/1iqnDNIUou-Ly_9-WCI8_8J1Fqe9mrCH-?usp=share_link
</p>
----------------------------------------------------------------------------
</p>
Pronto tudo Funcionando
</p>
----------------------------------------------------------------------------
