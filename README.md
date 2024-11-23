# AWS SAM "Hello, World!" Example

Let's create a simple "Hello, World!" example using AWS SAM. This example will deploy a Lambda function that returns "Hello, World!" when invoked. Follow these steps:

## 1. Install AWS SAM CLI
If you don’t have the AWS SAM CLI installed, follow the [installation guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html) for your operating system.

Verify installation:

```bash
sam --version
```

## 2. Set Up Your Project
1. **Initialize the project:**

   Run the following command and choose the "Hello World Example":
   
   ```bash
   sam init
   ```
   - Runtime: Choose your preferred language (e.g., Python, Node.js).
   - Template: Select "AWS Quick Start Templates."
   - Name your project (e.g., `hello-world`).

   This creates a directory structure with some boilerplate code.

## 3. Understand the Files
Navigate to your project directory:

```bash
cd hello-world
```

Key files include:
- **template.yaml**: The SAM template that defines your infrastructure.
- **hello_world/**: Contains the Lambda function code (e.g., `app.py` for Python).

## 4. Modify the Function Code
Edit the function in `hello_world/app.py` (or equivalent for your chosen runtime). For Python, it will look like this:

```python
def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": "Hello, World!"
    }
```

## 5. Validate the Template
Validate your `template.yaml` file:

```bash
sam validate
```

## 6. Build Your Project
Prepare the project for deployment:

```bash
sam build
```

## 7. Test Locally
Run the Lambda function locally to test it:

```bash
sam local invoke HelloWorldFunction
```

You should see:

```json
{"statusCode": 200, "body": "Hello, World!"}
```

## 8. Deploy to AWS
1. **Package and deploy:**
   
   ```bash
   sam deploy --guided
   ```
   - Follow the prompts to specify stack name, region, etc.
   - AWS SAM will deploy the Lambda function and create the necessary resources.

2. **After deployment**, SAM will provide an API Gateway URL. For example:

   ```
   https://abc123.execute-api.region.amazonaws.com/Prod/hello/
   ```

## 9. Test Your Deployment
Use a browser or a tool like `curl` to test:

```bash
curl https://abc123.execute-api.region.amazonaws.com/Prod/hello/
```

You should get:

```
Hello, World!
```

## 10. Clean Up
To remove resources:

```bash
sam delete
```

---

This is a simple way to get started with AWS SAM. Let me know if you need help setting up or extending this!
