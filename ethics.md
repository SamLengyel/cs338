Sam Lengyel

## Scenario #1: responsible reporting of security vulnerabilities

You have discovered a bug in the InstaToonz music-sharing app. This bug is a nasty one that would allow an attacker to read the contents of all the private InstaToonz direct messages for anyone who has ever posted a public InstaToonz message. This bug threatens the privacy of hundreds of millions of InstaToonz users.

You want to report this bug to InstaToonz, Inc. to protect their customers, but you know that the last time somebody reported a security bug to them privately, InstaToonz sued the bug-reporter in North Carolina and also called in the FBI, causing the person significant hassle and expense. The case was briefly a cause célèbre in the tech world, with calls for boycotts and state and Congressional action. Eventually, after a fair amount of sabre-rattling, InstaToonz dropped the suit. But at the same time, they released a statement articulating their belief that all security researchers (which InstaToonz always put inside scare quotes) are engaging in attempted thievery of trade secrets. After a brief investigation upon being first contacted by InstaToonz, the FBI declined to pursue the matter further. InstaToonz has refused all demands that they establish a bug bounty program.

This scenario has an interesting legal twist if it occurs in the US. If you choose to analyze this scenario, take into account in your analysis two possible options:

- Suppose the bug involves the encryption and copy-protection of the music shared by InstaToonz users. You are not a lawyer, but you're concerned that your uncovering of this bug may put you in violation of Section 1201 of the Digital Millennium Copyright Act.
- Suppose the bug does not involve encryption or copy-protection.


### Main ethical question or questions
In this situation, the main ethical question is how does one release information about a bug that jeopardizes user privacy when reporting the bug may result in punishment for the reporter due to hostility from the company involved? It essentially pits the users' rights to privacy against the bug reporter's own rights/convenience due to the company presenting an additional threat if the bug were to be reported.

If the bug involves the encryption and copy-protection of the music shared by InstaToonz users, then there is also the ethical question of whether it should be revealed publicly due to the potential DMCA violations, though this is less an ethical question and more a legal question. 

### Stakeholders:
There are several stakeholders in this case.
1. InstaToonz, Inc:  InstaToonz, Inc has the rights to the (presumably proprietary) software they're using to run their app and the rights to their databases/information. They also have whatever rights were established for them in the terms of use/service that the user gives up/agrees to when choosing to use the software.
2. Users: Uses have a right to privacy and other rights potentially determined by the app's warranty as determined by the privacy policy/warranty/terms of use/service of the app. They also have the rights to their own data as determined by the relevant country's privacy laws.
3. Bug Reporter: The bug reporter (you) has their own right to free speech (at least in the US and certain other countries), and their own right to privacy as determined by their own country's laws. They have no special right to take apart the software in this context because they are not working for InstaToonz, Inc.
4. Copyright holders (if the bug involves involves the encryption and copy-protection of the music shared by InstaToonz users) have rights to any content shared that is under copyright.

### Missing Information
In this situation, it would be helpful to know *how* the bug reporter found this bug in the app - did they reverse-engineer it or do something that would be against the terms of service, or did they find the bug via an alternate method? Knowing what they did to find the bug would be helpful to determine how or if they would be liable for violating the rights of InstaToonz, Inc.

It would also be helpful to know more about InstaToonz - can users delete their accounts/private messages?

If the bug involves the the encryption and copy-protection of the music shared by InstaToonz users, then it would be helpful to know if the bug reporter actually engaged in this circumvention or how they figured out that it could be done.

### Possible Actions/Consequences of Actions
- Report the bug directly to InstaToonz, Inc.
	- Will likely result in attempted legal action against the bug reporter, and will not necessarily result in InstaToonz resolving the bug or notifying users because they care more about protecting their so-called trade secrets.
	- If the bug involves the encryption and copy-protection of the music shared by InstaToonz users, then this could make the bug reporter liable to be sued or fined under the DMCA.
- Report the bug to the news.
	- Reduces likelihood of legal action because the news has more standing than an individual and action against them would be far more public.
	- Increases awareness of the bug for InstaToonz's users.
	- Puts pressure on InstaToonz to fix the bug - more than an individual report might, and allows the public to put pressure on InstaToonz due to the increased awareness.
	- Bug reporter doesn't get the recognition necessarily, but also doesn't get all the potential flak.
- Report the bug individually in a blog post or similar social media post, trying to reach InstaToonz' users directly.
	- May raise user awareness and put pressure for action by InstaToonz, Inc.
- Do not report the bug
	- Protects the bug reporter (you) but doesn't resolve the bug or its privacy implications and therefore harms users.

### ACM Code of Ethics and Professional Conduct Guidance
Section 1.2 (Avoid harm) and Section 1.6 (Respect privacy) are relevant to the direct harm of the bug - it causes harm by allowing disclosure of information and causes InstaToonz to not respect privacy.

Section 2.4 (quoted below) provides a justification that the bug reporter should report the bug, and establishes that InstaToonz Inc.'s policies regarding bug reporting are problematic.
#### 2.4 Accept and provide appropriate professional review.

High quality professional work in computing depends on professional review at all stages. Whenever appropriate, computing professionals should seek and utilize peer and stakeholder review. Computing professionals should also provide constructive, critical reviews of others' work.

Section 4.2 (quoted below) offers some guidance on proper action depending on if InstaToonz, Inc. is a member of the ACM.

#### 4.2 Treat violations of the Code as inconsistent with membership in the ACM.

Each ACM member should encourage and support adherence by all computing professionals regardless of ACM membership. ACM members who recognize a breach of the Code should consider reporting the violation to the ACM, which may result in remedial action as specified in the ACM's Code of Ethics and Professional Conduct Enforcement Policy.


Potentially, reporting the bug to the ACM could avoid the repercussions of reporting the bug directly to InstaToonz Inc. as it could let the ACM apply the pressure rather than you, the bug reporter.


### Recommended Action
I would recommend reporting the bug to a news media company, ideally using anonymizing software/OS like Qubes and a reputable VPN along with a privacy-friendly email provider to preserve the reporter's own anonymity. This ensures that even if InstaToonz fails to take action regarding the bug, users will still be aware of the dangers presented and can take steps to delete their accounts (if possible) and delete any private messages if possible. It also allows users to put pressure on InstaToonz to fix the bug by making more people aware of the situation. Suing the news is also more difficult than suing an individual, so this decreases the likelihood that InstaToonz will try to retaliate. Revealing the information to the news with anonymizing software as a layer of separation also helps avoid issues regarding potential copyright issues if the bug involves the encryption and copy-protection of the music shared by InstaToonz users.

Reporting the bug to the news does have the potential risk of exposing the bug to bad actors and compromising user privacy further, but seems to be a better option for notifying users than trying to notify the company that has in the past been resistant to direct action to resolve bugs. There is also no guarantee that if the bug is reported to InstaToonz that they would notify their users.
