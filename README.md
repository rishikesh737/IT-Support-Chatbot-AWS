# AI Chatbot for IT Support 
## ( NOTE : This site will be decommissioned as backend AWS services are removed )
## Overview
This project delivers an AI-powered IT Support Chatbot designed as a first-line assistant for common technical queries. It provides instant, automated solutions and seamlessly escalates complex or unrecognized issues to human agents via email.

## Key Features & Technologies Used

### 1. Bot Development
* **Amazon Lex (V2):** The core conversational engine. The chatbot was built using Lex V2 to understand user intent for common IT issues such as:
    * Password reset
    * Wi-Fi troubleshooting
    * Email access problems
* Intents were trained with various sample utterances to ensure robust Natural Language Understanding (NLU).
* An LLM Gemini 2.0 Flash was also integrated into the fallback Lambda to attempt to answer general troubleshooting queries before escalating to email.

### 2. Backend Response Handling
* **AWS Lambda:** Serverless functions were used to handle bot fulfillment.
    * **FAQ Lookup:** A Lambda function queries a **DynamoDB** table (`ITSupportFAQ`) to retrieve predefined answers for recognized intents.
    * **Fallback & Escalation:** For queries not matched by specific intents or when FAQ answers were unavailable, another Lambda function (acting as a fallback) was invoked. This function sends an email notification to IT support via **Amazon SES**, ensuring human intervention when needed.
    * * LLM Integration: For more advanced fallback, an LLM  was integrated into the fallback Lambda to attempt to answer general troubleshooting queries before escalating to email.

### 3. Frontend Integration
* **AWS S3 & AWS Amplify:** The static web frontend (HTML, CSS, JavaScript) is hosted on an S3 bucket and deployed via AWS Amplify, providing continuous deployment and a public URL.
* **AWS CloudFormation:** The Amazon Lex Web UI was deployed and customized using a CloudFormation template. This pre-built UI was then embedded into our custom frontend as an `<iframe>`, providing a rich, interactive chatbot interface with real-time interaction capabilities.
* **Amazon CloudFront:** Automatically configured by CloudFormation, CloudFront serves the Lex Web UI assets globally for low-latency access.

### 4. Monitoring & Feedback Loop
* **Amazon DynamoDB:** A separate DynamoDB table (`ChatbotLogs`) stores all user queries, bot responses, detected intents, and confidence scores. This data is crucial for monitoring bot performance and identifying areas for future training improvements.

### 5. Security
* **AWS IAM:** Identity and Access Management roles and policies were configured to ensure that Lambda functions had only the necessary permissions to interact with DynamoDB, SES, and Lex.

⚠️ Important Note: Site Decommissioning
Please be aware that this deployed application is for demonstration and portfolio purposes only. The associated AWS backend services are subject to deletion, and therefore, the live site will be decommissioned and may cease to be functional at any time.

### Images

![Image](https://github.com/user-attachments/assets/b99bd9ba-1d65-43d6-ae69-c6043499417b)
![Image](https://github.com/user-attachments/assets/90c64aad-92a3-4841-b448-dd301d528d80)
![Image](https://github.com/user-attachments/assets/ca2d4f50-edec-4a3a-bae3-ae9a3cc9d18e)
![Image](https://github.com/user-attachments/assets/84f310ea-20b6-4974-bc07-e71a45201cb2)
![Image](https://github.com/user-attachments/assets/738476b0-6df8-4ef1-b687-da6a3d06019c)
