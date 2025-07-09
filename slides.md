<!-- Slide 1 -->
## An LLM goes to the doctor

Understanding LLMs psychology through how the models are trained.

Note: Welcome everyone! Today we're going to explore LLM psychology - not in the sense of giving AI therapy, but understanding how these models "think" and behave based on their training process. I think it's important to understand as we use LLMs more and more in our daily lives. We'll trace through the entire training lifecycle from raw data to conversational AI, and I'll share practical insights that will immediately improve your LLM interactions.

---

<!-- Slide 2 -->
## Agenda

- **Phase 1: Data Gathering** → Token Awareness Psychology

- **Phase 2: Base Model Creation** → Understanding Pattern Prediction

- **Phase 3: Fine-tuning** → Conversational Abilities

- **Context Window Management** → Model's memory

- **Beyond Basic Chat:** Tools, MCP and Agents

Note: We'll follow the LLM training pipeline chronologically. Each phase creates specific behavioral patterns that persist in the final model. (Go briefly through sections) Each section includes actionable strategies you can use immediately.


---

<!-- Section 2: Data Gathering → Token Awareness -->
## Phase 1: Collecting Training Data

![Data Gathering Process](images/slide_3_image_1.jpg)
<!-- .element: style="max-width: 35%; margin: 5px auto;" -->

Note: I'm old enough to remember this meme - this is essentially what happens when training LLMs.

--
## Phase 1: Collecting Training Data

**Massive Scale Collection:**
- **Trillions of words** from diverse sources
- **Years of internet content** processed

Note: To understand LLM behavior, you need to understand the sheer scale. We're talking about traversing the entire internet, different sources - webpages, books, forums. This massive scale is why LLMs have such broad knowledge but also why they can be inconsistent - they've learned from both expert sources and random internet comments.

--

## Data Sources & Processing

**Where the data comes from:**
- 📚 **Books & Literature** - High-quality language patterns
- 🌐 **Web Pages** - Common knowledge and discussions  
- 💻 **Code Repositories** - Programming logic and syntax
- 📰 **News & Articles** - Current events and facts
- 💬 **Forums & Q&A** - Conversational patterns

**Quality Control Process:**
- Remove duplicates and low-quality content
- Filter harmful, biased, or copyrighted material
- Clean formatting and extract pure text
- **Convert text to tokens** - the language models can understand

Note: The quality control process is crucial but imperfect. Despite filtering, models still learn biases and inconsistencies from training data. The final step - tokenization - is where human text becomes machine-readable tokens. This process fundamentally shapes how LLMs 'see' and process language, leading to some of their most characteristic behaviors.

--

## Understanding How LLMs "See" Text

### LLMs Don't See Words - They See Tokens

**What is a token?**
- **Word pieces** not necessarily complete words

- **Subword units** that efficiently map to the training corpus

- **Functional division** for LLMs to represent their internal model (words with same meaning may represent different tokens based on placement in the sentence)

- **Numerical representations** tokens are represented as numbers

Note: This is crucial to understand - LLMs don't see words like we do. They see tokens, which are subword units. 'Strawberry' might be broken into 'straw' and 'berry', or even 'str', 'aw', 'ber', 'ry'. This tokenization process is the root cause of many seemingly strange LLM behaviors.

--

## Interactive Tokenization Demo

<iframe src="https://tiktokenizer.vercel.app/" 
        width="100%" 
        height="500" 
        frameborder="0"
        style="border-radius: 8px; background: white;">
</iframe>

https://tiktokenizer.vercel.app/

Note: Let's see this in action. Try typing 'My favorite color is red. Red is my favorite color'. This hands-on demonstration explains why LLMs struggle with character-level tasks.
--

## Why Token Awareness Matters

**Counting tasks (ex. counting letters in a word)**

![Strawberry problem](images/slide_3_image_2.png)
<!-- .element: style="max-width: 55%; margin: 5px auto;" -->

Note: This is the famous 'strawberry problem' - LLMs consistently struggle to count letters in words because they don't see individual letters. When you understand tokenization, this makes perfect sense. Models see tokens, not letters. This is why models perform poorly on character-level tasks like counting, spelling backwards, or anagrams.

---

<!-- Section 3: Base Model Creation → Overconfidence -->
## Phase 2: Creating the Base Model

![Base Model Creation](images/slide_4_image_1.jpg)
<!-- .element: style="max-width: 35%; margin: 5px auto;" -->

**Neural Network Training:**
- **Transformer architecture** with attention mechanisms
- **Billions of parameters** (GPT-3: 175B, GPT-4: estimated 1.7T)
- **Months of training** on powerful GPU clusters
- **Self-supervised learning** - no human labels needed

Note: When we have the entire learning material, we enter the most resource-intensive phase. The key insight is self-supervised learning - no human labels needed, just predict the next token. This massive scale allows the model to learn incredibly complex patterns, but also leads to the overconfidence we'll explore later.

--

## How Base Models Learn

**The Training Objective:**
- **Predict the next word** given previous context
- Learn statistical patterns in human language
- Build internal representations of concepts and relationships
- Develop grammar, facts, and reasoning patterns

**What They Optimize For:**
- **Likelihood maximization** - pick the most probable next token
- **Pattern completion** based on training data
- **Confident predictions** - always output something
- **Pretraining**: large, unlabeled datasets for general language understanding

**Mostly a well-defined and standardized process (no massive innovations in this space)**

Note: The training objective is deceptively simple - predict the next token. But this teaches the model to complete patterns, not verify truth. The model learns to always output something plausible, never to say 'I don't know' or express uncertainty. This is the root of hallucinations and overconfidence. The process is now well-standardized - the real innovations happen in the fine-tuning stages.

--

## Base model

![Base Model](images/slide_4_image_2.png)
<!-- .element: style="max-width: 90%; margin: 5px auto;" -->
https://huggingface.co/spaces/Bradarr/Gemma-3-pt-llamacpp

Note: Here you can see a base model in action - notice how it just continues text without any conversational structure. It's completing patterns, not having conversations. This is why base models feel alien - they're pure pattern completion engines. They lack the conversational training that makes modern LLMs feel more natural. That's not what we want - we want to be able to have a ChatGPT-like conversation.

---

## Phase 3: From Base Model to Conversational AI

## Supervised Fine-tuning (SFT) with human experts

**Creating Conversational Abilities:**
- **Human experts** create thousands of high-quality Q&A pairs
- **Diverse scenarios** - coding, reasoning, creative writing, analysis
- **Multi-turn conversations** - teaching context awareness
- **Safety training** - learning to refuse harmful requests

**What Changes:**
- Models learn **instruction following** instead of text completion
- Develop **conversational patterns** and helpful responses
- Learn to **ask clarifying questions** when needed
- Begin to understand **context flow** in conversations

Note: This is where the magic happens - transforming a pattern completion engine into a conversational assistant. Human experts create thousands of examples showing how to be helpful, harmless, and honest. This is relatively small-scale compared to pretraining but has huge impact on behavior. The model learns to follow instructions, engage in dialogue, and develop what feels like personality.

--

## Special "system" tokens

<iframe src="https://tiktokenizer.vercel.app/" 
        width="100%" 
        height="500" 
        frameborder="0"
        style="border-radius: 8px; background: white;">
</iframe>

https://tiktokenizer.vercel.app/

Note: Fine-tuning introduces special formatting tokens that structure conversations. You'll notice special tokens like <im_start> and <im_end> that separate user and assistant messages. The training corpus will contain those special, tokens and the model will be fine-tuned with them.

--

## ⚠️ The Confidence Problem

### Hallucinations

![Hallucinations](images/slide_4_image_3.png)
<!-- .element: style="max-width: 35%; margin: 5px auto;" -->

Note: Now we come to the issue that all LLMs suffer from - hallucinations. Why do models produce incorrect and fabricated data and why they are so confident presenting them?


--

## The Psychology Behind Overconfidence and Hallucinations

### Why This Happens?

**Base models are confident pattern predictors:**
- Base models learn to **complete patterns**, not **verify truth**
- Rewarded for **fluent responses**, not **accurate ones**
- No penalty for confident wrong answers during base training

Note: This is crucial to understand - the base training optimizes for fluency and plausibility, not accuracy. There's no mechanism during base training to distinguish between true and false information, only between fluent and awkward text. This creates the fundamental tension between helpfulness and truthfulness.


--

## The Psychology Behind Overconfidence and hallucinations

### Why This Happens?

**Fine-tuned models tend toward a human-like presentation:**
- **Authoritative tone** mimmicking the way a domain expert would talk about his area of knowledge
- **Detailed explanations** increase perceived reliability
- **LLMs are pattern predictors** - in this case they predict how an expert would talk

Note: Fine-tuning actually makes this worse in some ways. Models learn to mimic expert communication patterns - detailed explanations, authoritative tone, specific examples. This makes false information more convincing because it's presented exactly how a real expert would present true information. The model isn't lying intentionally - it's just very good at mimicking expert communication patterns.

--

## Actionable Strategies

### 🛡️ Protecting Against Overconfidence

**Verification Habits:**
- **Cross-check important facts** with reliable sources
- **Ask for sources** and verify they actually exist
- **Question specific claims** - dates, numbers, quotes
- **Always be skeptical** and verify LLM output

Note: Everybody repeats it, but I will reiterate - never fully trust an LLM output. Always verify. Treat LLMs as very capable research assistants who might make errors, not as authoritative sources. The key is developing a healthy skepticism while still leveraging their capabilities.

--

## Actionable Strategies

### 🛡️ Protecting Against Overconfidence

**Red Flags to Watch For:**
- Very specific claims without sources
- Information that seems too convenient - especially when you try to correct the model
- Claims about recent events (training cutoff issues) - can be mitigated with tools (more later)

Note: These red flags help you identify when to be extra skeptical. The 'too convenient' point is crucial - especially, if challenged the model on its response - for ex. he proposed an answer that was not going in the direction you wanted, so you correct him, but often times models will try to give you want you want and, for ex. create nonexisting APIs . Recent events are problematic due to training cutoffs, but tools can help here.

---

## Context Window Management

### Context Windows

**Model's memory**
- **Fixed size memory** - 128K+ tokens window (GPT-4o) - some models "claim" larger windows<br/>
https://github.com/NVIDIA/RULER

- **Sliding window** - older content gets "forgotten" when limit reached

- **Attention mechanism** - models tend to focus more on the context

Note: Context windows are the model's working memory - everything it can 'remember' during a conversation. Most models have over 128 thousand token memory, some claim larger, but those numbers are sometimes challeneged - here is a website that tracks "effective" token size instead of declared. All whish is outside the context window is forgotten. There is a tendency for models to concentrate on the context instead of training material. They tend to forget their training as the context gets larger.

--

## Psychology Tip: Context Window Management

### 🧠 Context is Conversation Memory

**Context Window Psychology:**
- **Everything in session** is "remembered" and influences responses

- **Context switching** (new chat) completely resets memory

Note: Context is your memory and it will influence future responses. Starting a new chat is like meeting someone with complete amnesia. Use this wisely.

--

### Context Management Examples

**Effective Context Usage:**

**Building on Previous Responses:**
```text
User: "Here are my project details: (...). Do you have any suggestions for improvements?"
AI: [detailed explanation]
User: "Would the project benefit from changing to server-side rendering?"
AI: [references specific project details from previous answer]
```

Note: This shows effective context usage - the second question builds on the first, and the AI can reference specific project details without you repeating them. The model can also adjust the answer specifically to your project instead of being generic.

--

### Strategic Context Management

#### 💡 Optimizing Your Conversations

**Best Practices:**

**Maintaining Context:**
- Keep **related discussions** in the same conversation - you can reopen previous chats!
- **Reference earlier points** to build coherent discussions
- **Summarize key points** when conversations get long (some tools do it automatically, ex. Claude Caude auto-compact)
- **Avoid topic switching** unless necessary - open a new chat when switching topic

Note: These practices help you work with the model's memory limitations rather than against them. Reopening previous conversations maintains context across sessions. When conversations get long, summarizing helps keep important information accessible. Topic switching in the same conversation can confuse the model's responses - it's better to start fresh for unrelated topics.

--

### Strategic Context Management

#### 💡 Optimizing Your Conversations

**Best Practices:**

**Providing Context**
- **Give the right amount of context at start**

![](images/slide_5_image_2.png)
<!-- .element: style="max-width: 85%; margin: 5px auto;" -->

average drop of 39%, OpenAI’s o3’s score dropped from 98.1 to 64.1.<br/>
https://arxiv.org/pdf/2505.06120

Note: How we provide the context also makes a difference. This is from a recent publication by a team of researchers at Microsoft where they gave two types of contexts to the LLMs. One was full context in one message, the other way was to split the same information into multiple prompts. Huge drop in efficiency. Lesson for us - give the maximum amount of information at the start.

--

### Strategic Context Management

#### 💡 Optimizing Your Conversations

**Best Practices:**

**Providing Context**
- **Beware of context poisoning** - when models get lost, restart.

>Fixations on delusions due to goal-setting and also due to the Guidance Gemini instance are not
an uncommon occurrence in watching Gemini Plays Pokémon (...). An especially egregious form of this issue can take place with “context
poisoning” – where many parts of the context (goals, summary) are “poisoned” with misinformation
about the game state, which can often take a very long time to undo. As a result, the model can
become fixated on achieving impossible or irrelevant goals

https://storage.googleapis.com/deepmind-media/gemini/gemini_v2_5_report.pdf

Note: A Team of researchers at Google were using Gemini to play the game of Pokemon. They struggled with context poisoning. Context poisoning is when incorrect information early in a conversation affects all subsequent responses. Models can become fixated on wrong assumptions and it's often easier to start a new conversation than to correct the context.

--

### Strategic Context Management

#### 💡 Optimizing Your Conversations

**Best Practices:**

**Providing Context**
- **Divide complex tasks into subproblems**

>We found that a multi-agent system with Claude Opus 4 as the lead agent and Claude Sonnet 4 subagents outperformed single-agent Claude Opus 4 by 90.2% on our internal research eval. For example, when asked to identify all the board members of the companies in the Information Technology S&P 500, the multi-agent system found the correct answers by decomposing this into tasks for subagents, while the single agent system failed to find the answer with slow, sequential searches.

https://www.anthropic.com/engineering/built-multi-agent-research-system

Note: There is huge value in dividing complex tasks into subproblems. A publication by the team of researchers at Anthropic tried two approaches for a problem of identifying board members of S&P500 - either a single agent or lead agent+subagents. The second approach yielded significantly better results.
--

### Advanced Context Strategies

**Context Priming:**
- Establish **role and context** 

```text
[User] Explain trigonometry

[Claude] Trigonometry is the study of triangles and the relationships between their angles and sides. 
It originated from practical needs like navigation, astronomy, and surveying.
The foundation rests on three basic ratios in right triangles. 
If you have a right triangle and focus on one of the non-right angles, you can define:

Sine (sin): opposite side ÷ hypotenuse
Cosine (cos): adjacent side ÷ hypotenuse
Tangent (tan): opposite side ÷ adjacent side

These ratios stay constant for any given angle, regardless of the triangle's size. 
A 30° angle always has the same sine value, whether you're measuring a tiny triangle or a massive one.
(...)
```

Note: There is a whole branch of research called Prompt Engineering which deals with those techniques, I won't be getting into detailed ones, but just wanted to show some of simpler ones. For example, when asking models for explanations, sometimes we have a specific context of the question - for ex. explain some problem to developers vs explaining them to business people.

--

### Advanced Context Strategies

**Context Priming:**
- Establish **role and context** 

```text
[User] You are a helpful Maths teacher who explains the concepts to a primary school student using simple examples. 
Explain trigonometry.

[Claude] Trigonometry is about triangles and how their sides and angles relate to each other.
Let me start with the basics using things you already know:
What makes trigonometry special?
We focus on right triangles - triangles that have one corner that's exactly like the corner of a square (90 degrees).
The three main parts:
Think of a right triangle like a ladder leaning against a wall:

The wall is the "opposite" side
The ground is the "adjacent" side
The ladder itself is the "hypotenuse" (the longest side)

The three trigonometric ratios:

Sine (sin) = opposite ÷ hypotenuse
If your ladder is 5 meters long and reaches 3 meters up the wall, then sin = 3÷5 = 0.6
Cosine (cos) = adjacent ÷ hypotenuse
If the bottom of the ladder is 4 meters from the wall, then cos = 4÷5 = 0.8
Tangent (tan) = opposite ÷ adjacent
This compares the height (3m) to the distance from wall (4m), so tan = 3÷4 = 0.75
```

Note: We can ask for straightforward explanation, however if we give a role to the model, it's gonna give results way better adapated at our situation. In this context, I want to explain trigonometry to my child who is in primary school.

--

### Advanced Context Strategies

![Temperature](images/slide_6_image_1.png)
<!-- .element: style="max-width: 65%; margin: 5px auto;" -->

- **Use system prompts** to maintain consistent context

- **Use temperature settings** - low temperature == low creativity

Note: System prompts are persistent context that affects every response. So it's like a "pinned" message that gets added to every prompt. Temperature controls randomness - low temperature for factual tasks, higher temperature for creative tasks. Use that along with the context to play with models behaviour

---

## 🤖 Beyond Basic Chat: Tools and Agents 🤖

### Extending LLM Capabilities

**Model Context Protocol (MCP):**
- **Standardized way** for LLMs to connect to external tools and data sources
- **Real-time information** - access current data, not just training data
- **Tool integration** - file systems, databases, APIs, web search
- **Secure connections** - controlled access to external resources

Note: This is where LLMs transcend their training limitations. MCP allows models to access real-time information, breaking free from training cutoffs. Instead of just predicting patterns, models can now retrieve current data, perform calculations, and interact with external systems. This fundamentally changes their capabilities from static knowledge to dynamic information access.

--

## 🤖 Beyond Basic Chat: Tools and Agents 🤖

### Extending LLM Capabilities

**AI Agents:**
- **Autonomous task execution** - LLMs that can take actions
- **Multi-step reasoning** - breaking down complex tasks
- **Goal-oriented behavior** - working toward specific outcomes

Note: Agents represent the evolution from passive Q&A to active problem-solving. They can plan, execute, and iterate on tasks autonomously. This is LLMs with agency - the ability to take actions in the world, not just generate text. They combine the pattern recognition of LLMs with the ability to interact with external systems and persist through multi-step tasks.

--

## Psychology Tips for Tools and Agents

### 🔧 Understanding Enhanced Capabilities

**What Changes with Tools/Agents:**
- **Reduced hallucination** - access to real-time, verified data
- **Dynamic context** - can fetch relevant information as needed
- **Action capability** - can modify files, send emails, make API calls

Note: This addresses many of the fundamental limitations we've discussed. Tools provide verified, real-time data that reduces hallucination. Dynamic context means models aren't limited to their training data or current conversation. Action capability transforms them from text generators to task executorss

--

## Psychology Tips for Tools and Agents

### 🔧 Understanding Enhanced Capabilities

**New Considerations:**
- **Verify agent actions** - understand what tools are being used and only confirm if you know what the command does
- **Understand limitations** - agents are still LLMs with the same core psychology
- **Force LLMS to use tools** by using keywords - ex. "use code" or "use web"

Note: Enhanced capabilities come with new responsibilities (or same responsibilities). Always verify what tools agents are using - they inherit the same overconfidence issues we discussed. The core psychology remains the same; they just have more ways to act on their predictions. Most of the times models will now when you want to use the tools, but you can ask them specifically.

--

## Psychology Tips for Tools and Agents

### 🔧 Understanding Enhanced Capabilities

ChatGPT:

```text
User: how many r's are in the word strawberry? Use code
```

```text
AI: Analysis:
```

```python
# Count how many times the letter 'r' appears in the word 'strawberry'
word = "strawberry"
count_r = word.count('r')
count_r
```

```text
There are 3 letter **'r'**s in the word "strawberry". 
```

Note: This solves the tokenization problem we discussed earlier! By using code execution, the model can count individual characters correctly, bypassing the token-level limitations. The key phrase 'Use code' forces the model to use its tools rather than relying on pattern prediction. This is a perfect example of how tools overcome fundamental LLM limitations.
--

## Psychology Tips for Tools and Agents

### 🚧 Creating complex projects

**Best Practices for creating complex projects:**
- **Create a detailed execution plan** - you can even ask LLM to do it for you.

![Execution plan](images/slide_6_image_2.png)
<!-- .element: style="max-width: 85%; margin: 5px auto; align: center" -->

--

## Psychology Tips for Tools and Agents

### 🚧 Creating complex projects

**Best Practices for creating complex projects:**
- **Save the plan to an MD file** - or ask the LLM to do it (if uses agents)
- **Ask the LLM to move step by step** through the execution plan. Commit after each step. Use tools like ClaudeCode.

![Execution plan](images/slide_6_image_3.png)
<!-- .element: style="max-width: 85%; margin: 5px auto; align: center" -->

Note: What agents allow us to do is to create complex projects almost by themselves (don't forget to supervise). There are some good practices being developed in the community, still we are in early stages of trully capable agent workflows. What is currently recommended is to first create a grand development plan and save it to a file (like MD for example). This is an example of a hobby project I did (present details if you want).

--

## Psychology Tips for Tools and Agents

### 🚧 Creating complex projects

**Best Practices for creating complex projects:**
- **Review agent plans** before execution
- **Remember** - agents inherit LLM strengths and weaknesses

Note: This is crucial - agents don't magically fix LLM psychology. They're still pattern predictors with access to tools. Review plans for the same issues we've discussed: overconfidence, hallucination, and context limitations. The enhanced capabilities make these issues more consequential since agents can take actions in the real world.

---

## More

**Missing parts** <br/>
Reasoning models, Deep research, voice and image processing, vibe coding?

**Recommended** <br/>
Andrey Karpathy: https://www.youtube.com/andrejkarpathy

Note: We've covered the core training pipeline and psychological patterns, but there's always more to explore. We haven't touched (...). If you're interested in a deep dive into how LLMs work, I highly recommend Andrey Karpathy's channel. The key takeaway: understanding how LLMs are trained gives you superpowers in using them effectively. Every interaction is more productive when you understand the psychology behind the responses.