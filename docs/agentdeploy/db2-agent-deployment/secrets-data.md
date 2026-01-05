# Configuring the `secrets.data` variables

Scrolling down further in the **Db2 for z/OS** section of your `values.yaml` file, you will see a **`secrets.data`** section with additional variables you must configure. It will look like what’s shown below:

```
secrets:
  data:
    ENCRYPT_KEY: ""
    AGENT_AUTH_TOKEN: ""
```

### Setting the `ENCRYPT_KEY` variable

The `ENCRYPT_KEY` variable is used to store confidential information in the provided mongodb metadata store. Follow the <a href="https://github.com/IBM/z-ai-agents/tree/main/agent-helm-charts/db2z-agent#generating-an-encrypt-key-with-python" target="_blank">steps documented here</a> to generate your encrypt key.

The output of running the referenced command lines may look similar to what's shown below:
```
>>> from cryptography.fernet import Fernet
Fernet.generate_key()>>> Fernet.generate_key()
b'H4PKYAmr1OeUGi2hdrZddxb78QvjcgKi4yOYHjaIA0E='
```

Copy and paste the string within the single-quotes and set it to the `ENCRYPT_KEY` variable. In the above example, the string would be `H4PKYAmr1OeUGi2hdrZddxb78QvjcgKi4yOYHjaIA0E=`.

### Setting the `AGENT_AUTH_TOKEN` variable

Lastly, set the `AGENT_AUTH_TOKEN` variable to `DB2_AGENT_TOKEN` or something similar. This is the token used by the agent-controller to register this agent with WxO. 

