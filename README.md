# Travel Memory

`.env` file to work with the backend:

```
MONGO_URI='ENTER_YOUR_URL'
PORT=3000
```

Data format to be added: 

```json
{
    "tripName": "Incredible India",
    "startDateOfJourney": "19-03-2022",
    "endDateOfJourney": "27-03-2022",
    "nameOfHotels":"Hotel Namaste, Backpackers Club",
    "placesVisited":"Delhi, Kolkata, Chennai, Mumbai",
    "totalCost": 800000,
    "tripType": "leisure",
    "experience": "Lorem Ipsum, Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum, ",
    "image": "https://t3.ftcdn.net/jpg/03/04/85/26/360_F_304852693_nSOn9KvUgafgvZ6wM0CNaULYUa7xXBkA.jpg",
    "shortDescription":"India is a wonderful country with rich culture and good people.",
    "featured": true
}
```
---------------------------------------------------------------------------------------------------------------------------------

# Travel Memory

## Backend Setup

### MongoDB Configuration

1. Create an account on MongoDB and deploy a cluster. For learning purposes, consider using the M0 free cluster.
   - [MongoDB Cloud](https://account.mongodb.com/account/login?n=%2Fv2%2F6519492b8cbd8711f6f61f10&nextHash=%23clusters)

2. Create user credentials with read and write permissions.

3. Use MongoDB Compass to verify the login credentials.

### Amazon EC2 Instances

1. Create two Amazon EC2 instances with Ubuntu OS and a security group allowing all IPs. One instance will host the front end and the other the back end.

2. Connect to the instance via SSH.

3. Update software and install Git:
   ```bash
   sudo apt update
   sudo apt-get install git -y

4. Clone the repository:
   ```bash
   git clone [repository_url]

5. Install Node.js and npm:
   ```bash
   sudo apt-get update
   sudo apt-get install -y ca-certificates curl gnupg
   sudo mkdir -p /etc/apt/keyrings
   curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
   NODE_MAJOR=18
   echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee 
   /etc/apt/sources.list.d/nodesource.list
   sudo apt-get update
   sudo apt-get install nodejs -y

6. Initialize npm in the backend folder:
   ```bash
   cd Travelmemory/backend
   npm init -y
   npm install

7. Create a .env file in the backend folder and update it with the MongoDB URI:
   ```bash
   nano .env

   Add the following:
   MONGO_URI='mongodb+srv://travelmemory:<password>@travelmemory.9unov3y.mongodb.net/'
   PORT=3000

8. Start the Node.js server:
   ```bash
   node index.js

9. Install and configure Nginx for reverse proxy:
   ```bash
   sudo apt install nginx -y
   sudo systemctl start nginx
   sudo systemctl enable nginx
   cd /etc/nginx/sites-available
   nano default

10. Update the location part in the default file:
    ```bash
    location / {
    proxy_pass http://localhost:3000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    }

11. Restart Nginx:
    ```bash
    sudo systemctl restart nginx

12. Access the public IP of the backend instance. Ensure that the reverse proxy to the Nginx server is functioning.

# Frontend Setup

1. Connect to the frontend EC2 instance via SSH.
2. Update the URL in src/url.js to point to the backend instance's public IP.
3. Initialize npm in the frontend folder:
   ```bash
   cd TravelMemory/frontend
   npm init -y
   npm install

4. Start the frontend server:
   npm start

5. Install and configure Nginx for reverse proxy similar to the backend instance.
6. Access the public IP of the frontend instance. Ensure that the reverse proxy to the Nginx server is functioning.

#   Domain Purchase, DNS Configuration, and CloudFlare Setup

## 1. Domain Purchase:
   * Visit a domain registrar like GoDaddy.
   * Search for your desired domain name and complete the purchase process.
## 2. DNS Configuration at Registrar:
   * Log in to your domain registrar’s dashboard.
   * Navigate to the DNS management section.
   * Add an A record for the frontend server's IP.
   * Add another A record for the backend server's IP with a subdomain (e.g., api).
## 3. Setting up CloudFlare:
   * Register and log in to Cloudflare.
   * Add your domain to CloudFlare and select the free plan.
   * Change your domain’s nameservers to CloudFlare’s nameservers.
   * Add A records for the frontend and backend servers in CloudFlare DNS settings.
## 4. Updating Frontend Application:
  *  Update the frontend/src/url.js file to use the new backend API URL (http://api.[your domain name]).
  *  Restart and Verification:
  *  Restart both frontend and backend applications.
  *  Access your domain via HTTP and verify that the application functions correctly.
    
#  Implementing SSL with Certbot
## 1. Certbot Installation:
   * Ensure Snapd is installed and up to date.
   * Remove any existing Certbot installations.
   * Install Certbot using snap.
## 2. Obtaining SSL Certificate:
   * Run Certbot with the Nginx plugin.
   * Follow the on-screen instructions to select your domain and obtain the certificate.
## 3. Testing and Restarting Nginx:
   * Test the Nginx configuration for syntax errors.
   * Restart Nginx to apply the new configuration.
## 4. Verification:
   * Access your application using https://[your-domain-name] to verify that SSL is working correctly.
## 5. Updating Frontend Configuration:
   * Update the frontend/src/url.js file to use HTTPS for the backend URL.
   * Restart the frontend application to apply the change.
 
   
  
   
   
   
   
 
   
   
