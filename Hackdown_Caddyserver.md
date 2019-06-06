```
---
layout: post
title: "Caddyserver"
date: To be Decided
categories:
  - Webserver
  - Technical
description: “”
featured-img: caddy
---
```
# Caddy Server

## What is CaddyServer?
  Caddy server is a simple, yet HEAVILY extensible webserver written in go.
  When you install caddyserver, it will download only a singl e bianry and give it the proper permissions. Be default this program will not have extensions builtin, but they can easily be added on the website.

  But also, CaddyServer will automatically get a VALID SSL CERTIFICATE from `letsencrypt.org` for your domain. 
  ##### Note: this will not work for a domain that is not exposed to the clear internet. Which means LAN (local area network) IP Adresses and custom DNS configs will not get a ssl certificate

## How does it work and what requirments does it have?
  It works by making a simple webserver for displaying static content like most webservers. It can also handle PHP in pretty much the same way `nginx` does. 
  It has verry little in the way of requirements, pretty much just have a supported CPU and system. which to say the least, the only desktop pc platform it cant run on that i know of, is DOS. Purely because it uses a 16bit architecture and no one wants to support that.

  The program is opensource and written in `golang` so if youve had expirence with golang, you can make edits as you wish.

## Use cases?
There are a multitude of usecases for caddyserver, one of which that I (The author of this article) uses alot, is for quickly testing html/js based applications
## How does one install?
  Simple really, just head on over to [Their download page](https://caddyserver.com/download) and follow the instructions!
  
  There are a few ways to configure caddy beyond the defaults you get when you run the command. 
  For example. persay you are trying to test a html application that needs some specifc server side settings and the files are stored at `/home/user/projects/html-app/`. 
  Make a file in the application folder named `Caddyfile`, caddy will look for this file in its current working directory, and if it exists, use that configuration. 
  Or you can specify a different Caddyfile that is somewhere else on your system by using the `-conf` flag like so, `caddy -conf /home/user/caddyfiles/basic` and it will load that specific config file. I use this to keep myself from writing the same lines of code over and over and just have specific config files for each of these tasks.

Persay you want to have a universal config that you can import to save you time for example, `php`. Make the file with the php caddy config, `/home/user/caddyfiles/php` and add this to the appropriete location in your original Caddyfile `import /home/user/caddyfiles/php`

### DISCLAIMER: You must manually make these configs yourself

## Example Caddyfile. 
```
:80 {
  index index.html
  log     ./Caddylog
  errors  ./Caddyerr
}
```