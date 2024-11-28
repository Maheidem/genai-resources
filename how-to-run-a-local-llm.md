%md
# How to Run Large Language Models Locally: A Comprehensive Guide

## Table of Contents

1. [Introduction](#introduction)
2. [Why Run Language Models Locally?](#why-run-language-models-locally)
3. [Prerequisites](#prerequisites)
   - [Hardware Requirements](#hardware-requirements)
   - [Software Requirements](#software-requirements)
4. [Installing LLM Studio](#installing-llm-studio)
   - [For Windows](#for-windows)
   - [For macOS](#for-macos)
   - [For Linux](#for-linux)
5. [Downloading and Using Models in LLM Studio](#downloading-and-using-models-in-llm-studio)
   - [Understanding Model Sizes and Quantization](#understanding-model-sizes-and-quantization)
   - [Downloading a Model](#downloading-a-model)
   - [Interacting with the Model](#interacting-with-the-model)
6. [Setting Up a ChatGPT-like Interface](#setting-up-a-chatgpt-like-interface)
   - [Installing Docker](#installing-docker)
   - [Running the Web UI](#running-the-web-ui)
   - [Accessing the Interface](#accessing-the-interface)
7. [Configuring the Interface to Use Local Models](#configuring-the-interface-to-use-local-models)
   - [Starting the LLM Studio Server](#starting-the-llm-studio-server)
   - [Connecting the Interface to LLM Studio](#connecting-the-interface-to-llm-studio)
8. [Using OpenAI's API with the Interface](#using-openais-api-with-the-interface)
   - [Obtaining an OpenAI API Key](#obtaining-an-openai-api-key)
   - [Configuring the Interface to Use OpenAI Models](#configuring-the-interface-to-use-openai-models)
   - [Cost Considerations](#cost-considerations)
9. [Exploring Advanced Models](#exploring-advanced-models)
   - [Understanding Hardware Limitations](#understanding-hardware-limitations)
   - [Downloading and Using Advanced Models](#downloading-and-using-advanced-models)
10. [Conclusion](#conclusion)
11. [Additional Resources](#additional-resources)

---

## Introduction

With the rapid advancement of artificial intelligence and large language models (LLMs) like ChatGPT, there's a growing interest in running these models locally on personal computers. This guide provides a comprehensive walkthrough on how to set up and run LLMs on your machine, ensuring privacy, security, and potentially saving costs associated with cloud-based solutions.

## Why Run Language Models Locally?

Running LLMs locally offers several benefits:

- **Privacy and Security**: Your data stays on your machine, reducing the risk of sensitive information being collected by external servers.
- **Cost Savings**: Avoid recurring subscription fees for premium AI services.
- **Customization**: Ability to tweak and experiment with models as per your requirements.
- **Accessibility**: Use AI models even without an internet connection.

## Prerequisites

### Hardware Requirements

- **Minimum RAM**: 8 GB (models with smaller sizes)
- **Recommended RAM**: 16 GB or more (for better performance and ability to run larger models)
- **Processor**: Modern CPU (Intel, AMD, or Apple Silicon)
- **Storage**: Sufficient disk space to store models (models can range from a few GBs to over 30 GB)

### Software Requirements

- **Operating System**: Windows, macOS, or Linux
- **Docker**: For setting up the ChatGPT-like interface
- **LLM Studio**: Application to download and run models locally
- **Internet Connection**: For downloading software and models

## Installing LLM Studio

LLM Studio is a versatile tool that allows you to download and run language models locally. It supports Windows, macOS, and Linux.

### For Windows

1. **Download LLM Studio**:
   - Visit the [LLM Studio website](https://lmstudio.ai/download) (replace with actual URL).
   - Click on the Windows download link.

2. **Install LLM Studio**:
   - Run the downloaded installer.
   - Follow the on-screen instructions to complete the installation.

### For macOS

1. **Download LLM Studio**:
   - Visit the [LLM Studio website](https://lmstudio.ai/download).
   - Click on the macOS download link.

2. **Install LLM Studio**:
   - Open the downloaded `.dmg` file.
   - Drag the LLM Studio app to your Applications folder.

### For Linux

1. **Download LLM Studio**:
   - Visit the [LLM Studio website](https://lmstudio.ai/download).
   - Download the Linux installer or use the provided terminal commands.

2. **Install LLM Studio**:
   - Open a terminal.
   - Navigate to the downloaded file.

## Downloading and Using Models in LLM Studio

### Understanding Model Sizes and Quantization

- **Model Size**: Determines the amount of RAM required to run the model.
- **Quantization**: Process of reducing the model's precision to make it smaller and faster at the cost of some accuracy.

### Downloading a Model

1. **Open LLM Studio**.
2. **Navigate to the 'Discover' Tab**:
   - Here, you can browse available models.

3. **Select a Model Suitable for Your Hardware**:
   - For 8 GB RAM: Consider models like LLaMA 2 7B with higher quantization (e.g., Q8).
   - For 16 GB or more: You can choose larger models like LLaMA 2 13B or even 30B.

4. **Download the Model**:
   - Click on the model.
   - Click the **Download** button.
   - Wait for the download to complete.

### Interacting with the Model

1. **Load the Model**:
   - Go to the **Chat** tab.
   - Select the model from the dropdown at the top.

2. **Start a Conversation**:
   - Type your prompt in the input box.
   - Press **Enter** or click **Send**.
   - The model will generate a response.

## Setting Up a ChatGPT-like Interface

To enhance your experience, you can set up a web interface similar to ChatGPT using Docker.

### Installing Docker

1. **Download Docker Desktop**:
   - Visit the [Docker website](https://www.docker.com/products/docker-desktop).
   - Choose the version for your operating system.

2. **Install Docker**:
   - Run the installer.
   - Follow the on-screen instructions.

3. **Verify Installation**:
   - Open a terminal or command prompt.
   - Run `docker --version`.
   - Ensure Docker is running.

### Running the Web UI

1. **Obtain the Docker Command**:
   - Use the following command to pull and run the web UI container:

     ```bash
     docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
     ```

2. **Execute the Command**:
   - Paste the command into your terminal.
   - Press **Enter**.
   - Docker will download the image and start the container.

### Accessing the Interface

1. **Open a Web Browser**.
2. **Navigate to**: `http://localhost:3000`.
3. **Create an Account**:
   - The first time you access the interface, you'll be prompted to create a local account.
   - Set a username and password.

## Configuring the Interface to Use Local Models

### Starting the LLM Studio Server

1. **Open LLM Studio**.
2. **Go to the 'Developer' Tab**:
   - Click on **Start Server**.
   - Enable **Serve Local Network**.

### Connecting the Interface to LLM Studio

1. **In the Web Interface**, click on the **Settings** icon (usually a gear icon).
2. **Navigate to 'Admin' > 'Connections'**.
3. **Add a New Connection**:
   - Choose **OpenAI** as the provider.
   - **API Base URL**: Enter `http://host.docker.internal:1234/v1`.
   - **API Key**: Leave this field empty or enter `none`.

4. **Verify the Connection**:
   - Click on **Verify**.
   - If successful, you'll see a confirmation.

5. **Save the Configuration**.

6. **Start a New Chat**:
   - In the interface, click on **New Chat**.
   - Select one of your local models.
   - Begin interacting with the model through the web interface.

## Using OpenAI's API with the Interface

### Obtaining an OpenAI API Key

1. **Sign Up or Log In** to [OpenAI](https://platform.openai.com/).
2. **Navigate to the API Keys Section**:
   - Click on your profile icon.
   - Select **View API Keys**.

3. **Create a New API Key**:
   - Click on **Create new secret key**.
   - Name it (e.g., "Workshop").
   - Copy the generated key.

### Configuring the Interface to Use OpenAI Models

1. **In the Web Interface**, go to **Settings** > **Admin** > **Connections**.
2. **Add a New Connection**:
   - Choose **OpenAI** as the provider.
   - **API Base URL**: Leave as default (`https://api.openai.com/v1`).
   - **API Key**: Paste your OpenAI API key.

3. **Verify the Connection**.
4. **Save the Configuration**.
5. **Start a New Chat**:
   - Select an OpenAI model.
   - Interact as you would with ChatGPT.

### Cost Considerations

- **Pay-per-Use**: With OpenAI's API, you're charged based on token usage.
- **Savings**: Depending on your usage, this can be more cost-effective than a monthly subscription.
- **Monitoring Usage**: Keep an eye on your OpenAI dashboard to track usage and costs.

## Exploring Advanced Models

### Understanding Hardware Limitations

- **Larger Models**: Models like Qwen 2.5 Coder 32B Instruct require more RAM (32 GB or more).
- **Performance**: Advanced models offer better performance but need more resources.
- **Compatibility**: Some models perform better on specific hardware (e.g., ARM-based processors).

### Downloading and Using Advanced Models

1. **Search for the Model in LLM Studio**:
   - Go to the **Discover** tab.
   - Search for models like `Qwen 2.5 Coder`.

2. **Select the Appropriate Version**:
   - Look at the available quantization options.
   - Higher quantization (e.g., Q8) reduces RAM usage at the cost of some accuracy.

3. **Download the Model**:
   - Click on the desired model.
   - Click **Download**.

4. **Load and Use the Model**:
   - As before, load the model in the **Chat** tab.
   - Interact with it through LLM Studio or the web interface.

5. **Experiment with Different Quantizations**:
   - Test lower precision versions to fit within your hardware limits.
   - Assess performance and response quality.

## Conclusion

Running large language models locally empowers you with greater control over your data, cost savings, and the flexibility to experiment with different models. While hardware limitations may pose challenges, tools like LLM Studio and Docker make it accessible for many users. Whether you're seeking privacy, customization, or just exploring AI capabilities, this guide provides the steps to get you started.

## Additional Resources

- **LLM Studio Documentation**: [Link to official docs]
- **Docker Documentation**: [https://docs.docker.com/](https://docs.docker.com/)
- **OpenAI API Pricing**: [https://openai.com/pricing](https://openai.com/pricing)
- **Community Forums**: Join AI and ML communities for support and discussions.

---

*Note: This guide is based on a presentation by Marcos Heidemann, highlighting the possibilities and steps to run language models locally. Always ensure you comply with the licensing terms of the models you use.*
