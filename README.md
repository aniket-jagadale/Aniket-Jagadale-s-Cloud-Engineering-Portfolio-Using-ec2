# Aniket Jagadale's Cloud Engineering Portfolio

This repository contains my personal portfolio website, showcasing my skills as a Cloud Engineering Specialist. This is my first simple project deployed on an AWS EC2 instance.

## Live Demo

You can view my live portfolio at: [aniketjagadale.com](http://aniketjagadale.com/)

## Project Goal

The main goal of this project was to successfully deploy a static HTML website on an AWS EC2 instance, make it accessible via a custom domain, and manage the web server (Nginx).

## Technologies Used

*   **HTML5 & CSS3:** For the website structure and styling.
*   **AWS EC2:** Cloud computing service to host the website.
*   **Nginx:** A high-performance web server used to serve the HTML content.
*   **GoDaddy:** For domain name registration and DNS management.

## Deployment Steps on AWS EC2

This section outlines the simplified steps I followed to deploy this portfolio on an AWS EC2 instance using Nginx and link it to my domain.

**Assumptions:**
*   You have an AWS EC2 instance already launched and running (e.g., Amazon Linux 2 or Ubuntu).
*   You have an SSH key to connect to your instance.
*   Your EC2 Security Group allows HTTP (port 80) traffic.

1.  **Connect to your EC2 Instance via SSH:**
    ```bash
    ssh -i /path/to/your-key.pem ec2-user@YOUR_EC2_PUBLIC_IP
    # (Replace 'ec2-user' with 'ubuntu' if using Ubuntu AMI)
    ```

2.  **Update System Packages and Install Nginx:**
    *   **For Amazon Linux 2:**
        ```bash
        sudo yum update -y
        sudo yum install nginx -y
        ```
    *   **For Ubuntu:**
        ```bash
        sudo apt update -y
        sudo apt install nginx -y
        ```

3.  **Start and Enable Nginx:**
    ```bash
    sudo systemctl start nginx      # Start the Nginx service
    sudo systemctl enable nginx     # Enable Nginx to start on boot
    ```

4.  **Stop Apache (if installed and running):**
    If Apache is running, it will conflict with Nginx on port 80.
    *   **For Amazon Linux 2 (if `httpd` is present):**
        ```bash
        sudo systemctl stop httpd
        sudo systemctl disable httpd
        ```
    *   **For Ubuntu (if `apache2` is present):**
        ```bash
        sudo systemctl stop apache2
        sudo systemctl disable apache2
        ```

5.  **Navigate to Nginx Web Root and Deploy `index.html`:**
    *   The default Nginx web root is usually `/usr/share/nginx/html/` (Amazon Linux) or `/var/www/html/` (Ubuntu).
    *   First, remove the default Nginx index file:
        ```bash
        sudo rm /usr/share/nginx/html/index.html # Or /var/www/html/index.nginx-debian.html for Ubuntu
        ```
    *   Then, transfer your `index.html` file to this directory. You can use `scp` from your local machine:
        ```bash
        # From your LOCAL machine:
        scp -i /path/to/your-key.pem index.html ec2-user@YOUR_EC2_PUBLIC_IP:/usr/share/nginx/html/
        # (Adjust path to /var/www/html/ for Ubuntu if needed)
        ```
    *   Ensure the file has correct permissions:
        ```bash
        sudo chmod 644 /usr/share/nginx/html/index.html
        ```

6.  **Verify Nginx Configuration (Optional but Recommended):**
    ```bash
    sudo nginx -t
    ```
    This command checks for syntax errors in your Nginx configuration.

7.  **Restart Nginx to Apply Changes:**
    ```bash
    sudo systemctl restart nginx
    ```

8.  **Configure DNS with GoDaddy:**
    *   Log in to your GoDaddy account.
    *   Go to your domain's DNS management (`aniketjagadale.com`).
    *   Add or update an `A` record pointing your domain (`@` for the root, or `www`) to your EC2 Instance's Public IPv4 Address.

## Final Success!
![](/success_image.png)


After following these steps, my portfolio website was live and accessible via my custom domain: aniketjagadale.com!