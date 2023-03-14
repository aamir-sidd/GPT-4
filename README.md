# GPT-4
GPT-4 is a large multimodal model (accepting image and text inputs, emitting text outputs) that, while less capable than humans in many real-world scenarios, exhibits human-level performance on various professional and academic benchmarks.

Paper - https://cdn.openai.com/papers/gpt-4.pdf

System Card - https://cdn.openai.com/papers/gpt-4-system-card.pdf



| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| VQAv2         | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

## Capabilities



### Visual inputs

GPT-4 can accept a prompt of text and images, which—parallel to the text-only setting—lets the user specify any vision or language task. Specifically, it generates text outputs (natural language, code, etc.) given inputs consisting of interspersed text and images. Over a range of domains—including documents with text and photographs, diagrams, or screenshots—GPT-4 exhibits similar capabilities as it does on text-only inputs. Furthermore, it can be augmented with test-time techniques that were developed for text-only language models, including few-shot and chain-of-thought prompting. Image inputs are still a research preview and not publicly available.

### Steerability

OpenAI's been working on each aspect of the plan outlined in their post about defining the behavior of AIs, including steerability. Rather than the classic ChatGPT personality with a fixed verbosity, tone, and style, developers (and soon ChatGPT users) can now prescribe their AI’s style and task by describing those directions in the “system” message. System messages allow API users to significantly customize their users’ experience within bounds. OpenAI will keep making improvements here (and particularly know that system messages are the easiest way to “jailbreak” the current model, i.e., the adherence to the bounds is not perfect).

## Limitations



## Training process

Like previous GPT models, the GPT-4 base model was trained to predict the next word in a document, and was trained using publicly available data (such as internet data) as well as data we’ve licensed. The data is a web-scale corpus of data including correct and incorrect solutions to math problems, weak and strong reasoning, self-contradictory and consistent statements, and representing a great variety of ideologies and ideas.

So when prompted with a question, the base model can respond in a wide variety of ways that might be far from a user’s intent. To align it with the user’s intent within guardrails, we fine-tune the model’s behavior using reinforcement learning with human feedback (RLHF).

Note that the model’s capabilities seem to come primarily from the pre-training process—RLHF does not improve exam performance (without active effort, it actually degrades it). But steering of the model comes from the post-training process—the base model requires prompt engineering to even know that it should answer the questions.
