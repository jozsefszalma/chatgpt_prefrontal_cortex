# ChatGPT Prefrontal Cortex
Inspired by [this article](https://www.noemamag.com/ai-chatbots-dont-care-about-your-social-norms/?utm_source=noematwitter&utm_medium=noemasocial) <br>
When I read it, I was thinking 'ok sure, but this sounds like an inhibitory problem' so I set out to give ChatGPT an inner voice to remind it when it is misbehaving.
<br>
This particular implementation will only provide an opportunity for the main model to review its message, based on the feedback from the inhibitor model; this can be of course re-engineered for different outcomes.

<b>work in progress!</b>

### How it works:
<img width="779" alt="pass" src="https://user-images.githubusercontent.com/96535232/225124598-8dbd97fe-0494-4a2d-85de-33fee83b4f60.png">
<img width="779" alt="inhibit" src="https://user-images.githubusercontent.com/96535232/225124715-3cbcc935-cbfd-4a99-9074-389d0ab5533e.PNG">
<img width="779" alt="inhibit" src="https://user-images.githubusercontent.com/96535232/225137989-f340268b-0a52-4e5e-8913-74d981bdb8c0.png">



### Set up: 
env variables (e.g. in a .env file if using vscode) 
- "KEY", for your OpenAI API key 
- "PROMPT_SYSTEM" this is where you set your chatbot's default personality (e.g. helpful expert in area x); there is also where you might want to spell out the role of the inhibitor model, so the main model knows what to do with it
- "PROMPT_INHIBITOR" default instructions to the inhibitor model (i.e. what to look for, formatting the feedback in json etc) <br>
    my code is expecting the responses from the inhibitor in the following format: <br>
        {"decision": "pass", "explanation": ""}<br>
        {"decision": "inhibit", "explanation": ""} <br>
    so, you need to engineer your prompt accordingly. <br>
    Also, you need to educate the inhibitor about your risk appetite, otherwise it might complain about every minor thing. 

### Known issues:
- the UI will only work in Jupyter environments that handle ipywidgets properly (e.g. Databricks' Jupyter does not, vscode is marginal)
- if using vscode keep in mind:
    - enter and shift-enter in the input window are captured by vscode, use the Send button instead
    - in vscode the default key binding to turn a cell into markdown is "m", you need to re-bind that in the settings as vscode captures it during typing
- ChatGPT keeps apologizing after an inhibit decision (e.g. see screenshot above) while it should just rephrase the answer; I'm still working on the proper prompt. 
