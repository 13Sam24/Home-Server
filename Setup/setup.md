# Home Server Setup

## 1. Choosing an operating system

First, I need to decide on an operating system to use for the server. After doing some research there are a few main options including, Ubuntu Server, proxmox, Windows Server and TrueNAS. For this project I will be using ubuntu server as I do have some experience with Linux and It should allow me to run multiple different services and easily scale it in the future.

## 2. Server Hardware

For this project I will be using a second hand desktop as the server. Since it did not come with storage I had to add it myself with things from old devices using one drive for the OS and one for data. I have pre routed cables for future HDDs.

- **Model** Lenovo 90G8
- **CPU** Intel Core I5-7400
- **RAM** 8GB DDR4
- **Storage 1** 240GB 2.5" SSD
- **Storage 2** 1TB HDD

## 3. Operating System Install

The next thing to do it to put ubuntu server on the server. To do this I downloaded Ubuntu server from there website and put it onto a USB with balenaEtcher. I then booted into it with the computer and went through the setup procedure. 

## 4. SSH

Once it was setup I setup SSH so that I am able to access the device from my main computer. This will let me connect it to ethernet nearer the router without me having to go down there very time when I want to do something. To make sure that it stays secure I made sure to add an SSH key to the server. This was generated through the windows terminal. This works through the server using the public key that I provided it to encrypt a message and sending it to the device that wants to connect. If that device can unencrypt it correctly and sends back the correct message then it is allows access. I have done this to make the server more secure as I don't want anyone on the WIFI to be able to access the server incase they should not be on the WIFI or dont know what they are doing.

## 5. Mounting the HDD

Since the HDD was unplugged during the setup I then had to plug it back in and mount it. I did this by first erasing it. To do this I first had to find the name of the drive with the command 'lsblk' which listed all my drives. I then formatted it with 'sudo mkfs.ext4 /dev/sda1. I then made a new directory called hdd1 in the /mnt directory and mounted it with 'sudo mount /dev/sda1 /mnt/hdd1' This kept the file structure clean so it is easier to manage.

Since the server runs ubuntu I have found that the easiest way to run multiple things is through installing docker. Docker is a platform that can be used to run applications and manage them. They can be easaly set up with a .yml file. To set this up I first installed it with
