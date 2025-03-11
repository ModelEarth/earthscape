# Launch EarthScape

If you've already installed locally, 
you'll have "chatbotui" in your Docker container.
Simply run in your Earthscape folder to launch. (Step 11)

	npm run chat

You may need to rerun `npm ci` to install recent syncs.
You'll probably create a new account each time. Can we reload an existing Supabase?

[Earthscape](https://model.earth/earthscape/) is a fork of [Chatbot UI](https://github.com/mckaywrigley/chatbot-ui) by [Nick Wrigley](https://twitter.com/mckaywrigley).  
Install documented by our [Model.earth Team](/projects)

---

<h1 style="font-size:24px;">Quick Install</h1>

Steps based on [github.com/mckaywrigley/chatbot-ui](https://github.com/mckaywrigley/chatbot-ui)

1.) Fork and clone the [Earthscape fork](https://github.com/modelearth/earthscape/) to your local desktop.

2.) Confirm your python and conda versions are current.

	python -V && conda -V

If older than python 3.12 and conda 23.3, [see our upgrade notes](https://model.earth/io/coders/python/).

3.) You can create a virtual environment using conda to avoid dependencies/version issues on your computer.

By using conda, no extra env files will reside in your repo. Type "y" when prompted.

	conda create --name myenv &&
	conda activate myenv && conda -V

Or you can reuse the existing .gitignore: .env\*.local by adding X:

	python3 -m venv .envX.local &&
	source .envX.local/bin/activate

4.) In the local repo run `npm ci` as an alternative to `npm install` to avoid updating the package-lock.json file.

	npm ci

5.) Start Docker on your computer. You should see a whale icon at the top.  
Click the whale icon. A green dot confirms Docker is running.

If you don't have Docker on your computer yet, [Install Docker](https://docs.docker.com/get-docker/).

<!--
After docker factory reinstall, this example is provided:

docker run -d -p 80:80 docker/getting-started
-->

<!--
This was not in the chatbot-ui setup steps:
It was an idea suggested by team, but reinstalling Docker fixed issue. Also did a docker factory reset first.

	docker pull supabase/postgres
-->

6.) Install Supabase CLI

	brew install supabase/tap/supabase

For Windows [see detailed steps](../)

<!--
Start postgres

	brew services start postgresql@14
-->
7.) Start supabase - Uses Docker (Might not need to re-run each time.)

	supabase start

Takes about 10 minutes as Docker pulls images and creates the containers.  
When step #7 completes, your secrets for #10 will be in the cmd window.

8.) Copy .env.local.example to .env.local so you can add API values.  
-n is short for --no-clobber and prevents overwriting.

	cp -n .env.local.example .env.local

9.) Run this to get the API secrets URLs for step 10.  
(`supabase start` above also provides your API secrets.)

	supabase status

10.) Open the blank .env.local file you created in step #8.  
(It might be a hidden file.)

Fill in the the configuration information obtained:
For NEXT_PUBLIC_SUPABASE_URL use API URL

NEXT\_PUBLIC\_SUPABASE\_URL  
NEXT\_PUBLIC\_SUPABASE\_ANON\_KEY  
SUPABASE\_SERVICE\_ROLE_KEY


11.) Run

	npm run chat

12.) Add some global API Keys to .env.local

You can optionally [install Ollama](https://github.com/ollama/ollama#macos) for local models.

NOTE:
The hosted site at [chatbotui.com](https://www.chatbotui.com) seems to require a ChatGPT key.


## Run update

When you return to edit, update your local files:

	npm run update

<!-- WE ARE LOCAL, not needed
If you run a hosted instance you'll also need to run: 
TO DO: Add link on "hosted instance" to provide clarity.

	npm run db-push

conda env create -f environment.yml
-->


<!--
## Current Errors

Errors are occurring because Docker was not yet configured.
TO DO: Please add Docker setup info above.

npm run update
failed to connect to postgres: failed to connect to host=127.0.0.1 user=postgres database=postgres: dial error (dial tcp 127.0.0.1:54322: connect: connection refused)

supabase start
failed to start docker container: Error response from daemon: Mounts denied: approving /Users/helix/Library/Data/earthscape/supabase/functions: file does not exist

supabase status
Error response from daemon: No such container: supabase_db_chatbotui
-->

## Run NextJS using Github Pages

Next, we'll add [steps for deploying NextJS to Github](https://www.freecodecamp.org/news/how-to-deploy-next-js-app-to-github-pages/) without Vercel.

We will also document how to sync from Github to a site hosted with our [Cloudflare&nbsp;Setup](https://model.earth/localsite/start/cloudflare/).

NextJS provides an api layer powered by Express that allows you to build an Express app inside of your NextJS app. You can simply delete the API folder from the pages folder and no backend code will be present. [YouTube](https://youtu.be/PN1HgvAOmi8) video about rendering patterns.

<!--
## The Free Energy Principle

The free energy principle is a theoretical framework suggesting that the brain reduces surprise or uncertainty by making predictions based on internal models and updating them using sensory input. It highlights the brain's objective of aligning its internal model with the external world to enhance prediction accuracy.

#### Natural Intelligence vs Artificial Intelligence

[Verses AI - Genius Beta Signup](https://www.verses.ai/genius)
Unlike AI trained on enormous datasets to excel at pattern recognition and reconstruction, Verses AI "Genius" utilizes nature-inspired biological processes to generate agents and collaborate to exhibit the dynamic behaviors of autonomous intelligent systems. This enables Verses to manage uncertainty and risk as it strives to create safe and sustainable environments at&nbsp;scale.
-->