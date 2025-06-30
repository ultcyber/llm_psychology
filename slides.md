<!-- Slide 1 -->
## An LLM goes to the doctor

Understanding LLMs psychology through how they are trained.

---

<!-- Slide 2 -->
## Agenda

- How are LLMs built 
- What are the differences between model types? 
- Some tips and tricks on how to effectively use LLMs 

---

<!-- Section 2: Data Gathering → Token Awareness -->
## Phase 1: Collecting Training Data

![Data Gathering Process](images/slide_3_image_1.jpg)
<!-- .element: style="max-width: 35%; margin: 5px auto;" -->

--
## Phase 1: Collecting Training Data

**Massive Scale Collection:**
- **~500 billion tokens** for GPT-3
- **Trillions of words** from diverse sources
- **Years of internet content** processed

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

--

## Understanding How LLMs "See" Text

### LLMs Don't See Words - They See Tokens

**What is a token?**
- **Word pieces** not necessarily complete words

- **Subword units** that efficiently map to the training corpus

- **Functional division** for LLMs to represent their internal model (words with same meaning may represent different tokens based on placement in the sentence)

- **Numerical representations** tokens are represented as numbers

--

## Interactive Tokenization Demo

<iframe src="https://tiktokenizer.vercel.app/" 
        width="100%" 
        height="500" 
        frameborder="0"
        style="border-radius: 8px; background: white;">
</iframe>

https://tiktokenizer.vercel.app/
--

## Why Token Awareness Matters

**Counting tasks (ex. counting letters in a word)**

![Strawberry problem](images/slide_3_image_2.png)
<!-- .element: style="max-width: 55%; margin: 5px auto;" -->

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
- **No built-in uncertainty** - models don't say "I don't know"

--

## Training Scale & Process

**Massive Computational Requirements:**
- **Thousands of GPUs** running for months
- **Petabytes of training data** processed multiple times
- **Gradient descent optimization** adjusting billions of weights
- **Cost**: Millions of dollars for large models

--

## Training Scale & Process

**Learning Process:**
- See partial text → Predict next word → Check against actual → Adjust weights
- Repeat trillions of times across the entire dataset
- Gradually builds sophisticated language understanding
- Mostly a well-defined and standardized process (no massive innovations in this space)

--

## Base model

![Base Model](images/slide_4_image_2.png)
<!-- .element: style="max-width: 75%; margin: 5px auto;" -->

https://huggingface.co/spaces/Bradarr/Gemma-3-pt-llamacpp

--

## From Base Model to Conversational AI

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

--

## Special "system" tokens

<iframe src="https://tiktokenizer.vercel.app/" 
        width="100%" 
        height="500" 
        frameborder="0"
        style="border-radius: 8px; background: white;">
</iframe>

https://tiktokenizer.vercel.app/

--

## ⚠️ The Confidence Problem

### Hallucinations

![Hallucinations](images/slide_4_image_3.png)
<!-- .element: style="max-width: 35%; margin: 5px auto;" -->



--

## The Psychology Behind Overconfidence and Hallucinations

### Why This Happens?

**Base models are confident pattern predictors:**
- Base models learn to **complete patterns**, not **verify truth**
- Rewarded for **fluent responses**, not **accurate ones**
- No penalty for confident wrong answers during base training


--

## The Psychology Behind Overconfidence and hallucinations

### Why This Happens?

**Fine-tuned models tend toward a human-like presentation:**
- **Authoritative tone** mimmicking the way a domain expert would talk about his area of knowledge
- **Detailed explanations** increase perceived reliability
- **LLMs are pattern predictors** - in this case they predict how an expert would talk

--

## Actionable Strategies

### 🛡️ Protecting Against Overconfidence

**Verification Habits:**
- **Cross-check important facts** with reliable sources
- **Ask for sources** and verify they actually exist
- **Question specific claims** - dates, numbers, quotes
- **Always be skeptical** and verify LLM output

--

## Actionable Strategies

### 🛡️ Protecting Against Overconfidence

**Red Flags to Watch For:**
- Very specific claims without sources
- Information that seems too convenient
- Responses that don't acknowledge uncertainty
- Claims about recent events (training cutoff issues) - can be adjusted with agents (more later)

---

## Context Window Management

### Context Windows

**Context Window Architecture:**
- **Fixed size memory** - 128K+ tokens window (GPT-4o) to even several million for reasoning models
- **Sliding window** - older content gets "forgotten" when limit reached
- **Attention mechanisms** - models focus on relevant parts of context

--

## Psychology Tip: Context Window Management

### 🧠 Context is Conversation Memory

#### How Models Use Conversation History

**Context Window Psychology:**
- **Everything in session** is "remembered" and influences responses
- **Recent information** carries more weight than older information
- **Context switching** (new chat) completely resets memory

--

### Context Management Examples

**Effective Context Usage:**

**Building on Previous Responses:**
```text
User: "Explain quantum computing"
AI: [detailed explanation]
User: "How does this relate to the security example you mentioned?"
AI: [references specific security point from earlier]
```

--

### Strategic Context Management

#### 💡 Optimizing Your Conversations

**Best Practices:**

**Maintain Context:**
- Keep **related discussions** in the same conversation - you can reopen previous chats!
- **Reference earlier points** to build coherent discussions
- **Summarize key points** when conversations get long
- **Avoid topic switching** unless necessary - open a new chat when switching topic

--

### Strategic Context Management

#### 💡 Optimizing Your Conversations

**Best Practices:**

**Provide Context When Needed:**
- **Start with background** when switching topics
- **Remind the model** of important constraints or preferences
- **Restate key information** if conversation is getting long

--

### Strategic Context Management

#### 💡 Optimizing Your Conversations

**Best Practices:**

**Work with Context Limits:**
- **Break complex tasks** into focused conversations
- **Use conversation history** strategically
- **Be aware** that models can't "remember" across sessions

--

### Advanced Context Strategies

**Power User Techniques:**

**Context Priming:**
- Establish **role and context** for complex tasks
- **Start a new chat** when context becomes unfocused
- **Use system prompts** to maintain consistent context

---

## 🤖 Beyond Basic Chat: MCP and Agents 🤖

### Extending LLM Capabilities

**Model Context Protocol (MCP):**
- **Standardized way** for LLMs to connect to external tools and data sources
- **Real-time information** - access current data, not just training data
- **Tool integration** - file systems, databases, APIs, web search
- **Secure connections** - controlled access to external resources

--

## 🤖 Beyond Basic Chat: MCP and Agents 🤖

### Extending LLM Capabilities

**AI Agents:**
- **Autonomous task execution** - LLMs that can take actions
- **Multi-step reasoning** - breaking down complex tasks
- **Goal-oriented behavior** - working toward specific outcomes

--

## Psychology Tips for MCP and Agents

### 🔧 Understanding Enhanced Capabilities

**What Changes with MCP/Agents:**
- **Reduced hallucination** - access to real-time, verified data
- **Dynamic context** - can fetch relevant information as needed
- **Action capability** - can modify files, send emails, make API calls
- **Extended memory** - can save and retrieve information across sessions

--

## Psychology Tips for MCP and Agents

### 🔧 Understanding Enhanced Capabilities

**New Considerations:**
- **Verify agent actions** - understand what tools are being used and only confirm if you know what the command does
- **Understand limitations** - agents are still LLMs with the same core psychology
- **Force LLMS to use tools** by using keywords - ex. "use code" or "use web"

--

## Psychology Tips for MCP and Agents

### 🔧 Understanding Enhanced Capabilities

ChatGPT:

User: how many r's are in the word strawberry? Use code

AI: Analysis:
```python
# Count how many times the letter 'r' appears in the word 'strawberry'
word = "strawberry"
count_r = word.count('r')
count_r

```
There are 3 letter **'r'**s in the word "strawberry". 

--

## Psychology Tips for MCP and Agents

### 🚧 Creating complex projects

**Best Practices for creating complex projects:**
- **Create a detailed execution plan** - you can even ask LLM to do it for you.
- **Review agent plans** before execution
- **Ask the LLM to move step by step** through the execution plan. Commit after each step.
- **Remember** - agents inherit LLM strengths and weaknesses

---

## More

**Missing parts** <br/>
Reasoning models, RLHF (Reinforcement learning from human feedback), vibe coding?

**Recommended** <br/>
Andrey Karpathy: https://www.youtube.com/andrejkarpathy