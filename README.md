# ChatGPT Prefrontal Cortex
Inspired by [this article](https://www.noemamag.com/ai-chatbots-dont-care-about-your-social-norms/?utm_source=noematwitter&utm_medium=noemasocial) <br>
When I read it, I was thinking 'ok sure, but this sounds like an inhibitory problem' so I set out to give ChatGPT an inner voice to remind it when it is misbehaving.
<br>
This particular implementation will only provide an opportunity for the main model to review its message, based on the feedback from the inhibitor model; this can be of course re-engineered for different outcomes.

<b>work in progress!</b>

### set up 
env variables (e.g. in a .env file if using vscode) 
- "KEY", for your OpenAI API key 
- "PROMPT_SYSTEM" (optionally) if you want to give your chatbot a default personality (e.g. helpful expert in area x)
- "PROMPT_INHIBITOR" default instructions to the inhibitor model (i.e. what to look for, formatting the feedback in json etc) <br>
    my code is expecting the responses from the inhibitor in the following format: <br>
        {"decision": "pass", "explanation": ""}<br>
        {"decision": "inhibit", "explanation": ""} <br>
    so, you need to engineer your prompt accordingly. <br>
    Also, you need to educate the inhibitor about your risk appetite, otherwise it might complain about every minor thing. 

### known issues:
- the UI will only work in Jupyter environments that handle ipywidgets properly (e.g. Databricks' Jupyter does not, vscode is marginal)
- if using vscode keep in mind:
    - enter and shift-enter in the input window are captured by vscode, use the Send button instead
    - in vscode the default key binding to turn a cell into markdown is "m", you need to re-bind that in the settings as vscode captures it during typing
