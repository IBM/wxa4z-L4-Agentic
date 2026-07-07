# Verification and Testing

### Log into watsonx Orchestrate and test zRAG Agent

Once confirmed that the tenant services are deployed and running, navigate to your **watsonx Orchestrate** service UI and find your deployed **zRAG Agent**. 



## zRAG Agent Configuration

### Configuring Websearch

Additionally, **Web Search** can be configured for your zRAG Agent to retrieve up-to-date and relevant information from external sources. It enhances the accuracy, completeness, and usefulness of responses by supplementing internal knowledge with live web results. 

To setup the **Web Search** capability, follow the instructions <a href="https://www.ibm.com/docs/en/watsonx/waz/3.3.0?topic=z-configuring-web-search-zrag-agent" target="_blank">here.</a>

**NOTE:** to set up a free trial and get access to a **SERPER** API key for the purpose of enabling web search, you can follow the steps below:



Step 1 — Open the signup page
Go to:
https://serper.dev/
Click "Get 2,500 free queries" or "sign up"

Step 2 — Create your account
Fill in:
* Name
* Email address
* Password
Then click Create account.
You do not need a credit card for the free tier.

Step 3 — Verify your email
Serper will send a verification email to your inbox.
* Open the email
* Click the verification link
After verification, log in to your dashboard.

Step 4 — Get the free credits
Once your account is active, Serper automatically adds:
* 2,500 free search credits
to your account dashboard.

Step 5 — Access your API key
After logging in:
1. Open the dashboard
2. Look for:
    * API Key
    * or API Keys in the sidebar
3. Copy the generated key
That key is your authentication token for all API requests.

------
    - Testing
        - go into tenant namespace and check all 3 pods are running
        - log into wxo and ensure zrag agent is bootstrapped
        - how to modify zrag web search, etc....
