---
title: "How Drasi used GitHub Copilot to find documentation bugs"
url: "https://opensource.microsoft.com/blog/2026/04/09/how-drasi-used-github-copilot-to-find-documentation-bugs/"
date: "Thu, 09 Apr 2026 15:05:00 +0000"
author: "Aman Singh"
feed_url: "https://azure.microsoft.com/en-us/blog/feed/"
---
<p class="wp-block-paragraph">For early-stage open-source projects, the “Getting started” guide is often the first real interaction a developer has with the project. If a command fails, an output doesn’t match, or a step is unclear, most users won’t file a bug report—they will just move on.</p>



<p class="wp-block-paragraph">Drasi, a CNCF sandbox project that detects changes in your data and triggers immediate reactions, is supported by our small team of four engineers in Microsoft Azure’s Office of the Chief Technology Officer, and we move fast. We have comprehensive tutorials, but we are shipping code faster than we can manually test them.</p>



<p class="wp-block-paragraph">Detect and react to your first database change using Drasi<br />The team didn’t realize how big this gap was until late 2025, when GitHub updated its Dev Container infrastructure, bumping the minimum Docker version. The update broke the Docker daemon connection—and every single tutorial stopped working. Because we relied on manual testing, we didn’t immediately know the extent of the damage. Any developer trying Drasi during that window would have hit a wall.</p>



<p class="wp-block-paragraph">This incident forced a realization: with advanced AI coding assistants, documentation testing can be converted to a monitoring problem.</p>



<p class="wp-block-paragraph">The problem: Why does documentation break?<br />Documentation usually breaks for two reasons:</p>



<ol class="wp-block-list">
<li class="wp-block-list-item">The curse of knowledge<br />Experienced developers write documentation with implicit context. When we write “wait for the query to bootstrap,” we know to run <code>drasi list query</code> and watch for the <code>Running</code> status, or even better—run the <code>drasi wait</code> command. A new user has no such context. Neither does an AI agent. They read the instructions literally and don’t know what to do. They get stuck on the “how,” while we only document the “what.”</li>



<li class="wp-block-list-item">Silent drift<br />Documentation doesn’t fail loudly like code does. When you rename a configuration file in your codebase, the build fails immediately. But when your documentation still references the old filename, nothing happens. The drift accumulates silently until a user reports confusion.</li>
</ol>



<p class="wp-block-paragraph">This is compounded for tutorials like ours, which spin up sandbox environments with Docker, k3d, and sample databases. When any upstream dependency changes—a deprecated flag, a bumped version, or a new default—our tutorials can break silently.</p>



<p class="wp-block-paragraph">The solution: Agents as synthetic users<br />To solve this, we treated tutorial testing as a simulation problem. We built an AI agent that acts as a “synthetic new user.”</p>



<p class="wp-block-paragraph">This agent has three critical characteristics:</p>



<p class="wp-block-paragraph">It is naïve: It has no prior knowledge of Drasi—it knows only what is explicitly written in the tutorial.<br />It is literal: It executes every command exactly as written. If a step is missing, it fails.<br />It is unforgiving: It verifies every expected output. If the doc says, “You should see ‘Success’”, and the command line interface (CLI) just returns silently—the agent flags it and fails fast.<br />The stack: GitHub Copilot CLI and Dev Containers<br />We built a solution using GitHub Actions, Dev Containers, Playwright, and the GitHub Copilot CLI.</p>



<p class="wp-block-paragraph">Our tutorials require heavy infrastructure:</p>



<p class="wp-block-paragraph">A full Kubernetes cluster (k3d)<br />Docker-in-Docker<br />Real databases (such as PostgreSQL and MySQL)<br />We needed an environment that exactly matches what our human users experience. If users run in a specific Dev Container on GitHub Codespaces, our test must run in that same Dev Container.</p>



<p class="wp-block-paragraph">The architecture<br />Inside the container, we invoke the Copilot CLI with a specialized system prompt (view the full prompt here):</p>



<p class="wp-block-paragraph">A screen shot of a computer terminal:</p>



<p class="wp-block-paragraph">bash</p>



<p class="wp-block-paragraph">copilot -p &#8220;$(cat prompt.md)&#8221; \<br />&#8211;allow-all-tools \<br />&#8211;allow-all-paths \<br />&#8211;deny-tool &#8216;fetch&#8217; \<br />&#8211;deny-tool &#8216;websearch&#8217; \<br />&#8211;deny-tool &#8216;githubRepo&#8217; \<br />&#8211;deny-tool &#8216;shell(curl *)&#8217; \</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: plain; title: ; notranslate">
# ... additional deny-tool flags 
</pre></div>


<p class="wp-block-paragraph">&#8211;allow-url localhost \<br />&#8211;allow-url 127.0.0.1<br />This prompt using the prompt mode (-p) of the CLI agent gives us an agent that can execute terminal commands, write files, and run browser scripts—just like a human developer sitting at their terminal. For the agent to simulate a real user, it needs these capabilities.</p>



<p class="wp-block-paragraph">To enable the agents to open webpages and interact with them as any human following the tutorial steps would, we also install Playwright on the Dev Container. The agent also takes screenshots which it then compares against those provided in the documentation.</p>



<p class="wp-block-paragraph">Security model<br />Our security model is built around one principle: the container is the boundary.</p>



<p class="wp-block-paragraph">Rather than trying to restrict individual commands (a losing game when the agent needs to run arbitrary node scripts for Playwright), we treat the entire Dev Container as an isolated sandbox and control what crosses its boundaries: no outbound network access beyond localhost, a Personal Access Token (PAT) with only “Copilot Requests” permission, ephemeral containers destroyed after each run, and a maintainer-approval gate for triggering workflows.</p>



<p class="wp-block-paragraph">Dealing with non-determinism<br />One of the biggest challenges with AI-based testing is non-determinism. Large language models (LLMs) are probabilistic—sometimes the agent retries a command; other times it gives up.</p>



<p class="wp-block-paragraph">We handled this with a three-stage retry with model escalation (start with Gemini-Pro, on failure try with Claude Opus), semantic comparison for screenshots instead of pixel-matching, and verification of core-data fields rather than volatile values.</p>



<p class="wp-block-paragraph">We also have a list of tight constraints in our prompts that prevent the agent from going on a debugging journey, directives to control the structure of the final report, and also skip directives that tell the agent to bypass optional tutorial sections like setting up external services.</p>



<p class="wp-block-paragraph">Artifacts for debugging<br />When a run fails, we need to know why. Since the agent is running in a transient container, we can’t just Secure Shell (SSH) in and look around.</p>



<p class="wp-block-paragraph">So, our agent preserves evidence of every run—screenshots of web UIs, terminal output of critical commands, and a final markdown report detailing its reasoning like shown here:</p>



<h1 class="wp-block-heading" id="drasi-getting-started-tutorial-evaluation">Drasi Getting Started Tutorial Evaluation</h1>



<h2 class="wp-block-heading" id="environment">Environment</h2>



<ul class="wp-block-list">
<li class="wp-block-list-item">Timestamp: 2026-02-20T13:32:07.998Z</li>



<li class="wp-block-list-item">Directory: /workspaces/learning/tutorial/getting-started</li>
</ul>



<h2 class="wp-block-heading" id="step-1-setup-drasi-environment">Step 1: Setup Drasi Environment</h2>



<ul class="wp-block-list">
<li class="wp-block-list-item">Skipped as per instructions (already in DevContainer).</li>



<li class="wp-block-list-item">Verified environment setup by checking <code>resources</code> folder existence.</li>
</ul>



<h2 class="wp-block-heading" id="step-2-create-postgresql-source">Step 2: Create PostgreSQL Source</h2>



<ul class="wp-block-list">
<li class="wp-block-list-item">Command: <code>drasi apply -f ./resources/hello-world-source.yaml</code></li>
</ul>



<p class="wp-block-paragraph">………………………………<br />………… more steps ……….<br />………………………………</p>



<h3 class="wp-block-heading" id="scenario-1-hello-world-from">Scenario 1: hello-world-from</h3>



<ul class="wp-block-list">
<li class="wp-block-list-item">Initial check: “Brian Kernighan” present. (Screenshot: <code>09_hello-world-from.png</code>)</li>



<li class="wp-block-list-item">Action: Insert ‘Allen’, ‘Hello World’.</li>



<li class="wp-block-list-item">Verification: “Allen” appeared in UI. (Screenshot: <code>10_hello-world-from-updated.png</code>)</li>



<li class="wp-block-list-item">Result: <strong>PASSED</strong></li>
</ul>



<p class="wp-block-paragraph">……………………………………………………<br />….. more validation by playwright taking screenshots …..<br />……………………………………………………</p>



<h2 class="wp-block-heading" id="conclusion">Conclusion</h2>



<p class="wp-block-paragraph">The tutorial instructions were clear and the commands executed successfully. The expected behavior matches the actual behavior observed via the Debug Reaction UI.</p>



<h2 class="wp-block-heading" id="status-success">STATUS: SUCCESS</h2>



<p class="wp-block-paragraph">These artifacts are uploaded to the GitHub Action run summary, allowing us to “time travel” back to the exact moment of failure and see what the agent saw.</p>



<p class="wp-block-paragraph">Screenshot of Agents report output in a folder with other files.<br />Parsing the agent’s report<br />With LLMs, getting a definitive “Pass/Fail” signal that a machine can understand can be challenging. An agent might write a long, nuanced conclusion like:</p>



<p class="wp-block-paragraph">To make this actionable in a CI/CD pipeline, we had to do some prompt engineering. We explicitly instructed the agent:</p>



<p class="wp-block-paragraph">In our GitHub Action, we then simply grep for this specific string to set the exit code of the workflow.</p>



<p class="wp-block-paragraph">Simple techniques like this bridge the gap between AI’s fuzzy, probabilistic outputs and CI’s binary pass/fail expectations.</p>



<p class="wp-block-paragraph">Automation<br />We now have an automated version of the workflow which runs weekly. This version evaluates all our tutorials every week in parallel—each tutorial gets its own sandbox container and a fresh perspective from the agent acting as a synthetic user. If any of the tutorial evaluation fails—the workflow is configured to file an issue on our GitHub repo.</p>



<p class="wp-block-paragraph">This workflow can optionally also be run on pull-requests, but to prevent attacks we have added a maintainer-approval requirement and a <code>pull_request_target</code> trigger—which means that even on pull-requests by external contributors, the workflow that executes will be the one in our main branch.</p>



<p class="wp-block-paragraph">Running the Copilot CLI requires a PAT token which is stored in the environment secrets for our repo. To make sure this does not leak, each run requires maintainer approval—except the automated weekly run which only runs on the <code>main</code> branch of our repo.</p>



<p class="wp-block-paragraph">What we found: Bugs that matter<br />Since implementing this system, we have run over 200 “synthetic user” sessions. The agent identified 18 distinct issues including some serious environment issues and other documentation issues like these. Fixing them improved the docs for everyone, not just the bot.</p>



<p class="wp-block-paragraph">Implicit dependencies: In one tutorial, we instructed users to create a tunnel to a service. The agent ran the command, and then—following the next instruction—killed the process to run the next command.<br />The fix: We realized we hadn’t told the user to keep that terminal open. We added a warning: “This command blocks. Open a new terminal for subsequent steps.”<br />Missing verification steps: We wrote: “Verify the query is running.” The agent got stuck: “How, exactly?”<br />The fix: We replaced the vague instruction with an explicit command: <code>drasi wait -f query.yaml</code>.<br />Format drift: Our CLI output had evolved. New columns were added; older fields were deprecated. The documentation screenshots still showed the 2024 version of the interface. A human tester might gloss over this (“it looks mostly right”). The agent flagged every mismatch, forcing us to keep our examples up to date.<br />AI as a force multiplier<br />We often hear about AI replacing humans, but in this case, the AI is providing us with a workforce we never had.</p>



<p class="wp-block-paragraph">To replicate what our system does—running six tutorials across fresh environments every week—we would need a dedicated QA resource or a significant budget for manual testing. For a four-person team, that is impossible. By deploying these Synthetic Users, we have effectively hired a tireless QA engineer who works nights, weekends, and holidays.</p>



<p class="wp-block-paragraph">Our tutorials are now validated weekly by synthetic users—try the Getting Started guide yourself and see the results firsthand. And if you’re facing the same documentation drift in your own project, consider GitHub Copilot CLI not just as a coding assistant, but as an agent—give it a prompt, a container, and a goal—and let it do the work a human doesn’t have time for.</p>
<p>The post <a href="https://opensource.microsoft.com/blog/2026/04/09/how-drasi-used-github-copilot-to-find-documentation-bugs/">How Drasi used GitHub Copilot to find documentation bugs</a> appeared first on <a href="https://azure.microsoft.com/en-us/blog">Microsoft Azure Blog</a>.</p>
