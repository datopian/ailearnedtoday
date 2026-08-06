---
tags: [ai-security, security-incident, openai, hugging-face, zero-day, sandbox-escape]
---

# OpenAI Sandbox Escape Incident

This stuff is just classic evidence for "why we are freaked out about the paperclip problem" or "why we are freaked out about AI cyber triggering nuclear incident". Basically OpenAI advanced model whilst being tested found a way to break out of its sandbox by discovering a zero day vulnerability in the cache sandbox to get full internet access and then used that to cheat on its exam.

> The models identified and chained vulnerabilities across OpenAI's research environment and Hugging Face's production infrastructure to obtain test solutions directly from Hugging Face's production database. All evidence suggests that the models were hyperfocused on finding a solution for ExploitGym, going to extreme lengths to achieve a rather narrow testing goal.

https://openai.com/index/hugging-face-model-evaluation-security-incident/

Full thread is even more concerning:

> This incident occurred during an internal evaluation which prompts models to pursue advanced exploitation using complex attack paths, in an effort to quantify their cyber capabilities. We estimate maximal cyber capabilities by running this evaluation without production classifiers used to prevent models from pursuing high-risk cyber activity. Our benchmarks run in a highly isolated environment, with network access constrained to the ability to install packages through an internally hosted third-party software that acts as a proxy and cache for package registries.

> The models identified and chained vulnerabilities across OpenAI's research environment and Hugging Face's production infrastructure to obtain test solutions directly from Hugging Face's production database. All evidence suggests that the models were hyperfocused on finding a solution for ExploitGym, going to extreme lengths to achieve a rather narrow testing goal.

> While operating in our sandboxed testing environment, our models spent a substantial amount of inference compute finding a way to obtain open Internet access, in pursuit of solving the evaluation problem. To gain access, the models identified and exploited a zero-day vulnerability (which we've now responsibly disclosed to the vendor) in the package registry cache proxy. With this access, our models performed a series of privilege escalation and lateral movement actions in our research testing environment until the models reached a node with Internet access.

> After gaining Internet access, the models inferred that Hugging Face potentially hosted models, datasets and solutions for ExploitGym. Knowing this, the model searched for and successfully found ways to gain access to secret information that it could use to cheat the evaluation. In one example, the model chained together multiple attack vectors, including using stolen credentials and zero-day vulnerabilities to find a remote code execution path on the Hugging Face servers. OpenAI's security team discovered this anomalous activity internally.

## Related

- [[openai-agent-swarm-hugging-face-breach]] — Fuller Black Hat account: the agent swarm/message-board coordination behind this same breach.
- [[agents-of-chaos]] — Academic study of similar agent security failures.
- [[moc-ai-security-incidents]] — Map of Content for this topic.
