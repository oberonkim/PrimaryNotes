#Installing wetty on CentOS

To install wetty there are a few prerequisites. First, you need to have an recent version of Node.js installed. If you don't have Node.js installed, enable the Nodesource repository with the following command:
```
$ curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash 
```
sudo yum install gcc-c++ make
Then install the Node.js package using `yum`

```
$ sudo yum install nodejs
```

Make sure Node.js installed correctly by typing the following command

```
$ node --version
```

At the time of this write up, the latest version of Node.js is 8.16.0

Next, install Yarn, a Javascript package manager. It can be installed via Yarn's RPM package repository.

```
$ curl --silent --location https://dl.yarnpkg.com/rpm/yarn.repo | sudo tee /etc/yum.repos.d/yarn.repo
$ sudo yum install yarn
```

The last things we need before installing wetty is `git` and `gcc-c++`

```
$ sudo yum install git gcc-c++
```

We are now ready to install wetty

Clone the source from github

```
$ git clone https://github.com/krishnasrinivas/wetty.git
```

Change directories

```
$ cd wetty
```

Build wetty using `yarn`

```
$ yarn
$ yarn build
```

*Note: Make sure to run `yarn` before `yarn build` otherwise wetty will not install correctly* 
Congratualations! You've installed wetty. There's a few more things we need to do before you get up and running.

To start wetty, run the following `node` command

```
$ node index.js
```

By default, wetty will launch on port 3000. This can be changed by adding the `-p` flag to the command. For example, to launch wetty on port 8080

```
$ node index.js -p 8080
```

For safety adn security reasons, you should probably launch wetty via HTTPS. Generate an SSL ceritificate (self signed) using `openssl`

```
$ openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365 -nodes 
```

Follow the prompt and fillout the information. Next, launch wetty again using your new SSL certificate

```
$ node index.js --sslkey key.pem --sslcert cert.pem -p 8080 &

```

Access wetty via

```
https://Your_Ip_Address:8080/wetty
```

If you're like me and hosting Centos 7 via a vagrant box, you'll need to change some of your config to properly host wetty on a private network with it's own IP and port.

Add these two lines to your vagrant config file
```
    config.vm.network "forwarded_port", guest:80, host: 8080
    config.vm.network :private_network, ip: "192.168.68.8"
end
```
