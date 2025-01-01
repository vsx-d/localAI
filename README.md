# Run Large Language Models locally in WSL or natively in Linux with Docker 🚀
### Introduction 
This wiki provides step-by-step instructions for setting up and running Large Language Models (LLMs) locally in Windows Subsystem for Linux (WSL) or Linux natively with Docker. This guide is perfect for anyone who wants to host LLaMA, Stable Diffusion, or similar models on their local machine without relying on cloud services.

### Disclaimer⚠️
This tutorial assumes a slight knowledge of 
* **Linux**.  
* **WSL**  
* **Docker**
* **CLI**
  
While the steps are straightforward, familiarity with these topics will help you troubleshoot any issues that might arise.

However, if you're new to these concepts, don't worry! Just follow the instructions step by step, and you'll be able to set everything up successfully. If any issues come up you can feel free to contact me or you can always revisit the steps to make sure everything is set up correctly.

### Prerequisites
Before you begin, ensure that you meet the following requirements:

* Windows 10 or later..

* An NVIDIA GPU (optional but highly recommended for better performance).
* At least 8 GB of RAM (more is recommended for larger models).  

### Happy building! 🚀
***


## 1. Setting up WSL (Linux users can skip this step) 
* Open terminal and execute the following command to install WSL.  
`wsl --install`   

![399558738-2f718026-730a-4334-bb9a-3de0169d6ca4](https://github.com/user-attachments/assets/396a585b-e963-4d8f-8719-7b00afc6cd87)


 

* Now create username and password (Write down the password somewhere safe).  
* After creating a user open a new session of the terminal and run.  
`wsl`  

![Screenshot 2025-01-01 170352](https://github.com/user-attachments/assets/086679a9-ae8e-411d-a332-0b05ee645328)


* Update and Upgrade packages in ubuntu by running below commands   
`sudo apt update` and `sudo apt upgrade` 

## 2. Downloading and running [Ollama](https://ollama.com/download/linux)   
* Paste this command to download Ollama inside WSL or Linux CLI.  
`curl -fsSL https://ollama.com/install.sh | sh` 

![image](https://github.com/user-attachments/assets/33b89c1c-a800-4b64-90b3-a47020c60af1) 

* Download LLaMa models  
`ollama pull llama3.1`
`ollama pull llava`  
* You can download other models too by executing   
`ollama pull _followed by model name_`

![image](https://github.com/user-attachments/assets/8e680209-d11e-46f4-878b-3ae13e45b2e6)


* Run the LLaMA 3.1 model using Ollama, execute the following command in WSL.  
`ollama run llama3.1`  

![image](https://github.com/user-attachments/assets/eb5e7f0d-0ef3-46d4-9ff6-2e42f724a767)

### Now you can start chatting with AI right here in the Command line.  

## 3. Installing  [Docker Container](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) to set-up a webUI for LLM.  
* Add Docker's official GPG key:  
`sudo apt-get update`   
`sudo apt-get install ca-certificates curl`  
`sudo install -m 0755 -d /etc/apt/keyrings`    
`sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc`   
`sudo chmod a+r /etc/apt/keyrings/docker.asc`  

* Add the repository to Apt sources: (press enter after typing "echo \")   
`echo \  
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update`  

![image](https://github.com/user-attachments/assets/c337099e-717c-47f5-a918-39dbcf251db0)


* Create a container  
`sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`  

## 4.Deploying open-webUI container.  
* Simply copy paste this command.    
`docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main`  

![image](https://github.com/user-attachments/assets/edf91011-0824-4d4c-85fd-01178a0201ca)  

* After above steps go to the web browser and search  
`localhost:8080`  
  
* Sign up with your email and create a password.  
 
![image](https://github.com/user-attachments/assets/729697a5-2fd0-42ca-9e27-f189630aaaf0)  

# And Boom!🔥 You’ve got your own AI Model running locally.🚀🤖💻

![Screenshot 2025-01-01 181954](https://github.com/user-attachments/assets/5c07d231-e362-4ffb-b27c-79fe140c1b5d)

# Tips🖊️
* To analyze images and recognize files, use the LLaVA 7B model.  
* For image generation, use Stable Diffusion Automatic 1111. Stay tuned, as I’ll be writing a detailed wiki on how to set it up very soon! 🎨✨
  



