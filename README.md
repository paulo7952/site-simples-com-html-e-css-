# site-simples-com-html-e-css

Olá pra você que escolheu esse repositório! Nessa repositório você vai enconntrar um site bem simples feito com as tecnolgias html, css esse site(website) usando html e css foi feito apenas para praticar os estudos sobre programação front-end. Espero que gostes e também aproveita e vai dar uma passeada✌ lá no canal.

## [🛠Assistir](https://www.youtube.com/watch?v=3R7QtNcwE3c)
## [⚠Me Ajude](https://www.youtube.com/channel/UCxKIsX5OXyyNWVmomuDc-LA?sub_confirmation=1)
# Preview
![ubuntu](https://raw.githubusercontent.com/paulo7952/site-simples-com-html-e-css-/refs/heads/main/images.jfif)


COMO FAZER UM SCRIPT EM HTML PARA INSTALAÇÃO E CONFIGURACÃO DO APACH:
#!/bin/bash

# Script de instalação do Apache2 com acesso via 'meusite' no navegador
# Pode ser executado como usuário normal (usa sudo quando necessário)

# 1. Atualizar sistema
sudo apt update && sudo apt upgrade -y

# 2. Instalar Apache
sudo apt install apache2 -y

# 3. Iniciar e ativar Apache
sudo systemctl start apache2
sudo systemctl enable apache2

# 4. Criar diretório do site
mkdir -p ~/meusite/public_html

# 5. Criar página index.html
cat <<EOF > ~/meusite/public_html/index.html
<html>
<head>
    <title>Meu Site</title>
</head>
<body>
    <h1>Bem-vindo ao Meu Site!</h1>
    <p>Acessado digitando apenas 'meusite' no navegador</p>
</body>
</html>
EOF

# 6. Configurar virtual host
sudo bash -c 'cat <<EOF > /etc/apache2/sites-available/meusite.conf
<VirtualHost *:80>
    ServerName meusite
    DocumentRoot /home/'"$USER"'/meusite/public_html
    ErrorLog \${APACHE_LOG_DIR}/error.log
    CustomLog \${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
EOF'

# 7. Adicionar entrada no /etc/hosts
sudo sh -c "echo '127.0.0.1 meusite' >> /etc/hosts"

# 8. Habilitar site e desabilitar default
sudo a2dissite 000-default.conf
sudo a2ensite meusite.conf

# 9. Reiniciar Apache
sudo systemctl restart apache2
echo "Configuração concluída!"
echo "Agora você pode acessar seu site digitando apenas 'meusite' no navegador"

# 10 instalação do webmin:
para poder baixar o wwbmin pelo terminal, primeiramente você deve alterar as configurações de rede.
altere a rede para um metodo IPV4 para DNS automatico.
em DNS coloque o IP: 192.168.0.10
wget https://www.webmin.com/download/deb/webmin-current.deb
sudo dpkg -i webmin-current.deb
sudo apt -f install "para corrigis as falhas"
para deixar tudo com  estava antes, novamente altere as configurações de rede
mudando o metodo IPV4 para manual e faça as seguintes alterações:
IP: 192.168.0.10
MASCARA: 255.255.255.0
GATEWAY: 192.168.0.1
Ligue e desligue a rede
de o comando: ip a para checar as informações.
