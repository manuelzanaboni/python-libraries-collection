# Python libraries collection

A collection of Python libraries grouped by application area.

Installation guides and code snippets are provided. Pick your area and explore some useful libraries.

*This collection is meant to let you discover new libraries and give a first, brief description. Also, a link to the documentation is provided (click on library name).*


<details>
<summary>Screenshot</summary>

#### [pyscreenshot](https://github.com/ponty/pyscreenshot)

pyscreenshot let you take screenshots and save them as images.


Installation:

    pip install pyscreenshot
   
Usage example:

function **grab(...)**
```python
import pyscreenshot as ImageGrab

img = ImageGrab.grab() # grab fullscreen
img.save("fullscreen.png") # save image file

# bbox=(x_start, y_start, x_end, y_end)
im = ImageGrab.grab(bbox=(10, 10, 510, 510)) # part of the screen
im.save("box.png") # save image file
```
</details>

<details>
<summary>Serialization</summary>

#### [pickle](https://docs.python.org/3/library/pickle.html) *Object serialization*

pickle let you serialize and de-serialize Python objects.

Installation:

    pip install pickle
   
Usage examples:

function **dump(obj, file, protocol=None, ...)**
```python
import pickle

obj = ['Hello', 'World'] # object to be serialized 
with open('serialized.pkl', 'wb') as file:
    pickle.dump(obj, file, protocol=pickle.HIGHEST_PROTOCOL) # object saved as ./serialized.pkl
```

function **load(file, ...)**
```python
import pickle

with open('serialized.pkl', 'rb') as file:
    read = pickle.load(file)
    print(read) # ['Hello', 'World']
```
Also, **dumps(...)** and **loads(...)**
are provided to work with bytes objects instead of file object. 
</details>

<details>
<summary>Speech to text</summary>

#### [SpeechRecognition](https://pypi.org/project/SpeechRecognition/) *Speech to text*

SpeechRecognition let you convert speech to text.

Installation:

    pip install SpeechRecognition
   
*PyAudio 0.2.11+ (required only if you need to use microphone input)*

Usage examples:

function **list_microphone_names(...)**
```python
import speech_recognition as sr

# list all available audio input devices
for index, name in enumerate(sr.Microphone.list_microphone_names()):
    print("Microphone with name \"{1}\" found for `Microphone(device_index={0})`".format(index, name))
```

functions **listen(...), recognize_google(...)**
```python
import speech_recognition as sr

recognizer = sr.Recognizer()
with sr.Microphone() as source: # uses default input device
    print("Speak now...")
    audio = recognizer.listen(source)

recognized = recognizer.recognize_google(audio)
print(recognized)
```
</details>

<details>
<summary>Working with text</summary>

#### [googletrans](https://py-googletrans.readthedocs.io/en/latest/) *Text translation*

googletrans is a free and unlimited python library that implement Google Translate API.

Installation:

    pip install googletrans
   
Usage examples:

costant **LANGUAGES**
```python
import googletrans

print(googletrans.LANGUAGES) # returns all available languages with key
```

function **translate(text, dest='en', src='auto', ...)**
```python
from googletrans import Translator

translator = Translator()
translated = translator.translate('Buongiorno') # default language destination English, source language auto
print(translated.text) # text translated
```
If source language is not given, google translate attempts to detect the source language.

Array can be used to translate a batch of strings in a single method call and a single HTTP session, refer to documentation.

------

#### [pyspellchecker](https://pyspellchecker.readthedocs.io/en/latest/code.html) *Spell checker*

pyspellchecker can be used to determine if a word is misspelled and what the likely correct spelling would be based on word frequency.

Installation:

    pip install pyspellchecker
   
Usage examples:

functions **unknown(word_list), correction(word)**
```python
from spellchecker import SpellChecker

spell = SpellChecker()
words = ['hello', 'world', 'pithon', 'leptop', 'camputr']
misspelled = spell.unknown(words) # returns misspelled words

for word in misspelled:
    correction = spell.correction(word) # the most likely candidate correction
    print(f'Misspelled: {word}, correction: {correction}')
```
Also, **candidates(word)**, **word_probability(word)** and other functions are provided to work with spell checking, refer to documentation.
</details>

More to come...
