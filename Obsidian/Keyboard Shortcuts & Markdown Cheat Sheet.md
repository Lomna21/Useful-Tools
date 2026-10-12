## **1. 🚀 Most Useful Obsidian Hotkeys**

`⌘` = Command · `⌥` = Option · `⌃` = Control · `⇧` = Shift

| **Action**                                                                             | **macOS**       | **Windows/Linux**  |
| -------------------------------------------------------------------------------------- | --------------- | ------------------ |
| Open Command Palette                                                                   | `⌘ + P`         | `Ctrl + P`         |
| Quick Switcher (Obsidian will search your notes and let you jump directly to the note) | `⌘ + O`         | `Ctrl + O`         |
| Create new note                                                                        | `⌘ + N`         | `Ctrl + N`         |
| Open search                                                                            | `⌘ + Shift + F` | `Ctrl + Shift + F` |
| Search current note                                                                    | `⌘ + F`         | `Ctrl + F`         |
| Replace in current note                                                                | `⌘ + Opt + F`   | `Ctrl + H`         |
| Save                                                                                   | `⌘ + S`         | `Ctrl + S`         |
| Undo                                                                                   | `⌘ + Z`         | `Ctrl + Z`         |
| Redo                                                                                   | `⌘ + Shift + Z` | `Ctrl + Shift + Z` |
| Close current tab                                                                      | `⌘ + W`         | `Ctrl + W`         |
| Reopen closed tab                                                                      | `⌘ + Shift + T` | `Ctrl + Shift + T` |
| Toggle edit/reading mode                                                               | `⌘ + E`         | `Ctrl + E`         |
| Open settings                                                                          | `⌘ + ,`         | `Ctrl + ,`         |
| Open help                                                                              | `⌘ + ?`         | `Ctrl + ?`         |
| Navigate back                                                                          | `⌘ + Alt + ←`   |                    |
| Navigate forward                                                                       | `⌘ + Alt + →`   |                    |
| Move line up                                                                           | `⌥ + ↑`         |                    |
| Move line down                                                                         | `⌥ + ↓`         |                    |
| Insert Markdown Link                                                                   | `⌘ + K`         |                    |
| Insert callout                                                                         | `⌥ + C`         |                    |

# **2. ✍️ Basic Text Formatting**
We **don’t need to memorize the syntax**. In Obsidian, we can also use the **Command Palette** (`⌘ + P`) and search for any command (eg.: table-related commands).

```Markdown
Bold          --> **This is bold** --> ⌘ + B
Italic        --> *This is italic* --> ⌘ + I
Bold & Italic --> ***Bold and italic*** --> ⌘ + B and then ⌘ + I
Strikethrough --> ~~This is deleted~~
Inline Code   --> `git status`
Highlight     --> ==Important Text==
Blockquotes   --> > This is a quote.

Code Block
	```language_name
	code content
	```

Headings
	# Heading 1
	## Heading 2
	### Heading 3
	#### Heading 4
	##### Heading 5
	###### Heading 6


Bullet points 
- Point 1
- point 2


Task Lists
- [ ] Create Jira ticket
- [x] Implement API


Links
	- External Link
	  [Google](https://google.com)
	
	- Link to another Obsidian Note
	  [[file_name]]
	  
	- Link with Different Display Test
	  [[Kafka|Kafka Architecture]] 
	  
	- Link to a Heading
	  [[Kafka#Kafka Architecture]]
    
	- Link to Specific Block
	  [[Kafka#^5af733]]

	  
Images
	We can include any file, any heading and any section as an image 
	using ! and links commands from above.
		- ![[Keyboard Shortcuts & Markdown Cheat Sheet]]
	

Attach Files
	- ![[diagram.png]]
	- ![[architecture.pdf]]
	  

Horizontal Divider
	---
	***


Footnotes
	Kafka is a distributed event streaming platform.[^1]
	
	[^1]: Apache Kafka documentation.
```

>[!NOTE]- Example for Images
Example for Images (Attaching any section of the note from any file)
![[Kafka#^6ec333]]



#obsidian 

```clojure
(def ^:const pre-rotation-reminder-days  
  "For Auto domains only: Calendar-day offsets before scheduled rotation that trigger a reminder.  
   Deduped by derivation: send only when days-until-due equals one of these."  #{14 3 1})
```







[[📌 Callouts]]
