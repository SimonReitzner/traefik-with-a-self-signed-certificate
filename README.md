<div id="top"></div>

<br />
<h2 align="center">Traefik with a Self-Signed Certificate</h2>
<br />
</div>

1. [About the Project](#about-the-project)
2. [Built With](#built-with)
3. [Usage](#usage)
4. [Contact](#contact)
<br />

### About the Project <a id="about-the-project"></a>
This project demonstrates a very simple Traefik setup with a self-signed certificate. In this project, we set up Traefik to route traffic to an HTTPD service, using a self-signed certificate for HTTPS.

### Built With <a id="built-with"></a>
- [Traefik](https://traefik.io): 3.1
- [OpenSSL](https://openssl.org): 3.0.14
- [Docker](https://www.docker.com): 20.10.14
- [Vagrant](https://www.vagrantup.com): 2.4.1
- [Ansible](https://www.ansible.com): 10.2.0
- [VirtualBox](https://www.virtualbox.org): 7.0.6

### Usage <a id="usage"></a>
#### Prerequisites
Install **VirtualBox** and **Vagrant** on your system.

#### Setup Instructions
1. **Clone the Repository**
   ```sh
   git clone https://github.com/SimonReitzner/traefik-self-signed-certificate
   cd traefik-self-signed-certificate
   ```

2. **Set Environment Variables**
   Create a `.env` file in the root directory and set the necessary environment variable for the VM_IP.
   ```sh
   VM_IP=<VM_IP>
   ```

3. **Create Self-Signed Certificates**
   Ensure you have a self-signed certificate in the `certs` directory. If not, generate one using the following commands:
   ```sh
   # Step 1: Create the server private key
   openssl genrsa -out certs/server.key 2048

   # Step 2: Generate the CSR
   openssl req -new -key certs/server.key -out certs/server.csr -config certs/csr.conf

   # Step 3: Create the self-signed certificate
   openssl x509 -req -days 365 -in certs/server.csr -signkey certs/server.key -out certs/server.crt
   ```

4. **Export environment variables**
   ```sh
   export $(cat .env | xargs)
   ```

5. **Start Vagrant**
   ```sh
   vagrant up
   ```

6. **Access the Services**
   - HTTPD Service: `https://<VM_IP>/httpd`

### Contact <a id="contact"></a>
Project Link: [Traefik-with-a-Self-Signed-Certificate](https://github.com/SimonReitzner/traefik-with-self-signed-certificate)

<p align="right">(<a href="#top">back to top</a>)</p>
