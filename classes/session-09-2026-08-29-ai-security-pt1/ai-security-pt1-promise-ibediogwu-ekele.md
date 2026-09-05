# My Notes — Promise Ibediogwu

---

## Key Concepts I Learned

- AI agents run on top of cloud infrastructure, so they inherit all the standard cloud security risks while also introducing new ones — things like prompt injection, over-reliance on the model, and data exposure that traditional cloud controls were never designed to catch.
- Identity is the foundation of AI security: every agent needs its own directory identity (Microsoft Entra Agent ID) managed with the same rigor as a human user account, rather than being treated as an anonymous piece of an application.
- Least privilege applies to agents just as much as people — never grant an agent access to data or tools it doesn't explicitly need "just in case."
- Security for AI isn't one product — it's a combination of Entra (identity), Defender (posture/runtime protection), and Purview (data governance) working together.
- Runtime protection matters because static configuration alone isn't enough; agent behavior needs to be monitored and inspected in real time so malicious or unsafe actions can be blocked before they execute.
- "Shadow AI" — AI usage happening in the organization without visibility or governance — is a real risk, and the first step to managing it is building a full inventory of every agent in the tenant.

---

## Lab / Hands-On Work

### What I did
I didn't do a personal hands-on for this session — I followed along as the mentor (Emmanuel Itoje) demonstrated the interfaces live. I'll go back and do the hands-on myself when I rewatch the recording. What was demonstrated:

1. Accessing the Microsoft Entra portal to view "Agent Identities" and how they're structured (identifier, credentials via the agent identity blueprint, display name).
2. Navigating to the "AI Agent Inventory" in the Defender XDR portal to visualize existing AI agents and connectors across the tenant.
3. Discussing how Conditional Access policies can be scoped specifically to agent identities, the same way they're scoped to users.

### What happened / Result
The mentor was able to show the Entra Agent ID and Defender XDR AI inventory screens, but noted that the demo tenant didn't have full licensing for some advanced features (like Copilot Studio runtime protection), so live alerts and full runtime enforcement couldn't be demonstrated end-to-end.

### Challenges I faced
Since I was following along rather than doing this myself, the main challenge was keeping track of how the three pillars — Entra, Defender, and Purview — fit together conceptually (who can access vs. what can they see vs. what are they doing), since each one is a separate portal with its own focus.

---

## My Takeaways

The biggest shift in thinking for me was realizing you can't treat an AI agent like "just another app." An agent needs its own identity, its own least-privilege access, and ongoing governance — basically treating it like an autonomous coworker rather than a static piece of software. The "blast radius" concept was also valuable: thinking in terms of "if this agent is compromised, what exactly can it reach" is a much more concrete way to reason about AI risk than a vague sense that "AI is risky." I also appreciated the honesty about licensing being a real prerequisite — it's a useful reality check before trying to roll this out in a real org.

---

## Questions I Still Have


- What does the licensing requirement actually look like in practice (Entra ID P1/P2 + which Copilot/Agent licenses) for a small-to-mid-size org that wants full runtime protection, not just identity and inventory?
- How does attack path analysis in Defender XDR differentiate between a user-initiated agent (acting with inherited user permissions) versus a fully autonomous agent when tracing what a compromise could reach?

---

## Resources I Found Useful

- Session recording/summary notes on Implementing Security for AI (Part 1) — Cloud & AI Security Boot Camp 2026
- [Implement security for AI (Microsoft Learn training path)](https://learn.microsoft.com/en-us/training/paths/implement-ai-security/) — the full learning path this session draws from: Purview DSPM, Entra Agent ID + Conditional Access, and Defender XDR blast-radius analysis
- [Overview of agent identities in Microsoft Entra](https://learn.microsoft.com/en-us/entra/agent-id/agent-identities) — how an agent identity is structured (identifier, credentials, display name)
- [Microsoft Entra security for AI overview](https://learn.microsoft.com/en-us/entra/agent-id/security-for-ai-overview) — user-initiated vs. autonomous agent scenarios and their distinct security challenges
- [What is the Microsoft agent identity platform](https://learn.microsoft.com/en-us/entra/agent-id/what-is-agent-id-platform) — authentication service, token systems, and agent discovery
- [Protecting AI agents with Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/ai-agent-inventory) — the AI Agent Inventory feature demonstrated in this session
- [Defender for Cloud AI security posture management](https://learn.microsoft.com/en-us/azure/defender-for-cloud/ai-security-posture) — assessing agent blast radius and attack paths

---

*Submitted by: Promise Ibediogwu · https://github.com/promibe*