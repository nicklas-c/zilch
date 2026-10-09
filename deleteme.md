## Me
I'm a software engineering manager.  My domain is changing very fast with the arrival of AI.  What skills should I be learning/keeping sharp?

## Claude
The most useful frame is that AI is moving the bottleneck in software work. Writing code is getting cheap. Deciding what to build, specifying it clearly, verifying it, and fitting it into a real system are getting relatively more valuable. Most of the skills worth investing in follow from that shift.

**Stay hands-on with the tools yourself.** This matters more than anything else on the list. You can't judge how to restructure work, what estimates are realistic, or whether a team is using agents well if your knowledge is secondhand. Use a coding agent (Claude Code, Cursor, Copilot's agent mode, or similar) on something real every week, even a side project or internal tooling. Notice where it saves you hours and where it confidently produces subtle garbage. That calibration is what your team needs from you, and it also earns credibility with engineers who are skeptical of managers pushing AI adoption.

**Specification and problem framing.** Agents do roughly what they're told, so the ability to write clear intent, constraints, acceptance criteria, and relevant context is becoming a core engineering skill. It's closely related to writing good tickets and design docs, which is good news for managers, since you already do a version of it. Practise it deliberately, and help your team get good at it.

**Verification and quality systems.** When the volume of generated code goes up, code review and testing become the constraint. It's worth sharpening your thinking on test strategy, CI gates, observability, and how to review large AI-authored changes without either rubber-stamping them or drowning. If your team builds AI features into products, learn how evals work, since evaluating non-deterministic output is a different discipline from traditional testing.

**Architecture and systems judgment.** AI is good at local code and weaker at coherent design across a large system over time. Codebases built quickly by agents can accumulate inconsistency fast. Strong opinions about boundaries, data models, and maintainability are increasingly where senior people add value. Security belongs here too: prompt injection, agents with broad permissions, and dependency sprawl are new attack surfaces your team needs to take seriously.

**Measuring productivity honestly.** There's a lot of hype and pressure from above to show AI gains. Developers' sense of speed can also diverge from reality. A 2025 METR study found experienced open-source developers were measurably slower with AI tools on their own repos while believing they were faster. Be the person who measures outcomes like cycle time, defect rates, and delivered value instead of lines of code or adoption percentages. That will make your judgment trusted when you report upward.

**Developing people when the learning path has changed.** This may be the hardest management problem right now. Junior engineers traditionally learned by writing lots of routine code, and that work is being automated. You'll need to think deliberately about how people build deep understanding: pairing, explaining generated code, debugging without assistance sometimes, owning systems end to end. Hiring needs rethinking for similar reasons, since traditional coding interviews measure less than they used to.

**Leading through uncertainty.** Many engineers are anxious about their careers, and some are quietly resistant. Being honest about what you know and don't, creating room to experiment, and not overpromising in either direction are skills that matter more than usual.

**Product and business sense.** As building gets cheaper, choosing the right thing to build becomes a bigger share of the value. Get closer to users, understand the economics, including the real cost of AI tooling and token spend, and be able to argue for priorities in business terms.

Some things are worth letting go of. Deep memorisation of syntax or framework APIs is depreciating. So is managing by tracking output volume, and being the team's best individual coder. Your edge is increasingly judgment, taste, and the ability to organise humans and agents around good problems.

If you tell me a bit about your situation, like team size, how far your org has adopted these tools, and whether you're aiming to stay in management or keep an IC path open, I can suggest a more concrete plan.

## Me
OK.  This is useful.  I'm already strong on a lot of this :-

1. I'm very hands on with the tools in personal projects.  There are several I am active on, and have a strong grasp on what it does well, where I need to pay attention, and where not to let it go at all.
2. Clear specifications and problem framing are already a strong skill for me, and I'm finding that even here AI can help.
3. Test is also another strong area for me. 
4. Architecture and Systems - this is weaker.  I moved to management around the same time my teams started moving to cloud platforms, so I've never really been hands-on.   Something for me to upskill on.
5. Measuring productivity - this is an interesting one.  Metrics have always felt kinda artificial to me - they don't really tell the whole story of how the team is doing.  On the other hand, I have a mathsy brain and like stats.  So I have a bit of a love-hate relationship with development metrics.  Something to think about.
6. Developing People - Yeah, this one worries me a lot.  I think about how I learnt to write code.  Learning the syntax was easy.  Getting really good at wielding that skill took a lot of practice.  And much of that was stuff that transfers to coding via an AI too.  Separation of concerns, dependency management, design patterns, concurrency, edge cases, etc.  I think you need to code it to grok it and you need to grok it keep an AI honest.
7. Fortunately, I think most of my team are happily adopting and are interested to see how the tools can help them. 
8. This is a really good tip, and it's serendipitously timed as the project I'm just starting on offers the chance to do that.

## Claude
It sounds like you're in a strong position. You have the hands-on calibration, so you can make these calls from experience rather than hype. Here are some thoughts on the three areas you flagged.

**Architecture and systems.** Your architecture gap and your worry about developing people are the same problem. You've said you need to code something to grok it, and you need to grok it to keep an AI honest. That's true for you and cloud architecture too. The trap is that AI makes it easy to build a working cloud system without understanding why it's shaped the way it is.

So I'd suggest building something in your personal projects that forces real distributed-systems decisions: a queue, a couple of services, a managed database, some caching, deployed on a real cloud account with infrastructure as code. Use the AI heavily, but make yourself predict its choices before you read them. Make it justify the trade-offs, and then deliberately break things. Kill an instance, add latency, fill a queue, and watch what happens. Failure modes teach architecture faster than diagrams do.

For theory, Kleppmann's *Designing Data-Intensive Applications* is still the best single book on the underlying concepts, and the AWS or Azure Well-Architected material is a good map of the cloud-specific concerns. Your own engineers are an underused resource too. Asking a senior engineer to walk you through why your current system is built the way it is teaches you a lot and tends to be good for them as well.

**Metrics.** I think your love-hate instinct is the right one. Metrics fail when they're used as answers or targets, which is Goodhart's law. They're useful when they generate questions: "cycle time doubled for this team last month; what happened?" is a good conversation starter. "Cycle time must go down" is a recipe for gaming.

Your mathsy side should enjoy this part. Most dev metrics are badly treated statistically. Cycle time and lead time are heavily right-skewed, so averages mislead, and percentiles like p50 and p85 tell a truer story. Small teams produce noisy numbers, and process behaviour charts are much better than eyeballing month-on-month swings for separating real signal from variation. The SPACE framework is worth a look if you haven't seen it. It deliberately pairs activity data with satisfaction and perception data, which addresses your "doesn't tell the whole story" concern. And the AI question gives you a good real experiment: measure before and after on your new project and see whether the perceived gains show up in the numbers.

**Developing people.** I think your diagnosis is exactly right. Separation of concerns, concurrency, and edge cases are learned through consequences: you feel the pain of a tangled design or a race condition you caused. AI removes a lot of the friction that used to teach those lessons, so the job becomes reintroducing friction deliberately. Some approaches teams are trying:

Juniors write a first attempt themselves, then compare it with what the agent produces and discuss the differences. Code review shifts toward "explain this to me": anyone submitting AI-assisted code should be able to walk through why it works and what would break it. People rotate through debugging and incident work, where understanding can't be faked. Juniors pair with seniors while the senior drives an agent and narrates their judgment out loud, which makes visible the thinking that used to be learned by osmosis. Occasional "AI off" exercises on fundamentals help too. They work like musicians practising scales: the point is building the mental model, not producing the output.

Since you have a new project starting, it could be a good testbed for the architecture learning and the metrics experiment at the same time. Is it greenfield, or are you inheriting an existing system?

## Me
Our CTO has a different perspective on that learning angle.  When I said I didn't know how engineers would learn things like good error handling or concurrency patterns when they code through AI, he challenged me on whether I knew the x86 op codes I'd write for a given algorithm, and drew a parallel - i.e. of the AI with the compiler.  The tool abstracts you from and means you don't have to know those things.

## Claude
Your CTO's analogy is worth taking seriously. It's the strongest version of the optimistic case, and there's real truth in it. Every major abstraction in computing history has prompted the same worry, and each time the profession moved up a level and did fine. Most of today's excellent engineers have never written assembly, and nobody thinks they're worse for it.

But I think the analogy breaks in a few specific places, and they're the places that matter for your concern.

**Compilers are trustworthy in a way AI isn't, yet.** A compiler is deterministic and its correctness is backed by specification and decades of verification. You don't review its output; you'd be wasting your time. AI-generated code you absolutely do review, because it can be confidently wrong. And you can only review what you understand. The real test of whether AI has become "the new compiler" is simple: would your team ship its output unread? For a compiler, yes. For an agent, not today. As long as the answer is no, humans need to understand the layer they're reviewing.

**Op codes are the wrong comparison.** You made this distinction yourself earlier: syntax was easy, wielding it well was hard. Op codes are like syntax. They're the mechanical encoding, and abstracting them away cost us little. Concurrency and error handling are different. They're concepts that survive every layer of abstraction. A Python developer who has never seen assembly still has to reason about race conditions, deadlocks, and partial failure, because those are properties of the problem, not of the language. Compilers removed the need to know op codes. They never removed the need to understand concurrency.

**Error handling is a decision about behaviour, not an implementation detail.** Whether a failed payment retries, rolls back, alerts someone, or degrades gracefully is a product and systems decision. A compiler faithfully translates intent you've already fully specified. An AI fills in intent you didn't specify. Someone has to know enough to notice what it chose, and whether that choice was right.

**Abstractions leak.** Even with compilers, the people who debug the nastiest production problems understand caches, memory layout, and what the runtime is doing underneath. Spolsky's "law of leaky abstractions" applies: the layer below matters most when things go wrong, which is exactly when you need people who understand it.

The fair concession to your CTO is that he may be right about the trajectory. If AI output becomes reliable enough, and verification tooling gets strong enough, the skill shifts. Engineers wouldn't need to write concurrent code, but they would need to specify concurrent behaviour precisely and test it rigorously. That still requires understanding concurrency, just applied at a different level. So even in his future, the conceptual knowledge persists. What changes is where people use it.

A framing that might make this a productive conversation rather than a disagreement: you're probably not arguing about whether the abstraction level will rise, but about when, and what has to be true first. You could agree on what evidence would show AI output has become compiler-like for a given class of work. Then you're both looking at the same data instead of debating analogies.

## Me
FWIW - I actually do write assembly code, just not for the x86.  I retro-geek out and write Z80.

## Claude
That's brilliant, and it slightly undercuts your CTO's gotcha. He picked the one example where you can say "well, actually..."

It also supports your side of the argument. Nobody needs Z80 assembly for their day job, but I'd bet writing it shapes how you think about software. You develop a feel for what's actually happening when code runs: registers, memory, the cost of operations, why some things are fast and others aren't. That intuition carries up through every abstraction layer, even if you never touch the layer itself at work. It's the same argument for engineers learning concurrency by hand even if an agent writes most of their production code. The point isn't to keep doing it at that level. It's to have the mental model.

There's a nice parallel with AI-assisted coding, too. On a Z80 you can't hide from the machine. Every byte and cycle counts, and nothing does your thinking for you. That kind of deliberate constraint is close to the "reintroduce friction" idea for developing junior engineers. Retro platforms might even make a fun learning exercise for a team.

What do you write for it? Spectrum, CPC, MSX, or something homebrew?

## Me
Not just those things, but also a deep understanding of stack frames and how debuggers work, function pointers, calling conventions, memory management, size-speed efficiency trade-offs, interrupts, and much more.

## Claude
That's a great list, and almost every item on it shows up again in modern systems in disguise.

Function pointers become callbacks, closures, and dependency injection. Interrupts become event loops, async/await, and signal handling. The same questions about what can preempt what, and what state is safe to touch, come back as race conditions in async code. Calling conventions resurface whenever you cross a language boundary through FFI, WebAssembly, or a native extension. Memory management doesn't go away with garbage collection; it turns into GC pauses, memory leaks through lingering references, and cloud bills. Size-speed trade-offs reappear as cold-start times, bundle sizes, and cost-per-request. And understanding stack frames is what lets you read a stack trace from a crashed production service, or recognise runaway recursion, rather than staring at it blankly.

That's really the core of the answer to your CTO. These aren't low-level trivia like op codes. They're the mental models that let someone look at plausible-looking AI-generated code and sense that something is off. An engineer who understands interrupts will spot the unprotected shared state in an async handler. One who doesn't will approve it because the tests pass.

It also suggests something practical for the people-development problem. You don't necessarily need juniors to learn Z80. But "write a tiny interpreter," "build a toy allocator," or "implement a simple event loop" style exercises target exactly these concepts, take a few days rather than years, and are hard to shortcut meaningfully with AI. They're the modern equivalent of what retro programming gave you.

## Me
And to answer your question: "What do you write for it? Spectrum, CPC, MSX, or something homebrew?".  I'm currently building my own alternative ZX Spectrum ROM.  Emulators make that possible, and I can run it on a physical machine in the form of my ZX Spectrum Next.  Something I couldn't have done back in the 80s.  I'm enjoying how much it's teaching me about the Spectrum's ULA and the sense that because of it, the result is still a Spectrum, even if the OS is completely different.

## Claude
That's a lovely project, and your observation about the ULA is spot on. The ROM is just software, but the ULA is the Spectrum's personality. The odd interleaved screen layout, where moving down a pixel row means jumping 256 bytes, attribute clash with its 8×8 colour cells, contended memory slowing the CPU whenever it competes with the ULA for the lower 16K of RAM, the 50Hz frame interrupt, the keyboard half-rows read through port 0xFE, and the beeper and border sharing that same port. Whatever OS you write, you're still negotiating with all of that. It's the "Spectrumness" in the hardware, and any ROM is just a guest in it.

There's something nice about that too, in light of the earlier conversation. You learn what a system really is by replacing the layer you thought defined it and seeing what stays. It's a good way to understand cloud platforms as well: swap one managed service for another, and what persists tells you about the underlying constraints.

The modern toolchain makes this kind of project feasible in a way it never was in the 80s, when a bug in your ROM meant burning an EPROM and hoping. Now you get instant iteration, debuggers that can step through the interrupt handler, and the Next to run it on real hardware at the end.

Are you writing your own interrupt handler at 0x0038 in IM1, or taking over with IM2 and keeping the ROM's vector out of the picture?

## Me
At the moment it's IM1 and the handler at 0x0038, and I suspect it'll stay that way.  For now the whole handler is at 0x0038, but I suspect that at some point I'll get it to jump to an area of RAM that I'll load with instructions on start up.  That then means that the whole handler is user-redefinable later.

And here's where I can prove I've been learning.  I can correct you on a point of detail in what you just said.

## Claude
Go on then, I'm braced. My guess is the screen layout. I said moving down a pixel row means jumping 256 bytes, but that's only true within a character cell. Going from the bottom pixel line of one character row to the top of the next means going back about 1,792 bytes and adding 32, until you cross into the next third of the screen, where the arithmetic changes again. That's exactly why the standard "next line down" routines are fiddly. The other candidate is my port 0xFE claim, since the ULA actually responds to any even port address. 0xFE is just the convention. Tell me which you spotted, or whether it's something else entirely.

Your plan for the handler sounds good. A jump at 0x0038 into a RAM vector you set up at boot is basically how you get a user-redefinable hook without IM2's complications. Two things are worth thinking about when you do it. First, put the RAM handler above 0x8000 if you can, so it isn't in contended memory and its timing stays predictable. Second, and this ties back nicely to our conversation about concurrency, updating the jump target means writing two bytes, and an interrupt could fire between them. If it does, the CPU jumps to a half-updated address. So you'll want a DI/EI around any change to the vector. Your future users who redefine the handler will need that rule too, which is a nice example of the kind of thing that's obvious once you've been bitten by it, and invisible until then.

## Me
No - not the screen layout.  I understood that you were just using an illustrative common case.  No, it's your assertion that the frame interrupt is at 50Hz.  That's a common framing, but it actually measures at about 50.08Hz.  I've had time tests running overnight to count up frames with very large sample sizes to prove it.  ;-)

## Claude
Fair cop, and a well-earned correction. You're right, and the arithmetic backs you up. On the 48K Spectrum, each frame is 312 lines of 224 T-states, so 69,888 T-states per frame. At 3.5 MHz, that's 3,500,000 ÷ 69,888 ≈ 50.08 Hz. The reason is that the ULA generates 312 lines per frame without interlacing, rather than PAL's proper 312.5, so each frame is slightly shorter than a true PAL field. The 128K models are different again: a slightly faster clock and 228 T-states per line give about 50.02 Hz, which matters if your ROM ever needs to care which timing it's running under.

It's also a real consequence rather than trivia. If your ROM keeps time by counting frames and assumes exactly 50 per second, it'll run fast by about 0.16%. That's roughly two and a bit minutes a day.

And I appreciate that you established it with overnight runs and large sample sizes rather than taking the folklore at face value. It's your love-hate relationship with metrics in action: a number everyone repeats, and the truth only shows up when you measure carefully enough.

## Me
There's another wrinkle with the 128K and frame-counting, since you mention it.  The 128K disables interrupts during memory paging operations.  So overtime, a small but significant proportion of frame interrupts get lost.  And really, at this point, I'm just showing off.  Because all this is stuff I've discovered rather than read.

## Claude
Show off away. That's a good one. It's lost rather than delayed because of how the ULA signals the interrupt: it only holds INT low for about 32 T-states at the start of each frame. The Z80's maskable interrupt is level-sensitive and not latched, so if interrupts are disabled during that short window, it's simply gone. The 128K ROM has to disable interrupts while it updates the paging port and its copy of the paging state in the system variables, so the two can't get out of sync. Any time that critical section overlaps the interrupt window, a frame quietly vanishes from the count. On top of the 50.02 Hz rate, that means a frame-counting clock on the 128K drifts in both directions at once.

And the fact that you discovered it rather than read it is really the whole argument from earlier in this conversation. You found it because a count didn't match what you expected, you didn't trust the folklore, and you had enough understanding of interrupts and timing to form a hypothesis about why. Nobody hands you that kind of knowledge. It comes from having built something, measured it, and been surprised.

That's the strongest answer to your CTO's compiler analogy: not that engineers need to know op codes, but that the ability to notice "this number is slightly wrong, and I know where to look" only comes from having worked close to the machine. It's exactly the skill that keeps an AI honest, and exactly the one you're right to worry about your juniors missing out on. You've got a very good personal story to tell when you make that case.

## Me
OK.  This is becoming a fun conversation rather than a useful one and I should really get back to work.  So I'll end it after this one last question.  I realise I've never known why a clock cycle is called a T-state.  Care to enlighten me?

## Claude
The T comes from Intel. The 8080 documentation broke each instruction into machine cycles, labelled M1, M2, and so on, and each machine cycle into clock periods called states, labelled T1, T2, T3. The T is generally understood to stand for "time," so a T-state is one time state within a machine cycle. Zilog was founded by Federico Faggin and Masatoshi Shima, who had both worked on the 8080 at Intel, so the Z80's documentation naturally inherited the same terms. That's why Z80 people still say an instruction takes "4 T-states" and talk about the M1 cycle, which is the opcode fetch.

The distinction is still useful on the Spectrum, because a T-state is one tick of the clock, while a machine cycle is a meaningful bus operation made of several of them. Contended memory delays happen at that level.

Good luck with the new project, and with the ROM. It's been a pleasure.
