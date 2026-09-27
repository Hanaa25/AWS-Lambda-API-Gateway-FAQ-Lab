# AWS Lambda & API Gateway FAQ Lab

**Keywords:** `AWS Lambda` • `API Gateway` • `CloudWatch` • `Node.js` • `REST API`

## 📌 Project Overview

This hands-on AWS lab demonstrates how to create a serverless FAQ application using **AWS Lambda** and **Amazon API Gateway**.

The Lambda function contains a collection of frequently asked questions and returns a randomly selected FAQ. Amazon API Gateway provides a REST API endpoint that invokes the Lambda function, while Amazon CloudWatch Logs is used to review the function execution and logging information.

The lab also includes testing the Lambda function directly from the AWS Lambda console using a custom test event.

---

## 🏗️ Architecture

```text
User / Browser
      │
      ▼
Amazon API Gateway
     REST API
      │
      ▼
AWS Lambda
   FAQ Function
      │
      ├── Select random FAQ
      │
      └── Return JSON response
      │
      ▼
User / Browser

AWS Lambda
      │
      ▼
Amazon CloudWatch Logs
```

---

## ☁️ AWS Services Used

| AWS Service            | Purpose                                                    |
| ---------------------- | ---------------------------------------------------------- |
| **AWS Lambda**         | Executes the FAQ application code without managing servers |
| **Amazon API Gateway** | Provides a REST API endpoint to invoke the Lambda function |
| **Amazon CloudWatch**  | Stores and displays Lambda execution logs                  |
| **Amazon VPC**         | Provides the networking environment required by the lab    |

---

## ⚙️ Lambda Function

The Lambda function was created with:

* **Function name:** `FAQ`
* **Runtime:** `Node.js 22.x`
* **Execution role:** `lambda-basic-execution`
* **VPC:** `10.0.0.0/16`
* **Subnets:** `10.0.1.0/24` and `10.0.2.0/24`
* **Security group:** `LambdaSecurityGroup`

The provided JavaScript code defines a list of FAQ questions and answers.

The function generates a random index and selects one FAQ:

```javascript
var rand = Math.floor(Math.random() * json.questions.length);
```

The selected FAQ is then returned as a JSON response.

---

## 🔗 API Gateway Configuration

An **API Gateway REST API** was configured as a trigger for the Lambda function.

Configuration used in the lab:

* **API type:** REST API
* **API name:** `FAQ-API`
* **Deployment stage:** `myDeployment`
* **Security:** Open
* **Integration:** AWS Lambda

The API endpoint can be accessed from a web browser to invoke the Lambda function and retrieve a random FAQ.

---

## 🧪 Testing

### 1. API Gateway Test

The API Gateway endpoint was opened in a web browser.

A random FAQ was returned in JSON format:

```json
{
  "q": "FAQ question",
  "a": "FAQ answer"
}
```

Different FAQ entries can be returned because the Lambda function selects an item randomly from the FAQ list.

### 2. Lambda Console Test

The function was also tested directly from the AWS Lambda console.

A test event named:

```text
BasicTest
```

was created with an empty JSON object:

```json
{}
```

The execution completed successfully, and the returned FAQ appeared inside the `body` parameter.

---

## 📊 CloudWatch Logs

The Lambda execution logs were reviewed through Amazon CloudWatch.

The function logs information about the selected FAQ and the generated response.

The logs were accessed through:

**Lambda → Monitor → View CloudWatch logs → Log stream**

Reviewing the log stream provides visibility into the Lambda execution and helps verify the function's behavior.

---

## 📸 Screenshots

The `api-lab-images` folder contains the screenshots captured during the lab.

### 01 — Create Lambda Function

![Create Lambda Function](api-lab-images/01-Create%20Lambda%20function.png)

### 02 — Add Code

![Add Code](api-lab-images/02-Add%20code.png)

### 03 — Update General Configuration

![Update General Configuration](api-lab-images/03-Update%20general%20configrations.png)

### 04 — Add API Gateway Trigger

![Add API Gateway Trigger](api-lab-images/04-Add%20trigger%20API%20gate%20way.png)

### 05 — API Endpoint

![API Endpoint](api-lab-images/05-API%20end%20point.png)

### 06 — First Lambda Test

![First Lambda Test](api-lab-images/06-First%20test%20of%20Lambda.png)

### 07 — Save Second Test

![Save Second Test](api-lab-images/07-Save%20second%20test.png)

### 08 — Second Test Successful

![Second Test Successful](api-lab-images/08-Second%20test%20is%20successfully.png)

### 09 — CloudWatch Log Stream

![CloudWatch Log Stream](api-lab-images/09-View%20log%20stream.png)

---

## 🎯 Key Learning Outcomes

Through this lab, I practiced:

* Creating and configuring an AWS Lambda function
* Working with the Node.js runtime
* Deploying Lambda code
* Integrating Lambda with Amazon API Gateway
* Creating and testing a REST API endpoint
* Testing Lambda functions using custom test events
* Reviewing Lambda execution results
* Accessing and examining CloudWatch Logs
* Understanding a basic serverless, event-driven architecture

---

## 🛠️ Technologies

* AWS Lambda
* Amazon API Gateway
* Amazon CloudWatch
* Amazon VPC
* Node.js
* JavaScript
* REST API
* JSON

---

## 📚 Lab Reference

**Introduction to Amazon API Gateway**
**SPL-58 — Version 2.0.38**

This repository documents practical hands-on work completed in an AWS training lab and is maintained as a personal learning and portfolio project.
