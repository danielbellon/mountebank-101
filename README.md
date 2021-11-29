# Mountebank 101

First, you need to install NPM, if you don't have it, you can go to https://docs.npmjs.com/getting-started
and get the installation guide. On the other hand, if you want to get further information around Mountebank, 
you can visit http://www.mbtest.org/docs/gettingStarted.

## Installing Mountebank

``` shell
$ npm install -g mountebank
```

Alternatively, you can use docker to get Mountebank on your machine

``` shell
$ docker run --rm -p 2525:2525 -p 8080:8080 bbyars/mountebank:2.5.0 mb start --configfile imposters.ejs
```

## Running Mountebank

``` shell
$ mb
```
Now you have a Mountebank instance in your local environment,
it is important that Mountebank runs on the `2525` port by default so you can use the Mountebank API
to start creating Imposters. If you want to know the Mountebank command line, please go to http://www.mbtest.org/docs/commandLine

## Specifying a configuration file

``` shell
$ sudo mb --configfile imposters.ejs
```
Once Mountebank runs with the configuration file, you can test the configured
imposter in https://localhost:1000/mountebank-101

---
# Step 1
In this step we're going to improve the ejs configuration around Mountebank, and now
we will be able to start the Mountebank server using a npm command:

``` shell
$ npm run mock
```

## Testing imposter ...

``` shell
$ curl --location --request POST 'localhost:8080/step-1'
```
---
# Step 2
Now we're going to configure a failing imposter ..

``` shell
curl --location --request GET 'localhost:9090/step-2'
```
---
# Step 3
In this step we're going to build an SMTP test double, using the bellow instruction:


1. Open your command prompt. Now, connect with telnet using the following command:

``` shell
$ telnet example.com 25
``` 

2. Type ehlo example.com. Some servers also accept helo in place of ehlo.

``` shell
$ ehlo example.com
```

3. Type mail from: username@example.com:

``` shell
mail from: username@example.com
``` 

4. Type rcpt to: friend@hotmail.com, friend2@yahoo.com (replace with your actual recipient name):

``` shell
rcpt to: friend@hotmail.com, friend2@yahoo.com
``` 

5. To write the message - type data, followed by your subject and message. To end the message, put a period on a line by itself and press enter:

``` shell
data
Subject: My Telnet Test Email

Hello,

This is an email sent by using the telnet command.

Your friend,
Me

.
``` 
6. Type quit to exit telnet.
