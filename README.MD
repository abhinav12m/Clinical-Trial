# Reddit Sentiment Analysis on Clinical Trials

This Python script analyzes the sentiment of comments on Reddit posts related to clinical trials across various subreddits. It uses the PRAW library to interact with the Reddit API, the VADER library for sentiment analysis, and the OpenAI GPT-3.5 language model to generate responses based on the sentiment.

## Setup Instructions

1. Install the required Python libraries:
   ```
   pip install praw
   pip install openai
   pip install nltk
   ```

2. Set up your Reddit API credentials and OpenAI API credentials in the script or as environment variables.

3. Install the VADER lexicon for sentiment analysis:
   ```python
   import nltk
   nltk.download('vader_lexicon')
   ```

4. Run the script.

## Methodology and Challenges

The script follows these steps:

1. Create a PRAW instance with Reddit API credentials.
2. Set the OpenAI API key.
3. Define a list of subreddit names to search for posts related to clinical trials.
4. Initialize the VADER SentimentIntensityAnalyzer for sentiment analysis.
5. Define a function to generate responses using the OpenAI GPT-3.5 language model.
6. Create a dictionary to store sentiment counts.
7. For each subreddit:
   - Get the posts related to "clinical trial".
   - For each post:
     - Print the post title.
     - Get the comments from the post.
     - For each comment:
       - Perform sentiment analysis using VADER.
       - Categorize the sentiment based on the compound score.
       - If the sentiment is neutral or negative, generate a response from OpenAI encouraging the benefits of clinical trials.
       - Update the sentiment counts.
8. Print the final sentiment counts.

Challenges faced:

- Handling rate limiting and exceptions when interacting with the Reddit API and OpenAI API.
- Finding specific subreddits related to health conditions relevant to the clinical trial.
- Limiting number of posts and comments for relevancy.
- Ensuring the script runs efficiently and does not overload the APIs.
- Interpreting the sentiment of comments, as sentiment analysis is a complex task.
- Generating relevant and helpful responses from the language model due to exhaustion of my current quota.

# Examples

Here are some examples of data collected, analysis performed, and messages generated:

```
Scraping posts from r/clinicalresearch:

Post Title: I'm considering taking part in a Phase 1 clinical trial, how risky is it?

Post Comments:

Comment: Been seeing more and more of these posts lately, is it because of that one TikTok video with the guy showing off how much he made participating in clinical trials?…

As mentioned, Phase 1 trials are very focused on safety which does usually mean a lot of PK and ADA samples (EX: blood draws pre-dose, post-dose, 1 hour post-dose, 8 hour post-dose, etc.), ECGs, etc. You’ll be poked and prodded a lot but the whole basis of the trial is that they believe it to be safe. You are essentially a guinea pig, but it’s not like they’re just guessing here. You’ll likely be asked to complete some sort of follow-up, but it could just be a few quick phone calls to confirm if you’re still feeling alright. 

No one here or at the study site can guarantee you won’t experience any adverse events (side effects), but there is a reason they’re doing this in a hospital setting. You’ll have essentially around the clock observation. Read the informed consent thoroughly and ASK QUESTIONS, that’s what the study team is there for - they should be able to address any concerns before, during and after.
Sentiment Compound Score: 0.7362
Sentiment: Very happy and will try again
------------------------------------------------------------

Comment: Phase 1 is all about safety, so keep that in mind. They’ve established a good proof of concept with animal models, but it’s never been in humans. So, they THINK it’s safe, but the purpose of the trial is to prove it.
Sentiment Compound Score: 0.7717
Sentiment: Very happy and will try again
------------------------------------------------------------

Comment: I would definitely ask to the consent form to read in advance (typically they’ll be able to email it to you). Not liking blood draws is kinda a deal-breaker for many- there are some where you’ll have your blood drawn 10x or more. If you didn’t mind having your blood drawn, participating in a Phase 1 study would be a lot more approachable, but it might be one of the most important parts of the study. If getting your blood drawn is stressful to you, I could definitely see skipping Phase I trials.

More about the study:
- You’ll check in for the designated time- you won’t get to come/go as you please
- You might be asked to eat a standardized meal or pick from a standard menu at certain times
- when it is time to get your blood drawn, you’ll get your blood drawn. This could mean a nurse waking you up at 2am and 6am to poke you.
- Typically, you’ll be around other people 
- you have a right to leave/change your mind at any time
- every phase 1 trial is different so one person’s experience may not apply to you. There will be experienced participants there that will tell you stories about what’s typical, but don’t count on one trial being exactly like another
Sentiment Compound Score: 0.8823
Sentiment: Very happy and will try again
------------------------------------------------------------

Scraping posts from r/auckland:

Post Title: Clinic trials

Post Comments:

Comment: I did one for 6k, 3 night stay then 2 weeks of follow up. I was unemployed at the time so it was worth it. They will take a lot of blood samples from you so prepare for that.

Read up for what they are testing you for, the one I did was for a patent of a medication that was about to expire, so they were testing for issues on something that is already in the mass market. I was happy to accept that risk.

The follow up sessions are the worst especially if you have other commitments. So take account of that before you commit. They will deduct money from you if you miss it.
Sentiment Compound Score: 0.5209
Sentiment: Happy with the results
------------------------------------------------------------

Comment: I've done a few... Just because I'm curious how things are done research wise and because I'm fascinated with medical stuff.

That particular study is not a first time gig.... Do a short one 3 or 4 nights with no more than 10 follow ups... That one is HARDCORE... They make you eat 3 meals plus 1 or 2 snacks a day it's super strict and you HAVE to eat every mouthful within a set time.... guys usually moan THE WHOLE FUCKING TIME how hungry they are... Meanwhile I'm so full I'm half way to a food coma, but I'm craving vegetables and spicy food by day 3... So it's really variable experience.

Keep in mind if you can't entertain yourself for days at a time while being very sedentary this is also not for you. You are very much confined to a bed and a social room. They provide decent internet and on a 15 day study they might take you outside once or twice usually to the rooftop or a supervised short walk around the block. 

Medically these are stage 3 healthy volunteer trials so fairly safe... That said I did have an adverse reaction to one of the drugs and because you are so closely monitored the whole time they picked it up before I even felt anything and I had to stay an extra 2 nights and had extra follow ups and everything is back to normal. I was paid a little extra for the inconvenience and the rest of the trial was called off and everyone else sent home early with half the pay. So keep that in mind especially if it's a multiple dose study.... And especially with loads of followups. 

Feel free to pm me for any questions you might have.
Sentiment Compound Score: -0.024
Sentiment: Neutral
------------------------------------------------------------
```

**As I have exceeded my current credits, I have generated OpenAI response independently**

Here is the generated response:

```
OpenAI Response for Neutral Sentiment: Dear Reader,

Participating in clinical trials can offer access to cutting-edge treatments, expert medical care, and the opportunity to contribute to medical advancements. By joining a trial, you may receive early access to potentially life-saving therapies and help shape the future of healthcare. Your participation can make a real difference, both for yourself and for others facing similar health challenges.

Best regards, 
Your AI Assistant
------------------------------

OpenAI Response for Not Happy or Reluctant Sentiment: I understand your concerns about past experiences with clinical trials, but I encourage you to reconsider. Clinical trials offer the opportunity to access cutting-edge treatments, contribute to medical advancements, and receive top-notch care from experts. Your participation could make a difference not only for yourself but for others as well. Take a step towards better health and well-being by exploring the benefits of clinical trials.
------------------------------

```

## My Approach to this Project

1. Finding specifics subreddit related to health conditions relevant with Clinical Trials.
2. Using ideal reddit scraping library(PRAW)
3. Noting down subreddits.
4. Implementing script to search for "Clinical Trials" in each subreddits.
5. Printing posts and comments in each subreddits.
6. Using NLTK sentiment analyser for Sentiment Analysis
7. Writing prompts for "Neutral" and "Negative" Sentiments as they can be persuaded better with personalized OpenAI generated message.

**Compound Sentiment**
To calculate the sentimental score of the entire text, Vader scans the text for known sentimental features, modified the intensity and polarity according to the rules, summed up the scores of features found within the text and normalized the final score to (-1, 1) using function:

![alt text](https://miro.medium.com/v2/resize%3Afit%3A360/format%3Awebp/1%2AlNPhwiUsEJktBXJ8111Fdg.png)

In Vader, alpha is set to be 15 which approximates the maximum expected value of x.

## Requirements and Edits suggestion

- Reddit API credentials (feel free to use one provided in the code)
- OpenAi API credentials
- You can change the number of posts and comments to be shown.
- Play with subreddit.search()
- If you have infinite number of OpenAI API credits, you can generate personalized response for each comments. Make sure to include OpenAI function in the comments section in the script.

## Ethical Considerations

When designing and implementing this solution, the following ethical considerations were taken into account:

1. **Privacy and Data Protection**: The script does not store or share any personal or identifiable information from Reddit users. Only publicly available post titles and comments are analyzed.

2. **Transparency and Consent**: The script operates on publicly available data from Reddit, where users have consented to their content being publicly accessible.

3. **Responsible Use of Language Models**: The generated responses from the OpenAI language model are designed to provide general information and encourage positive perspectives, without making any specific claims or recommendations.

4. **Accuracy and Bias**: While sentiment analysis and language models can be useful tools, they may have inherent biases or limitations, the script aims to interpret sentiment accurately, but users should not rely solely on the generated responses for critical decisions.

5. **Ethical Use of APIs**: The script adheres to the terms of service and ethical guidelines provided by Reddit and OpenAI. API credentials and keys are securely stored, and rate limiting is respected to avoid overloading the APIs.

6. **Responsible Research**: While the script is designed for research purposes, it does not involve any direct interaction with human subjects or the collection of sensitive data.

Overall, the script strives to maintain ethical practices, respect user privacy, and promote the responsible use of language models and sentiment analysis techniques.