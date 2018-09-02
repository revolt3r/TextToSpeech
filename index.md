## Documentation

You can use the [editor on GitHub](https://github.com/revolt3r/TextToSpeech/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Controlling Speech Synthesis


<details><summary><code>public static void Speak(string speechString)</code></summary>
<p>
<strong>Description</strong><br>
Enqueues an utterance to be spoken using DefaultParameters<br>
<strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.<br>
<strong>Example</strong><br>
  <code>TTS.Speak("Hello world!");</code><br>
</p>
</details>
<br>

<details><summary><code>public static void Speak(string speechString, string language)</code></summary>
<p>
<strong>Description</strong><br>
Enqueues an utterance to be spoken using a voice object for the specified language and locale.<br>
<strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.<br>
  <i>language</i> - A BCP 47 code specifying language and locale for a voice.<br>
<strong>Example</strong><br>
  <code>TTS.Speak("Hello world!", "en-US");</code><br>
</p>
</details>
<br>

<details><summary><code>public static void Speak(string speechString, ISpeechSynthesisVoice voice)</code></summary>
<p>
<strong>Description</strong><br>
Enqueues an utterance to be spoken using a specific voice object<br>
<strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.<br>
  <i>voice</i> - The voice used to speak the utterance.<br>
<strong>Example</strong><br>
  <code>var voice = TTS.GetVoiceForLanguage("en-US");<br />
  TTS.Speak("Hello world!", voice);</code><br>
</p>
</details>
<br>

<details><summary><code>public static void Speak(string speechString, SpeechUtteranceParameters speechUtteranceParameters)</code></summary>
<p>
<strong>Description</strong><br>
Enqueues an utterance to be spoken with default voice using specific parameters<br>
<strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.<br>
  <i>speechUtteranceParameters</i> - Parameters that affect the speech<br>
<strong>Example</strong><br>
  <code>var parameters = new SpeechUtteranceParameters();<br />
  TTS.Speak("Hello world!", parameters);</code><br>
</p>
</details>
<br>

<details><summary><code>public static void Speak(SpeechUtterance speechUtterance)</code></summary>
<p>
<strong>Description</strong><br>
Enqueues an utterance to be spoken with using specific parametersbr>
<strong>Parameters</strong><br>
  <i>speechUtterance</i> - A chunk of text to be spoken, along with parameters that affect its speech.<br>
<strong>Example</strong><br>
  <code>var utterance = new SpeechUtterance("Hello world!");<br />
  TTS.Speak(utterance);</code><br>
</p>
</details>
<br>















Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/revolt3r/TextToSpeech/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
