# RStudio on a Virtual Machine

This is a guide to set up RStudio on a Virtual Machine ("VM"). The goal is to provide a computer capable of running analysis on large datasets.

# Requirements

- A computer with internet access
- [DigitalOcean account](https://try.digitalocean.com/freetrialoffer/)

We will use DigitalOcean as our VM provider. They offer a free trial and have pre-configured VMs ready to use. DigitalOcean calls their VM service "Droplets".

# Quick Setup

Set up a pre-configured Droplet that includes RStudio and other tools from the [Marketplace](https://marketplace.digitalocean.com/).

## Sign into your account

After creating your DigitalOcean account, sign into it.

## Create the Droplet

Navigate to the pre-configured Droplet: [RStudio by Simply Statistics](https://marketplace.digitalocean.com/apps/rstudio).

![rstudio logo](assets/preconfig_rstudio_logo.png)

Click `Create RStudio Droplet`.

![create rstudio](assets/preconfig_rstudio_create_droplet.png)

## Configure the settings

**Choose Region:** Select the location closest to you.

**Datacenter:** Leave as default.

**Choose an image:** This should default to the Rstudio by Simply Statistics.

![rstudio image](assets/preconfig_rstudio_choose_image.png)

**Choose Size:** Select the specifications you need (options detailed [here](https://docs.digitalocean.com/products/droplets/concepts/choosing-a-plan/)).

> Note: free trial accounts may need to request access to the Dedicated CPU/Premium CPUs.

**Backups:** Select if needed.

**Choose Authentication Method:** Select the Password method for simplicity. Create a password for your Droplet.

![authentication method](assets/preconfig_rstudio_auth_method.png)

**Finalize Details:** Change the Hostname to help identify your Droplet. Click `Create Droplet`.

![create droplet](assets/preconfig_rstudio_spin_up_droplet.png)

More details on settings [here](https://docs.digitalocean.com/products/droplets/how-to/create/).

## Set up a RStudio user

Under your project, you will see the newly-created Droplet. Note the green dot next to the Hostname indicating it is active. Click your Droplet.

![new droplet](assets/preconfig_rstudio_resources.png)

In the top menu bar, note your **ipv4 address**. To the right, click the `Console`.

![console](assets/preconfig_rstudio_console.png)

This will open a new window with a console to your Droplet. Look to the bottom for the line `root@<your-hostname>:~#`. This is where you will type commands.

![console](assets/preconfig_rstudio_cli.png)

### Console Steps: Add a RStudio user

Enter the following commands into the console.

1. `adduser <username>`
2. Enter a new password.
    > Note: The password will not be displayed while typing.
3. It will then ask for some basic info. You can leave them blank by pressing enter. At the end, enter `y` to confirm the info is correct.

## Access RStudio

Open a new browser and type your **ipv4 address** and `:8787` into the URL address bar: `<your.ipv4.address>:8787`

This will take you to the RStudio sign in page. Enter the RStudio user credentials you previously created.

![rstudio login](assets/preconfig_rstudio_login.png)

Congrats! You should now have access to RStudio.

![rstudio browser](assets/preconfig_rstudio_browser.png)

# Manual Setup

Set up a Droplet with RStudio.

## Sign into your account

After creating your DigitalOcean account, sign into it.

## Create the Droplet

From your Projects page, click Create and then click Droplets.

![create droplet](assets/manual_rstudio_create_droplet.png)

## Configure the settings

**Choose Region:** Select the location closest to you.

**Datacenter:** Leave as default.

**Choose an image:** Unless you need a specific image, leave as default Ubuntu and default version.

![ubuntu image](assets/manual_rstudio_choose_image.png)

**Choose Size:** Select the specifications you need (options detailed [here](https://docs.digitalocean.com/products/droplets/concepts/choosing-a-plan/)). Note free trial accounts may need to request access to the Dedicated CPU/Premium CPUs.

**Backups:** Select if needed.

**Choose Authentication Method:** Select the Password method for simplicity. Create a password for your Droplet.

![authentication method](assets/preconfig_rstudio_auth_method.png)

**Finalize Details:** Change the Hostname to help identify your Droplet. Click `Create Droplet`.

![create droplet](assets/preconfig_rstudio_spin_up_droplet.png)

More details on settings [here](https://docs.digitalocean.com/products/droplets/how-to/create/).

## Install R and RStudio

Under your project, you will see the newly-created Droplet. Note the green dot next to the Hostname indicating it is active. Click your Droplet.

![new droplet](assets/manual_rstudio_resources.png)

In the top menu bar, note your **ipv4 address**. To the right, click the `Console`.

![console](assets/preconfig_rstudio_console.png)

This will open a new window with a console to your Droplet. Look to the bottom for the line `root@<your-hostname>:~#`. This is where you will type commands.

![console](assets/manual_rstudio_cli.png)

### Console Steps: Install R and  RStudio

> Note: We used Ubuntu v. 24.04. Be sure to check the official install instructions [here](https://posit.co/download/rstudio-server/) if you're on a different image/version.
 
Enter the following commands into the console.

1. `sudo apt update`
2. `sudo apt upgrade -y`
3. `sudo apt install r-base -y`
4. `sudo apt install gdebi-core -y`
5. `wget https://download2.rstudio.org/server/jammy/amd64/rstudio-server-2024.09.0-375-amd64.deb`
6. `sudo gdebi rstudio-server-2024.09.0-375-amd64.deb`
   - You be asked for confirmation. Enter `y` to continue.

> Note: You may receive pop-up windows during the installation process. Leave the default choices and press enter to continue.

The console will display RStudio Server as active. You can check the RStudio Server status with the command: `systemctl status rstudio-server`

![server active](assets/manual_rstudio_server_active.png)

## Final steps

1. See [Console Steps: Add a RStudio user](#console-steps-add-a-rstudio-user).
2. See [Access RStudio](#5-access-rstudio).

---

