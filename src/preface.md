# Preface

My name is [MD Ariful Islam Protik](https://github.com/arifulprotik). I work as a software engineer, and outside work I am learning AI engineering on my own. No course, no cohort, no deadline except the ones I set. These files are my personal notes from that learning, published in the open.

I do not learn well from video courses. I pause, I rewind, I lose the thread, and an hour passes with little to show for it. I learn by reading. I read a page, I stop, I reread the paragraph that confused me, I try the idea in code. That pace suits me, so these notes take the form I wish someone had handed me: written chapters I can read slowly and revisit.

Each chapter follows one node of the roadmap at roadmap.sh/ai-engineer. I picked that roadmap because it names tools, libraries, and techniques instead of gesturing at topics. I work through it top to bottom, and every node gets a note here once I have researched it properly.

## Why books, and why notes in public

Reading gives me control a video player never does. I set the speed. I skip what I already know and camp on what I do not. A book also lets me search, copy a snippet into my editor, and check a claim against the docs in another tab. Try doing that with a forty-minute lecture.

Writing is the second half of the method. I have forgotten most of what I only read. The ideas that stayed are the ones I explained back, in my own words, with a working example attached. So each chapter here is written to teach, because teaching is how I check whether I understood anything.

Publishing the notes in the open adds pressure I find useful. A private notebook tolerates vague sentences. A public chapter does not, or at least it should not. If something I wrote is wrong, a reader can point at the exact line. That keeps me honest in a way no study plan taped to a wall ever did.

## How each chapter works

Every note follows the same shape. It opens with learning goals so you know what the chapter promises. Then come the detailed notes, an explanation of how the thing works, and a Python example you can run. After that I list the pitfalls I ran into or found written up elsewhere, then the free resources that taught me the most, and finally a short checklist so you can confirm the knowledge stuck.

The examples are in Python because that is where the AI engineering ecosystem lives: the OpenAI SDK, LangChain, LlamaIndex, Chroma, sentence-transformers. I pin library versions in a comment at the top of each example so the code keeps working as libraries move on. The one exception is Transformers.js, which gets JavaScript, since running models in the browser is the entire point of that library.

## Whose words are these

None of this knowledge is mine. It comes from documentation, articles, papers, and the people who built the tools. My work is collecting it, testing it, and organizing it so I can learn. Every chapter links its sources in the free resources section, and credit belongs there.

## The rules I hold myself to

Nothing here is summarized from memory. If I write about embeddings, I have read the embedding docs, generated actual vectors, and compared retrieval results first. If I describe a failure mode, I either hit it myself or I link the write-up where someone else did.

Every link is free unless it says otherwise. Where a paid resource covers ground no free alternative covers, I mark it paid and say why it is there. I check every link before it goes in. Links rot, so a dead one is a bug worth reporting, same as a wrong code sample.

I also refuse to pad. If a chapter can say its point in eight hundred words, it will not run to two thousand. Your time is scarce, and filler spends it without asking.

## What these notes will not do

I am not an AI researcher, and these notes will not teach you to build models from scratch. It covers what an AI engineer does day to day: call models through APIs, shape their behavior with prompts, give them your own data with retrieval, connect them to tools as agents, and ship the result. That is the job I am training for, and these are the notes from the training.

The notes are published chapter by chapter with mdBook and they are unfinished by design. A checkbox list in the repository tracks which nodes are done and which sit ahead of me. I write one node per session, verify the build, and check it off. You are reading something being built in the open.

Start at chapter zero if the prerequisites are new to you. Otherwise jump to whatever node matches the problem in front of you. Each chapter stands on its own, but they build on each other in roadmap order.
