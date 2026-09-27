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

# 🔧 Implementation

## 1. Create the Lambda Function

An AWS Lambda function named `FAQ` was created using the **Node.js 22.x** runtime.

The function was configured with the lab-provided execution role and VPC networking settings.

![Create Lambda Function](api-lab-images/01-Create%20Lambda%20function.png)

---

## 2. Add the Lambda Code

The provided JavaScript code was added to the Lambda function.

The code defines a collection of frequently asked questions and answers. The function then selects one FAQ randomly when it is invoked.

The random selection is performed using:

```javascript
var rand = Math.floor(Math.random() * json.questions.length);
```

![Add Lambda Code](api-lab-images/02-Add%20code.png)

---

## 3. Update the General Configuration

The Lambda function description was configured as:

`Provide a random FAQ`

This configuration identifies the purpose of the function.

![Update General Configuration](api-lab-images/03-Update%20general%20configrations.png)

---

## 4. Add an API Gateway Trigger

An **Amazon API Gateway REST API** was added as a trigger for the Lambda function.

The API was configured with:

* **API name:** `FAQ-API`
* **API type:** REST API
* **Deployment stage:** `myDeployment`
* **Security:** Open

This allows requests sent to the API endpoint to invoke the Lambda function.

![Add API Gateway Trigger](api-lab-images/04-Add%20trigger%20API%20gate%20way.png)

---

## 5. Obtain the API Endpoint

After configuring the API Gateway trigger, the generated **API endpoint** was accessed from the Lambda console.

The endpoint can be opened in a web browser to invoke the Lambda function.

![API Endpoint](api-lab-images/05-API%20end%20point.png)

---

# 🧪 Testing

## 6. Test the Lambda Function

The API endpoint was opened in a web browser to test the integration between **API Gateway and Lambda**.

The Lambda function returned a randomly selected FAQ entry in JSON format.

A typical response contains:

```json
{
  "q": "FAQ question",
  "a": "FAQ answer"
}
```

![First Lambda Test](api-lab-images/06-First%20test%20of%20Lambda.png)

---

## 7. Create a Lambda Test Event

The Lambda function was also tested directly from the AWS Lambda console.

A test event named:

`BasicTest`

was created using an empty JSON object:

```json
{}
```

![Save Second Test](api-lab-images/07-Save%20second%20test.png)

---

## 8. Verify Successful Execution

The `BasicTest` event was executed successfully.

The execution result returned the selected FAQ inside the `body` parameter.

![Second Test Successful](api-lab-images/08-Second%20test%20is%20successfully.png)

---

# 📊 CloudWatch Logs

## 9. Review the Lambda Logs

The Lambda execution logs were accessed through **Amazon CloudWatch Logs**.

The log stream provides information about the Lambda execution, including the randomly selected FAQ and the generated response.

Logs can be accessed through:

**Lambda → Monitor → View CloudWatch logs → Log stream**

![View CloudWatch Log Stream](api-lab-images/09-View%20log%20stream.png)

---

# 🎯 Key Learning Outcomes

Through this lab, I practiced:

* Creating and configuring an AWS Lambda function
* Working with the Node.js runtime
* Deploying Lambda code
* Integrating Lambda with Amazon API Gateway
* Creating and testing a REST API endpoint
* Creating custom Lambda test events
* Verifying successful Lambda execution
* Accessing and reviewing CloudWatch Logs
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
