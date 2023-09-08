<p align="center"><img src="https://i.imgur.com/DIpuNTI.jpg"></p>

<p align="center">
    <a href="https://twitter.com/thewhiteh4t">
      <img src="https://img.shields.io/badge/-TWITTER-black?logo=twitter&style=for-the-badge">
    </a>
    &nbsp;
    <a href="https://twc1rcle.com/">
      <img src="https://img.shields.io/badge/-THE WHITE CIRCLE-black?logo=&style=for-the-badge">
    </a>
    &nbsp;
    <a href="https://thewhiteh4t.github.io/">
      <img src="https://img.shields.io/badge/-BLOG-black?logo=dialogflow&style=for-the-badge">
    </a>
</p>

<p align="center">
  <br>
  <b>Available in</b>
  <br>
  <img src="https://i.imgur.com/1wJVDV5.png">
</p>

<p>
  <a style="margin-right: 10px;" href="https://github.com/thewhiteh4t/seeker#installation">
    <img src="https://dabuttonfactory.com/button.png?t=INSTALL&f=Open+Sans&ts=15&tc=000&hp=25&vp=10&c=5&bgt=unicolored&bgc=00e2ff">
  </a>
  <a style="margin-right: 10px;" href="https://github.com/thewhiteh4t/seeker#usage">
    <img src="https://dabuttonfactory.com/button.png?t=USAGE&f=Open+Sans&ts=15&tc=000&hp=25&vp=10&c=5&bgt=unicolored&bgc=00e2ff">
  </a>
  <a href="https://github.com/thewhiteh4t/seeker#demo">
    <img src="https://dabuttonfactory.com/button.png?t=DEMO&f=Open+Sans&ts=15&tc=000&hp=25&vp=10&c=5&bgt=unicolored&bgc=00e2ff">
  </a>
</p>

O conceito por trás do Seeker é simples, assim como hospedamos páginas de phishing para obter credenciais, por que não hospedar uma página falsa que solicita sua localização, como muitos sites populares baseados em localização. Leia mais no Blog thewhiteh4t’s. Seeker hospeda um site falso que pede permissão de localização e, se o alvo permitir, podemos obter:

Longitude Latitude Precisão Altitude - nem sempre disponível Direção - apenas disponível se o usuário estiver se movendo Velocidade - apenas disponível se o usuário estiver se movendo Juntamente com as informações de localização, também obtemos informações do dispositivo sem permissões:

ID exclusivo usando impressão digital de tela Modelo do dispositivo - nem sempre disponível Sistema operacional Plataforma Número de núcleos de CPU - resultados aproximados Quantidade de RAM - resultados aproximados Resolução da tela Informações da GPU Nome e versão do navegador Endereço IP público Endereço IP local Porta local Reconhecimento automático de endereço IP é realizado após o recebimento das informações acima.

Esta ferramenta é uma prova de conceito e é apenas para fins educacionais, Seeker mostra quais dados um site malicioso pode coletar sobre você e seus dispositivos e por que você não deve clicar em links aleatórios e permitir permissões críticas, como localização etc.

Como isso é diferente da GeoLocalização IP Outras ferramentas e serviços oferecem GeoLocalização IP que NÃO é precisa e não fornece a localização do alvo, mas sim a localização aproximada do ISP.

### Seeker usa HTML API e obtém permissão de localização e, em seguida, obtém longitude e latitude usando o hardware GPS, que está presente no dispositivo, portanto, Seeker funciona melhor com smartphones, se o hardware GPS não estiver presente, como em um laptop , Seeker recorre à GeoLocalização IP ou procurará coordenadas armazenadas em cache.

Geralmente, se um usuário aceita permissões de localização, a precisão das informações recebidas é precisa em aproximadamente 30 metros

### A precisão depende de vários fatores que você pode ou não controlar, como:

Dispositivo - não funcionará em laptops ou telefones que tenham GPS quebrado Navegador - alguns navegadores bloqueiam javascripts Calibração do GPS - se o GPS não estiver calibrado, você pode obter resultados imprecisos e isso é muito comum Modelos disponíveis:

### Google Drive  
### WhatsApp  
### Telegrama Zoom 
### Google reCAPTCHA 
Crie seu próprio modelo! As etapas para permitir que você crie seu modelo são descritas neste tutorial

Depois que seu modelo estiver pronto, não se esqueça de propô-lo à comunidade por meio de um PR (pull request)

Testado em: Kali Linux BlackArch Linux Ubuntu Fedora Kali Nethunter Termux Parrot OS OSX - Monterey v.12.0.1 

### Instalação

### Kali Linux / Arch Linux / Ubuntu / Fedora / Parrot OS / Termux

```bash
git clone https://github.com/thewhiteh4t/seeker.git
cd seeker/
chmod +x install.sh
./install.sh
```

### BlackArch Linux

```bash
sudo pacman -S seeker
```

### Docker

```bash
docker pull thewhiteh4t/seeker
```

### OSX
```bash
git clone https://github.com/thewhiteh4t/seeker.git
cd seeker/
python3 seeker.py
````

In order to run in tunnel mode, install ngrok by running this command in the terminal:
```bash
brew install ngrok/ngrok/ngrok

ngrok http 8080
````

## Usage

```bash
python3 seeker.py -h

usage: seeker.py [-h] [-k KML] [-p PORT] [-u] [-v] [-t TEMPLATE] [-d] [--telegram token:chatId] [--webhook WEBHOOK]

options:
  -h, --help                            show this help message and exit
  -k KML, --kml KML                     KML filename
  -p PORT, --port PORT                  Web server port [ Default : 8080 ]
  -u, --update                          Check for updates
  -v, --version                         Prints version
  -t TEMPLATE, --template TEMPLATE      Auto choose the template with the given index
  -d, --debugHTTP                       Disable auto http --> https redirection for testing purposes 
                                        (only works for the templates having index_temp.html file)
  --telegram                            Send info to a telegram bot, provide telegram token and chat to use
                                        format = token:chatId separated by a colon
  --webhook                             Send events to a webhook endpoint to be processed
                                        Note : endpoint must be unauthenticated and accept POST request

#########################
# Environment Variables #
#########################

Some of the options above can also be enabled via environment variables, to ease deployment.
Other parameters can be provided via environment variables to avoid interactive mode.

Variables:
  DEBUG_HTTP            Same as -d, --debugHTTP
  PORT                  Same as -p, --port
  TEMPLATE              Same as -t, --template
  TITLE                 Provide the group title or the page title
  REDIRECT              Provide the URL to redirect the user to, after the job is done
  IMAGE                 Provide the image to use, can either be remote (http or https) or local
                        Note : Remote image will be downloaded locally during the startup
  DESC                  Provide the description of the item (group or webpage depending on the template)
  SITENAME              Provide the name of the website
  DISPLAY_URL           Provide the URL to display on the page
  MEM_NUM               Provide the number of group membres (Telegram so far)
  ONLINE_NUM            Provide the number of the group online members (Telegram so far)
  TELEGRAM              Provide telegram token and chat to use to send info to a telegram bot
                        format = token:chatId separated by a colon
  WEBHOOK               Provide the webhook url to forward the events to 
                        Note : endpoint should be unauthenticated and accept POST method
                        

##################
# Usage Examples #
##################

# Step 1 : In first terminal
$ python3 seeker.py

# Step 2 : In second terminal start a tunnel service such as ngrok
$ ./ngrok http 8080

###########
# Options #
###########

# Ouput KML File for Google Earth
$ python3 seeker.py -k <filename>

# Use Custom Port
$ python3 seeker.py -p 1337
$ ./ngrok http 1337

# Pre-select a specific template
$ python3 seeker.py -t 1

################
# Docker Usage #
################

# Step 1
$ docker network create ngroknet

# Step 2
$ docker run --rm -it --net ngroknet --name seeker thewhiteh4t/seeker

# Step 3
$ docker run --rm -it --net ngroknet --name ngrok wernight/ngrok ngrok http seeker:8080
```

## Local Tunnels
Use
```
ssh -R 80:localhost:8080 nokey@localhost.run
```
as an alterntive to ngrok

## Demo

**YouTube**

<a href="https://youtu.be/Q91cTFwIvLc">
  <img src="https://i3.ytimg.com/vi/Q91cTFwIvLc/maxresdefault.jpg">
</a>
