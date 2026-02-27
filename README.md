## Installing OpenClaw on Azure VM (Free Setup) Using Ollama

This guide walks through how I installed OpenClaw on a Microsoft Azure Virtual Machine using the Azure free trial ($200 credit) and connected it to a local LLM using Ollama.

The goal of this lab was simple:

- Use Azure free credits
- Deploy OpenClaw
- Run a local LLM with Ollama
- Avoid paid APIs


If you're learning cloud, AI, or just want to experiment without spending money, this setup works great.


## What is OpenClaw?

OpenClaw (formerly Clawdbot/Moltbot) is an open-source, autonomous AI agent that runs locally on your machine. It acts as a personal assistant, interacting with applications, reading/writing files, and automating tasks via messaging platforms like Discord or Telegram.
You can use it for:  
  - Building AI chatbots
  - Connecting to messaging platforms
  - Testing LLM integrations
  - Automation experiments
  - Running AI in your own controlled lab and many more....

For this demo, I’m keeping it simple and connecting it to a local LLM using Ollama.


## Why Ollama?

Instead of using paid APIs, I used Ollama.
Ollama allows you to run Large Language Models locally. That means:
  - No API key required
  - No token charges
  - Fully local execution
  - Good for testing and labs

For learning and demos, this is perfect.


## Step 1 – Create Azure Free Account
- First, sign up for the Azure Free Trial.
- Azure gives you $200 free credit (30 days)
<img width="844" height="276" alt="Screenshot 2026-02-26 at 6 56 01 PM" src="https://github.com/user-attachments/assets/129cfd11-4bbd-45b4-af7e-179a6c827977" />

⚠️ Important: Always double-check resource and virtual machine image pricing before creating anything. Selecting the wrong VM size or disk type can generate charges.

## Step 2 – Create a Virtual Machine
After logging into Azure:
  - Click Create a Resource
  - Select Virtual machines
  - Fill in the details
  - You can follow your own preferences, but here’s what you must be careful about:
      - Choose a region that supports free-tier resources
      - Select a free-eligible VM size
      - Avoid premium SSD disks
      - Keep networking simple

Take your time here. Most surprise bills happen because of wrong VM size or storage selection.
<img width="663" height="694" alt="Screenshot 2026-02-26 at 6 54 48 PM" src="https://github.com/user-attachments/assets/f41ad66f-7473-47b4-8de6-0bb3879976c3" />

<img width="855" height="680" alt="Screenshot 2026-02-26 at 6 57 49 PM" src="https://github.com/user-attachments/assets/01d39f5c-105b-4acd-9353-257a5cbf2fe4" />


## Step 3 – Connect to the VM
Once the VM is deployed:
- Open the Virtual Machine page
- Click Connect
- Choose Connect via Bastion

You can use SSH to remotely connect, but for this lab, I used Bastion since it’s easier directly from the browser.
<img width="1034" height="775" alt="Screenshot 2026-02-26 at 6 59 18 PM" src="https://github.com/user-attachments/assets/7ed30581-2652-43db-8f3b-6f82c2b54cb4" />

If you didn’t set a password or forgot it:
- Go to VM Overview
- Click Help
- Select Reset password
- Set a new password
After that, connect again using the new credentials.
<img width="959" height="606" alt="Screenshot 2026-02-26 at 7 00 45 PM" src="https://github.com/user-attachments/assets/3e65e937-f263-4706-998f-9b2fbb344d24" />

<img width="1037" height="634" alt="Screenshot 2026-02-26 at 7 02 25 PM" src="https://github.com/user-attachments/assets/9d0cfef2-eacd-4291-a0fd-0fc7e6c41deb" />


## Step 4 – Install OpenClaw
Once connected to your VM terminal, run the installation commands one by one.
* `sudo apt-get update && sudo apt-get upgrade -y` — Updates the package list and upgrades all installed packages to the latest available versions to keep the system secure and up to date.

* `curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -` — Adds the official NodeSource repository to your system so you can install Node.js version 22.

* `sudo apt-get install -y nodejs` — Installs Node.js (including npm) on your virtual machine.

* `sudo apt-get install -y git build-essential cmake` — Installs Git and essential development tools required to compile and build software like OpenClaw and other dependencies.


<img width="1036" height="663" alt="Screenshot 2026-02-26 at 7 10 45 PM" src="https://github.com/user-attachments/assets/9f1aaa75-b93e-4823-9610-5c7d0f49633d" />

- Command to install OpenClaw
    - npm install -g openclaw@latest
<img width="965" height="797" alt="Screenshot 2026-02-26 at 7 11 34 PM" src="https://github.com/user-attachments/assets/965f6959-32d6-4134-b79c-5a25e803a63c" />

## Onboarding in OpenClaw
After installation completes, start the onboarding process.
You can skip most advanced settings for now. I previously configured ChatGPT and Telegram API integrations, but for this demo we’re keeping it simple and using Ollama instead.

<img width="1040" height="432" alt="Screenshot 2026-02-26 at 7 13 40 PM" src="https://github.com/user-attachments/assets/2bbdcfb8-4a0f-4398-9f5e-acd55e929a9c" />
<img width="600" height="766" alt="Screenshot 2026-02-26 at 7 15 19 PM" src="https://github.com/user-attachments/assets/8ecd1e01-8255-458d-9399-215917b4b354" />

## Step 5 – Install Ollama
Now install Ollama inside your VM.
- Command to install Ollama
    - curl -fsSL https://ollama.com/install.sh | sh
<img width="1024" height="793" alt="Screenshot 2026-02-26 at 7 16 20 PM" src="https://github.com/user-attachments/assets/6c1bd1fe-86d2-4ec3-952c-90a4cb012cba" />

<img width="1044" height="713" alt="Screenshot 2026-02-26 at 7 17 14 PM" src="https://github.com/user-attachments/assets/56c42956-9085-4bf5-bf28-846e46773be5" />

Run Ollama with this command
  - ollama run llama3
<img width="1015" height="738" alt="Screenshot 2026-02-26 at 7 18 38 PM" src="https://github.com/user-attachments/assets/71e0ec0b-aaaf-4099-9165-d881091ee0cb" />


## Step 6 – Test the Chatbot
Now it's ready!

Test the chatbot.
- Ask it:
    - Technical questions
    - Random prompts
    - Automation ideas
    - Even casual conversation
  
Yes, you can even flirt with it, just don’t fall in love 😄
<img width="1025" height="495" alt="Screenshot 2026-02-26 at 7 20 03 PM" src="https://github.com/user-attachments/assets/be5e9855-e62d-4e1f-9b66-284336178dbf" />


At this point, you have a local LLM running inside your Azure VM.
No paid API. No token usage.

.
.







