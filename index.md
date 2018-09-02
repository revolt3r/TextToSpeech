## Documentation


### Synthesizing Speech

<p><details><summary><code>public static void Speak(string speechString)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken using DefaultParameters</p>
<p><strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.</p>
<p><strong>Example</strong>
  <pre>TTS.Speak("Hello world!");</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(string speechString, string language)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken using a voice object for the specified language and locale.</p>
<p><strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.<br>
  <i>language</i> - A BCP 47 code specifying language and locale for a voice.</p>
<p><strong>Example</strong>
  <pre>TTS.Speak("Hello world!", "en-US");</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(string speechString, ISpeechSynthesisVoice voice)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken using a specific voice object</p>
<p><strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.<br>
  <i>voice</i> - The voice used to speak the utterance.</p>
<p><strong>Example</strong>
  <pre>
  var voice = TTS.GetVoiceForLanguage("en-US");
  TTS.Speak("Hello world!", voice);</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(string speechString, SpeechUtteranceParameters speechUtteranceParameters)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken with default voice using specific parameters</p>
<p><strong>Parameters</strong><br>
  <i>speechString</i> - The text to be spoken in the utterance.<br>
  <i>speechUtteranceParameters</i> - Parameters that affect the speech</p>
<p><strong>Example</strong>
  <pre>
  var parameters = new SpeechUtteranceParameters();
  TTS.Speak("Hello world!", parameters);</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(SpeechUtterance speechUtterance)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken with using specific parameters</p>
<p><strong>Parameters</strong><br>
  <i>speechUtterance</i> - A chunk of text to be spoken, along with parameters that affect its speech.</p>
<p><strong>Example</strong>
  <pre>
  var utterance = new SpeechUtterance("Hello world!");
  TTS.Speak(utterance);</pre></p>
</details></p>


### Controlling Speech Synthesis

<p><details><summary><code>public static bool Continue()</code></summary>
<p><strong>Description</strong><br>
Continues speech from the point at which it left off.</p>
<p><strong>Returns</strong><br>
  Returns true if speech has continued, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Continue();</pre></p>
</details></p>

<p><details><summary><code>public static bool Pause()</code></summary>
<p><strong>Description</strong><br>
Pauses speech at default boundary constraints.</p>
<p><strong>Returns</strong><br>
  Returns true if speech has paused, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Pause();</pre></p>
</details></p>

<p><details><summary><code>public static bool Pause(SpeechBoundary speechBoundary)</code></summary>
<p><strong>Description</strong><br>
Pauses speech at the specified boundary constraint.</p>
  <p><strong>Parameters</strong><br>
  <i>speechBoundary</i> - A constant describing whether speech should pause immediately or only after finishing the word currently being spoken.</p>
<p><strong>Returns</strong><br>
  Returns true if speech has paused, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Pause(SpeechBoundary.Word);</pre></p>
</details></p>

<p><details><summary><code>public static bool Stop()</code></summary>
<p><strong>Description</strong><br>
Stops all speech at default boundary constraints.</p>
<p><strong>Returns</strong><br>
  Returns true if speech has stopped, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Stop();</pre></p>
</details></p>

<p><details><summary><code>public static bool Stop(SpeechBoundary speechBoundary)</code></summary>
<p><strong>Description</strong><br>
Stops all speech at the specified boundary constraint.</p>
  <p><strong>Parameters</strong><br>
  <i>speechBoundary</i> - A constant describing whether speech should stop immediately or only after finishing the word currently being spoken.</p>
<p><strong>Returns</strong><br>
  Returns true if speech has stopped, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Stop(SpeechBoundary.Word);</pre></p>
</details></p>


### Callback Delegates

<p><details><summary><code>public static SpeechUtteranceCallback onSpeechUtteranceCancelled</code></summary>
<p><strong>Description</strong><br>
Called when the synthesizer has resumed speaking an utterance after being paused.</p>
<p><strong>Example</strong>
  <pre>
TTS.onSpeechUtteranceCancelled = ClearTextProgress;
  
private void LogOnCancelled
{
              Debug.Log("Utterance was cancelled");
}
    </pre></p>
</details></p>
