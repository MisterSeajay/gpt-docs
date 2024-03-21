---
title: Arcane Paintbrush
layout: single
classes: wide
permalink: /arcane_paintbrush/
---

An image-generating GPT intended to be used to illustrate role-playing game
characters in a consistent fantasy art style. The GPT will respond to requests
such as a "book illustration", "sketch" or "study" of a RPG character to deliver
images in particular formats or styles.

The GPT is able to access publicly-shared characters on the
[D&D Beyond](https://dndbeyond.com) website via their character ID.

## How to use this GPT

* [Open in ChatGPT](https://chat.openai.com/g/g-3R9svhPj5-arcane-paintbrush)

The key information that this GPT needs is the ID from D&D Beyond of the
character you want to illustrate. Instruct the GPT to get the description of the
character using the ID and you should see it calling an API. From this point on
you should be able to refer to your character by name.

A few example characters have been pre-loaded in the GPT including:

* **Aelar Fernblade**, a female elf ranger.
* **Gimble "Skip" Hopper**, a male gnome wizard.
* **Paliadryna "Pali" Vega**, a female human paladin.

### Screenshots

<table align="center" width="70%">
  <tr><td width="40%">
    <img src="/assets/images/arcane_paintbrush_01.jpg">
  </td><td width="55%">
    <img src="/assets/images/arcane_paintbrush_02.jpg">
  </td></tr>
</table>

## Behind the scenes

### Actions

This GPT uses **Actions** to access data held remotely. In some cases the files
are private and the GPT uses secrets to access them.

### Versioned Knowledge Documents

Rather than edit or upload **Knowledge Documents** repeatedly to ChatGPT,
versioned files are saved in a private GitHub repo. These can be retrieved using
an Action to download the file. The advantage is that edits can be made to these
documents outside of ChatGPT and then (re)loaded dynamically by the GPT.

### AWS Lambda functions

Originally it was expected that this GPT would query the D&D Beyond API directly
using the character_id (i.e. the number in the URL when you open the character
sheet). However, since the D&D Beyond API returns such a large amount of data,
it was necessary to use an interim API that would filter this data and return
only what is necessary for the GPT to use.

A few **AWS Lambda** functions have been created to act as this middle layer.
