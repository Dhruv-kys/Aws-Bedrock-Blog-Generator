📘 Blog Generator using AWS Bedrock + Lambda + S3

    This project shows how to build a 🌐 serverless blog generator using AWS Bedrock, AWS Lambda, S3, and API Gateway.
    It generates a ✍️ blog post on any given topic using a Large Language Model (LLM) from Bedrock, saves it into an 🪣 S3 bucket, and exposes an API tested with Postman.

✨ Workflow:
    1️⃣ User provides a blog topic via API Gateway / Postman
    2️⃣ Lambda calls 🤖 Bedrock LLM with the topic
    3️⃣ Blog of ~200 words is generated 📝
    4️⃣ Blog is saved in S3 with a timestamp ⏰
    5️⃣ Logs can be monitored in 📊 CloudWatch

🛠️ AWS Services Used:
    ⚡ Amazon Bedrock → LLM inference (meta.llama2-13b-chat-v1)
    🖥️ AWS Lambda → Serverless execution
    🪣 Amazon S3 → Storage of generated blogs
    🌐 API Gateway → Expose Lambda as REST API
    📊 CloudWatch → Logs and monitoring
    📬 Postman → API testing

📂 Project Structure:
    📄 lambda_function.py → Lambda handler with Bedrock + S3 integration
    📄 requirements.txt → Python dependencies
    📄 README.md → Documentation

🚀 Setup Instructions:
    1️⃣ Prepare Environment
    ✅ Install dependencies → pip install -r requirements.txt
    ✅ Zip code + dependencies → upload to Lambda

2️⃣ Configure AWS Resources:
    🪣 Create S3 bucket (example: awsbedrock90)
    🖥️ Create Lambda function → upload zip file
    🔑 Attach IAM role → permissions: bedrock:InvokeModel, s3:PutObject, CloudWatch logging
    🌐 Create API Gateway → POST route (example: /generate-blog) → integrate with Lambda

3️⃣ Test with Postman:
    📬 POST request → API Gateway endpoint
    Example JSON body:
    { "blog_topic": "Artificial Intelligence in Healthcare" }

4️⃣ Monitor Logs:
    🔎 Open CloudWatch Logs to see request and response details

📖 Example Flow:
    ➡️ Input: { "blog_topic": "Future of Renewable Energy" }
    ➡️ Lambda calls Bedrock → generates blog
    ➡️ File saved in S3: blog-output/153045.txt
    ➡️ Logs available in CloudWatch

✅ Key Notes:
    🔹 Model used: meta.llama2-13b-chat-v1
    🔹 Blog filenames use current time format HHMMSS.txt
    🔹 Requires Bedrock access enabled in AWS account
    🔹 Update s3_bucket name in code before deployment

🌟 Future Improvements
🔮 Add multiple LLMs (Claude, Llama3, etc.)
🔮 Generate presigned URLs for direct download
🔮 Store metadata in DynamoDB for blog tracking
🔮 Build a frontend UI for easy usage
