# AI Interview Agent Technical Assignment LunarTech

## Architecture

The system operates in this order:

- **User Speaks** 

- **Microphone** 

- **Speech-to-Text (Whisper)** 

- **Text Input** 

- **LLM Core (OpenAI GPT-3.5)** 

- **Text Response** 

- **Text-to-Speech (ElevenLabs)** 

- **Speaker**

- **User Listens**



- **LLM Core**: The `InterviewAgent` class in Python. The class contain these methods: the conversation flow, state, prompt engineering, and summarization.
- **Voice I/O**: `speech_recognition` library captures microphone input, and the `elevenlabs` client provides natural-sounding speech output.
- **Data Logging**: The entire interaction, including a final JSON summary, is saved to a timestamped file in a `logs/` directory. 

## Setup Instructions


You can do these steps if you don't want to use Google Colab and Jupyter Notebook, these steps are for VS Code, Github Condespaces:


### Step 1: Clone the Repository
If this were a Git repo, you'd clone it.

```bash
git clone https://github.com/AslauAlexandru/AI-Interview-Agent-Technical-Assignment-LunarTech
```

### Step 2: Install Dependencies
To create using ```requirements_pip_freeze.txt``` you need to use ```pip freeze > requirements_pip_freeze.txt```. 
Make sure you have Python installed. Then, install the required libraries from `requirements_pip_freeze.txt` .

```bash
pip install -r requirements_pip_freeze.txt
```
**Note for Audio:** The `PyAudio` library may require system-level dependencies.
- On macOS: `brew install portaudio`
- On Debian/Ubuntu: `sudo apt-get install portaudio19-dev python3-pyaudio`

### Step 3: Set Up API Keys
The project uses API keys for OpenAI and ElevenLabs.

1.  Create a file named `.env` in the root of the project directory.
2.  Add your API keys to this file as follows:

    ```env
    OPENAI_API_KEY="sk-YourOpenAIKeyHere"
    ELEVENLABS_API_KEY="YourElevenLabsKeyHere"
    ```

### Step 4: Run the Application
Ensure your microphone is connected and set as the default input device for your system. Then, run the main script:

```bash
python main.py
```

The agent will greet you and begin the interview. After the final question, it will generate and print a summary, and save a detailed log file in a newly created `logs/` directory.

## Known Limitations & Next Steps

- **Linear Conversation**: The agent strictly follows its script of 5 questions. It can handle basic FAQs but cannot deviate into complex, open-ended conversation.
- **Basic Error Handling**: If the STT service fails to understand the user, it will simply ask them to repeat. More robust error handling could be implemented.
- **Noisy Environments**: STT accuracy will degrade significantly in noisy environments.

**Future Improvements:**
- **Advanced State Management**: Implement a more complex state machine to allow for a more dynamic conversation.
- **Database Integration**: Store interview logs in a SQLite or PostgreSQL database for easier querying and analysis.
- **Calendly API**: Integrate a scheduler to book a follow-up interview with a human reviewer directly from the conversation.







