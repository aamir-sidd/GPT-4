# GPT-4
GPT-4 is a large multimodal model (accepting text inputs and emitting text outputs today, with image inputs coming in the future) that can solve difficult problems with greater accuracy than any of our previous models, thanks to its broader general knowledge and advanced reasoning capabilities. While less capable than humans in many real-world scenarios, exhibits human-level performance on various professional and academic benchmarks.  Like gpt-3.5-turbo, GPT-4 is optimized for chat but works well for traditional completions tasks.
It was trained on Microsoft Azure AI supercomputers



Paper - https://cdn.openai.com/papers/gpt-4.pdf

System Card - https://cdn.openai.com/papers/gpt-4-system-card.pdf

API Waitlist - https://openai.com/waitlist/gpt-4-api

GPT-4 Wiki - https://en.wikipedia.org/wiki/GPT-4

GPT-3 Wiki - https://en.wikipedia.org/wiki/GPT-3

GPT-3 - https://chat.openai.com/chat



| LATEST MODEL   | DESCRIPTION    |	MAX TOKENS     | TRAINING DATA  |
| -------------- | -------------- | -------------- | -------------- |
| gpt-4          | More capable than any GPT-3.5 model, able to do more complex tasks, and optimized for chat. Will be updated with our latest model iteration. | 8,192 tokens | Up to Sep 2021 |
| gpt-4-0314     | Snapshot of gpt-4 from March 14th 2023. Unlike gpt-4, this model will not receive updates, and will only be supported for a three month period ending on June 14th 2023. | 8,192 tokens | Up to Sep 2021 |
| gpt-4-32k	     | Same capabilities as the base gpt-4 mode but with 4x the context length. Will be updated with our latest model iteration. | 32,768 tokens | Up to Sep 2021 |
| gpt-4-32k-0314 | Snapshot of gpt-4-32 from March 14th 2023. Unlike gpt-4-32k, this model will not receive updates, and will only be supported for a three month period ending on June 14th 2023. | 32,768 tokens | Up to Sep 2021 |


## Capabilities

### Visual inputs

GPT-4 can accept a prompt of text and images, which—parallel to the text-only setting—lets the user specify any vision or language task. Specifically, it generates text outputs (natural language, code, etc.) given inputs consisting of interspersed text and images. Over a range of domains—including documents with text and photographs, diagrams, or screenshots—GPT-4 exhibits similar capabilities as it does on text-only inputs. Furthermore, it can be augmented with test-time techniques that were developed for text-only language models, including few-shot and chain-of-thought prompting. Image inputs are still a research preview and not publicly available.

### Steerability

OpenAI's been working on each aspect of the plan outlined in their post about defining the behavior of AIs, including steerability. Rather than the classic ChatGPT personality with a fixed verbosity, tone, and style, developers (and soon ChatGPT users) can now prescribe their AI’s style and task by describing those directions in the “system” message. System messages allow API users to significantly customize their users’ experience within bounds. OpenAI will keep making improvements here (and particularly know that system messages are the easiest way to “jailbreak” the current model, i.e., the adherence to the bounds is not perfect).

## Benchmarks

GPT-4 evaluation on traditional benchmarks designed for machine learning models. GPT-4 considerably outperforms existing large language models, alongside most state-of-the-art (SOTA) models which may include benchmark-specific crafting or additional training protocols:

![Screenshot 2023-03-15 030315](https://user-images.githubusercontent.com/123953232/225142682-47dc4bf9-382f-404a-b269-89753a7298f8.png)


## Limitations

Despite its capabilities, GPT-4 has similar limitations as earlier GPT models. Most importantly, it still is not fully reliable (it “hallucinates” facts and makes reasoning errors). Great care should be taken when using language model outputs, particularly in high-stakes contexts, with the exact protocol (such as human review, grounding with additional context, or avoiding high-stakes uses altogether) matching the needs of a specific use-case.

The model can have various biases in its outputs.

GPT-4 generally lacks knowledge of events that have occurred after the vast majority of its data cuts off (September 2021), and does not learn from its experience. It can sometimes make simple reasoning errors which do not seem to comport with competence across so many domains, or be overly gullible in accepting obvious false statements from a user. And sometimes it can fail at hard problems the same way humans do, such as introducing security vulnerabilities into code it produces.

GPT-4 can also be confidently wrong in its predictions, not taking care to double-check work when it’s likely to make a mistake. Interestingly, the base pre-trained model is highly calibrated (its predicted confidence in an answer generally matches the probability of being correct). However, through OpenAI's current post-training process, the calibration is reduced.

## Training process

Like previous GPT models, the GPT-4 base model was trained to predict the next word in a document, and was trained using publicly available data (such as internet data) as well as data we’ve licensed. The data is a web-scale corpus of data including correct and incorrect solutions to math problems, weak and strong reasoning, self-contradictory and consistent statements, and representing a great variety of ideologies and ideas.

So when prompted with a question, the base model can respond in a wide variety of ways that might be far from a user’s intent. To align it with the user’s intent within guardrails, we fine-tune the model’s behavior using reinforcement learning with human feedback (RLHF).

Note that the model’s capabilities seem to come primarily from the pre-training process—RLHF does not improve exam performance (without active effort, it actually degrades it). But steering of the model comes from the post-training process—the base model requires prompt engineering to even know that it should answer the questions.

### Predictable scaling

A large focus of the GPT-4 project has been building a deep learning stack that scales predictably. The primary reason is that, for very large training runs like GPT-4, it is not feasible to do extensive model-specific tuning. We developed infrastructure and optimization that have very predictable behavior across multiple scales. To verify this scalability, we accurately predicted in advance GPT-4’s final loss on our internal codebase (not part of the training set) by extrapolating from models trained using the same methodology but using 10,000x less compute:

![Screenshot 2023-03-15 031408](https://user-images.githubusercontent.com/123953232/225146754-c93ea463-7d08-40ff-a9ae-38ce02666586.png)

Some capabilities are still hard to predict. For example, the Inverse Scaling Prize was a competition to find a metric that gets worse as model compute increases, and hindsight neglect was one of the winners. Just like with another recent result, GPT-4 reverses the trend:

![image](https://user-images.githubusercontent.com/123953232/225147314-ed08ad68-747f-4471-800b-b0b8dc4de4fb.png)
