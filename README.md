# MOEBIUS ORDER — Novel Chapters Repository

### 📖 Overview
Welcome to the **MOEBIUS ORDER** repository — the **official open-source narrative archive** for the upcoming game **_PICK ME UP: INFINITE GACHA GAME_**.

This repository contains the **primary lore, serialized chapters, and narrative source files** that define the **MOEBIUS ORDER** universe.  
All chapters are stored as **structured JSON files**, making them easy to parse, validate, and integrate into the game engine, apps, and lore databases.

> 📜 Every story here contributes to the living canon of the **MOEBIUS ORDER** — a secret organization manipulating the balance between creation, chaos, and memory.

---

## 🌍 Purpose

This project serves as the **official story backbone** for the _Pick Me Up: Infinite Gacha Game_ and related media.  
It is designed to be **open-source**, allowing writers, developers, and fans to contribute, refine, and expand the universe collaboratively.

### Goals
- 🧠 Provide a **structured narrative repository** accessible for both humans and machines  
- 🔄 Encourage **community-driven improvements** (typo fixes, translations, metadata, etc.)  
- 💾 Offer **modular JSON chapters** that integrate with any game or web project  
- 📚 Preserve the lore of **MOEBIUS ORDER** as a transparent and evolving archive  

---

## ⚖️ License

This project is licensed under the **MIT License**, granting freedom to use, modify, and redistribute the content — provided attribution is given to **MOEBIUS ORDER**.

> ⚠️ This repository contains narrative assets that are part of the _MOEBIUS ORDER_ intellectual world.  
> While you are free to fork and extend, please respect attribution and universe consistency.

---

## 💬 Community & Collaboration

Join our **official Discord server** to collaborate with editors, writers, and fans of the MOEBIUS universe:  
👉 [https://discord.gg/xBM7BZmJPH](https://discord.gg/xBM7BZmJPH)

Here you can:
- Discuss lore, continuity, and story ideas  
- Coordinate translation or adaptation efforts  
- Contribute formatting and validation scripts  
- Stay up to date with **PICK ME UP: INFINITE GACHA GAME** development  


---

## 🧱 JSON Chapter Format

Each chapter in this repository is stored as an independent `.json` file — there are **no volume folders**.  
Every chapter follows a unified schema for consistency and easy integration with the Pick Me Up: Infinite Gacha Game narrative system.

### Example Format

```json
{
  "chapter": NUMBER,
  "title": "STRING",
  "original_language": "STRING_CODE",
  "full_text": "LONG_STRING_OF_ALL_TEXT",
  "paragraphs": [
    {
      "id": NUMBER,
      "text": "PARAGRAPH_TEXT_STRING",
      "is_dialogue": BOOLEAN,
      "is_narrative": BOOLEAN,
      "is_descriptive": BOOLEAN,
      "section_heading": BOOLEAN,
      "section_ref": "SECTION_REFERENCE_STRING",
      "note": "OPTIONAL_NOTE_STRING"
    },
    {
      "id": NUMBER,
      "text": "PARAGRAPH_TEXT_STRING",
      "is_dialogue": BOOLEAN,
      "is_narrative": BOOLEAN,
      "is_descriptive": BOOLEAN,
      "section_heading": BOOLEAN,
      "section_ref": "SECTION_REFERENCE_STRING",
      "note": "OPTIONAL_NOTE_STRING"
    },
    // ... repeat for all paragraphs
    {
      "id": NUMBER,
      "text": "PARAGRAPH_TEXT_STRING",
      "is_dialogue": BOOLEAN,
      "dialogue_id": NUMBER_OR_NULL,
      "is_narrative": BOOLEAN,
      "is_descriptive": BOOLEAN,
      "section_heading": BOOLEAN,
      "section_ref": "SECTION_REFERENCE_STRING",
      "note": "OPTIONAL_NOTE_STRING"
    }
  ]
}
--
```

## 🧩 Field Descriptions

| Field | Type | Description |
| :--- | :--- | :--- |
| **chapter** | `number` | Numeric index of the chapter (e.g., `1`, `2`, `3`...) |
| **title** | `string` | Title of the chapter |
| **original_language** | `string` | ISO code for the original language (e.g., `"en"`, `"jp"`, `"ko"`) |
| **full_text** | `string` | Complete text of the chapter, stored as one continuous string for search and archival purposes |
| **paragraphs** | `array` | List of all paragraphs, dialogues, or descriptive text blocks in order |
| **paragraphs[].id** | `number` | Unique paragraph ID within the chapter |
| **paragraphs[].text** | `string` | Text content of the paragraph or dialogue line |
| **paragraphs[].is_dialogue** | `boolean` | `true` if this text is spoken dialogue |
| **paragraphs[].dialogue_id** | `number or null` | Optional ID for linking multi-line dialogues (used in complex conversation sequences) |
| **paragraphs[].is_narrative** | `boolean` | `true` if this text provides narrative exposition or story flow |
| **paragraphs[].is_descriptive** | `boolean` | `true` if this paragraph describes setting, tone, or physical elements |
| **paragraphs[].section_heading** | `boolean` | `true` if this marks a section or scene transition heading |
| **paragraphs[].section_ref** | `string` | Internal reference name for the section (e.g., `"intro_scene_1"`, `"battle_sequence_2"`) |
| **paragraphs[].note** | `string` | Optional short note for internal author remarks, translations, or metadata |

---

## 🪶 Chapter Naming Convention

Each chapter file must follow this strict naming pattern:

chapter_##.json

**Examples:**

chapter_01.json
chapter_02.json
chapter_03.json


✅ **Rules**
- Always use **two-digit numbers** (`01–99`).
- Avoid uppercase letters, spaces, or symbols.
- The `"chapter"` key inside the file **must** match the filename number.
- Each JSON should contain a **valid UTF-8 string**, and **no trailing commas**.

---

## 🧠 Writing Guidelines

To maintain a consistent narrative and structural format across all chapters, please follow these conventions:

### 1. Dialogues
- Set `"is_dialogue": true` for spoken lines.  
- Each new speaker starts with a new `"id"`.  
- Use `"dialogue_id"` to group multi-line dialogue segments spoken by the same character.

**Example:**
```json
{
  "id": 12,
  "text": "You really think you can win this battle alone?",
  "is_dialogue": true,
  "dialogue_id": 2,
  "is_narrative": false,
  "is_descriptive": false,
  "section_heading": false,
  "section_ref": "scene_forest_conflict"
}
```
### 2. Narration
- Set `"is_narrative": true` for story narration or internal thoughts.  
- Use for transitions, reflections, or storytelling outside of direct dialogue.

**Example:**
```json
{
  "id": 15,
  "text": "The forest trembled as if the wind itself feared what was coming.",
  "is_dialogue": false,
  "is_narrative": true,
  "is_descriptive": false,
  "section_heading": false,
  "section_ref": "forest_tension"
}
```

### 3. Descriptions
- Set `"is_descriptive": true` for visual, environmental, or emotional tone.  
- Use this for scene-building, setting details, or atmospheric effects.

**Example:**
```json
{
  "id": 18,
  "text": "Dark clouds gathered above, their shadows crawling across the ground like ink.",
  "is_dialogue": false,
  "is_narrative": false,
  "is_descriptive": true,
  "section_heading": false,
  "section_ref": "battle_preparation"
}
```
### 4. Section Headings
- Set `"section_heading": true` to indicate major story divisions, scene changes, or acts.  
- Each heading should include a `"section_ref"` value for internal linking or scripting purposes.

**Example:**
```json
{
  "id": 1,
  "text": "ACT II — Shadows of Resolve",
  "is_dialogue": false,
  "is_narrative": false,
  "is_descriptive": false,
  "section_heading": true,
  "section_ref": "act_2_intro"
}
```

## 🗂️ Folder & File Organization

All chapter files are stored inside a single root-level directory called `chapters/`.  
There are **no volume or subfolders** to keep the structure flat and easily accessible.

**Example structure:**
📦 repository_root/
┣ 📂 chapters/
┃ ┣ 📜 chapter_01.json
┃ ┣ 📜 chapter_02.json
┃ ┣ 📜 chapter_03.json
┃ ┗ 📜 ...
┣ 📜 README.md
┗ 📜 LICENSE


- Each JSON file represents **one full chapter**.  
- Filenames must follow the `chapter_##.json` convention.  
- All files should be valid JSON with no trailing commas.


## 🧾 Metadata Example

Below is a compact example to illustrate the structure of a chapter JSON file:

```json
{
  "chapter": 1,
  "title": "A Silent Beginning",
  "original_language": "en",
  "full_text": "The wind was still. Nothing moved in the ruins...",
  "paragraphs": [
    {
      "id": 1,
      "text": "ACT I — The Forgotten Dawn",
      "is_dialogue": false,
      "is_narrative": false,
      "is_descriptive": false,
      "section_heading": true,
      "section_ref": "act_1_intro",
      "note": ""
    },
    {
      "id": 2,
      "text": "The wind was still. Nothing moved in the ruins of the old world.",
      "is_dialogue": false,
      "is_narrative": true,
      "is_descriptive": false,
      "section_heading": false,
      "section_ref": "intro_scene",
      "note": ""
    },
    {
      "id": 3,
      "text": "\"What is this place?\"",
      "is_dialogue": true,
      "dialogue_id": 1,
      "is_narrative": false,
      "is_descriptive": false,
      "section_heading": false,
      "section_ref": "intro_scene",
      "note": "Esel speaks for the first time"
    }
  ]
}
```
---

## ✅ Conclusion

The **MOEBIUS ORDER Novel Chapters Repository** provides a fully structured, open-source collection of narrative content for **_Pick Me Up: Infinite Gacha Game_**.  

- Follow the **JSON schema** and naming conventions for new chapters.  
- Keep paragraphs, dialogues, narration, and descriptions clearly marked with the appropriate boolean fields.  
- Use the `"section_ref"` and `"note"` fields for internal linking and annotations.  
- Contribute via **pull requests** and collaborate on our **Discord**: [https://discord.gg/xBM7BZmJPH](https://discord.gg/xBM7BZmJPH)

This repository is designed to be **modular, accessible, and collaborative**, allowing writers, developers, and fans to help expand the MOEBIUS ORDER universe while keeping all chapters **consistent, structured, and game-ready**.

