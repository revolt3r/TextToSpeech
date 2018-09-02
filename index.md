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


### Setting Callbacks

#### Delegate Types

<p><details><summary><code>public delegate void SpeechUtteranceCallback()</code></summary>
<p><strong>Description</strong><br>
void Method with no parameters.</p>
</details></p>

<p><details><summary><code>public delegate void StringSpeechUtteranceCallback(int startIndex, int stringLength, string utteranceSpeechString)</code></summary>
<p><strong>Description</strong><br>
void Method with 3 parameters: int startIndex, int stringLength, string utteranceSpeechString.</p>
  <p><strong>Parameters</strong><br>
  <i>int startIndex</i> - The start index of the spoken part of the utterance string.<br>
  <i>int stringLength</i> - The number of characters in the spoken part of the utterance string.<br>
  <i>string utteranceSpeechString</i> - The utterance currently being spoken.</p>
</details></p>

#### Callbacks
<p><details><summary><code>public static SpeechUtteranceCallback onSpeechUtteranceCancelled</code></summary>
<p><strong>Description</strong><br>
Called when the synthesizer has resumed speaking an utterance after being paused.</p>
<p><strong>Example</strong>
<pre>private void Start()
{
    TTS.onSpeechUtteranceCancelled = LogOnCancelled;
}

private void LogOnCancelled()
{
    Debug.Log("Utterance was cancelled");
}
</pre></p>
</details></p>

<p><details><summary><code>public static SpeechUtteranceCallback onSpeechUtteranceContinued</code></summary>
<p><strong>Description</strong><br>
Called when the synthesizer has resumed speaking an utterance after being paused.</p>
<p><strong>Example</strong>
<pre>private void Start()
{
    TTS.onSpeechUtteranceContinued = LogOnContinued;
}

private void LogOnContinued()
{
    Debug.Log("Utterance was unpaused");
}
</pre></p>
</details></p>

<p><details><summary><code>public static SpeechUtteranceCallback onSpeechUtteranceFinished</code></summary>
<p><strong>Description</strong><br>
Called when the synthesizer has finished speaking an utterance.</p>
<p><strong>Example</strong>
<pre>private void Start()
{
    TTS.onSpeechUtteranceFinished = LogOnFinished;
}

private void LogOnFinished()
{
    Debug.Log("Finished speaking an utterance");
}
</pre></p>
</details></p>

<p><details><summary><code>public static SpeechUtteranceCallback onSpeechUtterancePaused</code></summary>
<p><strong>Description</strong><br>
Tells the delegate when the synthesizer has paused while speaking an utterance.</p>
<p><strong>Example</strong>
<pre>private void Start()
{
    TTS.onSpeechUtterancePaused = LogOnPaused;
}

private void LogOnPaused()
{
    Debug.Log("Utterance was paused");
}
</pre></p>
</details></p>

<p><details><summary><code>public static SpeechUtteranceCallback onSpeechUtteranceStarted</code></summary>
<p><strong>Description</strong><br>
Tells the delegate when the synthesizer has begun speaking an utterance.</p>
<p><strong>Example</strong>
<pre>private void Start()
{
    TTS.onSpeechUtteranceStarted = LogOnStarted;
}

private void LogOnStarted()
{
    Debug.Log("Utterance was started");
}
</pre></p>
</details></p>

<p><details><summary><code>public static StringSpeechUtteranceCallback onWillSpeakPartOfString</code></summary>
<p><strong>Description</strong><br>
Tells the delegate when the synthesizer is about to speak a portion of an utterance’s speechString.</p>
  <p><strong>Parameters</strong><br>
  <i>int startIndex</i> - The start index of the spoken part of the utterance string.<br>
  <i>int stringLength</i> - The number of characters in the spoken part of the utterance string.<br>
  <i>string utteranceSpeechString</i> - The utterance currently being spoken.</p>
<p><strong>Example</strong>
<pre>private void Start()
{
    TTS.onWillSpeakPartOfString = LogOnWillSpeak;
}

private void LogOnWillSpeak(int startIndex, int stringLength, string utteranceSpeechString)
{
    var partOfSpring = utteranceSpeechString.Substring(startIndex, stringLength);
    Debug.Log("Will speak: " + partOfSpring + " from the text: " + utteranceSpeechString);
}
</pre></p>
</details></p>
