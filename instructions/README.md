# Assignment 2: Prompting via Crowdsourcing Strategies

In this assignment, you will **apply decades of research findings in Crowdsourcing instructions to LLM prompting**. Hopefully the assignment will help you:

- Get familiar with the concept of prompting.
- Get familiar with the OpenAI interface.
- Get familiar with crowdsourcing techniques & limitations.
- Explore the feasibility of using LLMs as crowdworkers -- _If the results are interesting, we might use them to compile a research paper with everyone in the class listed as a coauthor!_

## Assignment overview

**Background**: If you think of each large language model call as a crowdworker completing a small task, then naturally we can ask: can multiple LLM modules collectively solve a larger task, if each of them completes a microtask?
This is the basic idea behind multiple research papers like [AI Chains](https://arxiv.org/pdf/2110.01691.pdf) (CHI 2022), [least-to-most prompting](https://arxiv.org/pdf/2205.10625.pdf) (2022), etc.
**I highly recommend reading the [AI Chains](https://arxiv.org/pdf/2110.01691.pdf) paper, especially the Introduction, Sec 2.3 (gives you an overview of Crowdsouring workflow vs. LLM workflow), and Sec 3.1 (why LLMs can be used in workflows).**

This framing opens up additional possible explorations of LLM usage. Researchers have explored microtasking/building workflow and pipelines for crowdsourcing tasks for decades, and so we can see if their design pipelines can also be applied to LLMs.

In this assignment, you will:

1. read a crowdsourcing paper in detail,
2. replicate its pipeline by writing multiple prompts that would instruct different LLM modules to complete different subtasks,
3. test the pipeline on some tasks and inputs you selected, and
4. write a reflection on why the pipeline worked or did not work.

## Steps for completing the assignment.

### 1. Pick a Crowdsoucring paper to focus on.

Pick from one of the six crowdsourcing papers to read in detail. You will replicate its baseline when you do prompting in the notebook (see next section).

- **Please [use this Google Sheet](https://docs.google.com/spreadsheets/d/1gKnCvzuWH9msP3JsxZPDtLfmExPrHR7mooqI-uqv5Fw/edit?usp=sharing) signup for the paper you are replicating**. Each paper can be signed up by up to four people, first come first serve.
- If none of these six look interesting to you, you can also pick your own paper. In that case, please email Sherry the paper link so I can approve it.

### 2. Set up the environment and code.

1. **Envoirnment setup.** Similar to Assignment 1, setup the virual Python environment so you can use the same version of Python. Here, I show an example of using [Conda](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html#before-you-start) (which I highly recommend):

   ```sh
   # create an environment named eval_env, under the version of python 3.7
   conda create --name prompt_env python=3.7
   # start the environment.
   conda activate prompt_env
   ```

2. **Install necessary packages.** This assignment only requires to install OpenAI API and Jupyter Notebook.

   ```sh
   # You should make sure you are in the environment when installing packages.
   conda activate prompt_env

   pip install openai
   pip install notebook
   ```

3. **Start the programming environment**

   ```sh
   # Make sure you are in the right environment
   conda activate prompt_env
   # clone this git repo.
   git clone $GIT_REPO_URL
   # Make sure you are in the right folder
   cd $PATH_TO_YOUR_LOCAL_REPO
   # start the jupyter notebook
   jupyter notebook
   ```

4. **Setup OpenAI account and get an API key**. You will create a new OpenAI account, and this will give you $18 credit which should be enough for this small exploration study.

   - Go to [OpenAI platform](https://platform.openai.com/overview), create a new account.
   - Log into OpenAI, create your [API Key](https://beta.openai.com/account/api-keys) (In Account -> View API Keys -> create new secret key).
   - create a json file `credential.json` in the repo folder, and put the following information there (for safety, this information will not be uploaded to GitHub):

     ```json
     {
       "openai": "[INPUT YOUR APIKEY HERE]"
     }
     ```

   - Read the [tutorial doc](https://beta.openai.com/docs/introduction), and the [pricing page](https://openai.com/api/pricing/) to get a general sense of GPT-3. **Importantly, you should generate your final model outputs with `text-davinci-003`.**
   - Please keep track of your [granted free credits](https://platform.openai.com/account/usage)! **Unfortunately we won't be able to reimburse any additional costs.**
   - **Tips for saving credits:** (1) You can use a cheaper model for tuning your prompts (see [pricing](https://openai.com/api/pricing/)) before generating the final responses using the most capable model `text-davinci-003`. (2) [AI21](https://www.ai21.com/studio) provides a model similar to GPT-3 / API service similar to OpenAI, and it involves more free credits for you to try. (3) You can also Play with [ChatGPT](https://chat.openai.com/chat) which is a free and similarly capable model.

5. **Start to complete the task in the notebook.** Visit `http://localhost:8888/notebooks/A2-Notebook.ipynb` so you can see your notebook. To help you better understand the steps involved, we provide a [toy example solution](http://localhost:8888/notebooks/A2-Notebook-Sample.ipynb) of this assignment.

## Delivery

1. Make sure you have finished all of the steps in the notebook.
2. Download the notebook as HTML, via File => Download As => HTML in Jupyter Notebook.
3. Rename the downloaded HTML `A2-Notebook.html` to `A2-Notebook-[AndrewID].html` (e.g. `A2-Notebook-janedoe.html`)
4. Go back to Canvas, and submit `A2-Notebook-[AndrewID].html`.

## Grading:

If you find the assignment difficult, there are some ways to earn partial credits, as shown below.

The base grade will be up to 80, based on how you attempted the task:

- **0 point** if no submission.
- **30 points if you only describe your task and strategies without actual prompting**. You will only need to fill in the writeup sessions in the notebook. For the result part, you should write how you _envision_ the model to perform.
- **60 points if you modified the pipeline in the Sample notebook** -- i.e., if you created a different task (that's not metaphor creation, and has different inputs and outptus), and showed that a pipeline similar to the Sample pipeline also works for your new task.
- **70 points if you wrote a pipeline that's applicable to 1 input** (i.e., you made it work for a particular input).
- **80 points if you wrote a pipeline that's applicable to 3 inputs** (i.e., you showed some generalizability).

**The remaining 20 point will be based on peer review results:**:

- Three students will read your notebook and rate your prompting effort on a 1-5 scale. This rating will be about whether you've put in enough effort replicating and improving the selected crowdsourcing pipeline for LLM prompting (and, relatedly, how thoughtful was your writeup), not on the final prompt efficiency.
- Your score depends on the relative ranking of averaged your test score usefulness. you wil get {20, 15, 10, 5} scores if your averaged score is ranked top {25%, 50%, 75%, 100%} percent respectively.

## Questions?

Please post your questions on [Canvas Discussion](https://canvas.cmu.edu/courses/32856/discussion_topics/509909).
