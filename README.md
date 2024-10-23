# llmcord.py - forked from [jakobdylanc/llmcord.py](https://github.com/jakobdylanc/llmcord.py)

This is an edited version designed to function as an AI chatbot in the [All Things Linux Discord server](https://discord.gg/linux).

## Installation

Before you begin, ensure you have [Python](https://www.python.org/downloads/) installed and clone this repository.

### Bare metal

1. **Install Python Dependencies:**
   
   ```bash
   pip install -r requirements.txt
   ```

2. **Configure the Bot:**
   
   - Duplicate the `config-example.json` file and rename it to `config.json`.
   - Edit `config.json` with your desired settings.

3. **Run the Bot:**
   
   - **Using Python:**
     
     ```bash
     python llmcord.py
     ```
   

### Using Docker
     
     Ensure you have [Docker](https://www.docker.com/) installed, then run:
     
     ```bash
     docker compose up -d
     ```

## Configuration

Customize your bot by editing the `config.json` file. Below are the configuration settings you can adjust:

### LLM Settings

| **Setting**              | **Description**                                                                                                                                                                                                        |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **providers**            | Specify the LLM providers you want to use. Each provider requires a `base_url` and an optional `api_key`. Common providers like `openai` and `ollama` are pre-included. **Only OpenAI-compatible APIs are supported.** |
| **model**                | Define the model by setting it to `<provider name>/<model name>`. Examples:<br /><br />- `openai/gpt-4o`<br />- `ollama/llama3.2`<br />- `openrouter/anthropic/claude-3.5-sonnet`                                      |
| **extra_api_parameters** | Add any additional API parameters your LLM might require. For example:<br />- `max_tokens=4096`<br />- `temperature=1.0`<br />*Default values are provided, but you can customize as needed.*                          |
| **system_prompt**        | Customize the bot's behavior by writing a system prompt. **Leave blank if you do not wish to use a system prompt.**                                                                                                    |

### Discord Settings

| **Setting**             | **Description**                                                                                                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **bot_token**           | Obtain your Discord bot token by creating a new bot at [Discord Developers](https://discord.com/developers/applications). Generate the token under the "Bot" tab and ensure "MESSAGE CONTENT INTENT" is enabled. |
| **client_id**           | Find your bot's Client ID under the "OAuth2" tab in the Discord Developers portal.                                                                                                                               |
| **status_message**      | Set a custom status message for your bot's Discord profile. **Maximum of 128 characters.**                                                                                                                       |
| **allowed_channel_ids** | List the Discord channel IDs where the bot is permitted to operate. **Leave empty to allow usage in all channels.**                                                                                              |
| **allowed_role_ids**    | Specify Discord role IDs that are allowed to use the bot. **Leaving this empty allows everyone to use the bot. Specifying at least one role also disables direct messages (DMs).**                               |
| **max_text**            | Define the maximum amount of text allowed in a single message, including text from file attachments. **Default:** `100,000` characters.                                                                          |
| **max_images**          | Set the maximum number of image attachments permitted in a single message. **Only applicable when using a vision model.** **Default:** `5` images.                                                               |
| **max_messages**        | Determine the maximum number of messages allowed in a reply chain. **Default:** `25` messages.                                                                                                                   |
| **use_plain_responses** | When set to `true`, the bot will respond with plaintext instead of embeds. This will also disable streamed responses and warning messages. **Default:** `false`                                                  |
