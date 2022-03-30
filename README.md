# Setup Instructions

**Note:** *The instructions below are intended to be run on the Mac you will be using as the media player. Be sure to follow the commands exactly as steps 3 and beyond assume you are in the proper directory (from step 2)*

 1. Clone/download this repository and launch Terminal
 2. Navigate to the repository: `cd ~/Downloads/itunes-api/`
 3. Run the bootstrap command: `script/bootstrap`
 4. Replace the local-itunes agent file: `mv config/agent.js node_modules/local-itunes/libs/utils/`
 5. Install itunes-api to run as a service: `script/install` 
     *You may optionally run the server in development mode: `script/server`*
