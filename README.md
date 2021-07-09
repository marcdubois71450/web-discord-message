# web-discord-message

During this project we will create a website from zero, at the end on the site it will be possible to send a message on discord. Available on the internet with a domain name in https!

# Create a free domain name on freenom.com.

Replace monsuperdomain.com with what enchants you (especially depending on what will be available for free)

This domaine pointing to www.monsuperdomain.com and monsuperdomain.com towards the IP address of the leo server (DNS registration type A: 62.4.30.245)

Command to see if DNS is working with your domain:
```
dig monsuperdomain.com
```
or
```
nslookup monsuperdomain.com
```
# Connect to leo server 

Windows : 
 - Downlaod putty 
 - Open putty, new ssh connection to tonsuperdomain.com 
 - Ask marc for username


Linux/macOS : 
 - Ask marc for username


On terminal (replace user by your user): 
```
ssh user@monsuperdomain.com
```

Windows & Linux & macOS:


See if you are on the right server, for that we will check the ip:
```
ip a
```
You should find there the address 62.4.30.245 (the one you have configured in the DNS)

# Generate the HTTPS certificate. 

For that we will use let's encrypt, in one command you have a certificate!
The command (to be executed on the leo server, when the DNS is configured):
```
certbot certonly
````
The first answer select
```
1: Nginx Web Server plugin (nginx)
````
Then answer the question he asks you.


# Config web/http server.
On leo's server there is nginx the web server. 

Go to the nginx config folder:
```
cd /etc/nginx/conf.d/
```
Look at the files that if already found:
```
ls
```
Be curious, look inside a file, the cat command displays the contents of a file:
```
cat leoberthier.com.conf
```
You can already see what you need to change after you copy paste this file.

Now copy paste one of the configuration replacing monsuperdomain.com with your domain, we will modify the content in the next step.
```
cp leoberthier.com.conf monsuperdomain.com.conf
```
Look at your file, to see what to change:
```
cat monsuperdomain.com.conf
```
Basically you have to replace all the leoberthier.com by monsuperdomain.com, here is a magic command that allows you to do it:
```
sed -i -e "s/leoberthier.com/monsuperdomain.com/g" monsuperdomain.com.conf
```
There is one line left to modify:
```
root /var/www/leoberthier;
```
This line represents the entry point of the site, basically where the html files are. The home page should be called index.html

We will therefore create this folder, with an index.html file in it to test.

Already move to the right place:
```
cd /var/www/
```
List the files to see that you are in the right place:
```
ls
```
You should see the leoberthier folder.


You will therefore create the folder for your site:
```
mkdir monsuperdomain
```
Now move to this folder:
```
cd monsuperdomain
```
or
```
cd /var/www/monsuperdomain
```

We can now create our index.html file, for it's done:
```
nano index.html
```
And paste it a simple html piece that says Hello World!


Save: Ctrl + O


Exit: Crtl + X

Check that your HTML is correct:
```
cat index.html
```
We will now be able to tell nginx (our http / web server) where the site root folder is located. For this we go back to our nginx configuration folder:
```
cd /etc/nginx/conf.d/
```
We will now edit our configuration file:
```
nano monsuperdomain.com.conf
```

Save: Ctrl + O


Exit: Crtl + X


Replace line:
```
root /var/www/leoberthier;
```
Through
```
root /var/www/monsuperdomain;
```


Everything should be configured, you must now restart nginx for it to take into account the new configuration, for that:
```
systemctl reload nginx
```


Go to https://monsuperdomain.com/

Ok now that the server is ready, we go to the website/api part.

# Create Python Script for send message on discord general channel. 

# Create Flask Api.

Blabla 

# Create Web App.

Blabla 

# Config Nginx For React App with Flask API. 

BlaBla 

# Modify flask Api & React App for send on choice by user channel (general, code, musique-tracklist). 

Blabla


Enjoy! 
