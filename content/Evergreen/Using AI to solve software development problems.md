## Introduction

Unlocking the potential of Generative AI (Gen AI) requires a clear understanding of its capabilities and limitations. While this article offers a comprehensive overview, we'll delve deeper into the core concepts to dispel any confusion.

### What is Gen AI?

Generative AI is a subset of artificial intelligence that involves training algorithms to produce new data with similar characteristics as the data they were trained on. it actively generates new content that aligns with the learned patterns. This content can encompass text, images, videos, audio, or other formats. The generated output is guided by user input, which provides prompts or constraints for the AI to follow.

Before generative AI and Large Language Models (LLMs) became popular, we also had many machine learning models that serve specific purposes, for example:

- Text Classification: Classify text into specific classes.
- Text Summarization: Summarize long text.
- Sentiment Analysis: Identify emotions in text.

These models are trained to do a specific task based on human-labeled datasets. Their strengths lie in accuracy and precision within their narrow domains, but flexibility and broad generalizability remain limitations.

In contrast, generative AI, often embodied by large language models like LLMs, takes a different approach. Instead of tackling individual tasks, it aims to learn the underlying patterns and relationships within massive, unlabeled datasets. This holistic understanding enables flexible application to diverse tasks, including text generation, translation, and even creative writing.

In other words, its ability is only one: to fill in the blanks, by matching the input with the patterns it has learned. But it is precisely this simplicity that brings about great application potential, because the "blank" can be anything: class, summary, sentiment, code.

**Bonus:** Today's LLMs are built on the Transformer model, introduced by Google in 2017. Transformer is based on the attention mechanism to process input data. This mechanism allows the model to focus on the important parts of the input data, ignoring the unimportant parts, helping to reduce the resources needed for training and inference.

### Context: The Master Key

![[Pasted image 20231120103134.png]]

Imagine you ask to finish this sentence, "He is in..."; without further details, the options are endless. But add "he is in ..., because today is the first day after summer vacation," and suddenly, the picture becomes clear: "school"

Context isn't just about words; it encompasses your understanding of language, the relationships between concepts, and the broader situation. The more nuanced your context, the more accurate and relevant the output from Gen AI becomes.

However, providing more context isn't without its costs. Increasing the number of parameters in an LLM to handle diverse contexts requires more computational power. But the trade-off is worth it: a deeper understanding of context leads to less confusion and more accurate, meaningful results.

### The Double-Edged Sword: Hallucination

One of the biggest problems with AI is hallucination. AI can generate content that seems very convincing, very confident, and certain, but is actually wrong. This phenomenon is called hallucination.

The cause of this hallucination is due to the training data containing incorrect information, not being diverse enough, containing bias, and the design of the model is not good.

In the early days of Gen AI, hallucination results occurred more frequently, and later improved significantly.

![[Pasted image 20231206104651.png]]
> [Source](obsidian://opengate?url=https://promptengineering.org/measuring-how-much-leading-ai-chatbots-hallucinate/)

Read more: [[Vectara's Evaluation Approach]]

In the use cases below, you will notice that there are many cases where AI generates incorrect results, code that does not run, or worse, wrong logic but is still very confident. So it is important to always be suspicious when using gen AI.

On the user side, there are a few ways to reduce hallucination, such as ReACT and RAG. Understanding this will help us to be proactive and less disappointed when using AI. In the examples below, the results will be much better when we provide more context and better prompts.

## What challenges do we face in programming?

Programming thrives on challenges. Solutions like languages, frameworks, and tools emerge, but these often become future hurdles, necessitating ongoing learning and adaptation.

![[Pasted image 20231113103426.png]]

Two of the most frustrating things about coding are that it can be either too boring or too "hard".

We often have to write the same code over and over again, such as CRUD, lint config, and error checking. This is called boilerplate code, and it can be tedious and difficult to maintain.

By "hard," I don't mean challenging. I mean unnecessarily difficult, such as when trying to understand requirements or communicate with others. It can take a lot of time to understand the nuances of language in refinement meetings or to decipher poorly written documentation. How can we code if we can't even understand the requirements?

All of these roadblocks can have a negative impact on productivity, code quality, and maintainability. They can also make programming less enjoyable and less rewarding.

Perhaps the programming experience will never be perfect. There is no one language that is both sweet and powerful. However, with the advancement of AI, there is hope for real improvements in this area.

### How can LLMs help us solve these challenges?

As mentioned above, LLMs can now understand context and generate anything that is left blank. So what can it help us with in programming? In this article, we will take a look at some typical usage scenarios, such as:

1. **Generating code**
2. **Analyzing requirements and providing consultation**
3. **Supporting work with legacy projects**
4. **Analyzing databases**
5. **Onboarding and training new developers**
6. **Ensuring coding conventions**

## AI-powered story writing and analysis

**Problem**

Good user stories are essential for the success of a sprint, but there are two common problems:

- **Low-quality user stories:** They may be incomplete or even misleading to developers.
- **Misunderstanding:** Developers with limited product knowledge or perspective may not fully understand or misunderstand a story.

There are many reasons for these problems, such as lack of project knowledge, poor communication skills, or time constraints. However, even if the problem is due to other factors, if you don't understand the story, it can lead to rework or difficulty working with other developers.

**Solution**

![](https://www.youtube.com/watch?v=IhHkMyxxFh8&t=63s&ab_channel=Atlassian)

As shown in the video, AI can make it easier for the entire team to write and understand stories.

Atlassian's product is only available for a limited number of users at this time. However, imagine if it had additional features, such as the ability to integrate with the code base on GitLab, automatically break down tasks for developers, ask follow-up questions, brainstorm with the product owner, suggest potential problems, or even write test cases.

These additional features would make AI-assisted story writing and analysis even more powerful and useful. They would help to improve communication and collaboration between developers, product owners, and other stakeholders.

### Demo

The best way to use AI-assisted story writing and analysis at the moment is to use Github Copilot Chat. It currently supports JetBrain's IDE and VS Code.

![](https://youtu.be/NpD83elT_5E)

Final: [idea.md](https://github.com/nguyenvanduocit/stockbar/blob/main/docs/idea.md)

From this point, we will ask AI to create requirements based on this idea:

![](https://youtu.be/gJxTNwxt9ao)

View file: [requirement.md](https://github.com/nguyenvanduocit/stockbar/blob/main/docs/requirement.md)

Now break it down in to tasks:

![](https://youtu.be/7eWjXZ8ARcI)

View file: [user-stories.md](https://github.com/nguyenvanduocit/stockbar/blob/main/docs/user-stories.md)

## AI for System Architecture Design

### Problem

System architecture design is an important and complex process that requires deep professional knowledge and sharp decision-making skills. The system architecture must meet the requirements of performance, security, flexibility, and scalability. At the same time, the system architecture must be suitable for the business's characteristics, be able to adapt to changes in requirements, and be able to integrate tightly with legacy systems.

### Solution

The application of AI in system architecture design can be very helpful, like searching for information on Google or reading books, but more direct and time-saving. Here are some ways that AI can help:

- **Provide design suggestions:** AI can analyze requirements and evaluate different options to provide design suggestions that are most suitable for the needs of the business. This helps system developers save time and effort.
- **Create necessary diagrams to help understand the system better:** Based on requirements, AI can create necessary diagrams to help understand the system better, such as data flow diagrams or sequence diagrams. This makes it easier for system developers to grasp and manage the system.
- **Identify potential risks and propose mitigation strategies:** AI can help identify potential risks and propose mitigation strategies.

Có nhiều level architecture ([[software architecture level]]). 

### Demo AI giúp thiết kế hệ thống phần mềm



### Demo Draw diagram

As a visual learner, drawing and writing are essential for me to solidify my thoughts and output the results of design processes. But manually crafting all aspects of diagrams isn't necessary! AI can jumpstart simple diagrams, letting you focus on the juicy bits. In the example below, I had AI sketch out the collector-database interaction, then the database-analysis interaction, step-by-step.



![[Pasted image 20231121165252.png]]
Take this example: I used AI to build a diagram step-by-step, starting with collector-database interaction, then adding the database-analysis flow. The more context you provide, the closer the output matches your vision. Shoutout to @hey_thien and their awesome usediagram.com tool!


Đã thiết kế xong, phần tiếp theo ta cần hiện thực các design này thành từng dòng code cụ thể. Việc mà qua thời gian có phần trở nên nhàm chán, và hằng ngày ta luôn tìm cách để cải thiện nó.

Now, the less exciting part: translating designs into code. We all yearn for ways to make this process less tedious, and AI might just be the answer. Ready to explore?

## Code Generation

When coding, we use a strange language that humans don't use, a kind of mysterious incantation, which is certainly not comfortable, from ancient times:

Then:

![[Pasted image 20231121171409.png]]

Now :

![[Pasted image 20231121171428.png]]

Another challenge of coding is boilerplate code. Boilerplate code is code that is repeated in many places with little or no change. It can be found in all programming languages, but it is particularly common in languages that are considered verbose, such as Java and C++.

![img.png](img.png)

Example:

![[Pasted image 20231121172916.png]]

Boilerplate code can be a major source of frustration for programmers. It can take up a lot of time to write, and it can be difficult to maintain. It can also make code less readable and less maintainable.

There are a number of things that programmers can do to reduce the amount of boilerplate code in their code. One option is to use a code generator. Code generators can automatically generate boilerplate code, which can save programmers a lot of time and effort.

Another option is to use a framework or library. Frameworks and libraries provide pre-written code that can be used to perform common tasks. This can help to reduce the amount of boilerplate code that programmers need to write.

However, these things still seem to be not quite satisfying, as they still leave repetitive lines of incantations that require some thought to understand.

With AI, there is a slight difference. You no longer have to save a bunch of long snippets. I remember the first time I used Copilot. I wrote a comment in human language, and the incantation was created. If I didn't like the result, I could find another result, right there in the code file I was working on, which was very convenient.

But today, it is even more powerful when you no longer need to choose different results. Instead, you can directly provide additional context to Copilot to generate a new code snippet that is closer to your expectations.

![](https://youtu.be/C9Dwm8caoU8)

A very strange prompt, but when provided with a lot of context, such as the position of the mouse, the files that are open, or even upload the file, Copilot can generate a very accurate answer.

Another problem with boilerplate code is that it is difficult to maintain. Although it requires less effort than inheritance, when you need to change a logic somewhere, you have to go find and fix it everywhere. It's not too difficult if you use search/replace. But sometimes the boilerplate needs to be changed a little bit, then at this time only AI can help find it, AI can process the entire codebase to find similar segments and fix them all at once.

There are many levels of code generation. If in the above example we generate from backend code, then below we can generate components for the frontend:

![](https://youtu.be/WbUF6XEk0zI)

Bonus một số tool generate:

1. https://tailwind-ai-generator.vercel.app/tailwind/860
2. https://flutterflow.io/ai-gen
3. https://retool.com/products/ai

## AI giúp viết test

To be honest, I rarely write unittests. It's quite time-consuming and difficult. I only write them when the function is really important and difficult to integration test. I believe there are many developers like me.

Especially with TDD, we have to clearly define what we expect before we code. That's the right thing to do, but to be honest with myself, I would have to estimate an additional 50% before I would dare to practice TDD.

Unittests are like insurance. We only see their value when a bug occurs. When everything is working, we hardly see the benefits. However, unittests are a best practice and are required in enterprise applications.

There is a saying: "Do whatever you don't want to do, let AI do it."

![[Pasted image 20231114135420.png]](https://www.toptal.com/qa/how-to-write-testable-code-and-why-it-matters)

As you saw in the demo, writing unittests is much simpler now than it used to be. Of course, there are still some limitations, but they are acceptable and worth it. So, with the help of AI, I hope that the adoption of TDD will be simpler and more widespread.

![](https://youtu.be/HFJlTDE_vLA)

## AI Helps Write Documentation

We often write code better than we write documentation, even though documentation is an important skill. Like unittests, we don't need documentation for what we've done during the development process, but we only see the value when we need to read it. So we often don't take it seriously, but it is also, once again, a best practice and a policy in enterprise applications. Moreover, writing documentation also helps us to review our system ourselves.

Things we don't want to do, let AI do.

![](https://youtu.be/bKXGut226CA)

The process of writing documentation with AI is not completely automated. Instead, the developer provides guidance and review, while the AI plays the role of reviewer.

Using AI is especially beneficial in cases where documentation needs to be written for an old project or a project that has not been updated for a long time. This is because AI can process the entire codebase and old documentation at the same time, quickly. This makes the process of rewriting the documentation simpler. Copilot allows you to rewrite a selected section, making it easier to edit the content.

## AI Helps Write Commit

![img_1.png](img_1.png)

Looking at this commit, it is very difficult to reverse to the correct error location, not to mention that a commit may contain more changes than it describes. To improve this problem, there are many practices such as conventional commit, or advising continuous commit and small commit. But developers will always be developers.

With AI, it can analyze the results of git diff and create many commands to help divide the changes into the correct commit, commit with more accurate content, thus giving out a beautiful, easy-to-understand and reverse git tree.

![](https://youtu.be/ILFWF2eMuDY)

In this demo, I did two different tasks and forgot to commit. Github Copilot helped me create two separate commits for each change.

However, this is just a simple example. Currently, it still has many limitations, for example, if you make two different changes to the same file, no one can help you. When AI is cheaper and faster, it can process your code in real time, then it can help you in this difficult case.

## Review code

![[Pasted image 20231117135349.png]]

This is a best practice in software development. After passing the testcases, lint rules, the logic cannot be reviewed by the rules. But it is also an important part of the codebase. Code review helps ensure the healthy of the codebase over time[^2].

If anyone has ever done code review, they might agree that code review is quite difficult. The hardest part is how to balance between personal opinion and the healthy of the codebase. We often tend to see our own practices as better, and the logic we don't understand, or is confusing with the way we think is bad. But the problem is that sometimes it is right, sometimes it is wrong.

![[Pasted image 20231115093835.png]]

AI does not have such feelings. Even though it has bias, we can provide our policy for it under the prompt to force it to follow, so the review will be less subjective.

I create an assistant on OpenAI. and provide it with system prompts and some files about Google's code review[^3] for retrieval as follows:

![[Pasted image 20231115103147.png]]

I will try to copy a random text on the internet to ask it to review, in fact, we will use code changes in the commit. I will use the following code:


```go
func DiscountEdit(ctx context.Context, shopID int64, discountEdit *model.DiscountEdit, repo *repository.MongodbRepository) error {

	order, mcaDirectPurchase, err := lambda_func.GetOrderDetails(ctx, shopID, discountEdit.OrderID)
	if err != nil {
		if strings.Contains(err.Error(), "order not found") {
			return nil
		}
		return errors.Wrap(err, "failed to get order details")
	}

	sales := ConvertDiscountEditToSaleReports(*discountEdit, *order, mcaDirectPurchase)
	//if err != nil {
	//	return errors.Wrap(err, "failed to convert order refund to sale reports")
	//}
	if len(sales) == 0 {
		return nil
	}

	err = repo.SaveItemNew(ctx, sales)
	if err != nil {
		return errors.Wrap(err, "failed to insert OrderEdit to sell report")
	}
	return nil
}
```

Here is the output:

![[Pasted image 20231115111038.png]]
![[Pasted image 20231115111238.png]]
![[Pasted image 20231115112137.png]]
Personally, I think the results are very good. Although lint tools are necessary to analyze code, if they can be combined with AI, the results will be more valuable. For example, in this demo, it is something that lint tools are difficult to do:

![[Pasted image 20231115112224.png]]
But it is very meaningful, it reminds us of business. Is the definition of currencyRate really correct, or perhaps our purpose is not currencyRate but something else.

## AI giúp bảo trì hệ thống cũ

There is a joke that we quit our jobs to escape the legacy code we created to swim in the legacy code that someone else just left. The joke is true, we are always afraid of legacy code, whether it is ours or someone else's. Especially if it is a codebase that violates all of the above, no documentation, unclear design, messy commits.

AI can help, in this case it is similar to when AI supports writing documentation, using AI to index the entire codebase, and can answer and analyze any piece of code in the codebase, you ask it how to deploy, or run a service, it will return the necessary commands to you without having to fumble around or wait for someone to ask.

However, to be like that, it may need a more complete solution, because besides the codebase, it also needs to index requirements, issues, changelogs, etc.

![](https://youtu.be/upV8znS-HU4)

Currently, it is not very convenient, you have to provide some files for context yourself, and you cannot access all the documentation related to the project and the codebase. However, GitHub is developing GitHub Copilot for enterprise to support this capability.

## AI-Powered Command Line Assistance

Writing command line is probably one of the first areas supported by OpenAI when it was founded. It is not as complex as generating code, simpler and the context is shorter but more necessary, because most terminals do not support autocompelte like IDE.


![[Pasted image 20231115094106.png]]

Most recently, we have GitHub Copilot for cli. but it is still simple and the usage is complicated. Warp is a terminal with features like an editor, supports AI very smoothly, let's take a look at the example below.

![[demo_warp.mp4]]
However, when running cli, you should be careful, because if you do not fully understand what the command is running, it can easily lead to unfortunate mistakes. For example, if you ask AI to remove a directory and it returns the following command, it will be troublesome:

```shell
rm -rf /
```

## Challenges and Considerations

Even though AI has its limits and conveniences, like any other wave, the use of AI and the development of AI-supporting tools also raise many controversies and concerns.

### Reliance on AI

**Dependency:** The main concern is that developers can become too dependent on AI. This dependency can make developers less skilled at writing code, because developers can rely on AI's suggestions without understanding the basic logic.

**Loss of creativity:** Reliance on AI to code can limit the creativity of developers. The solutions provided by AI tend to be based on existing patterns, if developers are only satisfied with the results, it can hinder the creation of new solutions.

### Security and privacy

Another issue is the issue of security. There are many levels of concern for this, when the entire code base is indexed and sent to the OpenAI server, it is not certain whether it will be used for other purposes or not. With this concern, many companies are moving towards using open source models and building policies for the use of AI.

In addition, AI can be injected. For example, you parse the content of a website, and the website quietly inserts some segments to inject inappropriate context into your prompt, causing AI to provide unwanted results.

When AI explodes, every company wants to share, many companies disregard the privacy of users, and may use user data to train their models. This information can be generated for other users, leading to many privacy concerns.

### Outlook on the future

One of the limiting factors of current LLMs is probably compute. These models all require massive computing power to train, fine-tune, and infer. So currently there is still no model that can process data and update the model in real time.

But with the current development and investment, these limits are being broken every day, in terms of both the size of the model and the fine-tuning techniques and resource optimization. Hardware companies also have their own improvements.

Whether we want it or not, the development of AI is an inevitable thing. When something new develops, it will replace the old, and perhaps the way we program in 2 years will be very different from the way we are coding now. Adaptation is a must, but it does not mean losing your skills. Instead, keep training your wings and attach the right tools to them to fly faster and higher.

For businesses, they should have a positive outlook and invest more in AI in parallel with developing new skills for employees. By restructuring itself, Github is fully focused on AI, as well as the trend of FANG companies, we can see that AI will be one of the important factors for competition in the future. Slowing down in this field can lose many advantages. Proper and correct application of AI into daily workflows can bring significant improvements. Parallel to that is developing policies to ensure security and privacy issues.

## Conclusion

In this article, we understand more about Gen AI and a little bit about the concepts of context and parameter. We can see that sometimes, simple goals can lead to wide applications. But its limitations are that it uses too many resources, and the output still has a lot of illusions and bias. But with the current development and investment, these limits are being broken every day. The future of a natural programming language that can repair itself is not far off. AI will be a step change that no one can stand outside of.

![[Pasted image 20231121171845.png]]

## Footnotes

[^1]: [Scaling Laws of Large Language Models: Parameters vs Tokens - Sarvex Jatasra
](https://www.linkedin.com/pulse/scaling-laws-large-language-models-parameters-vs-tokens-jatasra-p0ogf/)
[^2]: [Google Eng Practice](https://google.github.io/eng-practices/)
[^3]: [Styleguide repo](https://github.com/google/styleguide)
