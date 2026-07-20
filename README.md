# 🚀 WishFlow AI

WishFlow AI is an automated, AI-powered WhatsApp greeting scheduler. Built with Flask and SQLite, this application allows users to generate personalized messages using the Groq API (Llama 3.1) and schedule them for automatic delivery via WhatsApp Web.

## ✨ Features

*   **🔐 Secure User Authentication:** Registration and login system with hashed passwords using `werkzeug.security`.
*   **🤖 AI Message Generation:** Integrated with the Groq API to instantly generate contextual wishes based on relation, occasion, and desired tone (e.g., Funny, Professional, Romantic).
*   **📅 Automated Scheduling:** Users can specify an exact date and time for message delivery.
*   **✉️ WhatsApp Automation:** A dedicated background script (`scheduler.py`) utilizes `pywhatkit` and `pyautogui` to automatically open WhatsApp Web and dispatch pending messages at their scheduled times.
*   **📊 Dashboard Management:** A sleek, dark-themed UI to view upcoming scheduled wishes and track the total number of sent messages.

## 🛠️ Tech Stack

*   **Backend:** Python 3, Flask
*   **Database:** SQLite (`wishbot.db`)
*   **AI Integration:** Groq API (`llama-3.1-8b-instant`)
*   **Automation:** `pywhatkit`, `pyautogui`
*   **Frontend:** HTML5, CSS3 (Custom Dark Theme)
*   **Security:** `werkzeug.security`, `dotenv` (for API key management)

## ⚙️ Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/wishflow-ai.git](https://github.com/yourusername/wishflow-ai.git)
    cd wishflow-ai
    ```

2.  **Install dependencies:**
    Ensure you have Python installed, then install the required packages.
    ```bash
    pip install Flask groq pywhatkit pyautogui python-dotenv werkzeug
    ```

3.  **Environment Variables:**
    Create a `.env` file in the root directory and add your Groq API keys (comma-separated for smart key rotation).
    ```env
    GROQ_API_KEYS=your_groq_api_key_1,your_groq_api_key_2
    ```

4.  **Run the Web Server:**
    Start the Flask application. This will also automatically initialize the SQLite database if it doesn't exist.
    ```bash
    python app.py
    ```

5.  **Run the Automation Scheduler:**
    *Important: Ensure you are logged into WhatsApp Web in your default browser before running this script.*
    Open a new terminal window and start the scheduler:
    ```bash
    python scheduler.py
    ```

## ⚠️ Important Automation Notes

The `scheduler.py` script relies on `pywhatkit` and `pyautogui` to physically control your mouse and keyboard to send the message. 
*   Your computer must be awake and unlocked at the time of scheduled delivery.
*   Do not interact with the mouse or keyboard while the script is actively sending a message, as it may interrupt the `pyautogui` keystrokes.
