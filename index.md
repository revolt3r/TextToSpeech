## Documentation


### Synthesizing Speech

<p><details><summary><code>public static void Speak(string speechString)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken using DefaultParameters</p>
<p><strong>Parameters</strong><br>
  <i>string speechString</i> - The text to be spoken in the utterance.</p>
<p><strong>Example</strong>
  <pre>TTS.Speak("Hello world!");</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(string speechString, string language)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken using a voice object for the specified language and locale.</p>
<p><strong>Parameters</strong><br>
  <i>string speechString</i> - The text to be spoken in the utterance.<br>
  <i>string language</i> - A BCP 47 code specifying language and locale for a voice.</p>
<p><strong>Example</strong>
  <pre>TTS.Speak("Hello world!", "en-US");</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(string speechString, ISpeechSynthesisVoice voice)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken using a specific voice object</p>
<p><strong>Parameters</strong><br>
  <i>string speechString</i> - The text to be spoken in the utterance.<br>
  <i>ISpeechSynthesisVoice voice</i> - The voice used to speak the utterance.</p>
<p><strong>Example</strong>
  <pre>
  var voice = TTS.GetVoiceForLanguage("en-US");
  TTS.Speak("Hello world!", voice);</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(string speechString, SpeechUtteranceParameters speechUtteranceParameters)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken with default voice using specific parameters</p>
<p><strong>Parameters</strong><br>
  <i>string speechString</i> - The text to be spoken in the utterance.<br>
  <i>SpeechUtteranceParameters speechUtteranceParameters</i> - Parameters that affect the speech</p>
<p><strong>Example</strong>
  <pre>
  var parameters = new SpeechUtteranceParameters();
  TTS.Speak("Hello world!", parameters);</pre></p>
</details></p>

<p><details><summary><code>public static void Speak(SpeechUtterance speechUtterance)</code></summary>
<p><strong>Description</strong><br>
Enqueues an utterance to be spoken with using specific parameters</p>
<p><strong>Parameters</strong><br>
  <i>SpeechUtterance speechUtterance</i> - A chunk of text to be spoken, along with parameters that affect its speech.</p>
<p><strong>Example</strong>
  <pre>
  var utterance = new SpeechUtterance("Hello world!");
  TTS.Speak(utterance);</pre></p>
</details></p>


### Controlling Speech Synthesis

<p><details><summary><code>public static bool Continue()</code></summary>
<p><strong>Description</strong><br>
Continues speech from the point at which it left off.</p>
<p><strong>Return value</strong><br>
  Returns true if speech has continued, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Continue();</pre></p>
</details></p>

<p><details><summary><code>public static bool Pause()</code></summary>
<p><strong>Description</strong><br>
Pauses speech at default boundary constraints.</p>
<p><strong>Return value</strong><br>
  Returns true if speech has paused, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Pause();</pre></p>
</details></p>

<p><details><summary><code>public static bool Pause(SpeechBoundary speechBoundary)</code></summary>
<p><strong>Description</strong><br>
Pauses speech at the specified boundary constraint.</p>
  <p><strong>Parameters</strong><br>
  <i>SpeechBoundary speechBoundary</i> - A constant describing whether speech should pause immediately or only after finishing the word currently being spoken.</p>
<p><strong>Return value</strong><br>
  Returns true if speech has paused, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Pause(SpeechBoundary.Word);</pre></p>
</details></p>

<p><details><summary><code>public static bool Stop()</code></summary>
<p><strong>Description</strong><br>
Stops all speech at default boundary constraints.</p>
<p><strong>Return value</strong><br>
  Returns true if speech has stopped, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Stop();</pre></p>
</details></p>

<p><details><summary><code>public static bool Stop(SpeechBoundary speechBoundary)</code></summary>
<p><strong>Description</strong><br>
Stops all speech at the specified boundary constraint.</p>
  <p><strong>Parameters</strong><br>
  <i>SpeechBoundary speechBoundary</i> - A constant describing whether speech should stop immediately or only after finishing the word currently being spoken.</p>
<p><strong>Return value</strong><br>
  Returns true if speech has stopped, or false otherwise.</p>
<p><strong>Example</strong>
  <pre>TTS.Stop(SpeechBoundary.Word);</pre></p>
</details></p>

### Voices and Languages

#### Classes

<p><details><summary><code>public interface ISpeechSynthesisVoice</code></summary>
<p><strong>Description</strong><br>
The voice object used to speak the utterance.</p>
  <p><strong>Properties</strong><br>
  <p><i>string Identifier</i><br>
    The unique identifier for a voice object.</p>
  <p><i>string Name</i><br>
    The name for a voice object.</p>
  <p><i>string Language</i><br>
    A BCP 47 code identifying the voice’s language and locale.<br>
    The locale of a voice reflects regional variations in pronunciation or accent; for example, a voice with code en-US speaks English text with a North American accent, and a voice with code en-AU speaks English text with an Australian accent.</p>
  <p><i>VoiceQuality Quality</i><br>
    The speech quality for a voice object.<br>
    Default - he lower quality version of a voice that is usually installed on the device by default.<br>
    Enhanced - The higher quality version of a voice that is usually downloaded by the user.</p></p>
</details></p>

<p><details><summary><code>public enum VoiceQuality</code></summary>
<p><strong>Description</strong><br>
The speech quality for a voice object.</p>
  <p><strong>Values</strong><br>
  <p><i>Default = 1</i><br>
    The lower quality version of a voice that is usually installed on the device by default.</p>
  <p><i>Enhanced = 2</i><br>
    The higher quality version of a voice that is usually downloaded by the user.</p></p>
</details></p>

#### Usages

<p><details><summary><code>public static ISpeechSynthesisVoice GetVoiceForLanguage(string language)</code></summary>
<p><strong>Description</strong><br>
Returns a voice object for the specified language and locale.</p>
<p><strong>Parameters</strong><br>
  <i>string language</i> - A BCP 47 code specifying language and locale for a voice.</p>
<p><strong>Return value</strong><br>
  Returns null if no voice available for the specified language</p>
<p><strong>Example</strong>
  <pre>
  var voice = TTS.GetVoiceForLanguage("en-US");
  TTS.Speak("Hello world!", voice);</pre></p>
</details></p>

<p><details><summary><code>public static ISpeechSynthesisVoice[] GetAllVoicesForLanguage(string language)</code></summary>
<p><strong>Description</strong><br>
Returns all available voice objects for the specified language and locale.</p>
<p><strong>Parameters</strong><br>
  <i>string language</i> - A BCP 47 code specifying language and locale for a voice.</p>
<p><strong>Return value</strong><br>
  Returns an empty array if no voice available for the specified language</p>
<p><strong>Example</strong>
  <pre>
  var voices = TTS.GetAllVoicesForLanguage("en-US");
  Debug.Log("There are " + voices.Length + "voices available for en-US");</pre></p>
</details></p>

<p><details><summary><code>public static ReadOnlyCollection&lt;ISpeechSynthesisVoice&gt; AllAvailableVoices</code></summary>
<p><strong>Description</strong><br>
Returns all available voices.</p>
<p><strong>Return value</strong><br>
  Returns a read-only collection of all available voices</p>
<p><strong>Example</strong>
  <pre>
  var voices = TTS.AllAvailableVoices;
  Debug.Log("There are " + voices.Count + "voices available on this device");</pre></p>
</details></p>

<p><details><summary><code>public static string CurrentLanguageCode</code></summary>
<p><strong>Description</strong><br>
Returns the code for the user’s current locale.</p>
<p><strong>Return value</strong><br>
  Returns a string containing BCP 47 language and locale code for the user’s current locale.</p>
<p><strong>Example</strong>
  <pre>
  var languageCode = TTS.CurrentLanguageCode;
  Debug.Log("Current language code is " + languageCode);</pre></p>
</details></p>

<p><details><summary><code>public static string[] GetAllAvailableLanguages()</code></summary>
<p><strong>Description</strong><br>
Returns all language codes (A BCP 47) for which voices are available.</p>
<p><strong>Return value</strong><br>
  Returns an array with all language codes (A BCP 47) for which voices are available.</p>
<p><strong>Example</strong>
  <pre>
  var languages = TTS.GetAllAvailableLanguages();
  Debug.Log("There are voices available in " + languages.length + " languages");</pre></p>
</details></p>

### Custom Parameters

#### Classes

<p><details><summary><code>public class SpeechUtterance</code></summary>
<p><strong>Description</strong><br>
A chunk of text to be spoken, along with parameters that affect its speech.</p>
  <p><strong>Properties</strong><br>
  <p><i>string SpeechString</i><br>
    The text to be spoken in the utterance.<br>
  An utterance’s text cannot be changed once it is created. To speak different text, create a new utterance.</p>
  <p><i>float PitchMultiplier</i><br>
    The baseline pitch at which the utterance will be spoken.<br>
  The default pitch is 1.0. Allowed values are in the range from 0.5 (for lower pitch) to 2.0 (for higher pitch).</p>
  <p><i>float PreUtteranceDelay</i><br>
    The amount of time in seconds a speech synthesizer will wait before actually speaking the utterance upon beginning to handle it.<br>
  When two or more utterances are spoken, the time between periods when either is audible will be at least the sum of the first utterance’s postUtteranceDelay and the second utterance’s preUtteranceDelay.</p>
    <p><i>float PostUtteranceDelay</i><br>
      The amount of time in seconds a speech synthesizer will wait after the utterance is spoken before handling the next queued utterance.<br>
  When two or more utterances are spoken, the time between periods when either is audible will be at least the sum of the first utterance’s postUtteranceDelay and the second utterance’s preUtteranceDelay.</p>
    <p><i>float SpeechRate</i><br>
      The rate at which the utterance will be spoken.<br>
  Speech rates are values in the range between UtteranceMinimumSpeechRate and UtteranceMaximumSpeechRate. Lower values correspond to slower speech, and vice versa. The default value is UtteranceDefaultSpeechRate.</p>
    <p><i>ISpeechSynthesisVoice Voice</i><br>
      The voice used to speak the utterance.<br>
  The default value is null, which causes the utterance to be spoken in the default voice.</p>
  <p><i>float Volume</i><br>
  The volume used when speaking the utterance.<br>
  Allowed values are in the range from 0.0 (silent) to 1.0 (loudest). The default volume is 1.0.</p>
  <p><strong>Constructors</strong>
  <pre>public SpeechUtterance(string speechString)</pre>
  <pre>public SpeechUtterance(string speechString, SpeechUtteranceParameters parameters)</pre></p></p>
</details></p>

<p><details><summary><code>public class SpeechUtteranceParameters</code></summary>
<p><strong>Description</strong><br>
Parameters that affect the speech.</p>
  <p><strong>Properties</strong><br>
  <p><i>float PitchMultiplier</i><br>
    The baseline pitch at which the utterance will be spoken.<br>
  The default pitch is 1.0. Allowed values are in the range from 0.5 (for lower pitch) to 2.0 (for higher pitch).</p>
  <p><i>float PreUtteranceDelay</i><br>
    The amount of time in seconds a speech synthesizer will wait before actually speaking the utterance upon beginning to handle it.<br>
  When two or more utterances are spoken, the time between periods when either is audible will be at least the sum of the first utterance’s postUtteranceDelay and the second utterance’s preUtteranceDelay.</p>
    <p><i>float PostUtteranceDelay</i><br>
      The amount of time in seconds a speech synthesizer will wait after the utterance is spoken before handling the next queued utterance.<br>
  When two or more utterances are spoken, the time between periods when either is audible will be at least the sum of the first utterance’s postUtteranceDelay and the second utterance’s preUtteranceDelay.</p>
    <p><i>float SpeechRate</i><br>
      The rate at which the utterance will be spoken.<br>
  Speech rates are values in the range between UtteranceMinimumSpeechRate and UtteranceMaximumSpeechRate. Lower values correspond to slower speech, and vice versa. The default value is UtteranceDefaultSpeechRate.</p>
    <p><i>ISpeechSynthesisVoice Voice</i><br>
      The voice used to speak the utterance.<br>
  The default value is null, which causes the utterance to be spoken in the default voice.</p>
  <p><i>float Volume</i><br>
  The volume used when speaking the utterance.<br>
  Allowed values are in the range from 0.0 (silent) to 1.0 (loudest). The default volume is 1.0.</p>
  <p><strong>Constructors</strong>
  <pre>public SpeechUtteranceParameters()</pre></p>
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
Called when the synthesizer has paused while speaking an utterance.</p>
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
Called when the synthesizer has begun speaking an utterance.</p>
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
Called when the synthesizer is about to speak a portion of an utterance’s speechString.</p>
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
