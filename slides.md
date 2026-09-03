---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable Comark Syntax: https://comark.dev/syntax/markdown
comark: true
# duration of the presentation
duration: 15min
---

#  WordList App mit Speech Actions

In React Native

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
    Using Kimi K3
</div>

<div class="mt-12 py-1" hover:bg="white op-10">
  von Henrik Giesel
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

---
transition: slide-up
level: 2
---

# Requirements

- Lange Liste mit Wörtern (Daten)
- Speech Recognition API
- Anbindungen an LLMs für NLP

<v-click>

---
transition: fade-out
---

# Probleme bei langen Listen

- Angebungen an Firestore API mit 1000+ Einträgen

## Optimierungsansätze


- clientseitig:
  - `FlatList` + `keyExtractor` 
  - `onEndReached` + `onEndReachedThreshold`
  - `React.memo`, insbesondere das zwei Argumente
- API-seitig: 
  - paging + appending (im Falle eines Infinite Scroll)

```rust [filter-word.rs] {all|1|6-8|9}
impl<F: Fetch> FilterWordBy for F {
    async fn filter_words_by_language<Lang>(
        &mut self,
        language: &Lang,
    ) -> Result<Vec<Word<Lang::PartOfSpeech>>> {
        let response = self
            .fetch(format!("/words/language/{}", language.code()))
            .await?;
        Ok(self.deserialize_json(response).await?)
    }
    
    ...
}
```


---

<br>
<br>
<br>
    
<center>

# Vielen Dank!

</center>
