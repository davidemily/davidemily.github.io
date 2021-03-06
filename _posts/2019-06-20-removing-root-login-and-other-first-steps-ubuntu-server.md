# Removing Root Login  
Just recently I created a fresh [DigitalOcean](http://digitalocean.com/) to play around with a side project. I think managing a remote Ubuntu server can be a little overwhelming so I wanted to walk through some steps to set up a safe, remote environment.  
### Connecting to your Server
DigitalOcean will either prompt you to choose between SSH keys or a one time password. For this example, I chose to use a one-time password, all though I suggest setting up SSH keys which can be created using PuttyGen. For Windows, things are a little tricker but I suggest using Putty, which can be found [here](https://www.putty.org/) or by `choco install putty` if you use the Chocolatey package manager. Soon you should receive an email from DigitalOcean containing your new server's name, ip address, and one-time password. You'll want to enter the IP address in Putty's 'HostName(or IP address)' box, verify the 'Port' box is set to 22, and hit 'Open'. You should receive a warning about this being unsafe if you do not know what you are trying to connect to, but go ahead and hit continue.  

### On the Server
So now you're in! You should have a CMD-looking window asking you to login. For the 'login as' enter `root` and hit the enter key. It will now prompt you for a password, which will be the one-time password sent to you over the email. After entering the password, it'll prompt you to change the password. What ever you choose to be the root password, try to  keep somewhere safe. While you soon won't need to login as root, having the password will save you a possible headache down the road.  

#### Update Server
First thing after resetting the password is to make sure your server is up to date. This can be done easily using Ubuntu's included package manager by typing `sudo apt update && sudo apt upgrade`. This will run through your programs and make sure you have the most up to date versions.  

#### UFW Firewall Setup
Next I'd install a firewall to keep your server safe. I recommend installing the ['UncomplicatedFirewall'](https://help.ubuntu.com/community/UFW), or UFW, on your server. This can be done by typing `sudo apt-get install ufw` although most DigitalOcean droplets come with it pre-installed. Now choose which ports you want enabled and disabled. You will want to ensure the SSH port (how you connect to the server) is enabled so I recommend starting with `sudo ufw allow ssh` command. Next is dependent on what services your server is running. If you're wanting to turn this into a web server, you will probably want to additionally run `sudo ufw allow 80/tcp` and `sudo ufw allow 443/tcp`. Now start the UFW service by typing `sudo ufw enable` and type yes when it asks if you want to proceed. Now that the service is enabled, you can type `sudo ufw status` to see that the service is running and what ports it is allowing. This is useful if down the road you want to add more to enable more features.  

#### Fail2Ban
After enabling a firewall, I'd install [Fail2Ban](https://www.fail2ban.org/wiki/index.php/Main_Page), a service that stops users from brute-forcing entry into your server. This can be done by entering `sudo apt-get install fail2ban` and hitting yes at the prompt. Fail2Ban has additional features such as emailing an address when supicious activity is occuring and the ability to see what IP addresses have been banned, so feel free to read the [Fail2Ban Wiki](https://www.fail2ban.org/wiki/index.php/Main_Page) for more options.  

#### Creating Account
Next, let's create a new account so you will no longer need to do anything under root. First use the 'useradd' command by typing `useradd username` with username being the account's name you'd like to create. Next change the password to that account by typing `passwd username` where username is the account name you just created. Now that there is a new account, let's give it the ability to use sudo commands by entering `usermod -a -G sudo username` with username as the account's name.  

#### Removing Root Login
You're almost done! Now that we have a firewall, a security system, and a new user, let's remove the ability to remotely SSH in by root. Enter `vi /etc/ssh/sshd_config` to open the server system-wide configuration file. Now you'll want to change the line that says 'PermitRootLogin yes' to say 'PermitRootLogin no' and add a line under it saying 'AllowUsers username' where username is the account name you created. This can be done by using the arrow keys to navigate to that row, hit the 'i' key to enter insert mode, delete the 'yes', type in 'no', hitting the 'enter' key, typing `AllowUsers username` where username is the account name you created, hit the 'Q' key to quit insert mode, hit the 'ESC' keyboard key, and then entering `:wq` to save your changes and exit the file.  

#### Restart
Moment of truth! Type in `service ssh restart` to restart the SSH service or just `sudo reboot` to reboot the server. Now open another Putty window and try to connect using root.. you should be denied! Now try with your new account and you should be able to login.  

### You did it!
While this is certainly not the end of security features you should install, this serves as a good baseline when starting a new DigitalOcean droplet or any remote Ubuntu server.