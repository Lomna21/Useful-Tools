# **🏷️ Tags**
Tags are useful for categorizing notes

```Markdown
#kafka 
#backend/clojure
```

> [!NOTE]- Example for tags
>
#kafka 
#backend/clojure

# **📝 Comments**
Obsidian supports comments that don’t appear in rendered notes:
- These comments won't appear in Reading View.
- Useful for leaving yourself reminders.
- Shortcut key --> `⌘ + /`

```Markdown
%% This is an internal comment. %%
```

%% This is an internal comment. %%


# **🧩 Nested Pages / Note Organization**
Instead of making huge notes in single file we should have something like.

```Plain text
Kafka/
├── Kafka Overview.md
├── Kafka Architecture.md
├── Kafka Producer.md
├── Kafka Consumer.md
├── Kafka Consumer Groups.md
├── Kafka Topics.md
└── Kafka Troubleshooting.md
```
Then connect them:
```Markdown
# Kafka

## Concepts
- [[Kafka Architecture]]
- [[Kafka Producer]]
- [[Kafka Consumer]]
- [[Kafka Consumer Groups]]
- [[Kafka Topics]]
```


# **🏷️ YAML Frontmatter / Properties**
This have to be added top of the file

```YAML
---
title: Kafka
type: learning
status: in-progress
tags:
  - backend
  - kafka
created: 2026-09-24
sources:
---
```
This is called frontmatter. Obsidian also exposes these as Properties

Useful Properties:
```
---
title:
type:
status:
tags:
created:
updated:
source:
---
```




