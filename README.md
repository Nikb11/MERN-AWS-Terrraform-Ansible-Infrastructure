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
