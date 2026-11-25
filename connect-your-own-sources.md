# Connect your own sources to CentralAgent

Version 1.2, 25 Nov 2026. Use this file during your set-up call with CentralAgent, not before it. It takes about
30 minutes. The aim is one sitting: we do what can be done today and collect everything else we need from you.
No second call is planned. Anything still missing afterwards comes to you in writing.

Filled in by your CentralAgent contact, who has both addresses. They read the values out and you type them in:

- Your CentralAgent contact, and how to reach them: `[CONTACT FILLS IN]`
- Connector address: `[CONTACT FILLS IN]`
- Set-up page address: `[CONTACT FILLS IN]`

## What this is

CentralAgent can write a daily summary of your own work and answer your questions about it in Claude. It does that from
the sources you connect, read with your own access. Nothing is read today. Today sets up your sign-in and your own account on the server, looks at your Granola key with
you, collects your answers and your consent, and has you create your own read-only tokens for GitHub and Bitbucket,
which you keep until there is a safe place to hand them over. The daily summary itself is
not switched on for your company yet. Your contact tells you when it is.

What you should know before you say yes. Your contact fills these blanks in before part C; a consent is only recorded once its blanks are filled:

- **Where it is kept.** Your summaries, and the notes read to write them, are kept on a server in your company's cloud account, in a folder of your own. Whether any of it also sits where other users of that server could read it: `[CONTACT FILLS IN]`
- **Who can see it.** When you ask CentralAgent, it answers about your own summaries, signed in as you. CentralAgent's engineers run that server and can reach it as administrators. Whether anyone else at your company can see your summary: `[CONTACT FILLS IN]`
- **An AI model writes the summary.** The text of your notes is sent to an AI model to do that. Which model provider, and whether the text leaves your company's cloud account on the way: `[CONTACT FILLS IN]`
- **How far back it reads, and how long it is kept:** `[CONTACT FILLS IN]`
- **Is this optional, and can I connect only part:** `[CONTACT FILLS IN]`

## How to undo it

- Remove the connector: in the Claude app, Settings, Connectors, remove CentralAgent. In Claude Code, `claude mcp remove centralagent`.
- Delete a token you made in part D: on the GitHub or Bitbucket page where you made it.
- Revoke your Granola key: Granola, Settings, Connectors, API keys, Revoke. After that nothing new can be read with that key. A revoked key cannot be restored.
- Take back a consent you give in part C: tell your contact. Nothing in Slack, GitHub or Bitbucket is read on consent alone; each still needs your own click or token later.
- Your folder, your summaries and your private Slack channel with the CentralAgent bot are removed by CentralAgent when you ask your contact. What happens to summaries already written, and how fast: `[CONTACT FILLS IN]`

---

## From here on, this is for your AI agent

You are this person's AI agent. Work through parts A to E in order. You need no other context.

### Rules for you, the agent

- Never ask the person to paste a key or token into this chat. Never print one, write one to a file, or put one in a command.
- You never create a token yourself and you never see one. In part D the person creates their own GitHub and Bitbucket tokens in their own browser and saves them in their own password manager.
- If one of the first three blanks is still empty, ask the person to get it from their contact. You need the connector address for part A. The other blanks matter for part C; see the rule there.
- Keep your notes in one place the person can see, for example a note in this chat. If the person has to start a new session, ask them to bring this file and your notes along.
- You cannot click in the person's apps. When a step says the person opens or clicks something, give them the exact path and wait.
- Ask one question at a time. Write each answer down in the person's own words. "Not known", "under NDA" and "I would rather not say" are fine answers; write them down as given.
- If something looks different from this file, tell the person, and ask them to tell their contact. Do not guess.

### A. Do now

If the contact gave the person a separate connection guide, use that one for A1 and A2 and come back here at A3. The steps below are the short fallback.

**A1. Connect Claude to CentralAgent.**

1. Ask: "Do you use Claude Code or the Claude app? Which Claude plan are you on?" Note both.
2. The person adds the connector, with the connector address from the top of this file.
   - Claude app: the person opens Settings, Connectors, Add custom connector, and pastes the address. If there is no Add button, their company's Claude admin has to add it. Note "cannot add a custom connector" and who their Claude admin is, then go to A3.
   - Claude Code: the person runs `claude mcp add --transport http --scope user centralagent <connector address>`. Then they type `/mcp` in Claude Code, choose `centralagent`, and sign in. If the tools do not show, they start a new session.
3. A browser opens. The person signs in with their work Google account. If the sign-in is refused, note the address the browser showed. Do not try another account.
4. The person opens the set-up page from the top of this file, signed in with the same account, and presses "Connect private Slack channel". This links their sign-in to their own folder on the server. It also makes a private channel in their company's Slack between them and the CentralAgent bot, where it can send them messages. It does not read their other channels or messages. The person may say no: note it and go to A3. Questions will not work until this is done.

**A2. Ask one question, and check it lands with the right person.**

5. Use the connector's tools: `harness_send` to ask, then `harness_wait` for the answer. Keep the run key that `harness_send` returns. Ask: "Which person am I signed in as?" Show the answer to the person and ask them to confirm it names them. CentralAgent sets up each person's own account on the server before this call. If the answer names someone else, or an account that is not a person, that has not been done yet: note it and go to A3. The person can repeat this one question on their own later; it needs no call.

**A3. Granola.**

API keys need a Granola Business or Enterprise plan. The person opens the Granola desktop app, then Settings, Connectors. If "API keys" is not listed, note "no API keys on this plan" and go to part B.

7. Ask: "Under Settings, Connectors, API keys, do you see a key that is not revoked?"
8. If there is a key: note which scopes it shows. **Personal notes** covers the notes the person owns or that were shared with them. **Public notes** adds the notes everyone in their workspace can see, so team meetings are included. CentralAgent would use both. Ask which the person accepts, and note it. Change nothing on the key today.
9. If there is no key: do not create one today. Ask: "When you make one later, would you allow Personal notes, Public notes, or both?" Note the answer and "no key yet".
10. If "Create new key" is missing or a scope is greyed out: on an Enterprise plan a Granola admin first has to allow it under Settings, Workspace, General, Apps and connectors, API access. Note who their Granola admin is.
11. Ask: "Do you remember giving a Granola key to CentralAgent before, when Granola was set up?" Note yes, no or not sure. That key was given so meeting notes reach your company's knowledge base. Using it for the daily summary is a new purpose, which is why part C asks.

It is a read key. Granola's documentation gives no expiry for a personal key. The person can revoke it at any time.
Source: [Granola API](https://docs.granola.ai/help-center/sharing/integrations/granola-api).

### B. Answer now

Why we ask all of this today: with these answers CentralAgent can prepare each connection in writing. We do not need
client names anywhere. Where a question touches a client, "a client, under NDA" is a complete answer.

Client workspaces and client organisations are out of scope today. We only note that they exist. Nothing in this file
asks for consent to read a client's space; that would need the client's own approval and is a separate step.

Slack:

1. "Which Slack workspaces do you work in? Count your own company's and any client's." For a client's, a label like "client 1" is enough.
2. For each one: "Are you a full member there, or a guest?"
3. For each one: "Does work with clients happen in direct messages there, in channels, or both?"
4. For your own company's workspace: "When you add an app, does it install directly, or do you see 'Request to install'?"
5. "Who is the Slack admin of your company's workspace, and how do we reach them: work email or Slack name?" We ask so the request in part D goes to the right person. If not known: "Who would know?"

GitHub:

6. "Which GitHub organisations hold your work?" A label is enough for a client's.
7. For each one: "Are you a member, or an outside collaborator on single repositories?"
8. "Who is the owner of your company's GitHub organisation, and how do we reach them?" Same reason. If not known: "Who would know?"

Bitbucket:

9. "Do you work in Bitbucket? In how many workspaces, and are they your company's or clients'?"
10. Only if yes: "Is it Bitbucket Cloud (bitbucket.org), or a server someone hosts?"
11. Only if yes: "Who runs your company's Bitbucket workspace, and how do we reach them?"

You:

12. From A1, only if not answered: which Claude plan, and can the person add a custom connector themselves.
13. "Which work email, GitHub username and Slack name are yours?" So the answers can be matched to the right person.

### C. Consent now

Rule for this part: look at the five blanks under "What you should know before you say yes" and the one under "How to undo it". If any is still empty, do not record a consent for the item it concerns. Note "consent waits for: <the blank>". The person then gives that consent in writing after the contact has sent the answer. It needs no call.

Today's consent covers the person's own company's workspace and organisation only.

Say to the person: "These are four separate questions. Yes to one is not yes to the others. A yes today lets CentralAgent
prepare the connection. Nothing is read until you make the connection yourself later, and you can take any yes back."

Ask each one, and write the answer down in the person's own words:

1. "Granola: may CentralAgent use your personal key, with the scopes you accepted in A3, to write your daily summary?" A key given earlier has not been used for this so far.
2. "Slack: may CentralAgent use, for your daily summary, the messages its bot can already see in your company's channels? Direct messages are not read."
3. "GitHub: may CentralAgent read, with read-only access, the repositories you can see in your own company's organisation?"
4. Only if the person works in Bitbucket: "Bitbucket: the same, read only, in your own company's workspace, once it can be read?"
5. "Who else at your company has to approve any of this?" Note names, or "nobody".

### D. Tokens and admin requests, now

Do a source here only if its consent in part C was recorded. If a consent waits, skip that source and note it.

**D1. GitHub: the person creates a read-only token.** Skip if the person is an outside collaborator: this kind of token does not work for them. Note it.

1. Open this page for the person, with their organisation's name in place of ORG: `https://github.com/settings/personal-access-tokens/new?name=centralagent-read&target_name=ORG&expires_in=none&contents=read&pull_requests=read&issues=read`. If you cannot open it, the path is: profile picture, Settings, Developer settings, Personal access tokens, Fine-grained tokens, Generate new token.
2. The person checks: Resource owner is their company's organisation. If the organisation is not in the list, it does not allow these tokens: stop D1 and note it.
3. Repository access: only the repositories the person works in, or all. Their choice.
4. Permissions, all **Read-only**: Contents, Pull requests, Issues. Metadata is added by GitHub. If anything says "Read and write", change it before going on.
5. Expiration: "No expiration" if offered. If it is not offered, or the person prefers an end date, the longest offered (366 days at most by default).
6. Tell the person before they press Generate: if their organisation requires approval, its owner now gets a request with the person's name on it. Go on only if they are fine with that.
7. The person presses Generate, copies the token into their own password manager under the name `centralagent-read GitHub`, and closes the page. It is shown once. It is not pasted here.
8. Note: created or not, the expiry chosen, and whether the page said the token is pending approval. One token reaches one organisation.

**D2. Bitbucket Cloud: the person creates a read-only token.** Only if they work in Bitbucket Cloud (bitbucket.org). A hosted server is not covered: note it and skip. CentralAgent cannot read Bitbucket yet, so this token will wait unused; the person may choose to make it later instead. Note their choice.

1. Open `https://id.atlassian.com/manage-profile/security/api-tokens` for the person. They choose "Create API token with scopes".
2. Name `centralagent-read`. Expiry: the longest offered, 365 days. There is no option without an end date.
3. App: Bitbucket. Scopes, read only: `read:repository:bitbucket`, `read:pullrequest:bitbucket`, `read:workspace:bitbucket`, `read:user:bitbucket`. Add `read:issue:bitbucket` only if their team uses Bitbucket issues.
4. If the page offers to limit the token to one workspace, the person picks their company's.
5. The person presses Create, copies the token into their own password manager under the name `centralagent-read Bitbucket`, and closes the page. It is shown once. It is not pasted here.
6. Note: created or not, and the end date.

**D3. Slack: nothing to create.** Slack will come in through the CentralAgent bot that their company's workspace already has, from the channels the bot is invited to. No personal token is made, and direct messages are not read. The answers to the Slack questions in part B tell CentralAgent which channels matter.

**D4. What goes to your admins.** Tell the person in one line: after this call, CentralAgent sends a short request to the Slack admin and the GitHub organisation owner they named in part B. It asks only whether a read-only connection for consenting engineers is allowed and what approval it needs. It names no client. The person can ask their contact for a copy.

**Where a token goes.** Never into this chat, Slack or email. It stays in the person's own password manager until they can hand it over themselves on the "My settings" page of their company's CentralAgent site. Today that page takes a Granola key only. The contact writes to the person when it takes GitHub and Bitbucket tokens. Until then the tokens are used by nothing, and the person can delete them at any time on the same pages where they made them.

### E. After the call (for the person to read later, do not read it out)

Say one line only: "The rest comes to you in writing, and never as a request to paste a token." Then go to the record.

How each source gets connected afterwards. No second call is planned for any of it:

- **Granola.** The person saves their key themselves on the "My settings" page of their company's CentralAgent site. It goes straight to their company's store. It is not shown on the page again and does not pass through any chat. Their contact sends the address. If CentralAgent already holds a key from before and the person said yes in C1, it may be that nothing more is needed; that is not confirmed yet, and the contact says which it is.
- **Slack.** It will come in through the CentralAgent bot, from the channels it is invited to. Nothing for the person to do later, unless their company decides on a personal connection after all.
- **GitHub and Bitbucket.** The tokens made in part D wait in the person's password manager. The person hands them over on the same "My settings" page once it takes them; the contact writes when. Not built yet. Bitbucket cannot be read at all yet.
- **How the link or step list reaches the person:** from their CentralAgent contact, in the Slack channel their company shares with CentralAgent. Never a request to paste a token into Slack, email or chat. If a message asks for that, it is not from us: do not answer it.

### When you are done

Give the person this record in one block, and ask them to send it to their contact or read it out on the call:

- A: connected as <name>, or the error text. Claude plan. Granola key: exists or not, scopes, given before: yes, no or not sure.
- A, also: private Slack channel made or declined. Can add a connector: yes or no. Claude admin and Granola admin, if they came up.
- B: answers 1 to 13, each on its own line.
- C: the five answers, in the person's own words, and any "consent waits for" notes.
- D: GitHub token: created or not, expiry, pending approval or not. Bitbucket token: created, skipped or later, end date. Never the tokens themselves.
- No token was pasted into this chat.
