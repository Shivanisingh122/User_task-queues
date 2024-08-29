Node.js API with Rate Limiting and Task Queuing
This project implements a Node.js API that handles tasks with rate limiting and task queuing per user ID. When the rate limit is exceeded, tasks are queued and processed accordingly. Task completions are logged to a file for auditing purposes.

Requirements
Node.js (v14 or later)
Redis (for queue management)
Postman (for testing)
Setup and Installation
1. Configure Redis
Ensure Docker is installed and running on your system. Then, set up Redis using Docker:

Pull the Redis image:
bash
Copy code
docker pull redis
Run a Redis container:
bash
Copy code
docker run --name my-redis -p 6379:6379 -d redis
2. Run the Node.js Application
Navigate to your project directory and start the server:

bash
Copy code
node index.js
3. Test the Application with Postman
1. Open Postman
Launch Postman on your machine.



2. Create a New Request
Click New and select Request.
Name your request (e.g., Submit Task) and save it to a collection.


3. Configure the Request
Set the Method to POST.
Enter the URL: http://localhost:3000/Request.
In the Body tab:
Select raw and choose JSON format.
Enter the following JSON in the body:
json
Copy code
{
  "user_id": "345"
}


4. Test Rate Limiting and Queuing
Send Requests: Use the Send button to submit the request.
Rate Limit Testing: Send multiple requests quickly to simulate exceeding the rate limit.
Check for rate limit error responses (e.g., status code 429).
Verify that tasks are queued and processed according to the limits.
Verify Logs: Check the task_logs.txt file in your project directory.
Confirm that it contains the expected user_id and timestamp for each task completion.


5. (Optional) Use Collection Runner for Bulk Testing
Create a Collection: Save your requests to a collection.
Run the Collection:
Click on the collection name in Postman.
Click Run to open the Collection Runner.
Set the number of iterations or use a data file to simulate multiple user IDs.
Click Run and monitor the results.

License
This project is licensed under the MIT License