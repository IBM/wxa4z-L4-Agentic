# Additional configuration

After you save and close the **Conversational search** configuration page, a few more configurations are needed to get the best experience from your conversational chat. Details on these settings are available <a href="https://www.ibm.com/docs/en/watsonx/waz/2.0.0?topic=cluster-configuring-your-assistant-use-zassistantdeploy" target="_blank">here</a>.


1. Hover your cursor over the left-side navigation and click **Actions**.
   
    ![](_attachments/add1.png)

2. Click **Set by assistant** under the **All items** menu.
   
    ![](_attachments/add2.png)

3. Select **No matches**. 

    ![](_attachments/add3.png)

4. Under **Conversation steps**, select the first step and do the following:

    **a.** In the **Is taken** drop-down, select **Without conditions**. In the **Clear conditions?** Dialog box, click **Clear conditions**.

    **b.** In the **Assistant says** text box, delete the default text.

    **c.** In the **And then** drop-down, select **Search for the answer**.

    **d.** At the bottom of the page, click **Edit settings**, select the **After generation** tab, and then click the ***End the action after this step*** checkbox.

    **e.** Then click **Apply**.

    ***The configuration of Step 1 should look like the following:***

    ![](_attachments/add4.png)

5. Then click on the 2nd step of the **No matches** action and click on the **Delete** icon to delete the step.
   
    ![](_attachments/add5.png)

6. Save the settings and **close** the window. 
   
    ![](_attachments/add6.png)

7. Then click the **Fallback** action in the **Actions** table.
   
    ![](_attachments/add7.png)

8. Delete **all** of the **Conversation steps** except for the last one (Step 6).
   
    **Note:** You need to select each step individually. Click the **delete** icon and confirm the deletion for the first 5 steps.

    ![](_attachments/add8.png)

9. Verify that the first 5 **Conversation steps** are deleted and then click the **x** to close the **Editor** window.
    
    ![](_attachments/add9.png)

10. Click the **Global settings** icon.
    
    ![](_attachments/add10.png)

11. Click **No matches** under the **Conversation routing** tab.
    
    ![](_attachments/add11.png)

12. Move the slider to **More often**. 
    
    ![](_attachments/add12.png)

13. Then click the **Autocorrection** tab and toggle the feature to the **Off** position.
    
    ![](_attachments/add13.png)

14. Click **Save (a)** and then **Close (b)**. 
    
    ![](_attachments/add14.png)

15. Hover over the left-side navigation and click **Environments**.
    
    ![](_attachments/add15.png)

16. Click **Web chat**. 
    
    ![](_attachments/add16.png)

17. On the **Style** tab, click the **Streaming** toggle to enable streaming.
    
    The streaming setting allows responses to be streamed to the assistant and displayed as they are generated versus waiting until the full response is received and then displayed.

    ![](_attachments/add17.png)

18. Click on the **Home screen** tab. 
    
    Customize the Home screen by setting a custom **Greeting message** and deleting the default **Conversation starters**.

    ![](_attachments/add18.png)

19. Click the **Suggestions** tab and toggle the feature to the **Off** position.
    
    ![](_attachments/add19.png)

20. Finally, click **Save and exit (a)** and then **Close (b)**.
    
    ![](_attachments/add20.png)

21. Lastly, you will add **prompt instructions** to your assistant to configure how the LLM responds to queries. The prompt instructions help LLMs to guide the conversations with clarity and specificity to achieve the end goal of an action. You can provide instructions to customize the output to an expert or a novice, to answer with a more structured output, such as bullets or examples, as applicable.

    Hover over the left-side navigation and click on **Generative AI**.

    ![](_attachments/add21.png)

22. Click **Add instructions**. 
    
    ![](_attachments/add22.png)

23. In the **Add prompt instructions** text box, copy and paste the following example:
    
    ```
    You are a subject matter expert on mainframe systems. Respond to all prompts with truth and accuracy. Provide answers in a bulleted list with headings. Provide examples and commands when requested. DO NOT guess the answer.
    ```

    ![](_attachments/add23.png)

    ***NOTE:** Prompt instructions are highly customizable and should be tested prior to delivering a demo or pilot. The provided prompt instructions above are just one example.*