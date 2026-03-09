# StudentClaw

[中文](README.md)

> A human-powered execution platform with WeChat-native intake.  
> A graduate student stays in the loop, with `OpenClaw` or other agents used as on-demand reinforcement.

> Unofficial parody project; not affiliated with `OpenClaw`, `OpenAI`, `WeChat`, or related platforms. See the disclaimer below.

## Product Overview

`StudentClaw` is positioned for high-pressure, fragmented, time-sensitive work:  
requests arrive through WeChat, the system prioritizes them, a human execution layer carries the task forward, and external agents are pulled in only when structured generation or automation becomes the better fit.

Typical workloads include:

- research synthesis and information cleanup
- writing refinement and delivery follow-through
- deadline-driven emergency support
- tasks that still need human judgment and human fallback

## Launch Highlights

- **WeChat Native Interface**: tasks arrive through the channel people already use
- **Human Runtime**: the critical path stays human-driven and directly accountable
- **Agent Augmentation**: the operator can call `OpenClaw` or other agents on demand
- **Deadline-Aware Scheduling**: prioritization shifts with urgency, interruptions, and delivery windows
- **Typical Pricing**: commonly `¥400 / month`, with variation by lab, familiarity, and snack policy

## Skills

| Skill | Description | Best For | Agent Escalation |
| --- | --- | --- | --- |
| `Deadline Rescue` | Prioritizes delivery under deadline pressure and pulls the result together fast. | Last-minute drafts, missing materials, final-round edits | Supported |
| `Seen-But-No-Reply` | Detects stalled threads and drags silent tasks back into motion. | Follow-ups, chasing replies, repeated pings | Optional |
| `Advisor Interrupt` | Handles sudden high-priority interruptions by reordering the queue. | Incoming urgent requests, broken schedules | Not needed |
| `Chat-to-Task` | Converts messy chat context into a concrete task list and deliverables. | Fragmented requirements, scattered context | Optional |
| `First-Draft First` | Produces a usable first pass, then tightens it through feedback loops. | Drafting, outlining, explanatory writing | Supported |
| `Human Saturation Fallback` | Switches to external agents when the human execution layer is overloaded. | Bulk rewriting, structured generation, repetitive work | Default on |

## Requirements

| Item | Requirement |
| --- | --- |
| Operating System | A master's student's struggling laptop |
| Task Entry | A working WeChat conversation |
| Required Access | At least one of: `Advisor API` or `Professor API` |
| Optional Boost | `OpenClaw` or another external agent |
| Network | Good enough to send messages and hopefully receive replies |

### How to obtain `Advisor API` / `Professor API`

- This project does **not** ship with `Advisor API` or `Professor API`
- These permissions usually require you to **bring your own lab relationship** or receive access from your research group
- If your environment has neither `Advisor API` nor `Professor API`, many high-priority workflows will not complete end-to-end
- In short: the missing prerequisite is not the bug; the missing documentation was

## Quick Start

1. Make sure you have at least one working privilege: `Advisor API` or `Professor API`  
2. Send the task, context, and delivery requirements through WeChat  
3. Let the routing layer decide priority and execution path  
4. `Student Runtime` handles execution, follow-through, and delivery  
5. Bring in external agents when automation becomes useful  
6. Return results and iterate until the task is closed

## When Local Run Fails

If your first local attempt at `StudentClaw` fails, that usually does not mean the system is down.  
More often, the privileges are incomplete, the context is too messy, or the graduate-student laptop surrendered first.

In the current version, local failure usually falls into one of these buckets:

- no `Advisor API` and no `Professor API`
- WeChat entry works, but the task description is too fragmented to route cleanly
- external agents are unavailable while the human lane is already saturated
- advisor interruption, deadline compression, and fan noise all arrive at the same time

In short, local failure is usually an environment problem, not an installation-technique problem.

## Troubleshooting

| Symptom | Common Cause | Suggested Action |
| --- | --- | --- |
| Crashes immediately on start | Missing `Advisor API` or `Professor API` | Obtain at least one advisor-level privilege first |
| Tasks are sent but nobody moves | The flow got stuck in `Seen-But-No-Reply`, advisor interruption, or deadline pressure | Add missing context or wait for priority to settle |
| Output is painfully slow | Only the human lane is active and the machine is weak | Bring in `OpenClaw` or another external agent |
| Three revision rounds later, still no closure | The chat history is too fragmented and the task was never normalized | Run the equivalent of `Chat-to-Task` before continuing |
| The machine freezes outright | Heat, memory pressure, or morale collapsed first | Lower concurrency and protect the core deliverable |

## Architecture

```text
                           +--------------------------------+
                           | Advisor Interrupts / Deadlines |
                           +---------------+----------------+
                                           |
                                           v
+-----------+     +----------------+     +----------------+     +----------------+
| Requester | --> | WeChat Gateway | --> |  Task Router   | --> | Priority Queue |
+-----------+     +----------------+     +----------------+     +--------+-------+
                                                                         |
                                                                         v
                                                              +-------------------+
                                                              |  Student Runtime  |
                                                              +----+---------+----+
                                                                   |         |
                                      +----------------------------+         +---------------------------+
                                      |                                                          |
                                      v                                                          v
                         +---------------------------+                             +------------------------+
                         | Research / Writing /      |                             |     Agent Adapter      |
                         | Delivery                  |                             +-----------+------------+
                         +-------------+-------------+                                         |
                                       |                                                       v
                                       v                                           +------------------------+
                         +---------------------------+                             | OpenClaw / Other Agents|
                         |      Result Delivery      |                             +-----------+------------+
                         +---------------------------+                                         |
                                                                                              v
                                                                                   +-------------------+
                                                                                   |  Student Runtime  |
                                                                                   +-------------------+
```

### Architecture Notes

| Module | Role |
| --- | --- |
| WeChat Gateway | Receives requests, context, and follow-up instructions |
| Task Router | Classifies work, assigns priority, and selects execution path |
| Priority Queue | Reorders work based on deadlines, urgency, and interruptions |
| Student Runtime | Human execution layer responsible for judgment, handling, and delivery |
| Agent Adapter | External capability layer for `OpenClaw` or other agents |
| Result Delivery | Sends results back, handles revision requests, and closes the loop |

## Comparison with OpenClaw

> This table is a parody positioning comparison. For official `OpenClaw` features, capabilities, and deployment details, refer to its official website and repository.

| Dimension | StudentClaw | OpenClaw |
| --- | --- | --- |
| Product category | Human-backed execution platform | Personal AI Assistant |
| Primary executor | Graduate student + caffeine | Local or self-hosted agent |
| Task entry | WeChat-first | Multi-channel messaging + local control plane |
| Control plane | Task routing, human judgment, and strategic disappearance | Local-first Gateway |
| Extensibility | Human tool use, agent fallback, and last-minute overtime | Tools, skills, routing, and multi-agent workflows |
| Cost structure | Commonly `¥400 / month`, still varying by lab, familiarity, and late-night snack policy | Self-hosted software plus model / deployment costs |
| Failure mode | Seen-but-no-reply, advisor interruptions, deadline compression | Configuration, permission, runtime, and security-policy issues |
| Best fit | High-pressure tasks that need human fallback | Long-running personal AI assistant workflows |

## Plans & Service Level

| Item | Description |
| --- | --- |
| Standard Plan | Commonly `¥400 / month` |
| Pricing Basis | Moves up or down depending on lab, funding mood, relationship quality, and snack expectations |
| Token Policy | Theoretically unmetered, practically limited by how long a human can keep going |
| Response SLA | Fast on a good day, “I saw it” on a bad one |
| Escalation Policy | Brings in `OpenClaw` or other agents when the human layer is cooked |
| Autoscaling | Elastic capacity powered by caffeine, anxiety, and approaching deadlines |

## Use Cases

- delivery windows are short, but full automation is still risky
- someone needs to watch the process, details, and rework
- the request stream already lives in WeChat

## FAQ

### Is this a real product?

No.  
Please do not actually try to place an order.

### Does it actually support WeChat task dispatch?

Within the premise of the joke, yes.  
As a real shipped product feature, no.

### Can I use this without `Advisor API` or `Professor API`?

Not well.  
Some baseline paths may exist, but many critical workflows assume at least one advisor-level permission.

### Where do I get `Advisor API` / `Professor API` access?

The project does not provide it.  
Usually you either bring it yourself, receive it from your lab, or earn it through long-term relationship maintenance.

### Why compare it with `OpenClaw`?

Because most people immediately want to know how this thing is supposed to differ from `OpenClaw`.

### Is this endorsing student exploitation?

No.  
The point is to expose how uncomfortable that logic already is, not endorse it.

## Changelog

### Unreleased

- added a `When Local Run Fails` section
- added a `Troubleshooting` section
- documented `Advisor API` / `Professor API` as hard prerequisites
- normalized pricing language to “commonly `¥400 / month`, with variation”

### `v0.1.0`

- initial public release
- shipped a Chinese-first homepage and a separate English README
- included an ASCII architecture diagram, `OpenClaw` comparison, skills section, and base FAQ

## Disclaimer

`StudentClaw` is fundamentally an entertainment-oriented parody project.

- This repo does **not** provide a real subscription service
- This repo does **not** recruit students, graduate students, or labor of any kind
- This repo does **not** promise deliverables, capability, pricing guarantees, response times, or SLAs
- This repo does **not** endorse exploitative treatment of students, research assistants, or workers
- This repo has **no affiliation** with `OpenClaw`, `OpenAI`, `WeChat`, or any school, institution, organization, or platform
- Third-party names are used only for identification, commentary, parody, or context, and do not imply endorsement, partnership, agency, or official status

If you are looking for an actual product, this is not a purchase page.

## License

This repository is released under the `MIT` license; see `LICENSE` for details.

Please note:

- `MIT` applies only to the original text and code in this repository
- Third-party product names, trademarks, and brand assets remain the property of their respective owners
- If you create a derivative joke or parody, keeping the non-official disclaimer is strongly recommended
